---
layout: post
title: "How ChatGPT Learned To Code."
subtitle : "Understanding how language models develop abilities such as math, programming and more."
date: 2023-03-12
project : 
    title : "Artificial Intelligence"
    description : "Collections of blogs on artificial intelligence."
    color : "#fca5a5"
categories: 
    - Programming
    - Artificial Intelligence
    - OpenAI
    - ChatGPT
---

![OpenAI logo]({{ "/assets/images/how_chatgpt_learned_to_code/image1.jpg" | relative_url }} "How ChatGPT Learned To Code")

Originally built to be a language model, ChatGPT can solve questions related to mathematics, chemistry and write code. It is also capable of writing original stories, poems and more. These abilities were never programmed or trained into the model. This post dives into how and why large language models develop such emergent abilities.

### What is an LLM?
Large Language Models (LLMs) are designed to process and understand human language, and they can generate human-like responses to questions, comments, and other inputs. This makes them incredibly versatile and useful for a wide range of applications, including chatbots, language translation tools, voice assistants, and more. To train an LLM, massive amounts of text data are fed into the system, allowing it to analyze and learn the structure and patterns of language. This data can include anything from books and articles to social media posts and email messages. The more data that is fed into the LLM, the more accurate and sophisticated its language processing capabilities become. LLMs have demonstrated remarkable emergent abilities, including the ability to generate coherent and contextually appropriate responses to complex language inputs. For example, they can answer questions, generate detailed summaries of articles, and even engage in natural-sounding conversations with humans. LLMs are also capable of language translation, sentiment analysis, and identifying key topics and themes in large bodies of text.

Language Models define the probability distribution over word sequences. As a result, they are used for generative purposes for predicting the most likely word given the start of a sentence. They are trained using a process known as supervised learning which involves training over a large dataset of text such as books, articles or social media posts, that has been labelled with the correct output. For example, the input might be a sentence or a paragraph of text, and the output might be a summary of that text or a response to a question. During training, the LM is fed the input text and learns to predict the corresponding output using a neural network architecture. The network adjusts its weights and parameters based on the error between its predicted output and the correct output in the training data, using backpropagation to update the model's internal representations. This process is repeated for many iterations, with the model gradually improving its accuracy on the training data. Then task specific datasets are fed into the model to fine-tune the LM in a supervised fashion, making it faster and more efficient for the specific task at hand.

![Architecture of Generative Pre Training]({{ "/assets/images/how_chatgpt_learned_to_code/image2.png" | relative_url }} "Via : [Improving language understanding by generative pre training](https://s3-us-west-2.amazonaws.com/openai-assets/research-covers/language-unsupervised/language_understanding_paper.pdf) - Alec Radford, Karthik Narasimhan.")

### Emergent Abilities

But if you scale a language model into a large language model, it develops these abilities without the need for any fine-tuning or task specific training. LLMs are not just capable, but sometimes even better than the specialized networks at performing these tasks. Emergent abilities refer to skills or capabilities that arise spontaneously as a result of a system's interactions with its environment or data. These abilities are not explicitly programmed into the system but emerge as a result of the system's inherent complexity and the feedback it receives from its environment. As LLMs are scaled they hit a series of generations in which new abilities are suddenly unlocked.

Emergent abilities are not unique to AI and can be observed in many complex systems. They are seen in ant colonies. Individual ants have simple behaviors and limited intelligence, but when they work as a colony they can perform complex tasks such as building nests, finding food and defending their colonies. Traffic on highways can exhibit emergent behavior as well, with traffic jams emerging from the interactions between individual vehicles. Even small disruptions in traffic flow, such as a single car braking suddenly, can lead to a ripple effect that causes a traffic jam to form

[BIG-bench](https://github.com/google/BIG-bench) is a project which consists of 204 tasks, contributed by 444 authors across 132 institutions. Task topics are diverse, drawing problems from linguistics, childhood development, math, common-sense reasoning, biology, physics, social bias, software development, and beyond. BIG-bench focuses on tasks that are believed to be beyond the capabilities of current language model. They evaluate the behavior of LLMs like ChatGPT across model sizes spanning millions to hundreds of billions of parameters.

emoji_movie is a task in the BIG benchmark, in which a sequence of emojis describes a particular movie, and the task is to guess the movie given the sequence. For example, the sequence 👧🐟🐠🐡represents Finding Nemo. Here we can see the performance of BIG-G on emoji_movie at different scales.

![Performance of BIG-G on emoji movie at different scales]({{ "/assets/images/how_chatgpt_learned_to_code/image3.jpg" | relative_url }} "Via : [Beeyond The Imitation Game](https://arxiv.org/pdf/2206.04615.pdf)")

As we can see, the model performs quite poorly across scales, which is perhaps unsurprising. Nevertheless, the model appears to be getting slightly better as its size grows. If we extrapolate using just the last few scales, we might expect something like the below graph, where the solid lines are the extrapolations.

![Performance of BIG-G on emoji movie at different scales]({{ "/assets/images/how_chatgpt_learned_to_code/image4.jpg" | relative_url }} "Via : [Beeyond The Imitation Game](https://arxiv.org/pdf/2206.04615.pdf)")

However, what we actually find is this.

![Performance of BIG-G on emoji movie at different scales]({{ "/assets/images/how_chatgpt_learned_to_code/image5.jpg" | relative_url }} "Via : [Beeyond The Imitation Game](https://arxiv.org/pdf/2206.04615.pdf)")

Once the model surpasses a certain apparent threshold, estimated to be between 10^10 and 10^11 effective parameters, it enters a new phase where it can accomplish the relatively complex task with significantly improved precision. The shift can be described as a catapult effect. This accuracy boost is not the only one to emerge with scale - several other tasks in BIG-bench have been shown to exhibit similar behavior. Somewhat mysteriously, all of these abilities emerge at a similar scale despite being relatively unrelated.

![Highest Breakthrough Tasks]({{ "/assets/images/how_chatgpt_learned_to_code/image6.jpg" | relative_url }})

The significant aspect of this phenomenon is that we don't have prior knowledge of its occurrence or the extent of its impact. As a result, while we may attempt to develop new structures or other innovative solutions to address complex natural language problems, we may simply scale up LLMs to larger sizes to solve them. In addition, even if better architectures or other innovations could potentially solve these problems, the continuous advancements in hardware and AI technology suggest that these issues could be resolved with time alone.

So while an LLM like GPT has no understanding of what code it is writing, it can predict the syntax of a given problem in the same way it predicts the next most likely word in a sentence. The emergent abilities of Language Models (LLMs) are rapidly expanding the horizons of natural language processing. The ability of LLMs to recognize complex patterns and relationships within text data has led to the emergence of new abilities such as language understanding, generation, and translation.