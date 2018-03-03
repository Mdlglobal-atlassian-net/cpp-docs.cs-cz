---
title: "Upozornění linkerů Lnk4102 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4102
dev_langs:
- C++
helpviewer_keywords:
- LNK4102
ms.assetid: bfd1b17e-05c7-4bc2-80d6-2888b1a425b2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 80efad60da9f6742110811a5cf4c12f07c7def67
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4102"></a>Upozornění linkerů LNK4102
Export odstranění destruktor 'name'; bitová kopie nemusí správně fungovat.  
  
 Program se pokusil exportovat odstraňování destruktor. Výsledný odstranění může dojít přes hranice knihovny DLL tak, aby tento proces se může uvolnit paměť, která není vlastníkem. Ujistěte se, zda daný symbol není uveden v souboru .def a zda je symbol není uvedena jako argument **nebo IMPORTU** nebo **/EXPORT** možnost v příkazovém řádku linkeru.  
  
 Pokud se znovu sestavit běhové knihovny jazyka C, můžete tuto zprávu ignorovat.