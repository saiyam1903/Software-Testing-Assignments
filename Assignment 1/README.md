# Assignment 1

Created Use-case and Sequence diagram using PLantUML tool.

## 1. Sequence Diagram using PlantUML

### Diagram

![alt text](https://github.com/errpv78/Software-testing/blob/main/Assignment1/SequenceDiagram.png?raw=true)

### Code
```
@startuml SequenceDiagram
title Scene Depiction in Videos for Blind
actor User as A
participant VoiceAgent as B
participant VideoPlayer as C
participant CaptionGenerator as D
autonumber
->A: Initializtion
A->B: Input_Video
B->C: Validate Video

alt Valid video
    C->B: Valid Input
    B->A: Video Loaded Successfully
else else
    C->B: Invalid Input
    B->A: Error
end

C->C: Display_video
A->B: Voice Command
B->C: Voice to Function
C->C: Video Functions
C->D: Generate Caption
D->B: Caption
B->A: Caption to Audio
@enduml
```

## 2. Use-case Diagram using PlantUML

### Diagram
![alt text](https://github.com/errpv78/Software-testing/blob/main/Assignment1/UseCaseDiagram.png?raw=true)

### Code

```
@startuml UseCaseDiagram

skinparam actorStyle awesome
actor User as U
actor "Third party Video Source" as V
left to right direction
skinparam packageStyle rectangle

rectangle "Video Captioning Web App" {
(Upload Video) as uploadVideo
(Network Error) as networkError
(Enter URL) as enterUrl
(URL not found Error) as urlError
(Select user type) as selectUT
(Change user type) as changeUT
(Select interaction type) as selectIT
(Change interaction type) as changeIT
(Adjust Video Player Settings) as adjustVPS
(Command Not Found) as cnf
(Ask for help) as help
(Play instruction file) as insFile
}

uploadVideo <.. networkError : extend
enterUrl  <.. urlError : extend
selectUT <.. changeUT  : extend
selectIT <.. changeIT : extend
adjustVPS <.. cnf : extend
help ..> insFile : include

U -- uploadVideo
U -- enterUrl
U -- selectUT
U -- selectIT
U -- adjustVPS
U -- help

enterUrl --> V 

@enduml
```
