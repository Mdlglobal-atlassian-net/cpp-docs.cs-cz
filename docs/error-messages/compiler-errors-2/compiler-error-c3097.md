---
title: "C3097 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3097
dev_langs: C++
helpviewer_keywords: C3097
ms.assetid: b24bd8f8-e04f-4fbb-be57-4feb9165572e
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b71dc70808d1740af51d76ec46bd7af5a4e7d398
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3097"></a>C3097 chyby kompilátoru
'atribut': atribut musí být obor s ' sestavení:' nebo ' modulu:.  
  
 Globální atribut nebyl použit správně.  
  
 Další informace najdete v tématu [uživatelem definované atributy](../../windows/user-defined-attributes-cpp-component-extensions.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3097.  
  
```  
// C3097.cpp  
// compile with: /clr /c  
using namespace System;   
  
[AttributeUsage(AttributeTargets::All, AllowMultiple = true)]  
public ref class Attr : public Attribute {  
public:  
   Attr(int t) : m_t(t) {}  
   int m_t;  
};  
  
[Attr(10)];   // C3097  
[assembly:Attr(10)];   // OK  
  
[Attr(10)]   // OK  
public ref class MyClass {};  
```