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
   * importar y usar el modulo de TypeORM en el modulo principal ej:
      ```
        imports: [
          ConfigModule.forRoot(),
          TypeOrmModule.forRoot({
            type: 'postgres',
            host: process.env.DB_HOST,
            port: parseInt(process.env.DB_PORT),
            username: process.env.DB_USER,
            password: process.env.DB_PASSWORD,
            database: process.env.DB_NAME,
            synchronize: true,
            autoLoadEntities: true,
          }),
          AuthModule
        ],
      ```



   * crear archivo `.env` para variables de entorno global.
   * importar módulo para poder configurar las variables de manera global `$yarn add @nestjs/config`
      ```
        imports: [
           ConfigModule.forRoot(),
           ],
      ```
    
    
    

   
   
 
   
 
