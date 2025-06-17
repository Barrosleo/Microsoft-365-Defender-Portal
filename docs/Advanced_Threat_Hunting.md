# Advanced Threat Hunting with KQL

## Overview:

Advanced threat hunting leverages Kusto Query Language (KQL) to detect hidden threats:

- **Built-In & Custom Queries:**

  Use pre-built queries or write your own to search through logs.
  
- **Example Query:**
  
  ```kusto
  SigninLogs
  | where ResultType != 0
  | extend Country = tostring(LocationDetails.CountryOrRegion)
  | summarize FailedAttempts = count() by IPAddress, Country, bin(TimeGenerated, 1h)
  | where FailedAttempts > 5
  ```
  
This query helps detect potential brute-force attacks.

Use these techniques to convert findings into actionable incidents for further investigation.

---

## Files in `queries/`

### File: queries/failed_signins.kql

```kusto
SigninLogs
| where ResultType != 0
| extend Country = tostring(LocationDetails.CountryOrRegion)
| summarize FailedAttempts = count() by IPAddress, Country, bin(TimeGenerated, 1h)
| where FailedAttempts > 5
```
