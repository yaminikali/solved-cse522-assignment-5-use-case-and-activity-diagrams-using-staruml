Download Link: https://assignmentchef.com/product/solved-cse522-assignment-5-use-case-and-activity-diagrams-using-staruml
<br>
<strong><em>Part 1: Use-Case and Activity Diagrams using StarUML          </em></strong>

You are to develop an ‘external view’ of an Online Forum application described briefly below.

The Online Forum caters to three main categories of Users – Students, TAs, and Professor<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a>– each with different privileges.  TAs and the Professor are collectively referred to as Staff.   The Online Forum supports three types of Posts:  a Q&amp;A Post, a Poll Post, and a Resource Post.  Staff may make all three types of Posts, but Students may only make a Q&amp;A Post and a Poll Post.   As the focus of this assignment is on the external view of the application, the internal details of these posts are not relevant in this assignment.

All Users must login to use the Online Forum; they may logout at any time but must login back again in order to take any actions.  Initially, the Professor logs in and creates the class which includes enrolling the TAs and Students.  Only after the class is created may Students and TAs login and activate their accounts – activation to be done only once, at the start of the semester.

During the course of the semester, Students, TAs, and the Professor all operate concurrently relative to one another in taking their actions on the Online Forum.  However, each User operates sequentially in taking their individual actions.  Each User may make any number of Posts (of the permitted types) and in any order.   As noted above, a user may logout at any time, but must login back again before any further other action can be taken.

Finally, the Online Forum maintains statistics on the usage of the online forum, such as average response time for queries, numbers of posts made by users, etc.   All activity in the Online Forum ends at the end of the semester.

<ul>

 <li><strong><em>What to Represent in the Use-Case Diagram.</em></strong></li>

</ul>

<ul>

 <li>The Users to be represented are: Student, TA, Professor, Staff, User, and OnlineForum. <em> </em></li>

</ul>

<ul>

 <li>The Actions to be represented are: Login, Logout, Activate, Post, Q&amp;A Post, Poll Post, Resource Post, Create Class, Enroll Students, Enroll Staff, and Maintain Statistics<em>. </em></li>

</ul>

<ul>

 <li>‘Generalization’ arrows are to be used to depict relevant relations between different types of Users. Similarly forActions.   Draw these arrows pointing upwards or slanted upwards.</li>

</ul>

<ul>

 <li>‘Directed Association’ arrows are to be used in relating Users with their Actions. Draw these arrows pointing sideways or slanted upwards/downwards</li>

</ul>

<ul>

 <li>‘<strong>&lt;&lt;</strong><em>includes</em><strong>&gt;&gt;</strong><em>’</em> arrows are to be used in relating Actions where appropriate.</li>

</ul>

<ul>

 <li><strong><em>What to Represent in the Activity Diagram.</em></strong></li>

 <li>Introduce three swim lanes, for Student, TA, and Professor Within each swim lane, define the control flow for the permitted actions for that type of user. <em> </em></li>

 <li>The Actions to be represented are: Login, Logout, Activate, Q&amp;A Post, Poll Post, Resource</li>

</ul>

Post, Create Class<em>.  </em>

<ul>

 <li>Introduce one initial node and one final node for the entire diagram.</li>

</ul>

<ul>

 <li>Use Fork/Join nodes (in Professor) to initiate/terminate concurrent operation of all users. Termination takes place at the end of the semester.   Note that each user takes their individual actions in a sequential manner.</li>

</ul>

<ul>

 <li>Use Decision and Merge nodes to construct an iterative flow of control within the Student, TA, and Professor swim lanes. To the extent possible, use vertical and horizontal arrows in depicting flow of control.  Slanted arrows are permissible – StarUML also allows an arrow to have more than one segment (bend).  <em> </em></li>

</ul>

<em> </em>

<ul>

 <li>Show ‘end of semester’ as a constraint on the outgoing edge of appropriate decision nodes.</li>

</ul>

<strong><em>Finally: </em></strong>

Save your model as a file OnlineForum.mdj.  The suffix mdj is automatically added by StarUML

<strong><em>Important Note: </em></strong>

Points will be deducted for sloppily drawn use-case and activity diagrams.  Hence pay attention to drawing and aesthestics, as noted in the instructions above.  Strive for symmetric diagrams with minimal line crossings to the extent possible – some asymmetry and line crossings are acceptable.

