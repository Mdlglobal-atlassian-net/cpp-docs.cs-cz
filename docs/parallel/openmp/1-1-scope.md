---
title: 1.1 určení oboru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a8570a3c-1dd6-4c3d-b368-a10fcb3534a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 81babf799860030f6d398f64b55ed65039de8649
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46393527"
---
# <a name="11-scope"></a>1.1 Rozsah

Tato specifikace obsahuje paralelizace pouze uživatel přesměruje, ve které uživatel explicitně určuje akce, které mají být provedeny kompilátorem a za běhu systému, aby bylo možné paralelně spustit program. Implementace OpenMP – C a C++ nejsou nutné k vyhledání závislostí, je v konfliktu, zablokování, časování nebo jiné problémy, jejichž výsledkem nesprávné programu. Uživatel je vaší odpovědností správně spustí aplikaci pomocí konstrukce OpenMP – C a C++ API. Vygenerovaný kompilátorem automatickou paralelizaci a direktivy kompilátoru pomáhat takové paralelizace nejsou zahrnuté v tomto dokumentu.