# spark-installation
## Instructions:
* Download Spark tar file to C: drive and untar the file
* Set Environmental variables for Spark
## Code:

* New RDD from Harry_potter.txt in Spark source directory <br/>
``` val textFile = sc.textFile("Harry_potter.txt") ```

* To find number of items in the RDD <br/>
``` textFile.count() ```

* To find the first item in the RDD <br/>
``` textFile.first() ```

* transformation filter applied to return a new RDD with a subset of the items in the file <br/>
``` val linesWithSpark = textFile.filter(line => line.contains("Darren")) ```

* To find the number of lines that contain "Darren" <br/>
``` val ct = textFile.filter(line => line.contains("Darren")).count() ```

* To find the line with most words in RDD <br/>
``` textFile.map(line => line.split(" ").size).reduce((a, b) => if (a > b) a else b) ```

* To find the largest line count <br/>
``` textFile.map(line => line.split(" ").size).reduce((a, b) => Math.max(a, b)) ```

* Read the maximum words into maxwords <br/>
``` val maxWords = textFile.map(line => line.split(" ").size).reduce((a, b) => if (a > b) a else b) ```

* To maintain the key value pairs of word counts <br/>
``` val wordCounts = textFile.flatMap(line => line.split(" ")).map(word => (word, 1)).reduceByKey((a, b) => a + b) ```

* collect the word count in shell <br/>
``` wordCounts.collect() ```

* sorted word counts <br/>
``` val sort = wordCounts.sortBy(_._2,false); ```

* writing to a file <br/>
``` def writingToAFile(f: java.io.File)(i: java.io.PrintWriter => Unit) { val p = new java.io.PrintWriter(f); try { i(p) } finally { p.close() } } ```

* top 10 words from the sorted data <br/>
``` val topWords = sort.take(10);  ```

* import from java.io; <br/>
``` import java.io._; ```

* collect the dta to visual_data.txt <br/>
``` writingToAFile(new File("C:/visual_data.txt")) { p => topWords.foreach(p.println) } ```

## Visual Results:
* Excel document uploaded to visualize the data
## References:
* [https://spark.apache.org/downloads.html](https://spark.apache.org/downloads.html)
* [https://harrypotterfanfiction.com/printerfriendly.php?mode=chapter&object=512593](https://harrypotterfanfiction.com/printerfriendly.php?mode=chapter&object=512593)
* [https://github.com/denisecase/setup-spark.git](https://github.com/denisecase/setup-spark.git)

