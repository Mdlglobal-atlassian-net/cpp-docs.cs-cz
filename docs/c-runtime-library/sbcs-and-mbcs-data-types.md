---
title: Datové typy SBCS a MBCS
ms.date: 04/11/2018
f1_keywords:
- MBCS
- SBCS
helpviewer_keywords:
- SBCS and MBCS data types
- data types [C], MBCS and SBCS
ms.assetid: 4c3ef9da-e397-48d4-800e-49dba36db171
ms.openlocfilehash: 9f45d888e10ad1f86d0ba395155c7fd5c6c1bf0f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50633451"
---
# <a name="sbcs-and-mbcs-data-types"></a>Datové typy SBCS a MBCS

Všechny rutiny knihovny run-time Microsoft MBCS, která zpracovává jenom jeden vícebajtový znak nebo jeden bajt vícebajtového znaku očekává, že `unsigned int` argument (kde 0x00 < = hodnota znaku < = 0xFFFF a 0x00 < = bajtovou hodnotou < = 0xFF). Rutiny znakové sady MBCS, která zpracovává vícebajtové bajtů nebo znaků v kontextu řetězec vícebajtového znakového řetězce, aby se dala vyjádřit jako očekává, že `unsigned char` ukazatele.

> [!CAUTION]
> Každý bajt vícebajtového znaku je možné znázornit na 8-bit **char**. Ale jednobajtový znak SBCS nebo MBCS typu **char** s hodnotou větší než 0x7F jsou negativní. Pokud takový znak je převeden přímo do **int** nebo **dlouhé**, výsledek je rozšířen o znaménko kompilátorem a proto může vést k neočekávaným výsledkům.

Proto je nejvhodnější pro reprezentaci bajt vícebajtového znaku jako 8-bit `unsigned char`. Nebo se pokud chcete vyhnout záporný výsledek, jednoduše převést jednobajtový znak typu **char** do `unsigned char` před převodem na **int** nebo **dlouhé**.

Protože některé SBCS zpracování řetězců funkce vzít (se znaménkem) **char** <strong>\*</strong> parametry, způsobí upozornění kompilátoru Neshoda typů při **_MBCS** je definice. Abyste tomu předešli, upozornění, uvedeny v pořadí podle efektivitu třemi způsoby:

1. Funkce TCHAR vložené typově bezpečný. H. Toto je výchozí chování.

1. Pomocí přímého makra v TCHAR. H definováním **_MB_MAP_DIRECT** na příkazovém řádku. Pokud to uděláte, musíte ručně odpovídají typům. Toto je nejrychlejší způsob, ale není typově bezpečný.

1. Funkce TCHAR staticky propojené knihovny typově bezpečné. H. Uděláte to tak, definujte konstantu **_NO_INLINING** na příkazovém řádku. Toto je metoda nejpomalejší ale nejvíce typově bezpečné.

## <a name="see-also"></a>Viz také

[Internacionalizace](../c-runtime-library/internationalization.md)<br/>
[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
