# Assumptions
You have downloaded NONMEM751.zip on your local machine
You have a nonmem.lic license file
You have installed Docker or Podman on your computer

# Step 1: Prepare your folder structure
Create a folder (e.g., nonmem-docker) and put these inside:

        NONMEM751.zip (downloaded ZIP)
                
        nonmem.lic (license file)

        A Dockerfile 

# Step 2: Build the Docker or Podman Image

    cd /local/path/folder
    docker build -t nonmem751-image .
    # podman build -t nonmem751-image . 

This reads your Dockerfile, copies files, installs software, and runs setup.

The image is named nonmem751-image.

# Step 3: Run a container from your image

    docker run --rm -it nonmem751-image
    # podman run --rm -it nonmem751-image

You get a bash shell inside your NONMEM environment.

You can execute NONMEM commands directly inside this shell.

# Step 4: Managing your NONMEM data and license
To keep your NONMEM data and license persistent or to access local files, use volumes:

    docker run --rm -it -v /local/path/license:/opt/nonmem/licence -v /local/path/data:/opt/nonmem/data nonmem751-image
    # podman run --rm -it -v /local/path/license:/opt/nonmem/licence -v /local/path/data:/opt/nonmem/data nonmem751-image

Replace /local/path/license and /local/path/data with your local folders.
