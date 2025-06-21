Flask App with MySQL Docker Setup
This is a simple Flask app that interacts with a MySQL database. The app allows users to submit messages, which are then stored in the database and displayed on the frontend.

Prerequisites
Before you begin, make sure you have the following installed:

Docker
Git (optional, for cloning the repository)
Commands
// create network to comunicate between database and backend

docker network create two-tier -d bridge
// build two tier app image
docker build -t two-tier-backend .
// run two tier app
docker run -d -p 5000:5000 --name two-tier-app --network two-tier -e MYSQL_HOST=mysql -e MYSQL_USER=root -e MYSQL_PASSWORD=root -e MYSQL_DB=devops two-tier-backend:Latest
// Mysql database
docker build -d -t mysql .
// run Mysql
docker run -d --name mysql --network two-tier -e MYSQL_ROOT-PASSWORD=root -e MYSQL_DATABASE=devops mysql

