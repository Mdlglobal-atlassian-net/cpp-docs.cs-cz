---
title: Upozornění příkazového řádku D9041 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D9041
dev_langs:
- C++
helpviewer_keywords:
- D9041
ms.assetid: ada8815f-4246-4e25-b57d-a7f16fa107cc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c22573d26e09e14789f4cbd64d68f4082125c2b3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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