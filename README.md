[![License: GPL v2](https://img.shields.io/badge/License-GPL%20v2-blue.svg)](https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html)

# FBA Data Repository
This repository contains the segment annotations, assessments and other metadata of student performances for the Florida all-state auditions. The dataset is available on request from the Florida Bandmasters Association (FBA).

## Usage
This repository is meant to be used with the [MIG-MusicPerformanceAnalysis repository](https://github.com/GTCMT/MIG-MusicPerformanceAnalysis) and both should be cloned at the same folder level. 
There are additional intermediate representations such as pitch contours which are pre-computed and stored at [provide link](https://dummy.link). To obtain those follow the steps below:
1. Go the [provide link](https://dummy.link) and download the folder titled `FbaData`.
2. Copy the folder and paste it at the same folder level as this repository.
3. Select 'Paste and Merge' when prompted. 

The downloaded 'FbaData' folder from the previous link should be merged with this cloned repository before it can be used. 

## Dataset Description
The data set contains student recordings for 18 different instruments covering the instrument groups woodwind, brass, and percussion. The performances are assessed by expert judges in different categories. The data is anonymized - personal identification of students and judges is impossible.

## Folder Structure
The folder structure is shown below: 

`MIG-FbaData`

    --> `FBA2013` 
    
        --> `bandname.xlsx` : this excel sheet contains the tabulated assessments for all students for a particular band. The band could be middle school, concert band, or symphonic band.
        
        --> `bandname` : folder, for a particular band
        
            --> `student-id` : folder, for a particular student. student-id is a 5 digit number. contains annotations for the student. individual files are described in the section 'Annotations & Metadata' is this readme
            
        --> `midiscores` : folder, contain the scores that the students are performing instrument wise in midi format
        ...
        ...
    
    --> `FBA2014`
        ...
        ...
    ...
    ...

## Annotations & Metadata
Each student-id folder contains the following annotations and metadata files:

### *_assessments.txt
Contains the judge assessments of a student's audition. Students were assessed in different categories (ex. note accuracy) and separately for different segments of the audition (ex. technical etude). Assessments are normalized to [0,1], and -1 indicates a missing assessment. The assessments are organized into a 10 x 26 matrix where rows represent segments and columns represent categories:

Rows (10 segments):
1. lyricalEtude
2. technicalEtude
3. scalesChromatic
4. scalesMajor
5. sightReading
6. malletEtude
7. snareEtude
8. timpaniEtude
9. readingMallet
10. readingSnare

Columns (26 categories):
1. articulation
2. artistry
3. musicalityTempoStyle
4. noteAccuracy
5. rhythmicAccuracy
6. toneQuality
7. articulationStyle
8. musicalityPhrasingStyle
9. noteAccuracyConsistency
10. tempoConsistency
11. Ab
12. A
13. Bb
14. B
15. C
16. Db
17. D
18. Eb
19. E
20. F
21. Gb
22. G
23. chromatic
24. musicalityStyle
25. noteAccuracyTone
26. rhythmicAccuracyArticulation

### *_instrument.txt
Contains the played instruments (ex. snare drum) and their corresponding activities (ex. etude). The data is formatted as a N*2 matrix, N is the number of segments. The first column is the instrument name (str) represented by the first three letters (ex. xylophone as xyl, snare drum as sna). The second column is the activity name (str), which shares the same pool as the 26 categories described above. 
Instrument ids:
bcl	Bb Clarinet
tru	Trumpet
tsa 	Tenor Saxophone
flu 	Flute
axs 	Alto Saxophone
frh	French Horn
obo 	Oboe
sna	snare drum
xyl	xylophone
tim	timpani

### *_segment.txt
Contains the starting time (in sec) and duration (in sec) of every segment. The data is formatted as a N*2 matrix, N is the number of segments. The first column is the starting time, and the second column is the duration. 

### *_pyin_pitchtrack.txt
Contains the extracted [pYin](https://code.soundsoftware.ac.uk/projects/pyin) pitch contour for each student recording organized as a N*2 matrix, where N is the number of frames into which the recording is split. The 1st column is the timestamp of the frame in seconds and the 2nd column is the extracted f0 (fundamental frequency) in Hz. (Note that these files are commited to the repository and can be obtained by following the steps listed under the Usage section of this readme).

## Contact
---
Alexander Lerch
alexander.lerch@gatech.edu

Georgia Tech Center for Music Technology
840 McMillan Street
Atlanta, GA 30332
