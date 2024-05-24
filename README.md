# London Air Pollution Visualisation

This project aims to analyze air quality data in London using data fetched from the London Air API. The project demonstrates the use of API calls, SQL for data storage and retrieval, data analysis, and visualization techniques. The data covers air quality indices for various pollutants across different locations in London over a specified period.

Check out the initial visualisation [here](https://govindvirdee.github.io/London-Air-Pollution/monitoring_sites_map.html) showing the data collection sites, colour coded by site type. 

## Data Fetching
The data is fetched from the [London Air API](https://www.londonair.org.uk/LondonAir/API/) for a specified period. The fetch_air_quality_data function retrieves data for a given date, and the fetch_period_data function aggregates this data for the entire period.

## Database Schema

The fetched data is stored in a SQLite database with the following schema:

### authorities

| Column                | Type  | Description                              |
|-----------------------|-------|------------------------------------------|
| LocalAuthorityCode    | TEXT  | Primary key                              |
| LocalAuthorityName    | TEXT  | Name of the local authority              |
| LaCentreLatitude      | TEXT  | Latitude of the local authority center   |
| LaCentreLongitude     | TEXT  | Longitude of the local authority center  |
| LaCentreLatitudeWGS84 | TEXT  | Latitude of the local authority center in WGS84 format |
| LaCentreLongitudeWGS84| TEXT  | Longitude of the local authority center in WGS84 format |

### sites

| Column                | Type  | Description                              |
|-----------------------|-------|------------------------------------------|
| SiteCode              | TEXT  | Primary key                              |
| SiteName              | TEXT  | Name of the site                         |
| SiteType              | TEXT  | Type of the site (e.g., Suburban, Urban) |
| Latitude              | TEXT  | Latitude of the site                     |
| Longitude             | TEXT  | Longitude of the site                    |
| LatitudeWGS84         | TEXT  | Latitude of the site in WGS84 format     |
| LongitudeWGS84        | TEXT  | Longitude of the site in WGS84 format    |
| BulletinDate          | TEXT  | Date of the bulletin                     |
| LocalAuthorityCode    | TEXT  | Foreign key referencing authorities      |

### species

| Column                | Type  | Description                              |
|-----------------------|-------|------------------------------------------|
| SpeciesCode           | TEXT  | Code of the species                      |
| SpeciesDescription    | TEXT  | Description of the species               |
| AirQualityIndex       | TEXT  | Air quality index for the species        |
| AirQualityBand        | TEXT  | Air quality band for the species         |
| IndexSource           | TEXT  | Source of the index                      |
| SiteCode              | TEXT  | Foreign key referencing sites            |
| SiteName              | TEXT  | Name of the site                         |
| BulletinDate          | TEXT  | Date of the bulletin                     |
