---
title: "C4439 upozornění kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4439
dev_langs:
- C++
helpviewer_keywords:
- C4439
ms.assetid: 9449958f-f407-4824-829b-9e092f2af97d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 150690bc5d2778945eec95c8576b2cc57050bbe8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-c4439"></a>C4439 upozornění kompilátoru
'function': definice funkce spravovaného typu v podpisu musí mít __clrcall konvenci volání  
  
 Kompilátor implicitně nahradit konvence volání s [__clrcall](../../cpp/clrcall.md). Chcete-li toto upozornění vyřešit, odeberte `__cdecl` nebo `__stdcall` konvence volání.  
  
 C4439 je vždy vydané jako chyba. Toto upozornění se můžete vypnout `#pragma warning` nebo **/wd**; najdete v části [upozornění](../../preprocessor/warning.md) nebo [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, nebo jsme /wo, /Wv, wdn (úroveň upozornění)](../../build/reference/compiler-option-warning-level.md)Další informace.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4439.  
  
```  
// C4439.cpp  
// compile with: /clr  
void __stdcall f( System::String^ arg ) {}   // C4439  
void __clrcall f2( System::String^ arg ) {}   // OK  
void f3( System::String^ arg ) {}   // OK  
```