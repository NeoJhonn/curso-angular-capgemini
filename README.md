# Curso Angular Capgemini

- Instalar versão 14 do Angular: ``npm i -g @angular/cli@14``

- Instalar seguintes extesões no VSCode:
  -Angular language service.

- Criando um projeto no Angular: ng new nome-projeto
  -add Angular routing? - escolha Yes
  -stylesheet formar - ecolha SCSS.

- Para rodar/execultar uma aplicação Angular use o comando: ng serve

- Angular é composta basicamente de 3 coisas:
  - o template = arquivo html.

  - a classe = que vai servir como controlador da minha página(métodos, eventos e afins).

  - os estilos = arquivo css.

```
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.scss']
})
export class AppComponent {
  title = 'fundamentos-angular';
}
```

## Criando componentes "na mão"

- Dentro da pasta app, crie uma pasta com o nome meu-componente e dentro dela um arquivo TS(sempre usar o prefixo ".component"
depois do nome do componente que você criou, meu-componente.component.ts, um component vai ser um classe basicamente.

- Dentro do arquivo meu-componente.component.ts crie seu compoonente:

```
import { Component } from "@angular/core";


@Component({
  selector: "app-meu-componente", //sempre usar o prefixo "app-" na frente do nome do componente
  templateUrl: "./meu-componente.component.html",// url do arquivo html,você pode passar direto a tag par ao componente tbm.
  styleUrls: ['./meu-componente.component.scss']// urls do arquivo css
})

export class MeuComponenteComponent {

}
```

- crie dentro da pasta meu-componente os respectivos arquivos html e scss.

- acrecente o componente a aplicação no arquivo app.modules.ts:

```
@NgModule({
  declarations: [
    AppComponent,
    MeuComponenteComponent <----------------------------
  ],
  imports: [
    BrowserModule,
    AppRoutingModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
```

- Para mostra o componente que você criou vá no arquivo app.component.html e adicione a tag do seu componente, não esqueça
de adicionar o o prefixo "app-" :

```
<app-meu-componente></app-meu-componente>
```

-Criando componente automaticamente na linha de comando: ``ng generate component segundo-componente``

- Criando pela linha de comando ele já acrecenta o componente a aplicação no arquivo app.modules.ts


# Usando interpolação de texto e pipe "|" para formatar textos dentro de uma tag HTML

- Arquivo nome-componente.component.html:

```
<!-- Usando interpolação de texto e pipe "|" para formatar texto -->
<p>{{ nome | uppercase}}</p>
```

- Arquivo nome-componente.component.ts:

```
export class SegundoComponenteComponent implements OnInit {
nome: string = "Jhonny Alves de Souza Azevedo"; <---------------------- declare a propriedade

  constructor() { }

  ngOnInit(): void {
  }

}
```

- Você pode consultar todos os pipes do Angular na [documentação:](angular.io/guide/pipes)


## Criando um Pipe seu, personalizado

- crie um pipe usando o comando no cmd: ``ng g pipe nomeMeuPipe``

- ex: ``ng g pipe multiplicaPor``

-o arquivo multiplica-por.pipe.ts é criado e já é adicionado em app.modules.ts:

```
@NgModule({
  declarations: [
    AppComponent,
    MeuComponenteComponent,
    SegundoComponenteComponent,
    MultiplicaPorPipe <-----------------------------
})
```

- no arquivo multiplica-por.pipe.ts crie o seu pipe:

```
import { Pipe, PipeTransform } from '@angular/core';

@Pipe({
  name: 'multiplicaPor' <------------- como irei chamar meu pipe no html do componente
})
export class MultiplicaPorPipe implements PipeTransform {

  transform(valor: number, multiplicador: number): unknown { <------------ parêmetro e argumetos personalizados
    return valor * multiplicador; <------------------------
  }

}
```

- no componente que queira usar o seu pipe personalizado faça da seguinte forma no html:

```
<h2>Pipe customizado Multiplica Por um valor</h2>
<p>Valor=  {{ 2 | multiplicaPor:3 }}</p> <---------------------------
```




_Continuar Aula 4.D























































