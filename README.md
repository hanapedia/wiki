# Hanapedia's personal wiki
This project is my personal wiki page. 
The wiki will contain my blogs, documents, and notes.
The page is built using [Hugo](https://gohugo.io) with [Docsy][].

## About this project
You can find detailed theme instructions in the [Docsy user guide][].

## Running a container locally

You can run docsy-example inside a [Docker](https://docs.docker.com/)
container, the container runs with a volume bound to the `docsy-example`
folder. This approach doesn't require you to install any dependencies other
than [Docker Desktop](https://www.docker.com/products/docker-desktop) on
Windows and Mac, and [Docker Compose](https://docs.docker.com/compose/install/)
on Linux.

1. Build & Run the docker image

   ```bash
   docker compose up --build
   ```

1. Verify that the service is working.

   Open your web browser and type `http://localhost:1313` in your navigation bar,
   This opens a local instance of the wiki page. You can now make
   changes to the docsy example and those changes will immediately show up in your
   browser after you save.

### Cleanup

To stop Docker Compose, on your terminal window, press **Ctrl + C**.

To remove the produced images run:

```bash
docker-compose rm
```
For more information see the [Docker Compose documentation][].

## Deployment
The wiki is hosted at Github Pages, and the deployment is automated using Github Actions. 
To deploy the new version of the wiki, push the new commit to the main branch of this repo.
The page will be available at https://hanapedia.github.io/wiki


[Docsy user guide]: https://docsy.dev/docs
[Docsy]: https://github.com/google/docsy
[example.docsy.dev]: https://example.docsy.dev
[Hugo theme module]: https://gohugo.io/hugo-modules/use-modules/#use-a-module-for-a-theme
