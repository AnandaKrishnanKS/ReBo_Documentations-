# BMAPS_Services

## Description
This repository acts as an index for all services and modules in the BMAPS project.
There are 12 services in total along with the authenticator application:
1. Automatic Stock Replenishment
2. Strategic Plan
3. Range Architecture
4. Option to Buy
5. Assortment Plan​
6. Budget Planning
7. Merchandise Financial Plan​
8. Sales Forecasting​
9. Margin Forecasting
10. WSSI/MSSI
11. Store Grading
12. Option Planning

* [Web Application](https://github.com/Electric-Grasshopper/bmaps_web)
* [Backend API](https://github.com/Electric-Grasshopper/BMAPS_API)

## Tech Stack
* Web Application is built with [NextJS](https://nextjs.org/)
* API is built with [FastAPI](https://fastapi.tiangolo.com/)

### Programming Languages
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54) ![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white) 
### Frameworks
![FastAPI](https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi) ![NextJS](https://img.shields.io/badge/next%20js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white)
### UI Kits
![TailwindCSS](https://img.shields.io/badge/tailwindcss-%2338B2AC.svg?style=for-the-badge&logo=tailwind-css&logoColor=white) 
### Tools
![Webpack](https://img.shields.io/badge/webpack-%238DD6F9.svg?style=for-the-badge&logo=webpack&logoColor=black) ![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white) ![Nginx](https://img.shields.io/badge/nginx-%23009639.svg?style=for-the-badge&logo=nginx&logoColor=white) 
### Operating System
![Ubuntu](https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)  
### Database
![Maria DB](https://img.shields.io/badge/MariaDB-003545?style=for-the-badge&logo=mariadb&logoColor=white) 

## BMAPS API
BMAPS API is developed with FastAPI in a monolithic architecture. Every service communicates with the API and authenticates via token generated via Authentication app.

## Build Instructions
### All in one server
If you want to deploy the entire project in a single server then you may follow the steps below:
1. Clone the repository
```
  git clone --recurse-submodules -j8 https://github.com/Electric-Grasshopper/BMAPS_Services
```
2. Build and Start the Services (note: docker-compose file is being written)
```
  docker-compose up --build
```
3. Stop the services
```
  docker-compose down
```

### Separate services
If you want to run each service in separate server then you may follow the build instructions in the service repository
