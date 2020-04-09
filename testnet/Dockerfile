FROM christroutner/ct-base-ubuntu
MAINTAINER Chris Troutner <chris.troutner@gmail.com>

RUN apt-get update -y

#Set the working directory to be the home directory
WORKDIR /home/safeuser

COPY bin/Fulcrum Fulcrum
COPY testnet.conf testnet.conf
COPY certs/fullchain.pem fullchain.pem
COPY certs/privkey.pem privkey.pem

RUN chown -R safeuser *

# Switch to user account.
USER safeuser
# Prep 'sudo' commands.
#RUN echo 'abcd8765' | sudo -S pwd

RUN mkdir blockchain

# Install Redis. TODO: Make this a separate container.

COPY bin/Fulcrum Fulcrum
COPY testnet.conf testnet.conf

CMD ["./Fulcrum", "testnet.conf"]

#COPY bin/dummyapp.js dummyapp.js
#CMD ["node", "dummyapp.js"]
