# ghost

```yalm
version: "3"

services:

  ghost:
    image: hasangnu/ghost
    volumes:
      - ./ghost-data:/var/lib/ghost/content
    environment:
      - url=https://ghost.hasanucar.xyz
      - database__client=mysql
      - database__connection__host=db
      - database__connection__user=example
      - database__connection__password=example
      - database__connection__database=example
      - VIRTUAL_PORT=2368
    ports:
      - "8080:2368"
    networks:
      - ghost
    depends_on:
      - db
    restart: unless-stopped

  db:
    image: hasangnu/mariadb
    volumes:
      - ./mariadb-data:/var/lib/mysql
    environment:
      - MYSQL_ROOT_PASSWORD=example
      - MYSQL_DATABASE=example
      - MYSQL_USER=example
      - MYSQL_PASSWORD=secret
    networks:
      - ghost
    restart: unless-stopped

networks:
  ghost:
```
