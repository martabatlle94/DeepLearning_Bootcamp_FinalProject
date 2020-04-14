# Deep Learning Bootcamp Final Project. Building this project with a colleague under the supervision of data science experts.
*Under construction* One million songs sentiment analyzer. The aim is to compare two sentiment analyzers (using audio images (e.g. spectrograms) vs. using song lyrics (NLP). 

Steps:
1) Build an architecture on Amazon Web Services (s3 instance and several servers).
2) Get one million songs list:  use the One Million Song Dataset
3) Get the songs from youtube_dl (Youtube API)
4) Get the lyrics from Google lyrics (scrapping)
5) Convert the songs into spectrograms in Python
6) Sentiment analysis of lyrics/NLP using a simple polarity algorithm or a recurrent neural network/LSTM
7) "Sentiment analysis" of images (spectrograms) in Python using convolutional neural networks
7) Compare the performance of the two analyzers (to what extent do they give us the same results?)
9) Compare our results to the valence metrics from the Spotify API 
   (Get the valence for all our songs using the One Million Song Dataset ID-> Echonest -> Spotify API ID)
