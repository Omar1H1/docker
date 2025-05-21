## How to run my application :

### Locally:

- You need to have rust installed go to [rustup](https://rustup.rs/)
- Build the binary via :

```bash
cargo build
```
This command creates an executable file in target/debug/xxxx (or target\debug\xxxx.exe on Windows) rather than in your current directory. Because the default build is a debug build, Cargo puts the binary in a directory named debug. You can run the executable with this command:

```bash
./target/debug/shop_bin # or .\target\debug\shop_bin.exe on Windows
```

if it all goes well, you will have an error telling you that `rust can't connect to database`, what you need to do is having a postgres running with the following :

- username : postgres
- password : postgres
- host: localhost:5432
- database named : app

or just run this via docker :

```bash
	docker run -d --name postgres -p 5432:5432 \
		-e POSTGRES_DB=app \
		-e POSTGRES_USER=postgres \
		-e POSTGRES_PASSWORD=postgres \
		postgres:latest
	sleep 5
	docker exec -it postgres psql -U postgres -d app -c 'CREATE DATABASE app;' || true
```

now if everything goes will you can re-run the binary with the command :

```bash
./target/debug/shop_bin # or .\target\debug\shop_bin.exe on Windows
```

You should be able to access it on [localhost]("localhost:8080") :bowtie:


