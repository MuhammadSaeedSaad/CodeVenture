# Nestjs

# General
1. main advantage of Nest is the Architecture.
2. Nest's archtecture heavily based on Angular.

# Quick Notes
1. Validation can be done before the route handler using DTO and also Before object creation using the Entity (validation code can be put in the Entity);
2. In TypeORM the functions `insert() update() delete()` doesn't execute hooks.
3. The type helper `Partial<>` usually used in attributes when updating an entity or a model is specific to TypeScript itself.
4. A service inside Nestjs can be user by other controllers than `HTTP` i.e. `WEBSOCKET GRPC` though we should not return HTTP errors from inside the service itself.
5. Don't apply serialization to the entire entity as it is more controller related thing. i.e. don't put `@Exclude` decorator in the entity itself and use controller/route handler specific interceptors instead.
6. Interceptors can be used on whole conroller or on specific route handler.