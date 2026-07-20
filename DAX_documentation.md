# DAX Documentation — bank_loan_data_insights.pbix

## 1. DAX Measures (table_measures)

| Measure Name | DAX Expression |
|---|---|
| `total_loan_appl` | `count(financial_loan[id])` |
| `MTD_loan_appl` | `CALCULATE(TOTALMTD([total_loan_appl], 'Date Table'[Date]))` |
| `PMTD_loan_appl` | `CALCULATE([total_loan_appl],DATESMTD(DATEADD('Date Table'[Date],-1,MONTH)))` |
| `MOM_loan_appl` | `([MTD_loan_appl]-[PMTD_loan_appl])/[PMTD_loan_appl]` |
| `total_funded_amt` | `sum(financial_loan[loan_amount])` |
| `MTD_funded_amt` | `CALCULATE(TOTALMTD([total_funded_amt], 'Date Table'[Date]))` |
| `PMTD_funded_amt` | `CALCULATE([total_funded_amt],DATESMTD(DATEADD('Date Table'[Date],-1,MONTH)))` |
| `MOM_funded_amt` | `([MTD_funded_amt]-[PMTD_funded_amt])/[PMTD_funded_amt]` |
| `total_received_amt` | `sum(financial_loan[total_payment])` |
| `MTD_received_amt` | `CALCULATE(TOTALMTD([total_received_amt], 'Date Table'[Date]))` |
| `PMTD_received_amt` | `CALCULATE([total_received_amt],DATESMTD(DATEADD('Date Table'[Date],-1,MONTH)))` |
| `MOM_received_amt` | `([MTD_received_amt]-[PMTD_received_amt])/[PMTD_received_amt]` |
| `avg_interest_rate` | `AVERAGE(financial_loan[int_rate])` |
| `MTD_interest_rate` | `CALCULATE(TOTALMTD([avg_interest_rate], 'Date Table'[Date]))` |
| `PMTD_Interest_rate` | `CALCULATE([avg_interest_rate],DATESMTD(DATEADD('Date Table'[Date],-1,MONTH)))` |
| `MOM_interest_rate` | `([MTD_interest_rate]-[PMTD_Interest_rate])/[PMTD_Interest_rate]` |
| `avg_DTI` | `AVERAGE(financial_loan[dti])` |
| `MTD_avg_DTI` | `CALCULATE(TOTALMTD([avg_DTI], 'Date Table'[Date]))` |
| `PMTD_avg_DTI` | `CALCULATE([avg_DTI],DATESMTD(DATEADD('Date Table'[Date],-1,MONTH)))` |
| `MOM_avg_DTI` | `([MTD_avg_DTI]-[PMTD_avg_DTI])/[PMTD_avg_DTI]` |
| `good_loan_per` | `(CALCULATE([total_loan_appl],financial_loan[Good vs Band Loan] = "Good Loan")) / [total_loan_appl]` |
| `good_loan_appl` | `(CALCULATE([total_loan_appl], financial_loan[Good vs Band Loan]="Good Loan"))` |
| `good_loan_funded_amt` | `(CALCULATE([total_funded_amt], financial_loan[Good vs Band Loan]="Good Loan"))` |
| `good_loan_received_amt` | `(CALCULATE([total_received_amt], financial_loan[Good vs Band Loan]="Good Loan"))` |
| `bad_loan_per` | `(CALCULATE([total_loan_appl],financial_loan[Good vs Band Loan] = "Bad Loan")) / [total_loan_appl]` |
| `bad_loan_appl` | `(CALCULATE([total_loan_appl], financial_loan[Good vs Band Loan]="Bad Loan"))` |
| `bad_loan_funded_amt` | `(CALCULATE([total_funded_amt], financial_loan[Good vs Band Loan]="Bad Loan"))` |
| `bad_loan_received_amt` | `(CALCULATE([total_received_amt], financial_loan[Good vs Band Loan]="Bad Loan"))` |

### Full measure definitions

**total_loan_appl**
```DAX
total_loan_appl = count(financial_loan[id])
```

**MTD_loan_appl**
```DAX
MTD_loan_appl = CALCULATE(TOTALMTD([total_loan_appl], 'Date Table'[Date]))
```

**PMTD_loan_appl**
```DAX
PMTD_loan_appl = CALCULATE([total_loan_appl],DATESMTD(DATEADD('Date Table'[Date],-1,MONTH)))
```

