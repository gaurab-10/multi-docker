FROM node:alpine as builder

WORKDIR '/app'
COPY package*.json .
RUN yarn install
COPY . .
# running this coommand will store the build files in /build directory i.e. workdi/build ==> app/build
RUN yarn build 


FROM nginx 
EXPOSE 3000
#  copy nginx default conf file
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf

# COPY SOMETHING FROM BUILDER // SPECIFY FOLDER WE WANT TO COPY // SPECIFY where we want to copy
COPY --from=builder /app/build /usr/share/nginx/html    