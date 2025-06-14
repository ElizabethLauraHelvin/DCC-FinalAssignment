1. Jalankan melalui terminal
	docker build -t nodejs-app .
	docker run -d -p 3000:3000 --name node-js nodejs-app

2. Jalankan app di web browser melalui http://localhost:3000
