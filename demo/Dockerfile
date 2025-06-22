# Étape 1 : Image contenant Maven + Java
FROM maven:3.9.6-eclipse-temurin-17 AS build

# Étape 2 : Copier le projet dans le conteneur
COPY . /app

# Étape 3 : Définir le répertoire de travail
WORKDIR /app

# Étape 4 : Compiler le projet (générer le .jar)
RUN mvn clean package -DskipTests

# Étape 5 : Image finale avec uniquement le .jar
FROM openjdk:17-jdk-slim

WORKDIR /app

# Copier le .jar depuis l’étape précédente
COPY --from=build /app/target/*.jar app.jar

# Exposer le port (à adapter si ce n’est pas 8080)
EXPOSE 9999

# Lancer l’application
ENTRYPOINT ["java", "-jar", "app.jar"]
