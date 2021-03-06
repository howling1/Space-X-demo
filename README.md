# Space-X-demo
A mini website to search and manage Space-X ships, with JAVA, Springboot backend, Vue.js frontend, and MongoDB database. The ship data source is https://api.spacexdata.com/v4/ships

## Prerequisite
To run this system on your local PC(Mac), there are several steps to complete:
1. Download Node.js for frontend: https://nodejs.org/en/download/
2. Download JAVA(JDK 8 or higher version): https://www.oracle.com/java/technologies/downloads/ and IntelliJ IDEA: https://www.jetbrains.com/idea/
3. Download and configure MongoDB locally: https://www.mongodb.com/try/download/community
4. Create an admin user in your MongoDB. You can follow this tutorial: https://docs.mongodb.com/manual/tutorial/configure-scram-client-authentication/. If you are using this tutorial, you are supposed to download the mongosh to interact with your MongoDB: https://docs.mongodb.com/mongodb-shell/#mongodb-binary-bin.mongosh
5. Clone the whole project to your local PC.
6. Import the backend file into your IntelliJ IDEA with Maven. You can follow this tutorial(text part): https://www.jetbrains.com/idea/guide/tutorials/working-with-maven/importing-a-project/
7. Modify the username and password in the file Space-X-demo/backend/src/main/resources/application.yml to your own MongoDB admin user you created in step 4
<img width="1432" alt="image" src="https://user-images.githubusercontent.com/45118918/152965941-36d92925-acb7-4412-8367-1ce98eb3dafe.png">

8. Run your MongoDB service. How to start MongoDB service: https://docs.mongodb.com/manual/tutorial/install-mongodb-on-os-x/
9. Run the main method in the file Space-X-demo/backend/src/main/java/edu/tum/backend/BackendApplication.java to start the backend.
<img width="1435" alt="image" src="https://user-images.githubusercontent.com/45118918/152967010-fbafa7f1-30bf-43bb-afec-ea141382927f.png">

10. Open your terminal and change the current directory to Space-X-demo/frontend, and execute the command "npm install" to install all packages of the frontend.
11. Execute the command "npm run serve -- --port 3000" to start the frontend.
12. Open your browser and access the URL: http://localhost:3000 to use this website.

## System function
1. Ships display: the home page display the basic information of all ships loaded from the Space-X API, including the name, the build year, the total number of ships. By clicking the name, you can be directed to the corresponding website of a specific ship.
<img width="1439" alt="image" src="https://user-images.githubusercontent.com/45118918/152970233-fe8aa488-2037-4d90-a44f-17adc30fe8f0.png">

2. Ship search: you can fuzzy search for ships by name.
<img width="1439" alt="image" src="https://user-images.githubusercontent.com/45118918/152970592-d33119b5-f2ac-4ef3-acb9-3cd2372fdc08.png">

3. Adding new a new ship: You can add a new ship with basic information. the field ID and Name must be not null and different from those of ships in the local database. Otherwise, the request will be refused. The field Link and Build year are optional.
<img width="1439" alt="image" src="https://user-images.githubusercontent.com/45118918/152971434-3b6a6cf8-10fe-4055-95db-bfe4eb94a522.png">

<img width="1439" alt="image" src="https://user-images.githubusercontent.com/45118918/152971607-86d564a5-870a-47fd-8dd4-45fefa05fc75.png">

If the addition is successful, you will get a success notification. The new ship will be added to the display list and the total number of ships will increase by 1.
<img width="1439" alt="image" src="https://user-images.githubusercontent.com/45118918/152972236-191f40a0-5ec6-4d12-9c83-77255a9dd6d3.png">

<img width="1439" alt="image" src="https://user-images.githubusercontent.com/45118918/152972299-f0c70851-63da-4573-953c-3ef2f693eab6.png">

