---
title: Upozornění linkerů LNK4022
ms.date: 11/04/2016
f1_keywords:
- LNK4022
helpviewer_keywords:
- LNK4022
ms.assetid: 890f487e-db98-45dd-a226-c7ccead82b1e
ms.openlocfilehash: 9b9ce09a7133c0bdc18957f6ade213583e9540eb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194184"
---
# <a name="linker-tools-warning-lnk4022"></a>Upozornění linkerů LNK4022

Nejde najít jedinečnou shodu pro symbol symbol.

ODKAZ nebo LIB nalezl více shod pro daný nedekorovaný symbol a nemohl vyřešit nejednoznačnost. Není vytvořen žádný výstupní soubor (. exe,. dll,. exp nebo. lib). Toto upozornění je následováno jedním upozorněním [linkerů LNK4002](../../error-messages/tool-errors/linker-tools-warning-lnk4002.md) pro každý duplicitní symbol a je nakonec následováno závažnou chybou [linkerů LNK1152](../../error-messages/tool-errors/linker-tools-error-lnk1152.md).

Chcete-li zabránit tomuto upozornění, zadejte symbol v upravené podobě. Pokud chcete zobrazit dekorované názvy, spusťte na objektu [DUMPBIN](../../build/reference/dumpbin-options.md) .
