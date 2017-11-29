---
title: "C3519 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3519
dev_langs: C++
helpviewer_keywords: C3519
ms.assetid: ca24b2bc-7e90-4448-ae84-3fedddf9bca7
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c655c8ba0513bcf25d5bc9666d65352a7f587374
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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