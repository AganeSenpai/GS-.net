
# 🌊 API de Alerta de Enchentes

Este projeto é uma API RESTful desenvolvida com ASP.NET Core para gerenciar alertas de enchentes, previsões climáticas e cidades. Ele também integra funcionalidades de mensageria com RabbitMQ e análise preditiva com Machine Learning.

## 📌 Funcionalidades

- CRUD de cidades
- CRUD de alertas de enchente
- CRUD de previsões climáticas
- Publicação de mensagens com RabbitMQ
- Análise de risco com modelo de Machine Learning
- Rate limiting de IPs com AspNetCoreRateLimit
- API documentada com Swagger

---

## 🧱 Estrutura do Projeto

```
Enchente/
├── Core/
│   ├── Entities/
│   ├── Interfaces/
├── Infrastructure/
│   ├── Data/
│   ├── Repositories/
│   ├── Messaging/
│   └── ML/
├── Controllers/
├── Program.cs
└── appsettings.json
```

---

## 🧪 Tecnologias Utilizadas

- ASP.NET Core 6
- Oracle Database
- RabbitMQ
- Machine Learning (via `MLService`)
- Swagger
- AspNetCoreRateLimit

---

## ⚙️ Configuração do Ambiente

### 1. Pré-requisitos

- [.NET 6 SDK](https://dotnet.microsoft.com/download)
- [Oracle Database](https://www.oracle.com/database/)
- [RabbitMQ](https://www.rabbitmq.com/download.html)

### 2. Clonar o repositório

```bash
git clone https://github.com/seu-usuario/enchente-api.git
cd enchente-api
```

### 3. Configurar `appsettings.json`

```json
{
  "ConnectionStrings": {
    "OracleConnection": "User Id=usuario;Password=senha;Data Source=localhost:1521/XEPDB1;"
  },
  "IpRateLimiting": {
    "EnableEndpointRateLimiting": true,
    "GeneralRules": [
      {
        "Endpoint": "*",
        "Period": "1m",
        "Limit": 60
      }
    ]
  }
}
```

---

## 🚀 Executando o Projeto

```bash
dotnet build
dotnet run
```

- Acesse a API: `https://localhost:5001/api/`
- Documentação Swagger: `https://localhost:5001/swagger`

---

## 📬 Integração com RabbitMQ

Mensagens são publicadas quando novos dados relevantes (ex: alertas) são criados.

**Exemplo de publicação:**
```csharp
_messagingService.SendMessage("alertas", "Alerta enviado para cidade X");
```

---

## 🧠 Integração com Machine Learning

Ao criar uma nova previsão do tempo (`POST /api/previsaoclima`), a API usa um modelo de ML para prever risco de enchente:

```csharp
var prediction = _mlService.Predict(previsao);
```

A resposta inclui o resultado da predição.

---

## 📤 Endpoints Principais

| Método | Endpoint                         | Descrição                     |
|--------|----------------------------------|-------------------------------|
| GET    | `/api/cidade`                    | Lista todas as cidades        |
| POST   | `/api/alertaenchente`            | Cria um novo alerta           |
| POST   | `/api/previsaoclima`             | Cria uma previsão e prediz    |
| GET    | `/api/previsaoclima/{id}`        | Retorna previsão por ID       |

---

## ✅ Roadmap Futuro

- 🔄 Consumo de APIs externas de clima (ex: OpenWeather)
- 🧠 Aprimoramento do modelo de ML com dados reais
- 📊 Painel administrativo com gráficos

---

## 👨‍💻 Integrantes

Carlos Eduardo Ariza Sartorio RM553461

Fernando Shinji Tanigushi RM553587

João Vitor Valaitis Paulo RM553972


