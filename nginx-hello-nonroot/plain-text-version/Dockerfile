FROM nginx:1.16.1-alpine

# We need to give all user groups write permission on folder /var/cache/nginx/ and file /var/run/nginx.pid.
# So users with random uid will be able to run NGINX.
RUN chmod -R a+w /var/cache/nginx/ \
        && touch /var/run/nginx.pid \
        && chmod a+w /var/run/nginx.pid \
        && rm /etc/nginx/conf.d/*

COPY hello.conf /etc/nginx/conf.d/
EXPOSE 8080
# NOTE: steve: non numberic users can cause trouble in Kubernetes
# CreateContainerConfigError: Error: container has runAsNonRoot and 
#   image has non-numeric user (username), cannot verify user is non-root.
# USER nginx
USER 1234
