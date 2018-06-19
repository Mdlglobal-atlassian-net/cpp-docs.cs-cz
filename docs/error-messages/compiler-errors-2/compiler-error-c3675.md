---
title: C3675 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3675
dev_langs:
- C++
helpviewer_keywords:
- C3675
ms.assetid: 87461613-6633-430b-b95d-c7cb1bb63776
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1b4aaa53ae1d92364fad143f127ee3e7b504acdd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273641"
---
# <a name="compiler-error-c3675"></a>C3675 chyby kompilátoru
'function': je rezervována, protože je definována 'vlastnost'  
  
 Po deklarování jednoduché vlastnosti kompilátor generuje get a sadu přístupových metod a těch, které se nacházejí v oboru vašeho programu názvy.  Generované kompilátorem názvy jsou tvořeny předřazení get_ a set_ název vlastnosti.  Proto nelze deklarovat funkce se stejným názvem jako přístupové objekty generované kompilátorem.  
  
 V tématu [vlastnost](../../windows/property-cpp-component-extensions.md) Další informace.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3675.  
  
```  
// C3675.cpp  
// compile with: /clr /c  
ref struct C {  
public:  
   property int Size;  
   int get_Size() { return 0; }   // C3675  
};  
```