---
title: "Přístup k argumentu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.arguments
dev_langs:
- C++
helpviewer_keywords:
- argument access macros [C++]
- variable-length argument lists
ms.assetid: 7046ae34-a0ec-44f0-815d-3209492a3e19
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 97db036822687936f3f8e4084c065c8ec64ca23e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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