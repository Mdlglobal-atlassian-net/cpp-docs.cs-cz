---
title: "Upozornění příkazového řádku D9041 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- D9041
dev_langs:
- C++
helpviewer_keywords:
- D9041
ms.assetid: ada8815f-4246-4e25-b57d-a7f16fa107cc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 307d290bb525ee879f29853c6823d5b9565aba4b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="command-line-warning-d9041"></a>Upozornění příkazového řádku D9041
Neplatná hodnota 'Hodnota' pro '/ možnost'; za předpokladu, že 'Hodnota'; Přidejte ' / analyzovat ' pro možnosti příkazového řádku při zadávání toto upozornění  
  
 Číslo upozornění analýzy kódu byl přidán do **/wd**, **/we**, **/wo**, nebo **/Wl online** možnost příkazového řádku bez zadání také **/ analyze** možnost příkazového řádku. Chcete-li opravit tuto chybu, přidejte **/ analyze** příkazového řádku, nebo odeberte neplatné číslo upozornění z příslušné **/w** možnost příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující příklad příkazový řádek vygeneruje upozornění D9041:  
  
```  
cl /EHsc /LD /wd6001 filename.cpp  
```  
  
 Chcete-li opravit upozornění, přidejte **/ analyze** možnost příkazového řádku. Pokud **/ analyze** nejsou podporovány na vaší verzi kompilátor, odeberte neplatné číslo upozornění z **/wd** možnost.  
  
## <a name="see-also"></a>Viz také  
 [Chyby příkazového řádku D8000 až D9999](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)   
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)