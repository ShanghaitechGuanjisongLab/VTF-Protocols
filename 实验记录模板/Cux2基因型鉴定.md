实验背景：实验需要使用Cux2-Cre基因型小鼠。繁育后代理论上是Cux2-Cre杂合或野生型，需要进行基因型鉴定。
实验目的：鉴定小鼠基因型是否为Cux2-Cre

# 实验材料
待鉴定小鼠组织样品（脚趾、尾尖等）
NaOH 2g/L ddH₂O、冰、TE Buffer (5m㏖ EDTA, 1m㏖ Tris, pH8.0)、PCR Mix、双蒸水、琼脂糖、GelGreen核酸染料、Acmec MarkerⅠDNA Ladder (100~600bp)、TAE溶液
振荡机、PCR仪、微波炉、凝胶模具、凝胶托盘、电泳仪、凝胶成像仪

三种 Cux2-Cre 引物 10μ㏖/L ddH₂O（金唯智生产）序列：
Cux2.F: 5’-AAG ACC TAC CAT GCC ACA CC-3’
Cux2.R: 5’-CTG CCC CAA GTG TAA TGT CA-3’
Cre.R: 5’-GCA AAC GGA CAG AAG CAT TT-3’

# 实验方法
将样品与120㎕NaOH混合，95℃20min。放冰上冷却1min，加 30㎕ TE Buffer，震荡混匀，简单离心，取上清作为模板，配 20㎕ PCR 体系：10㎕ PCR Mix，1㎕ 模板，三种引物各1㎕（注意引物存储液可能是10倍浓度），6㎕双蒸水。放入PCR仪，开程序，以C++示意：
```C++
import std;
using namespace std::chrono_literals;
template <typename TDuration>
void 温控(float 摄氏度, TDuration 时间);
//无限时长直到手动停机
void 温控(float 摄氏度);
int main()
{
	温控(95, 3min);
	for (uint8_t a = 0; a < 35; ++a)
	{
		温控(94, 30s);
		温控(62, 30s);
		温控(72, 45s);
	}
	温控(72, 10min);
	温控(4);
}
```
根据样品数量选择合适的凝胶模具和凝胶托盘，一般完整方形托盘需要搭配100㎖体积的凝胶。据此配琼脂糖凝胶 20㎎/㎖ TAE 溶液，多加1/3体积的dd水以补足蒸发量，置于容积至少6倍于液体体积的容器中防止沸出，微波炉加热80s使其初步溶解，晃匀后再加热40s（分两次加热防止暴沸），然后静置冷却至约60℃（冷却时间大约为液体㎖数的2/3次幂分钟），加入核酸染料0.1㎕/㎖，混匀后倒入凝胶模具。PCR程序结束、琼脂糖凝胶固化（约需静置30min）后，将凝胶连着托盘一起放入电泳仪，倒入TAE溶液没过凝胶表面。将PCR体系和 DNA Marker 加入凝胶孔中，启动电泳仪，4V/㎝，对于23㎝电泳槽则为92V 2h。条带展开后，将凝胶（不含托盘）放入凝胶成像仪，开UV拍照。WT 592bp，MUT 650bp，如果是杂合则两条带都有。

# 实验日志（带鼠号的胶图）