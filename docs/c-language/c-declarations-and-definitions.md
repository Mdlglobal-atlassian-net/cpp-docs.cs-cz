---
title: Deklarace a definice jazyka C
ms.date: 11/04/2016
ms.assetid: 575f0c9b-5554-4346-be64-b2129ca9227f
ms.openlocfilehash: 3be9cd72e9f4dbad4d279cc1bb65dfb92a61cd42
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56150516"
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

## <a name="see-also"></a>Viz také:

[Zdrojové soubory a zdrojové programy](../c-language/source-files-and-source-programs.md)
