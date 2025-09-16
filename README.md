# dio-desafio-projeto-bootcamp-baires-modulo8-projeto3_visao_computacional_com_ml
Desafio de Projeto 3 - Módulo 8 - Testes com Langchain + Azure GPT

Agente de IA para Geração de Testes Unitários com LangChain e Azure OpenAI

Este projeto demonstra a criação de um agente de inteligência artificial em Python capaz de gerar testes unitários automaticamente usando as bibliotecas LangChain e pytest, com o poder do modelo de linguagem do Azure OpenAI Service.

O agente foi projetado para ler um arquivo Python e, de forma autônoma, gerar um arquivo de teste funcional (test_<nome_do_arquivo>.py) que cobre casos de sucesso, falha e casos de borda.

Funcionalidades
Automação Inteligente: Utiliza um AgentExecutor do LangChain para orquestrar as tarefas de leitura, geração e escrita de arquivos de teste.

Integração com Azure: Conecta-se de forma segura à API do Azure OpenAI para acessar modelos de IA avançados como o GPT-3.5-Turbo.

Geração de Código: Gera código de testes unitários no formato pytest, garantindo que o código seja limpo e pronto para ser executado.

Flexibilidade: Pode ser adaptado para gerar testes para qualquer função Python que você forneça.

Como Executar o Projeto
Siga este passo a passo para rodar o agente e gerar seus próprios testes.

1. Configuração do Ambiente
Certifique-se de ter o Python 3.7+ instalado. Clone este repositório e instale as dependências:

Bash

git clone https://github.com/seu-usuario/seu-repositorio.git
cd seu-repositorio
pip install -r requirements.txt
O arquivo requirements.txt deve conter as seguintes dependências:

langchain
langchain-openai
python-dotenv
pytest
2. Configuração do Azure OpenAI
Crie um arquivo chamado .env na raiz do projeto.

Preencha-o com suas credenciais do Azure OpenAI Service, seguindo o exemplo abaixo:

.env

AZURE_OPENAI_API_KEY="sua_chave_de_api"
AZURE_OPENAI_ENDPOINT="https://seu-endpoint.openai.azure.com/"
AZURE_OPENAI_API_VERSION="2023-05-15"
AZURE_OPENAI_DEPLOYMENT_NAME="seu_modelo_implantado"
Substitua os valores com as suas credenciais, obtidas no portal do Azure.

3. Execução do Agente
O agente foi projetado para ler o arquivo funcoes_para_teste.py por padrão. Basta executar o script principal:

Bash

python main.py
O agente irá exibir seu processo de raciocínio no terminal (verbose=True), e ao final, criará um novo arquivo chamado test_funcoes_para_teste.py no mesmo diretório.

4. Verificação e Execução dos Testes
Para verificar se os testes gerados funcionam corretamente, utilize o pytest:

Bash

pytest test_funcoes_para_teste.py
O pytest irá rodar todos os testes no arquivo e reportar os resultados, confirmando a eficácia do agente.

Exemplo de Uso
Este projeto inclui o arquivo funcoes_para_teste.py com duas funções simples. O agente gerou o seguinte código de teste para elas:

Código de teste gerado:

Python

# test_funcoes_para_teste.py
import pytest
from funcoes_para_teste import soma, divisao

def test_soma():
    assert soma(2, 3) == 5
    assert soma(-1, 1) == 0
    assert soma(0.5, 0.5) == 1.0
    assert soma(-10, -5) == -15

def test_divisao():
    assert divisao(10, 2) == 5.0
    assert divisao(5, 2) == 2.5
    assert divisao(-10, 2) == -5.0

def test_divisao_por_zero():
    with pytest.raises(ValueError, match="Divisor não pode ser zero."):
        divisao(10, 0)
