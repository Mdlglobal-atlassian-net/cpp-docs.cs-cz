---
title: C3170 chyby kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3170
dev_langs:
- C++
helpviewer_keywords:
- C3170
ms.assetid: ca9a59d6-7df3-42f0-b028-c09d0af3ac2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8bb077bcad95de0be17e630803b5d4ea9825be61
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3170"></a>C3170 chyby kompilátoru
nemůže mít jiného modulu identifikátory v projektu  
  
 [modul](../../windows/module-cpp.md) v dva soubory v kompilaci byly nalezeny atributy s různými názvy. Pouze jeden jedinečný `module` jeden kompilace lze zadat atribut.  
  
 Identické `module` atributy lze zadat v více než jednoho souboru se zdrojovým kódem.  
  
 Například, pokud byly nalezeny následující atributy modulu:  
  
```  
// C3170.cpp  
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];  
int main() {}  
```  
  
 A pak  
  
```  
// C3170b.cpp  
// compile with: C3170.cpp  
// C3170 expected  
[ module(name="MyModule1", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];  
```  
  
 Kompilátor by vygeneroval C3170 (Všimněte si odlišné názvy).