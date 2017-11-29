---
title: "C3551 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3551
dev_langs: C++
helpviewer_keywords: C3551
ms.assetid: c8ee23da-6568-40db-93a6-3ddb7ac47712
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 450bd97efc9cfbf07eac84a3e6a693af698fc64f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3551"></a>C3551 chyby kompilátoru
"očekává, že že pozdní zadán návratový typ"  
  
 Pokud použijete `auto` – klíčové slovo jako zástupný symbol pro návratový typ funkce, je nutné zadat návratový typ pozdní zadaný. V následujícím příkladu pozdní určených pro návratový typ funkce `myFunction` ukazatel na pole čtyři elementy typu `int`.  
  
```  
auto myFunction()->int(*)[4];   
```  
  
## <a name="see-also"></a>Viz také  
 [automaticky](../../cpp/auto-cpp.md)