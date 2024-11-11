# Ecommerce Operations Dashboard Automation
#### Video Demo:  <https://youtu.be/IxV458Cf90E>
#### Description: 
In this project I have automated my business flow. 3 major flows I have automated are-
1. Orders Fetching
2. MRP and Label Automation
3. Entry Reconciler for better Stock and Data Management

   1. Orders Fetching-
      Set Script Properties: Stores API credentials (refresh token, client ID, client secret) for Amazon SP-API authentication.

      Authentication: Uses the getAccessToken function to fetch an access_token via OAuth2, enabling API requests.

      Retry Logic: Implements makeRequestWithRetries to handle failed API calls with up to 5 retries and exponential backoff.

      Order Fetching: fetchOrders retrieves new and updated orders using two SP-API endpoints (CreatedAfter and LastUpdatedAfter) and combines them into a unique list using a Map.

      Order Item Details: fetchOrderItems fetches detailed item information for each order.

      Data Writing to Google Sheets: appendOrdersToSheet processes orders and writes them to a Google Sheet (Orders Confirmed), adding headers and ensuring data structure.

      Backend Tracking: Updates the last run timestamp in the Backend sheet to track incremental order fetching.

      Workflow: The main function sets credentials and runs the order-fetching and processing workflow.

   2. MRP & Label Automation-
      Initialize Sheets and Set Background:
      
      Retrieves two sheets: LABELS TAG DATA (originsht) and Please Read Automation & Backend (sheet).
      Temporarily changes the background of A1:I1 in LABELS TAG DATA to red for visual indication.
      Check for Previous File:
      
      Checks if K1 in the backend sheet is set to "SUCCESS".
      If true, deletes the previously created file (ID from cell J1) by marking it as trashed.
      Retrieve PDF IDs:
      
      Reads a count (H1) to determine how many PDF files to merge.
      Retrieves file IDs from column G (rows 2 onward) and stores them in an array (ids).
      Fetch and Merge PDF Files:
      
      Uses the PDF-lib library (via CDN) to handle PDF merging.
      Loads and merges all specified PDFs into a single PDF document:
      For each PDF ID, it loads the file as binary data.
      Copies all pages from the individual PDFs into a new PDF document (pdfDoc).
      Save the Merged PDF:
      
      Saves the merged PDF file as a new file in Google Drive with the name from cell L3.
      Gets the file’s URL and writes it to cell I1 in the backend sheet, along with the filename in I2.
      Update and Share:
      
      Marks the process as "SUCCESS" in cell K1.
      Shares the newly created file with edit permissions for anyone.
      Restores the original background color of LABELS TAG DATA (A1:I1 to white).

   3. Entry Reconciler for better Stock and Data Management (I couldn’t include this in the video due to time constraints, but it was a challenging task that I’m proud of, so I wanted to share it here for consideration.)
      Initialize Sheets and Set Background:
      
      Retrieves two sheets: LABELS TAG DATA (originsht) and Please Read Automation & Backend (sheet).
      Temporarily changes the background of A1:I1 in LABELS TAG DATA to red for visual indication.
      Check for Previous File:
      
      Checks if K1 in the backend sheet is set to "SUCCESS".
      If true, deletes the previously created file (ID from cell J1) by marking it as trashed.
      Retrieve PDF IDs:
      
      Reads a count (H1) to determine how many PDF files to merge.
      Retrieves file IDs from column G (rows 2 onward) and stores them in an array (ids).
      Fetch and Merge PDF Files:
      
      Uses the PDF-lib library (via CDN) to handle PDF merging.
      Loads and merges all specified PDFs into a single PDF document:
      For each PDF ID, it loads the file as binary data.
      Copies all pages from the individual PDFs into a new PDF document (pdfDoc).
      Save the Merged PDF:
      
      Saves the merged PDF file as a new file in Google Drive with the name from cell L3.
      Gets the file’s URL and writes it to cell I1 in the backend sheet, along with the filename in I2.
      Update and Share:
      
      Marks the process as "SUCCESS" in cell K1.
      Shares the newly created file with edit permissions for anyone.
      Restores the original background color of LABELS TAG DATA (A1:I1 to white).
