# MeetingBank:A Benchmark Dataset for Meeting Summarization
## Overview
As the number of recorded meetings increases, it becomes increasingly important to utilize summarization technology to create useful summaries of these recordings. However, there is a crucial lack of annotated meeting corpora for developing this technology, as it can be hard to collect meetings, especially when the topics discussed are confidential. Furthermore, meeting summaries written by experienced writers are scarce, making it hard for abstractive summarizers to produce sensible output without a reliable reference. This lack of annotated corpora has hindered the development of meeting summarization technology. In this paper, we present \emph{MeetingBank}, a new benchmark dataset of city council meetings over the past decade. \emph{MeetingBank} is unique among other meeting corpora due to its divide-and-conquer approach, which involves dividing professionally written meeting minutes into shorter passages and aligning them with specific segments of the meeting. This breaks down the process of summarizing a lengthy meeting into smaller, more manageable tasks. The dataset provides a new testbed of various meeting summarization systems and also allows the public to gain insight into how council decisions are made. We will make the collection, including meeting videos, transcripts, reference summaries, agendas, and other metadata, publicly available in order to facilitate the development of better meeting summarization techniques.


## Acknowledgement
Yebowen Hu, Tim Ganter, Hanieh Deilamsalehy, Franck Dernoncourt, Hassan Foroosh, Fei Liu

In main conference of Association for Computational Linguistics (ACL'23), Toronto, Canada.


## Dataset
Dataset preprocessing and results reproduce utilities code repository: [MeetingBank_Utils](https://github.com/YebowenHu/MeetingBank)

## License

This website is powered by [Jekyll](https://jekyllrb.com/) with [al-folio](https://github.com/alshedivat/al-folio) theme and is hosted by [GitHub Pages](https://pages.github.com/).
