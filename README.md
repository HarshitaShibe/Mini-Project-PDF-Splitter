# Mini-Project-PDF-Splitter 

## Usage
```mermaid
flowchart TD
    A[Start Script] --> B[Check if __name__ == "__main__"]
    B --> C[Prompt user for split page number]
    C --> D[Call split_pdf(input_pdf, output_dir, split_page)]

    subgraph split_pdf Function
        D1[Check if output_dir exists]
        D1 -->|No| D2[Create output_dir]
        D1 -->|Yes| D3[Open input PDF using PdfReader]
        D3 --> D4[Count total pages]
        D4 --> D5[Validate split_page range]
        D5 -->|Invalid| E1[Raise ValueError]

        D5 -->|Valid| D6[Initialize two PdfWriter objects]
        D6 --> D7[Loop through all pages]
        D7 --> D8{page_num < split_page?}
        D8 -->|Yes| D9[Add page to part1_writer]
        D8 -->|No| D10[Add page to part2_writer]
        D9 --> D7
        D10 --> D7

        D7 -->|Done| D11[Write part1.pdf to disk]
        D11 --> D12[Write part2.pdf to disk]
        D12 --> D13[Print output file paths]
    end

    D13 --> Z[End]




    


