实验背景：实验需要使用PV-Cre基因型小鼠。繁育后代理论上是PV-Cre杂合。但以防万一，需要进行基因型鉴定。
实验目的：鉴定小鼠基因型是否为PV-Cre

# 实验材料
待鉴定小鼠
NaOH 2g/L ddH₂O、冰、TE Buffer (5m㏖ EDTA, 1m㏖ Tris, pH8.0)、PCR Mix、双蒸水、琼脂糖、GelGreen核酸染料、100kb DNA Ladder、TAE溶液
95℃水浴锅、振荡机、PCR仪、微波炉、凝胶模具、凝胶托盘、电泳仪、凝胶成像仪

三种 PV-Cre 引物 10㏖/L ddH₂O（金唯智生产）序列：
Wild type Forward: CCATTCCCTCATCCACAGAG
Mutant Forward: GACGCAATCGTCCGATCC
Common: CAAACAAACTGAACAGAAACTCAGG

# 实验方法
将样品与120㎕NaOH混合，95℃水浴20min。放冰上冷却1min，加 30㎕ TE Buffer，震荡混匀，简单离心，取上清作为模板，配 20㎕ PCR 体系：10㎕ PCR Mix，1㎕ 模板，PV-Cre 三种引物各1㎕（注意引物存储液可能是10倍浓度），6㎕双蒸水。放入PCR仪，开程序，以C++示意：
```C++
#include <stdint.h>
void 温控(uint8_t 摄氏度, uint16_t 秒);
//无限时长直到手动停机
void 温控(uint8_t 摄氏度);
void PCR()
{
	温控(94, 120);
	for (uint8_t a = 0; a < 10; ++a)
	{
		温控(90, 15);
		温控(65, 15);
		温控(68, 40);
	}
	for (uint8_t a = 0; a < 29; ++a)
	{
		温控(94, 15);
		温控(60, 15);
		温控(72, 40);
	}
	温控(72, 360);
	温控(10);
}
```
根据样品数量选择合适的凝胶模具和凝胶托盘，一般完整方形托盘需要搭配100㎖体积的凝胶。据此配琼脂糖凝胶 10g/L TAE 溶液，微波炉加热约2min使其溶解，用双蒸水补足加热时蒸发掉的体积，然后静置冷却约10min至约60℃，加入核酸染料0.1㎖/L，混匀后倒入凝胶模具。PCR程序结束、琼脂糖凝胶固化（约需静置30min）后，将凝胶连着托盘一起放入电泳仪，倒入TAE溶液没过凝胶表面。将PCR体系加入凝胶孔中，启动电泳仪，110V 1h。条带展开后，将凝胶（不含托盘）放入凝胶成像仪，开UV拍照。PV-Cre 600bp，WT 200bp，如果是杂合则两条带都有。

# 实验日志
