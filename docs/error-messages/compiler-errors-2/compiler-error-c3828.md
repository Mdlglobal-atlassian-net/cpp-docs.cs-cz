---
title: C3828 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3828
dev_langs:
- C++
helpviewer_keywords:
- C3828
ms.assetid: 8d9cee75-9504-4bc8-88b6-2413618a3f45
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: adb016c164923e1ac6008e6318e39f8ac8632113
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33267417"
---
# <a name="compiler-error-c3828"></a>C3828 chyby kompilátoru
Typ objektu: umístění argumentů není povolen, vytváření instancí spravované nebo WinRTclasses  
  
 Při vytvoření objektu spravovaného typu nebo typ prostředí Windows Runtime, nemůžete použít umístění formu operátor [nové, gcnew ref](../../windows/ref-new-gcnew-cpp-component-extensions.md) nebo [nové](../../cpp/new-operator-cpp.md).  
  
 Následující ukázka generuje C3828 a ukazuje, jak to opravit:  
  
```  
// C3828a.cpp  
// compile with: /clr  
ref struct M {  
};  
  
ref struct N {  
   static array<char>^ bytes = gcnew array<char>(256);  
};  
  
int main() {  
   M ^m1 = new (&N::bytes) M();   // C3828  
   // The following line fixes the error.  
   // M ^m1 = gcnew M();  
}  
```