**MOM_loan_appl**
```DAX
MOM_loan_appl = ([MTD_loan_appl]-[PMTD_loan_appl])/[PMTD_loan_appl]
```

**total_funded_amt**
```DAX
total_funded_amt = sum(financial_loan[loan_amount])
```

**MTD_funded_amt**
```DAX
MTD_funded_amt = CALCULATE(TOTALMTD([total_funded_amt], 'Date Table'[Date]))
```

**PMTD_funded_amt**
```DAX
PMTD_funded_amt = CALCULATE([total_funded_amt],DATESMTD(DATEADD('Date Table'[Date],-1,MONTH)))
```

**MOM_funded_amt**
```DAX
MOM_funded_amt = ([MTD_funded_amt]-[PMTD_funded_amt])/[PMTD_funded_amt]
```

**total_received_amt**
```DAX
total_received_amt = sum(financial_loan[total_payment])
```

**MTD_received_amt**
```DAX
MTD_received_amt = CALCULATE(TOTALMTD([total_received_amt], 'Date Table'[Date]))
```

**PMTD_received_amt**
```DAX
PMTD_received_amt = CALCULATE([total_received_amt],DATESMTD(DATEADD('Date Table'[Date],-1,MONTH)))
```

**MOM_received_amt**
```DAX
MOM_received_amt = ([MTD_received_amt]-[PMTD_received_amt])/[PMTD_received_amt]
```

**avg_interest_rate**
```DAX
avg_interest_rate = AVERAGE(financial_loan[int_rate])
```

**MTD_interest_rate**
```DAX
MTD_interest_rate = CALCULATE(TOTALMTD([avg_interest_rate], 'Date Table'[Date]))
```

**PMTD_Interest_rate**
```DAX
PMTD_Interest_rate = CALCULATE([avg_interest_rate],DATESMTD(DATEADD('Date Table'[Date],-1,MONTH)))
```

**MOM_interest_rate**
```DAX
MOM_interest_rate = ([MTD_interest_rate]-[PMTD_Interest_rate])/[PMTD_Interest_rate]
```

**avg_DTI**
```DAX
avg_DTI = AVERAGE(financial_loan[dti])
```

**MTD_avg_DTI**
```DAX
MTD_avg_DTI = CALCULATE(TOTALMTD([avg_DTI], 'Date Table'[Date]))
```

**PMTD_avg_DTI**
```DAX
PMTD_avg_DTI = CALCULATE([avg_DTI],DATESMTD(DATEADD('Date Table'[Date],-1,MONTH)))
```

**MOM_avg_DTI**
```DAX
MOM_avg_DTI = ([MTD_avg_DTI]-[PMTD_avg_DTI])/[PMTD_avg_DTI]
```

**good_loan_per**
```DAX
good_loan_per = (CALCULATE([total_loan_appl],financial_loan[Good vs Band Loan] = "Good Loan")) / [total_loan_appl]
```

**good_loan_appl**
```DAX
good_loan_appl = (CALCULATE([total_loan_appl], financial_loan[Good vs Band Loan]="Good Loan"))
```

**good_loan_funded_amt**
```DAX
good_loan_funded_amt = (CALCULATE([total_funded_amt], financial_loan[Good vs Band Loan]="Good Loan"))
```

**good_loan_received_amt**
```DAX
good_loan_received_amt = (CALCULATE([total_received_amt], financial_loan[Good vs Band Loan]="Good Loan"))
```

**bad_loan_per**
```DAX
bad_loan_per = (CALCULATE([total_loan_appl],financial_loan[Good vs Band Loan] = "Bad Loan")) / [total_loan_appl]
```

**bad_loan_appl**
```DAX
bad_loan_appl = (CALCULATE([total_loan_appl], financial_loan[Good vs Band Loan]="Bad Loan"))
```

**bad_loan_funded_amt**
```DAX
bad_loan_funded_amt = (CALCULATE([total_funded_amt], financial_loan[Good vs Band Loan]="Bad Loan"))
```

**bad_loan_received_amt**
```DAX
bad_loan_received_amt = (CALCULATE([total_received_amt], financial_loan[Good vs Band Loan]="Bad Loan"))
```

## 2. Calculated Columns

**financial_loan[Good vs Band Loan]**
```DAX
Good vs Band Loan = SWITCH(
	TRUE,
	ISBLANK('financial_loan'[loan_status]),
	"(Blank)",
	'financial_loan'[loan_status] IN {"Charged Off"},
	"Bad Loan",
	'financial_loan'[loan_status] IN {"Current",
		"Fully Paid"},
	"Good Loan",
	'financial_loan'[loan_status]
)
```

