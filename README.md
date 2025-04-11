# 📊 AWS Tag Inventory

Este projeto em Python realiza o inventário de recursos da AWS utilizando a API `resourcegroupstaggingapi`, que permite listar recursos com base em suas **tags associadas**.

É uma abordagem **eficiente, gratuita e rápida**, ideal para aplicações de **FinOps, Governança e Auditoria** em ambientes AWS.

---

## ✅ Funcionalidades

- 🔎 Coleta automática de todos os recursos com tags
- 📁 Exportação em planilha Excel (.xlsx)
- 📊 Gráficos automáticos (Pizza e Barras) gerados com base:
  - Nos 10 principais tipos de recurso
  - Na distribuição por região
  - Nas tags mais utilizadas
- 📑 Organização por abas no Excel:
  - Inventário Completo
  - Top Tipos
  - Recursos por Região
  - Top Tags
- 🔐 Execução segura via perfil IAM programático

---

## 🛠️ Tecnologias Utilizadas

- [Python 3.x](https://www.python.org)
- [boto3](https://boto3.amazonaws.com/v1/documentation/api/latest/index.html) – SDK oficial da AWS
- [pandas](https://pandas.pydata.org/)
- [openpyxl](https://openpyxl.readthedocs.io/)

---

## ▶️ Como Executar

### 1. 🛡️ Criar usuário IAM com acesso programático

Crie um usuário com permissões para utilizar a API de inventário:

#### Política mínima recomendada:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": ["tag:GetResources"],
      "Resource": "*"
    }
  ]
}
```

### 2. Clone o repositório

```bash

git clone https://github.com/arijunior2020/aws-tag-inventory.git
cd aws-tag-inventory

```

### 3. 📦 Instalar dependências

```bash
pip install -r requirements.txt
```

### 4. ⚙️ Configurar credenciais

Crie um arquivo `~/.aws/credentials` com o seguinte conteúdo:

```ini
[default ou "nome do perfil que deseja usar"]
aws_access_key_id = SEU_ACCESS_KEY
aws_secret_access_key = SEU_SECRET_KEY
region = REGIAO_QUE_DESEJA_USAR
output = json
```

Se preferir em vez de criar ou editar esse arquivo pode executar o seguinte comando:

```bash
aws configure --profile nome_do_perfil
```

**OBS**: Esse nome do perfil vai ser utilizado no script `main.py`

### 5. 🖥️ Executar o script

```bash
python aws_tag_inventory.py
```

Ele irá solicitar o local onde deseja salvar o arquivo Excel.

### 6. 📊 Visualizar resultados

Após a execução, um arquivo Excel será gerado com as seguintes abas:

- **Inventário Completo**: Lista todos os recursos com tags.
- **Top Tipos**: Mostra os 10 principais tipos de recursos.
- **Recursos por Região**: Distribuição dos recursos por região.
- **Top Tags**: Exibe as tags mais utilizadas.
- **Gráficos**: Gráficos de pizza e barras com as informações mais relevantes.

### 7. ⚠️ Limitações da API resourcegroupstaggingapi

- A API retorna apenas recursos com tags.
- Pode listar recursos já deletados recentemente, como task definitions ou security groups órfãos.
- Para inventários mais precisos e com histórico de estados, considere utilizar o AWS Config (serviço pago).

Porém, para uma visão inicial prática e gratuita, este projeto entrega ótimos resultados e pode ser o primeiro passo de uma estratégia FinOps.

### Contato

- Desenvolvido por Arimatéia Júnior

Dúvidas, sugestões ou contribuições são bem-vindas!
[LinkedIn](https://www.linkedin.com/in/arimateiajunior/)
