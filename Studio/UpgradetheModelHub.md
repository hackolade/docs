---
description: Upgrade Hackolade Model Hub to a new version with Docker Compose, after a backup of its database.
seoTitle: Upgrade Hackolade Model Hub
---
# Upgrade the Model Hub

Each new version of the Model Hub is published as a tag of the [hackolade/model-hub](<https://hub.docker.com/r/hackolade/model-hub/tags> "target=\"_blank\"") image. The Model Hub updates its database structure itself when the new version starts.

Before you upgrade a production Model Hub, take a full backup or snapshot of its database, as described in [Data backup](Databackup.md), and keep the encryption key with it. The new version may change the database structure when it starts.

Then, on the server, in the folder of your `docker-compose.yml`:

1. Pick the new version among the tags of the [hackolade/model-hub](<https://hub.docker.com/r/hackolade/model-hub/tags> "target=\"_blank\"") image.

2. Set `MODEL_HUB_VERSION` to that version in your `.env` file.

3. Pull the new image and restart the Model Hub:

   ```bash
   docker compose pull
   docker compose up -d
   ```

4. Follow the logs until they show `Server ready`, then check that your users can open `https://<your-hostname>`:

   ```bash
   docker compose logs -f model-hub
   ```

To go back to the previous version, restore that backup, set the previous `MODEL_HUB_VERSION` in `.env`, and run `docker compose up -d`.

If the Model Hub does not start, its logs show `Failed to start server` with the cause. [Model Hub installation troubleshooting](ModelHubinstallationtroubleshooting.md) lists the usual causes.
