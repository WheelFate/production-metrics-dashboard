# 📊 Vital Production Metrics Dashboard

This project demonstrates a simple, **completely online, no-installation-required** way to visualize vital production metrics using **Google Sheets** as a data source and **GitHub Pages** for hosting a live, interactive dashboard. It's perfect for beginners looking to get started with data visualization and understanding key operational metrics.

---

## What are Vital Production Metrics in DevOps?

In the world of **DevOps** (which combines software development and IT operations), "Vital Production Metrics" are the key measurements that tell you how well your software applications and systems are performing and serving your users in a live, production environment.

Think of them as the "health indicators" or "report card" for your digital services. Monitoring these metrics helps teams:

1.  **Understand System Health:** Are things running smoothly, or are there problems?
2.  **Identify Issues Quickly:** Spot performance slowdowns or errors before they become major incidents.
3.  **Improve User Experience:** Ensure customers are having a good experience with your service.
4.  **Make Informed Decisions:** Decide where to invest time and resources for improvements.

Common categories of vital production metrics include:

* **Performance Metrics:**
    * **Latency/Response Time:** How quickly your application responds to user requests. (e.g., "Average API Response Time")
    * **Throughput:** How many requests or transactions your system can handle per second/minute. (e.g., "Requests Per Second")
    * **Error Rate:** The percentage of requests that result in an error. (e.g., "5xx Errors per Minute")
* **Availability Metrics:**
    * **Uptime:** The percentage of time your system is operational and accessible. (e.g., "Service Uptime Percentage")
* **Resource Utilization Metrics:**
    * **CPU/Memory Usage:** How much computing power and memory your servers or applications are consuming. (e.g., "Server CPU Usage %")
    * **Disk I/O:** How often data is being read from or written to storage.
* **Business/User Metrics:**
    * **Active Users:** How many users are currently using your service.
    * **Conversion Rate:** The percentage of users completing a desired action (e.g., making a purchase).
    * **Customer Churn:** The rate at which customers stop using your service.

**Why are they "vital"?** Because they directly impact your users, your business, and your team's ability to deliver reliable software. This dashboard helps you keep an eye on them!

---

## Project Overview

This project sets up a simple web page hosted on GitHub Pages that fetches data from a publicly published Google Sheet and displays it using interactive charts powered by Chart.js.

**How it works:**

1.  **Data Source:** You update your metrics manually (or via simple automation) in a Google Sheet.
2.  **Public CSV:** The Google Sheet is published to the web as a CSV (Comma Separated Values) file, making it accessible via a unique URL.
3.  **GitHub Pages:** A static website (`index.html`) is hosted on GitHub Pages.
4.  **Data Fetching:** The `index.html` file contains JavaScript code that, when loaded in a browser, fetches the CSV data from your Google Sheet URL.
5.  **Visualization:** Chart.js library (loaded from a CDN) then takes this data and renders dynamic, responsive charts on your dashboard.
6.  **Automatic Updates:** Whenever you update your Google Sheet, the charts on your live dashboard automatically refresh with the new data when the page is reloaded.

---

## How to Create Your Own Dashboard (Step-by-Step Guide for Beginners)

Follow these steps to set up your own vital production metrics dashboard. No software installation is required!

### Step 1: Identify Your Vital Metrics 📈

Before anything else, decide what 2-3 key metrics you want to track. These should be things you can easily measure and represent with numbers over time.

* **Examples:**
    * `Daily Website Visitors`
    * `Daily Sales Count`
    * `Customer Support Tickets Solved Daily`

### Step 2: Prepare Your Data in Google Sheets 📊

Google Sheets will be your central place for data entry.

