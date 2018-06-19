---
title: C2868 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2868
dev_langs:
- C++
helpviewer_keywords:
- C2868
ms.assetid: 6ff5837b-e66d-44d1-9d17-80af35e08d08
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 84465453ca7a1d76a9dd6b199232384c2ef9124b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33244362"
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