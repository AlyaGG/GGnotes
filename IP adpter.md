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
## 2.1 embeding scale
V only：通常默认发送的是value，就是一个值
K+V:
K+V W/penalty:
K+mean(V) w/c penalty:
### 2.1.1 embeding 底层传参过程
embedings————处理器/采样器（dict）
dict 是双组数：包含key（name）和Value（高）