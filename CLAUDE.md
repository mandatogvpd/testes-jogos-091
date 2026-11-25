# Regras do projeto (Mandato GVPD)

Este arquivo é lido pelo Claude no início de cada sessão. Vale para todos os projetos criados a partir deste modelo. Se o projeto tiver regras próprias, adicione-as na seção "Específico deste projeto" no final.

## Contexto
- Organização: Mandato GVPD. Os projetos apoiam o trabalho do mandato: sites e páginas, análises de dados, automações, documentos e relatórios.
- Quem usa: pessoas da equipe, muitas sem experiência com Git ou programação. Explique em linguagem simples, sem jargão desnecessário, e diga o que foi feito ao final.

## Idioma e tom
- Responder, comentar o código, escrever commits e documentação em **português do Brasil**.
- Textos para o público (posts, notas, sites, discursos) são **rascunho**: devem ser revisados por uma pessoa antes de serem publicados. Não invente fatos, números, datas, citações ou declarações de pessoas.

## Segurança e dados (regra mais importante)
- **Nunca** commitar: senhas, tokens, chaves de API, arquivos `.env`, credenciais.
- **Nunca** commitar dados pessoais: planilhas com nome, CPF, telefone, e-mail, endereço ou outros dados de eleitores, apoiadores, doadores ou servidores. Use dados fictícios em exemplos e testes.
- Se um arquivo sensível for necessário ao trabalho, mantenha-o fora do repositório (ele já é ignorado pelo `.gitignore`) e avise a pessoa responsável.
- Se perceber que algo sensível já foi commitado, **pare e avise imediatamente**. Não basta apagar o arquivo, o histórico ainda o guarda.
- Respeitar a LGPD e a legislação eleitoral aplicável. Em caso de dúvida sobre o uso de dados ou de conteúdo de campanha, perguntar antes de agir.

## Fluxo de trabalho com Git
- Pode commitar **direto na `main`**, sem Pull Request.
- Antes de começar, atualizar com `git pull`. Antes de enviar, conferir com `git status` e `git diff` o que será commitado.
- Commits pequenos e frequentes, com mensagens curtas e claras em português, no imperativo. Exemplos: `Adiciona página de contato`, `Corrige cálculo do total por região`.
- Nunca usar `git push --force` na `main` nem reescrever o histórico.
- Não commitar arquivos gerados, dependências (`node_modules`, `.venv`) nem arquivos grandes sem necessidade.

## Publicação na internet (Cloudflare Pages)
- Por padrão, **nenhum projeto é publicado**. Estar no GitHub não coloca o projeto no ar.
- Só publique se a pessoa pedir. Ao terminar um projeto que poderia virar site ou aplicativo, pergunte uma vez: "Quer que este projeto seja publicado na internet? (sim/não)". Se a resposta for não ou vier sem confirmação, não faça nada e não insista.
- A publicação é feita por um fluxo automático do GitHub (`.github/workflows/publicar.yml`), que só age se existir o arquivo `publicar.json` na raiz do repositório. **Nunca** peça, leia, grave ou use tokens da Cloudflare: eles ficam guardados como segredos da organização no GitHub e não são acessíveis ao Claude.
- Se a resposta for **sim**:
  1. Antes, confirmar que o projeto não contém dados pessoais, credenciais nem informações internas, pois **tudo o que está no projeto publicado fica público**.
  2. Deixar o projeto pronto para publicar e conferir localmente que o build funciona. Ver o formato em `publicar.exemplo.json`: `projeto` (nome do site: só letras minúsculas, números e hífens), `build` (comando de build, ou vazio se for HTML pronto) e `saida` (pasta com os arquivos finais, por exemplo `dist` ou `public`; use `.` para a raiz de um site em HTML puro).
  3. Criar o `publicar.json` na raiz, preencher a seção "Publicação" do `README.md` e fazer o commit na `main`. O envio do commit é o que dispara a publicação.
  4. Dizer à pessoa onde acompanhar: aba **Actions** do repositório no GitHub. O endereço do site será `https://NOME-DO-PROJETO.pages.dev`. Se o fluxo falhar por falta dos segredos `CLOUDFLARE_API_TOKEN` e `CLOUDFLARE_ACCOUNT_ID`, avisar que o administrador da organização precisa configurá-los.
- Para **tirar do ar** ou parar de publicar, apagar o `publicar.json` e avisar que o site já publicado continua no ar até ser removido no painel da Cloudflare por quem administra a conta.
- Depois de publicado, cada commit na `main` atualiza o site automaticamente. Reforçar: testar antes de commitar.
- Páginas que devem ser vistas só pela equipe precisam de controle de acesso (Cloudflare Access). Nunca presumir que um link "escondido" é privado.
- O link público do projeto, quando existir, é anotado no `README.md`.

## Organização do projeto
- Atualizar o `README.md` sempre que o objetivo, a forma de uso ou o responsável mudarem.
- Documentos e anotações de apoio ficam em `docs/`.
- Por tipo de projeto:
  - **Sites e páginas:** manter a estrutura simples, com HTML, CSS e JS em pastas claras, e testar a página antes de commitar.
  - **Análise de dados:** guardar os dados brutos fora do repositório quando forem sensíveis, documentar a origem e a data dos dados, e fazer o código reproduzível.
  - **Automações:** registrar no README o que a automação faz, quando roda e quais acessos usa. Segredos entram por variáveis de ambiente, nunca no código.
  - **Documentos:** preferir formatos abertos (Markdown) quando o arquivo for versionado.

## Qualidade
- Antes de dizer que terminou, rodar ou abrir o resultado e conferir que funciona.
- Conferir números e fontes de qualquer análise. Informar claramente o que não foi possível verificar.
- Em caso de dúvida sobre o que a pessoa quer, perguntar antes de fazer algo grande ou difícil de desfazer.

## Específico deste projeto
<!-- Preencha ao criar o projeto: objetivo, responsáveis, regras próprias, links úteis. -->
