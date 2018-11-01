---
title: Kompilátor upozornění (úroveň 4) C4960
ms.date: 11/04/2016
f1_keywords:
- C4960
helpviewer_keywords:
- C4960
ms.assetid: 3b4ed286-9e8d-46f1-af0c-00ba669693a9
ms.openlocfilehash: ff4a9b3d78a108a45abb18c22049b104e630bf15
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516360"
---
# <a name="compiler-warning-level-4-c4960"></a>Kompilátor upozornění (úroveň 4) C4960

'function' je příliš velké, aby se dalo Profilovat.

Při použití [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md), kompilátor zjistil vstupu modulu s funkcí větší než 65 535 pokyny. Velké funkce není k dispozici pro optimalizace řízenou profily.

Pokud chcete vyřešit toto upozornění, zmenšete velikost funkce.