<a href="#_ftnref1" name="_ftn1">[1]</a> Assume there is only one Professor for the course, although online forums such as Piazza allow more than one Professor.

<strong><em>Part 2:  Communicating State Charts </em></strong>

Download and unzip A5_Part2.zip.  It has four files:  Circular_Buffer.mdj,

Circular_Buffer.java, Circular_Buffer.txt, and MessagePassing.jar.

File Circular_Buffer.mdj contains a <strong><em>StarUML State Chart</em></strong> (reproduced above) giving the outline of the controller for a circular buffer.  This buffer is accessed by two <em>concurrent</em> processes, Producer and Consumer, who communicate with the buffer controller using two <em>channels, </em>put and get.  The producer repeatedly does a put! and the consumer similarly does a get?, and the buffer controller performs the respective complementary operations.




File Circular_Buffer.java contains the outline of a Java implementation of the above state chart using the <strong><em>Message Passing Library</em></strong> discussed in Lecture 15 – examples were posted in Sample Programs →  MessagePassingExamples.zip.   The file gives the main program (class Driver), the classes Producer and Consumer, and also the outline of class Circular_Buffer.




Class Circular_Buffer uses an integer array, data, of size n in order to hold its data.  It has a field count that gives, at any given time, the number of values that can be taken out of the buffer.  It also has two indices p and g to point, respectively, to the places in the array where the next value is to be put by the producer and taken out by the consumer.  These indices are incremented (modulo n) as put/get operations take place.   The actual insertion and retrieval of values are performed by two methods put() and get() respectively.




<strong><em>What you should do: </em></strong>




<ol>

 <li>Complete the state chart mdj by providing suitable labels on the <strong><em>four transitions</em></strong> shown.   Each label is of the form <strong><em>event [ guard ] / action</em></strong> –   Lecture 26 includes a demo on how to construct StarUML State Charts.   These labels should collectively express the synchronization policy of the buffer controller, namely, that:</li>

</ol>




(i) when the buffer is empty (count == 0) only a put operation is permitted; (ii) when the buffer is full (count == n) only a get operation is permitted; (iii) otherwise, both put and get are permitted – the selection is non-deterministic.







In specifying the <em>transition labels</em> in <strong><em>StarUML</em></strong>:




<ul>

 <li>each <strong><em>event</em></strong> is a channel send/receive, and is specified as a <em>Trigger Event</em>;</li>

 <li>each <strong><em>guard</em></strong> is a boolean expression and specified in the <em>Properties</em> section; and</li>

 <li>each <strong><em>action</em></strong> is a call on one of the methods put() or get(), and specified as an <em>Effect Behavior </em>→<em> OpaqueBehavior</em>.</li>

</ul>




<ol start="2">

 <li>Complete the run() method in class Circular_Buffer providing an implementation of the above synchronization policy. As the state chart specifies that the buffer controller operates in a repetitive cycle, the top level of the run() method should be a while(true) {…}</li>

</ol>




In Eclipse, right-click on the project, then select <em>Build Path </em>→<em> Configure Build Path </em>→<em> Add External JAR </em>→<em> browse and select </em>MessagePassing.jar.




Run the completed program under JIVE after adding Scheduler.* to <em>Debug Configurations </em>→<em> JIVE </em>→<em> Exclusion Filter</em>.  Check that the <em>Console</em> output shows the strings Put 1, …, Put 50 as well as Get 1, …, Get 50.   The ‘Put’ and ‘Get’ strings will not be in strict alternation, but their respective values should be in ascending order – this property is to be checked as specified below.




Save the <em>Execution Trace</em> in a file, Circular_Buffer.csv, and load it into the <em>Property Checker</em>:




<ul>

 <li>Add op and Driver.val to the <em>Key Attributes</em>.</li>

 <li>Enter op = op, Driver.val=val in the <em>Abbreviations</em> textbox.</li>

 <li>Choose Method Granularity – this is important.</li>

 <li>Copy the contents of the file txt into the <em>Properties</em> textbox. – Press <em>Validate</em> and check that all properties are satisfied; otherwise, the program has an error which needs to be corrected.</li>

</ul>