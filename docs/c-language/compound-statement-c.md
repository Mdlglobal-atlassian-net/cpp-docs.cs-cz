---
title: Složený příkaz (C)
ms.date: 11/04/2016
helpviewer_keywords:
- compound statements
- statements, compound
ms.assetid: 32d1bf86-cbbc-42a9-ba3a-1be1c6c7754c
ms.openlocfilehash: 42d4c1d21c3e98dfc0281a47a35e033852f8de18
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62312560"
---
# <a name="compound-statement-c"></a>Složený příkaz (C)

Složený příkaz (označovaný také jako "Block") se obvykle zobrazuje jako tělo jiného příkazu, jako je například příkaz **if** . [Deklarace a typy](../c-language/declarations-and-types.md) popisují formu a význam deklarací, které se mohou objevit na začátku složeného příkazu.

## <a name="syntax"></a>Syntaxe

*složený příkaz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *deklarace-seznam*příkazů<sub>opt</sub> *-list*<sub>opt</sub> **}**

*seznam deklarací*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*změny*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;deklarace *seznamu deklarací* *declaration*

*seznam příkazů*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*vydá*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;příkaz *-list –* *příkaz*

Pokud existují deklarace, musí být před všemi příkazy. Rozsah každého identifikátoru deklarovaného na začátku složeného příkazu se rozšíří z jeho bodu deklarace na konec bloku. Je viditelný v rámci bloku, pokud v vnitřním bloku neexistuje deklarace stejného identifikátoru.

Identifikátory v složeném příkazu jsou považovány za **Automatické** , pokud nejsou explicitně deklarovány jinak s **Registry**, **static**nebo `extern`, s výjimkou funkcí `extern`, které mohou být pouze. Můžete ponechat `extern` specifikátor v deklaracích funkcí a funkce bude i nadále `extern`.

Úložiště není přidělené a inicializace není povolená, pokud je v složeném příkazu s třídou `extern`úložiště deklarovaná proměnná nebo funkce. Deklarace odkazuje na externí proměnnou nebo funkci definovanou jinde.

Proměnné deklarované v bloku s klíčovým slovem **auto** nebo **Register** jsou znovu přiděleny a v případě potřeby inicializovány při každém zadání složeného příkazu. Tyto proměnné nejsou definovány po ukončení složeného příkazu. Pokud Proměnná deklarovaná uvnitř bloku má **statický** atribut, je proměnná inicializována při zahájení provádění programu a udržuje její hodnotu v celém programu. Informace o **statických**třídách naleznete v tématu [třídy úložiště](../c-language/c-storage-classes.md) .

Tento příklad znázorňuje složený příkaz:

```
if ( i > 0 )
{
    line[i] = x;
    x++;
    i--;
}
```

V tomto příkladu, pokud `i` je větší než 0, všechny příkazy uvnitř složeného příkazu jsou spouštěny v pořadí.

## <a name="see-also"></a>Viz také

[Příkazy](../c-language/statements-c.md)
