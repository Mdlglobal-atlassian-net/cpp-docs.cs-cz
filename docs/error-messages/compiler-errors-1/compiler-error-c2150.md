---
title: C2150 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2150
dev_langs:
- C++
helpviewer_keywords:
- C2150
ms.assetid: 21e82a10-c1d4-4c0d-9dc6-c5d92ea42a31
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7dc7a84ff666fdc17f0abeec690a548f216ce975
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33170145"
---
# <a name="compiler-error-c2150"></a>C2150 chyby kompilátoru
  
> '*identifikátor*': bit pole musí mít typ int, 'podepsaný int' nebo 'unsigned int.  
  
 Základní typ pro bitové pole musí být `int`, `signed int`, nebo `unsigned int`.  
  
## <a name="example"></a>Příklad  
  
 Tento příklad ukazuje, jak můžete setkat C2150 a jak můžete opravit:  
  
```cpp  
// C2150.cpp  
// compile with: /c  
struct A {  
   float a : 8;    // C2150  
   int i : 8;      // OK  
};  
```