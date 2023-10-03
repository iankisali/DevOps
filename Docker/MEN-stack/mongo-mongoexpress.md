## Creating docker network
docker network create mongo-network

##starting mongodb
docker run -d \
-p 27017:27017 \
-e ME_CONFIG_MONGODB_ADMINUSERNAME=admin \
-e E_CONFIG_MONGODB_ADMINPASSWORD=password \
--net mongo-network \
--name mongodb \
mongo

##starting mongo-express
docker run -d \
-p 8081:8081 \
-e ME_CONFIG_MONGODB_ADMINUSERNAME=admin \
-e ME_CONFIG_MONGODB_ADMINPASSWORD=password \
-e ME_CONFIG_MONGODB_SERVER=mongodb \
--net mongo-network \
--name mongo-express \
mongo-express
