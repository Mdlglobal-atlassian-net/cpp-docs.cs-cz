---
title: Typy SBCS a MBCS dat | Microsoft Docs
ms.custom: ''
ms.date: 04/11/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- MBCS
- SBCS
dev_langs:
- C++
helpviewer_keywords:
- SBCS and MBCS data types
- data types [C], MBCS and SBCS
ms.assetid: 4c3ef9da-e397-48d4-800e-49dba36db171
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ccdec81251589ba36209f878f1fa8b727d7d2b98
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409274"
---
# <a name="sbcs-and-mbcs-data-types"></a>Datové typy SBCS a MBCS

Všechny rutiny běhové knihovny Microsoft MBCS, která zpracovává jenom jeden vícebajtových znaků nebo jeden bajt vícebajtových znaků očekává `unsigned int` argument (kde 0x00 < = hodnota znaku < = 0xFFFF a 0x00 < = hodnota bajtu < = 0xFF). Rutiny MBCS, která zpracovává vícebajtové bajtů nebo znaků v kontextu řetězec očekává řetězec vícebajtových znaků tak, aby být reprezentován jako `unsigned char` ukazatel.

> [!CAUTION]
> Každý bajt vícebajtových znaků, které mohou být v 8-bit reprezentována **char**. Ale jednobajtové znak SBCS nebo MBCS typu **char** s hodnotou vyšší než 0x7F je záporná. Když se takový znak přímo na převést **int** nebo **dlouho**, výsledek je rozšířeny kompilátorem a proto přispět neočekávané výsledky.

Proto je nejlepší představují bajt vícebajtových znaků jako 8-bit `unsigned char`. Nebo, abyste se vyhnuli záporný výsledek, jednoduše převést znakovou typu **char** k `unsigned char` před jeho převodem **int** nebo **dlouho**.

Protože některé SBCS zpracování řetězců funkce proveďte (se znaménkem) **char\***  upozornění o neshodě typů parametrů, dojde při **_MBCS** je definována. Abyste tomu předešli, upozornění, uvedené v pořadí podle efektivitu třemi způsoby:

1. Použijte v Tchar – bezpečnost typů vložených funkcí. H. Toto je výchozí chování.

1. Použitím přímého makra v Tchar –. H definováním **_MB_MAP_DIRECT** na příkazovém řádku. Pokud to uděláte, musíte ručně spárovat typy. To je nejrychlejší způsob, ale není bezpečnost typů.

1. Pomocí funkce zajišťující bezpečnost typů staticky propojené knihovny v Tchar –. H. Uděláte to tak, definujte konstantu **_NO_INLINING** na příkazovém řádku. Toto je metoda nejpomalejší, ale nejvíce bezpečnost typů.

## <a name="see-also"></a>Viz také

[Internacionalizace](../c-runtime-library/internationalization.md)<br/>
[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
