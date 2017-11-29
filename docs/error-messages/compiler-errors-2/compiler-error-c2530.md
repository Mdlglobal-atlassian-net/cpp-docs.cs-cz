---
title: "C2530 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2530
dev_langs: C++
helpviewer_keywords: C2530
ms.assetid: b790a312-48df-4a6a-9e27-be2c5f32f16c
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f9438937ad99e66d9e623e1e3703dc6496f8153a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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