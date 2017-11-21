---
title: feclearexcept1 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname: feclearexcept
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- feclearexcept
- fenv/feclearexcept
dev_langs: C++
helpviewer_keywords: feclearexcept function
ms.assetid: ef419da3-c248-4432-b53c-8e7a475d9533
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ef5576dbe5df784f9e93de6b1d4167d4ee6afa74
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="feclearexcept"></a>feclearexcept
Pokusí se Vymazat příznaky výjimek plovoucí desetinné čárky určený argumentem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int feclearexcept(  
   int excepts  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `excepts`  
 Příznaky stavu výjimka zrušte.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí nula v případě `excepts` rovná nule, nebo pokud byly úspěšně vymazán všechny zadané výjimky. Jinak vrátí nenulovou hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 `feclearexcept` Funkce pokusí zrušte procedura bod příznaky stavu výjimka určeného `excepts`. Funkce podporuje tyto makra výjimek definované v fenv.h:  
  
|Výjimka – makro|Popis|  
|---------------------|-----------------|  
|FE_DIVBYZERO|V dříve s plovoucí desetinnou čárkou operace; došlo k chybě singularity nebo pólu byl vytvořen nekonečnou hodnotu.|  
|FE_INEXACT|Funkce musela být zaokrouhleno uložený výsledek dříve operace s plovoucí desetinnou čárkou.|  
|FE_INVALID|Došlo k chybě domény v dříve operaci s plovoucí desetinnou čárkou.|  
|FE_OVERFLOW|Rozsah došlo k chybě; výsledek operace s plovoucí desetinnou čárkou starší byl příliš velký a nelze je.|  
|FE_UNDERFLOW|Výsledek operace s plovoucí desetinnou čárkou starší byla příliš malé a nelze na úplné přesnost; Hodnota denormal byla vytvořena.|  
|FE_ALLEXCEPT|Bitová hodnota OR všech podporována s plovoucí desetinnou čárkou výjimky.|  
  
 `excepts` Argument může být nula nebo bitová hodnota OR jeden nebo více makra podporované výjimek. Výsledek jakoukoli jinou hodnotu argumentu není definován.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Hlavička C|Hlavička C++|  
|--------------|--------------|------------------|  
|`feclearexcept`|\<fenv.h >|\<cfenv >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace funkcí abecedně](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fetestexcept](../../c-runtime-library/reference/fetestexcept1.md)