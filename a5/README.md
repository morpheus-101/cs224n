## Neural Machine Translation ##

<a target="_blank" href="https://github-readme-medium-recent-article.vercel.app/medium/@rishikeshdhayarkar1091/0"><img src="https://github-readme-medium-recent-article.vercel.app/medium/@rishikeshdhayarkar1091/0" alt="Assignment 4 blog post">

This assignment builds on top of assignment 4. Check out my medium blogpost on assignment 4 solution.
[Assignment 4 blog](https://medium.com/@rishikeshdhayarkar1091/neural-machine-translation-a-comprehensive-guide-ef414e79b49?source=friends_link&sk=2a480e785e9104499991441644e9bcef)





  
Take a look at some Spanish to English translation done by this Neural Machine Translator.</br>
Test sentences in Spanish 
<p align="center">
  <img height="320" width="800" src="https://github.com/RishikeshDhayarkar/cs224n/blob/master/a5/git_pics/test_es.png">
</p>  

English ground truth for the Spanish test sentences
<p align="center">
  <img height="320" width="800" src="https://github.com/RishikeshDhayarkar/cs224n/blob/master/a5/git_pics/test_en.png">
</p>  

Test output from the NMT model
<p align="center">
  <img height="320" width="800" src="https://github.com/RishikeshDhayarkar/cs224n/blob/master/a5/git_pics/test_out.png">
</p>  

[Results notebook](https://github.com/RishikeshDhayarkar/cs224n/blob/master/a5/a5_final.ipynb) 
<p align="center">
  <img height="320" width="900" src="https://github.com/RishikeshDhayarkar/cs224n/blob/master/a5/git_pics/code_output.png">
</p> 

NMT models can be broken down into 4 basic stages. This is shown in the figure below. All these stages create an NMT model at a word level, as discussed in assignment 4 blogpost. The goal of this assignment is to convert a word level NMT model into a character level NMT model. </br>
The core idea is that when our word-level decoder produces an unknown toekn(<UNK>), we trigger out character level decoder to produce a target word instead of an unknown token. This process happens character by character. This helps in producing rare and out of vocabulary target words and it also performs transliteration to some extent. To achieve this goal we basically need to replace step 1 with a character based convolutional encoder and modify step 4 by adding a character based LSTM decoder. 
  
<p align="center">
  <img height="170" width="700" src="https://github.com/RishikeshDhayarkar/cs224n/blob/master/a5/git_pics/over_all_nmt.png">
</p>  

First thing that we need to do is to replace the typical 'Embedding lookup' stage with a sequence of operations shown in figure 2. 

<p align="center">
  <img height="640" width="700" src="https://github.com/RishikeshDhayarkar/cs224n/blob/master/a5/git_pics/h_1.png">
</p>

## Convert words to charcater indices ##

<p align="center">
  <img height="200" width="700" src="https://github.com/RishikeshDhayarkar/cs224n/blob/master/a5/git_pics/1_step1.png">
</p>

## Padding and embedding lookup ##

<p align="center">
  <img height="200" width="700" src="https://github.com/RishikeshDhayarkar/cs224n/blob/master/a5/git_pics/1_step2.png">
</p>

## Connvolutional Network ##

<p align="center">
  <img height="600" width="700" src="https://github.com/RishikeshDhayarkar/cs224n/blob/master/a5/git_pics/1_step3.png">
</p>

## Highway layer and dropout ##

<p align="center">
  <img height="300" width="700" src="https://github.com/RishikeshDhayarkar/cs224n/blob/master/a5/git_pics/1_step4.png">
</p>

## Character based LSTM decoder ## 

<p align="center">
  <img height="640" width="700" src="https://github.com/RishikeshDhayarkar/cs224n/blob/master/a5/git_pics/h_2.png">
</p>

## Forward computation of character decoder ##

<p align="center">
  <img height="300" width="700" src="https://github.com/RishikeshDhayarkar/cs224n/blob/master/a5/git_pics/2_step_1.png">
</p>

## Training of character decoder ##

<p align="center">
  <img height="300" width="700" src="https://github.com/RishikeshDhayarkar/cs224n/blob/master/a5/git_pics/2_step_2.png">
</p>

## Decoding from the character decoder ##

<p align="center">
  <img height="200" width="700" src="https://github.com/RishikeshDhayarkar/cs224n/blob/master/a5/git_pics/2_step_3.png">
</p>

## Greedy decoding ##

<p align="center">
  <img height="300" width="700" src="https://github.com/RishikeshDhayarkar/cs224n/blob/master/a5/git_pics/h_3.png">
</p>


