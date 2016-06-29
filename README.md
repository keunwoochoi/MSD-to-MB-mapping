# MSD-to-MB-mapping
Million Song Dataset to MusicBrainz (AcousticBrainz) mapping files

#### These are not mine
These files are just a copy of files that are kindly provided from [AcousticBrainz labs](http://labs.acousticbrainz.org/million-song-dataset-mapping/). This repo is just a redundant source of the same files and all the credits go to AcousticBrainz labs. 
According to the original page,
> We currently have a mapping for about 250,000 MSD IDs, resulting in 370,000 matches (because a MSD ID may map to more than one MusicBrainz ID).

Please let me know if hosting this might cause any problem. 

#### How to use
After cloning,
> cat msd-mbid-2016-01-results.json.bz2.gz.a? | gunzip > msd-mbid-2016-01-results.json.bz2
to merge and get `msd-mbid-2016-01-results.json.bz2`. Then,
> bzip2 -d *.bz2
and that's it.

#### Source code
They used [this code](https://github.com/MTG/acousticbrainz-labs/tree/master/msdtombid) to get these files. 

Below is also copied & pasted from the official distribution.

#### Files

* msd-mbid-2016-01-abz-mbids.csv.bz2 (33M): A unique list of MusicBrainz IDs present in AcousticBrainz at the time of the matching
* msd-mbid-2016-01-results.json.bz2 (195M): A mapping of MSD IDs and metadata to Recordings in MusicBrainz
* msd-mbid-2016-01-results-ab.json.bz2 (60M): The same mapping file, containing MBIDs only present in AcousticBrainz (filtered with the first file)
* msd-mbid-2016-01-results-ab.csv.bz2 (13M): The AB mapping file in CSV format, with simplified metadata

#### File Format

```
{
  "query": { // MSD metadata used for the query
    "song_id": "SOTUGDX12A8C13E5F7",
    "title": "Aground",
    "artist_name": "Fresh Moods",
    "track_id": "TRMRLVN128F42AA35E",
    "release": "Exhale",
    "duration": "377.02485",
    "artist_mbid": "cba5dbef-14f8-47a7-8632-a63e7a9738e2"
  },
  "match": [ // A list of all results from MusicBrainz which match on artist id and title
    {
      "length": 375000,
      "title": "Aground",
      "id": "eb301e57-5c6d-49a4-bb0d-2d963ca5a59b",
      "releases": [ // Releases on which this recording appears. Could be more than 1
        {
          "id": "24e38551-44ab-4aed-81c6-b60447dbfd0d",
          "title": "Campari Lounge II"
        }
      ],
      "artists": [ // Artists from MusicBrainz. Could be more than 1
        {
          "id": "cba5dbef-14f8-47a7-8632-a63e7a9738e2",
          "name": "Fresh Moods"
        }
      ]
    },
    {
      "length": 380026,
      "title": "Aground",
      "id": "47ce77c9-9296-4bc3-a878-7390a3303e0c",
      "releases": [
        {
          "id": "6ca97f9c-b764-4c98-b512-3ddf6e51db79",
          "title": "Exhale"
        }
      ],
      "artists": [
        {
          "id": "cba5dbef-14f8-47a7-8632-a63e7a9738e2",
          "name": "Fresh Moods"
        }
      ]
    }, //... More matches
  ],
  "matchtypes": { // Some data about how the MusicBrainz data matches the MSD data
    "duration": "withindur",
    "release": "",
    "type": "exact"
  }
}
```
