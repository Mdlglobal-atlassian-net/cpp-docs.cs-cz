---
title: "C3648 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3648
dev_langs: C++
helpviewer_keywords: C3648
ms.assetid: 5d042989-41cb-4cd0-aa50-976b70146aaf
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5be1886ad2404f0c0eb30cb5511111e4e8e97180
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3648"></a>C3648 chyby kompilátoru
tuto syntaxi explicitní přepsání vyžaduje /clr:oldSyntax  
  
Při kompilování nejnovější spravované syntaxe, kompilátoru nalezen explicitní přepsání syntaxi pro předchozí verze, která již není podporována.  
  
Další informace najdete v tématu [explicitní přepsání](../../windows/explicit-overrides-cpp-component-extensions.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3648:  
  
```  
// C3648.cpp  
// compile with: /clr  
public interface struct I {  
   void f();  
};  
  
public ref struct R : I {  
   virtual void I::f() {}   // C3648  
   // try the following line instead  
   // virtual void f() = I::f{}  
};  
```