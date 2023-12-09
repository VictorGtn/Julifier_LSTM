# Julifier_LSTM
Project : generating new lyrics from an artist from scratch.

# Scrapping the data :
In order to have the data, I used lyricsgenius that scrap lyrics from the website Genius. So, here I decided to scrap 250 songs by JUL. One might take more if he as a gpu.

You can leave the artist as Jul, or you can take any artist you like, the process will be the same.

# Preprocessing of the data : 
Then there is a huge processing part, where i remove some things of the scrapped lyrics. I then create a corpus with all the songs set side by side. Then I create the data that will be fed to my model : a sliding windows goes throught all the data. The parameters of this window are sequence_lenght : the number of words we are going to use to predict a new one, and step, it's the step of the sliding windows : higher it is, less data you have.

# The model :
Then an LSTM architecture is used, it's a really simple one : an embedding layer, an lstm layer, a dropoutlayer, and a dense layer. The dropout layer is here to make sure our model doesn't overfit, this is really important since we only use one artist. The choice of architecture follow a lab i did , where we used RNN for translation and saw it's limits so I wanted to see how much better at language modeling task LSTM where. This is why I chose LSTM's. For the parameters of the model they are arbitrarly since I don't have the computing power to really tune it perfectly.

Either you can train it, or you can use the model.keras provided that is normally the model i trained for 100 epochs, with batch_size = 32.

# Generation of lyrics :
Then at the end, there is the generating part : You just need to put the start of your lyrics in the 'source' (provided it was in the vocabulary) and it will generate the number of words you asked (n_token).

As we can see with the results, it achevied to understand the shape of a music. Yet, the lyrical value of what is said is low, we have many sentece that have little to no sense. However sometimes we see that we can retrieve a bit from Jul style.
One way of making it better would be to have more training data, which is easy with my scrapping method, but i don't have an efficient enought computer to tackle all that data.

# Thoughts about this project
One thing I observed during this project was that at first I was using n-grams and not the sliding window, and it acheived really nicely to make what we call punchline (one line of generation). Yet it struggled way more when asking to do more.

Here I used a classic and really simple model architecture because I don't have a powerfull CPU/GPU, but one could change the model to put a stack of LSTM and it might be really better.

There is a follow up to this project that is Julifier, it'a a much simpler project where I finetune a GPT2 model in order to generate jul (still...). And we see it works clearly better because it as already all the knowledge from previous language modelling task. Yet it does valid (grammaticaly) sentences but, we lose a bit of jul's style. One might need to fine tune it even more.
