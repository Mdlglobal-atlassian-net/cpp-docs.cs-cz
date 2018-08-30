---
title: Upozornění (úroveň 4) C4242 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4242
dev_langs:
- C++
helpviewer_keywords:
- C4242
ms.assetid: 8df742e1-fbf1-42f3-8e93-c0e1c222dc7e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 623183e5ee54c995d624f47461c724ee8f4befae
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43217395"
---
# <a name="compiler-warning-level-4-c4242"></a>Kompilátor upozornění (úroveň 4) C4242
'identifier': převod z 'type1' na 'type2', možná ztráta dat  
  
 Typy se liší. Převod typu může dojít ke ztrátě dat. Kompilátor provede převod typů.  
  
 Toto upozornění je vypnuto ve výchozím nastavení. Zobrazit [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.  
  
 Další informace o C4242 najdete v tématu [běžné chyby kompilátoru](/windows/desktop/WinProg64/common-compiler-errors).  
  
 Následující ukázka generuje C4242:  
  
```  
// C4242.cpp  
// compile with: /W4  
#pragma warning(4:4242)  
int func() {  
   return 0;  
}  
  
int main() {  
   char a;  
   a = func();   // C4242, return type and variable type do not match  
}  
```