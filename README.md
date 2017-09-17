# Ghost on Raspberry Pi

This is a [Docker](https://www.docker.com/) image for [Ghost](https://ghost.org). This image runs with a base of [Hypriot/rpi-node](https://hub.docker.com/r/hypriot/rpi-node/)

This image is also available on [Docker Hub](https://hub.docker.com/r/

## Usage
We recommend using our images in conjunction with [Docker-Compose](https://docs.docker.com/compose/). This allows for easier creation of containers with the proper volumes and ports enabled.

We have included an [example docker-compose](https://github.com/ZZROTDesign/alpine-ghost/blob/master/examples/docker-compose.example.yml) file to show how this image might be used both for development and production in a different project.

This image works out of the box with no volumes. It differs from the official Docker Ghost image by including a config.js file with some env variables defined.

1. DEV_DOMAIN = Is the domain that is reachable on your development machine. This is typically your docker-machine host ip
2. PROD_DOMAIN = When running this image in production (NODE_ENV=production), this is the domain that is used.

This image also runs with containers. It will accept a volume from your ghost content folder, as well as a custom config.js file. These must point to /var/lib/ghost/ - See the [example docker-compose](https://github.com/ZZROTDesign/alpine-ghost/blob/master/examples/docker-compose.example.yml) for specification.

### Available ENV Variables

- DEV_DOMAIN: URL for Ghost Blog running in Development
- DEV_FORCE_ADMIN_SSL: Force SSL (secure HTTP or https) for the admin panel in Development

- PROD_DOMAIN: URL for Ghost Blog running in Production
- PROD_FORCE_ADMIN_SSL: Force SSL (secure HTTP or https) for the admin panel in Production

#### Mail ENV VARIABLES

- DEV_MAIL_TRANSPORT: Type of Transport used for Development Email
- DEV_MAIL_SERVICE: The Service by which email will be sent in Development
- DEV_MAIL_HOST: Hostname of the SMTP server (defaults to "localhost", not needed with DEV_MAIL_SERVICE)
- DEV_MAIL_NAME: The name of the client server (defaults to machine name)
- DEV_MAIL_USER: Username for the Development email service
- DEV_MAIL_PASS: Password for the Development email service
- DEV_MAIL_FROM: Address which the Development email will be sent from
- DEV_MAIL_SECURE_CONNECTION: Use SSL (default is false, not needed with DEV_MAIL_SERVICE)
- DEV_MAIL_PORT: Port of the SMTP server (defaults to 25, not needed with DEV_MAIL_SERVICE)
- DEV_MAIL_IGNORE_TLS: Ignore server support for STARTTLS (defaults to false)
- DEV_MAIL_DEBUG: Output client and server messages to console

- PROD_MAIL_TRANSPORT: Type of Transport used for Production Email
- PROD_MAIL_SERVICE: The Service by which email will be sent in Production
- PROD_MAIL_HOST: Hostname of the SMTP server (defaults to "localhost", not needed with PROD_MAIL_SERVICE)
- PROD_MAIL_NAME: The name of the client server (defaults to machine name)
- PROD_MAIL_USER: Username for the Production email service
- PROD_MAIL_PASS: Password for the Production email service
- PROD_MAIL_FROM: Address which the Production email will be sent from
- PROD_MAIL_SECURE_CONNECTION: Use SSL (default is false, not needed with PROD_MAIL_SERVICE)
- PROD_MAIL_PORT: Port of the SMTP server (defaults to 25, not needed with PROD_MAIL_SERVICE)
- PROD_MAIL_IGNORE_TLS: Ignore server support for STARTTLS (defaults to false)
- PROD_MAIL_DEBUG: Output client and server messages to console

## Getting Started

To run this container with the predefined defaults:

    docker run -p 2368:2368 zzrot/alpine-ghost

Now the Ghost container will be available at your.dockermachine.ip:2368.

See the example compose file for specification of including the ENV variables as well as the volumes.

### Volumes

This image has one volume that can be utilized. By connecting a folder with:

     /var/lib/ghost/

You can not only keep your data persistent, but also upload a custom config.js file. In order to do this connect your volume like this:

     /your/contentfolder:/var/lib/ghost/

## License

The code is available under the [MIT License](https://github.com/ZZROTDesign/alpine-ghost/LICENSE).
