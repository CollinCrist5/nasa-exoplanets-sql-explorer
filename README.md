# nasa-exoplanets-sql-explorer

This is an SQL project for exploring data from the NASA Exoplanet Archive.

### Data Source
NASA Exoplanet Archive: https://exoplanetarchive.ipac.caltech.edu

### Tools Used
- SQL
- PostgreSQL + pgAdmin


### The Questions that I am answering
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
|    | discoverymethod | count |
| ----- | --------------- | ----- |
|1| Transit | 4640 |
|2| Radial Velocity | 1180 |
|3| Microlensing | 278 |
|4| Imaging | 97 |
|5| Transit Timing Variations | 40 |
|6| Eclipse Timing Variations | 17 |
|7| Orbital Brightness Modulation | 9 |
|8| Pulsar Timing | 8 |
|9| Astrometry | 6 |
|10| Pulsation Timing Variations | 2 |
|11| Disk Kinematics | 1 |

- Transit discovery method found 4640 exoplanets.
- Radial Velocity discovery method found 1180 exoplanets.
- Microlensing discovery method found 278 exoplanets.
- Imaging discovery method found 97 exoplanets.
- Transit Timing Variations discovery method found 40 exoplanets.
- Eclipse Timing Variations discovery method found 17 exoplanets.
- Orbital Brightness Modulation discovery method found 9 exoplanets.
- Pulsar Timing discovery method found 8 exoplanets.
- Astrometry discovery method found 6 exoplanets.
- Pulsation Timing Variations discovery method found 2 exoplanets.
- Disk Kinematics discovery method found 1 exoplanets.

###
**2. How many planets have a recorded mass but no recorded radius?**

```sql
SELECT COUNT(pl_bmasse)
FROM planets
WHERE pl_rade IS NULL;
```
**Steps:**
- Selected how many planets have a recorded mass where their radius is also NULL

**Answer:**
|   |  pl_bmasse |
| --| ---------- |
| 1 | 1571 |

- There were 1,571 exoplanets that have a recorded mass but no recorded radius.

**Extra**
- I wanted to see which exoplanets didn't have a recorded radius while having a recorded mass

```sql
SELECT pl_names
FROM planets
WHERE pl_rade IS NULL AND pl_bmasse IS NOT NULL;
```
**Answer:**

|   |  pl_name |
| --| ---------- |
| 1 | 11 Com b |
| 2 | 11 UMi b |
| 3 | 14 And b |
...
| 1570 | ups Leo b |
| 1571 | xi Aql b |

###
3. Which year saw the most exoplanet discoveries?
- How many planets fall into each size category - Earth-sized, Super-Earth, Neptune-sized, and Jupiter-sized?
- Which planets are potentially in the habitable zone (orbital period between 200 and 500 days and radius less than 2 Earth radii)?

