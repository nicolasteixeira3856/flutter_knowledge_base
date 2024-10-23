
# Arquiteturas de Software - Flutter

Este repositório apresenta quatro diferentes arquiteturas de software implementadas em um módulo de autenticação no Flutter (login, registro e esqueci minha senha). Utilizamos os packages `get_it`, `flutter_bloc` (com cubits), e `go_router`, além de abstrações de outros packages, como `http` e biometria.

Cada arquitetura possui uma estrutura de pastas específica que segue os princípios estabelecidos por cada abordagem.

---

## 1. Pacote por Componente

```plaintext
lib/
├── authentication/
│   ├── data/
│   │   ├── repositories/
│   │   │   ├── iauthentication_repository.dart
│   │   │   ├── authentication_repository_impl.dart
│   │   │   └── local_auth_service_impl.dart
│   │   ├── datasources/
│   │   │   ├── ilocal_auth_service.dart
│   │   │   ├── iauth_api_service.dart
│   │   │   └── auth_api_service_impl.dart
│   │   └── models/
│   │       ├── user_model.dart
│   │       └── auth_response_model.dart
│   ├── domain/
│   │   ├── entities/
│   │   │   ├── user_entity.dart
│   │   │   └── auth_response_entity.dart
│   │   ├── usecases/
│   │   │   ├── login_usecase.dart
│   │   │   ├── register_usecase.dart
│   │   │   └── forgot_password_usecase.dart
│   ├── presentation/
│   │   ├── cubit/
│   │   │   ├── login_cubit.dart
│   │   │   ├── register_cubit.dart
│   │   │   └── forgot_password_cubit.dart
│   │   └── pages/
│   │       ├── login_page.dart
│   │       ├── register_page.dart
│   │       └── forgot_password_page.dart
├── core/
│   ├── services/
│   │   ├── navigation_service.dart
│   │   └── http_service.dart
│   └── utils/
│       ├── validators.dart
│       └── constants.dart
(Compartilhamento de entitidades e repositories entre features diferentes)
├── shared/
│   ├── entities/
│   │   ├── user_entity.dart
│   └── repositories/
│       ├── user_repository.dart
│ 
```

---

## 2. Pacote por Serviço

```plaintext
lib/
├── authentication/
│   ├── services/
│   │   ├── iauthentication_service.dart
│   │   ├── authentication_service_impl.dart
│   │   ├── ilocal_auth_service.dart
│   │   └── local_auth_service_impl.dart
│   ├── repositories/
│   │   ├── iauthentication_repository.dart
│   │   └── authentication_repository_impl.dart
│   ├── usecases/
│   │   ├── login_usecase.dart
│   │   ├── register_usecase.dart
│   │   └── forgot_password_usecase.dart
│   ├── cubit/
│   │   ├── login_cubit.dart
│   │   │   register_cubit.dart
│   │   └── forgot_password_cubit.dart
│   ├── models/
│   │   ├── user_model.dart
│   │   └── auth_response_model.dart
│   └── pages/
│       ├── login_page.dart
│       ├── register_page.dart
│       └── forgot_password_page.dart
├── core/
│   ├── services/
│   │   ├── navigation_service.dart
│   │   └── http_service.dart
│   └── utils/
│       ├── validators.dart
│       └── constants.dart
(Compartilhamento de entitidades e repositories entre features diferentes)
├── shared/
│   ├── entities/
│   │   ├── user_entity.dart
│   └── repositories/
│       ├── user_repository.dart
│ 
```

---

## 3. Ports and Adapters (Arquitetura Hexagonal)

```plaintext
lib/
├── authentication/
│   ├── adapters/
│   │   ├── http_auth_adapter_impl.dart
│   │   ├── ilocal_auth_adapter.dart
│   │   └── local_auth_adapter_impl.dart
│   ├── ports/
│   │   ├── iauth_repository.dart
│   │   ├── iauth_service.dart
│   │   └── ilocal_auth_service.dart
│   ├── repositories/
│   │   ├── auth_repository_impl.dart
│   └── services/
│       ├── auth_service_impl.dart
│       └── local_auth_service_impl.dart
│   ├── usecases/
│   │   ├── login_usecase.dart
│   │   ├── register_usecase.dart
│   │   └── forgot_password_usecase.dart
│   ├── cubit/
│   │   ├── login_cubit.dart
│   │   ├── register_cubit.dart
│   │   └── forgot_password_cubit.dart
│   └── pages/
│       ├── login_page.dart
│       ├── register_page.dart
│       └── forgot_password_page.dart
├── core/
│   ├── services/
│   │   ├── navigation_service.dart
│   │   └── http_service.dart
│   └── utils/
│       ├── validators.dart
│       └── constants.dart
(Compartilhamento de entitidades e repositories entre features diferentes)
├── shared/
│   ├── entities/
│   │   ├── user_entity.dart
│   └── adapters/
│       ├── user_repository_impl.dart
│   └── ports/
│       ├── user_repository.dart
│ 
```

---

## 4. Pacote por Recurso

```plaintext
lib/
├── authentication/
│   ├── domain/
│   │   ├── entities/
│   │   │   ├── user_entity.dart
│   │   │   └── auth_response_entity.dart
│   │   ├── repositories/
│   │   │   ├── iauthentication_repository.dart
│   │   │   └── authentication_repository_impl.dart
│   │   └── usecases/
│   │       ├── login_usecase.dart
│   │       ├── register_usecase.dart
│   │       └── forgot_password_usecase.dart
│   ├── infrastructure/
│   │   ├── datasources/
│   │   │   ├── iauthentication_service.dart
│   │   │   ├── ilocal_auth_service.dart
│   │   │   └── authentication_service_impl.dart
│   │   └── models/
│   │       ├── user_model.dart
│   │       └── auth_response_model.dart
│   ├── presentation/
│   │   ├── cubit/
│   │   │   ├── login_cubit.dart
│   │   │   ├── register_cubit.dart
│   │   │   └── forgot_password_cubit.dart
│   │   └── pages/
│   │       ├── login_page.dart
│   │       ├── register_page.dart
│   │       └── forgot_password_page.dart
├── core/
│   ├── services/
│   │   ├── navigation_service.dart
│   │   └── http_service.dart
│   └── utils/
│       ├── validators.dart
│       └── constants.dart
(Compartilhamento de entitidades e repositories entre features diferentes)
├── shared/
│   ├── domain/
│   │   ├── entities/
│   │   │   ├── user_entity.dart
│   │   └── repositories/
│   │       ├── user_repository.dart
│   └── infrastructure/
│       └── user_repository_impl.dart
```

---

## Conclusão

Cada uma dessas arquiteturas possui suas vantagens e desvantagens. Aqui está uma breve comparação:

- **Pacote por Componente**: Modulariza os componentes e mantém as camadas separadas dentro de um mesmo domínio.
- **Pacote por Serviço**: Centraliza a lógica ao redor dos serviços, mas ainda mantém uma divisão por camadas.
- **Ports and Adapters**: Promove um desacoplamento completo entre a lógica de negócios e a infraestrutura, utilizando interfaces e adaptadores.
- **Pacote por Recurso**: Foco no agrupamento de tudo relacionado a um recurso em um único pacote, proporcionando alta coesão.
