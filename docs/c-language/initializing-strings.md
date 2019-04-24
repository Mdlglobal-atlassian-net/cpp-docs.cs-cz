---
title: Inicializace řetězců
ms.date: 11/04/2016
helpviewer_keywords:
- character arrays, initializing
- strings [C++], initializing
- initializing arrays, strings
ms.assetid: 0ab8079d-d0d3-48f9-afd1-36a7bb439b29
ms.openlocfilehash: c9dbad72314e9ce01d022d26209e2132c29c106a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325998"
---
# <a name="initializing-strings"></a>Inicializace řetězců

Pole znaků (nebo širokých znaků) lze inicializovat textovým literálem (nebo širokým textovým literálem). Příklad:

```
char code[ ] = "abc";
```

inicializuje pole `code` jako pole znaků o čtyřech prvcích. Čtvrtý prvek je znak Null, který ukončuje všechny textové literály.

Seznam identifikátorů může dosahovat maximálně délky počtu identifikátorů, které mají být inicializovány. Zadáte-li velikost pole menší než řetězec, jsou přesahující znaky ignorovány. Například následující deklarace inicializuje pole `code` jako pole znaků o třech prvcích:

```
char code[3] = "abcd";
```

Do pole `code` jsou přiřazeny pouze první tři znaky inicializátoru. Znak `d` a znak Null ukončující řetězec jsou ignorovány. Tím dojde k vytvoření neukončeného řetězce (tedy řetězce bez hodnoty 0 označující jeho konec) a k vygenerování diagnostické zprávy, která tuto situaci oznamuje.

Deklarace

```
char s[] = "abc", t[3] = "abc";
```

je shodná s

```
char s[]  = {'a', 'b', 'c', '\0'},
     t[3] = {'a', 'b', 'c' };
```

Je-li řetězec kratší než zadaná velikost pole, jsou zbývající prvky pole inicializovány na hodnotu 0.

**Microsoft Specific**

V jazyce Microsoft C mohou být textové literály dlouhé až 2048 bajtů.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Inicializace](../c-language/initialization.md)
