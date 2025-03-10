实验背景：在行为学实验中发现合并迁移学习比初始学习更快。为了找出哪些脑区是迁移学习过程加速所必需的，现有CNO-hM4D(Gi)化学遗传操作系统，可以在注射CNO时抑制表达了hM4D(Gi)受体的神经细胞。cFos是一种神经元活动依赖的即早基因，使用Cre-DIO条件表达系统可以在因持续活动而表达cFos的细胞中同时表达病毒基因。CreER是一种特殊的Cre变体，它只能在注射 Tamoxifen (TM) 24 小时后发挥DNA剪切作用。以此，可以用TM控制cFos-CreER-DIO表达系统的运行时机。
实验目的：在学会后用cFos标记持续活动的神经元，迁移阶段抑制，观察迁移行为是否受到影响。

# 实验材料
安装有头部固定架的cFos-CreER小鼠，并在多脑区注射了pAAV-hSyn-DIO-hM4D(Gi)-mCherry-WPRE病毒，休息3周以上病毒表达。
小鼠固定床、Arduino Mega 2560 开发板、蓝色LED灯、蠕动水泵、橡胶管、小鼠灌胃针、杜邦线、触感电容、隔音黑箱、水瓶、5V-12V升压板、USB摄像头、有源蜂鸣器、5㎎ 氯氮平N-氧化物（CNO）/8.3㎖ D-PBS 溶液、20㎎ Tamoxifen / ㎖ 玉米油溶液

Tamoxifen溶液配制方法：先用无水乙醇溶解，然后加入等体积玉米油，真空离心以挥发掉无水乙醇，得到玉米油溶液。挥发速度约500㎕/h。

# 设备部署
小鼠通过头架固定在床上，嘴前放置灌胃针，使得小鼠能且仅能伸舌头恰好碰到针头。灌胃针管后部连接橡胶管，橡胶管连接蠕动水泵，水泵另一端连接水瓶，这样水泵开动时就可以从水瓶抽水，水珠悬挂在灌胃针上，小鼠伸舌头就能舔到。水泵的正负电极通过杜邦线连接到5V-12V升压板的12V端，5V端连接Arduino开发板控制。
此外，灌胃针外还缠绕铜线圈，通过杜邦线连接到触感电容。这样小鼠舌头触碰针头时，触感电容就会感应到，发送信号给Arduino。
蓝色LED灯和有源蜂鸣器放在小鼠右眼旁，连接Arduino开发板控制。
小鼠、LED灯、灌胃针和摄像头一同置于隔音黑箱中，通过杜邦线和橡胶管通过黑箱开口同外部连接。

# 实验方法
将小鼠固定在床上，置于黑箱中，灌胃针头对准嘴。然后使用[通用行为实验控制](https://github.com/ShanghaitechGuanjisongLab/Generic-Behavioural-Experimental-Control)软件，配置实验设计参数，然后自动开始运行实验。
先每天训练声水，早晚各一次。学会后继续训练3天，前两天每天注射一次Tamoxifen溶液，2㎕/g体重。然后等待2周以上病毒表达。那之后，每次先注射 CNO 3㎕/g 体重，等待至少1h后再做光水，早晚各一次，直到学会。

# 基本训练回合
声-水偶联训练：给200㎳声音，等待800㎳，然后给水。在这前后一共1s时间内，如果小鼠舔了灌胃针头，记为命中；若未舔，记为错失。（无论舔不舔都给水）等待小鼠在随机5~10s之内没有舔水行为，开始下一回合
光-水偶联训练：给200㎳蓝光，等待800㎳，然后给水。在这前后一共1s时间内，如果小鼠舔了灌胃针头，记为命中；若未舔，记为错失。（无论舔不舔都给水）等待小鼠在随机5~10s之内没有舔水行为，开始下一回合

# 实验日志
日期时间	鼠号	备注