---
title: "C2868 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2868
dev_langs:
- C++
helpviewer_keywords:
- C2868
ms.assetid: 6ff5837b-e66d-44d1-9d17-80af35e08d08
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7255aa3e73e23109535ae0e83d6e9bd907cdbcd4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2868"></a>C2868 chyby kompilátoru  
  
> '*identifikátor*': Neplatná syntaxe pro používání deklaraci; očekávaný kvalifikovaný název  
  
A [pomocí deklarace](../../cpp/using-declaration.md) vyžaduje *kvalifikovaný název*, operátor rozsahu (`::`) oddělený pořadí obor názvů, třídu nebo výčet názvů, který končí název identifikátoru. Operátor řešení jednoho rozsahu lze zavést název z globálního oboru názvů.  
  
## <a name="example"></a>Příklad  
  
Následující ukázka generuje C2868 a také ukazuje správné použití:  
  
```cpp  
// C2868.cpp  
class X {  
public:  
   int i;  
};  
  
class Y : X {  
public:  
   using X::i;   // OK  
};  
  
int main() {  
   using X;   // C2868  
}  
```