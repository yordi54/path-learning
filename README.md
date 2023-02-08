# path-learning

# Docker
  1. Crear archivo `docker-compose.yaml` en la ruta raíz del proyecto. 
  2. Configurar el docker con postgresql ver [docker-documentación](https://hub.docker.com/_/postgres).
  3. Ejecutar el comando para crear el contenedor `docker-compose up -d`

# Nest
   **Crear un proyecto nuevo**
   * tener instalado nest de forma global, comando `$npm i -g @nestjs/cli`
   * crear proyecto nuevo con el comando `$nest new project-name`
   * crear componentes o modulos completos `$nest g resource <nombre>`
   
   **TypeORM**
   * instalar packages `$yarn add @nestjs/typeorm typeorm pg` ver [documentación](https://docs.nestjs.com/techniques/database#typeorm-integration)
   * usar el modulo de TypeORM en el modulo principal ej:
   ```
      imports: [
        TypeOrmModule.forRoot({
          type: mysql,
          host: localhost,
          port: 3306,
          username: root,
          password: root,
          database: test,
          entities: [],
          synchronize: true,
        })
    })```
    
    * asdsasd
    
    
    

   
   
 
   
 
