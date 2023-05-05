Download Link: https://assignmentchef.com/product/solved-ece253-homework-1
<br>
Reading: Read the Vivado Getting Started and MicroBlaze References, and the papers by Lee and Tennenhouse.

<h1>Problems</h1>

<ol>

 <li>Caches are very commonly used to improve the average performance of processors by providing a small, fast memory for often reused portions of program of data. The issue with a cache is that when the needed program fragment is not present in the cache, the processor waits while the data is fetched. Finally, for simplicity and overall performance, the replacement often is a small cache-line of 32 or 64 bytes. In this problem, you are to make measurements augmenting a program to model the timing of processor memory accesses. Note: You need a C compiler for this problem. If you do not have one on your local machine, you can make use of the digilab machines. Please refer to the ‘Compiling C on Linux’ note on Gauchospace for instructions on compiling your code using the command line. On windows, you can download free Visual Studio for full IDE support although many people choose the simple mingw package supporting gcc on windows.

  <ul>

   <li>An access to main memory takes a fixed setup of 7 cycles plus 1 cycle for each sequential word, reads to random addresses must again pay the setup overhead.</li>

   <li>The cache access is 1 cycle if the data is in the cache, and if not, it reads an 8-word cache line from the main memory (taking same time as a processor access to main memory), then an additional 2 cycles to update and respond to the read. As part of the update, some line in the cache is overwritten.</li>

   <li>When the cache is disabled, a single buffer of 4 sequential words stores the result of the previous memory read.</li>

   <li>The model assumes 16-bit address for words and a cache size of 256 lines, each line consisting of 8 words.</li>

  </ul></li>

</ol>

A program for the model (in C) will be provided, you should use this model and write C code that interfaces to this, providing addresses and gathering statistics.

<ul>

 <li>Determine the expected access time with cache enabled and disabled, given random reads of the 16-bit memory space.</li>

 <li>Assuming that:</li>

</ul>

s=0.6 is the probability that the next address follows the current one, p=0.35 is the probability that the next address is not sequential but is within 40 words

(either direction) of the current one,

thus 0.05 is the probability of a random far address, determine the expected values for access time with cache enabled and disabled.

1

<ul>

 <li>What is the worst case access time for the memory?</li>

 <li>For the data gathered in parts (a) and (b) above, plot Cumulative Distribution Functions (CDFs). (CDFs plot the cumulative probability vs. the range of observations). Based on the CDFs, what are the confidence limits on your data? Estimate the fraction of time for which the memory access time is less than the worst case access time calculated in part (c). Why is this hard to estimate in a real system?</li>

</ul>

Hint: The distributions you will find above hardly meet Gaussian (normal) statistics. A classic method to find the expectation of accuracy of a measurement that does not require normal statistics is re-sampling. The idea is to do experiment, say for 1000 address trials, and determine the expectation. Then redo the experiment a few dozen times – each time you should get a new expectation that isnt too different but indicates the uncertainty of the measurement. In practice, you can do this by randomly sampling the original measurement (when data is expensive to generate).

<ol start="2">

 <li>A hand mixer is to be run by a grand loop controller on a small microcontroller. The following tasks must be run, each taking a certain amount of time:</li>

</ol>

<table width="392">

 <tbody>

  <tr>

   <td width="55">Task</td>

   <td width="157">Description</td>

   <td width="105">Time to Run</td>

   <td width="76">Deadline</td>

  </tr>

  <tr>

   <td width="55">Ctrl</td>

   <td width="157">Control Calculations</td>

   <td width="105">9 ms</td>

   <td width="76">24 ms</td>

  </tr>

  <tr>

   <td width="55">Torq</td>

   <td width="157">Torque Check</td>

   <td width="105">3 ms</td>

   <td width="76">18 ms</td>

  </tr>

  <tr>

   <td width="55">Temp</td>

   <td width="157">Temperature Check</td>

   <td width="105">3 ms</td>

   <td width="76">30 ms</td>

  </tr>

  <tr>

   <td width="55">UI</td>

   <td width="157">User Interface</td>

   <td width="105">5 ms</td>

   <td width="76">30 ms</td>

  </tr>

 </tbody>

</table>

<ul>

 <li>What is the utility of the system?</li>

</ul>

In practice, the grand loop time is fixed by the fact that we can only switch power at the zero crossing of the mains voltage. Given 60 Hz mains and 2 zero crossings per cycle, this gives a loop time of 8 ms, i.e., reads and writes can occur every 8 ms. The deadline for each task is timed between consecutive writes of that task. Every write should be preceded by a read and complete execution of the task. Task execution can also be broken into any number of non-contiguous segments.

<ul>

 <li>Show a valid schedule with an 8 ms loop time. What is the period of execution for each task?</li>

 <li>What is the processor utility under this schedule?</li>

</ul>

Assuming the mixer is successful in the US market, it is desired to introduce it to the European market. Given 50 Hz mains, the loop cycle time will be 10 ms:

<ul>

 <li>Show that it is no longer possible to find a schedule under the above assumptions.</li>

 <li>Given this, the torque check task is re-written so as to raise the deadline to 20 ms while still maintaining adequate safety. A schedule should now be possible. Find a schedule that works.</li>

 <li>What is the utility of that schedule? Is it higher or lower than the 60 Hz / 8 ms schedule?</li>

</ul>