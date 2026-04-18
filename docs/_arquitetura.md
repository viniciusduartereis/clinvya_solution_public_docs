
## 🏗️ Arquitetura

<div class="mermaid">
%%{init: {
  "theme": "base",
  "flowchart": {
    "curve": "basis",
    "nodeSpacing": 35,
    "rankSpacing": 45,
    "padding": 20
  }
}}%%
graph TB

    subgraph APP["Aplicação Clínica"]
        A["Usuário / Navegador"] --> B["Frontend Next.js"]
        B --> C["Backend .NET API"]
        C --> D["Keycloak Auth"]
        C --> E["Database PostgreSQL"]

        B --> F["Portal do Paciente"]
        C --> G["Agenda Inteligente"]
        C --> H["Controle Financeiro"]
        C --> I["Prontuário Digital"]
    end

    subgraph AI["Pipeline de IA"]
        J["Gravação de Consulta"] --> K["Azure Blob Storage"]
        K --> L["Azure Service Bus"]
        L --> M["Worker .NET"]
        M --> N["Azure AI Services"]
        N --> O["Transcrição + Resumo"]
        O --> E
    end

    subgraph CICD["CI/CD e Deploy"]
        P["GitHub Actions"] --> Q["Deploy Backend Azure"]
        P --> R["Deploy Frontend Azure"]
        P --> S["Deploy Auth Keycloak Azure"]
    end

    classDef cloud fill:#e1f5fe,stroke:#01579b,color:#0d3557,stroke-width:2px
    classDef frontend fill:#f3e5f5,stroke:#6a1b9a,color:#3b145a,stroke-width:2px
    classDef backend fill:#e8f5e8,stroke:#1b5e20,color:#163d18,stroke-width:2px
    classDef auth fill:#fff3e0,stroke:#e65100,color:#7a3200,stroke-width:2px
    classDef db fill:#fce4ec,stroke:#ad1457,color:#6a1037,stroke-width:2px
    classDef github fill:#f5f1ff,stroke:#5b3cc4,color:#2f1f73,stroke-width:2px

    class K,L,N cloud
    class B frontend
    class C,M,F,G,H,I backend
    class D auth
    class E db
    class P,Q,R,S github
</div>

<script src="https://cdn.jsdelivr.net/npm/mermaid@11/dist/mermaid.min.js"></script>
<script>mermaid.initialize({ startOnLoad: true });</script>

---


## 🏗️ Architecture

<div class="mermaid">
%%{init: {
  "theme": "base",
  "flowchart": {
    "curve": "basis",
    "nodeSpacing": 35,
    "rankSpacing": 45,
    "padding": 20
  }
}}%%
graph TB

    subgraph APP["Clinical Application"]
        A["Client Browser"] --> B["Frontend Next.js"]
        B --> C["Backend .NET API"]
        C --> D["Keycloak Auth"]
        C --> E["PostgreSQL Database"]

        B --> F["Patient Portal"]
        C --> G["Smart Scheduling"]
        C --> H["Financial Control"]
        C --> I["Digital Medical Record"]
    end

    subgraph AI["AI Pipeline"]
        J["Consultation Recording"] --> K["Azure Blob Storage"]
        K --> L["Azure Service Bus"]
        L --> M[".NET Worker"]
        M --> N["Azure AI Services / Foundry"]
        N --> O["Transcription + Summary"]
        O --> E
    end

    subgraph CICD["CI/CD & Deployments"]
        P["GitHub Actions"] --> Q["Deploy Backend to Azure"]
        P --> R["Deploy Frontend to Azure"]
        P --> S["Deploy Auth (Keycloak) to Azure"]
    end

    classDef cloud fill:#e1f5fe,stroke:#01579b,color:#0d3557,stroke-width:2px
    classDef frontend fill:#f3e5f5,stroke:#6a1b9a,color:#3b145a,stroke-width:2px
    classDef backend fill:#e8f5e8,stroke:#1b5e20,color:#163d18,stroke-width:2px
    classDef auth fill:#fff3e0,stroke:#e65100,color:#7a3200,stroke-width:2px
    classDef db fill:#fce4ec,stroke:#ad1457,color:#6a1037,stroke-width:2px
    classDef github fill:#f5f1ff,stroke:#5b3cc4,color:#2f1f73,stroke-width:2px

    class K,L,N cloud
    class B frontend
    class C,M,F,G,H,I backend
    class D auth
    class E db
    class P,Q,R,S github
</div>

<script src="https://cdn.jsdelivr.net/npm/mermaid@11/dist/mermaid.min.js"></script>
<script>mermaid.initialize({ startOnLoad: true });</script>

---

**Architecture Overview:**
- **Frontend**: Next.js hosted on Azure, responsive interface for professionals and patients  
- **Backend**: .NET 10 minimal API hosted on Azure Container Apps, feature-based architecture  
- **Authentication**: Keycloak for user and role management, with refresh token  
- **Database**: PostgreSQL for clinical and transactional data  
- **Cloud Services**: Azure Blob for audio storage, Service Bus for messaging, AI Services / Foundry for transcription  
- **Consumer**: .NET service for asynchronous transcription processing  
- **CI/CD**: GitHub Actions automating builds, tests, and deploys  
