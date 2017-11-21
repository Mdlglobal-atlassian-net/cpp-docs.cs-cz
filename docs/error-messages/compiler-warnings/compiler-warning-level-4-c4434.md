---
title: "Kompilátoru (úroveň 4) upozornění C4434 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4434
dev_langs: C++
helpviewer_keywords: C4434
ms.assetid: 24b8785e-353a-4c37-8bed-ed61001a871d
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b400ef921cd310cd27b5b4a65867ab7d27255a3c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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