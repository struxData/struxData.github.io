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
Tree structure of downloaded MeetingBank
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

#### 1. MeetingBank.json
Splitted meeting segments from city council meetings. Each meeting segments along with a reference summary, transcripts and item type. We also release all URLs resources of meeting videos and agendas.
Each meeting is saved as dictionary:

```
<MeetingID>:
{   
    "URLs":{"Webpage":(str), "Video":(str), "MeetingDetail":(str)}, 
    "VideoDuration":(int), # Total meeting duration(sec)
    "Transcripts":(str) # Related transcripts file name
    "itemInfo":{<itemID>: \ 
    {"Summary", "transcripts", "type", "startTime", "endTime", "duration"}}
}
```

 **MeetingID**: {CityName}_{MeetingDate}. Eg: ***SeattleCityCouncil_12142015***

 **URLs** (dictionary) :
 - **Webpage** (string) : Link to meeting web page.

 - **Video** (string): Link to access or download video.

 - **MeetingDetail** (string) : Link to agenda items of current meeting.


 **itemInfo** (dictionary) : Includes all meeting items and related discussion segments.
 - **itemID** (string) : The ID of disccused items. For example, "CB 118549" is an Ordinance item ID from the City of Seattle. 

 - **Summary** (string): Reference-summary to summarize meeting segments.

 - **transcripts** (dictionary) : Text transcripts for each selected segments.

 - **type** (string) : Item type parsed from the city conucil agendas. Includes but limit to 'Ordinance', 'Clerk File', 'Agenda Item', 'Motion' and 'Resolution'.

 - **startTime** (int) : Segment start time in the meeting.

 - **endTime** (int) : Segment end time in the meeting.

 - **duration** (int) : Length of each meeting segments.


#### 2. Splits for training and evaluating summarizers perfomance
 We split our dataset into train, validation and test sets, containing 5169, 861, 862 instances respectively. Each summarizer is given the transcript of a meeting segment and tasked with generating a concise summary. 

<p align="center">
    <img src="/assets/data splits.png" alt="interface" style="width:70%; height:auto">
      <br>
</p>

The structure of data entry in split dataset

```
    {"id": (str), "source": (str), "summary": (str)}
```

**id** : In format of {MeetindID}_{itemID}.

**source** : Processed transcripts and each turns have been consolidated into one single paragraph.

**summary** : Reference summary.


#### 3. Abs&Ext Summaries

We evaluate state-of-the-art summarization systems on city council meetings, focusing on segments of the meetings rather than entire transcripts due to the length constraint imposed by abstractive summarizers.

For abstrcative summaries, we provide model generated summaries from 7 best performing neural abstractive summarizers. Including BART-Large, Pegasus, Longformer, DialogLM, HMNet and GPT-3 with zero-shot prompt. As for extractive summaries, we provide outputs by LEAD-3, Oracle and Lexrank algorithms. 


#### 4. Human Evaluation

We evaluate the performance of seven state-of-the-art summarization systems, including fine-tuned abstractive models **HMNet**, **BART**, **Pegasus**, **DialogLM**, **Longformer** and **GPT-3** with prompting, and traditional extractive models **LexRank** and **LEAD** to best assess the effectiveness of system-generated meeting summaries. All abstractive models have been fine-tuned on the train split of our city councils dataset to achieve the best possible results.

The workers are asked to watch a video segment, typically 30 minutes or less, read the transcript, and then evaluate the quality of each system summary based on five criteria: ***informativeness***, ***factuality***, ***fluency***, ***coherence***, and ***redundancy***.


#### 5. Speech-to-text meeting video transcripts

We use [Speechmatics.com](Speechmatics.com)'s speech-to-text API to automatically transcribe 3,579 hours of meetings, an order of magnitude larger than existing datasets. Our transcripts include word-level time alignment, casing, punctuation, and speaker diarization. . Filename format: `{audio_name}.json`. 

Each word in the transcript is annotated as a dictionary:
```
{“confidence”:(float), “duration”:(int),  “offset”:(int),  “text”:(string)}
```
where “confidence” indicates the STT confidence in the prediction, “duration” (unit:microsecond or 1e-6 second) is the duration of the transcribed word, “offset” (unit:microsecond or 1e-6 second) is the start time of the transcribed word in the full-length recording.
<!-- ## Reproducibility -->
