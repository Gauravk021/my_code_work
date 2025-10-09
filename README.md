# my_code_work
spring:
  data:
    mongodb:
      uri: mongodb://localhost:27017/test
  autoconfigure:
    exclude: org.springframework.boot.autoconfigure.mongo.MongoAutoConfiguration

server:
  ssl:
    enabled: false

policy:
  service:
    enabled: false

