## Formulário Symfony + SQLite

Aplicação Symfony 8 com formulário de contato, salvando mensagens em SQLite.

### Requisitos
- PHP 8.4+
- Composer (phar já incluso no diretório raiz, pode usar `php composer`)

### Instalação
```bash
cd /Users/vicenteneto/Documents/codigos/formulario/app
php ../composer install
```

### Configuração de banco
- Em `app/.env`, `DATABASE_URL` já está para SQLite:
  ```
  sqlite:///%kernel.project_dir%/var/data_%kernel.environment%.db
  ```
- Para criar/atualizar o schema:
```bash
php bin/console doctrine:schema:update --force
```

### Executar servidor de desenvolvimento
```bash
cd /Users/vicenteneto/Documents/codigos/formulario/app
php -S localhost:8000 -t public
```
Acesse: http://localhost:8000

### Estrutura principal
- `src/Entity/Contact.php` – entidade com validações.
- `src/Form/ContactType.php` – definição do formulário.
- `src/Controller/ContactController.php` – exibe e processa o formulário.
- `templates/contact/form.html.twig` – template principal.
- `public/css/custom.css` – estilo moderno (glass/dark).

### Fluxo do formulário
1) Usuário acessa `/` e preenche nome, e-mail e mensagem.  
2) Symfony valida; em sucesso salva em SQLite (`var/data_dev.db`) e mostra flash de sucesso.  

### Comandos úteis
- Listar rotas: `php bin/console debug:router`
- Validar schema: `php bin/console doctrine:schema:validate`
- Limpar cache: `php bin/console cache:clear`

### Observações
- Para usar outro banco (ex.: MySQL/Postgres), ajuste `DATABASE_URL` e rode `doctrine:migrations:diff` + `doctrine:migrations:migrate`.
- Assets: `asset()` habilitado via `symfony/asset`.
# formulario.php
