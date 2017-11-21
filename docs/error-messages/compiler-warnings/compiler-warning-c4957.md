---
title: "C4957 upozornění kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4957
dev_langs: C++
helpviewer_keywords: C4957
ms.assetid: a18c52d4-23e2-44f1-b4b5-f7fa5a7f3987
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c43ddf0e336d9964d08939bb7c1dd145caf6c848
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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