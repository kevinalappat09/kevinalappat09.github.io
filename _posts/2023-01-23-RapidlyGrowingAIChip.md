---
layout: post
title: "The Rapidly Growing AI Chip Industry"
subtitle : "A dive into the hardware that powers AI models and the way it is evolving."
date: 2023-01-23
project : 
    title : "Artificial Intelligence"
    description : "Collections of blogs on artificial intelligence."
    color : "#fca5a5"
categories: 
    - Programming   
    - Artificial Intelligence
    - Hardware
    - Chip
---

![Server Room]({{ "/assets/images/rapidly_growing_chip_industry/image1.jpg" | relative_url }} "Server Room")

Artificial Intelligence is revolutionizing almost every field of work and has also made its way into our lifestyle. As a result, the hardware that powers it is also equally crucial. The hardware that powers AI is a complex and rapidly evolving field, with new technologies and advancements being constantly made. We will take a closer look at the different types of hardware used in AI and the companies that are leading the development of AI-specific hardware.

### How Deep Learning Works

Data used for deep learning and the neural networks parameters are represented in the form of a multi-dimensional array.
Deep learning works in two steps - The training phase and the inference phase.
The training phase starts by initializing the parameters of the neural network with random values. Then a set of training data is fed into the network, and the output of that network is compared to the true output. The difference between the expected output and predicted output is known as the loss and is used to judge the performance of a training model. Then the original parameters are updated by a technique called back-propagation. The same deep learning technique was used in [natural language processors](https://kevinalappat.substack.com/p/but-how-does-chatgpt-actually-work). The network parameters are updated after each iteration of the training data or after a batch of the training data is completed. The training process is repeated several times, with each iteration called an epoch. Once the network is trained, it can be used for inference on new data. This training process involves carrying out matrix multiplication between the network parameters, training data, and gradients of the error function concerning the parameters.
Then, during the inference phase, the trained neural network can make predictions on new inputs. The input data is once again represented as a matrix, where each row corresponds to a particular sample of data and each column corresponds to a particular feature that is common throughout the sample. The network parameters are also represented in the form of a matrix. Here each element of the matrix corresponds to a weight (which is a parameter representing the strength of the connection between two neurons). The dot product of the input matrix and weight matrix is taken for each layer of the network. The dot product is calculated by summing the product of the corresponding elements in the input data matrix and the weight matrix. The output matrix is then passed through an [activation function](https://deepai.org/machine-learning-glossary-and-terms/activation-function) until the final predicted output is reached.

### Why Are Graphic Cards Used

For a long time, CPUs have taken the brunt of the work in PCs and servers. But CPUs have been designed to handle a variety of tasks that a user has to perform. This includes running programs, managing memory, I/O operations and many more. To facilitate all these features the CPU has a lot of additional features that are not required for matrix multiplication. This includes large cache memory, complex instruction sets and more. As a result, CPUs are less efficient at performing the sizeable amount of floating point operations that need to be done for matrix multiplication.
GPUs on the other hand are specifically designed for parallel processing and handling large amounts of data. One of the first applications for the GPU was video game rendering. Video games require the graphics to be rendered in real-time, which means that the images on the screen need to be constantly updated as a player interacts with various parts of the game. This requires a large number of calculations to be carried out by the processor. GPUs are designed for this type of workload.

A GPU has many simple cores, known as CUDA (Computer Unified Device Architecture). These can perform the same operation simultaneously on different data sets. This makes the GPU much faster than a single-core CPU. The GPU also has a large amount of memory bandwidth and local memory called VRAM. These make it easy to move data between the GPU and the main memory. The GPU also has specialized hardware for rasterization units and texture mapping units.

But it's the first two features that make the graphics card ideal for deep learning algorithms. Some NVIDIA graphics cards also have specialized hardware called Tensor Core which optimizes the matrix multiplication process. Certain GPUs also have specialized instruction libraries made for deep learning such as cuBLAS, cuDNN, and TensorRT. These too assist in matrix multiplication.

### Shortcomings of GPU

Although GPUs are faster than CPUs for deep learning algorithms they have shortcomings of their own. The primary shortcoming is the power-hungry nature of GPUs. A high-end GPU can consume anywhere between 150-250 watts of power (some even more). They require a significant amount of energy to perform matrix calculations. This is a problem for devices with limited power such as mobile devices and embedded systems. Most GPUs support 16bit or 32bit precision but some deep learning models such as GANs, VAEs, GPT-2, and RNNs, require 64bit precision which is not well supported.

The last two shortcomings are the primary reason why companies are investing in AI-specific hardware. GPUs are costly and difficult to scale up with. Even a budget GPU such as the GeForce GTX 1650 costs around ₹12500. Professional GPUs like the NVIDIA A100 costs around ₹7,50,000. This makes increasing the scale of a deep learning model difficult. The computational resources of a GPU become a bottleneck. At this point, you can either buy multiple GPUs - which becomes more expensive or invest in AI-specific hardware.

### AI Specific Hardware

In May 2016, Google announced the Tensor Processing Unit at Google I/O. They had been using the TPU for almost a year at that point. It is an AI Accelerator application-specific integrated circuit. It was developed using Google’s TensorFlow software. The first-generation TPU is an 8-bit matrix multiplication engine. It was manufactured on a 28nm process. It has 28Mib of on-chip memory and 4Mib of 32-bit accumulators. It also includes an 8GiB of dual channel 2133 MHz DDR3 SDRAM offering 34Gb/s of bandwidth. Recently, they announced the fourth generation of TPU, with an on-chip memory of 144MiB and a memory bandwidth of 1200Gb/s. Capable of performing 275 Tera Operations Per Second. TPUs have a dedicated matrix multiplication unit. It has 65536 ALUs. That means a TPU can process 65536 multiply-and-adds for 8-bit integers for every cycle.

![Architecture of TPU]({{ "/assets/images/rapidly_growing_chip_industry/mage2.jpg" | relative_url }} "Architecture of TPU")
TPU solves the major problem that GPUs face when it comes to deep learning. It is energy efficient. A TPU is 29 times more energy efficient as compared to a GPU and more than 80 times better than a CPU. Also, the TPU is much better at performing predictions than GPUs.

However, TPU is one specific neural processing unit. These are processing units that help accelerate matrix multiplication specifically. There are also processing units that are optimized to perform a specific task. These are known as Application Specific Integrated Circuits (ASICs). These are highly optimized to perform one specific task with maximum efficiency which makes them ideal for use in mobile and embedded systems. Groq Tensor Streaming Processor (TSP), and Mythic AI processor are two examples of chips that are specifically designed for NLP. They are optimized for matrix and vector calculations but also to process recurrent neural networks and transformer models. Many companies have designed their ASICs - NVIDIA, IBM, and AMD, just to name a few. Qualcomm has been developing AI-specific hardware for mobile and embedded systems. Taiwan Semiconductor Manufacturing Company, the leading contract chip-making company had stated in 2017 that it will be focusing more of its efforts on developing chips suited for artificial intelligence. “We expect high-performance computing to become our major growth engine from 2020. By 2020 to 2025, that’s the time the need for high-performance computing products will really pick up.” said TSMC co-chief executive Mark Liu.

### Conclusion

AI hardware is a rapidly growing field that is becoming increasingly important as the demand for AI and deep learning applications continues to rise. GPUs have been the go-to hardware for deep learning due to their ability to perform matrix multiplications quickly. However, newer AI-specific hardware such as TPUs, IPUs, and NPUs have been developed that are specifically optimized for deep learning workloads. Companies like Nvidia, Intel, AMD, Xilinx, Graphcore, Cerebras Systems, Qualcomm, and IBM are leading the way in the development of AI hardware. With the advancement in technology, it's expected that AI hardware will continue to evolve and improve, making AI applications more accessible and efficient in the future.