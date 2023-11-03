**Chapter 3 Review Questions**

## SECTIONS 3.1–3.3 

**R3. Consider a TCP connection between Host A and Host B. Suppose that the TCP segments traveling from Host A to Host B have source port number *x* and destination port number *y*. What are the source and destination port numbers for the segments traveling from Host B to Host A?**

> source port numbers: y
>
>  destination port number: x



**R7. Suppose a process in Host C has a UDP socket with port number 6789. Suppose both Host A and Host B each send a UDP segment to Host C with destination port number 6789. Will both of these segments be directed to the same socket at Host C? If so, how will the process at Host C know that these two segments originated from two different hosts?**

> Yes, both segment will be directed to the same socket at Host C.
>
> Distinguish based on source IP



目标IP和目标port一样，被定义为相同的socket

回传的时候，根据不同IP回传

![image-20231101155547827](assets\image-20231101155547827.png)



## SECTION 3.4

**R9. In our rdt protocols, why did we need to introduce sequence numbers?**

> Sequence number can help us to find 
>
> - whether the arriving packet is a retransmission or new data
> - determine the order of the data packet is correct.



**R10. In our rdt protocols, why did we need to introduce timers?**

> To handle packet loss problem:
>
> after the sender sends the packet, it starts the timer. If no ACK is received before the time expires, it will retransmit to prevent packet loss.



## SECTION 3.5

**R14. True or false?**

**a. Host A is sending Host B a large file over a TCP connection. Assume Host B has no data to send Host A. Host B will not send acknowledgments to Host A because Host B cannot piggyback the acknowledgments on data.**

> F. If B does not send any data to A, B will send a separate confirmation to A



**b. The size of the TCP rwnd never changes throughout the duration of the connection.**

> F. The size of the receive window is set based on the available space of the cache. The cache space changes over time, so the size of the receive window also changes.
>
> size=接收缓存-主机B中已经接收但是未读取的数据量



**c. Suppose Host A is sending Host B a large file over a TCP connection. The number of unacknowledged bytes that A sends cannot exceed the size of the receive buffer.**

> T.

不会超过buffer，更不会超过free buffer



**d. Suppose Host A is sending a large file to Host B over a TCP connection. If the sequence number for a segment of this connection is *m*, then the sequence number for the subsequent segment will necessarily be *m* + 1.**

> F
>
> TCP connections are byte numbers, and the sequence number of subsequent message segments is m + the number of bytes in the segment.

以字节为变化，而不是以segment

TCP连接为字节编号，后续报文段的序号为m+该段字节数量



e. The TCP segment has a field in its header for rwnd.

> T
>

receive window

![image-20231102193349212](assets\image-20231102193349212.png)

f. Suppose that the last SampleRTT in a TCP connection is equal to 1 sec. The current value of TimeoutInterval for the connection will necessarily be  1 sec.

> F

渐渐下降

![image-20231101161414425](assets\image-20231101161414425.png)

是要多个采样值的平均

![image-20231102193546412](assets\image-20231102193546412.png)

**g. Suppose Host A sends one segment with sequence number 38 and 4 bytes of data over a TCP connection to Host B. In this same segment, the acknowledgment number is necessarily 42.**

> F.
>
> If B does not successfully receive the 38 message segment, then the confirmation number is 38



**R15. Suppose Host A sends two TCP segments back to back to Host B over a TCP connection. The first segment has sequence number 90; the second has sequence number 110.**

![image-20231101161716705](assets\image-20231101161716705.png)

**a. How much data is in the first segment?**

> 110-90=20 bytes

**b. Suppose that the first segment is lost but the second segment arrives at B. In the acknowledgment that Host B sends to Host A, what will be the acknowledgment number?**

> 90 . ACK is the last byte received sequentially + 1, which is the byte number expected to be received.（ACK为顺序收到的最后一个字节+1，即为期待收到的字节号）



![image-20231102193754930](assets\image-20231102193754930.png)

![image-20231102193814849](assets\image-20231102193814849.png)

## Problems

P1. Suppose Client A initiates a Telnet session with Server S. At about the same time, Client B also initiates a Telnet session with Server S. Provide possible source and destination port numbers for

assume at A port number: x, at B port number: y

a. The segments sent from A to S.

source: x

destination:  23 

b. The segments sent from B to S.

source: y

destination: 23

c. The segments sent from S to A.

source: 23

destination: x 

d. The segments sent from S to B.

source: 23

destination: y

e. If A and B are different hosts, is it possible that the source port number in the segments from A to S is the same as that from B to S?

yes. 

we can use IP address to distinguish A and B.

f. How about if they are the same host?

no. 

with the same port and IP, we cannot distinguish them



**P3. UDP and TCP use 1s complement for their checksums.** 

Suppose you have the following three 8-bit bytes: 

01010011, 01100110, 01110100. 

What is the 1s complement of the sum of these 8-bit bytes? (Note that although UDP and TCP use 16-bit words in computing the checksum, for this problem you are being asked to consider 8-bit sums.) Show all work. 

Why is it that UDP takes the 1s complement of the sum; that is, why not just use the sum? 

