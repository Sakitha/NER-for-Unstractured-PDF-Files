# Unstractured_PDF_DATA

Original challenge was to extract entities (Name, Address, companies they worked, postions they held.. etc) from pdf resume files.

For each entity in a resume the context comes from the section they resides within the resume. Neighboring entities gives context to each other.
(As a human, if we saw a resume from a foreign language we still can identify Names, addresses, companies because of the graphical context) 

Pre trained models are mostly trained to extract enteties from full sentences. So I have to define my own feature vector and train a model

let's say the pdf file is this - 

----

x k 

  v
l

----

i have a predefined words set.these are the most used words in considered pdf file set.
lets say x,v,j words have the highest chance of accouring. (i defined them as cornerstone words) 

in the above pdf there are only x and v.

next im defining each of the word in the pdf as a vector of relative distances to those cornerstone words which are founded in the currant pdf.

A simple builtin NLP models has a lstm network with a crf layer.( lstm captures sentence patterns, crf to capture the context)

if a pdf has 100 cornerstone words then the feature vector will also contain 200 ( x, y lengths for each cornerstone word) entries. if we decided to include font sizes, word vectors, along with relative distances then feature vector becomes much larger     

LSTM has the vanishing gradient problem when it comes to a long sequences.

here i have tried to replace lstm recurrent cells with a feedforward net in a loop since 

I have formed the input data in a way that each of them has information about other entities in the sequence.
