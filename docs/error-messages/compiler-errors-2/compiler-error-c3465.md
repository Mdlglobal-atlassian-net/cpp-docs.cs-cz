---
title: "C3465 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3465
dev_langs: C++
helpviewer_keywords: C3465
ms.assetid: aeb815e5-b3fc-4525-afe2-d738e9321df1
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 716eb175d03cc97389c84b9fa382ac92153071f5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3465"></a>C3465 chyby kompilátoru
Pokud chcete použít typ "typ" musí odkazovat na sestavení 'assembly.  
  
 Předávání typů bude fungovat pro klientskou aplikaci, dokud je překompilovat klienta. Když je překompilovat, budete potřebovat odkaz pro každé sestavení, které obsahuje definici typu, který se používá v klientské aplikace.  
  
 Další informace najdete v tématu [předávání typu (C + +/ CLI)](../../windows/type-forwarding-cpp-cli.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázka vytvoří sestavení, které obsahuje nové umístění typu.  
  
```  
// C3465.cpp  
// compile with: /clr /LD  
public ref class R {  
public:  
   ref class N {};  
};  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří sestavení, který používá pro jiné definice typu, ale teď obsahuje syntaxi předávání pro typ.  
  
```  
// C3465_b.cpp  
// compile with: /clr /LD  
#using "C3465.dll"  
[ assembly:TypeForwardedTo(R::typeid) ];  
```  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3465.  
  
```  
// C3465_c.cpp  
// compile with: /clr  
// C3465 expected  
#using "C3465_b.dll"  
// Uncomment the following line to resolve.  
// #using "C3465.dll"  
  
int main() {  
   R^ r = gcnew R();  
}  
```