# DBFWdata_base
Script para registro de cartas de DBFW automatizado


Script de Gerenciamento de Cartas de Dragon Ball Fusion World
Este é um script para Google Apps Script que automatiza o gerenciamento de cartas do jogo Dragon Ball Super Card Game Fusion World em um banco de dados do Notion. Ele é projetado para ajudar a manter o controle do seu estoque de cartas de forma rápida e eficiente.

Funcionalidades Principais
O script executa as seguintes ações de forma automatizada:

Processa Registros Pendentes: Lê um banco de dados auxiliar no Notion (Registro) em busca de novas entradas.

Atualiza o Estoque: Se a carta já existir no banco de dados principal (DB de Cartas), ele adiciona o número de cópias informado.

Cria Novas Entradas: Se a carta não for encontrada, ele cria uma nova página na sua planilha de estoque.

Fallback Robusto: O script tenta buscar detalhes da carta (nome, cor, custo, etc.) de um site de banco de dados oficial via web scraping. Se a busca falhar, ele ainda cria a carta com o ID e a quantidade, garantindo que o processo não seja interrompido.

Organização: Após o processamento, ele marca o registro como "Processado" para evitar duplicações.

Como Configurar
Para usar este script, você precisará de um token de integração do Notion e dos IDs dos seus bancos de dados.

Obtenha seu Token do Notion:

Vá para a página de "Meus tokens de integração" no Notion.

Clique em "+ Novo token de integração" para criar um novo e copie-o.

Encontre os IDs dos Bancos de Dados:

No seu banco de dados de cartas principal e no banco de dados de registro, clique em ... (três pontos) no canto superior direito e depois em Copiar link do banco de dados.

O ID é a sequência de caracteres entre a URL e o ?v=. Por exemplo, se a URL for https://www.notion.so/meu-nome/ID-DO-DB?v=..., o ID é ID-DO-DB.

Configure o Script:

Abra o Google Apps Script e cole o código completo.

Substitua os valores das constantes no início do arquivo:

JavaScript

const NOTION_TOKEN = "COLE_O_SEU_TOKEN_AQUI";
const DB_MAIN = "COLE_O_ID_DO_SEU_DB_PRINCIPAL";
const DB_REGISTRO = "COLE_O_ID_DO_SEU_DB_DE_REGISTRO";
Execute o Script:

Clique em Executar no editor do Google Apps Script.

Na primeira vez, você precisará autorizar o script a se conectar aos serviços do Google e ao Notion.

Observações Importantes
Web Scraping (Status Atual)
A parte do código que faz web scraping foi projetada para extrair dados do site oficial de Dragon Ball Super Card Game. No entanto, o web scraping é uma técnica frágil e pode quebrar se o site mudar seu layout.

No momento, o web scraping não está funcionando. As tentativas de extrair os dados da carta falham, mas o script continua a funcionar graças ao seu sistema de fallback.

O código foi mantido para referência futura. Caso uma API oficial seja lançada ou o site mude de layout para um mais previsível, a função buscarDadosDaCarta pode ser facilmente reescrita. O restante do script, que se comunica com o Notion, não precisará ser alterado.
