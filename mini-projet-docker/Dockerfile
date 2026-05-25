# Image Java 17 legere
FROM amazoncorretto:17-alpine

# Repertoire de travail
WORKDIR /app

# Copier le fichier jar
COPY target/paymybuddy.jar app.jar

# Exposer le port Spring Boot
EXPOSE 8080

# Lancer l'application
CMD ["java", "-jar", "app.jar"]
