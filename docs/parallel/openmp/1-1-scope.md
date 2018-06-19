---
title: 1.1 obor | Microsoft Docs
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
ms.openlocfilehash: 48d14ec722299a9ff72ad5bab0a68cde5e00d6ad
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686799"
---
# <a name="11-scope"></a>1.1 Rozsah
Tato specifikace popisuje paralelizace pouze uživatel přesměruje, ve kterém uživatel explicitně určuje akce, jež mají být přijata kompilátoru a běhu systému provádění programu paralelně. Implementace OpenMP C a C++ nejsou nutné k vyhledání závislosti, je v konfliktu, zablokování, časování nebo jiné problémy, jejichž výsledkem spuštění nesprávný programu. Uživatel je odpovědný za dodržování, správně spouští aplikace pomocí konstrukce OpenMP C a C++ rozhraní API. Generované kompilátorem Automatická paralelizace a direktivy kompilátoru pomůže takové paralelizace nejsou zahrnuté v tomto dokumentu.