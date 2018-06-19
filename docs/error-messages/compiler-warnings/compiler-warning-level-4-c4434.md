---
title: Kompilátoru (úroveň 4) upozornění C4434 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4434
dev_langs:
- C++
helpviewer_keywords:
- C4434
ms.assetid: 24b8785e-353a-4c37-8bed-ed61001a871d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c639fa1cc89266fd9cc2935d88132ceae225a85e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293410"
---
# <a name="compiler-warning-level-4-c4434"></a>C4434 kompilátoru upozornění (úroveň 4)
konstruktoru třídy musí mít privátní usnadnění; Změna privátní přístup  
  
 C4434 označuje, že kompilátor změnila usnadnění statického konstruktoru. Statické konstruktory musí mít privátní usnadnění, jako jsou určeny pouze má být volána modul common language runtime. Další informace najdete v tématu [statické konstruktory](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Static_constructors).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4434.  
  
```  
// C4434.cpp  
// compile with: /W4 /c /clr  
public ref struct R {  
   static R(){}   // C4434  
};  
```