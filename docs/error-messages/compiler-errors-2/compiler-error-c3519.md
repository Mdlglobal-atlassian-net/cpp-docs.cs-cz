---
title: C3519 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3519
dev_langs:
- C++
helpviewer_keywords:
- C3519
ms.assetid: ca24b2bc-7e90-4448-ae84-3fedddf9bca7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 740fef32484164e7439335686adce0a4aa8027f6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33257195"
---
# <a name="compiler-error-c3519"></a>C3519 chyby kompilátoru
'invalid_param': Neplatný parametr pro embedded_idl – atribut  
  
 Byl předán parametr `embedded_idl` atribut [#import](../../preprocessor/hash-import-directive-cpp.md), ale kompilátor nerozpoznal parametr.  
  
 Jenom parametry, které jsou povoleny pro `embedded_idl` jsou `emitidl` a `no_emitidl`.  
  
 Následující ukázka generuje C3519:  
  
```  
// C3519.cpp  
// compile with: /LD  
[module(name="MyLib2")];  
#import "C:\testdir\bin\importlib.tlb" embedded_idl("no_emitidcl")     
// C3519  
#import "C:\testdir\bin\importlib.tlb" embedded_idl("no_emitidl")     
// OK  
```