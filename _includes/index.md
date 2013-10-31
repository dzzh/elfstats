##About 

It is vitally important for web site administrators to constantly monitor the state of their systems. One of the ways to do it is by using data contained in the access logs of web servers. There exist many very different commercial and open-source tools used to extract and represent these data nowadays (see e.g. [Apache Log Viewer](http://www.apacheviewer.com), [wtop](https://github.com/ClockworkNet/wtop), [Sawmill](http://www.sawmill.net), [logstash](http://logstash.net), [Loggly](http://loggly.com)). Many of such tools can effectively work with the data that is the same in all setups, like IP addresses or response codes, but they do not usually provide efficient ways to aggregate the information contained in the processed requests with fine granularity, as the requests structure differs per each deployed application.

**Elfstats** is a set of tools aimed not to replace all the available access log monitoring solutions (well, at least in coming ten years), but rather provide the system engineers with flexible aggregation and reporting of information contained in the requests processed by their servers. As it was said before, the requests differ per each application, thus elfstats has to be configured to track specific requests structure in advance. This is done by means of regular expressions that can be as generic or fine-grained as needed.

Elfstats code is written in Python programming language and can be installed either together with the other Python packages or completely separately in an own directory. Elfstats works with Linux operating system (its compatibility with other POSIX-based OSes has not been tested yet) and can be installed either from the source codes or from a set of RPM packages.

##Features

* Ability to work with any [ELF-compatible](http://en.wikipedia.org/wiki/Extended_Log_Format) access log file after copying the format setting from the web server's configuration.
* Ability to process several different log files simultaneously.
* Ability to work with in-place and time-based rotating log files. 
* Adjustable time interval for data aggregation.
* Regex-based configuration of requests needed to be and not to be tracked.
* Combining the requests into groups and tracking them together.
* Regex-based extraction and aggregation of specific patterns occurring in the requests.
* Small codebase and clear architecture that allows to extend and change the functionality with ease.
* Free and open-source.

##Tracked data

* The total number of requests and slow requests per each defined group.
* Response times statistics, aggregated separately per each request group. Such metrics as min/max/avg latencies and user-defined percentiles are reported.
* The number of responses per response code -- in total and for each request group separately.
* For each user-specified pattern -- the number of occurrences in total and the number of distinct items matching the pattern.
* The total number of log records processed by elfstats as well as the number of intentionally skipped and erroneous records.

##Structure

So far elfstats consists of two main components, namely an aggregation backend and a presentation layer. The backend is implemented in a form of a Linux daemon called [elfstatsd][]. This daemon invokes once in a specified time interval, reads log records from the configured log files that were added since the daemon's previous run, processes them and writes the results into the report files.

After the data is aggregated and saved, it can be used as the input source by many different monitoring solutions. By now, however, only [Munin] is used for elfstats data visualization. [elfstats-munin][] repository contains a number of Munin plugins that read the data from the report files generated by *elfstatsd* and convert it into Munin-recognizable format. Several different plugins are available. Each of them can be turned on or off to better fit the administrator's needs. These plugins are very simple and allow for easy extension and change. They are based on [PyMunin][] framework. 

To simplify elfstats deployment for the system engineers not familiar with Python and/or operating web servers with restricted access (e.g. not allowing to download required dependencies from the Internet), an optional [elfstats-env][] infrastructural repository is maintained. It contains a Python virtual environment set up to work with elfstats. It can be installed prior to the other elfstats components. However, you are free not to use it and install elfstats the way you want.

The [elfstats][] repository is aimed to be the all-in-one umbrella repository for the project's development. So far it only contains the sources of this web site, but in near future it will include all the repositories listed above as its submodules and will contain build scenarios for all-in-one elfstats installation. 

##Okay, got it. What's next?

If you want to try elfstats, you need to install its components in the following order:

* [elfstats-env][] (optional)
* [elfstatsd][]
* [elfstats-munin][]

The detailed installation instructions are provided in the readme files of the respective repositories. The readme's also contain basic configuration guides.

You can also refer to [elfstatsd wiki](https://github.com/dzzh/elfstatsd/wiki) for configuration guide and report format specification and to [elfstats-munin wiki](https://github.com/dzzh/elfstats-munin/wiki) for the description of the available plugins.

##Support

If you have troubles with deploying or configuring elfstats, you may [file an issue](https://github.com/dzzh/elfstatsd/issues) desribing your problem at the issue tracker or [contact a maintainer](mailto:zmicier.zaleznicenka@gmail.com) directly via email. Feel free to share your thoughts and suggestions to improve the project!

[elfstats]: https://github.com/dzzh/elfstats
[elfstats-env]: https://github.com/dzzh/elfstats-env
[elfstatsd]: https://github.com/dzzh/elfstatsd
[elfstats-munin]: https://github.com/dzzh/elfstats-munin
[Munin]: http://munin-monitoring.org
[PyMunin]: http://aouyar.github.io/PyMunin/