**问题**

讲一下 pooling 的作用， 为什么 max pooling 要更常用？哪些情况下，average pooling 比 max pooling 更合适？

**作用：**

对输入的特征图进行压缩，一方面使特征图变小，简化网络计算复杂度；一方面进行特征压缩，提取主要特征。

通常来讲，max-pooling 的效果更好，虽然 max-pooling 和 average-pooling 都对数据做了下采样，但是 max-pooling 感觉更像是做了特征选择，选出了分类辨识度更好的特征，提供了非线性。 pooling 的主要作用一方面是去掉冗余信息，一方面要保留 feature map 的特征信息，在分类问题中，我们需要知道的是这张图像有什么 object，而不大关心这个 object 位置在哪，在这种情况下显然 max pooling 比 average pooling 更合适。在网络比较深的地方，特征已经稀疏了，从一块区域里选出最大的，比起这片区域的平均值来，更能把稀疏的特征传递下去。


average-pooling 更强调对整体特征信息进行一层下采样，在减少参数维度的贡献上更大一点，更多的体现在信息的完整传递这个维度上，在一个很大很有代表性的模型中，比如说 DenseNet 中的模块之间的连接大多采用 average-pooling，在减少维度的同时，更有利信息传递到下一个模块进行特征提取。


average-pooling 在全局平均池化 GAP 操作中应用也比较广，在 ResNet 和 Inception 结构中最后一层都使用了平均池化。有的时候在模型接近分类器的末端使用全局平均池化 GAP 还可以代替 Flatten 操作，使输入数据变成一位向量。 
