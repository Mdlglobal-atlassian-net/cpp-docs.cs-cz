---
title: "Upozornění linkerů Lnk4102 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4102
dev_langs: C++
helpviewer_keywords: LNK4102
ms.assetid: bfd1b17e-05c7-4bc2-80d6-2888b1a425b2
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0ac9cbdef0cc094888a2aba2098f1d655a351274
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-warning-lnk4102"></a>Upozornění linkerů LNK4102
Export odstranění destruktor 'name'; bitová kopie nemusí správně fungovat.  
  
 Program se pokusil exportovat odstraňování destruktor. Výsledný odstranění může dojít přes hranice knihovny DLL tak, aby tento proces se může uvolnit paměť, která není vlastníkem. Ujistěte se, zda daný symbol není uveden v souboru .def a zda je symbol není uvedena jako argument **nebo IMPORTU** nebo **/EXPORT** možnost v příkazovém řádku linkeru.  
  
 Pokud se znovu sestavit běhové knihovny jazyka C, můžete tuto zprávu ignorovat.