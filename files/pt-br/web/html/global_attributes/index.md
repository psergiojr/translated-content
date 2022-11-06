---
title: Atributos Globais
slug: Web/HTML/Global_attributes
---

{{HTMLSidebar("Global_attributes")}}

**Atributos Globais** são atributos comuns a todos elementos HTML; eles podem ser usados em todos os elementos, embora os atributos não tenham efeito em alguns elementos.

Os atributos globais podem ser especificados em todos os elementos HTML, mesmo aqueles não especificados no padrão. Isso significa que qualquer elemento não padrão ainda deve permitir esses atributos, mesmo que usar esses elementos significa que o documento não é mais compatível com HTML5. Por exemplo, navegadores compatíveis com HTML5 escondem o conteúdo marcado como `<foo hidden>...<foo>`, mesmo que `<foo>` não seja um elemento HTML válido.

Além dos atributos globais HTML básicos, os seguintes atributos globais também existem:

- **`xml:lang`** e **`xml:base`** — Estes são herdados das especificações XHTML e obsoletos, mas mantidos para fins de compatibilidade.
- Os vários atributos **[`aria-*`](/pt-BR/docs/Web/Accessibility/ARIA)**, são utilizados para promover a acessibilidade.
- Os atributos manipuladores de eventos:: **`onabort`**, **`onautocomplete`**, **`onautocompleteerror`**, **`onblur`**, **`oncancel`**, **`oncanplay`**, **`oncanplaythrough`**, **`onchange`**, **`onclick`**, **`onclose`**, **`oncontextmenu`**, **`oncuechange`**, **`ondblclick`**, **`ondrag`**, **`ondragend`**, **`ondragenter`**, **`ondragexit`**, **`ondragleave`**, **`ondragover`**, **`ondragstart`**, **`ondrop`**, **`ondurationchange`**, **`onemptied`**, **`onended`**, **`onerror`**, **`onfocus`**, **`oninput`**, **`oninvalid`**, **`onkeydown`**, **`onkeypress`**, **`onkeyup`**, **`onload`**, **`onloadeddata`**, **`onloadedmetadata`**, **`onloadstart`**, **`onmousedown`**, **`onmouseenter`**, **`onmouseleave`**, **`onmousemove`**, **`onmouseout`**, **`onmouseover`**, **`onmouseup`**, **`onmousewheel`**, **`onpause`**, **`onplay`**, **`onplaying`**, **`onprogress`**, **`onratechange`**, **`onreset`**, **`onresize`**, **`onscroll`**, **`onseeked`**, **`onseeking`**, **`onselect`**, **`onshow`**, **`onsort`**, **`onstalled`**, **`onsubmit`**, **`onsuspend`**, **`ontimeupdate`**, **`ontoggle`**, **`onvolumechange`**, **`onwaiting`**.

## Lista dos Atributos Globais

- [`accesskey`](/pt-BR/docs/Web/HTML/Global_attributes/accesskey)
  - : Fornece uma dica para gerar um atalho de teclado para o elemento atual. Este atributo consiste em uma lista de caracteres separados por espaços. O navegador deve usar o primeiro que existe no layout do teclado do computador.
- [`class`](/pt-BR/docs/Web/HTML/Global_attributes/class)
  - : É uma lista separada por espaço das classes do elemento. as classes permitem ao CSS e ao JavaScript selecionar e acessar elementos específicos atraves dos seletores de classe ou funciona como um método
    {{domxref("Document.getElementsByClassName()")}}.
- [`contenteditable`](/pt-BR/docs/Web/HTML/Global_attributes/contenteditable)

  - : É um atributo enumerado que indica se o elemento deve ser editado pelo usuário. Se assim for, o navegador modifica seu widget para permitir a edição. O atributo deve ter um dos seguintes valores:

    - `true` ou uma string vazia, indica que o elemento deve ser editável;
    - `false`, indica que o elemento não deve ser editável.

