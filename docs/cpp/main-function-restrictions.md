---
title: "Main – omezení funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Main
dev_langs: C++
helpviewer_keywords: main function, restrictions on using
ms.assetid: 7b3df731-344b-44a8-850c-11cbcbfbfa83
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c444fe53719aea5c78477aa9d9f35134c44d99a9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="main-function-restrictions"></a>main – omezení funkce
Několik omezení se vztahují na **hlavní** funkce, která se nevztahují na jiných funkcí jazyka C++. **Hlavní** funkce:  
  
-   Nemohou být přetíženy (viz [přetížení funkcí](function-overloading.md)).  
  
-   Nelze deklarovat jako **vložené**.  
  
-   Nelze deklarovat jako **statické**.  
  
-   Nelze zabrat její adresu.  
  
-   Nelze ji volat.  
  
## <a name="see-also"></a>Viz také  
 [hlavní: spuštění programu](../cpp/main-program-startup.md)