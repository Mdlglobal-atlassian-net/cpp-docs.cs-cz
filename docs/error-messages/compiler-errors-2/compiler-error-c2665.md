---
title: "C2665 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2665
dev_langs: C++
helpviewer_keywords: C2665
ms.assetid: a7f99b61-2eae-4f2b-ba75-ea68fd1e8312
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fdf6737c881df52793e1f59f04a1821a3c788134
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2665"></a>C2665 chyby kompilátoru
'function': Parametr číslo2 žádné přetížení Číslo1 můžete převést z typu "typ"  
  
 Parametr přetížené funkce nelze převést na požadovaný typ.  Možná řešení:  
  
-   Zadejte operátora převodu.  
  
-   Použijte explicitní převod.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2665.  
  
```  
// C2665.cpp  
void func(short, char*){}  
void func(char*, char*){}  
  
int main() {  
   func(0, 1);   // C2665  
   func((short)0, (char*)1);   // OK  
}  
```