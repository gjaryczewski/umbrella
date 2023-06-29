# umbrella

Projekt Umbrella

## Konfiguracja środowiska deweloperskiego w systemie Windows

```sh
winget install --id Microsoft.WindowsTerminal
winget install --id Git.Git
winget install --id Microsoft.VisualStudioCode
winget install --id Microsoft.AzureDataStudio
winget install --id Docker.DockerDesktop
```

## Konteneryzacja

### Dostarczanie sekretów

Secrets provide a more secure way of getting sensitive information in to your application’s services, so you don’t have to rely on using environment variables. If you’re injecting passwords and API keys as environment variables, you risk unintentional information exposure. Environment variables are often available to all processes, and it can be difficult to track access. They can also be printed in logs when debugging errors without your knowledge. Using Secrets mitigates these risks. Secrets are a flavor of [Configs](https://docs.docker.com/compose/compose-file/08-configs/) focusing on sensitive data, with specific constraint for this usage.

Services can only access secrets when explicitly granted by a `secrets` attribute.

The top-level `secrets` declaration defines or references sensitive data that is granted to the services in your Compose application. The source of the secret is either `file` or `environment`.

* `file`: The secret is created with the contents of the file at the specified path.
* `environment`: The secret is created with the value of an environment variable.
* `external`: If set to true, `external` specifies that this secret has already been created. Compose does not attempt to create it, and if it does not exist, an error occurs.
* `name`: The name of the secret object in Docker. This field can be used to reference secrets that contain special characters. The name is used as is and isn’t scoped with the project name.

Więcej informacji:

* [Secrets top-level element | Docker](https://docs.docker.com/compose/compose-file/09-secrets/)
* [How to use secrets in Docker Compose](https://docs.docker.com/compose/use-secrets/)

### Baza danych Postgresql

[How to Use the Postgres Docker Official Image](https://www.docker.com/blog/how-to-use-the-postgres-docker-official-image/)

Rozszerzenie Visual Studio Code: [PostgreSQL for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-ossdata.vscode-postgresql)

```sh
code --list-extensions
code --install-extension ms-ossdata.vscode-postgresql

azuredatastudio --list-extensions
azuredatastudio --install-extension microsoft.azuredatastudio-postgresql
```

Łączenie z bazą danych przy użyciu Azure Data Studio w środowisku lokalnym:

* Connection type: Postgresql
* Server name: localhost
* Authentication type: Password
* Username: postgres
* Password: hasło z pliku [.env](.env)

W przypadku niestandardowej konfiguracji portu (tj. zmienna środowiskowa UMBRELLA_DB_PORT inna od 5432), w oknie połączenia należy wybrać przycisk `Advanced`, a następnie wskazać niestandardowy port w polu `Port` sekcji `SERVER`.
