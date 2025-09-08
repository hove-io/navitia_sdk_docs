---
title: Expert iOS 2.9.1 - Changelog - Navitia SDK Docs
---

# Expert iOS 2.9.1 Changelog

<h2>🗓 24 Mar 2025</h2>

#### Tasks
- Removed Alamofire dependency and replaced it with native `URLRequest` for lighter networking
- Added handling for "no internet connection" errors to improve user feedback

#### Fixes
- Handled nullable arrays in model decoding
- Fixed issue with status code error handling to improve API response management
- Corrected query parameter encoding to ensure proper API requests
