# Exercise: Deploy ReactJS frontend with a NodeJS backend.

Our web application includes a frontend portal and a backend server need to be deployed.
Perform the following steps to deploy our web application:
1. Clone ReactJS frontend repo: https://github.com/thai-nm/sample-webapp-reactjs.git
2. Clone NodeJS backend repo: https://github.com/uet-app-distributor/sample-nodejs-webapp.git
3. Prepare frontend image:
  - Change directory to the frontend repo 
  - Get your host machine IP address in Docker network. This is usually the IP address value of `docker0` network interface.
  - Create if not exists and update the file `.env` with following content. Replace <YOUR_HOST_IP> with the real value you got above.
    ```
    VITE_API_SERVER=http://<YOUR_HOST_IP>:13000
    ```
  - Build your own image with the pre-provided Dockerfile. You should check for the Dockerfile and its build workflow to understand and review about multi-stage and image build process.
4. Prepare backend image:
   - Change directory to the backend repo and build your own image without seeing the pro-provided Dockerfile. After trying to build your own image or being get stuck, you can use the Dockerfile in the repository as a reference.
5. Upload those new images to your own DockerHub account.
6. Develop your own `compose.yml` file for Docker Compose to do the following:
  - Create a new network named `deployment-practice-network`
  - Create 2 services:
    - Service `backend` will create a container name `sample-webapp-nodejs` and refer to the backend image you just pushed above. This service requires environment variables: `USER=practioner-be` and `ENV=dev`. This service will only be exposed at port `13000` of the `0.0.0.0` interface and mapped to port `3000` of the container.
    - Service `frontend` will create a container name `sample-webapp-reactjs` and refer to the frontend image you just pushed above. This service requires environment variables: `USER=practioner-fe` and `ENV=dev`. This service will be exposed at port `18080` of the `0.0.0.0` interface and mapped to port `80` of the container.
7. Deploy with Docker Compose.
8. To check if the containers are working or not, open your browser and go to http://localhost:18080. Then click `Give me a quote`:
  - If there is a quote sent to you, everything is working well!
  - If not, you can debug with F12 Network tab and Console tab as well as contact me for more details.
9. (Optional) After all, you can use `compose-solution.yaml` as a reference.