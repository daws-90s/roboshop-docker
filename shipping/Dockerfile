FROM maven:3.9.16
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn clean package 
RUN mv target/shipping-1.0.jar shipping.jar 
EXPOSE 8080
CMD ["java", "shipping.jar"]