# git-container
# docker-compose file

version: '3.6'
services:
  web:
    image: 'gitlab/gitlab-ce:${version}'  # first should set version environmet on OS #
    container_name: 'gitlab-ce-${version}'
    restart: always
    hostname: 'gitlab'
    environment:
      GITLAB_OMNIBUS_CONFIG: |   # Add any other gitlab.rb configuration here, each on its own line
        external_url 'https://gd.fanapsoft.ir'
        
    ports:
      - '443:443'
      - '80:80' 
    volumes:
      - '$GITLAB_HOME/config:/etc/gitlab'  # Should set GITLAB_HOME environment on OS #
      - '$GITLAB_HOME/logs:/var/log/gitlab'
      - '$GITLAB_HOME/data:/var/opt/gitlab'
    shm_size: '256m'
