---
title: "C3836 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3836
dev_langs: C++
helpviewer_keywords: C3836
ms.assetid: 254f851b-7b7d-4c34-a740-fcf72f6a636a
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 43f7972efc5e8b930811817f5cef9c415a60cb5d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3836"></a>C3836 chyby kompilátoru
Statický konstruktor nemůže mít inicializátoru seznamu členů  
  
 Spravované třídy nemůže mít statický konstruktor, který také obsahuje seznam členů inicializace. Statická třída konstruktory jsou volány modul common language runtime třídy inicializaci členy statických dat inicializace.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3836:  
  
```  
// C3836a.cpp  
// compile with: /clr  
ref class M  
{  
   static int s_i;  
  
public:  
   static M() :  s_i(1234)   // C3836, delete initializer to resolve  
   {  
   }  
};  
  
int main()  
{  
}  
```  
