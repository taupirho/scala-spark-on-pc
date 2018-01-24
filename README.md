<h3>Setting up your PC for SCALA/Spark development and running your first code</h3>

Carry out the following steps to create a SCALA/SPARK/HADOOP development environment on your 
local windows PC. Note that it won't be a proper version of HADOOP we'll install, rather
we will fool your PC into thinking there's a real version of HADOOP installed that will enable
you to submit SPARK jobs to run.

<h4>Install the JAVA development kit</h4>

SCALA compiles down to JAVA byte code and is able to take advantage of existing
JAVA libraries therefore we need to install a JAVA development kit. You can get
this from www.oracle.com. Choose the latest version appropriate to you operating
system, download it and follow the installation instructions.

<h4>Install SPARK</h4>

You can get a pre-built version of SPARK from spark.apache.org. Make sure you
get one pre-built for Hadoop. It will download in a .tgz format which is a UNIX
type compressed format which windows will unlikely recognise off the bat. If so,
there is a utility called WinRAR which you can download from
[www.rarlab.com](http://www.rarlab.com) which will read this kind of file. Once
you’ve downloaded and unzipped the .tgz file copy the unzipped contents to
somewhere like c:\\spark on your PC.

<h4>Install winutils.exe</h4>

We need to trick windows into thinking that HADOOP is installed on it and to do
this there is a program called winutils.exe that you need to download and
install onto your PC. Search for it on Google and make sure it’s virus free
before installing it. Create a directory c:\\winutils\\bin on your PC and copy
the winutils.exe program to that location. You don’t run it explicitly, it will
run as and when needed.

<h4>Set-up some environment variables</h4>

The following environment variables now need to be set up


|Variable  |Value
|----------|-----------------------|
|SPARK_HOME|SPARK install directory e.g c:\\spark
|JAVA_HOME |JAVA JDK install directory e.g c:\\program files\\java\\jdk1.8
|HADOOP_HOME|bin directory where winutils.exe lives in e.g c:\\winutils



Lastly you need to amend your PATH environment variable and add the following to
it.

%SPARK_HOME%\\bin

%JAVA_HOME%\\bin

Install a SCALA IDE

There are a number to choose from but the one I use is based on Eclipse. You can
get it from www.scala-ide.org. Again just download the zip, uncompress it and
copy its contents to, for example, c:\\eclipse

To check that the Spark installation is OK, go to wherever you installed  Spark,
open up a command window and type in spark-shell. After a minute or so you
should see something similar to this:

![](https://github.com/taupirho/scala-spark-on-pc/blob/master/scala.png)

If you don’t see this then something has gone wrong and you should re-visit all
the steps described above and make sure all is OK with them. Similarly for the
IDE, just go to where the eclipse.exe lives and double click on it. If its the
first time running it, you should see an eclipse launcher window appear
prompting you to select a development workspace, otherwise the normal eclipse
IDE window will appear.

Now, for our very first SPARK/SCALA program we will do a simple wordcount
program on a text file. Handily, the c:\\spark sub-directory has an existing
file we can use called README.md. If you type this file from a DOS command
window you can see its contents. Now, make sure you are in the c:\\spark
directory and type spark-shell. Once you have the SCALA\> prompt, type in the
following lines of code:

scala\> val rdd = sc.textFile("README.md")


rdd: org.apache.spark.rdd.RDD[String] = README.md MapPartitionsRDD[1] at textFile at \<console\>:24

scala\> rdd.count()

res0: Long = 99

scala\>:quit

There you go, it shows the file has 99 lines and you just ran your first Spark/Scala code !


