---
title: "Testování znaků | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 376ba061-bae3-427e-9569-33fa5949a199
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: aeea6573b49e3bb093c3eb343ac3c89c27f0466b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="character-testing"></a>Testování znaků
**ANSI 4.3.1** sady znaků testována pomocí `isalnum`, `isalpha`, `iscntrl`, `islower`, `isprint`, a `isupper` funkce  
  
 Následující seznam popisuje implementaci těchto funkcí v kompilátoru jazyka Microsoft C.  
  
|Funkce|Testuje|  
|--------------|---------------|  
|`isalnum`|Znaky 0 - 9, A-Z, a – z ASCII 48-57, 65 90, 97 122|  
|`isalpha`|Znaky A-Z, a – z ASCII 65 90, 97 122|  
|`iscntrl`|ASCII 0-31, 127|  
|`islower`|A-z znaků ASCII 97-122|  
|`isprint`|Znaky A-Z,-z, 0 - 9, interpunkční znaménka, místo ASCII 126 32.|  
|`isupper`|Znaky ASCII 65-90 A-Z|  
  
## <a name="see-also"></a>Viz také  
 [Funkce knihovny](../c-language/library-functions.md)