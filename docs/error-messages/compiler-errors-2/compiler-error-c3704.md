---
title: C3704 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3704
dev_langs:
- C++
helpviewer_keywords:
- C3704
ms.assetid: ee40ea35-a214-4dec-9489-d7f155dd0ac2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2b3b1f255852def5e04d75751b0a902fb7072545
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33264139"
---
# <a name="compiler-error-c3704"></a>C3704 chyby kompilátoru
'function': metoda vararg nelze vyvolání události  
  
 Jste se pokusili použít [__event](../../cpp/event.md) na vararg metoda. Chcete-li tuto chybu opravit, nahraďte `fireEvent(int i, ...)` volání s `fireEvent(int i)` jak znázorňuje následující ukázka kódu volat.  
  
 Následující ukázka generuje C3704:  
  
```  
// C3704.cpp  
[ event_source(native) ]  
class CEventSrc {  
   public:  
      __event void fireEvent(int i, ...);   // C3704  
      // try the following line instead:  
      // __event void fireEvent(int i);  
};  
  
int main() {  
}  
```