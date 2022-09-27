Step:1 Creating Min and MAX Dates from Dates Column
List.Min(ReorderedColumns[Ex Date])
List.Max(ReorderedColumns[Ex Date])

Step: 2 Bring Min Date and Max Date to Excel by creating only connection

Step: 3 Creating FROM and TO dates
DateFROM: if ChangedType{0}[FROM] = null then MinDate else ChangedType{0}[FROM]
DateTO: if ChangedType{0}[TO] = null then MaxDate else ChangedType{0}[TO]

Step:3 Create Duplicate Column of Purpose

Step:4 Split Purpose Column by Delimiter "-"

Step:5 Split Bonus numericals using custom function
Formula: Table.SplitColumn(#"RenamedColumnType", "Action Type", 
Splitter.SplitTextByCharacterTransition((c) => not List.Contains({"0".."9",":"}, c), {"0".."9"}), {"Action Type", "Action Type.2"})
<img width="773" alt="image" src="https://user-images.githubusercontent.com/103557302/192464754-62f295ce-216e-4df4-ba37-c8d43a0b4072.png">

Step:6 Split Right issue using "Text before Delimiter"

Step:7 Removed unwanted Columns

Step:8 Filter based on Action Type using Data validation

Step:9 Take Action Type to Power Query
Formula: Table.SelectRows(TrimmedText, each ([Action Type] = ActionType))

Step:10 Close and Load create only connection
<img width="854" alt="image" src="https://user-images.githubusercontent.com/103557302/192467780-0b1aa370-fe08-4584-bde9-331dfc7b7f09.png">
