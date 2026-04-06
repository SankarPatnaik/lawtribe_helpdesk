<div align="center" markdown="1">

<img src=".github/hd-logo.svg" alt="LawTribe Helpdesk logo" width="80"/>
<h1>LawTribe Helpdesk</h1>

**Legal Support Operations, Organized and Efficient**

![GitHub release (latest by date)](https://img.shields.io/github/v/release/frappe/helpdesk)
[![codecov](https://codecov.io/github/frappe/helpdesk/branch/develop/graph/badge.svg?token=8ZXHCY4G9U)](https://codecov.io/github/frappe/helpdesk)
</div>

<div align="center">
	<img src="./.github/Hero2.png" alt="LawTribe Helpdesk Hero Image" width="100%" />
</div>
<br />
<div align="center">
	<a href="#overview">Overview</a>
	-
	<a href="#development-setup">Development Setup</a>
	-
	<a href="#contributing">Contributing</a>
</div>

## Overview

LawTribe Helpdesk is LawTribe's ticketing and support workspace, built on top of Frappe Helpdesk. It is designed to support legal operations teams with:

- Faster issue intake and triage
- Consistent client communication
- Clear ownership and SLA tracking
- Knowledge-driven support workflows

## Why LawTribe Helpdesk

LawTribe teams need a support tool that is practical, auditable, and easy to adapt to legal workflows. This repository provides that foundation while keeping all the flexibility of the Frappe ecosystem.

## Key Features

- **Agent & Customer Portals**: Separate, clean views for internal teams and external requesters.
- **SLA Management**: Configure service levels and monitor response and resolution targets.
- **Assignment Automation**: Route tickets by priority, category, or team ownership.
- **Knowledge Base**: Publish and organize articles to reduce repeated support effort.
- **Saved Replies**: Standardize common responses for speed and consistency.

<details open>
<summary>View Screenshots</summary>
<h3></h3>

<div align="center">
	<sub>
		Agent List View
	</sub>
</div>

![Agent List View](.github/AgentListView.png)

<div align="center">
	<sub>
		Knowledge Base for self-serve support and legal process guidance.
	</sub>
</div>

![Knowledge Base](.github/KB.png)

<div align="center">
	<sub>
		Smart search recommendations to help users resolve issues quickly.
	</sub>
</div>

![Article Search](.github/Search2.png)

</details>

## Technology

- [**Frappe Framework**](https://github.com/frappe/frappe): Full-stack framework for backend and data model.
- [**Frappe UI**](https://github.com/frappe/frappe-ui): Vue-based UI library used across the desk application.

## Production Setup

### Managed Hosting

You can deploy via [Frappe Cloud](https://frappecloud.com), which handles infrastructure concerns such as setup, upgrades, monitoring, and maintenance.

### Self Hosting

Follow these steps to set up LawTribe Helpdesk in production:

**Step 1**: Download the easy install script

```bash
wget https://frappe.io/easy-install.py
```

**Step 2**: Run the deployment command

```bash
python3 ./easy-install.py deploy \
    --project=lawtribe_helpdesk_prod \
    --email=your_email@example.com \
    --image=ghcr.io/frappe/helpdesk \
    --version=stable \
    --app=helpdesk \
    --sitename support.yourdomain.tld
```

Replace these parameters with your values:

- `your_email@example.com`: Your email address
- `support.yourdomain.tld`: The domain where LawTribe Helpdesk will be hosted

## Development Setup

### Docker

Ensure Docker, Docker Compose, and Git are installed. Then run:

```bash
mkdir lawtribe-helpdesk
cd lawtribe-helpdesk

# Download docker-compose
wget -O docker-compose.yml https://raw.githubusercontent.com/frappe/helpdesk/develop/docker/docker-compose.yml

# Download setup script
wget -O init.sh https://raw.githubusercontent.com/frappe/helpdesk/develop/docker/init.sh

# Start services
docker compose up -d
```

The site should be available at: [http://helpdesk.localhost:8000/helpdesk](http://helpdesk.localhost:8000/helpdesk)

Default credentials:

- Username: `Administrator`
- Password: `admin`

### Local

To run this repository locally:

1. Install Bench and create a `frappe-bench` directory using the [Frappe installation guide](https://frappeframework.com/docs/user/en/installation).
2. Start services: `bench start`
3. Create site: `bench new-site helpdesk.test`
4. Add hosts mapping: `bench --site helpdesk.test add-to-hosts`
5. Get Telephony app: `bench get-app https://github.com/frappe/telephony`
6. Get Helpdesk app: `bench get-app https://github.com/frappe/helpdesk`
7. Install app: `bench --site helpdesk.test install-app helpdesk`
8. Build assets: `bench build --app helpdesk`
9. Open: `http://helpdesk.test:8000/helpdesk`

### Frontend Development

Use a separate terminal:

```bash
cd frappe-bench/apps/helpdesk/desk
yarn install
yarn dev
# or
yarn dev --host helpdesk.test
```

Vite dev server URL: `http://helpdesk.test:8080`

## Compatibility Matrix

| Helpdesk Branch | Compatible Frappe Framework Version |
|-----------------|-------------------------------------|
| main            | version-15                          |
| main            | version-16                          |
| develop         | develop branch                      |

## Contributing

Contributions are welcome. Please use the same engineering standards used across LawTribe projects:

1. Open an issue for major feature ideas or architectural changes.
2. Keep PRs focused, testable, and well described.
3. Follow existing style and module boundaries.
4. Include migration notes when schema or behavior changes.

## Acknowledgements

This project is based on the open-source [Frappe Helpdesk](https://github.com/frappe/helpdesk) project.
