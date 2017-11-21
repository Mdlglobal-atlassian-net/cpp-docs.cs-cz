---
title: "Kompilátoru (úroveň 4) upozornění C4234 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4234
dev_langs: C++
helpviewer_keywords: C4234
ms.assetid: f7fecd5c-8248-4fde-8446-502aedc357ca
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 86a44dfc09e3b0bcb0744115ce4ddfaf8d96f258
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4234"></a>C4234 kompilátoru upozornění (úroveň 4)
nestandardní rozšíření používané: vyhrazeno pro budoucí použití – klíčové slovo '– klíčové slovo'  
  
 Kompilátor ještě neimplementuje klíčové slovo, které jste použili.  
  
 Toto upozornění je automaticky povýšen na chybu. Pokud chcete-li toto chování změnit, použijte [#pragma – upozornění](../../preprocessor/warning.md). Třeba, aby C4234 do problémem upozornění úroveň 4  
  
```  
#pragma warning(2:4234)  
```  
  
 ve zdrojovém kódu souboru.