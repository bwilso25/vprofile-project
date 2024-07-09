FROM nginx
LABEL "Project"="Vprofile"
LABEL "Author"="Bernard"
#remove their default configuration file and copy the one u made into it
RUN rm -rf /etc/nginx/conf.d/default.conf
COPY nginvproapp.conf /etc/nginx/conf.d/vproapp.conf