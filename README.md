# dmarc-visualizer

*Please note that this is a **fork** of dmarc-visualizer, and the intention is to keep a maintained and up-to-date version available, as the original repo has not been taken care of for quite some time. Credits goes to the original creator for the original work.*

Analyse and visualize DMARC results using open-source tools.

* [parsedmarc](https://github.com/domainaware/parsedmarc) for parsing DMARC reports,
* [Elasticsearch](https://www.elastic.co/) to store aggregated data.
* [Grafana](https://grafana.com/) to visualize the aggregated reports.

If anything is unclear, feel free to open a new issue on this repo, and I will take a look.

## How to use

NB: This project requires you to have Docker installed and running on your system, and that you have the docker compose plugin installed. (https://docs.docker.com/compose/install/)

1. In order to get started, please clone the repo. You will need all files in order to build the containers.
2. Get hold of all your dmarc reports. Extract them from your archives (*from .xml.gz --> .xml or from .zip --> .xml*). Put all your extracted reports inside the folder `/data/parsedmarc/files`. If the folder path does not exist, you can create it.
3. Run the project. From inside the root folder, do `docker compose up -d`. The containers will build and get sat up according to configuration in docker-compose.yml
4. In order to see logs, you can do `docker compose logs -f`. For a specific container, you can do it for either elasticsearch, parsedmarc or grafana: `docker compose logs -f parsedmarc`
5. Depending on the amount of files and the size of them, the parsing can take a long time. When `parsedmarc` is done, the container will exit gracefully and the data will be visualized in grafana at `[your docker host]:3000`. If you are running it on the same computer, you can reach it at `localhost:3000`.

## Screenshot

![Screenshot of Grafana dashboard](/big_screenshot.png?raw=true)
