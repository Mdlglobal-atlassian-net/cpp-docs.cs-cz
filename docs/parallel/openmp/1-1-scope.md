---
title: 1.1 obor | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: a8570a3c-1dd6-4c3d-b368-a10fcb3534a6
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 07859a95b739cf649ab6516cb2e8b605efe442dc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="11-scope"></a>1.1 Rozsah
Tato specifikace popisuje paralelizace pouze uživatel přesměruje, ve kterém uživatel explicitně určuje akce, jež mají být přijata kompilátoru a běhu systému provádění programu paralelně. Implementace OpenMP C a C++ nejsou nutné k vyhledání závislosti, je v konfliktu, zablokování, časování nebo jiné problémy, jejichž výsledkem spuštění nesprávný programu. Uživatel je odpovědný za dodržování, správně spouští aplikace pomocí konstrukce OpenMP C a C++ rozhraní API. Generované kompilátorem Automatická paralelizace a direktivy kompilátoru pomůže takové paralelizace nejsou zahrnuté v tomto dokumentu.