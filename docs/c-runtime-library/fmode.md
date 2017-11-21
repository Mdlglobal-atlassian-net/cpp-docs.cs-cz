---
title: "_fmode – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- fmode
- _fmode
dev_langs: C++
helpviewer_keywords:
- file translation [C++], default mode
- fmode function
- _fmode function
ms.assetid: ac6df9eb-e5cc-4c54-aff3-373c21983118
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9007cceacb150b13796e395799f2037704976802
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fmode"></a>_fmode
`_fmode` Proměnná nastaví výchozí režim překladu souboru pro překlad textu nebo binárních. Tato globální proměnná se už nepoužívá pro bezpečnější funkční verze [_get_fmode –](../c-runtime-library/reference/get-fmode.md) a [_set_fmode –](../c-runtime-library/reference/set-fmode.md), který má být použit místo globální proměnné. Je deklarován v Stdlib.h následujícím způsobem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
extern int _fmode;  
```  
  
## <a name="remarks"></a>Poznámky  
 Výchozí nastavení `_fmode` je `_O_TEXT` pro překlad textovém režimu. `_O_BINARY`je nastavení pro binárního režimu.  
  
 Můžete změnit hodnotu `_fmode` třemi způsoby:  
  
-   Odkaz s Binmode.obj. Tato operace změní počáteční nastavení `_fmode` k `_O_BINARY`, způsobuje všechny soubory kromě `stdin`, `stdout`, a `stderr` otevřít v binárním režimu.  
  
-   Volání na `_get_fmode` nebo `_set_fmode` pro získání nebo nastavení `_fmode` globální proměnná, v uvedeném pořadí.  
  
-   Změňte hodnotu `_fmode` přímo podle nastavení v programu.  
  
## <a name="see-also"></a>Viz také  
 [Globální proměnné](../c-runtime-library/global-variables.md)   
 [_get_fmode –](../c-runtime-library/reference/get-fmode.md)   
 [_set_fmode –](../c-runtime-library/reference/set-fmode.md)