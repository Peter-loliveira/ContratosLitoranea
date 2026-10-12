# Gerador de Contratos (Locação e Venda) – RE/MAX Litorânea

Sistema web de arquivo único (`gerador-contrato-locacao.html`) que gera, em formato **Word (.docx)** e a partir de um formulário, dois tipos de contrato: **ALUGUEL** (Contrato de Locação de Imóvel Residencial) e **VENDA** (Contrato de Compra e Venda, inclusive com financiamento, e Promessa de Cessão de Direitos Hereditários c/c Compra e Venda). O Word gerado reproduz o modelo original da imobiliária (cabeçalho com logos, numeração de cláusulas, formatação e rodapé), com os dados de cada contrato preenchidos.

O visual segue as cores da RE/MAX (vermelho `#DC1C2E` e azul `#003DA5`).

---

## Principais características

- **Um único arquivo HTML**, sem instalação e sem servidor. Basta abrir no navegador (Chrome, Edge, Firefox, Safari).
- **Funciona offline**: o modelo do contrato, a biblioteca de geração do .docx e o logo estão embutidos no arquivo.
- **Privacidade**: os dados digitados ficam no navegador e o Word é montado no próprio computador. Nada é enviado a servidores.
- **Fiel ao modelo**: o contrato é gerado a partir do próprio documento Word original, não de um texto refeito. Por isso layout, fontes, logos, linhas e numeração são preservados.
- **Vários proprietários e vários inquilinos**, com botões para adicionar e remover.
- **Cálculos automáticos**: data final do contrato, valores e prazos por extenso, caução sugerida.
- **Importação de contratos existentes** (.docx) para corrigir e gerar novamente.

---

## Como usar

1. Abra o arquivo `gerador-contrato-locacao.html` no navegador.
2. No topo, escolha o **tipo de contrato** (campo “Selecione um tipo de contrato”): **ALUGUEL** ou **VENDA**. Até a escolha, nada mais é exibido. As seções descritas daqui até “Importar contrato existente” são as do ALUGUEL; a VENDA está descrita na seção “Contrato de VENDA”.
3. Todas as seções começam **recolhidas**. Clique no título para abrir, ou use **Expandir tudo** / **Recolher tudo** no topo.
4. Preencha as seções (campos marcados com `*` são obrigatórios).
5. Clique em **Gerar contrato (.docx)**, na barra fixa no rodapé da tela.
6. O arquivo é baixado com o nome `Contrato_Locacao_<NOME_DO_1º_INQUILINO>_<AAAA-MM-DD>.docx` (a data é a do início do aluguel). A barra de status mostra a data de término calculada.
7. Abra o arquivo no Word e confira antes de imprimir ou enviar para assinatura.

Se faltar algum campo obrigatório, o sistema abre a seção correspondente, destaca o campo em vermelho e leva a tela até ele.

---

## Seções do formulário

| Nº | Seção | O que pede |
|----|-------|------------|
| 1 | **Locador(es) / Proprietário(s)** | Nome, CPF, RG, nacionalidade, estado civil, profissão e endereço. Botão **+ Adicionar outro proprietário**. |
| 2 | **Locatário(s) / Inquilino(s)** | Mesmos dados dos locadores. Botão **+ Adicionar outro inquilino**. |
| 3 | **Imóvel** | Tipo (lista), mobiliado ou não, endereço completo e composição (cômodos). |
| 4 | **Prazo da locação** | Início do aluguel e prazo em meses. O **término é calculado** e exibido na hora. |
| 5 | **Valores** | Aluguel mensal, **garantia da locação (caução ou seguro)** e o que o aluguel inclui (condomínio, IPTU, água). |
| 6 | **Pagamento do aluguel** | Banco, agência, conta, tipo e chave PIX, favorecido, dia de vencimento e tolerância. |
| 7 | **Contas de consumo** | Lista de contas por conta do locatário (energia, água, gás…), cada uma com seu número de contrato. |
| 8 | **Assinatura e testemunhas** | Local e data de assinatura; nome e CPF de duas testemunhas (opcionais). |
| 9 | **Imobiliária e corretor** | Dados da imobiliária e do corretor, já preenchidos (recolhida por padrão). |
| 10 | **Condições do contrato** | Multas, juros, prazos, reajuste, rescisão, foro e número de vias, com os valores padrão do modelo (recolhida por padrão). |