- [`contextmenu`](/pt-BR/docs/Web/HTML/Global_attributes/contextmenu)
  - : É o **[`id`](#attr-id)** de um {{HTMLElement("menu")}} para usar como o menu contextual para este elemento.
- [`data-*`](/pt-BR/docs/Web/HTML/Global_attributes/data-*)
  - : Forma uma classe de atributos, denominado de dados personalizados, que permite troca de informações proprietárias entre o [HTML](/pt-BR/docs/Web/HTML) e a sua representação no [DOM](/pt-BR/docs/Glossary/DOM) pode ser usada por scripts. Todos esses dados personalizados estão disponíveis através da interface do elemento {{domxref("HTMLElement")}} em que o atributo está definido. A propriedade {{domxref("HTMLElement.dataset")}} dá acesso a eles.
- [`dir`](/pt-BR/docs/Web/HTML/Global_attributes/dir)

  - : É um atributo enumerado que indica a direcionalidade do texto do elemento. Pode ter os seguintes valores:

    - `ltr`, significa da esquerda para a direita e deve ser usado para idiomas que são escritos da esquerda para a direita (como o português do Brasil, inglês, espanhol, etc);
    - `rtl`, significa da direita para a esquerda e deve ser usado para idiomas que são escritos da direita para a esquerda (como o árabe);
    - `auto`, que permite que o agente do usuário decida. Ele usa um algoritmo básico, pois analisa os caracteres dentro do elemento até encontrar um caractere com uma direcionalidade forte e, em seguida, aplica essa direcionalidade para todo o elemento.

- [`draggable`](/pt-BR/docs/Web/HTML/Global_attributes/draggable) {{experimental_inline}}

  - : É um atributo enumerado que indica se o elemento pode ser arrastado, usando a [API Drag and Drop](/pt-BR/docs/DragDrop/Drag_and_Drop). Pode ter os seguintes valores:

    - `true`, que indica que o elemento pode ser arrastado
    - `false`, que indica que o elemento não pode ser arrastado.

- [`dropzone`](/pt-BR/docs/Web/HTML/Global_attributes/dropzone) {{experimental_inline}}

  - : É um atributo enumerado que indica quais tipos de conteúdo podem ser descartados em um elemento, usando a [API Drag and Drop](/pt-BR/docs/DragDrop/Drag_and_Drop). Pode ter os seguintes valores:

    - `copy`, que indica que o lançamento criará uma cópia do elemento que foi arrastado.
    - `move`, que indica que o elemento que foi arrastado será movido para esta nova localização.
    - `link`, irá criar um link para os dados arrastados.

- [`hidden`](/pt-BR/docs/Web/HTML/Global_attributes/hidden)
  - : Um atributo booleano indica que o elemento ainda não é relevante ou não é mais relevante. Por exemplo, ele pode ser usado para ocultar elementos da página que não podem ser usados até que o processo de login tenha sido concluído. O navegador não renderizará esses elementos. Este atributo não deve ser usado para ocultar conteúdo que possa ser legível.
- [`id`](/pt-BR/docs/Web/HTML/Global_attributes/id)
  - : Define um identificador exclusivo (ID) que deve ser único em todo o documento. Seu objetivo é identificar o elemento ao vincular (usando um identificador de fragmento), um script ou estilo (com CSS).

> **Note:** **Nota:** Os 5 atributos seguintes são partes do [Recursos de Microdados WHATWG HTML](http://www.whatwg.org/specs/web-apps/current-work/multipage/links.html#microdata).

- [`itemid`](/pt-BR/docs/Web/HTML/Global_attributes/itemid) {{experimental_inline}}
  - : O identificador único e global de um item.
- [`itemprop`](/pt-BR/docs/Web/HTML/Global_attributes/itemprop) {{experimental_inline}}
  - : Usado para adicionar propriedades a um item. Cada elemento HTML pode ter um atributo itemprop especificado, onde um itemprop consiste em um par de nomes e valores.
- [`itemref`](/pt-BR/docs/Web/HTML/Global_attributes/itemref) {{experimental_inline}}
  - : As propriedades que não são descendentes de um elemento com o atributo `itemscope` podem ser associadas ao item usando um **itemref**. Itemref fornece uma lista de ids de elementos (não `itemid`) com propriedades adicionais em outro lugar do documento.
- `itemscope` {{experimental_inline}}
  - : Este atributo funciona, em geral, com o atributo [`itemtype`](/pt-BR/docs/Web/HTML/Global_attributes/itemtype) para especificar o HTML dentro de um bloco é sobre um item particular. [`itemscope`](/pt-BR/docs/Web/HTML/Global_attributes/itemscope) cria o item e define o escopo do [`itemtype`](/pt-BR/docs/Web/HTML/Global_attributes/itemtype) associado a ele. [`itemtype`](/pt-BR/docs/Web/HTML/Global_attributes/itemtype) é uma URL válida de um vocabulário (como o [schema.org](http://schema.org/)) que descreve o item e o context de seus atributos.
- [`itemtype`](/pt-BR/docs/Web/HTML/Global_attributes/itemtype) {{experimental_inline}}
  - : Especifica a URL do vocabulário que será usado para definir as propriedades do item na estrutura de dados. [`itemscope`](/pt-BR/docs/Web/HTML/Global_attributes/itemscope) é usado para alterar o escopo na estrutura de dados onde o vocabulário definido por [`itemtype`](/pt-BR/docs/Web/HTML/Global_attributes/itemtype) estará ativo.
- [`lang`](/pt-BR/docs/Web/HTML/Global_attributes/lang)
  - : Participa da definição do idioma do elemento, o idioma no qual os elementos não-editáveis estão escritos, ou o idioma no qual elementos editáveis devem ser escritos. A Tag contém um único valor no formato definido no documento da IEFT [Tags para Identificação de Idiomas (BCP47)](http://www.ietf.org/rfc/bcp/bcp47.txt). [**xml:lang**](#attr-xml:lang) tem prioridade mais alta que [`lang`](/pt-BR/docs/Web/HTML/Global_attributes/lang).
- [`spellcheck`](/pt-BR/docs/Web/HTML/Global_attributes/spellcheck) {{experimental_inline}}

  - : É um atributo enumerado que define se o elemento pode ser verificado por errors de ortografia. Pode ter os seguintes valores:

    - `true`, indica que o elemento deve ser, se possível, verificado por errors ortográficos;
    - `false`, indica que o elemento não deve ser verificado quanto à ortogratia do texto.

- [`style`](/pt-BR/docs/Web/HTML/Global_attributes/style)
  - : Contém regras de declarações [CSS](/pt-BR/docs/) para aplicar no elemento. Note que é recomendado que as regras CSS fiquem num arquivo, ou vários arquivos, separado do HTML. Este atributo e o elemento {{HTMLElement("style")}} tem principalmente o propósito para rápida estilização do elemento, como por exemplo para testes.
- [`tabindex`](/pt-BR/docs/Web/HTML/Global_attributes/tabindex)

  - : É um atributo que recebe valores inteiros e indica se um elemento pode receber o foco de entrada de valores (é focável), se ele deve entrar na sequência da navegação pelo teclado (através da tecla TAB), e qual posição da sequência. Sobre seus valores:

    - um _valor negativo_ indica que o elemento **é focável**, mas **não é alcançável** pela navegação sequencial do teclado (através da tecla TAB);
    - `0` indica que o elemento **é focável** e **alcançavel** pela navegação sequencial do teclado, mas sua ordem de seleção relativa é definida pela convenção da plataforma (ou do navegador);
    - um _valor positivo_ indica que o elemento **é focável** e **alcançável** pela navegação sequencial do teclado; sua ordem de seleção relativa é definida pelo valor colocado: a sequência segue em ordem crescente definida no [`tabindex`](/pt-BR/docs/Web/HTML/Global_attributes/tabindex). Se vários elementos possuem o mesmo valor de [`tabindex`](/pt-BR/docs/Web/HTML/Global_attributes/tabindex), sua ordem relativa é estabelecida pela posição relativa no documento HTML.

- [`title`](/pt-BR/docs/Web/HTML/Global_attributes/title)
  - : Contém um texto representativo sobre a informação relacionada ao elemento ao qual este atributo pertence. Tal informação pode, mas não necessariamente, ser apresentada através de um _tooltip_.
- [`translate`](/pt-BR/docs/Web/HTML/Global_attributes/translate)

  - : É um atributo enumerado, usado para especificar se um atributo de um elemento e os valores dos seus nós descendentes (filhos) {{domxref("Text")}} serão traduzidos quando a página for localizada, ou se não serão alterados. Pode ter os seguintes valores:

    - `yes` ou string vazia: indicam que o elemento será traduzido;
    - `no`: indica que o elemento não será traduzido.

## Especificações

| Especificação                                                                                            | Status                           | Comentário                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| -------------------------------------------------------------------------------------------------------- | -------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| {{SpecName('HTML WHATWG', "dom.html#global-attributes", "Global attributes")}} | {{Spec2('HTML WHATWG')}} | From latest snapshot, {{SpecName('HTML5.1')}}, `itemid`, `itemprop`, `itemref`, `itemscope`, and `itemtype` have been added.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| {{SpecName('HTML5.1', "dom.html#global-attributes", "Global attributes")}}     | {{Spec2('HTML5.1')}}     | Snapshot of {{SpecName('HTML WHATWG')}}. From {{SpecName('HTML5 W3C')}}, `spellcheck`, `draggable`, and `dropzone` have been added.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| {{SpecName('HTML5 W3C', "dom.html#global-attributes", "Global attributes")}}     | {{Spec2('HTML5 W3C')}}     | Snapshot of {{SpecName('HTML WHATWG')}}. From {{SpecName("HTML4.01")}}, the concept of global attributes is introduced and the `dir`, `lang`, `style`, `id`, `class`, `tabindex`, `accesskey`, and `title` are now true global attributes. `xml:lang` which was initially part of XHTML, is now also part of HTML. `hidden`, `data-*`, `contextmenu`, `contenteditable`, and `translate` have been added.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| {{SpecName('HTML4.01')}}                                                                         | {{Spec2('HTML4.01')}}     | There are no global attributes defined. Several attributes that will become global attributes in subsequent specifications are defined on a subset of elements. `class` and `style` are supported on all elements but {{HTMLElement("base")}}, {{HTMLElement("basefont")}}, {{HTMLElement("head")}}, {{HTMLElement("html")}}, {{HTMLElement("meta")}}, {{HTMLElement("param")}}, {{HTMLElement("script")}}, {{HTMLElement("style")}}, and {{HTMLElement("title")}}. `dir` is supported on all elements but {{HTMLElement("applet")}}, {{HTMLElement("base")}}, {{HTMLElement("basefont")}}, {{HTMLElement("bdo")}}, {{HTMLElement("br")}}, {{HTMLElement("frame")}}, {{HTMLElement("frameset")}}, {{HTMLElement("iframe")}}, {{HTMLElement("param")}}, and {{HTMLElement("script")}}. `id` is supported on all elements but {{HTMLElement("base")}}, {{HTMLElement("head")}}, {{HTMLElement("html")}}, {{HTMLElement("meta")}}, {{HTMLElement("script")}}, {{HTMLElement("style")}}, and {{HTMLElement("title")}}. `lang` is supported on all elements but {{HTMLElement("applet")}}, {{HTMLElement("base")}}, {{HTMLElement("basefont")}}, {{HTMLElement("br")}}, {{HTMLElement("frame")}}, {{HTMLElement("frameset")}}, {{HTMLElement("iframe")}}, {{HTMLElement("param")}}, and {{HTMLElement("script")}}. `tabindex` is only supported on {{HTMLElement("a")}}, {{HTMLElement("area")}}, {{HTMLElement("button")}}, {{HTMLElement("object")}}, {{HTMLElement("select")}}, and {{HTMLElement("textarea")}}. `accesskey` is only supported on {{HTMLElement("a")}}, {{HTMLElement("area")}}, {{HTMLElement("button")}}, {{HTMLElement("input")}}, {{HTMLElement("label")}}, {{HTMLElement("legend")}} and {{HTMLElement("textarea")}}. `title` is supported on all elements but {{HTMLElement("base")}}, {{HTMLElement("basefont")}}, {{HTMLElement("head")}}, {{HTMLElement("html")}}, {{HTMLElement("meta")}}, {{HTMLElement("param")}}, {{HTMLElement("script")}}, and {{HTMLElement("title")}}. |

## Compatibilidade com navegadores

{{Compat("html.global_attributes")}}

## Veja também

- {{domxref("Element")}} e {{domxref("GlobalEventHandlers")}} interfaces que permitem acessar a maioria dos atributos globais.