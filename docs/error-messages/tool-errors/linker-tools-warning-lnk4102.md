---
title: Upozornění linkerů Lnk4102 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4102
dev_langs:
- C++
helpviewer_keywords:
- LNK4102
ms.assetid: bfd1b17e-05c7-4bc2-80d6-2888b1a425b2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 16d13dcbc6d15efd7cf3a7ea0a310de4ab7b0c93
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302643"
---
# <a name="linker-tools-warning-lnk4102"></a>Upozornění linkerů LNK4102
Export odstranění destruktor 'name'; bitová kopie nemusí správně fungovat.  
  
 Program se pokusil exportovat odstraňování destruktor. Výsledný odstranění může dojít přes hranice knihovny DLL tak, aby tento proces se může uvolnit paměť, která není vlastníkem. Ujistěte se, zda daný symbol není uveden v souboru .def a zda je symbol není uvedena jako argument **nebo IMPORTU** nebo **/EXPORT** možnost v příkazovém řádku linkeru.  
  
 Pokud se znovu sestavit běhové knihovny jazyka C, můžete tuto zprávu ignorovat.