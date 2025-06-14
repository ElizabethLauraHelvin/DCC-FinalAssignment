1. Jalankan melalui terminal
	docker build -t laravel-app .
	docker run -d --rm --name laravel9 -p 9000:80 laravel-app

2. Jalankan app di web browser melalui http://localhost:9000
