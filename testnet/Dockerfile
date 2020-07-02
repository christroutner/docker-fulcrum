# Start with a pre-configured Ubuntu 18.04 image.
FROM christroutner/ct-base-ubuntu
MAINTAINER Chris Troutner <chris.troutner@gmail.com>

RUN apt-get update -y

#Set the working directory to be the home directory
WORKDIR /home/safeuser

# Copy the Fulcrum binary and config file.
COPY bin/Fulcrum Fulcrum
COPY testnet.conf testnet.conf

# Copy SSL certificates
#COPY certs/fullchain.pem fullchain.pem
#COPY certs/privkey.pem privkey.pem
COPY certs/server.crt server.crt
COPY certs/server.key server.key

# Ensure all files are owned by the safeuser user.
RUN chown -R safeuser *

# Switch to user account.
USER safeuser
# Prep 'sudo' commands.
#RUN echo 'abcd8765' | sudo -S pwd

# Used to hold the Fulcrum database.
RUN mkdir blockchain

# Start Fulcrum server.
CMD ["./Fulcrum", "testnet.conf"]

# Used for debugging.
#COPY bin/dummyapp.js dummyapp.js
#CMD ["node", "dummyapp.js"]
