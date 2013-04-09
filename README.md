= C++ Word Count MapReduce example with Hadoop Streaming with CDH4 =

== Requisites ==
* Apache Hadoop from CDH4 (http://www.cloudera.com/content/support/en/documentation/cdh4-documentation/cdh4-documentation-v4-latest.html)
* g++, autoconf, automake, make

== Quick Run ==
```bash
git clone http://github.com/QwertyManiac/cdh4-hadoop-streaming-cpp.git
cd cdh4-hadoop-streaming-cpp/
./run.sh
```

== Build ==
* Run ``build.sh`` in the top-directory, or follow below.
* Run following commands:
```bash
aclocal
autoreconf -f -i -Wall,no-obsolete
./configure
make
```

== Run ==
* Run ``run.sh`` in the top-directory, or follow below.
* Run the following commands:
```bash
hadoop fs -put src/string_split.cc input.txt
hadoop fs -rm -r output
hadoop jar /usr/lib/hadoop-0.20-mapreduce/contrib/streaming/hadoop-streaming-*.jar -file ./src/word_count_mapper -mapper ./word_count_mapper -file ./src/word_count_reducer -reducer ./word_count_reducer -input input.txt -output output
```