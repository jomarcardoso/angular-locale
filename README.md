# [Internacionalização com Angular](https://angular.io/guide/i18n-overview)

Conceitos iniciais:

- i18n = internacionalização (internacionalization)
- locale (localidade): é o idioma, unidade monetária, fuso horário, entre outros, de uma certa localidade, normalmente utilizado no padrão Unicode locale ID {idioma}-{LOCALIDADE} exemplo "pt-BR"

## [Passos](https://angular.io/guide/i18n-common-overview)

- `ng add @angular/localize`
- usar pipe de moeda com locale id `{{ amount | currency : 'en-US' }}`
- adicione o atributo `i18n` em todo conteúdo textual estático `<h1 i18n="site header|An introduction header for this sample">Hello i18n!</h1>`
- adicione o atributo `i18n-{nome-do-atributo}` `<img [src]="logo" i18n-title title="Angular logo" alt="Angular logo"/>`
- adicionar `$localize` antes de string `$localize ':site header|An introduction header for this sample:Hello i18n!';`
- [incluir expressões ICU para plurais](https://angular.io/guide/i18n-common-prepare#mark-plurals) `<span i18n>Updated {minutes, plural, =0 {just now} =1 {one minute ago} other {{{minutes}} minutes ago}}</span>`
- [incluir expressões ICU para gênero] `<span i18n>The author is {gender, select, male {male} female {female} other {other}}</span>`
- matar a pau `ng extract-i18n`
- a tradução deve ser uma cópia do arquivo original com o sufixo do idioma `src/locale/messages.fr.xlf`
- [altere o arquivo de tradução para incluir os `<target>`](https://angular.io/guide/i18n-common-translation-files)

```xlf
<trans-unit id="ba0cc104d3d69bf669f97b8d96a4c5d8d9559aa3" datatype="html">
  <source>I don&apos;t output any element</source>
  <target>Je n'affiche aucun élément</target>
</trans-unit>
```

- configurar o angular.json para gerar vários dists

```json
{
  "projects": {
      "angular.io-example": {
        "i18n": {
          "sourceLocale": "en-US",
          "locales": {
            "pt": {
              "translation": "src/locale/messages.pt.xlf",
            }
          }
        },
        "architect": {
          "build": {
            "builder": "@angular-devkit/build-angular:browser",
            "options": {
              "localize": true,
            }
          }
        }
      }
    }
  }
}
```

- criar as configurações para desenvolvimento

```json
{
  "projects": {
      "angular.io-example": {
        "architect": {
          "build": {
            "configuration": {
              "pt": {
                "localize": ["pt"]
              }
            },
          },
          "serve": {
            "builder": "@angular-devkit/build-angular:dev-server",
            "configurations": {
              "pt": {
                "browserTarget": "angular.io-example:build:development,pt"
              }
            }
          }
        }
      }
    }
  }
}
```
