---
title: "C2775 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2775
dev_langs: C++
helpviewer_keywords: C2775
ms.assetid: 9c488508-ade0-48f1-b94f-d538d15f807a
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 77462b90a0e24084426a8186912631cf6a323cb9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2775"></a>C2775 chyby kompilátoru
"identifikátor": žádná metoda "get" souvisí s touto vlastností  
  
 Datový člen deklarovat s [vlastnost](../../cpp/property-cpp.md) rozšířené atribut nemá `get` funkce zadaný, ale výraz se pokusí načíst jeho hodnotu.  
  
 Následující ukázka generuje C2775:  
  
```  
// C2775.cpp  
struct A {  
   __declspec(property(put=PutProp2, get=GetProp2)) int prop2;  
   int GetProp2(){return 0;}  
   void PutProp2(int){}  
  
   __declspec(property(put=PutProp)) int prop;  
   int PutProp(void){}  
  
};  
  
int main() {  
   A* pa = new A;  
   int x;  
   x = pa->prop;   // C2775  
   x = pa->prop2;  
}  
```