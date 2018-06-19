---
title: C2774 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2774
dev_langs:
- C++
helpviewer_keywords:
- C2774
ms.assetid: 10f428c6-7f49-489a-92ba-6ef978b7caaf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a6fc100bf7cd4a57c5c23630b28c41d92cf43d6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33234951"
---
# <a name="compiler-error-c2774"></a>C2774 chyby kompilátoru
"identifikátor": žádná, put, metoda souvisí s touto vlastností  
  
 Datový člen deklarovat s [vlastnost](../../cpp/property-cpp.md) neobsahuje žádné `put` funkce, ale výraz pokusí nastavení jeho hodnoty.  
  
 Následující ukázka generuje C2774:  
  
```  
// C2774.cpp  
struct A {  
   __declspec(property(get=GetProp)) int prop;  
   int GetProp(void);  
  
   __declspec(property(get=GetProp2, put=PutProp2)) int prop2;  
   int GetProp2(void);  
   void PutProp2(int);  
};  
  
int main() {  
   A* pa = new A;  
   int val = 0;  
   pa->prop = val;   // C2774  
   pa->prop++;   // C2774  
}  
```