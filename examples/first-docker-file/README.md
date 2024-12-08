Bind Mounts:

You’re in development mode, and you want real-time updates to your code without rebuilding or restarting the container every time you make a change.

Project Structure on Host:
/home/ubuntu/Docker-Zero-to-Hero/examples/first-docker-file
 ├── app.py
 ├── Dockerfile


Build docker image:
docker build -t dockerimagename .

Run the Container with Bind Mount:
docker run -v /home/ubuntu/Docker-Zero-to-Hero/examples/first-docker-file:/app -it <image-id>
