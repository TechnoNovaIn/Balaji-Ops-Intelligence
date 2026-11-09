# Balaji Transports -- Fleet Operations Intelligence

## Project Description

Fleet Operations Intelligence is a web-based dashboard for reviewing
Balaji Transports' fleet operations. It connects to the Balaji Transport
operations API and brings shipment and diesel-indent information into
one place.

The dashboard helps the transport team review vehicle utilisation,
loading performance, diesel consumption, fuel efficiency, cancellations,
driver--vehicle patterns, and detailed operational records.

## Main Features

### Login and Live API Connection

-   Login using an authorised operations API username and password.
-   Connects to the Balaji Transport API.
-   Fetches vehicle master, shipment, and diesel-indent records for the
    selected date range.
-   Shows a loading indicator while data is is being fetched.

### Filters

-   Select From and To dates.
-   Filter by vehicle type or view all vehicle types.
-   Click **Load range** to fetch the selected period.

### Dashboard Reports

1.  **Summary** -- Main operational KPIs, shipment and diesel
    comparisons, shipment-type mix, daily active vehicles, and
    cancellation details.
2.  **Under-utilized** -- Vehicle active days, idle days, trips, and
    utilisation percentage.
3.  **Under-loaded** -- Shipments below configured load limits and short
    tonnes.
4.  **Fuel-No-Ship** -- Own trucks and trailers that drew diesel but had
    no shipment in the selected range.
5.  **Cancelled** -- Cancelled diesel indents by issuer, location, bunk,
    vehicle type, and vehicle.
6.  **Driver ↔ Vehicle** -- Drivers linked to multiple vehicles and
    vehicles linked to multiple drivers.
7.  **Consumption** -- Diesel consumption by fuel bunk and location.
8.  **Heavy Diesel** -- Heavy diesel usage and isolated fuelling for
    trucks, trailers, and equipment.
9.  **Cancel TAT** -- Time between indent issue and cancellation.
10. **Irregular** -- Vehicles with irregular shipment patterns and long
    gaps between runs.
11. **Averages** -- Average net tonnes per trip by vehicle, location,
    and shipment type.
12. **Efficiency** -- Diesel litres per net tonne moved and statistical
    outliers.
13. **Multi-fill** -- Vehicles with three or more diesel fills on the
    same date.
14. **By Can** -- Active diesel indents where the vehicle number is
    blank or contains "BY CAN".
15. **Car & LMV** -- Active diesel indents for Car and LMV vehicle
    types.
16. **Cranes HSD** -- Active diesel indents for cranes.
17. **OST Pending** -- Diesel indents where the API provides OwnerName =
    "Pending".
18. **One-Page Summary** -- Diesel data by category, location, and
    issuer, with a plain-English summary.
19. **Raw Shipments** -- Filter shipment records and export them.
20. **Raw Diesel** -- Filter diesel-indent records and export them.

### Charts, Details, and Excel Export

-   Click chart items to open matching records.
-   View detailed shipment or diesel-indent tables.
-   Export supported report tables and drill-down details to Excel.
-   Filter raw shipment and diesel records.

## How to Run on Windows

### Requirements

-   Windows 10 or Windows 11.
-   Google Chrome or Microsoft Edge.
-   Internet connection.
-   An active Balaji Transport operations API account.
-   Access to the operations API from your network/browser.

### Step 1 -- Save the File

Save `balaji_fleet_intelligence_final.html` in a folder on your Windows
computer.

### Step 2 -- Open the Dashboard

1.  Open the folder.
2.  Double-click `balaji_fleet_intelligence_final.html`.
3.  The file opens in Chrome or Microsoft Edge.

No Node.js, Python, React, or database installation is required to open
this HTML file.

### Step 3 -- Login

1.  Enter your authorised API username.
2.  Enter your password.
3.  Click **Connect**.
4.  After successful login, the dashboard opens.

The HTML file has a default username value of `Raghu`. Use the username
assigned to your account. Do not add your password to the HTML file or
GitHub.

### Step 4 -- Load Data

1.  Select the **From** date and **To** date.
2.  Choose a vehicle type, or keep **All vehicle types** selected.
3.  Click **Load range**.
4.  Wait while shipment and diesel data are fetched from the API.

### Step 5 -- View Reports

Select a report tab at the top. Click chart bars, chart sections, or
supported table rows to inspect matching records.

### Step 6 -- Export to Excel

Use the **Excel** button in supported report tables or detail windows.

## API Connection

The HTML file connects to:

`https://external.balajitransports.in/api`

It uses API operations for login/session token, vehicle master data,
diesel indent reports, and shipment details. A working API connection
and authorised credentials are required. If the API is unavailable,
access is denied, or the browser blocks the request, live data cannot
load.

## Important Data and Calculation Notes

-   Shipment and diesel records are fetched for the selected date range
    in weekly chunks.
-   Shipment records are deduplicated by `shipmentId`; net weight is
    added when duplicate shipment rows are found.
-   Vehicle type and own-fleet identification use the Balaji Transport
    vehicle master.
-   Diesel indent rows are merged by `IndentID`.
-   Some reports cover only the Balaji Transport fleet; other diesel
    reports cover all transport. Check each report description before
    comparing totals.
-   Cranes, coil vehicles, hydra, LCV, small vehicles, and cars are
    excluded from reports specifically analysing trucks and trailers.
-   Under-loaded checks use load limits configured in the HTML code.
    Confirm these limits with the transport team before using the report
    for official decisions.
-   "Isolated" fuelling means diesel drawn with no shipment within two
    days before or after the fuelling date.
-   Cancellation-person identification is best-effort. The dashboard
    checks likely cancellation fields in the raw API record and may fall
    back to the issuer field. Verify the raw record before treating the
    name as confirmed.
-   **OST Pending** depends on the API returning an `OwnerName` field
    with the value `Pending`. If the field or value is not returned, the
    tab is designed to show zero/blank; it does not estimate pending
    amounts using another method.

## Troubleshooting

### Login fails

-   Check your username and password.
-   Confirm that your account is active.
-   Check whether the operations API is available.
-   Contact the API administrator if access is denied.

### Data does not load

-   Check your internet/network connection.
-   Confirm that the selected date range is valid.
-   Try a smaller date range.
-   Ask the API administrator to check API access and permissions.

### Charts or Excel export do not work

-   Check your internet connection. Chart.js and SheetJS are loaded from
    online CDN links.
-   Refresh the page and try again.
-   Use an updated version of Chrome or Edge.

## Suggested GitHub Folder Structure

``` text
Balaji-Fleet-Operations-Intelligence/
├── README.md
└── balaji_fleet_intelligence_final.html
```

## Security and Privacy

-   Do not upload API passwords, session tokens, or confidential
    credentials to GitHub.
-   This dashboard connects to a live company operations API. Do not
    publish it publicly unless the company has approved it.
-   Shipment, diesel, vehicle, driver, location, and payment-related
    information may be confidential. Keep the repository private unless
    you have permission to share the code and data.
-   Share access only with authorised users.

------------------------------------------------------------------------

**Project:** Balaji Transports -- Fleet Operations Intelligence\
**Type:** HTML-based live operations dashboard\
**Data source:** Balaji Transport operations API
