# MongoDB Quick Reference

## Connect to Mongo Shell

    mongo --host mongodb-rs3.ksl.com
    
## Date Range Query

    db.auto.find({
        createTime: {
            $gte: ISODate("2010-04-29T00:00:00.000Z"),
            $lt: ISODate("2010-05-01T00:00:00.000Z")
        }
    })

## Epoch Date

Get the date in seconds since the epoch by connecting to the mongo shell and running the following.

    new Date(2013,03,08)*1;
    
Note that the month (03) is zero based. "03" is April not March.

## Export JSON Data

Run the mongoexport command line utility with arguments like the following. Note that the date must be in seconds since the epoch (see above how to use mongo to generate it).

    mongoexport \
      --host mongodb-rs3.ksl.com \
      --db classifieds \
      --collection auto \
      --query '{state:"ID", createTime: {$gte: new Date(1365400800000), $lt: new Date(1366005600000)}}' \
      --out "/tmp/id.csv"

## Export CSV Data

Run the mongoexport command line utility with arguments like the following. Note that the date must be in seconds since the epoch (see above how to use mongo to generate it).

    mongoexport \
      --host mongodb-rs3.ksl.com \
      --db classifieds \
      --collection auto \
      --query '{state:"ID", createTime: {$gte: new Date(1365400800000), $lt: new Date(1366005600000)}}' \
      --type csv \
      -- fields id,city,state,createTime \
      --out "/tmp/id.csv"
