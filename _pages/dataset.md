---
layout: page
permalink: /dataset/
title: Dataset
description: 
nav: true
nav_order: 2
---

## Public Meetings
The release MeetingBank dataset includes 1,366 meetings from six cities or municipalities spanning over a decade, including [Seattle, Washington](https://seattle.legistar.com/Calendar.aspx); [King County, Washington](https://mkcclegisearch.kingcounty.gov/Calendar.aspx); [Denver, Colorado](https://denver.legistar.com/Calendar.aspx); [Boston, Massachusetts](https://boston.legistar.com/Calendar.aspx); [Alameda, California](https://alameda.legistar.com/Calendar.aspx); and [Long Beach, California](https://longbeach.legistar.com/DepartmentDetail.aspx?ID=2474&GUID=28A20A62-2645-436E-B1E5-1D5D9B9D25EB&Mode=MainBody).

## Dataset
```
.
├── LICENSE_ANNOTATIONS_ADOBE_RESEARCH_LICENSE.txt
├── LICENSE_AUDIO.csv
├── README.txt
├── Metadata
│   ├── MeetingBank.json
│   ├── Splits
│   ├── AbstractiveSummaries
│   ├── ExtractiveSummaries
│   └── HumanEvaluation
└── Audio&Transcripts
    ├── Seattle
    ├── KingCounty
    ├── Denver
    ├── Boston
    ├── Alameda
    └── LongBeach
```

### Metadata:
#### MeetingBank.json
Splitted meeting segments from city council meetings. Each meeting segments along with a reference summary, transcripts and item type. We also release all URLs resources of meeting videos and agendas.
Each meeting is saved as dictionary:

```
{   
    "URLs":{"Webpage":(str), "Video":(str), "MeetingDetail":(str)}, 
    "VideoDuration":(int), # Total meeting duration(sec)
    "Transcripts":(str) # Related transcripts file name
    "itemInfo":{<itemID>:{"Summary", "transcripts", "type", "startTime", "endTime", "duration"}}
}
```

'itemID' is the ID of disccused items. For example, "CB 118549" is an Ordinance item ID from the City of Seattle. 

#### Splits for training and evaluating summarizers perfomance
 We split our dataset into train, validation and test sets, containing 5169, 861, 862 instances respectively. Each summarizer is given the transcript of a meeting segment and tasked with generating a concise summary. 

|train | test| dev|
|:-----|:-----|:-----|
|5169|861|862|


#### Abs&Ext Summaries
We evaluate state-of-the-art summarization systems on city council meetings, focusing on segments of the meetings rather than entire transcripts due to the length constraint imposed by abstractive summarizers.
For extractive summaries, our method included the Oracle, LEAD, LexRank and TextRank. 
As for abstrcative summaries, we provide five best performing neural abstractive summarizers. Including BART-Large, Pegasus, Longformer, DialogLM and HMNet, 

## Data Splits

## Reproducibility


## Dataset

PodcastFillers dataset contains audio files and metadata. Tree structure of the PodcastFillers dataset:

### Metadata:
##### 1. Speech-to-text meeting video transcripts
Speech transcript in JSON format for each podcast episode. Generated using the [SpeechMatics STT](https://www.speechmatics.com/). Filename format: `{show name}_{episode name}.json`. 

Each word in the transcript is annotated as a dictionary:
```
{“confidence”:(float), “duration”:(int),  “offset”:(int),  “text”:(string)}
```
where “confidence” indicates the STT confidence in the prediction, “duration” (unit:microsecond or 1e-6 second) is the duration of the transcribed word, “offset” (unit:microsecond or 1e-6 second) is the start time of the transcribed word in the full-length recording.

##### 2. MeetingBank.csv
