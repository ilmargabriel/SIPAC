# Especificação de Caso de Uso: Cadastrar Plano de Manutenção

## 1. Descrição do Caso de Uso

Caso de uso responsável por exibir as requisições que estão em rota visita, isto é, os executantes saíram para execução do serviço de manutenção.

## 2. Pré-condições

- O ator deve estar logado no sistema e ter permissão de gestor de manutenção.

## 3. Pós-condições

- Requisição transformada para outro tipo de requisição de infraestrutura (meio ambiente, projeto/obra, parecer técnico avaliação) quando o seu status é alterado.

## 4. Fluxo de Eventos

### 4.1. Fluxo Principal

1. O ator seleciona opção em rota visita;
2. O sistema exibe filtros para consulta [[BD01](#bd01)], [[FE01](#fe01)], [[FE02](#fe02)], [[FE03](#fe03)]
3. O sistema exibe lista de requisições em rota visita; [[BD02](#bd02)], [RN01], [[FA02](#fa02)], [[FA03](#fa03)]
4. O sistema exibe ordens de serviço de cada requisição; [[BD03](#bd03)], [[FA05](#fa05)]
5. O ator seleciona uma ou mais requisições na lista; [[FA01](#fa01)], [[FA02](#fa02)]
6. O ator seleciona opção de continuar;
7. O sistema solicita ao ator que informe o tipo de operação;
8. O sistema exibe lista das requisições selecionadas; [[BD03](#bd03)]
9. O ator informa o tipo de operação; [[BD04](#bd04)], [[FA04](#fa04)]
10. O ator confirma operação;
11. O sistema exibe mensagem “Operação Realizada com Sucesso”;
12. O Caso de Uso é encerrado.

### 4.2. Fluxos Alternativos:
#### FA01
**Consultar requisição em rota visita:**
1. O ator consulta requisição informando um ou mais filtros exibidos pelo sistema e aciona opção de Buscar;
2. O sistema exibe lista de requisições conforme consulta;
3. O sistema retorna ao passo 3 do Fluxo Principal.

#### FA02
**Gerar cópia da requisição principal:**
1. O ator acionou a opção de gerar cópia da Requisição; [RN002], [RN003], [RN004], [RN005];
2. O sistema estende o caso de uso UC0002_SIPAC_Infraestrutura_CadastrarRequisicaodeManutencao - FA01 – Passo 02;

#### FA03
**Visualizar Ordem de Serviço:**
1. O ator acionou opção de “Visualizar Ordem de Serviço”;
2. O sistema estende o caso de uso UC0004_SIPAC_Infraestrutura_ConsultarOrdemdeServico;

#### FA04
**Tipo de operação serviço executado:**
1. O ator selecionou o status “Serviço Executado”;
2. O sistema solicita que o ator informe o valor da hora estimado para execução do serviço de manutenção;
3. Este fluxo é encerrado.

#### FA05
**Alterar Ordem de Serviço:**
1. O ator selecionou opção alterar ordem de serviço;
2. O sistema estende o caso de uso UC0005_SIPAC_Infraestrutura_AguardandoVisita.

### 4.3. Fluxo de Exceções

#### FE01
**Campo não Informado – Número/Ano da Requisição, tipo de Serviço, Profissional, Período da Requisição ou Categoria Profissional**
1. O ator selecionou o campo “<Nome do Filtro>” e não informou o <Nome do Filtro> e acionou a opção “Buscar”;
2. O sistema exibe a mensagem de “<Nome do Filtro>”: Campo obrigatório não informado.”
3. O sistema retorna ao Passo 2 do Fluxo Principal.

#### FE02
**Campo Informado Inválido – Número/Ano da Requisição**
1. O ator selecionou o campo “Número/Ano da Requisição” e informou uma requisição inexistente e acionou a opção “Buscar”;
2. O sistema exibe a mensagem de “Nenhuma requisição foi encontrada com os parâmetros de busca utilizados”;
3. O sistema retorna ao Passo 2 do Fluxo principal.

#### FE03
**Campo Informado Inválido – Período da Requisição**
1. O ator selecionou o filtro “Período da Requisição” e informou a data inicio ou fim em formato inválido e acionou a opção “Buscar”;
2. O sistema exibe a mensagem de “Início do Período: dd/mm/aaaa ou “Fim do Período: dd/mm/aaaa” não é um formato de data válido.”;
3. O sistema retorna ao Passo 2 do Fluxo Principal.


## 5. Blocos de Dados

### BD01

**Campos solicitados na Consulta de Requisição**

Campo                                 | Tipo                     | Obrigatório   | Observações
------------------------------------- | ------------------------ | ------------- | -------------
Número/ano da requisição              | Alfanumérico             | Sim           | O número é sequencial e gerado pelo sistema ao cadastrar a requisição. Na mudança de ano este número é reiniciado.                
Período da Requisição                 | Data | Sim               | Correspondem a data de cadastro da requisição.            
Tipo do Serviço                       | Seleção Única            | Sim           |
Categoria Profissional                | Seleção Única            | Sim           | Categorias cadastradas no UC0001-SIPAC-Infraestrutura-Cadastrar Categorias
Profissional                          | Autocomplete             | Sim           | Exibe os nomes dos profissionais terceirizados cadastrados no UC0003-SIPAC– Cadastrar contratados        

N/A: Não se Aplica.


### BD02

**Dados exibidos no resultado da Consulta de Requisições**

Campo                                 | Tipo                     | Obrigatório   | Observações
------------------------------------- | ------------------------ | ------------- | -------------
Número/Ano da Requisição              | N/A                      | Sim           | O número é sequencial e gerado pelo sistema ao cadastrar a requisição. Na mudança de ano este número é reiniciado.                
Descrição                             | N/A                      | Sim           | N/A
Unidade Requisitante                  | N/A                      | Sim           | N/A
Status                                | N/A                      | Sim           | N/A
Gerar Cópia                           | Imagem                   | Sim           | N/A

N/A: Não se Aplica.


### BD03

**Campos exibidos na lista de ordem de serviço**

Campo                                 | Tipo                     | Obrigatório   | Observações
------------------------------------- | ------------------------ | ------------- | -------------
Número/Ano da Requisição              | N/A                      | Sim           | O número é sequencial e gerado pelo sistema ao cadastrar a requisição. Na mudança de ano este número é reiniciado.                
Descrição                             | N/A                      | Sim           | N/A
Unidade Requisitante                  | N/A                      | Sim           | N/A
Status                                | N/A                      | Sim           | N/A

N/A: Não se Aplica.

### BD04

**Campos exibidos na lista de ordem de serviço**

Campo                                 | Tipo                     | Obrigatório   | Observações
------------------------------------- | ------------------------ | ------------- | -------------
Tipo de Operação                      | Seleção Única            | Sim           | O sistema mostra as opções: Aguardando Pedido de Material, Serviço Executado, Serviço não Executado, Serviço Executado parcialmente e mudar de diretoria.

N/A: Não se Aplica.


## 6. Requisitos Legais

### RL01

- LEI FEDERAL Nº 8.666, DE 21 DE JUNHO DE 1993  licitações e contratos da Administração Pública e dá outras providências Art. 1º, § 1º, inciso I.

## 7. Regras de Negócio


**Cópia da requisição de manutenção:**

### RN01
- O sistema não deve permitir criar uma cópia da requisição de manutenção filha partir de outra filha.

### RN02
- Não será permitido criar uma cópia se a requisição original se todas as filhas estiverem como “Serviço Executado” ou “Serviço não Executado” ou “Serviço Executado parcialmente”.

### RN03
- Se a requisição original não tiver filha não poderá criar cópia quando tiver Serviço Executado ou “Serviço não Executado” ou “Serviço Executado Parcialmente”.

### RN04
- Quando for marcar “Serviço Executado” ou “Serviço não Executado” ou “Serviço Executado Parcialmente” perguntar se o usuário deseja criar uma cópia.

**Mudança de status da requisição:**

### RN05
- O sistema só permitir atribuir os status “Serviço Executado” ou “Serviço não Executado” ou “Serviço Executado Parcialmente”. Deve permitir, ainda, transferir para outra diretoria alterando o tipo da requisição ou alterar o status para “aguardando material”.
Legislação:

### RN06
- Considerando o [RL01] o sistema deverá fazer …..

**Restrição na lista de requisição:**
### RN07
- O sistema só deve exibir requisições que estão nos estados em rota visita ou em execução.


## 8. Glossário do Documento

Não se Aplica.