### Detalhes dos campos

- **Tipo do imóvel**: Casa, Casa de Condomínio, Apartamento, Sala Comercial, Kitnet, Studio, Flat e Cobertura. Aparece em maiúsculas na Cláusula 1ª.
- **Mobília**: "Mobiliado" acrescenta ao texto a informação de que os móveis serão discriminados em laudo de vistoria; "Não mobiliado" omite o trecho.
- **Início e prazo**: informe a data de início e o número de meses. O término segue a convenção do modelo original, ou seja, **o mesmo dia do mês** após o prazo (05/10/2026 + 30 meses = 05/04/2029). Se o dia não existir no mês final, usa o último dia do mês.
- **Aluguel**: abaixo do campo o valor aparece **por extenso**.
- **Garantia da locação** (logo abaixo do aluguel): escolha **uma única opção** com os botões de rádio.
  - **Caução**: informe o valor. Ao digitar o aluguel, a caução é preenchida automaticamente com **2 aluguéis** (como no modelo); você pode editá-la e, se apagar o campo, ela volta a acompanhar o aluguel. O valor também aparece por extenso.
  - **Seguro**: informe apenas o nome da **empresa seguradora**. O campo da opção não escolhida fica desativado e não é exigido.
  - O texto das Cláusulas 3.3 a 3.5 muda conforme a escolha. Com **caução**, o texto é o do modelo original. Com **seguro**, entra um texto de seguro de fiança locatícia (contratação e manutenção da apólice, art. 37, III, e art. 41 da Lei do Inquilinato, e responsabilidade do locatário por danos ou débitos não cobertos). **Esse texto não consta no modelo original e deve ser revisado pelo responsável jurídico antes do uso.**
- **O aluguel inclui**: marque condomínio, IPTU e/ou água. Os itens marcados formam a frase "estando incluso no presente valor, os custos de …" na Cláusula 3ª. Se nenhum for marcado, a frase é omitida. Se **condomínio** não estiver incluso, a cláusula 6.3.1 passa a atribuir as taxas de condomínio ao locatário.
- **Contas de consumo**: cada linha tem "Conta (tipo / concessionária)" e "Nº da conta contrato". Há sugestões (Energia (COELBA), Água (EMBASA), Gás (SUPERGASBRAS)), mas o texto é livre. Use **+ Adicionar outra conta** e **Remover**. As contas entram nas cláusulas 6.1 e 6.2, por exemplo: *"Energia (COELBA conta contrato 123) e Gás (SUPERGASBRAS conta contrato 456)"*.
- **CPF**: a máscara `000.000.000-00` é aplicada ao digitar.
- **Testemunhas**: se deixadas em branco, o Word sai com linhas para preenchimento à mão.

---

## Regras automáticas aplicadas no texto

- Números **por extenso** em prazos, valores em reais e percentuais (ex.: `30 (trinta) meses`, `R$ 1.500,00 (mil e quinhentos reais)`, `10% (dez por cento)`).
- Datas no padrão do modelo: `05 de OUTUBRO de 2026` nas cláusulas; `03 de outubro de 2026` na assinatura.
- Concordância do rótulo da multa rescisória: "aluguel" (singular) ou "aluguéis" (plural).
- A cláusula de multa por saída antecipada usa o mês seguinte à carência informada (ex.: carência de 12 meses → "13º (décimo terceiro) mês").
- Correção de pequenos erros de digitação do modelo original (por exemplo, "LÁUSULA 5ª", "E m caso", "R$ R$" e "Camaçarí").

---

## Documento Word gerado

