---
title: Závažná chyba kompilátoru prostředků RC1120 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC1120
dev_langs:
- C++
helpviewer_keywords:
- RC1120
ms.assetid: 4e462931-e42e-42e3-8bfc-847677194286
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 62f28e381d4eac0bfd1f010ef3919452635a1b96
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056999"
---
# <a name="resource-compiler-fatal-error-rc1120"></a>Závažná chyba kompilátoru prostředků RC1120

Nedostatek paměti třeba počet bajtů

Nástroj Resource Compiler nemá dostatek úložiště pro položky, které je uložený v jeho haldy. Obvykle to je výsledkem by bylo příliš mnoho symbolů.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li vyřešit pomocí následujících možná řešení

1. Zvětšete místo odkládacího souboru Windows. Další informace o zvětšení místa odkládacího souboru naleznete v tématu virtuální paměti v nápovědě k Windows.

1. Odstraňte nepotřebné vkládané soubory, zejména nepotřebné `#define`prototypy s a funkce.

1. Rozdělit do dvou nebo více souborů aktuální soubor a zkompilovat je samostatně.

1. Odeberte ostatní programy a ovladače spuštěné v systému, který může spotřebovávat značné množství paměti.