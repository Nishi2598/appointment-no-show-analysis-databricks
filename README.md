# appointment-no-show-analysis-databricks
Healthcare analytics project analyzing patient appointment no-shows using Databricks SQL.
%sql 
SELECT 
  COUNT(*) AS total_appointments,
  SUM(no_show_flag) AS total_no_shows,
  ROUND(100.0 * AVG(no_show_flag), 2) AS no_show_rate_percent
FROM appointments_clean;

<img width="726" height="140" alt="image" src="https://github.com/user-attachments/assets/bccfdaa3-4d0a-45d5-8b00-cbc51392c119" />


SELECT 
  Gender,
  COUNT(*) AS total_appts,
  ROUND(100.0 * AVG(no_show_flag), 2) AS no_show_rate_percent
FROM appointments_clean
GROUP BY Gender
ORDER BY no_show_rate_percent DESC;

SELECT
  CASE 
    WHEN age < 18 THEN '0-17'
    WHEN age BETWEEN 18 AND 35 THEN '18-35'
    WHEN age BETWEEN 36 AND 55 THEN '36-55'
    WHEN age BETWEEN 56 AND 75 THEN '56-75'
    ELSE '75+'
  END AS age_group,
  COUNT(*) AS total_appts,
  ROUND(100.0 * AVG(no_show_flag), 2) AS no_show_rate_percent
FROM appointments_clean
GROUP BY age_group
ORDER BY age_group;

SELECT
  sms_received,
  COUNT(*) AS total_appts,
  ROUND(100.0 * AVG(no_show_flag), 2) AS no_show_rate_percent
FROM appointments_clean
GROUP BY sms_received;

SELECT
  CASE 
    WHEN wait_days <= 0 THEN '0 or less'
    WHEN wait_days BETWEEN 1 AND 3 THEN '1-3 days'
    WHEN wait_days BETWEEN 4 AND 7 THEN '4-7 days'
    WHEN wait_days BETWEEN 8 AND 14 THEN '8-14 days'
    WHEN wait_days BETWEEN 15 AND 30 THEN '15-30 days'
    ELSE '30+ days'
  END AS wait_bucket,
  COUNT(*) AS total_appts,
  ROUND(100.0 * AVG(no_show_flag), 2) AS no_show_rate_percent
FROM appointments_clean
GROUP BY wait_bucket
ORDER BY wait_bucket;

SELECT
  hypertension,
  COUNT(*) AS total_appts,
  ROUND(100.0 * AVG(no_show_flag), 2) AS no_show_rate_percent
FROM appointments_clean
GROUP BY hypertension;

SELECT
  Neighbourhood,
  COUNT(*) AS total_appts,
  ROUND(100.0 * AVG(no_show_flag), 2) AS no_show_rate_percent
FROM appointments_clean
GROUP BY Neighbourhood
HAVING COUNT(*) >= 100   -- only neighbourhoods with enough data
ORDER BY no_show_rate_percent DESC
LIMIT 15;