- **Partes**: cada locador e cada locatário ganha um bloco de qualificação numerado (LOCADOR(A) 1, 2…; LOCATÁRIO(A) 1, 2…). Com apenas uma pessoa, não há numeração.
- **Assinaturas das partes**: tabela de duas colunas, com **locadores à esquerda** e **locatários à direita**, qualquer que seja a quantidade de cada lado. Em seguida, a linha do corretor.
- **Testemunhas**: lado a lado, com linha de assinatura, nome e CPF.
- **Cabeçalho**: logo RE/MAX Litorânea e o ícone de balão da RE/MAX (imagem fornecida pela imobiliária), mantidos do modelo.
- O arquivo é um .docx padrão, editável normalmente no Word.

---

## Importar contrato existente

O botão vermelho **📂 Importar contrato existente (.docx)**, no topo, serve para **corrigir** contratos já feitos.

1. Clique no botão e escolha o arquivo .docx.
2. O sistema lê o texto do contrato e preenche o formulário: partes (quantas houver), imóvel, prazo, valores, pagamento, contas de consumo, condições, foro, data e testemunhas.
3. Aparece um quadro com o resumo e a **lista de campos que não foi possível identificar** (se houver).
4. As seções são abertas para revisão. Corrija o que estiver errado e clique em **Gerar contrato (.docx)**.

Observações:

- Funciona com contratos **gerados por este sistema** e com contratos feitos a partir do **modelo original** da imobiliária. O contrato é lido pelo **texto atual** do arquivo, então alterações manuais feitas no Word são consideradas, desde que a frase continue seguindo o padrão do modelo.
- Se uma frase foi reescrita fora do padrão, o campo correspondente fica com o valor padrão ou em branco e é listado como "não identificado".
- A importação **substitui** tudo o que estiver preenchido no formulário.
- Valores fora das listas (ex.: um estado civil como "Casada") são acrescentados automaticamente às opções.
- Erros do contrato antigo vêm junto para o formulário, para você corrigi-los (por exemplo, um CNPJ com pontuação errada).
- Revise sempre os dados importados antes de gerar o novo arquivo.

---

## Seções recolhíveis e navegação

- Todas as seções têm número em círculo vermelho e seta à direita, e abrem e fecham ao clicar no título.
- Cada locador e cada locatário adicionado também pode ser recolhido individualmente.
- **Expandir tudo** e **Recolher tudo** controlam todas as seções de uma vez.

---

## Contrato de VENDA

Ao escolher **VENDA**, o formulário usa as seções abaixo, no mesmo estilo do aluguel. O Word é montado a partir dos modelos de compra e venda da imobiliária (cabeçalho, rodapé, numeração e cláusulas preservados).

| Nº | Seção | O que pede |
|----|-------|------------|
| 1 | **Modalidade da venda** | *Compra e venda de imóvel residencial* ou *Promessa de cessão de direitos hereditários c/c compra e venda*. |
| 2 | **Vendedor(es)** | Nome, CPF, RG, nacionalidade, estado civil, profissão, telefone, e-mail e endereço. Quantos forem necessários (**+ Adicionar outro vendedor**). Na cessão, vira “Vendedores(as) / herdeiros(as) cedentes”. |
| – | **Falecido(a) – “de cujus”** *(só na cessão)* | Nome, CPF, RG, órgão emissor, estado civil, profissão, endereço e data do falecimento. |
| – | **Cônjuges anuentes** *(só na cessão)* | Mesmos dados das partes, opcionais. Se não houver, o bloco não aparece no contrato. |
| 3 | **Comprador(es)** | Mesmos dados, com quantos compradores forem necessários. |
| 4 | **Imóvel** | Tipo, área construída e total, inscrição municipal, matrícula, endereço, cartório e descrição. Campos em branco não aparecem no contrato. |
| 5 | **Preço e forma de pagamento** | Valor do imóvel e escolha entre **sem financiamento** e **com financiamento**. |
| 6 | **Contas bancárias** | Conta do comprador (origem) e conta(s) do vendedor (destino). |
| 7 | **Honorários de corretagem** | Percentual, valor (calculado) e após qual pagamento (A, B, C…) serão pagos. |
| 8 | **Posse e IPTU** | Quando a posse é transmitida e o ano do IPTU proporcional. |
| 9 | **Corretor(a) responsável** | Nome (digitado), CPF, RG e CRECI-BA do(a) corretor(a). |
| 10 | **Assinatura e testemunhas** | Cidade, data e testemunhas (opcionais). |
| 11 | **Condições do contrato** | Multas, juros, honorários de advogado, prazo de devolução, vias, foro e dados de recebimento dos honorários, com os valores padrão do modelo. |

