# Mini-Project-PDF-Splitter 

## Usage
```mermaid
flowchart TB
    Start([Start Script])
    Check{Is script run directly?}
    Input[Prompt for split page number]
    Call[Call split_pdf function]

    DirCheck{Does output folder exist?}
    CreateDir[Create output folder]
    OpenPDF[Open input PDF]
    CountPages[Count total pages]
    Validate{Is split page valid?}
    Error[Raise ValueError and exit]
    InitWriters[Initialize two PdfWriter objects]
    LoopPages[Loop through all pages]
    CheckPage{Page before split point?}
    AddPart1[Add page to part1_writer]
    AddPart2[Add page to part2_writer]
    SavePart1[Write part1.pdf]
    SavePart2[Write part2.pdf]
    PrintPaths[Print output paths]
    End([End Script])

    Start --> Check
    Check -->|Yes| Input
    Input --> Call
    Call --> DirCheck
    DirCheck -->|No| CreateDir --> OpenPDF
    DirCheck -->|Yes| OpenPDF
    OpenPDF --> CountPages
    CountPages --> Validate
    Validate -->|No| Error
    Validate -->|Yes| InitWriters
    InitWriters --> LoopPages
    LoopPages --> CheckPage
    CheckPage -->|Yes| AddPart1 --> LoopPages
    CheckPage -->|No| AddPart2 --> LoopPages
    LoopPages --> SavePart1
    SavePart1 --> SavePart2
    SavePart2 --> PrintPaths
    PrintPaths --> End







  



    


