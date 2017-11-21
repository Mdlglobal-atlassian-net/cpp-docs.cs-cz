---
title: "Přístup k argumentu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.arguments
dev_langs: C++
helpviewer_keywords:
- argument access macros [C++]
- variable-length argument lists
ms.assetid: 7046ae34-a0ec-44f0-815d-3209492a3e19
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c216c009d84771fdf34426b6121a89eb4b3f73e4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="argument-access"></a>Přístup k argumentu
`va_arg`, `va_end`, A `va_start` makra poskytnout přístup k argumenty funkce, pokud počet argumentů je proměnná. Tyto makra jsou definovány v STDARG. H pro ANSI C kompatibility a v vararg. H pro kompatibilitu s V systému UNIX.  
  
### <a name="argument-access-macros"></a>Přístup k argumentu makra  
  
|– Makro|Použití|  
|-----------|-------------------------------|  
|[va_arg –](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|Načtení argument ze seznamu|  
|[va_end –](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|Resetování ukazatele|  
|[va_start –](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|Nastavit ukazatel na začátku seznamu argumentů|  
  
## <a name="see-also"></a>Viz také  
 [Běhové rutiny podle kategorie](../c-runtime-library/run-time-routines-by-category.md)