### Forma de pagamento

- **Sem financiamento**: lista de pagamentos, com **+ Adicionar pagamento** (quantos forem necessários). Cada pagamento tem: *referente a* (sinal de compra, entrada de compra, parcela de compra ou quitação de compra), **valor**, **forma** (transferência/PIX/TED, dinheiro ou cheque) e **quando** (no ato da assinatura, em uma data específica ou outro prazo/condição descrito). Os pagamentos viram os itens A), B), C)… da Cláusula 3ª.
- **Com financiamento**: entrada (valor, forma e quando), opção **“O comprador utilizará FGTS”** (com valor) e **financiamento bancário** (banco financiador e valor). O valor financiado é sugerido automaticamente (preço − entrada − FGTS) e pode ser editado.
- **Conferência**: um quadro mostra a soma dos pagamentos e se ela confere com o valor do imóvel. O contrato só é gerado se a soma for **igual** ao preço.
- **Contas de destino**: havendo mais de uma conta (por exemplo, dois vendedores), o valor de cada pagamento é dividido pelos percentuais informados (divisão igual por padrão), como no modelo da cessão.

### Singular e plural

O texto se ajusta ao número de pessoas: com um vendedor, “PROMITENTE VENDEDOR”; com mais de um, “PROMITENTES VENDEDORES(AS)”, com artigos e verbos concordando (“obriga-se” / “obrigam-se”, “promete” / “prometem” etc.). O mesmo vale para os compradores. Na cessão, mantém-se a forma “(a)” do modelo.

### Observações da venda

- Os trechos que eram **anotações internas** dos modelos (“Caso nosso cliente seja o Comprador…”) viraram a escolha **“Quando será transmitida a posse”**: liquidação final do preço, momento do sinal/arras ou entrada, ou liquidação final após a comprovação do depósito do financiamento.
- As assinaturas saem em duas colunas (vendedores e cônjuges anuentes à esquerda, compradores à direita), seguidas do corretor e das testemunhas.
- **Não há importação** de contratos de venda existentes (a importação é só do aluguel).
- Os textos do item de **FGTS** e do **financiamento** foram adaptados a partir do modelo de financiamento e devem ser revisados pelo responsável jurídico.

---

## Limitações conhecidas

- Estas limitações são do ALUGUEL: o modelo é de **locação residencial**. Escolher "Sala Comercial" no tipo do imóvel não adapta o texto: o título e as cláusulas de uso continuam residenciais.
- As garantias previstas são **caução** ou **seguro de fiança locatícia** (uma ou outra). Não há opção de fiador.
- Os termos "LOCADOR(A)" e "LOCATÁRIO(A)" permanecem no singular mesmo com várias pessoas.
- O **endereço e os contatos do cabeçalho** do Word (texto ao lado do logo) são fixos; só mudam se o modelo for alterado.
- Os dados **não são salvos** entre sessões. Para continuar um contrato depois, gere o .docx e use a importação.
- O **texto das cláusulas fixas** está embutido no arquivo. Alterar o conteúdo jurídico do modelo exige gerar uma nova versão do HTML.

---

## Resumo técnico

- HTML + CSS + JavaScript puro, em um só arquivo.
- Geração do .docx no navegador com **JSZip** (embutida): o sistema abre o modelo Word embutido, substitui marcadores `{{campo}}` no XML do documento, monta os blocos repetidos (partes, assinaturas, testemunhas) e baixa o resultado.
- Importação: lê `word/document.xml` do arquivo enviado e extrai os campos por padrões de texto das cláusulas.
- Compatível com Word e LibreOffice.
