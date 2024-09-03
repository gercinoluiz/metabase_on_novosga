# Tutorial de Instalação do Docker Compose no Ubuntu

Este tutorial irá guiá-lo na instalação do Docker Compose no Ubuntu. Siga os passos abaixo para realizar a instalação com sucesso.

## 1. Atualize o Sistema

Antes de começar, é recomendável atualizar o sistema para garantir que todos os pacotes estejam nas versões mais recentes.

```bash
sudo apt-get update
sudo apt-get upgrade -y
```

## 2. Instale o Docker

Se você ainda não tem o Docker instalado, siga as etapas abaixo para instalá-lo. Se o Docker já estiver instalado, pule para a etapa 3.

### 2.1. Instale Dependências

```bash
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release -y
```

### 2.2. Adicione a Chave GPG Oficial do Docker

```bash
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

### 2.3. Configure o Repositório Docker

```bash
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

### 2.4. Instale o Docker Engine

```bash
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
```

### 2.5. Verifique a Instalação do Docker

```bash
sudo docker --version
```

## 3. Instale o Docker Compose

### 3.1. Baixe a Última Versão do Docker Compose

Substitua `v2.20.2` pela última versão disponível do Docker Compose. Você pode verificar a última versão [aqui](https://github.com/docker/compose/releases).

```bash
sudo curl -L "https://github.com/docker/compose/releases/download/v2.20.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

### 3.2. Aplique Permissões Executáveis

```bash
sudo chmod +x /usr/local/bin/docker-compose
```

### 3.3. Verifique a Instalação

```bash
docker-compose --version
```

Se tudo estiver correto, você verá a versão instalada do Docker Compose.

## 4. Configuração Adicional

Para garantir que o Docker Compose está instalado corretamente, crie um arquivo de teste:

### 4.1. Crie um arquivo `docker-compose.yml`

```yaml
version: '3'
services:
  hello-world:
    image: hello-world
```

### 4.2. Execute o Docker Compose

```bash
docker-compose up
```

Se tudo estiver correto, você verá a mensagem "Hello from Docker!" no terminal.

## 5. Referências

Para mais detalhes, consulte a [documentação oficial do Docker](https://docs.docker.com/desktop/install/linux-install/).

## Conclusão

Você instalou com sucesso o Docker Compose no Ubuntu. Agora, você pode usar o Docker Compose para gerenciar e orquestrar seus contêineres Docker.
