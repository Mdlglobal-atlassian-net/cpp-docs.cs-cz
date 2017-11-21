---
title: "Konstanty režimu posunutí | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _O_BINARY
- _O_TEXT
- _O_RAW
dev_langs: C++
helpviewer_keywords:
- O_BINARY constant
- O_TEXT constant
- O_RAW constant
- _O_TEXT constant
- _O_RAW constant
- translation constants
- _O_BINARY constant
- translation, constants
- translation, modes
- translation modes (file I/O)
ms.assetid: a5993bf4-7e7a-47f9-83c3-e46332b85579
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8f5224064158dcbcb277524af21a0059a324fbc5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="translation-mode-constants"></a>Konstanty režimu posunutí
## <a name="syntax"></a>Syntaxe  
  
```  
  
#include <fcntl.h>  
  
```  
  
## <a name="remarks"></a>Poznámky  
 `_O_BINARY` a `_O_TEXT` manifestu konstanty určit režim překladu pro soubory (`_open` a `_sopen`) nebo režim překladu pro datové proudy (`_setmode`).  
  
 Povolené hodnoty jsou následující:  
  
 `_O_TEXT`  
 Otevře soubor v režimu textových (přeložit). Návrat na začátek-kombinace nový řádek (CR-LF) jsou převedeny do jednoho nový řádek (LF) na vstupu. Konce řádku znaky jsou převedeny na znaky CR LF kombinace na výstup. Příkaz CTRL+Z je na vstupu interpretován jako znak konce souboru. V souborech otevřít pro čtení a čtení/zápis `fopen` kontroluje CTRL + Z na konci souboru a odstraní ji, pokud je to možné. To je provést, protože používá `fseek` a `ftell` může způsobit, že funkce přesunout v souboru s CTRL + Z `fseek` chovat nesprávně blíží konec souboru.  
  
 `_O_BINARY`  
 Otevře soubor v binárním režimu (nepřeložený). Výše uvedené překlady jsou potlačovány.  
  
 `_O_RAW`  
 Stejné jako `_O_BINARY`. Pro C 2.0 kompatibility podporována.  
  
 Další informace najdete v tématu [Text a vstupně-výstupní soubor binárního režimu](../c-runtime-library/text-and-binary-mode-file-i-o.md) a [překlad souboru](../c-runtime-library/file-translation-constants.md).  
  
## <a name="see-also"></a>Viz také  
 [_Otevřít _wopen –](../c-runtime-library/reference/open-wopen.md)   
 [_pipe –](../c-runtime-library/reference/pipe.md)   
 [_sopen –, _wsopen –](../c-runtime-library/reference/sopen-wsopen.md)   
 [_setmode –](../c-runtime-library/reference/setmode.md)   
 [Globální konstanty](../c-runtime-library/global-constants.md)