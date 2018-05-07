---
title: Upozornění linkerů Lnk4224 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4224
dev_langs:
- C++
helpviewer_keywords:
- LNK4224
ms.assetid: 8624b70e-0b93-43cf-b457-834d38632d0b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a051e341a22871b4229617b3958cb68dedc2921
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4224"></a>Upozornění linkerů LNK4224
již není podporována možnost; Ignorovat  
  
 Možnost neplatný, zastaralé linkeru byl zadán a ignorovány.  
  
 Například LNK4224 může dojít, pokud se zobrazí v direktivu/Comment. objektu vývoz. / Comment – direktiva by byly přidané prostřednictvím [komentáře (C/C++)](../../preprocessor/comment-c-cpp.md) – Direktiva pragma, pomocí možnosti nepoužívané exestr. Použijte dumpbin [nebo všechny](../../build/reference/all.md) zobrazíte direktivy linkeru v souboru .obj.  
  
 Pokud je to možné upravte zdroj .obj a odebrat – Direktiva pragma. Pokud se toto upozornění ignorovat, je možné, že .executable kompilovat s **/CLR: pure** nespustí podle očekávání.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje LNK4224.  
  
```  
// LNK4224.cpp  
// compile with: /c /Zi  
// post-build command: link LNK4224.obj /debug /debugtype:map  
int main () {  
   return 0;  
}  
```