1.  **Open Google Sheets:** Go to [sheets.google.com](https://sheets.google.com/) and create a **new blank spreadsheet**.
2.  **Name Your Sheet:** Rename it (e.g., `Production Metrics Data`).
3.  **Set Up Column Headers:** In the very first row (Row 1), create your column headers.
    * **Cell A1:** `Date`
    * **Cell B1:** Your first metric name (e.g., `Daily Website Visitors`)
    * **Cell C1:** Your second metric name (e.g., `Daily Sales Count`)
    * **Cell D1:** Your third metric name (e.g., `Customer Support Tickets Solved Daily`)
    * *Make sure these column names exactly match what's in the `index.html` code later!*
4.  **Enter Sample Data:** Starting from Row 2, add some sample data for a few days. This helps test your dashboard.
    | Date       | Daily Website Visitors | Daily Sales Count | Customer Support Tickets Solved Daily |
    | :--------- | :--------------------- | :---------------- | :------------------------------------ |
    | 2025-07-01 | 1500                   | 50                | 25                                    |
    | 2025-07-02 | 1620                   | 55                | 28                                    |
    | 2025-07-03 | 1480                   | 48                | 22                                    |
    | 2025-07-04 | 1550                   | 52                | 26                                    |
    | 2025-07-05 | 1700                   | 60                | 30                                    |
5.  **Publish to the Web as CSV:** This step makes your data publicly accessible.
    * Go to `File` > `Share` > `Publish to web`.
    * In the dialog:
        * Select the specific sheet you're working on (e.g., `Sheet1`).
        * For the format dropdown, choose "**Comma-separated values (.csv)**".
    * Click "Publish", then "OK" to confirm.
    * **IMPORTANT:** A URL will appear. **Copy this entire URL.** This is your public CSV data URL. It will look like `https://docs.google.com/spreadsheets/d/e/2PACX-1v.../pub?output=csv`. **Keep this URL safe; you'll need it in Step 4!**

### Step 3: Create Your GitHub Repository and Enable GitHub Pages 📁

This is where your dashboard code will live and be hosted online.

1.  **Create a New GitHub Repository:**
    * Go to [github.com](https://github.com/) and log in.
    * Click the `+` sign (top right) and select "**New repository**".
    * **Repository Name:** Choose a name like `production-metrics-dashboard`.
    * **Public:** Select "Public".
    * **Add a README file:** Check this box.
    * Click "**Create repository**".
2.  **Enable GitHub Pages:**
    * Once the repository is created, click the "**Settings**" tab.
    * In the left sidebar, click "**Pages**".
    * Under "Build and deployment," for "Source," select "**Deploy from a branch**".
    * For "Branch," choose "**main**" (or `master`) and select the `/ (root)` folder.
    * Click "**Save**".
    * GitHub will start deploying your site. It might take a few minutes. You'll see a message like "Your site is published at `https://yourusername.github.io/your-repository-name/`". **This is your live dashboard URL!**

### Step 4: Create Your Dashboard HTML and JavaScript 💻

Now you'll add the code that fetches your data and draws the charts.

1.  **Go to Your Repository:** Navigate to the "Code" tab of your new GitHub repository.
2.  **Create `index.html`:**
    * Click the "**Add file**" dropdown and select "**Create new file**".
    * Name the file `index.html`.
    * **Paste the following complete code into the file editor.**
    * **CRITICAL:** Find the line `const GOOGLE_SHEETS_CSV_URL = 'YOUR_GOOGLE_SHEETS_CSV_URL_HERE';` and **replace** `'YOUR_GOOGLE_SHEETS_CSV_URL_HERE'` with the exact CSV URL you copied from Google Sheets in Step 2.

    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Production Metrics Dashboard</title>
        <!-- Include Chart.js from CDN for charting capabilities -->
        <script src="[https://cdn.jsdelivr.net/npm/chart.js](https://cdn.jsdelivr.net/npm/chart.js)"></script>
        <style>
            body { font-family: Arial, sans-serif; margin: 20px; background-color: #f4f4f4; color: #333; }
            .container { max-width: 1000px; margin: auto; background: white; padding: 20px; border-radius: 8px; box-shadow: 0 2px 10px rgba(0,0,0,0.1); }
            h1 { text-align: center; color: #0056b3; }
            .chart-wrapper { margin-bottom: 30px; padding: 15px; border: 1px solid #ddd; border-radius: 5px; background: #fff; }
            canvas { max-width: 100%; height: auto !important; } /* Ensure charts are responsive */
        </style>
    </head>
    <body>
        <div class="container">
            <h1>📊 Vital Production Metrics</h1>

            <div class="chart-wrapper">
                <h2>Daily Website Visitors</h2>
                <canvas id="visitorsChart"></canvas>
            </div>

            <div class="chart-wrapper">
                <h2>Daily Sales Count</h2>
                <canvas id="salesChart"></canvas>
            </div>

            <div class="chart-wrapper">
                <h2>Customer Support Tickets Solved Daily</h2>
                <canvas id="ticketsChart"></canvas>
            </div>

            <p style="text-align: center; font-size: 0.9em; color: #666;">Data updates automatically from Google Sheets.</p>
        </div>

        <script>
            // --- YOUR PUBLISHED GOOGLE SHEETS CSV URL IS HERE ---
            const GOOGLE_SHEETS_CSV_URL = '[https://docs.google.com/spreadsheets/d/e/2PACX-1vTsk102kLxo9LfQvVWjMYYJV_WTpJYU3rYubkqeOAax6uq5BAz3Z2iuF9sEMxHhNV1VVst6S8ONKIgx/pub?gid=444981365&single=true&output=csv](https://docs.google.com/spreadsheets/d/e/2PACX-1vTsk102kLxo9LfQvVWjMYYJV_WTpJYU3rYubkqeOAax6uq5BAz3Z2iuF9sEMxHhNV1VVst6S8ONKIgx/pub?gid=444981365&single=true&output=csv)'; 

            async function fetchDataAndRenderCharts() {
                try {
                    const response = await fetch(GOOGLE_SHEETS_CSV_URL);
                    const csvText = await response.text();
                    
                    // Parse CSV data
                    const rows = csvText.trim().split('\n');
                    const headers = rows[0].split(',').map(h => h.trim()); // Trim headers
                    const data = rows.slice(1).map(row => {
                        const values = row.split(',').map(v => v.trim()); // Trim values
                        return headers.reduce((obj, header, index) => {
                            obj[header] = values[index];
                            return obj;
                        }, {});
                    });

                    // Prepare data for Chart.js based on your sheet's column names
                    const dates = data.map(row => row['Date']);
                    const visitors = data.map(row => parseInt(row['Daily Website Visitors'], 10)); // Ensure numbers are parsed
                    const sales = data.map(row => parseInt(row['Daily Sales Count'], 10));
                    const tickets = data.map(row => parseInt(row['Customer Support Tickets Solved Daily'], 10));

                    // Render Visitors Chart
                    new Chart(document.getElementById('visitorsChart').getContext('2d'), {
                        type: 'line', // Line chart for trends
                        data: {
                            labels: dates,
                            datasets: [{
                                label: 'Daily Website Visitors',
                                data: visitors,
                                borderColor: 'rgb(75, 192, 192)',
                                tension: 0.1, // Smooth lines
                                fill: false // No fill under the line
                            }]
                        },
                        options: {
                            responsive: true,
                            plugins: {
                                legend: { display: true }
                            },
                            scales: {
                                x: { title: { display: true, text: 'Date' } },
                                y: { beginAtZero: true, title: { display: true, text: 'Visitors' } }
                            }
                        }
                    });

                    // Render Sales Chart
                    new Chart(document.getElementById('salesChart').getContext('2d'), {
                        type: 'bar', // Bar chart for distinct daily counts
                        data: {
                            labels: dates,
                            datasets: [{
                                label: 'Daily Sales Count',
                                data: sales,
                                backgroundColor: 'rgba(153, 102, 255, 0.6)',
                                borderColor: 'rgba(153, 102, 255, 1)',
                                borderWidth: 1
                            }]
                        },
                        options: {
                            responsive: true,
                            plugins: {
                                legend: { display: true }
                            },
                            scales: {
                                x: { title: { display: true, text: 'Date' } },
                                y: { beginAtZero: true, title: { display: true, text: 'Sales Count' } }
                            }
                        }
                    });

                    // Render Tickets Chart
                    new Chart(document.getElementById('ticketsChart').getContext('2d'), {
                        type: 'line', // Line chart for trends
                        data: {
                            labels: dates,
                            datasets: [{
                                label: 'Customer Support Tickets Solved Daily',
                                data: tickets,
                                borderColor: 'rgb(255, 159, 64)',
                                tension: 0.1,
                                fill: false
                            }]
                        },
                        options: {
                            responsive: true,
                            plugins: {
                                legend: { display: true }
                            },
                            scales: {
                                x: { title: { display: true, text: 'Date' } },
                                y: { beginAtZero: true, title: { display: true, text: 'Tickets Solved' } }
                            }
                        }
                    });

                } catch (error) {
                    console.error('Error fetching or rendering data:', error);
                    document.querySelector('.container').innerHTML = '<p style="color: red; text-align: center;">Failed to load metrics. Please check your Google Sheets URL and ensure it\'s published correctly and data columns match the code.</p>';
                }
            }

            // Run the function when the page loads
            fetchDataAndRenderCharts();
        </script>
    </body>
    </html>
    ```

3.  **Commit New File (or Update File):**
    * Scroll down, add a commit message (e.g., "Add initial `index.html` for dashboard"), and click "**Commit new file**" (or "Commit changes" if editing an existing file).

### Step 5: View Your Live Dashboard & Maintain Your Metrics 🎉

1.  **Wait for GitHub Pages:** Give GitHub Pages a few minutes (1-5 typically) to build and deploy your site.
2.  **Access Your Dashboard:** Go to the URL you noted in Step 3 (e.g., `https://yourusername.github.io/your-repository-name/`). You should now see your live dashboard with charts!
3.  **Update Data:** Whenever you add new rows of data to your Google Sheet, your GitHub Pages dashboard will **automatically update** when you refresh the page in your browser. You don't need to touch GitHub again unless you want to change the dashboard's design or logic.

---

## Customization & Further Learning

* **More Metrics:** Add more columns to your Google Sheet and extend the `index.html` to include more charts.
* **Chart Types:** Chart.js supports many chart types (bar, pie, scatter, etc.). Experiment with `type: 'line'` or `type: 'bar'` in the JavaScript to see different visualizations.
* **Styling:** Modify the `<style>` section in `index.html` to change colors, fonts, and layout.
* **Automation:** For more advanced users, you could explore Google Apps Script to automate data entry into your Google Sheet from other sources.
* **Advanced Dashboards:** As you grow, consider dedicated monitoring tools like Grafana, Prometheus, or Kibana for more robust production metric dashboards.

---

## License

This project is open-source and available under the [MIT License](LICENSE). Feel free to use, modify, and distribute it.
