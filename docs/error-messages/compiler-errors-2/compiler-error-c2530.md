---
title: C2530 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2530
dev_langs:
- C++
helpviewer_keywords:
- C2530
ms.assetid: b790a312-48df-4a6a-9e27-be2c5f32f16c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9b226ef5ca0e839c745e13d4118264a69ca408db
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2530"></a>C2530 chyby kompilátoru
"identifikátor": odkazy musí být inicializován.  
  
 Odkaz musí inicializovat při bylo deklarováno, pokud je již deklarována:  
  
-   Pomocí klíčového slova [extern](../../cpp/using-extern-to-specify-linkage.md).  
  
-   Jako člena třídy, struktury nebo sjednocení (a je inicializován v konstruktoru).  
  
-   Jako parametr v deklaraci funkce nebo definice.  
  
-   Jako návratový typ funkce.  
  
 Následující ukázka generuje C2530:  
  
```  
// C2530.cpp  
int main() {  
   int i = 0;  
   int &j;   // C2530  
   int &k = i;   // OK  
}  
```