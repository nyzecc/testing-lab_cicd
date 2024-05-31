# Testing Lab

## CICD
### touch cicd.yaml
```
mkdir .github/workflows
touch .github/workflows/ci.yaml
touch .github/workflows/cd.yaml
```

### change cy:test command "no-exit"
`frontend/package.json`
```diff
{
  "name": "frontend",
  "private": true,
  "version": "0.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "tsc && vite build",
    "lint": "eslint . --ext ts,tsx --report-unused-disable-directives --max-warnings 0",
    "preview": "vite preview",
-    "cy:test": "cypress run --headed --no-exit"
+    "cy:test": "cypress run --headed"
  },
```

### create PAT
for ci formatter commit, download artifacts?
```
https://github.com/settings/tokens
```
<img width="348" alt="image" src="https://github.com/nyzecc/testing-lab_cicd/assets/65904378/b215fc7a-bbc6-4889-b9c6-014d023957bc">


### add Actions secrets and variables
paste PAT key
`ghp_xxxxxxxxx`
```
https://github.com/nyzecc/testing-lab_cicd/settings/secrets/actions
```
<img width="1237" alt="image" src="https://github.com/nyzecc/testing-lab_cicd/assets/65904378/c19974b0-ef6b-44e9-becd-2174ad47d733">


### add Action Runners
to your GCP or other device
```
https://github.com/nyzecc/testing-lab_cicd/settings/actions/runners
```
<img width="1193" alt="image" src="https://github.com/nyzecc/testing-lab_cicd/assets/65904378/86f50037-c720-4cfa-bdf8-c27d77876738">

### run CICD
<img width="932" alt="image" src="https://github.com/nyzecc/testing-lab_cicd/assets/65904378/683e8931-94e7-4170-b623-b271c19a363c">

<img width="1278" alt="image" src="https://github.com/nyzecc/testing-lab_cicd/assets/65904378/45541c43-309c-42ac-a6a2-3d0bb6ad711a">

### note
```
一定要先 ci 包一份 artifacts 上去
因為跑 ci 前會先說抓上一份成工的 artifacts ，抓不到會噴錯
```

----


## Backend

Fastify Server

### Set your environment variable

```
cd backend
cp .env.sample .env
```

### Development

Run a mongo container
```
docker run -d -p 27017:27017 mongo
```

Install dependencies
```
npm install
```

Start development mode
```
npm run dev
```

### Run the test

```
npm run test
```

## Frontend

React (by vite)

### Development

Install dependencies
```
npm install
```

Start development mode
```
cd frontend
npm run dev
```

Visit
http://localhost:5173

### Run cypress test

```
npm run cy:test
```
