---
id: 013-find-pypi-downloads.md
title: Python package download stats from PyPI
tags:
  - python
  - pypi
  - pypi-stats
author: Zoran Pandovski
meta-description: Found out the easiest way to get the PyPi downloads statistics
date: 2020-06-17 22:56:36 +0200
keywords: python, pypi, pypi-stats
template: post
categories:
  - python
image: assets/images/python/stats.svg
---

The download stats were removed from PyPi modules. There were few reasons for that as explained in the [mailing list](https://mail.python.org/pipermail/distutils-sig/2013-May/020855.html). So, now the best available option to get the statistics is to use the [Google BigQuery](https://console.cloud.google.com/bigquery?project=the-psf&page=table&t=downloads&d=pypi&p=the-psf) database. To use it you only need a Google account and enabled BigQuery API.
The most useful query is to count the package downloads:

```sql
SELECT
  COUNT(*) AS num_downloads,
  SUBSTR(_TABLE_SUFFIX, 1, 6) AS `month`
FROM `the-psf.pypi.downloads*`
WHERE
  file.project = 'YOUR_PACKAGE_NAME'
  AND
  details.installer.name = 'pip'
  AND _TABLE_SUFFIX
    BETWEEN FORMAT_DATE(
      '%Y%m01', DATE_SUB(CURRENT_DATE(), INTERVAL 10 MONTH))
    AND FORMAT_DATE('%Y%m%d', CURRENT_DATE())
GROUP BY `month`
ORDER BY `month` DESC
```

The above query uses the `the-psf.pypi.downloads` table that contains information about downloads. It selects the package and filters the data to contain only `pip` installs(no mirrors downloads) in the last 10 months.

Other useful columns from the  `the-psf.pypi.downloads` are:

|Column   |  Info | Example   |
|---|---|---|
| file.project  |  The package name | requests  |
| file.version  | Version of the package  | 1.2.1  |
|details.installer.name  | Installer name   | pip, bandersnatch |
| details.python  | Python version  | 2.7, 3.6, 3.7.3  |
