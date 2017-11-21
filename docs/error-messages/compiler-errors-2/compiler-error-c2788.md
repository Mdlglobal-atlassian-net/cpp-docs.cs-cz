---
title: "C2788 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2788
dev_langs: C++
helpviewer_keywords: C2788
ms.assetid: 8688fc5c-e652-43b4-b407-9c488c76f2db
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b3d66496da2940a08d87f968678125b5836587ac
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2788"></a>C2788 chyby kompilátoru
"identifikátor": více než jeden identifikátor GUID přidružené k tomuto objektu  
  
 [__Uuidof –](../../cpp/uuidof-operator.md) operátor má uživatelsky definovaný typ. s identifikátorem GUID připojen nebo objekt takového typu uživatelem definované. K této chybě dojde, když je objekt s více identifikátorů GUID.  
  
 Následující ukázka generuje C2788:  
  
```  
// C2788.cpp  
#include <windows.h>  
struct __declspec(uuid("00000001-0000-0000-0000-000000000000")) A {};  
struct __declspec(uuid("{00000002-0000-0000-0000-000000000000}")) B {};  
template <class T, class U> class MyClass {};  
  
typedef MyClass<A,B> MyBadClass;  
typedef MyClass<A,A> MyGoodClass;  
  
int main() {  
   __uuidof(MyBadClass);    // C2788  
   // try the following line instead  
   __uuidof(MyGoodClass);  
}  
```