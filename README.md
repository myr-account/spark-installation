# spark-installation
## Instructions:
* Download Spark tar file to C: drive and untar the file
* Set Environmental variables for Spark
## Code:
```
val textFile = sc.textFile("Harry_potter.txt")
textFile.count()
textFile.first()
val linesWithSpark = textFile.filter(line => line.contains("Darren"))
val ct = textFile.filter(line => line.contains("Darren")).count()
textFile.map(line => line.split(" ").size).reduce((a, b) => if (a > b) a else b)
textFile.map(line => line.split(" ").size).reduce((a, b) => Math.max(a, b))
val maxWords = textFile.map(line => line.split(" ").size).reduce((a, b) => if (a > b) a else b)
val wordCounts = textFile.flatMap(line => line.split(" ")).map(word => (word, 1)).reduceByKey((a, b) => a + b)
wordCounts.collect()
```
## References:
* [https://spark.apache.org/downloads.html](https://spark.apache.org/downloads.html)
* [https://harrypotterfanfiction.com/printerfriendly.php?mode=chapter&object=512593](https://harrypotterfanfiction.com/printerfriendly.php?mode=chapter&object=512593)
* [https://github.com/denisecase/setup-spark.git](https://github.com/denisecase/setup-spark.git)

