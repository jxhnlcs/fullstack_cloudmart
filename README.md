# CloudMart

## 📌 Descrição do Desafio
O desafio consiste em configurar e implantar a aplicação **CloudMart** localmente no **Windows**, utilizando **Docker** para conteinerização e **Terraform** para provisionamento da infraestrutura na AWS. O backend interage com o **DynamoDB** da AWS e futuramente utilizará APIs de IA da **OpenAI** e **AWS Bedrock**.

---

## 🛠️ Tecnologias Utilizadas
- **Docker** - Para conteinerização e execução dos serviços.
- **AWS CLI** - Para interagir com os serviços AWS.
- **Terraform** - Para provisionamento da infraestrutura (DynamoDB na AWS).
- **Node.js** - Utilizado no backend e frontend.
- **React, Axios e Tailwind CSS** - Stack do frontend.
- **Express e AWS Lambda** - Tecnologias utilizadas no backend.

---

## ⚙️ Pré-requisitos
Antes de iniciar, instale e configure as seguintes ferramentas:

- [Docker](https://www.docker.com/)
- [AWS CLI](https://aws.amazon.com/cli/)
- [Terraform](https://developer.hashicorp.com/terraform/downloads)
- [Node.js](https://nodejs.org/)

Além disso, configure a AWS CLI com suas credenciais:
```bash
aws configure
```

---

## 🚀 Etapas do Desafio

### 🔹 1. Provisionar Infraestrutura com Terraform
A infraestrutura do **DynamoDB** será provisionada utilizando **Terraform**. Siga os passos abaixo:

1. Acesse a pasta **infra**:
   ```bash
   cd infra
   ```
2. Inicialize o Terraform:
   ```bash
   terraform init
   ```
3. Revise o plano de execução:
   ```bash
   terraform plan
   ```
4. Aplique a configuração:
   ```bash
   terraform apply
   ```
   - Digite `yes` quando solicitado para confirmar a criação das tabelas.

---

### 🔹 2. Construir e Executar a Imagem Docker do Backend
1. Acesse a pasta do backend:
   ```bash
   cd ../backend
   ```
2. Crie o arquivo **`.env`** e preencha com suas variáveis de ambiente parecido como está no .env.example :
   
   **Conteúdo do `.env`**:
   ```
   PORT=5000
   AWS_REGION=us-east-1
   AWS_ACCESS_KEY_ID=
   AWS_SECRET_ACCESS_KEY=
   BEDROCK_AGENT_ID=
   BEDROCK_AGENT_ALIAS_ID=
   OPENAI_API_KEY=
   OPENAI_ASSISTANT_ID=
   ```
4. Construa a imagem Docker do backend:
   ```bash
   docker build -t cloudmart-backend .
   ```
5. Execute o container:
   ```bash
   docker run -d -p 5000:5000 --env-file .env cloudmart-backend
   ```

---

### 🔹 3. Construir e Executar a Imagem Docker do Frontend
1. Acesse a pasta do frontend:
   ```bash
   cd ../frontend
   ```
2. Crie o arquivo **`.env`** e preencha com suas variáveis de ambiente parecido como está no .env.example:
   
   **Conteúdo do `.env`**:
   ```
   VITE_API_BASE_URL=http://<seu-ip>/api
   ```
4. Construa a imagem Docker do frontend:
   ```bash
   docker build -t cloudmart-frontend .
   ```
5. Execute o container:
   ```bash
   docker run -d -p 5001:5001 cloudmart-frontend
   ```

---

## 🌐 Acesso à Aplicação
Após rodar os containers, a aplicação poderá ser acessada pelos seguintes endpoints:

- **Backend**: [http://localhost:5000](http://localhost:5000)
- **Frontend**: [http://localhost:5001](http://localhost:5001)

Caso tenha algum problema na execução ou precise de ajustes, verifique os logs dos containers:
```bash
docker logs -f <container_id>
```

🚀 **Boa sorte no desafio!**

