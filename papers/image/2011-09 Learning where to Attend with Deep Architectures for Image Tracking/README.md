

#Notes
##Abstract
We discuss an attentional model for simultaneous object tracking and recognition that is driven by gaze data. Motivated by theories of perception, the model consists of two interacting pathways: identity and control, intended to mirror the what and where pathways in neuroscience models. The identity pathway models object appearance and performs classification using deep (factored)-Restricted Boltzmann Machines. At each point in time the observations consist of foveated images, with decaying resolution toward the periphery of the gaze. The control pathway models the location, orientation, scale and speed of the attended object. The posterior distribution of these states is estimated with particle filtering. Deeper in the control pathway, we encounter an attentional mechanism that learns to select gazes so as to minimize tracking uncertainty. Unlike in our previous work, we introduce gaze selection strategies which operate in the presence of partial information and on a continuous action space. We show that a straightforward extension of the existing approach to the partial information setting results in poor performance, and we propose an alternative method based on modeling the reward surface as a Gaussian Process. This approach gives good performance in the presence of partial information and allows us to expand the action space from a small, discrete set of fixation points to a continuous domain. 

尝试翻译下，读起来好别扭，以后再改吧。

本文我们在视觉物体上进行跟踪和识别的问题上探讨了一种注意力模型。该模型基于感知机的理论，包括两个
视觉交互通路：标识与控制，分别对应神经科学模型的"what"和"where"通路。标识通路用来建模物体的出现
并使用深度限制玻尔兹曼机进行分类。在每个时间点，视网膜上的成像的分辨率从内到外不断降低。控制通路
对所注意的物体的位置，方向，尺度和速度进行建模。这些状态的先验分布可以使用粒子滤波进行估计。随着
控制通路的加深，我们使用注意力机制来学习如何选取关注的物体，从而最小化跟踪的不确定性。和我们以前的
工作不同，我们介绍了关注物体选择的策略，该策略只使用部分信息以及连续的动作空间。测试表明直接使用部分
信息的方法会导致很差的性能，我们提出了另一种基于高斯过程的奖励建模方法。这种方法在只使用部分信息的情况
下也能得到不错的性能，同时也有助于把动作空间从小的离散的固定点集扩展到连续域。

##Summary



**Reference**

