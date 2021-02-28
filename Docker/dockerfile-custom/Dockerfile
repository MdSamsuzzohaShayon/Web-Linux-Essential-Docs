# STEP-1 SPECIFY THE BASE IMAGE 
# The FROM instruction initializes a new build stage and sets the Base Image for subsequent instructions. As such, a valid Dockerfile must start with a FROM instruction. The image can be any valid image – it is especially easy to start by pulling an image from the Public Repositories.
# https://docs.docker.com/engine/reference/builder/#from
FROM alpine

# STEP-2 DOWNLOAD AND INSTALL DEPENDENCIES 
# he RUN instruction will execute any commands in a new layer on top of the current image and commit the results. The resulting committed image will be used for the next step in the Dockerfile.
# https://docs.docker.com/engine/reference/builder/#run
RUN apk add --update redis


# STEP-3 SETUP AND STARTUP COMMAND 
# There can only be one CMD instruction in a Dockerfile. If you list more than one CMD then only the last CMD will take effect.
# https://docs.docker.com/engine/reference/builder/#cmd
CMD ["redis-server"]