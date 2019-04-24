---
title: Kompatibilita se specifikací ANSI C
ms.date: 11/04/2016
f1_keywords:
- Ansi
helpviewer_keywords:
- underscores, leading
- compatibility [C++], ANSI C
- compliance with ANSI C
- conventions [C++], Microsoft extensions
- underscores
- naming conventions [C++], Microsoft library
- ANSI [C++], C standard
- Microsoft extensions naming conventions
ms.assetid: 6be271bf-eecf-491a-a928-0ee2dd60e3b9
ms.openlocfilehash: 7a4462e84ec01bd236849c6aed024b636b315243
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62290427"
---
# <a name="ansi-c-compliance"></a>Kompatibilita se specifikací ANSI C

Zásady vytváření názvů pro všechny identifikátory specifické pro společnost Microsoft v systému za běhu (například funkce, makra, konstant, proměnných a definice typů) kompatibilní se standardem ANSI. V této dokumentaci je uvedeno běhové funkce, která dodržuje standardy ANSI/ISO C jako ANSI kompatibilní. Vyhovující standardu ANSI aplikace by měly používat jenom tyto funkce kompatibilní ANSI.

Názvy funkcí specifických pro společnost Microsoft a globální proměnné začínají s jedním podtržítkem. Tyto názvy lze přepsat pouze místně v rámci oboru svého kódu. Například pokud zahrnete Microsoft za běhu hlavičkové soubory, můžete stále místně přepsat funkce specifické pro společnost Microsoft s názvem `_open` deklarováním místní proměnná se stejným názvem. Tento název globální funkce nebo globální proměnná však nelze použít.

Názvy maker specifické pro společnost Microsoft a konstanty manifestu začínají dvěma podtržítky, nebo jedno vedoucí podtržítko bezprostředně následovat velké písmeno. Rozsah těchto identifikátorů je absolutní. Například nemůžete použít identifikátor specifické pro společnost Microsoft **_UPPER** z tohoto důvodu.

## <a name="see-also"></a>Viz také:

[Kompatibilita](../c-runtime-library/compatibility.md)
