---
title: "C3628 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3628
dev_langs:
- C++
helpviewer_keywords:
- C3628
ms.assetid: 0ff5a4a4-fcc9-47a0-a4d8-8af9cf2815f6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 16e2e2a83cc5dbf52e7030e10d00c3cdfe7891d8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3628"></a>C3628 chyby kompilátoru
'základní třída': spravované nebo WinRTclasses podporují pouze veřejné dědičnosti  
  
Byl proveden pokus o použití spravované nebo WinRT třídy [privátní](../../cpp/private-cpp.md) nebo [chráněné](../../cpp/protected-cpp.md) základní třídy. Spravovat A nebo WinRT třídu lze použít pouze jako základní třída s [veřejné](../../cpp/public-cpp.md) přístup.  
  
Následující ukázka generuje C3628 a ukazuje, jak to opravit:  
  
```  
// C3628a.cpp  
// compile with: /clr  
ref class B {  
};  
  
ref class D : private B {   // C3628  
  
// The following line resolves the error.  
// ref class D : public B {  
};  
  
int main() {  
}  
```  
