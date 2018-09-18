---
title: C deklarace a definice | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 575f0c9b-5554-4346-be64-b2129ca9227f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7fcb83395313609fc5c9bad673416131b2332552
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019559"
---
# <a name="c-declarations-and-definitions"></a>Deklarace a definice jazyka C

„Deklarace“ vytvoří přidružení mezi určitou proměnnou, funkcí nebo typem a jejich atributy. [Přehled deklarací](../c-language/overview-of-declarations.md) poskytuje syntaxi standardu ANSI pro `declaration` neterminálu. Deklarace také určuje, kdy a kde lze k identifikátoru přistupovat („propojení“ identifikátoru). Zobrazit [životnost, rozsah, viditelnost a propojení](../c-language/lifetime-scope-visibility-and-linkage.md) Další informace o propojení.

„Definice“ proměnné vytváří stejné přidružení jako deklarace, ale také způsobí přiřazení úložiště proměnné.

Například funkce `main`, `find` a `count` a proměnné `var` a `val` jsou definovány v jednom zdrojovém souboru v tomto pořadí:

```
int main() {}

int var = 0;
double val[MAXVAL];
char find( fileptr ) {}
int count( double f ) {}
```

Proměnné `var` a `val` lze použít ve funkcích `find` a `count` a nejsou požadovány žádné další deklarace. Ale tyto názvy nejsou ve funkci `main` viditelné (přístupné).

## <a name="see-also"></a>Viz také

[Zdrojové soubory a zdrojové programy](../c-language/source-files-and-source-programs.md)