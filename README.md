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
      ```
        DB_USER = example
        DB_PASSWORD = example
        DB_HOST = localhost
        DB_NAME = example
        DB_PORT = 5432
      ```
   * importar módulo para poder configurar las variables de manera global `$yarn add @nestjs/config`
      ```
        imports: [
           ConfigModule.forRoot(),
           ],
      ```
      
   * crear una archivo entidad para el usuario con sus atributos 
      ```
        import { Entity, Column, PrimaryGeneratedColumn } from 'typeorm';

        @Entity('usuarios')
        export class Auth {
            @PrimaryGeneratedColumn('uuid')
            id: string;

            @Column('text', { unique: true })
            email: string;

            @Column('text')
            password: string;
        }
      ```
   * instalar libreria externa para validaciones `$yarn add class-validator class-transformer` ver [documentación](https://docs.nestjs.com/techniques/validation)
   * configuración para Global para Pipe de Validaciones en el archivo `main.ts`
      ```
        import { ValidationPipe } from '@nestjs/common';
        import { NestFactory } from '@nestjs/core';
        import { AppModule } from './app.module';

        async function bootstrap() {
          const app = await NestFactory.create(AppModule);
          app.useGlobalPipes(new ValidationPipe(
            {
              whitelist: true,
              forbidNonWhitelisted: true,
            }
          ));
          await app.listen(3000);
        }
        bootstrap();
        
        // whiteList: Remueve todo lo que no está incluído en los DTOs
        // forbidNonWhiteListed: Retorna bad request si hay propiedades en el objeto no requeridas
      ```
     * Authentication
      instalar paquetes `$yarn add @nestjs/passport passport`
      `$yarn add @nestjs/jwt passport-jwt`
      `$yarn add -D @types/passport-jwt`
      
      definir la strategy a jwt
        ```
          import { Module } from '@nestjs/common';
          import { AuthService } from './auth.service';
          import { AuthController } from './auth.controller';
          import { TypeOrmModule } from '@nestjs/typeorm';
          import { Auth } from './entities/auth.entity';
          import { PassportModule } from '@nestjs/passport';
          @Module({
            imports: [
              TypeOrmModule.forFeature([Auth]),
              PassportModule.register({ defaultStrategy: 'jwt' })
            ],
            controllers: [AuthController],
            providers: [AuthService]
          })
          export class AuthModule {}
        ```
      

    
    

   
   
 
   
 
