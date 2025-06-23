# Mini-Project-PDF-Splitter 

## Usage
```mermaid
flowchart TD
    A(Start script) --> B{Run directly?}
    B -->|Yes| C[Ask for split page number]
    C --> D[Call split_pdf()]

    subgraph split_pdf Function
        D1{Output folder exists?}
        D1 -->|No| D2[Create output folder]
        D1 -->|Yes| D3[Open input PDF]
        D2 --> D3
        D3 --> D4[Count total pages]
        D4 --> D5{Is page number valid?}
        D5 -->|No| E1[Raise error and exit]
        D5 -->|Yes| D6[Init two PDF writers]
        D6 --> D7[Loop over pages]
        D7 --> D8{Before split page?}
        D8 -->|Yes| D9[Add to part1]
        D8 -->|No| D10[Add to part2]
        D9 --> D7
        D10 --> D7
        D7 -->|Done| D11[Save part1.pdf]
        D11 --> D12[Save part2.pdf]
        D12 --> D13[Print output paths]
    end

    D13 --> Z(End)





  



    


