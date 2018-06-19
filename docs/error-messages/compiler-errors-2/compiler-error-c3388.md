---
title: C3388 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3388
dev_langs:
- C++
helpviewer_keywords:
- C3388
ms.assetid: 34336545-ed13-4d81-ab5f-f869799fe4c2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 481096aa870d7e66df032f4d297c652417a7b487
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33256121"
---
# <a name="compiler-error-c3388"></a>C3388 chyby kompilátoru
'type': není povolena jako omezení, za předpokladu, že 'ref class'. Chcete-li pokračovat, analýza  
  
 Omezení byl zadán pro obecný typ, ale omezení nebyl zadán správně. V tématu [omezení obecných parametrů typů (C + +/ CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md) Další informace.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3388.  
  
```  
// C3388.cpp  
// compile with: /clr /c  
interface class AA {};  
  
generic <class T>  
where T : interface class   // C3388  
ref class C {};  
  
// OK  
generic <class T>  
where T : AA  
ref class D {};  
```