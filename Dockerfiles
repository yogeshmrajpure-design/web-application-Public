FROM nginx:alpine

# Set the working directory
WORKDIR /usr/share/nginx/html

# Clean the default Nginx files
RUN rm -rf ./*

# Copy the contents of your specific project folder
# Note the path: we go into the folder where index.html actually lives
COPY ["css Project/templatemo_605_xmas_countdown/", "."]

# Ensure permissions are correct
RUN chmod -R 755 /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
