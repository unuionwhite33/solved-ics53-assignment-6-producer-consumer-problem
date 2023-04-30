Download Link: https://assignmentchef.com/product/solved-ics53-assignment-6-producer-consumer-problem
<br>
The producer-consumer problem is a well-known problem in concurrent programming.

In this assignment, you will implement an extension of this problem using the POSIX Threads library and you would need to synchronize executions of the threads to have the program working properly.




<h2>Project Specifications</h2>

<strong> </strong>

We have two kinds of threads: producers and consumers. In this assignment there can be many producers and consumers. Each producer and each consumer must execute in a different thread. A producers’ job is to produce items and put them into a bounded buffer. A consumer’s job is to remove items from the buffer. The buffer can hold 8 items. There are the following constraints on how producers and consumers can access the buffer.

<ol>

 <li>Only one thread can access the buffer at a time.</li>

 <li>A producer cannot write into the buffer if it is full.</li>

 <li>A consumer cannot read from the buffer if it is empty.</li>

</ol>




<h3>        –    Producer Behavior</h3>




<ul>

 <li>Each producer will have an associated producer number, ​<strong>n</strong>​, which is an integer from ​0​ to ​p-1​, where ​<strong>p</strong>​ is the number of producers.</li>

 <li>Each producer will produce a series of items and place each item in the buffer.</li>

 <li>Producers will not produce items in an infinite loop. Instead, each producer will produce only ​<strong>i </strong>​ After a producer thread has produced i items and placed them in the buffer, the producer thread will terminate.</li>

 <li>Each item produced is an integer between ​(n * i)​ and ​((n+1) * i – 1)​. This ensures that the items produced by all producers are unique; no two producers ever produce the same item.</li>

 <li>When a producer produces an item, it prints​ “producer_​<strong><em>n</em></strong>​ ​produced item <strong><em>item_value</em></strong>​” ​. The term ​n​ in the printed output should be replaced with the producer number, and the term ​item_value​ should be replaced with the item value.</li>

</ul>




<h3>        –    Consumer Behavior</h3>




<ul>

 <li>Each consumer will have an associated consumer number, ​<strong>m</strong>​, which is an integer from ​0​ to ​c-1​, where ​<strong>c</strong>​ is the number of consumers.</li>

 <li>Each consumer will remove items from the buffer.</li>

 <li>Consumers will not produce items in an infinite loop. Instead, each consumer will consume only ​(p*i)/​<strong>c </strong>​ After a consumer thread has consumed (p*i)/​<strong>c</strong>​ items, the consumer thread will terminate.</li>

 <li>When a consumer consumes an item, it prints​ “consumer_​<strong><em>m</em></strong>​ ​consumed item <strong><em>item_value</em></strong>​” ​. The term ​m​ in the printed output should be replaced with the consumer number, and the term ​item_value​ should be replaced with the item value.</li>

</ul>




<h3>        –    Delays</h3>




In order to demonstrate the behavior of the system under different conditions, you will add delays to the producer and consumer threads using the ​usleep()​ function. There will be two options for the insertion of delays. In the first option, a 0.5 second delay will be added to each producer thread immediately after it adds an item to the buffer. This will greatly slow down the rate of production. In the second option, a 0.5 second delay will be added to each consumer thread immediately after it removes an item from the buffer. The choice between these two delay options will be made by a command-line argument passed to your program.




<h3>        –    Command-Line Arguments</h3>




Your program will accept 4 command-line arguments which specify parameters of the producer-consumer system.

<ul>

 <li><strong>p</strong>​ – The number of producers. This must be between 1 and 16.</li>

 <li><strong>c</strong>​ – The number of consumers. This must be between 1 and 16. The number of consumers should always be smaller than the number of total items being produced (i.e. ​c &lt; p*i​).</li>

 <li><strong>i</strong>​ – The number of items produced by each producer.</li>

 <li><strong>d</strong> – The selection of the delay option. If d = 0 then the delay will be added to the​ producer threads,and if d = 1 then the delay will be added to the consumer threads.</li>

</ul>


