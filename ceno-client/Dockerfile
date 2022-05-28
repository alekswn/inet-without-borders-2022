FROM equalitie/ceno-client:latest

# Install ansible
RUN apt-get update 
RUN apt-get install -y ansible

# Copy your ansible configuration into the image
COPY ./ansible /ansible

# Run ansible to configure things
RUN ansible-playbook /ansible/localplay.yml
