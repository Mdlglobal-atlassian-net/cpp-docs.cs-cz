---
title: "Kompilátoru (úroveň 1) upozornění C4288 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4288
dev_langs: C++
helpviewer_keywords: C4288
ms.assetid: 6aaeb139-90cd-457a-9d37-65687042736f
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: abbc9ba0a41a4961c49cffca6c10ff9a4e4e1437
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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