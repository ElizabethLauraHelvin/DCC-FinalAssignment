1. Jalankan melalui terminal
	docker build -t reactjs-app .
	docker run -d -p 3001:80 --name react-container reactjs-app

2. Jalankan app di web browser melalui http://localhost:3001

