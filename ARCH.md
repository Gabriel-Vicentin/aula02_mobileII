## Estrutura final 
```
lib/
  main.dart
  app_root.dart
  core/
    app_errors.dart
  features/
    todos/
      data/
        datasources/
          todo_remote_datasource.dart
          todo_local_datasource.dart
        models/
          todo_model.dart
        repositories/
          todo_repository_impl.dart
      domain/
        entities/
          todo.dart
        repositories/
          todo_repository.dart
      presentation/
        pages/
          todos_page.dart
        viewmodels/
          todo_viewmodel.dart
        widgets/
          add_todo_dialog.dart
```

## Fluxo de dependências
UI → ViewModel → Repository → LocalDataSource/RemoteDatasource

## Decisões

### Tratamento da validação?
No `TodoViewModel`, antes de chamar o repositório — títulos vazios
são rejeitados na camada de apresentação, sem chegar ao repositório.

### parsing JSON?
Em `TodoModel` (camada `data/models`), no método `fromJson`.


### Tratamento de Erros?
Os erros HTTP são lançados como `Exception` em `TodoRemoteDataSource`
e capturados no `TodoViewModel` com `try/catch`, que expõe uma
mensagem de erro via estado para a UI exibir — sem que a UI
acesse HTTP ou SharedPreferences diretamente.


