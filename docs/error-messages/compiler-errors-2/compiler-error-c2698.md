---
title: C2698 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2698
dev_langs:
- C++
helpviewer_keywords:
- C2698
ms.assetid: 3ebfe395-c20b-4c56-9980-ca9ed8653382
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7c466e39702f1e408ad96d79c16c4a5953fa373f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33233814"
---
# <a name="compiler-error-c2698"></a>C2698 chyby kompilátoru
pomocí deklaraci pro ' Deklarace 1 nemohou existovat společně s existující pomocí deklaraci pro ' deklarace 2'  
  
 Jakmile máte [using – deklarace](../../cpp/using-declaration.md) pro člena dat všech pomocí deklarace ve stejném oboru, který používá stejný název není povolená, jak mohou být přetíženy pouze funkce.  
  
 Následující ukázka generuje C2698:  
  
```  
// C2698.cpp  
struct A {  
   int x;  
};  
  
struct B {  
   int x;  
};  
  
struct C : A, B {  
   using A::x;  
   using B::x;   // C2698  
}  
```