---
title: Konstanty souboru | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _O_EXCL
- _O_RDWR
- _O_APPEND
- _O_RDONLY
- _O_TRUNC
- _O_CREAT
- _O_WRONLY
dev_langs: C++
helpviewer_keywords:
- _O_RDWR constant
- O_EXCL constant
- O_RDWR constant
- O_WRONLY constant
- O_APPEND constant
- O_CREAT constant
- _O_CREAT constant
- _O_APPEND constant
- _O_EXCL constant
- O_TRUNC constant
- _O_RDONLY constant
- _O_TRUNC constant
- O_RDONLY constant
- _O_WRONLY constant
ms.assetid: c8fa5548-9ac2-4217-801d-eb45e86f2fa4
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 51d5de22dce0b68c55fc928b1a251b30d9ceed7f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="file-constants"></a>Konstanty souboru
## <a name="syntax"></a>Syntaxe  
  
```  
  
#include <fcntl.h>  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Celočíselný výraz vytvořen z jednoho nebo více z následujících konstant Určuje typ čtení nebo zápisu operace povolena. Je tvořen kombinování jeden nebo více konstant s konstantou, režim překladu.  
  
 Konstanty souboru jsou následující:  
  
 `_O_APPEND`  
 Přemístí ukazatel na konec souboru před každou operaci zápisu.  
  
 `_O_CREAT`  
 Vytvoří a otevře nový soubor pro zápis; To nemá vliv, pokud soubor určeného *filename* existuje.  
  
 `_O_EXCL`  
 Vrací hodnotu chyby, pokud soubor určeného *filename* existuje. Platí jenom při použití s `_O_CREAT`.  
  
 `_O_RDONLY`  
 Otevře soubor pro čtení pouze; Pokud je zadána tento příznak, ani `_O_RDWR` ani `_O_WRONLY` je možné přidělit.  
  
 `_O_RDWR`  
 Otevře soubor pro čtení i zápis; Pokud je zadána tento příznak, ani `_O_RDONLY` ani `_O_WRONLY` je možné přidělit.  
  
 `_O_TRUNC`  
 Otevře a zkrátí existující soubor na nulu length; soubor musí mít oprávnění k zápisu. Obsah souboru zničena. Pokud je zadána tento příznak nelze zadat `_O_RDONLY`.  
  
 `_O_WRONLY`  
 Otevře soubor pro zápis pouze; Pokud je zadána tento příznak, ani `_O_RDONLY` ani `_O_RDWR` je možné přidělit.  
  
## <a name="see-also"></a>Viz také  
 [_Otevřít _wopen –](../c-runtime-library/reference/open-wopen.md)   
 [_sopen –, _wsopen –](../c-runtime-library/reference/sopen-wsopen.md)   
 [Globální konstanty](../c-runtime-library/global-constants.md)