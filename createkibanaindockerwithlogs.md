# Setting Up Kibana in Docker with Logs

This guide will help you set up Kibana in Docker and access it to view logs.

## Prerequisites

- Docker installed on your machine
- Basic knowledge of Docker and Docker Compose

## Step 1: Create a Docker Compose File

Create a `docker-compose.yml` file with the following content:

```yaml
version: '7'
services:
    elasticsearch:
        image: docker.elastic.co/elasticsearch/elasticsearch:7.10.1
        container_name: elasticsearch
        environment:
            - discovery.type=single-node
        ports:
            - "9200:9200"
        volumes:
            - esdata:/usr/share/elasticsearch/data

    kibana:
        image: docker.elastic.co/kibana/kibana:7.10.1
        container_name: kibana
        ports:
            - "5601:5601"
        environment:
            ELASTICSEARCH_URL: http://elasticsearch:9200

volumes:
    esdata:
        driver: local
```

## Step 2: Start the Docker Containers

Run the following command to start the containers:

```sh
docker-compose up -d
```

## Step 3: Access Kibana

Open your web browser and navigate to `http://localhost:5601`. You should see the Kibana interface.

## Step 4: Configure Kibana to View Logs

1. Go to the **Management** section in Kibana.
2. Click on **Index Patterns** and create a new index pattern.
3. Enter the index name that matches your logs (e.g., `logstash-*`).
4. Follow the prompts to complete the setup.

## Conclusion

You have successfully set up Kibana in Docker and configured it to view logs. You can now use Kibana to analyze and visualize your log data.
