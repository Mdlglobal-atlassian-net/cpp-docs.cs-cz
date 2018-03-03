---
title: "Konstanty potvrzení na disku | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.constants
dev_langs:
- C++
helpviewer_keywords:
- commit-to-disk constants
ms.assetid: 0b903b23-b4fa-431e-a937-51d95f695ecf
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9dd4873d8f9b3a658996bfd057372e8fb29e3478
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="commit-to-disk-constants"></a>Konstanty potvrzení na disku
**Konkrétní Microsoft**  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
#include <stdio.h>  
```  
  
## <a name="remarks"></a>Poznámky  
 Tyto specifické pro společnost Microsoft konstanty zadejte, zda vyrovnávací paměť přidružené k otevření souboru vyprázdní vyrovnávací paměti operačního systému nebo na disk. Režim je součástí řetězec určující typ přístup pro čtení a zápis (**"r"**, **"w"**, **"a"**, **"r +"**, **"w +"** , **"+"**).  
  
 Režimy potvrzení na disku jsou následující:  
  
 **c**  
 Zapíše obsah unwritten zadané vyrovnávací paměti na disk. Tato funkce potvrzení disku dochází pouze v explicitní volání buď [fflush –](../c-runtime-library/reference/fflush.md) nebo [_flushall –](../c-runtime-library/reference/flushall.md) funkce. Tento režim je užitečné při plánování práce s důvěrnými osobními údaji. Například, pokud váš program ukončí po volání `fflush` nebo `_flushall`, můžete si být jisti, že vaše data dosaženo vyrovnávací paměti operačního systému. Ale pokud otevření souboru s **c** možnost, data může nikdy činit na disk v případě, že operační systém také ukončí.  
  
 **n**  
 Zapíše unwritten obsah zadanou vyrovnávací paměť do vyrovnávací paměti operačního systému. Operační systém může ukládat data do mezipaměti a pak stanovit, že optimální čas k zápisu na disk. V mnoha podmínkách toto chování usnadňuje efektivní program chování. Ale pokud doba uchování dat je důležité (například bankovní transakce nebo informace lístku letecká společnost) zvažte použití **c** možnost.  **n**  Režim je výchozí hodnota.  
  
> [!NOTE]
>  **c** a  **n**  možnosti nejsou součástí ANSI standard pro `fopen`, ale rozšíření Microsoft a neměl by se používat, kde je žádoucí přenositelnost ANSI.  
  
## <a name="using-the-commit-to-disk-feature-with-existing-code"></a>Funkce potvrzení na disku pomocí existujícího kódu  
 Ve výchozím nastavení, volá, aby se [fflush –](../c-runtime-library/reference/fflush.md) nebo [_flushall –](../c-runtime-library/reference/flushall.md) – funkce knihovny zápisu dat do vyrovnávací paměti udržuje v operačním systému. Operační systém určuje optimální dobu ve skutečnosti zapsat data na disk. Funkce běhové knihovny k potvrzení na disku umožňuje Ujistěte se, že je důležitá data zapsána přímo na disku, nikoli do vyrovnávací paměti operačního systému. Tato funkce můžete udělit do stávající aplikace bez přepisování pomocí jeho objekt soubory s COMMODE.OBJ propojení.  
  
 Ve výsledném spustitelného souboru, volá, aby se `fflush` zapsat obsah vyrovnávací paměti přímo na disku a volání `_flushall` zapisovat obsah všech vyrovnávací paměti na disk. Tyto dvě funkce jsou jediné vliv COMMODE.OBJ.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Datový proud vstupně-výstupních operací](../c-runtime-library/stream-i-o.md)   
 [_fdopen –, _wfdopen –](../c-runtime-library/reference/fdopen-wfdopen.md)   
 [fopen –, _wfopen –](../c-runtime-library/reference/fopen-wfopen.md)   
 [Globální konstanty](../c-runtime-library/global-constants.md)