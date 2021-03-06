# Voice_Steg
## 音频隐写检测数据集 
 
* 下载路径： 谷歌云：【https://drive.google.com/open?id=1bjqlB4QjoLlB6yIvAQJ3ZjvU6IRX8Lpk】 
             百度云：【https://pan.baidu.com/s/16yiyOf1qZGUw2nZwyU_FgQ】 提取码：cfsa  
* 音频来源：采集不同人的语音信号，然后按照 G.729a 标准进行编码； 提示： 不熟悉该编码方式，可以参考 这篇论文的建模和处理方式： Real - Time Steganalysis for Stream Media Based on Multi - channel Convolutional Sliding Windows
 音频时长：编码后的语音信号统一裁剪成 1s 的语音片段；  
 隐写算法：每段语音样本随机选择两种不同的隐写算法之一以随机的嵌入率进行嵌入， 两种隐写算法名称及相应的论文如下： 
 
## 隐写算法 相关论文 
CNV-QIM 
Xiao B, Huang Y, Tang S. An approach to information hiding in low bit-rate speech stream 
Pitch 
Huang Y, Liu C, Tang S, et al. Steganography integration into a low-bit rate speech codec   

## 语音隐写分析提供训练数据和测试：   
* 训练集：  音频数量：隐写和非隐写音频各 155327 段。隐写和非隐写音频由相同的 wav 音频（约 43 个小时的中文音频）编码得到。    
  文件夹：   ./ch_0_g729a：没有隐写的 G.729a 编码后音频   ./ch_steg_g729a：有隐写的 G.729a 编码后音频。  
* 测试集：  2000 段编码后时长为 1s 的音频片段，以 0.5 的概率选择数据集中的音频片段，然后随机挑选两种嵌入算法之一，并将随机生成的比特流以随机的嵌入率进行随机嵌入。 
 
# 使用方式：
1：准备音频数据 g729a有两个特征 LPC（三维）和PD（二维），用准备py脚本提取，工具为比赛方提供，使用concat.py将其拼成五位=维数据一起训练    
2：使用DANN_ATT_final.py 进行训练。
注：cnn_lstm_att.py里是没有DA的，test效果很差之前想分别用不同的特征训练，再把结果合起来，效果和瞎猜差不多。

# 最终结果
7/18 准确率0.5235 差一名就拿名次辽，虽然就比瞎猜好那么一丢丢。  
加了DA提了四个点，俩星期，太悲惨辽，感谢老卢同志的场外支持。

2019.10.15


# References：
1. https://github.com/ssamot/DANN-keras/blob/master/DANN_keras_blob.ipynb  
2. https://github.com/fjxmlzn/RNN-SM
