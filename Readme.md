# construindo a imagem do redis 

```bash
docker build -t nomes_redis:1 -f build/Dockerfile-redis .
```

# construindo a imagem do redis 

```bash
docker build -t nomes_app:1 -f build/Dockerfile-app .
```

# Criando a rede

```bash
docker network create nomes_network
```

# Colocando o redis na rede correta

```bash
docker run -d --name servidor_redis --network nomes_network nomes_redis:1
```

# Rodar a aplicacao

```bash
docker run -d -e REDIS_HOST=servidor_redis -e REDIS_CHAVE_NOMES=nomes --network nomes_network -p 8000:5000 --name servidor_aplicacao nomes_app:1 
```