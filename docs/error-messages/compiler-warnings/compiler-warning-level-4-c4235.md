---
title: "Kompilátoru (úroveň 4) upozornění C4235 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4235
dev_langs: C++
helpviewer_keywords: C4235
ms.assetid: d4214799-d62c-4674-b4e2-9e201c303303
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b0fea028932a48b9c7ee1a677a3e6dc8078edc35
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4235"></a>C4235 kompilátoru upozornění (úroveň 4)
nestandardní rozšíření používané: nejsou podporovány na této architektuře – klíčové slovo '– klíčové slovo'  
  
 Kompilátor nepodporuje klíčové slovo, které jste použili.  
  
 Toto upozornění je automaticky povýšen na chybu. Pokud chcete-li toto chování změnit, použijte [#pragma – upozornění](../../preprocessor/warning.md). Například aby C4235 do upozornění úroveň 2, použijte následující řádek kódu  
  
```  
#pragma warning(2:4235)  
```  
  
 ve zdrojovém kódu souboru.