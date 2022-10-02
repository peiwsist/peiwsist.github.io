



### Face

<mark>*Face* 是广义的网络接口</mark>。与物理网络接口类似，可以在 *Face* 上发送和接收数据包。NFD作为网络转发器，在网络接口之间移动数据包。NFD不仅可以在物理网络接口上进行通信，还可以在各种其他通信通道上进行通信，例如TCP和UDP上的覆盖隧道。因此，我们将“网络接口”泛化为“Face”，从而抽象了NFD可用于数据包转发的通信通道。

- 物理网络接口以在物理链路上进行通信（ *a physical network interface to communicate on a physical link* ）；
- NFD与远程节点之间的覆盖通信通道（ *an overlay communication channel between NFD and a remote node* ）；
- NFD与本地应用程序之间的进程间通信通道（ *an inter-process communication channel between NFD and a local application* ）。

<mark>*Face* 抽象（nfd :: Face类）为NDN`网络层`数据包提供尽力而为的传递服务。 *Forwarding* 可以通过 *Face* 发送和接收兴趣包（ *Interest packet* ），数据包（ *Data packet* ）和 Nack。</mark> 然后，该 *Face* 处理低层的通信机制（例如套接字），并对 *Forwarding* 隐藏不同底层协议的差异和细节。



#### **Forwarding 如何使用 Face的？** 

`FaceTable` 类是 *Forwarding* 的一部分，它跟踪所有活动的 *Face* 。 新创建的 *Face* 将传递给 `FaceTable::add`，这个函数为传入的 *Face* 分配一个数字 *FaceId* 用于识别。 关闭 *Face* 后，将其从 *FaceTable* 中删除。 ***Forwarding* 通过连接到`afterReceiveInterest`、`afterReceiveData`和`afterReceiveNack`信号来从 *Face* 接收数据包** ，此操作在 *FaceTable* 中完成。 *Forwarding* 可以通过调用`sendInterest`、`sendData`和`sendNack`方法来通过 *Face* 发送网络层数据包。



#### **Face内部结构（ *Internal structure* ）** 

在内部， ***Face* 由 *LinkService* 和 *Transport* 组成** （图2）。*Transport* （第2.2节）是 *Face* 较底层的部分，包裹了底层的通信机制（例如套接字或libpcap句柄），并为 *Face* 提供尽力而为的TLV数据包传递服务。*LinkService* （第2.3节）是 *Face* 较上层的部分，它在网络层数据包和较低层数据包之间进行转换，并提供其他服务，例如分片、链路故障检测和重传。*LinkService* 包含一个分片器（ *fragmentation* ）和一个重组器（ *reassembly* ），以允许它执行分片和重组。



接收和发送的数据包在传递到 *forwarding*  或 在链路上发送之前分别通过 *LinkService* 和 *Transport* 。 *Transport* 收到数据包后，将通过调用`LinkService::receivePacket`函数将其传递到 *LinkService* 。当通过 *Face* 发送数据包时，它首先通过特定于数据包类型的函数（`Face::sendInterest`、`Face::sendData`或`Face::sendNack`）传递给 *LinkService* 。处理完数据包后，将通过调用`Transport::send`函数将其传递，或者如果已分片，则将其碎片传递到 *Transport* 。在 *LinkService* 和 *Transport* 中，使用远程端点ID（`Transport::EndpointId`）标识远程端点，该ID是64位无符号整数，其中包含每个远程主机的协议特定的唯一标识符。

