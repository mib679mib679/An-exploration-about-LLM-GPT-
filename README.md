# An-exploration-of-LLM-GPT-
Code was adopted from Andrej Karpathy.

This script demonstrate how to train a GPT model from scratch, the code was adopted from Andrej Karpathy's Youtube video, "Let's build GPT: from scratch, in code, spelled out"(https://www.youtube.com/watch?v=kCc8FmEb1nY&t=4761s). The GPT model was trained on the tiny shakespeare dataset(https://www.kaggle.com/datasets/kaushaltiwari/tiny-shakespeare?resource=download) using a transformer architecture. I undertook this project to understand the concepts behind text generation, it was an incredibly inspiring tutorial.

Several thoughts on training a GPT from scratch:
1. It is still a classification problem, predicting the next character or sub-character in a sequence, but it does so in a innovative way. Kudos to the team developed this approach.
2. During training, each sentence is learned multiple times, allowing the model to calculate probalibilities for each unique characters to predict which character may occur next in the sequence.
e.g. The sentence I LOVE YOU. would be processed as follows: <br />
I  >> predict "L" <br />
I L >> predict "O" <br />
I LO >> predict "V" <br />
I LOV >> predict "E" <br />
I LOVE >> predict "Y" <br />
I LOVE Y >> predict "O" <br />
I LOVE YO >> predict "U" <br />
These characters would need to be encoded into unique numbers to train a model.
4. When optimising hyperparameters, it's advisable to start with smaller values and gradually increase them, we shall see an improvement in model performance up to a certain a point.
5. In tiny shakespeare dataset, there are 65 unique characters/tokens when using character-level tokenisation. However, when I tried sub-character tokenisation, the number of tokens exploded to over 2000. Similerly, when working with manderin text, such as training on the "Romance of Three Kingdoms" novel, the number of tokens exceeded 2000. This made the model difficult to train due to the large number of hyperparameters and made loss relatively higher. I quickly ran out of memory once the number of parameters exceeded 2.3 million. This experiecne suggests that training such models on a personel device is quite challenging. Cloud computing might help to overcome this issue, and I'm still exploring possible solutions.
