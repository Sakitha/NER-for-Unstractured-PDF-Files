# Unstractured_PDF_DATA
experimental architecture to model sequential independent input data.

idea is from named entity recognition algorithm which tries to classify entities from sentences.typycally this is done by lstm network with a crf layer. here i have tried to replace lstm recurrent cells with a feedforward net in a loop since LSTM has the vanishing gradient problem when it comes to a long sequences.

I have formed the input data in a way that each of them has information about other entities in the sequence.

let's say the pdf file is this - 

x k 
  v
l


i have predefined words set like this.these are the most used words in considered pdf files.(cornerstone words) 
x,v,j,l

now x, v ,l is in the considering document.

next im defining each of the word the pdf by the distances to the found cornerstone words in pdf.
