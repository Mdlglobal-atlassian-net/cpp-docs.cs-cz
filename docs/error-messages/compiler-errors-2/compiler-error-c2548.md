---
title: "C2548 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2548
dev_langs: C++
helpviewer_keywords: C2548
ms.assetid: 01e9c835-9bf3-4020-9295-5ee448c519f3
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f05c036e7f7f5d78f2ca5a9acaa231ba3485d464
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2548"></a>C2548 chyby kompilátoru
'class::member': Chybějící výchozí parametr pro parametr parametr  
  
 Seznam výchozích parametrů chybí parametr. Pokud zadáte parametr výchozí kdekoli v seznamu parametrů, je nutné zadat výchozí parametry pro všechny následné parametry.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2548:  
  
```  
// C2548.cpp  
// compile with: /c  
void func( int = 1, int, int = 3);  // C2548  
  
// OK  
void func2( int, int, int = 3);  
void func3( int, int = 2, int = 3);  
```