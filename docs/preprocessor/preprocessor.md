---
title: Preprocesor
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor
ms.assetid: e120eda3-b413-49f1-a07c-e9fb128cf500
ms.openlocfilehash: 883504810f1b659e28764a75ebc7cfda325920a5
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222232"
---
# <a name="preprocessor"></a>Preprocesor

Preprocesor je textový procesor, který pracuje s textem zdrojového souboru v rámci první fáze překladu. Preprocesor neanalyzuje zdrojový text, ale provádí jeho rozdělení do tokenů pro hledání volání makra. Ačkoli kompilátor obvykle vyvolá preprocesor v první fázi, pro zpracování textu bez kompilace lze preprocesor vyvolat také samostatně.

Referenční materiál preprocesoru obsahuje následující oddíly:

- [Direktivy preprocesoru](../preprocessor/preprocessor-directives.md)

- [Operátory preprocesoru](../preprocessor/preprocessor-operators.md)

- [Předdefinovaná makra](../preprocessor/predefined-macros.md)

- [Pragmas](../preprocessor/pragma-directives-and-the-pragma-keyword.md)

**Specifické pro společnost Microsoft**

Výpis zdrojového kódu můžete získat po předběžném zpracování pomocí možnosti kompilátoru [/e](../build/reference/e-preprocess-to-stdout.md) nebo [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) . Obě možnosti vyvolávají preprocesor a odesílají výsledný text do standardního výstupního zařízení, které je ve většině případů konzolou. Rozdíl mezi těmito dvěma možnostmi je, `/E` že `#line` zahrnuje direktivy `/EP` a vyříznout tyto direktivy.

**Specifické pro konec Microsoftu**

##  <a name="_predir_special_terminology"></a>Speciální terminologie

V dokumentaci preprocesoru odkazuje termín „argument“ na entitu, která je předána funkci. V některých případech je změněno "skutečnost" nebo "formální", což popisuje výraz argumentu zadaný ve volání funkce a deklaraci argumentu uvedenou v definici funkce v uvedeném pořadí.

Pojem „proměnná“ představuje jednoduchý datový objekt typu C. Pojem "Object" odkazuje na C++ objekty a proměnné; je to celková doba.

## <a name="see-also"></a>Viz také:

[C/C++ reference preprocesoru](../preprocessor/c-cpp-preprocessor-reference.md)\
[Fáze překladu](../preprocessor/phases-of-translation.md)