5. Deleting a ship: you can click the corresponding button Delete to delete a specific ship. Then a confirmation notification will be popped up. After confirmation, you will get a success notification if the delete was completed. Then the one you delete will not be displayed because you have deleted it in the local database. The total number of ships will also update.
<img width="1439" alt="image" src="https://user-images.githubusercontent.com/45118918/152972675-ae0a3870-67aa-4479-94a5-c4cece3aae82.png">

<img width="1439" alt="image" src="https://user-images.githubusercontent.com/45118918/152973971-b2e26920-450b-43a3-bead-21b60dc0c89b.png">

<img width="1439" alt="image" src="https://user-images.githubusercontent.com/45118918/152974019-4a060f10-f67b-4edb-ad2a-d15f2fa05211.png">

## Demo
Watch this video demo to know more about the system: https://drive.google.com/file/d/1FLAT86Q_6hFeYqQWXdycP6ErJP9I0OcZ/view?usp=sharing

## Implementation
### Frontend important files:

1. Space-X-demo/frontend/package.json: packages and libraries used in the Vue.js application
2. Space-X-demo/frontend/components/Footer.vue: subcomponent Footer
<img width="1439" alt="image" src="https://user-images.githubusercontent.com/45118918/152957565-e6724d46-8199-4b31-9642-7cb91ae3dafb.png">

3. Space-X-demo/frontend/components/NavBar.vue: the subcomponent NavBar
<img width="1438" alt="image" src="https://user-images.githubusercontent.com/45118918/152952286-68532d61-12f1-432a-88c0-ef42dec8c08d.png">

4. Space-X-demo/frontend/App.vue: the main component of the frontend consisting of the NavBar component, the Footer component, and the corresponding sub-component defined in the router below. The front-end application renders the current entire page through this component.

5. Space-X-demo/frontend/src/router.vue: the route manager managing routes for all pages. We define the URL for each page here.
6. Space-X-demo/frontend/components/Ship.vue: ship subcomponent
<img width="1411" alt="image" src="https://user-images.githubusercontent.com/45118918/152953040-97bc7237-8a49-48bb-8571-d8ed2706cdf4.png">

Space-X-demo/frontend/views/About.vue: the About page(URL:http://localhost:3000/about)
<img width="1439" alt="image" src="https://user-images.githubusercontent.com/45118918/152953353-452e448c-89ea-4559-ae57-45c516371748.png">

7. Space-X-demo/frontend/views/Home.vue: the Home page(URL:http://localhost:3000/)
<img width="1439" alt="image" src="https://user-images.githubusercontent.com/45118918/152953397-05409b6b-78b3-4ddd-8c7a-7fac8edd3067.png">

### Backend important files:

1. Space-X-demo/backend/pom.xml: the project maven file including all packages used in the backend
2. Space-X-demo/backend/src/main/resources/application.yml: the configuration file for the MongoDB database. please change the username, and password according to the user of your local MongoDB if you are running the website on your local PC.
3. Space-X-demo/backend/src/main/java/edu/tum/backend/BackendApplication.java: the backend main execution program, which invokes the method "deleteAllShips" of ShipService to clear the local database when the system is starting.
4. Space-X-demo/backend/src/main/java/edu/tum/backend/model/Ship.java: the ship model used for receiving ship objects from the frontend and the MongoDB database and inserting ship documents into the database
5. Space-X-demo/backend/src/main/java/edu/tum/backend/repository/ShipRepository: the ship repository, where all the database operations(CRUD) are defined
6. Space-X-demo/backend/src/main/java/edu/tum/backend/Service/ShipService: the ship service, where all service methods regarding CRUD are defined
7. Space-X-demo/backend/src/main/java/edu/tum/backend/controller/ShipController: the ship controller, taking responsibility of handling all requests regarding ships from the frontend
8. Space-X-demo/backend/src/main/java/edu/tum/backend/security/CorsConfig: the CORS configuration file, where privileges are defined to allow the frontend to access controller methods of the backend

## Abbreviations
1. CRUD: Create, Read, Update, Delete
2. CORS: Cross-origin resource sharing


