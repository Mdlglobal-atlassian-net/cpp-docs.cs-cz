---
title: Testování znaků | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 376ba061-bae3-427e-9569-33fa5949a199
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cdf65de941486cb8256ba8e30a3f186d3e3702d6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32381691"
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