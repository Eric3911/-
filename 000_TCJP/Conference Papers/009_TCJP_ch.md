
##	顶级会议与期刊的经典论文

** 1、DAC2019年《低功耗目标检测系统设计挑战赛》经典论文skyNet、shufflenetv2

	GPU一般都在NVIDIA—TX2上部署获得第一名的是skynet及shufflenetv2为基础YOLO实现25FPS。
	
	芯片性能方面：FPGA峰值性能是GPU的1/10左右这个主要得益于GPU的架构深度流水线技术、retiming技术这样可以让很多核同时高频率运算，想提高计算多加核增减芯片面积就行而FPGA由于浮点运算会占很多逻辑资源，当型号选定后它本身的SRAM（查找表）受到布线限制没法对比GPU的标准逻辑单元。这时候其实可以学习ASIC的flow随意布线改进。
	内存接口方面：GPU采用传统的GDDR或者升级为HBM2从而带宽比FPGA更高，这样算法访问内存频率增强。
	灵活性方面：FPGA可以根据特定的应用编辑硬件，假如应用层加法运算多久可以把大量逻辑资源实现加法器提高性能这个主要用在基站通信服务器方面显著。GPU如果修改加法器的逻辑单元只能重新设计硬件资源。在MultipleInstructionstreamSingleDatastream单指令平行处理大量数据方面GPU更强。这个理论在ISCA2014年微软证明过。一般如果是专用的FPGA应用在深度学习方面都需要在FPGA公司提供的编译器上进行二次开发实现MISD架构功能。针对不同的业务场景例如图像、语言设计架构后运行速度提高,不过同等情况下一般GPU大于1GHz比FPGA快大约200MHz。如果FPGA加速器架构的优势来弥补运行速度劣势带来可以比GPU搞三个数量级。百度在HotChips的论文中指出GPU相比FPGA主要在人工智能方面是矩阵运算的batch data SIMD bench远超FPGA；但在处理服务器端少量计算多次处理请求方面（即频繁请求多和每次请求数据量和计算量小）非常占优势。这也是FPGA在服务器基站和通信方面大量使用的根源。
	
	功耗方面：功耗和能效是需要结合说明，标准参数上GPU的性能是FPGA的20倍，但是在能效方面执行单程序需要的能量GPU的消耗更好。FPGA更加节省计算资源这个根本原因是逻辑单位和运算器对底层的指令执行流水线排队。
	
	