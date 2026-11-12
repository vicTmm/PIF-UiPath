# PIF UiPath — Processamento Inteligente de Faturas

Projeto em preparação para estudo e evolução por Victor Hugo. A execução neste ambiente ainda não foi validada.

## Estrutura

- `Dispatcher.xaml`: procura PDFs locais e adiciona referências aos arquivos na fila do Orchestrator.
- `Main.xaml` e `Framework/`: Performer baseado em REFramework.
- `Framework/Process.xaml`: OCR, extração com Document Understanding, revisão no Action Center e HTTP POST.
- `DocumentProcessing/taxonomy.json`: taxonomia.
- `Data/Config.xlsx`: configurações.
- `Tests/`: workflows de teste herdados, ainda não executados neste projeto.

Os campos previstos são número da nota, CNPJ e valor total. O Performer precisa conseguir acessar os caminhos locais registrados pelo Dispatcher.

## Preparar o ambiente

1. Clone `https://github.com/vicTmm/PIF-UiPath.git` e abra o projeto no UiPath Studio para Windows.
2. Restaure as dependências de `project.json`. O manifesto registra Studio `26.0.196.0` e atividades Excel em versão preview; valide a compatibilidade no ambiente de destino.
3. Configure seu Orchestrator, fila, Document Understanding, Storage Bucket e Action Center, com serviços e permissões disponíveis.
4. Revise `Data/Config.xlsx`, incluindo `DU_ApiKey` e `Webhook_Endpoint`. Use credenciais próprias e não publique segredos.
5. Ajuste no Dispatcher a pasta `C:\Temp\Faturas_Entrada`, a fila `Q_Invoices_Processing` e a pasta do Orchestrator, ainda ligada ao workspace original.
6. Revise no Performer o bucket `DU_Storage_Invoices`, a pasta `Faturas` e o endpoint do extrator. Alterar apenas o Excel não ajusta todos esses valores.
7. Use PDFs fictícios, execute o Dispatcher e depois `Main.xaml`. Acompanhe o Action Center e use um webhook de teste sob seu controle.

## Limitações e próximas iterações

O código usa `Confidence < 1.01f`, embora o README anterior descrevesse 80%. Para valores entre 0 e 1, qualquer valor extraído satisfaz a condição. A regra precisa ser ajustada e testada.

O JSON é montado por concatenação, e a atividade HTTP não armazena status nem corpo da resposta.

- [ ] Parametrizar caminhos, fila, pasta, bucket e confiança.
- [ ] Revisar credenciais e preparar configuração de exemplo sem segredos.
- [ ] Serializar o JSON e validar campos ausentes.
- [ ] Validar respostas HTTP e definir repetição e idempotência.
- [ ] Preparar PDFs fictícios e executar testes no Studio e Orchestrator.
- [ ] Documentar execução e contribuições próprias.

Veja a [revisão inicial](docs/revisao-inicial.md).

## Licença

[MIT](LICENSE).
