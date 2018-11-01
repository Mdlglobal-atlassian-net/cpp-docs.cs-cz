---
title: 1.1 Rozsah
ms.date: 11/04/2016
ms.assetid: a8570a3c-1dd6-4c3d-b368-a10fcb3534a6
ms.openlocfilehash: f87f631ae2d36662daa2ece4790170c00c5cbeb3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449202"
---
# <a name="11-scope"></a>1.1 Rozsah

Tato specifikace obsahuje paralelizace pouze uživatel přesměruje, ve které uživatel explicitně určuje akce, které mají být provedeny kompilátorem a za běhu systému, aby bylo možné paralelně spustit program. Implementace OpenMP – C a C++ nejsou nutné k vyhledání závislostí, je v konfliktu, zablokování, časování nebo jiné problémy, jejichž výsledkem nesprávné programu. Uživatel je vaší odpovědností správně spustí aplikaci pomocí konstrukce OpenMP – C a C++ API. Vygenerovaný kompilátorem automatickou paralelizaci a direktivy kompilátoru pomáhat takové paralelizace nejsou zahrnuté v tomto dokumentu.