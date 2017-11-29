---
title: "C2382 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2382
dev_langs: C++
helpviewer_keywords: C2382
ms.assetid: 4d4436f9-d0d6-4bd0-b8ec-767b89adfb2f
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 086a0675e877360d424346edfd2b32ea558514aa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2382"></a>C2382 chyby kompilátoru
'function': předefinování; Specifikace různých výjimek  
  
 V části [/Za](../../build/reference/za-ze-disable-language-extensions.md), tato chyba označuje, že došlo k pokusu přetížení funkce o pouze na [specifikace výjimek](../../cpp/exception-specifications-throw-cpp.md).  
  
 Následující ukázka generuje C2382:  
  
```  
// C2382.cpp  
// compile with: /Za /c  
void f1(void) throw(int) {}  
void f1(void) throw(char) {}   // C2382  
void f2(void) throw(char) {}   // OK  
```