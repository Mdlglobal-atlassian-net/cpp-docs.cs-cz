---
title: "C2488 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2488
dev_langs: C++
helpviewer_keywords: C2488
ms.assetid: cd435909-43e4-43c6-a57c-5d02468ef75f
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0dc6ac6ae2c7830ad11a95dceb6e3101cf662c38
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2488"></a>C2488 chyby kompilátoru
"identifikátor": "holé" lze použít pouze pro definice funkcí nejsou členy  
  
 [Holé](../../cpp/naked-cpp.md) atribut bylo použito pro deklaraci funkce.  
  
 Následující ukázka generuje C2488:  
  
```  
// C2488.cpp  
// compile with: /c  
// processor: x86  
__declspec( naked ) void func();   // C2488  declaration, not definition  
__declspec( naked ) void i;   // C2488  i is not a function  
  
__declspec( naked ) void func() {}   // OK  
```