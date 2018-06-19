---
title: 'Postupy: deklarace přídavných ukazatelů a typů hodnot | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- value types, declaring
- pinning pointers
ms.assetid: 57c5ec8a-f85a-48c4-ba8b-a81268bcede0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 40187b7da9083ddaa5342e4bdfeba556fb900e7b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880381"
---
# <a name="how-to-declare-pinning-pointers-and-value-types"></a>Postupy: Deklarace přídavných ukazatelů a typů hodnot
Typ hodnoty mohou být implicitně do pole. Potom můžete deklarovat Připnutí ukazatel na objekt typu hodnota samostatně a použití **pin_ptr** zabalené hodnoty typu.  
  
## <a name="example"></a>Příklad  
  
### <a name="code"></a>Kód  
  
```  
// pin_ptr_value.cpp  
// compile with: /clr  
value struct V {  
   int i;  
};  
  
int main() {  
   V ^ v = gcnew V;   // imnplicit boxing  
   v->i=8;  
   System::Console::WriteLine(v->i);  
   pin_ptr<V> mv = &*v;  
   mv->i = 7;  
   System::Console::WriteLine(v->i);  
   System::Console::WriteLine(mv->i);  
}  
```  
  
### <a name="output"></a>Výstup  
  
```  
8  
7  
7  
```  
  
## <a name="see-also"></a>Viz také  
 [pin_ptr (C++/CLI)](../windows/pin-ptr-cpp-cli.md)