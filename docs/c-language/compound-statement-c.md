---
title: Složené Statement (C) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- compound statements
- statements, compound
ms.assetid: 32d1bf86-cbbc-42a9-ba3a-1be1c6c7754c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e13f09defccb0aeb3d4ec47cf7cf1678deaee6dd
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43767800"
---
# <a name="compound-statement-c"></a>Složený příkaz (C)

Složený příkaz (také nazývané "blok") se obvykle zobrazuje jako text jiného příkazu, jako **Pokud** příkazu. [Deklarace a typy](../c-language/declarations-and-types.md) popisuje formulář opravdu zavřít a význam deklarace, které se mohou objevit v čele složený příkaz.

## <a name="syntax"></a>Syntaxe

*compound-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *seznam deklarací*<sub>optimalizované</sub> *seznamu příkazů*<sub>optimalizované</sub> **}**

*seznam deklarací*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*seznam deklarací* *deklarace*

*seznam příkazů*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*– Příkaz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*seznam příkazů* *– příkaz*

Pokud existují deklarace, musí předcházet všechny příkazy. Obor jednotlivé identifikátory deklarované na začátku složený příkaz sahá od jeho deklarace konec bloku. Je viditelné v rámci bloku deklaraci stejný identifikátor neexistuje ve vnitřním bloku.

Identifikátory v složeného příkazu se předpokládá, že **automaticky** Pokud nejsou explicitně deklarovány jinak s **zaregistrovat**, **statické**, nebo `extern`, s výjimkou funkcí, která může být pouze `extern`. Můžete vynechat `extern` specifikátor v deklaracích funkcí a funkci, bude i nadále `extern`.

Úložiště není přidělená a inicializace není povolena, pokud proměnné nebo funkce je deklarována v složený příkaz pomocí třídy úložiště `extern`. Deklarace odkazuje na externí proměnné nebo funkce definována jinde.

Proměnné deklarované v bloku s **automaticky** nebo **zaregistrovat** – klíčové slovo se a nevyčerpané prostředky se, pokud je potřeba, inicializuje pokaždé, když se zadá složený příkaz. Tyto proměnné nejsou definovány po složený příkaz je ukončen. Pokud je proměnná deklarována uvnitř bloku **statické** atribut, proměnná je inicializována při provádění programu začíná a udržuje její hodnotu v celém programu. Zobrazit [třídy úložiště](../c-language/c-storage-classes.md) informace o **statické**.

Tento příklad ukazuje složený příkaz:

```
if ( i > 0 )
{
    line[i] = x;
    x++;
    i--;
}
```

V tomto příkladu Pokud `i` je větší než 0, všechny příkazy uvnitř složeného příkazu jsou provedeny v pořadí.

## <a name="see-also"></a>Viz také
[Příkazy](../c-language/statements-c.md)