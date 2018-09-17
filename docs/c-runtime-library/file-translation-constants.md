---
title: Konstanty posunutí souboru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.constants.file
dev_langs:
- C++
helpviewer_keywords:
- translation constants
- file translation [C++], constants
- translation, file translation constants
- translation, constants
- constants [C++], file translation mode
- file translation [C++]
ms.assetid: 49b13bf3-442e-4d19-878b-bd1029fa666a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 613a6357da969cb39d84d1f6e764f14112b3b6fc
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712605"
---
# <a name="file-translation-constants"></a>Konstanty posunutí souboru
## <a name="syntax"></a>Syntaxe  
  
```  
#include <stdio.h>  
```  
  
## <a name="remarks"></a>Poznámky  

Tyto konstanty určení režimu překladu (**"b"** nebo **"t"**). Režim je součástí řetězce, který specifikuje typ přístupu (**"r"**, **"w"**, **"a"**, **"r +"**, **"w +"**, **"a +"**).  
  
Režimy překladu jsou následující:  
  
- **t**  

   Otevře se v textovém (přeloženém) režimu. V tomto režimu kombinace návrat na začátek řádku return nebo odřádkování (CR-LF) jsou přeloženy (LF) na vstupu a znaků LF jsou přeloženy do na výstupu jako kombinace CR-LF. Příkaz CTRL+Z je na vstupu interpretován jako znak konce souboru. V souborech otevřených pro čtení nebo čtení/zápis `fopen` vyhledává CTRL + Z na konci souboru a odstraní ji, pokud je to možné. Toto je provedeno z důvodu použití `fseek` a `ftell` může způsobit, že funkce pro přesun v rámci souboru končí CTRL + Z `fseek` nesprávné chování na konci souboru.  
  
   > [!NOTE]
   > **t** možnost není součástí standardu ANSI `fopen` a `freopen`. Je rozšířením společnosti Microsoft a neměl by se používat, kde je žádoucí přenositelnost ANSI.  
  
- **b**  

   Otevře se v binárním (nepřeloženém) režimu. Překlady uvedené výše jsou potlačeny.  
  
Pokud **t** nebo **b** není uveden v *režimu*, režim překladu definován proměnnou výchozího režimu [_fmode](../c-runtime-library/fmode.md). Další informace o používání textovém a binárním režimu najdete v tématu [textového a binárního režimu souboru vstupně-výstupních operací](../c-runtime-library/text-and-binary-mode-file-i-o.md).  
  
## <a name="see-also"></a>Viz také  
 [_fdopen – _wfdopen –](../c-runtime-library/reference/fdopen-wfdopen.md)   
 [fopen _wfopen –](../c-runtime-library/reference/fopen-wfopen.md)   
 [freopen, _wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)   
 [_fsopen – _wfsopen –](../c-runtime-library/reference/fsopen-wfsopen.md)   
 [Globální konstanty](../c-runtime-library/global-constants.md)