With the 1s complement scheme, how does the receiver detect errors? Is it possible that a 1-bit error will go undetected? How about a 2-bit error?

![image-20231102194303327](assets\image-20231102194303327.png)



P8. Draw the FSM for the receiver side of protocol rdt3.0.





P15. Consider the cross-country example shown in Figure 3.17. How big would the window size have to be for the channel utilization to be greater than 98 percent? Suppose that the size of a packet is 1,500 bytes, including both header fields and data







P23. Consider the GBN and SR protocols. Suppose the sequence number space is of size *k*. What is the largest allowable sender window that will avoid the occurrence of problems such as that in Figure 3.27 for each of these protocols?





P24. Answer true or false to the following questions and briefly justify your answer:

a. With the SR protocol, it is possible for the sender to receive an ACK for a packet that falls outside of its current window.

b. With GBN, it is possible for the sender to receive an ACK for a packet that falls outside of its current window.

c. The alternating-bit protocol is the same as the SR protocol with a sender and receiver window size of 1.

d. The alternating-bit protocol is the same as the GBN protocol with a sender and receiver window size of 1.





P27. 

Host A and B are communicating over a TCP connection, and Host B has already received from A all bytes up through byte 126. Suppose Host A then sends two segments to Host B back-to-back. The first and secondsegments contain 80 and 40 bytes of data, respectively. In the first segment, the sequence number is 127, the source port number is 302, and the destination port number is 80. Host B sends an acknowledgment whenever it receives a segment from Host A.

a. In the second segment sent from Host A to B, what are the sequence number, source port number, and destination port number?

b. If the first segment arrives before the second segment, in the acknowledgment of the first arriving segment, what is the acknowledgment number, 

the source port number, and the destination port number?

c. If the second segment arrives before the first segment, in the acknowledgment of the first arriving segment, what is the acknowledgment number?

d. Suppose the two segments sent by A arrive in order at B. The first acknowledgment is lost and the second acknowledgment arrives after the first timeout interval. Draw a timing diagram, showing these segments and all other segments and acknowledgments sent. (Assume there is no additional packet loss.) For each segment in your figure, provide the sequence number and the number of bytes of data; for each acknowledgment that you add, provide the acknowledgment number.







P32. Consider the TCP procedure for estimating RTT. Suppose that α = 0.1. Let SampleRTT1 be the most recent sample RTT, let SampleRTT2 be the next most recent sample RTT, and so on.

a. For a given TCP connection, suppose four acknowledgments have been returned with corresponding sample RTTs: SampleRTT4, SampleRTT3, SampleRTT2, and SampleRTT1. Express EstimatedRTT in terms of the four sample RTTs.

b. Generalize your formula for *n* sample RTTs.

c. For the formula in part (b) let *n* approach infinity. Comment on why this 

averaging procedure is called an exponential moving average.





P40. Consider Figure 3.61. Assuming TCP Reno is the protocol experiencing the behavior shown above, answer the following questions. In all cases, you should provide a short discussion justifying your answer.

a. Identify the intervals of time when TCP slow start is operating.

b. Identify the intervals of time when TCP congestion avoidance is operating.

c. After the 16th transmission round, is segment loss detected by a triple 

duplicate ACK or by a timeout?

d. After the 22nd transmission round, is segment loss detected by a triple duplicate ACK or by a timeout?

e. What is the initial value of ssthresh at the first transmission round?

f. What is the value of ssthresh at the 18th transmission round?

g. What is the value of ssthresh at the 24th transmission round?

h. During what transmission round is the 70th segment sent?

i. Assuming a packet loss is detected after the 26th round by the receipt of a triple duplicate ACK, what will be the values of the congestion window size and of ssthresh?

j. Suppose TCP Tahoe is used (instead of TCP Reno), and assume that triple duplicate ACKs are received at the 16th round. What are the ssthreshand the congestion window size at the 19th round?

k. Again suppose TCP Tahoe is used, and there is a timeout event at 22nd round. How many packets have been sent out from 17th round till 22nd round, inclusive?





P45. Consider Figure 3.54. Suppose that at *t* 3, the sending rate at which congestion loss next occurs drops to 0.75**W*max (unbeknownst to the TCP senders, of course). Show the evolution of both TCP Reno and TCP CUBIC for two more rounds each *(Hint: note that the times at which TCP Reno and TCP* CUBIC react to congestion loss may not be the same anymore).*





P53. 

Consider the network described in the previous problem. Now suppose that the two TCP connections, C1 and C2, have the same RTT of 100 msec. Suppose that at time t0, C1’s congestion window size is 15 segments but C2’s congestion window size is 10 segments.

a. What are their congestion window sizes after 2200 msec?

b. In the long run, will these two connections get about the same share of the 

bandwidth of the congested link?

c. We say that two connections are synchronized, if both connections reach 

their maximum window sizes at the same time and reach their minimum 

window sizes at the same time. In the long run, will these two connec

tions get synchronized eventually? If so, what are their maximum window 

sizes?

d. Will this synchronization help to improve the utilization of the shared 

link? Why? Sketch some idea to break this synchronization.

