---
title: "C3140 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3140
dev_langs: C++
helpviewer_keywords: C3140
ms.assetid: 122f8943-fac3-4db8-a3a8-2c5d19233de6
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e809ddaaa278e0c6a2660fbb71b84323dcd40018
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3140"></a>C3140 chyby kompilátoru
nemůže mít více atributů 'module' ve stejné jednotce kompilace  
  
 [Modulu](../../windows/module-cpp.md) atributu může být definovaný jenom jednou za projektu.  
  
 Následující ukázka generuje C3140:  
  
```  
// C3140.cpp  
// compile with: /c  
[emitidl];  
[module(name = "MyLibrary")];  
[module(name = "MyLibrary2")];   // C3140  
```