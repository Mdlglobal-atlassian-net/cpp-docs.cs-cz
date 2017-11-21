---
title: "Omezení pole cesty | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _MAX_EXT
- _MAX_DIR
- _MAX_PATH
- _MAX_FNAME
- _MAX_DRIVE
dev_langs: C++
helpviewer_keywords:
- path field constants
- MAX_FNAME constant
- _MAX_DIR constant
- _MAX_DRIVE constant
- paths, maximum limit
- _MAX_PATH constant
- MAX_DRIVE constant
- _MAX_FNAME constant
- _MAX_EXT constant
- MAX_DIR constant
- MAX_EXT constant
ms.assetid: 2b5d0e43-1347-45b4-8397-24a8a45c444e
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0adde41ca70fa5fdc457772f6023b02f9550e2ca
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="path-field-limits"></a>Omezení pole cesty
## <a name="syntax"></a>Syntaxe  
  
```  
#include <stdlib.h>  
```  
  
## <a name="remarks"></a>Poznámky  
 Tyto konstanty určit maximální délku cesty a jednotlivých polí v této cestě.  
  
|Konstanta|Význam|  
|--------------|-------------|  
|`_MAX_DIR`|Maximální délka directory součásti|  
|`_MAX_DRIVE`|Maximální délka jednotky součásti|  
|`_MAX_EXT`|Maximální délka součásti rozšíření|  
|`_MAX_FNAME`|Maximální délka součástí názvu souboru|  
|`_MAX_PATH`|Maximální délka úplné cesty|  
  
> [!NOTE]
>  C Runtime podporuje délka délky cesty až 32768 znaků, ale je až operačního systému, speciálně systému souborů, pro podporu těchto delší cesty. Součet pole nesmí být delší než `_MAX_PATH` pro úplné zpětné kompatibility s FAT32 systémy souborů. [!INCLUDE[win2kfamily](../c-runtime-library/includes/win2kfamily_md.md)], [!INCLUDE[WinXpFamily](../atl/reference/includes/winxpfamily_md.md)], [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)], a systému souborů Windows Vista NTFS podporuje cesty až 32768 znaků v délka, ale jenom v případě, že pomocí rozhraní API kódování Unicode. Při použití dlouhé názvy cest, předpony cestu s znaky \\ \\? \ a použít Unicode verze funkce C Runtime.  
  
## <a name="see-also"></a>Viz také  
 [Globální konstanty](../c-runtime-library/global-constants.md)