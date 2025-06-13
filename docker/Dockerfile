FROM eclipse-temurin:17-jdk-jammy

ENV APP_HOME=/ecommerce-app
RUN mkdir -p $APP_HOME
WORKDIR $APP_HOME

# Expone el puerto INTERNO de la aplicación, que es 8080
EXPOSE 8080

COPY target/ecommerce-*.jar app.jar

RUN useradd -m appuser && chown -R appuser:appuser $APP_HOME
USER appuser

HEALTHCHECK --interval=30s --timeout=3s \
  CMD curl -f http://localhost:8080/actuator/health || exit 1

ENTRYPOINT ["java", "-jar", "app.jar"]