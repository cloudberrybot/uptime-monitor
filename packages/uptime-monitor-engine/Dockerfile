# This file is generated by Nx.
#
# Build the docker image with `npx nx docker-build uptime-monitor-engine`.
# Tip: Modify "docker-build" options in project.json to change docker build args.
#
# Run the container with `docker run -p 3000:3000 -t uptime-monitor-engine`.
FROM docker.io/node:lts-alpine

ENV HOST=0.0.0.0
ENV PORT=3000

WORKDIR /app

RUN addgroup --system uptime-monitor-engine && \
          adduser --system -G uptime-monitor-engine uptime-monitor-engine

COPY dist/packages/uptime-monitor-engine uptime-monitor-engine
RUN chown -R uptime-monitor-engine:uptime-monitor-engine .

# You can remove this install step if you build with `--bundle` option.
# The bundled output will include external dependencies.
RUN npm --prefix uptime-monitor-engine --omit=dev -f install

CMD [ "node", "uptime-monitor-engine" ]
