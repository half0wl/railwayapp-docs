---
title: Add a Pre-Deploy Command
---

Pre-deploy commands execute between building and deploying your application, handling tasks like database migrations or data seeding before your application runs.
They execute within your private network and have access to your application's environment variables.

If your command fails, the deployment will not proceed.

<Image
src="https://res.cloudinary.com/railway/image/upload/v1736533539/docs/pre-deploy-command_sp1zqh.png"
alt="Screenshot of pre-deploy command configuration"
layout="intrinsic"
width={1494} height={644} quality={80} />

Make sure your command:

- Exits with a status code of `0` to indicate success or non-zero to indicate failure.
- Runs in a reasonable amount of time. It will occupy a slot in your build queue.
- Does not rely on the application running.
- Has the dependencies it needs to run installed in the application image.

<Banner variant="warning">Pre-deploy commands execute in a separate container from your application. Changes to the filesystem are not persisted.</Banner>
