# nasa-exoplanets-sql-explorer

This is an SQL project for exploring data from the NASA Exoplanet Archive.

## Data Source
NASA Exoplanet Archive: https://exoplanetarchive.ipac.caltech.edu

## Tools Used
- SQL
- PostgreSQL + pgAdmin


## The Questions that I am answering
**1. Which discovery method has found the most planets?**

```sql
SELECT discoverymethod,
    COUNT(discoverymethod)
FROM planets
GROUP BY discoverymethods
ORDER BY count DESC;
```

**Steps:**
- Selected the discovery method using a grouping statement to get the types of discovery methods used
- Use **COUNT** to get the number of planets found by each discovery method that is still utilizing the **GROUP BY** statement

**Answer:**
| discoverymethod | count |
| --------------- | ----- |










- How many planets haev a recorded mass but no recorded radius?
- Which year saw the most exoplanet discoveries?
- How many planets fall into each size category - Earth-sized, Super-Earth, Neptune-sized, and Jupiter-sized?
- Which planets are potentially in the habitable zone (orbital period between 200 and 500 days and radius less than 2 Earth radii)?

