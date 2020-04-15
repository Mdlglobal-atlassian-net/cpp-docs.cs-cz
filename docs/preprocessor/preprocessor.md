---
title: Preprocesor
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor
ms.assetid: e120eda3-b413-49f1-a07c-e9fb128cf500
ms.openlocfilehash: 7188d7a6803c9eec109a59906cf0c016a460819d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337512"
---
# <a name="preprocessor"></a>Preprocesor

Preprocesor je textový procesor, který pracuje s textem zdrojového souboru v rámci první fáze překladu. Preprocesor neanalyzuje zdrojový text, ale rozdělí jej na tokeny a vyhledá volání maker. Ačkoli kompilátor obvykle vyvolá preprocesor v první fázi, pro zpracování textu bez kompilace lze preprocesor vyvolat také samostatně.

Referenční materiál preprocesoru obsahuje následující oddíly:

- [Direktivy preprocesoru](../preprocessor/preprocessor-directives.md)

- [Preprocesorové operátory](../preprocessor/preprocessor-operators.md)

- [Předdefinovaná makra](../preprocessor/predefined-macros.md)

- [Pragmas](../preprocessor/pragma-directives-and-the-pragma-keyword.md)

**Specifické pro Microsoft**

Můžete získat výpis zdrojového kódu po předběžném zpracování pomocí [/E](../build/reference/e-preprocess-to-stdout.md) nebo [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) kompilátor možnost. Obě možnosti vyvolat preprocesor a odeslat výsledný text do standardního výstupního zařízení, což je ve většině případů konzola. Rozdíl mezi těmito dvěma `#line` možnostmi `/EP` je, že `/E` zahrnuje směrnice a pásy z těchto směrnic.

**END Microsoft Specifické**

## <a name="special-terminology"></a><a name="_predir_special_terminology"></a>Zvláštní terminologie

V dokumentaci preprocesoru odkazuje termín „argument“ na entitu, která je předána funkci. V některých případech je upravena "skutečné" nebo "formální", který popisuje argument výraz zadaný v volání funkce a argument prohlášení zadané v definici funkce, v uvedeném pořadí.

Pojem „proměnná“ představuje jednoduchý datový objekt typu C. Termín "objekt" odkazuje na objekty jazyka C++ i proměnné; Je to inkluzivní termín.

## <a name="see-also"></a>Viz také

[Odkaz na preprocesor C/C++](../preprocessor/c-cpp-preprocessor-reference.md)\
[Fáze překladu](../preprocessor/phases-of-translation.md)
