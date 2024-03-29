#### Steps for 1)

- run the Docker container from the public docker registry: `docker run -p 8080:80 awesometechnologies/synapse-admin` or use the [docker-compose.yml](docker-compose.yml): `docker-compose up -d`

  > note: if you're building on an architecture other than amd64 (for example a raspberry pi), make sure to define a maximum ram for node. otherwise the build will fail.

  ```yml
  version: "3"

  services:
    synapse-admin:
      container_name: synapse-admin
      hostname: synapse-admin
      build:
        context: .
        # args:
        #   - NODE_OPTIONS="--max_old_space_size=1024"
        #   # see #266, PUBLIC_URL must be without surrounding quotation marks
        #   - PUBLIC_URL=/synapse-admin
        #   - REACT_APP_SERVER="https://matrix.example.com"
      ports:
        - "8080:80"
      restart: unless-stopped
  ```

- browse to http://localhost:8080
# textrp-synapse-admin
