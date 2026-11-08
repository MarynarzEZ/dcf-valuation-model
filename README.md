# DCF Valuation Model (Excel)

An automated discounted cash flow (DCF) model for companies listed on the Warsaw Stock Exchange (GPW), designed for typical production companies. Enter a company code, refresh the workbook, and the model imports the financial statements and share price from BiznesRadar, proposes forecast assumptions from history, and calculates a value per share.

**[Download the template (DCF_Model_Template.xlsm)](DCF_Model_Template.xlsm?raw=true)**

The file is an empty template: it contains no company data until you run the import.

## Features

- **Automated import** with Power Query: financial statements and the latest share price from BiznesRadar
- **10-year history** with margins, investment and leverage ratios
- **5-year FCFF forecast** with model-proposed assumptions; the analyst can override any of them
- **WACC build-up** using CAPM, with cost of debt as the risk-free rate plus a synthetic-rating credit spread
- **Terminal value** based on long-term growth, with an optional mid-year cash flow convention
- **Sensitivity table** of value per share across WACC and long-term growth
- **18 automated checks** covering data quality, consistency of assumptions and whether the data belong to the selected company
- **VBA macro for switching companies**: entering a new code clears the previous company's inputs, confirms the code and refreshes the data

## Workbook structure

| Sheet | Purpose | User input |
| --- | --- | --- |
| Start | Results summary, guide and glossary | None |
| Import | Company selection and data download | Company name and code, confirmation of assumptions |
| Raw_Data | Statements as published | None (hidden, fills automatically) |
| Clean_Data | Statements converted to numbers | None (hidden) |
| Mapping | Links statement items to model lines | Only when Checks shows MISSING (hidden) |
| History | 10 years of key data and ratios | None (hidden) |
| Assumptions | WACC and 5-year forecast | Share count, risk-free rate, beta, ERP; optional overrides |
| DCF | FCFF forecast and value per share | None |
| Sensitivity | Value at other WACC and growth levels | Optional table steps |
| Checks | Automated validation tests | None |

## How to use

Requires desktop Excel with Power Query. When opening the file, click **Enable Content** to allow the macro and the data connections.

1. On **Import**, enter the company name and its BiznesRadar code (the last part of the company's page address, e.g. `WAWEL`).
2. Click **Data → Refresh All** (Ctrl+Alt+F5).
3. On **Assumptions**, fill in the orange cells: shares outstanding, risk-free rate, beta and equity risk premium. Override the model's proposals if needed.
4. Enter the company code in **Import!C9** to confirm the assumptions belong to this company.
5. Check that **Checks** shows no errors, then read the result on **Start** or **DCF**.

With macros enabled, changing the code on **Import** triggers the macro, which handles steps 2 and 4 and clears the previous company's inputs. You then only need to enter the share count and beta. Market-wide inputs such as the risk-free rate and ERP are kept.

Amounts are in PLN thousands, as published on BiznesRadar.

## Limitations

- Built for production companies; banks, insurers and similar businesses need a different approach.
- The result depends heavily on the assumptions, especially WACC and long-term growth.
- The import relies on the layout of BiznesRadar pages and may need adjusting if they change.

## Disclaimer

This is a portfolio project for educational purposes and is not investment advice. Financial data belongs to its respective providers and is not included in this repository.

## Author

Karol Słotwiński, [GitHub](https://github.com/MarynarzEZ)
