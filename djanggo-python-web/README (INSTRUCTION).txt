1. Aktifkan env djanggo-env
	djanggo-env\Scripts\activate

2. Jalankan melalui terminal
	docker build -t djanggo-web .
	docker run -d --name djanggo-web -p 8000:8000 djanggo-web

3. Jalankan app di web browser melalui http://localhost:8000