**DateTableTemplate_2874bb78-d6e0-4e83-ba49-1e8e734c0b72[Year]**
```DAX
Year = YEAR([Date])
```

**DateTableTemplate_2874bb78-d6e0-4e83-ba49-1e8e734c0b72[MonthNo]**
```DAX
MonthNo = MONTH([Date])
```

**DateTableTemplate_2874bb78-d6e0-4e83-ba49-1e8e734c0b72[Month]**
```DAX
Month = FORMAT([Date], "MMMM")
```

**DateTableTemplate_2874bb78-d6e0-4e83-ba49-1e8e734c0b72[QuarterNo]**
```DAX
QuarterNo = INT(([MonthNo] + 2) / 3)
```

**DateTableTemplate_2874bb78-d6e0-4e83-ba49-1e8e734c0b72[Quarter]**
```DAX
Quarter = "Qtr " & [QuarterNo]
```

**DateTableTemplate_2874bb78-d6e0-4e83-ba49-1e8e734c0b72[Day]**
```DAX
Day = DAY([Date])
```

**LocalDateTable_8d0cba94-ccce-46d4-83be-510ad1a68baa[Year]**
```DAX
Year = YEAR([Date])
```

**LocalDateTable_8d0cba94-ccce-46d4-83be-510ad1a68baa[MonthNo]**
```DAX
MonthNo = MONTH([Date])
```

**LocalDateTable_8d0cba94-ccce-46d4-83be-510ad1a68baa[Month]**
```DAX
Month = FORMAT([Date], "MMMM")
```

**LocalDateTable_8d0cba94-ccce-46d4-83be-510ad1a68baa[QuarterNo]**
```DAX
QuarterNo = INT(([MonthNo] + 2) / 3)
```

**LocalDateTable_8d0cba94-ccce-46d4-83be-510ad1a68baa[Quarter]**
```DAX
Quarter = "Qtr " & [QuarterNo]
```

**LocalDateTable_8d0cba94-ccce-46d4-83be-510ad1a68baa[Day]**
```DAX
Day = DAY([Date])
```

**LocalDateTable_6b2631e5-4bc1-4269-9691-d42fd560f648[Year]**
```DAX
Year = YEAR([Date])
```

**LocalDateTable_6b2631e5-4bc1-4269-9691-d42fd560f648[MonthNo]**
```DAX
MonthNo = MONTH([Date])
```

**LocalDateTable_6b2631e5-4bc1-4269-9691-d42fd560f648[Month]**
```DAX
Month = FORMAT([Date], "MMMM")
```

**LocalDateTable_6b2631e5-4bc1-4269-9691-d42fd560f648[QuarterNo]**
```DAX
QuarterNo = INT(([MonthNo] + 2) / 3)
```

**LocalDateTable_6b2631e5-4bc1-4269-9691-d42fd560f648[Quarter]**
```DAX
Quarter = "Qtr " & [QuarterNo]
```

**LocalDateTable_6b2631e5-4bc1-4269-9691-d42fd560f648[Day]**
```DAX
Day = DAY([Date])
```

**LocalDateTable_77492bad-8bec-4a4d-bb96-b305b3c73c6b[Year]**
```DAX
Year = YEAR([Date])
```

**LocalDateTable_77492bad-8bec-4a4d-bb96-b305b3c73c6b[MonthNo]**
```DAX
MonthNo = MONTH([Date])
```

**LocalDateTable_77492bad-8bec-4a4d-bb96-b305b3c73c6b[Month]**
```DAX
Month = FORMAT([Date], "MMMM")
```

**LocalDateTable_77492bad-8bec-4a4d-bb96-b305b3c73c6b[QuarterNo]**
```DAX
QuarterNo = INT(([MonthNo] + 2) / 3)
```

**LocalDateTable_77492bad-8bec-4a4d-bb96-b305b3c73c6b[Quarter]**
```DAX
Quarter = "Qtr " & [QuarterNo]
```

**LocalDateTable_77492bad-8bec-4a4d-bb96-b305b3c73c6b[Day]**
```DAX
Day = DAY([Date])
```

**Date Table[Month]**
```DAX
Month = FORMAT('Date Table'[Date], "mmm")
```

**LocalDateTable_03564684-c40d-4b46-93d6-f702bfae9a1f[Year]**
```DAX
Year = YEAR([Date])
```

