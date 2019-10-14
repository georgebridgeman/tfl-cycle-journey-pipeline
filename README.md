## Logstash pipeline for ingesting Transport For London cycle journey data
Transport For London (TFL) publish data on all journeys made by the 'Boris Bikes'. This data is useful for experimenting with Elasticsearch queries. As there is a high number of journeys, the dataset also makes a good training set for shard-related tasks.

### Usage
An environment variable called `CYCLE_CSV_PATH` is required for Logstash to know where to check for source data. The value should be a directory and glob pattern that will match the CSV files from TFL.

Once this environment variable is set, invoke Logstash:

```
logstash -f tfl-cycle-journey-pipeline.conf
```

The default output is an Elasticsearch node on `10.0.200.101`, as set up in my Elasticsearch training lab repository.

### Downloading source data
The source data is available from [TFL](https://cycling.data.tfl.gov.uk/). The bike usage data is in the `usage-stats` directory.

There is, generally, one file per week. Download as many files as you would like to ingest and place them into the path defined in `$CYCLE_CSV_PATH`. It may be best to focus on a certain month and year, and download several files for that period.
