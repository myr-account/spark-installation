# spark-installation
## Instructions:
* Download Spark tar file to C: drive and untar the file
* Set Environmental variables for Spark
## Code:
```
// New RDD from Harry_potter.txt in Spark source directory
val textFile = sc.textFile("Harry_potter.txt")

// To find number of items in the RDD
textFile.count()

// To find the first item in the RDD
textFile.first()

// transformation filter applied to return a new RDD with a subset of the items in the file
val linesWithSpark = textFile.filter(line => line.contains("Darren"))

// To find the number of lines that contain "Darren"
val ct = textFile.filter(line => line.contains("Darren")).count()

// To find the line with most words in RDD
textFile.map(line => line.split(" ").size).reduce((a, b) => if (a > b) a else b)

// To find the largest line count
textFile.map(line => line.split(" ").size).reduce((a, b) => Math.max(a, b))

// Read the maximum words into maxwords
val maxWords = textFile.map(line => line.split(" ").size).reduce((a, b) => if (a > b) a else b)

// To maintain the key value pairs of word counts
val wordCounts = textFile.flatMap(line => line.split(" ")).map(word => (word, 1)).reduceByKey((a, b) => a + b)

// collect the word count in shell
wordCounts.collect()
```
## Visual Results:
* Excel document uploaded to visualize the data
## References:
* [https://spark.apache.org/downloads.html](https://spark.apache.org/downloads.html)
* [https://harrypotterfanfiction.com/printerfriendly.php?mode=chapter&object=512593](https://harrypotterfanfiction.com/printerfriendly.php?mode=chapter&object=512593)
* [https://github.com/denisecase/setup-spark.git](https://github.com/denisecase/setup-spark.git)

