# [Internacionalização com Angular](https://angular.io/guide/i18n-overview)

Conceitos iniciais:

- i18n = internacionalização (internacionalization)
- locale: é o idioma de uma certa localidade, normalmente utilizado no padrão Unicode locale ID {idioma}-{LOCALIDADE} exemplo "pt-BR"

## [Passos](https://angular.io/guide/i18n-common-overview)

- `ng add @angular/localize`
- usar pipe de moeda com locale id `{{ amount | currency : 'en-US' }}`
- adicione o atributo `i18n` em todo conteúdo textual estático `<h1 i18n="site header|An introduction header for this sample">Hello i18n!</h1>`
- adicione o atributo `i18n-{nome-do-atributo}` `<img [src]="logo" i18n-title title="Angular logo" alt="Angular logo"/>`
- adicionar `$localize` antes de string `$localize ':site header|An introduction header for this sample:Hello i18n!';`
- [incluir expressões ICU para plurais](https://angular.io/guide/i18n-common-prepare#mark-plurals) `<span i18n>Updated {minutes, plural, =0 {just now} =1 {one minute ago} other {{{minutes}} minutes ago}}</span>`
- [incluir expressões ICU para gênero] `<span i18n>The author is {gender, select, male {male} female {female} other {other}}</span>`
