---
title: C4439 upozornění kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4439
dev_langs:
- C++
helpviewer_keywords:
- C4439
ms.assetid: 9449958f-f407-4824-829b-9e092f2af97d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4767f03d51bf1fcaac51678d17d454949eb30875
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33286952"
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