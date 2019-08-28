#基本概念
1. producer : 生产者，也就是消息发送方。生产者负责创建消息，然后投递到kafka中
2. consumer : 消费者，也就是消息接收到一方。消费者链接到kafka，并拉取消息进行业务处理
3. Broker   : 服务代理节点，对于kafka而言，Broker可以看作是一个独立的kafka服务节点
4. Topic    : kafka中的消息是以Topic为单位进行归类归类，生产者负责将消息发送到特定Topic,而消费者负责订阅Topic并进行消费
5. Partition:Topic是一个逻辑上到概念，它还可以细化为多个Partition,一个Partition只能属于一个Topic;同一个Topic下不同Partition包含的消息是不同的
分区在存储层面可以看作一个可追加的日志文件，Partition可以分布在不同的Broker上，也就是说一个Topic可以横跨多个Broker。
6.offset    :offset是消息在Partition中的唯一标识，Kafka通过它来保证消息在Partition内的顺序性，不过offset并不跨越Partition
也就是说Kafka保证消息的Partition有序而不是Topic有序
7.Replica   :Kafka为Partition引入了副本机制，通过增加副本数量提升融灾能力，同一个Partition不同Replica
保存相同内容，副本之间是一主多从，Leader负责处理读写请求，follower只负责与Leader消息同步。
8.AR       : 分区中所有副本的统称（Assigned Replicas)
9.ISR      :所有与Leader副本保持在一定程度同步的副本（包括Leader副本）组成ISR（In-Sync Replicas)
10.OSR     :所有与Leader副本同步滞后过多的副本组成OSR（Out-of-Sync Replicas)


