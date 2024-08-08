# Exemplos de Implementação do MongoDB

## 1. Configurando o MongoDB em um Servidor Local

### Passo a Passo:

**Instalação**: Para instalar o MongoDB em um servidor local, você pode usar os seguintes comandos (no caso de um sistema Ubuntu):

     
    sudo apt-get update
    sudo apt-get install -y mongodb


**Inicializando o Servidor**: Após a instalação, inicie o serviço do MongoDB:

    sudo systemctl start mongodb

**Verificando o Status**: Certifique-se de que o MongoDB está funcionando corretamente

    sudo systemctl status mongodb

**Conectando ao MongoDB**: Use o cliente de linha de comando MongoDB para se conectar ao servidor:

    mongo

**Resultado**:

- O MongoDB está agora rodando em seu servidor local e pode ser acessado via o terminal ou ferramentas de gerenciamento como o MongoDB Compass.

## 2.0 Criando um Banco de Dados e uma Coleção

### Passo a Passo:

**Criando um Banco de Dados**: No shell MongoDB, você pode criar um novo banco de dados simplesmente selecionando-o:

    use meuBancoDeDados

**Criando uma Coleção**: Depois de selecionar o banco de dados, crie uma nova coleção:

    db.createCollection("minhaColecao")

**Inserindo Documentos**: Adicione documentos à coleção recém-criada:

    db.minhaColecao.insertOne({ nome: "Dênis", idade: 28, profissão: "Desenvolvedor" })
    db.minhaColecao.insertMany([
    { nome: "Luis", idade: 30, profissão: "Engenheiro" },
    { nome: "Ronald", idade: 25, profissão: "Analista" }
    ])

**Resultado**:

- Agora, você tem um banco de dados com uma coleção que contém documentos JSON.

## 3.0 Consultando Dados no MongoDB

### Passo a Passo:

**Buscando Todos os Documentos**: Para recuperar todos os documentos em uma coleção:

    db.minhaColecao.find()

**Buscando Documentos Específicos**: Para buscar documentos que atendem a certos critérios:

    db.minhaColecao.find({ idade: { $gt: 25 } })

**Atualizando Documentos**: Para atualizar documentos existentes:

    db.minhaColecao.updateOne(
    { nome: "Dênis" },
    { $set: { idade: 29 } }
    )

**Deletando Documentos**: Para remover documentos de uma coleção:

    db.minhaColecao.deleteOne({ nome: "Ronald" })

**Resultado**:

 - Essas operações básicas permitem que você gerencie e manipule dados armazenados no MongoDB.

## 4. Configurando Replica Sets

### Passo a Passo:

**Iniciando um Replica Set**: Para iniciar um Replica Set, modifique o arquivo de configuração do MongoDB (mongod.conf) para incluir:

    replication:
    replSetName: "meuReplicaSet"

**Iniciando o MongoDB com Replica Set**: Reinicie o MongoDB com o novo arquivo de configuração:

    sudo systemctl restart mongodb

**Iniciando o Replica Set: No shell do MongoDB**:

    rs.initiate()

**Adicionando Membros**: Adicione membros ao Replica Set:

    rs.add("mongo2.example.net:27017")
    rs.add("mongo3.example.net:27017")

**Resultado**:

- Agora você tem um Replica Set configurado para alta disponibilidade e redundância de dados.


## 5. Exemplo de Implementação Real: Sistema de Gerenciamento de Usuários com MongoDB

## 1. Estrutura do Projeto

**Crie um diretório para o seu projeto e inicialize um novo projeto Node.js**:

    mkdir sistema-usuarios
    cd sistema-usuarios
    npm init -y

**Instale as dependências necessárias, como o driver do MongoDB e o Express.js para criar um servidor web simples**:

    npm install express mongodb

## 2. Configurando a Conexão com o MongoDB

**Crie um arquivo index.js na raiz do projeto e configure a conexão com o MongoDB**:

    const express = require('express');
    const { MongoClient } = require('mongodb');

    const app = express();
    const port = 3000;

    const uri = "mongodb://localhost:27017";
    const client = new MongoClient(uri);

    async function connectDB() {
        try {
            await client.connect();
            console.log("Conectado ao MongoDB!");
            const database = client.db('sistemaUsuarios');
            const usuarios = database.collection('usuarios');

            // Criar um usuário exemplo
            await usuarios.insertOne({ nome: "João", email: "joao@example.com", idade: 30 });

            app.get('/', async (req, res) => {
                const allUsers = await usuarios.find().toArray();
                res.json(allUsers);
            });

            app.listen(port, () => {
                console.log(`Servidor rodando em http://localhost:${port}`);
            });

        } catch (err) {
            console.error(err);
        }
    }

    connectDB();

## 3. Executando a Aplicação

**Para rodar a aplicação, utilize o comando**:

    node index.js

- Abra o navegador e acesse http://localhost:3000. Você verá uma lista de usuários que foi inserida no banco de dados MongoDB.

## 4. Expansão do Sistema

- Agora que a estrutura básica está pronta, você pode expandir o sistema adicionando rotas para criar, atualizar e deletar usuários:

**Criando um Novo Usuário**

Adicione uma rota POST para criar novos usuários:

    app.use(express.json());

    app.post('/usuarios', async (req, res) => {
        const novoUsuario = req.body;
        const resultado = await usuarios.insertOne(novoUsuario);
        res.json({ message: 'Usuário criado com sucesso!', id: resultado.insertedId });
    });

**Atualizando um Usuário**

Adicione uma rota PUT para atualizar os dados de um usuário existente:

    app.put('/usuarios/:id', async (req, res) => {
        const id = req.params.id;
        const novosDados = req.body;

        await usuarios.updateOne({ _id: new ObjectId(id) }, { $set: novosDados });
        res.json({ message: 'Usuário atualizado com sucesso!' });
    });

**Deletando um Usuário**

Adicione uma rota DELETE para remover um usuário:

    app.delete('/usuarios/:id', async (req, res) => {
        const id = req.params.id;

        await usuarios.deleteOne({ _id: new ObjectId(id) });
        res.json({ message: 'Usuário deletado com sucesso!' });
    });
