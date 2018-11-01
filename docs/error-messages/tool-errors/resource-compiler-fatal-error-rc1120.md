---
title: Závažná chyba kompilátoru prostředků RC1120
ms.date: 11/04/2016
f1_keywords:
- RC1120
helpviewer_keywords:
- RC1120
ms.assetid: 4e462931-e42e-42e3-8bfc-847677194286
ms.openlocfilehash: eff46ddee118c3355e548c73220b407db0561e36
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614919"
---
# <a name="resource-compiler-fatal-error-rc1120"></a>Závažná chyba kompilátoru prostředků RC1120

Nedostatek paměti třeba počet bajtů

Nástroj Resource Compiler nemá dostatek úložiště pro položky, které je uložený v jeho haldy. Obvykle to je výsledkem by bylo příliš mnoho symbolů.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li vyřešit pomocí následujících možná řešení

1. Zvětšete místo odkládacího souboru Windows. Další informace o zvětšení místa odkládacího souboru naleznete v tématu virtuální paměti v nápovědě k Windows.

1. Odstraňte nepotřebné vkládané soubory, zejména nepotřebné `#define`prototypy s a funkce.

1. Rozdělit do dvou nebo více souborů aktuální soubor a zkompilovat je samostatně.

1. Odeberte ostatní programy a ovladače spuštěné v systému, který může spotřebovávat značné množství paměti.