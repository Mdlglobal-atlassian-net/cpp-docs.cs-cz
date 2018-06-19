---
title: C2228 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2228
dev_langs:
- C++
helpviewer_keywords:
- C2228
ms.assetid: 901cadb1-ce90-4ae0-a360-547a9ba2ca18
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 969f622877c60bdc340dedf8a2416ac56b2ad0e0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33171022"
---
# <a name="compiler-error-c2228"></a>C2228 chyby kompilátoru
nalevo od '.identifier' musí mít třída, struktura/sjednocení  
  
 Operand nalevo od tečka (.) není třídy, struktury nebo union.  
  
 Následující ukázka generuje C2228:  
  
```  
// C2228.cpp  
int i;  
struct S {  
public:  
    int member;  
} s, *ps = &s;  
  
int main() {  
   i.member = 0;   // C2228 i is not a class type  
   ps.member = 0;  // C2228 ps is a pointer to a structure  
  
   s.member = 0;   // s is a structure type  
   ps->member = 0; // ps points to a structure S  
}  
```  
  
 Tato chyba se zobrazí také při použití spravovaných rozšíření používáte nesprávná syntaxe. Zatímco v dalších jazycích Visual Studio můžete použít operátor tečky o přístup člena třídy spravované, ukazatel na objekt v jazyce C++ znamená, budete muset použít -> – operátor pro přístup k členovi:  
  
 Nesprávný: `String * myString = checkedListBox1->CheckedItems->Item[0].ToString();`  
  
 Práva: `String * myString = checkedListBox1->CheckedItems->Item[0]->ToString();`