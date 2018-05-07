---
title: Kompilátoru (úroveň 4) upozornění C4235 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4235
dev_langs:
- C++
helpviewer_keywords:
- C4235
ms.assetid: d4214799-d62c-4674-b4e2-9e201c303303
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc63640bc58caefa281b9207b9796ffdf387a7a8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4235"></a>C4235 kompilátoru upozornění (úroveň 4)
nestandardní rozšíření používané: nejsou podporovány na této architektuře – klíčové slovo '– klíčové slovo'  
  
 Kompilátor nepodporuje klíčové slovo, které jste použili.  
  
 Toto upozornění je automaticky povýšen na chybu. Pokud chcete-li toto chování změnit, použijte [#pragma – upozornění](../../preprocessor/warning.md). Například aby C4235 do upozornění úroveň 2, použijte následující řádek kódu  
  
```  
#pragma warning(2:4235)  
```  
  
 ve zdrojovém kódu souboru.