# Search Console Looker Block

This is not an officially supported Google product. This project is not eligible for the [Google Open Source Software Vulnerability Rewards Program](https://bughunters.google.com/open-source-security).

## What does this Looker Block do for me?

This block is your solution for powerful, in-depth analysis of your organic search data. It's built to help you easily analyze and visualize the information from your Search Console BigQuery Export, turning raw data into actionable insights.

With this block, you can:

* Quickly identify performance trends with an **Insights Dashboard** that lets you compare any time period to an equivalent previous one.

* Track key metrics over time with a **Performance Dashboard** that visualizes Clicks, Impressions, CTR, and Average Site Position.

* Understand user behavior by dynamically segmenting your data by queries, country, and device.

The Search Console export provides access to your data in a powerful, flexible format. This Looker Block is built to help you access and leverage this information quickly.

Official documentation on how to export Search Console data in BigQuery can be found on the [Search Console Help site](https://support.google.com/webmasters/answer/12917675).

### Data Structure & Metrics

The Looker Block uses data exported from Search Console, which is aggregated by Date, Site, URL, Country, Query, and Device Type. This structure allows for a deep dive into user behavior.

Each row represents a daily summary of your site's performance for a specific Country, Device, and Query.

The key metrics you will find are:

* **Clicks:** The number of clicks from a Google search result to your site.

* **Impressions:** The number of times a URL from your site was shown to a user in a Google search result.

* **CTR (Click-Through Rate):** The percentage of impressions that resulted in a click.

* **Avg. Site Position:** The average position of your site's URL in the search results.

### Datasets Used

This Looker block utilizes the Dataset Exported by [Bulk Data Export of Search Console to BigQuery](https://support.google.com/webmasters/answer/12918484?hl=en&ref_topic=12917674&sjid=4892135313850277981-NC):

Table `searchdata_site_impression`: This table in BigQuery contains the aggregated data by [property](https://support.google.com/webmasters/answer/7576553#urlorsite), and Table `searchdata_site_impression` contains the aggregated data by [URL](https://support.google.com/webmasters/answer/7576553#urlorsite) you can find more related information about these tables [in tihs article](https://support.google.com/webmasters/answer/12917991?hl=en&ref_topic=12917674&sjid=4892135313850277981-NC#:~:text=all%20your%20data.-,Table%20schema,-Here%20are%20the)

## Key LookML Features

The LookML for this project is designed to be simple, making it easy to explore and understand the exported data.

* Previous Period Comparison (period_over_period): We leverage this functionality by using method 7 described [in this article](https://discuss.google.dev/t/methods-for-period-over-period-pop-analysis-in-looker/119253). This enables the straightforward and efficient calculation of previous period values (e.g., previous 7 days) for any selected metric, facilitating trend analysis and comparisons directly within your Explores and Dashboards.

### Looker Model and Views

The file structure of this block has been thoughtfully designed to ensure it is both easy to navigate and simple to extend.

* `searchdata_site_impression.view`: This is the foundational view for the block. It serves as the single source of truth for all core dimensions and metrics, including the sophisticated `period_over_period` logic that drives comparative analysis.

### Dashboards

* **Insights Dashboard:** Get a high-level overview of your site's performance, including a summary of top URLs, queries, and countries driving traffic.

* **Performance Dashboard:** Dive deep into time-series data for your key metrics. Use dynamic dimensions to segment and analyze performance by various user characteristics.
