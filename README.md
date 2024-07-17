# DATE-TIME-FUNCTIONS-USE-CASE

CREATE TABLE [dbo].[loginemployee](

	[name] [varchar](50) NULL,
 
	[checkindate] [datetime] NULL,
 
	[checkoutdate] [datetime] NULL
 
) ON [PRIMARY]
GO
INSERT [dbo].[loginemployee] ([name], [checkindate], [checkoutdate]) VALUES (N'Bob', CAST(N'2023-07-01T09:00:00.000' AS DateTime), CAST(N'2023-07-01T18:00:00.000' AS DateTime))

INSERT [dbo].[loginemployee] ([name], [checkindate], [checkoutdate]) VALUES (N'Alice', CAST(N'2023-07-02T08:00:00.000' AS DateTime), CAST(N'2023-07-02T19:00:00.000' AS DateTime))

INSERT [dbo].[loginemployee] ([name], [checkindate], [checkoutdate]) VALUES (N'Bob', CAST(N'2023-07-02T09:00:00.000' AS DateTime), CAST(N'2023-07-02T19:00:00.000' AS DateTime))

INSERT [dbo].[loginemployee] ([name], [checkindate], [checkoutdate]) VALUES (N'Charlie', CAST(N'2023-07-01T07:00:00.000' AS DateTime), CAST(N'2023-07-01T15:00:00.000' AS DateTime))

INSERT [dbo].[loginemployee] ([name], [checkindate], [checkoutdate]) VALUES (N'Alice', CAST(N'2023-07-01T08:00:00.000' AS DateTime), NULL)

INSERT [dbo].[loginemployee] ([name], [checkindate], [checkoutdate]) VALUES (N'Bob', CAST(N'2023-09-01T09:00:00.000' AS DateTime), CAST(N'2023-09-01T14:00:00.000' AS DateTime))

INSERT [dbo].[loginemployee] ([name], [checkindate], [checkoutdate]) VALUES (N'Alice', CAST(N'2023-03-01T09:00:00.000' AS DateTime), NULL)
GO

DATE TIME FUNCTIONS USE CASE

SELECT
        NAME,
    
        YEAR(CHECKINDATE) AS [WORK YEAR],
    
        MONTH(CHECKINDATE) AS [WORK MONTH],
    
	UPPER(DATENAME(DAY, CHECKINDATE)) AS [WORK DAY],
 
	UPPER(DATENAME(MONTH, CHECKINDATE)) AS [WORK MONTH NAME],
 
	UPPER(DATENAME(WEEKDAY, CHECKINDATE)) AS [WORK DATE NAME],
 
	UPPER(DATENAME(WEEKDAY, EOMONTH(GETDATE()))) as [LAST DAY OF MONTH NAME],
 
	DATEDIFF(HOUR, CHECKINDATE, CHECKOUTDATE) AS [TOTAL HOURS],
 
	DATEPART(HOUR,CHECKOUTDATE) - DATEPART(HOUR, CHECKINDATE) AS [TOTAL HOURS USING DATEPART],	
 
       DATEDIFF(MINUTE, CHECKINDATE, CHECKOUTDATE) / 60.0 AS [TOTAL HOURS USING MINUTE],
    
	FORMAT(CHECKINDATE,  'yyyy-MM-dd') AS [FORMATTED DATE],
 
	EOMONTH(GETDATE()) AS [LAST DAY OF MONTH],
 
	CONVERT(varchar,CHECKINDATE,100) AS [DATE FORMAT 1], -- Jul  1 2023  9:00AM
 
	CONVERT(varchar,CHECKINDATE,107) AS [DATE FORMAT 2], -- Jul 01, 2023
 
	CONVERT(varchar,CHECKINDATE,106) AS [DATE FORMAT 3], -- 01 Jul 2023
 
	CONVERT(varchar,CHECKINDATE,105) AS [DATE FORMAT 4], -- 01-07-2023
 
	CONVERT(varchar,CHECKINDATE,111) AS [DATE FORMAT 5]  -- 2023/07/01
 
FROM LOGINEMPLOYEE

<img width="851" alt="image" src="https://github.com/user-attachments/assets/2a75004a-3e61-4c0f-8e95-1f946c89f9c4">

<img width="887" alt="image" src="https://github.com/user-attachments/assets/eb74bf09-7f21-41cc-9e7e-c6501503bbcf">
