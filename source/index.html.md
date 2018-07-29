---
title: aspace, Inc. API

language_tabs:
  - http: HTTP
  - shell: cURL
  - javascript: Node.js (request)
  - python: Python

toc_footers:
  - <a href='https://api.trya.space/v1'>API (Production)</a>
  - <a href='https://api-dev.trya.space/v1'>API (Development)</a>
  - <a href='https://docs.trya.space/'>API Documentation</a>
  - <a href='https://status.trya.space/'>API Status</a>
  - <a href="https://api.trya.space/v1/admin/get_auth_key/">Auth Keys</a>
  - <a href='https://buddy.trya.space/'>Buddy CI/CD</a>
  - <a href='https://lab.trya.space/'>Data Lab</a>
  - <a href='https://trya.space/'>Main Website</a>

includes:
  - parking
  - routing
  - auth
  - admin
  - errors

search: true
---

# Introduction

Welcome to the aspace API! You can use this API to access the authentication, parking information, and administration endpoints, which can give you various information regarding the aspace applications.

To see samples of how to access this API, you can use the code examples on the dark area on the right, using the "HTTP", "cURL", "node.js (request), and Python tabs.

Because this API is still in active development, there may be inconsistencies with actual API behavior and the described/intended behavior. In this case, please [contact](mailto:help@trya.space) the API administrator **as soon as possible** and include the following info:

* The endpoint affected
* All of the information you sent to the endpoint, including the following
  * Parameters/queries
  * Body
  * Headers
* The information you received
* Any error codes you received that aren't documented in this API documentation

<aside class="notice">
The base URLs for APIs are:
<br>
&emsp;&ensp;<b>Production</b> (Live/Release) API: <a href="https://api.trya.space/v1"><b>https://api.trya.space/v1</b></a>
<br>
&emsp;&ensp;<b>Development</b> API: <a href="https://api-dev.trya.space/v1"><b>https://api-dev.trya.space/v1</b></a>
</aside>

<aside class="warning">
Please note that this documentation is only up-to-date with the <b>production</b> API. The development API may not behave as described in this documentation.
</aside>

<aside class="warning">
For methods that require auth keys, please go <a href="https://api.trya.space/v1/admin/get_auth_key">here</a>. Use your administration credentials to view the webpage, then enter one of the permissions listed below exactly as it appears:
<ul>
  <li><code>upload_spots</code></li>
  <li><code>update_status</code></li>
</ul>
</aside>