# Revisão inicial — 12/11/2026

Inspeção estática do manifesto, Dispatcher e Performer. Workflows preservados.

| Prioridade | Evidência | Próxima ação |
| --- | --- | --- |
| Alta | Revisão usa `Confidence < 1.01f` | Limite configurável e testes dos dois caminhos |
| Alta | Caminho, fila e workspace fixos no Dispatcher; bucket fixo no Performer | Parametrizar ambiente |
| Alta | Fila contém `FilePath` local | Garantir acesso do Performer ou transportar via storage |
| Alta | JSON concatenado e acesso direto à primeira linha | Serializar e validar campos ausentes |
| Alta | HTTP não captura `StatusCode` nem `Result` | Validar resposta, repetição e idempotência |
| Média | Dependência Excel preview | Restaurar e verificar compatibilidade |
| Média | Existe `Framework/~Process.xaml` | Confirmar se é cópia de edição antes de remover |

Verificação: XML dos XAML e JSON do manifesto/taxonomia. Isso não equivale a compilação ou execução UiPath. Nenhum OCR, Orchestrator, Action Center ou webhook foi acionado. O Excel de configuração ainda precisa de revisão antes da execução.
