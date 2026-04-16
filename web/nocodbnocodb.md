---
title: "nocodb/nocodb: 🔥 🔥 🔥 A Free & Self-hostable Airtable Alternative"
source: "https://github.com/nocodb/nocodb"
author:
published:
created: 2026-04-16
description: "🔥 🔥 🔥 A Free & Self-hostable Airtable Alternative. Contribute to nocodb/nocodb development by creating an account on GitHub."
tags:
  - "clippings"
---
NocoDB is the fastest and easiest way to build databases online.

[**Website**](http://www.nocodb.com/) • [**Discord**](https://discord.gg/c7GEYrvFtT) • [**Community**](https://community.nocodb.com/) • [**Twitter**](https://twitter.com/nocodb) • [**Reddit**](https://www.reddit.com/r/NocoDB/) • [**Documentation**](https://docs.nocodb.com/)

![video avi](https://private-user-images.githubusercontent.com/86527202/277104231-e2fad786-f211-4dcb-9bd3-aaece83a6783.gif?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNTQxMDAsIm5iZiI6MTc3NjM1MzgwMCwicGF0aCI6Ii84NjUyNzIwMi8yNzcxMDQyMzEtZTJmYWQ3ODYtZjIxMS00ZGNiLTliZDMtYWFlY2U4M2E2NzgzLmdpZj9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDE1MzY0MFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTM2OGRkZGIzZDJmYzliYmRhNTY1ODBkOGYwM2ZlNGU4ODczMTBiZTc3OTMyMjgxY2U5YzJjNWU4Nzc4Y2JhNTQmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRmdpZiJ9.QYIXQeJCB-UTWDJLN9HxGRR6n3gqiu8PvsckTBrHsTM)

[![](https://user-images.githubusercontent.com/61551451/135263434-75fe793d-42af-49e4-b964-d70920e41655.png)](https://github.com/nocodb/nocodb/blob/develop/markdown/readme/languages/chinese.md) [![](https://user-images.githubusercontent.com/61551451/135263474-787d71e7-3a87-42a8-92a8-be1d1f55413d.png)](https://github.com/nocodb/nocodb/blob/develop/markdown/readme/languages/french.md) [![](https://user-images.githubusercontent.com/61551451/135263531-fae58600-6616-4b43-95a0-5891019dd35d.png)](https://github.com/nocodb/nocodb/blob/develop/markdown/readme/languages/german.md) [![](https://user-images.githubusercontent.com/61551451/135263589-3dbeda9a-0d2e-4bbd-b1fc-691404bb74fb.png)](https://github.com/nocodb/nocodb/blob/develop/markdown/readme/languages/spanish.md) [![](https://user-images.githubusercontent.com/61551451/135263669-f567196a-d4e8-4143-a80a-93d3be32ba90.png)](https://github.com/nocodb/nocodb/blob/develop/markdown/readme/languages/portuguese.md) [![](https://user-images.githubusercontent.com/61551451/135263707-ba4e04a4-268a-4626-91b8-048e572fd9f6.png)](https://github.com/nocodb/nocodb/blob/develop/markdown/readme/languages/italian.md) [![](https://user-images.githubusercontent.com/61551451/135263770-38e3e79d-11d4-472e-ac27-ae0f17cf65c4.png)](https://github.com/nocodb/nocodb/blob/develop/markdown/readme/languages/japanese.md) [![](https://user-images.githubusercontent.com/61551451/135263822-28fce9de-915a-44dc-962d-7a61d340e91d.png)](https://github.com/nocodb/nocodb/blob/develop/markdown/readme/languages/korean.md) [![](https://user-images.githubusercontent.com/61551451/135263888-151d4ad1-7084-4943-97c9-56f28cd40b80.png)](https://github.com/nocodb/nocodb/blob/develop/markdown/readme/languages/russian.md)

[**See other languages »**](https://github.com/nocodb/nocodb/blob/develop/markdown/readme/languages/README.md)

## Join Our Community

[![](https://camo.githubusercontent.com/2016788104963fdc93d8f26743d3f68b4bcb5a4c221e327293f006ca4108232e/68747470733a2f2f646973636f72646170702e636f6d2f6170692f6775696c64732f3636313930353435353839343838383439302f7769646765742e706e673f7374796c653d62616e6e657233)](https://discord.gg/c7GEYrvFtT)

[![Stargazers repo roster for @nocodb/nocodb](https://camo.githubusercontent.com/18b72b6b150c9851a96d6f2d9d6827ac4bff701abce6c6f5c6c18f7c16f9c4fa/687474703a2f2f7265706f726f737465722e636f6d2f73746172732f6e6f636f64622f6e6f636f6462)](https://github.com/nocodb/nocodb/stargazers)

## Installation

## Docker with SQLite

```
docker run -d \
  --name noco \
  -v "$(pwd)"/nocodb:/usr/app/data/ \
  -p 8080:8080 \
  nocodb/nocodb:latest
```

## Docker with PG

```
docker run -d \
  --name noco \
  -v "$(pwd)"/nocodb:/usr/app/data/ \
  -p 8080:8080 \
  -e NC_DB="pg://host.docker.internal:5432?u=root&p=password&d=d1" \
  -e NC_AUTH_JWT_SECRET="569a1821-0a93-45e8-87ab-eb857f20a010" \
  nocodb/nocodb:latest
```

## Auto-upstall

Auto-upstall is a single command that sets up NocoDB on a server for production usage. Behind the scenes it auto-generates docker-compose for you.

```
bash <(curl -sSL http://install.nocodb.com/noco.sh) <(mktemp)
```

Auto-upstall does the following: 🕊

- 🐳 Automatically installs all pre-requisites like docker, docker-compose
- 🚀 Automatically installs NocoDB with PostgreSQL, Redis, Minio, Traefik gateway using Docker Compose. 🐘 🗄️ 🌐
- 🔄 Automatically upgrades NocoDB to the latest version when you run the command again.
- 🔒 Automatically setups SSL and also renews it. Needs a domain or subdomain as input while installation.

> install.nocodb.com/noco.sh script can be found [here in our github](https://raw.githubusercontent.com/nocodb/nocodb/develop/docker-compose/1_Auto_Upstall/noco.sh)

## Other Methods

> Binaries are only for quick testing locally.

| Install Method | Command to install |
| --- | --- |
| 🍏 MacOS arm64   (Binary) | `curl http://get.nocodb.com/macos-arm64 -o nocodb -L && chmod +x nocodb && ./nocodb` |
| 🍏 MacOS x64   (Binary) | `curl http://get.nocodb.com/macos-x64 -o nocodb -L && chmod +x nocodb && ./nocodb` |
| 🐧 Linux arm64   (Binary) | `curl http://get.nocodb.com/linux-arm64 -o nocodb -L && chmod +x nocodb && ./nocodb` |
| 🐧 Linux x64   (Binary) | `curl http://get.nocodb.com/linux-x64 -o nocodb -L && chmod +x nocodb && ./nocodb` |
| 🪟 Windows arm64   (Binary) | `iwr http://get.nocodb.com/win-arm64.exe -OutFile Noco-win-arm64.exe && .\Noco-win-arm64.exe` |
| 🪟 Windows x64   (Binary) | `iwr http://get.nocodb.com/win-x64.exe -OutFile Noco-win-x64.exe && .\Noco-win-x64.exe` |

> When running locally access nocodb by visiting: [http://localhost:8080/dashboard](http://localhost:8080/dashboard)

For more installation methods, please refer to [our docs](https://nocodb.com/docs/self-hosting)

## Screenshots

[![2](https://private-user-images.githubusercontent.com/86527202/266776344-a127c05e-2121-4af2-a342-128e0e2d0291.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNTQxMDAsIm5iZiI6MTc3NjM1MzgwMCwicGF0aCI6Ii84NjUyNzIwMi8yNjY3NzYzNDQtYTEyN2MwNWUtMjEyMS00YWYyLWEzNDItMTI4ZTBlMmQwMjkxLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDE1MzY0MFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTk2ZTUzNzJlZGIxMjE4ZDQwZjI1NmE3OTU5N2E0NjljYmY5OGFhNGJkOWU3MDRmMDcyNGU5MjBkYzJkNjJlYjEmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.r_QlgdgpLKmMlXDO-l-l0Ql6tn4jvAfd9zC_hmoQfq0)](https://private-user-images.githubusercontent.com/86527202/266776344-a127c05e-2121-4af2-a342-128e0e2d0291.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNTQxMDAsIm5iZiI6MTc3NjM1MzgwMCwicGF0aCI6Ii84NjUyNzIwMi8yNjY3NzYzNDQtYTEyN2MwNWUtMjEyMS00YWYyLWEzNDItMTI4ZTBlMmQwMjkxLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDE1MzY0MFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTk2ZTUzNzJlZGIxMjE4ZDQwZjI1NmE3OTU5N2E0NjljYmY5OGFhNGJkOWU3MDRmMDcyNGU5MjBkYzJkNjJlYjEmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.r_QlgdgpLKmMlXDO-l-l0Ql6tn4jvAfd9zC_hmoQfq0) [![3](https://private-user-images.githubusercontent.com/86527202/266776364-674da952-8a06-4848-a0e8-a7b02d5f5c88.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNTQxMDAsIm5iZiI6MTc3NjM1MzgwMCwicGF0aCI6Ii84NjUyNzIwMi8yNjY3NzYzNjQtNjc0ZGE5NTItOGEwNi00ODQ4LWEwZTgtYTdiMDJkNWY1Yzg4LnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDE1MzY0MFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTNiODNjNzgxNjA4ZjM4NDM5NDBmYWU0NDhkMjVlZGQ4ZTIwMzc5YWNlNTM5MWQ1MDBhYWZkZGE5MTRhMDk0MWEmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.76-9cwqviaGp-AWGbn8AFij2hk1jnBsStgCnB0pdOMA)](https://private-user-images.githubusercontent.com/86527202/266776364-674da952-8a06-4848-a0e8-a7b02d5f5c88.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNTQxMDAsIm5iZiI6MTc3NjM1MzgwMCwicGF0aCI6Ii84NjUyNzIwMi8yNjY3NzYzNjQtNjc0ZGE5NTItOGEwNi00ODQ4LWEwZTgtYTdiMDJkNWY1Yzg4LnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDE1MzY0MFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTNiODNjNzgxNjA4ZjM4NDM5NDBmYWU0NDhkMjVlZGQ4ZTIwMzc5YWNlNTM5MWQ1MDBhYWZkZGE5MTRhMDk0MWEmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.76-9cwqviaGp-AWGbn8AFij2hk1jnBsStgCnB0pdOMA) [![4](https://private-user-images.githubusercontent.com/86527202/266776365-cbc5152a-9caf-4f77-a8f7-92a9d06d025b.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNTQxMDAsIm5iZiI6MTc3NjM1MzgwMCwicGF0aCI6Ii84NjUyNzIwMi8yNjY3NzYzNjUtY2JjNTE1MmEtOWNhZi00Zjc3LWE4ZjctOTJhOWQwNmQwMjViLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDE1MzY0MFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWU3ODdhNjZkNzc1MjBkMjg1YTM5ZmY4ZjM5MTFkM2Y5ZmU5ZWNlMWNmZGNkZDA3NmZjN2IyNDRlZTczNGIzNzEmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.BI2GCzdkZm87cDz-vf95bPFMOxAQhCQx6AsX3FR5KMU)](https://private-user-images.githubusercontent.com/86527202/266776365-cbc5152a-9caf-4f77-a8f7-92a9d06d025b.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNTQxMDAsIm5iZiI6MTc3NjM1MzgwMCwicGF0aCI6Ii84NjUyNzIwMi8yNjY3NzYzNjUtY2JjNTE1MmEtOWNhZi00Zjc3LWE4ZjctOTJhOWQwNmQwMjViLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDE1MzY0MFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWU3ODdhNjZkNzc1MjBkMjg1YTM5ZmY4ZjM5MTFkM2Y5ZmU5ZWNlMWNmZGNkZDA3NmZjN2IyNDRlZTczNGIzNzEmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.BI2GCzdkZm87cDz-vf95bPFMOxAQhCQx6AsX3FR5KMU) [![5](https://private-user-images.githubusercontent.com/86527202/266776368-dc75dfdc-c486-4f5a-a853-2a8f9e6b569a.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNTQxMDAsIm5iZiI6MTc3NjM1MzgwMCwicGF0aCI6Ii84NjUyNzIwMi8yNjY3NzYzNjgtZGM3NWRmZGMtYzQ4Ni00ZjVhLWE4NTMtMmE4ZjllNmI1NjlhLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDE1MzY0MFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWJkNzlhYjZhMGRlNjZjY2MwMGYyZWE4ZGE4NjUyNjZlMDFkYWU4YTRmNDgzOTA1YjNjMDVmM2ZkODVlODFkOGYmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.GsZQEGtku6runG-mnkMRltcZSv4ZVS5zp6pBzzFSEhE)](https://private-user-images.githubusercontent.com/86527202/266776368-dc75dfdc-c486-4f5a-a853-2a8f9e6b569a.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNTQxMDAsIm5iZiI6MTc3NjM1MzgwMCwicGF0aCI6Ii84NjUyNzIwMi8yNjY3NzYzNjgtZGM3NWRmZGMtYzQ4Ni00ZjVhLWE4NTMtMmE4ZjllNmI1NjlhLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDE1MzY0MFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWJkNzlhYjZhMGRlNjZjY2MwMGYyZWE4ZGE4NjUyNjZlMDFkYWU4YTRmNDgzOTA1YjNjMDVmM2ZkODVlODFkOGYmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.GsZQEGtku6runG-mnkMRltcZSv4ZVS5zp6pBzzFSEhE)[![7](https://private-user-images.githubusercontent.com/86527202/266776445-be64e619-7295-43e2-aa95-cace4462b17f.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNTQxMDAsIm5iZiI6MTc3NjM1MzgwMCwicGF0aCI6Ii84NjUyNzIwMi8yNjY3NzY0NDUtYmU2NGU2MTktNzI5NS00M2UyLWFhOTUtY2FjZTQ0NjJiMTdmLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDE1MzY0MFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTY4YjlkZmE0OGNjOTQxMTRlNWIxODUzOTIyZTg2NGNjNThiMGY5MjYxN2I1Njg1MTA3OWMwODdjODc4MmI3ZmMmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.wnPELb9Dv2camNlmVjHggzScxD5n3js8TAsSvTCBFs0)](https://private-user-images.githubusercontent.com/86527202/266776445-be64e619-7295-43e2-aa95-cace4462b17f.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNTQxMDAsIm5iZiI6MTc3NjM1MzgwMCwicGF0aCI6Ii84NjUyNzIwMi8yNjY3NzY0NDUtYmU2NGU2MTktNzI5NS00M2UyLWFhOTUtY2FjZTQ0NjJiMTdmLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDE1MzY0MFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTY4YjlkZmE0OGNjOTQxMTRlNWIxODUzOTIyZTg2NGNjNThiMGY5MjYxN2I1Njg1MTA3OWMwODdjODc4MmI3ZmMmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.wnPELb9Dv2camNlmVjHggzScxD5n3js8TAsSvTCBFs0) [![8](https://private-user-images.githubusercontent.com/86527202/266776478-4538bf5a-371f-4ec1-a867-8197e5824286.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNTQxMDAsIm5iZiI6MTc3NjM1MzgwMCwicGF0aCI6Ii84NjUyNzIwMi8yNjY3NzY0NzgtNDUzOGJmNWEtMzcxZi00ZWMxLWE4NjctODE5N2U1ODI0Mjg2LnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDE1MzY0MFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTFkZmNiYjBmODZiYWEzYTkxMWMwMTA2ZTUwZmFhZDkyYzU4MWE4NzExMmU0MzJjYjg4NGM0ZDUzODNkYTYzOWUmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.JNK_NvfVGxiIzKtE9uxDnSBfPOFfiI36MEfebqA3xGg)](https://private-user-images.githubusercontent.com/86527202/266776478-4538bf5a-371f-4ec1-a867-8197e5824286.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNTQxMDAsIm5iZiI6MTc3NjM1MzgwMCwicGF0aCI6Ii84NjUyNzIwMi8yNjY3NzY0NzgtNDUzOGJmNWEtMzcxZi00ZWMxLWE4NjctODE5N2U1ODI0Mjg2LnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDE1MzY0MFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTFkZmNiYjBmODZiYWEzYTkxMWMwMTA2ZTUwZmFhZDkyYzU4MWE4NzExMmU0MzJjYjg4NGM0ZDUzODNkYTYzOWUmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.JNK_NvfVGxiIzKtE9uxDnSBfPOFfiI36MEfebqA3xGg)[![9](https://user-images.githubusercontent.com/35857179/194844897-cfd79946-e413-4c97-b16d-eb4d7678bb79.png)](https://user-images.githubusercontent.com/35857179/194844897-cfd79946-e413-4c97-b16d-eb4d7678bb79.png) [![10](https://user-images.githubusercontent.com/35857179/194844902-c0122570-0dd5-41cf-a26f-6f8d71fefc99.png)](https://user-images.githubusercontent.com/35857179/194844902-c0122570-0dd5-41cf-a26f-6f8d71fefc99.png) [![11](https://user-images.githubusercontent.com/35857179/194844903-c1e47f40-e782-4f5d-8dce-6449cc70b181.png)](https://user-images.githubusercontent.com/35857179/194844903-c1e47f40-e782-4f5d-8dce-6449cc70b181.png) [![12](https://user-images.githubusercontent.com/35857179/194844907-09277d3e-cbbf-465c-9165-6afc4161e279.png)](https://user-images.githubusercontent.com/35857179/194844907-09277d3e-cbbf-465c-9165-6afc4161e279.png)

## Features

### Rich Spreadsheet Interface

- ⚡ Basic Operations: Create, Read, Update and Delete Tables, Columns, and Rows
- ⚡ Fields Operations: Sort, Filter, Group, Hide / Unhide Columns
- ⚡ Multiple Views Types: Grid (By default), Gallery, Form, Kanban and Calendar View
- ⚡ View Permissions Types: Collaborative Views, & Locked Views
- ⚡ Share Bases / Views: either Public or Private (with Password Protected)
- ⚡ Variant Cell Types: ID, Links, Lookup, Rollup, SingleLineText, Attachment, Currency, Formula, User, etc
- ⚡ Access Control with Roles: Fine-grained Access Control at different levels
- ⚡ and more...

### App Store for Workflow Automations

We provide different integrations in three main categories. See [App Store](https://docs.nocodb.com/account-settings/oss-specific-details/#app-store) for details.

- ⚡ Chat: Slack, Discord, Mattermost, and etc
- ⚡ Email: AWS SES, SMTP, MailerSend, and etc
- ⚡ Storage: AWS S3, Google Cloud Storage, Minio, and etc

### Programmatic Access

We provide the following ways to let users programmatically invoke actions. You can use a token (either JWT or Social Auth) to sign your requests for authorization to NocoDB.

- ⚡ REST APIs
- ⚡ NocoDB SDK

## Contributing

Please refer to [Contribution Guide](https://github.com/nocodb/nocodb/blob/master/.github/CONTRIBUTING.md).

## Why are we building this?

Most internet businesses equip themselves with either spreadsheet or a database to solve their business needs. Spreadsheets are used by Billion+ humans collaboratively every single day. However, we are way off working at similar speeds on databases which are way more powerful tools when it comes to computing. Attempts to solve this with SaaS offerings have meant horrible access controls, vendor lock-in, data lock-in, abrupt price changes & most importantly a glass ceiling on what's possible in the future.

## Our Mission

Our mission is to provide the most powerful no-code interface for databases, accessible to every internet business across the world. By making this capability broadly available under a fair and sustainable model, we aim to democratise access to powerful computing tools and enable a billion-plus people to develop radical tinkering and building abilities on the internet.

## License

This project is licensed under [Sustainable Use License](https://github.com/nocodb/nocodb/blob/develop/LICENSE).

## Contributors

Thank you for your contributions! We appreciate all the contributions from the community.

[![](https://camo.githubusercontent.com/c55bd2da423bfe1d9874127894b48cbdb759693046c5d20287ec4a4b23e8a70a/68747470733a2f2f636f6e747269622e726f636b732f696d6167653f7265706f3d6e6f636f64622f6e6f636f6462)](https://github.com/nocodb/nocodb/graphs/contributors)