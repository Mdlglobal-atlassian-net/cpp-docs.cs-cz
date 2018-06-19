---
title: Kompilátoru (úroveň 1) upozornění C4288 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4288
dev_langs:
- C++
helpviewer_keywords:
- C4288
ms.assetid: 6aaeb139-90cd-457a-9d37-65687042736f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f2c51bdc201b364d76f1692db8ee14973c90923f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33276627"
---
# <a name="compiler-warning-level-1-c4288"></a>C4288 kompilátoru upozornění (úroveň 1)
nestandardní rozšíření používané: 'var': mimo obor cyklu for; se používá proměnná řízení smyčky deklarované v pro – smyčky je v konfliktu s deklaraci ve vnějším oboru  
  
 Při kompilaci s [/Ze](../../build/reference/za-ze-disable-language-extensions.md) a **/Zc:forscope-**, proměnná definovaná v **pro** smyčky byl použit po [pro](../../cpp/for-statement-cpp.md)-cykly oboru. Rozšíření Microsoft pro jazyk C++ umožňuje tato proměnná zůstat v rozsahu, a C4288 upozorní, že první deklarace proměnné nepoužívá.  
  
 V tématu [/Zc:forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) informace o tom, jak zadat příponu do Microsoft **pro** smyčky s /Ze.  
  
 Následující ukázka generuje C4288:  
  
```  
// C4288.cpp  
// compile with: /W1 /c /Zc:forScope-  
int main() {  
   int i = 0;    // not used in this program  
   for (int i = 0 ; ; ) ;  
   i++;   // C4288 using for-loop declaration of i  
}  
```