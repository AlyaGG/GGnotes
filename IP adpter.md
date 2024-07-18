# 1 CADU

# 2 权重 weight
为了更好的保持风格或特性 权重需要调整到1
	可以通过不同的权重方式来改变参考
	linear 线性 ：平的，从头到尾执行下来
	ease in 缓动：ipadpter 曲线权重由高到底
	ease out 缓动：ipadpter 曲线权重由低到高
	ease in out ： 缓入缓出，开头结尾权重高，中间权重地
	reverse in out：ip 权重低，只在生成过程中起作用
	weak input：没有谁在某个点位权重高，而是IPA权重和模型CLIP权重始终存在，配比不同。模型刚开始是比较弱的地步，后面慢慢扩大权重比例，权重倾向IPA
	weak onput：刚开始模型占据比例较多，IP权重慢慢增加
	weak middle：不常用，不好掌握，相互掺杂，大概主模型30％，IPA70％
	strong middle：IPA 30％
	style transfer (SDXL): 风格转移  会参考图中画风，人物特征等一切风格方向的。
	composition (SDXL):完全模仿图像中的构图，并不会参考人物特征，也不会参考画风，
## 2.1 embeding scale
V only：通常默认发送的是value，就是一个值
K+V:key和value 一起发送给采样器，
K+V W/penalty: 平均值
K+mean(V) w/c penalty:权重值

k+v：很多embedings当中的一些信息，它的分类就很明确，如果和题词没有相关分类的embedings，那我们的prompt就会体现出来，有了这个类型指定以后，他就不会堆叠了，如果没有类型的话：又是阳光/构图/人物/服装等等，堆叠在一起，没有分类就会过拟合，有了分类后，分类里面的权重其实并没有那么高。

变相的体现prompt，也可以在IP高权重的情况下来平衡我们整个的权重,
例如：IPA强度1.5，V only----会堆叠很多内容，造成画面混乱，过拟合
K+V:将这个embedings的缩放来调整一下，平衡权重和参考图之间的关系，在IPA高权重的情况下保持一定的简洁性（但无法确认是否会对IP保持减弱）
### 2.1.1 embeding 底层传参过程
embedings————处理器/采样器（dict）
dict 是双组数：包含key（name）和Value（高）


# 实际举例
例如：一张图参考构图，但是细节不是很好，需要怎么调整
	调高IPA 参考数值
	调整embedings scale 的参考类型变为 K+V