**LocalDateTable_03564684-c40d-4b46-93d6-f702bfae9a1f[MonthNo]**
```DAX
MonthNo = MONTH([Date])
```

**LocalDateTable_03564684-c40d-4b46-93d6-f702bfae9a1f[Month]**
```DAX
Month = FORMAT([Date], "MMMM")
```

**LocalDateTable_03564684-c40d-4b46-93d6-f702bfae9a1f[QuarterNo]**
```DAX
QuarterNo = INT(([MonthNo] + 2) / 3)
```

**LocalDateTable_03564684-c40d-4b46-93d6-f702bfae9a1f[Quarter]**
```DAX
Quarter = "Qtr " & [QuarterNo]
```

**LocalDateTable_03564684-c40d-4b46-93d6-f702bfae9a1f[Day]**
```DAX
Day = DAY([Date])
```

**Date Table[mon_no]**
```DAX
mon_no = MONTH('Date Table'[Date])
```

## 3. Calculated Tables

**DateTableTemplate_2874bb78-d6e0-4e83-ba49-1e8e734c0b72**
```DAX
DateTableTemplate_2874bb78-d6e0-4e83-ba49-1e8e734c0b72 = Calendar(Date(2015,1,1), Date(2015,1,1))
```

**LocalDateTable_8d0cba94-ccce-46d4-83be-510ad1a68baa**
```DAX
LocalDateTable_8d0cba94-ccce-46d4-83be-510ad1a68baa = Calendar(Date(Year(MIN('financial_loan'[last_credit_pull_date])), 1, 1), Date(Year(MAX('financial_loan'[last_credit_pull_date])), 12, 31))
```

**LocalDateTable_6b2631e5-4bc1-4269-9691-d42fd560f648**
```DAX
LocalDateTable_6b2631e5-4bc1-4269-9691-d42fd560f648 = Calendar(Date(Year(MIN('financial_loan'[last_payment_date])), 1, 1), Date(Year(MAX('financial_loan'[last_payment_date])), 12, 31))
```

**LocalDateTable_77492bad-8bec-4a4d-bb96-b305b3c73c6b**
```DAX
LocalDateTable_77492bad-8bec-4a4d-bb96-b305b3c73c6b = Calendar(Date(Year(MIN('financial_loan'[next_payment_date])), 1, 1), Date(Year(MAX('financial_loan'[next_payment_date])), 12, 31))
```

**Date Table**
```DAX
Date Table = CALENDAR(MIN(financial_loan[issue_date]),MAX(financial_loan[issue_date]))
```

**LocalDateTable_03564684-c40d-4b46-93d6-f702bfae9a1f**
```DAX
LocalDateTable_03564684-c40d-4b46-93d6-f702bfae9a1f = Calendar(Date(Year(MIN('Date Table'[Date])), 1, 1), Date(Year(MAX('Date Table'[Date])), 12, 31))
```

**table_measures**
```DAX
table_measures = Row("Column", BLANK())
```

**Select Measure**
```DAX
Select Measure = {
    ("Total Loan Applications", NAMEOF('table_measures'[total_loan_appl]), 0),
    ("Total Funded Amount", NAMEOF('table_measures'[total_funded_amt]), 1),
    ("Total Amount Received", NAMEOF('table_measures'[total_received_amt]), 2)
}
```

## 4. Power Query (M) — Source of financial_loan

**financial_loan**
```M
let
    Source = Csv.Document(File.Contents("P:\project\Bank Loan Report\financial_loan.csv"),[Delimiter=",", Columns=24, Encoding=1252, QuoteStyle=QuoteStyle.None]),
    #"Promoted Headers" = Table.PromoteHeaders(Source, [PromoteAllScalars=true]),
    #"Changed Type" = Table.TransformColumnTypes(#"Promoted Headers",{{"id", Int64.Type}, {"address_state", type text}, {"application_type", type text}, {"emp_length", type text}, {"emp_title", type text}, {"grade", type text}, {"home_ownership", type text}, {"issue_date", type date}, {"last_credit_pull_date", type date}, {"last_payment_date", type date}, {"loan_status", type text}, {"next_payment_date", type date}, {"member_id", Int64.Type}, {"purpose", type text}, {"sub_grade", type text}, {"term", type text}, {"verification_status", type text}, {"annual_income", type number}, {"dti", type number}, {"installment", type number}, {"int_rate", type number}, {"loan_amount", Int64.Type}, {"total_acc", Int64.Type}, {"total_payment", Int64.Type}})
in
    #"Changed Type"
```
