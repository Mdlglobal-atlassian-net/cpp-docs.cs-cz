---
title: Kompilátoru (úroveň 1) upozornění C4530 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4530
dev_langs:
- C++
helpviewer_keywords:
- C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 74804aa3ea0450c08710a5d0818eae67ce9b556e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283322"
---
# <a name="compiler-warning-level-1-c4530"></a>C4530 kompilátoru upozornění (úroveň 1)
Obslužná rutina výjimky C++ používá, ale unwind sémantiku nejsou povoleny. Zadejte /EHsc  
  
 Zpracovávání výjimek v jazyce C++ byl použit ale [/EHsc](../../build/reference/eh-exception-handling-model.md) nebyla vybrána.  
  
 Pokud možnost /EHsc nebylo povoleno, nebude objekt s automatické úložiště v rámci mezi funkce provádění throw a funkce zachytávání throw, zničena. Však vytvořen objekt s automatické úložiště v **zkuste** nebo **catch** bloku budou zničena.  
  
 Následující ukázka generuje C4530:  
  
```  
// C4530.cpp  
// compile with: /W1  
int main() {  
   try{} catch(int*) {}   // C4530  
}  
```  
  
 Zkompilujte ukázkový s /EHsc k vyřešení upozornění.