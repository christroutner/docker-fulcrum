FROM christroutner/ct-base-ubuntu
MAINTAINER Chris Troutner <chris.troutner@gmail.com>

RUN apt-get update -y

#Set the working directory to be the home directory
WORKDIR /home/safeuser

COPY bin/Fulcrum Fulcrum
COPY mainnet.conf mainnet.conf

# Copy certs
#COPY certs/fullchain.pem fullchain.pem
#COPY certs/privkey.pem privkey.pem
COPY certs/server.crt server.crt
COPY certs/server.csr server.csr
COPY certs/server.key server.key

RUN chown -R safeuser *

# Switch to user account.
USER safeuser
# Prep 'sudo' commands.
#RUN echo 'abcd8765' | sudo -S pwd

RUN mkdir blockchain

COPY bin/Fulcrum Fulcrum
COPY mainnet.conf mainnet.conf

#CMD ["./Fulcrum", "mainnet.conf"]

COPY bin/dummyapp.js dummyapp.js
CMD ["node", "dummyapp.js"]
