---
title: "Konstanty posunutí souboru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.constants.file
dev_langs: C++
helpviewer_keywords:
- translation constants
- file translation [C++], constants
- translation, file translation constants
- translation, constants
- constants [C++], file translation mode
- file translation [C++]
ms.assetid: 49b13bf3-442e-4d19-878b-bd1029fa666a
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a68c41793ea96a840a78e76e5b2a222f0b06a583
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="file-translation-constants"></a>Konstanty posunutí souboru
## <a name="syntax"></a>Syntaxe  
  
```  
  
#include <stdio.h>  
```  
  
## <a name="remarks"></a>Poznámky  
 Zadejte tyto konstanty režimu posunutí (**"b"** nebo **"t"**). Režim je součástí řetězec určující typ přístupu (**"r"**, **"w"**, **"a"**, **"r +"**, **"w +"**, **"+"**).  
  
 Režimy překladu jsou následující:  
  
 **t**  
 Otevře se v režimu textových (přeložit). V tomto režimu kombinace znaků CR vrátit/konce řádku (CR-LF) jsou převedeny do jednoho přečtené (LF) na vstupu a LF znaky jsou převedeny na znaky CR LF kombinace na výstup. Příkaz CTRL+Z je na vstupu interpretován jako znak konce souboru. V souborech otevřít pro čtení nebo čtení/zápis `fopen` kontroluje CTRL + Z na konci souboru a odstraní ji, pokud je to možné. To je provést, protože používá `fseek` a `ftell` může způsobit, že funkce přesunout v souboru s CTRL + Z `fseek` chovat nesprávně blíží konec souboru.  
  
> [!NOTE]
>  **t** možnost není součástí ANSI standard pro `fopen` a `freopen`. Je rozšíření Microsoft a neměl by se používat, kde je žádoucí přenositelnost ANSI.  
  
 **b**  
 Otevře se v binárním režimu (nepřeložený). Výše uvedené překlady jsou potlačovány.  
  
 Pokud **t** nebo **b** není uveden v *režimu*, režim překladu je definovanou proměnnou výchozí režim [_fmode –](../c-runtime-library/fmode.md). Další informace o používání textovém a binárním režimu najdete v tématu [Text a vstupně-výstupní soubor binárního režimu](../c-runtime-library/text-and-binary-mode-file-i-o.md).  
  
## <a name="see-also"></a>Viz také  
 [_fdopen –, _wfdopen –](../c-runtime-library/reference/fdopen-wfdopen.md)   
 [fopen –, _wfopen –](../c-runtime-library/reference/fopen-wfopen.md)   
 [freopen –, _wfreopen –](../c-runtime-library/reference/freopen-wfreopen.md)   
 [_fsopen –, _wfsopen –](../c-runtime-library/reference/fsopen-wfsopen.md)   
 [Globální konstanty](../c-runtime-library/global-constants.md)