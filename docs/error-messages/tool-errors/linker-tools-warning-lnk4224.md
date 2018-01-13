---
title: "Upozornění linkerů Lnk4224 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4224
dev_langs: C++
helpviewer_keywords: LNK4224
ms.assetid: 8624b70e-0b93-43cf-b457-834d38632d0b
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 96399e0c66eb3cb719073b2318513cd680723d97
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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