---
title: C4957 upozornění kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4957
dev_langs:
- C++
helpviewer_keywords:
- C4957
ms.assetid: a18c52d4-23e2-44f1-b4b5-f7fa5a7f3987
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a76fb6ff4c00317da3e65c5bf31979c777ea51e8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-c4957"></a>C4957 upozornění kompilátoru
'přetypovat': explicitní přetypování z 'cast_from' do 'cast_to' není ověřitelný  
  
 Přetypování bude mít za následek neověřitelný bitové kopie.  
  
 Některé položky CAST jsou bezpečné (například `static_cast` , aktivuje uživatelem definované převody a `const_cast`). A [safe_cast](../../windows/safe-cast-cpp-component-extensions.md) záruku, že se k vytvoření ověřitelný kód.  
  
 Další informace najdete v tématu [prázdná a ověřitelný kód (C + +/ CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).  
  
 Toto upozornění se objeví jako chybu a můžete je třeba zakázat pomocí [upozornění](../../preprocessor/warning.md) – Direktiva pragma nebo [/wd](../../build/reference/compiler-option-warning-level.md) – možnost kompilátoru.  
  
 Následující ukázka generuje C4957:  
  
```  
// C4957.cpp  
// compile with: /clr:safe  
// #pragma warning( disable : 4957 )  
using namespace System;  
int main() {  
   Object ^ o = "Hello, World!";  
   String ^ s = static_cast<String^>(o);   // C4957  
   String ^ s2 = safe_cast<String^>(o);   // OK  
}  
```