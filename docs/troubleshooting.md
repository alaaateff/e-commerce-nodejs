Dockerfile:15
--------------------
  13 |     COPY "../app/e-commerce-nodejs/public" ./public
  14 |     COPY "../app/e-commerce-nodejs/Routes" ./Routes
  15 | >>> COPY "../app/e-commerce-nodejs/Utils" ./Utils
  16 |     # COPY "../app/e-commerce-nodejs/.env.example" ./
  17 |     # COPY "../app/e-commerce-nodejs/server.js" ./
--------------------
ERROR: failed to build: failed to solve: failed to compute cache key: failed to calculate checksum of ref hbwlmw0glgjpww9l61jh9al3d::tb93eyuxhgis0pivsmqhehrei: "/app/e-commerce-nodejs/Utils": not found

-> This error because copy can't see files outside the build context despite the location of the dockerfile

solution:
I built the image in the root folder of the application and modify the copy to be "app/e-commerce-nodejs/Utils" ./Utils
and the build will contain -f docker/Dockerfile . , the dot means that the docker see all folders and files exist here and there's another solution that you move dockerfile inside the app folder and modify the copy to be Utils ./Utils

==============================================================================================================================

The error in "docker compose up" command because I put docker-compose.yml in docker folder and the app is outside this folder and must docker compose up in the same location docker-compose file exists
solution: 
instead of "build: ." in app service you can make it like this:

build:
context: ..     -> means it will go to the parent directory
dockerfile: docker/Dockerfile -> tells exactly what the dockerfile location

==============================================================================================================================
