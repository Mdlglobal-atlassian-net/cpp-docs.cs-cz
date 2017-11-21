---
title: fetestexcept1 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname: fetestexcept
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
- fetestexcept
- fenv/fetestexcept
dev_langs: C++
helpviewer_keywords: fetestexept function
ms.assetid: ca4dc43f-5573-440d-bc19-ead7571b13dc
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a2fa4448bc71fc8b01abffaa0655f63e6ef474a0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fetestexcept"></a>fetestexcept
Určuje, které příznaky stavu s plovoucí desetinnou čárkou výjimce momentálně nastaven.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int fetestexcept(  
   int excepts  
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `excepts`  
 Bitový operátor OR příznaků s plovoucí desetinnou čárkou stav pro testování.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí bitová maska obsahující bitové operace OR makra výjimek plovoucí desetinné čárky, které odpovídají příznaky stavu výjimka aktuálně nastavit. Vrátí hodnotu 0, pokud žádná z výjimky jsou nastavené.  
  
## <a name="remarks"></a>Poznámky  
 Pomocí funkce fetestexcept k určení výjimek, které byly vydané plovoucí bodu operaci. Použití `excepts` parametr k určení stavu příznacích výjimky k testování. `fetestexcept` Funkce používá tyto makra výjimek definované v \<fenv.h > v `excepts` a návratovou hodnotu:  
  
|Výjimka – makro|Popis|  
|---------------------|-----------------|  
|FE_DIVBYZERO|V dříve s plovoucí desetinnou čárkou operace; došlo k chybě singularity nebo pólu byl vytvořen nekonečnou hodnotu.|  
|FE_INEXACT|Funkce musela být zaokrouhleno uložený výsledek dříve operace s plovoucí desetinnou čárkou.|  
|FE_INVALID|Došlo k chybě domény v dříve operaci s plovoucí desetinnou čárkou.|  
|FE_OVERFLOW|Rozsah došlo k chybě; výsledek operace s plovoucí desetinnou čárkou starší byl příliš velký a nelze je.|  
|FE_UNDERFLOW|Výsledek operace s plovoucí desetinnou čárkou starší byla příliš malé a nelze na úplné přesnost; Hodnota denormal byla vytvořena.|  
|FE_ALLEXCEPT|Bitová hodnota OR všech podporována s plovoucí desetinnou čárkou výjimky.|  
  
 Zadaný `excepts` argument může mít hodnotu 0, jednoho z podporovaných výjimek plovoucí desetinné čárky makra nebo bitové hodnotě nebo dva nebo víc makra. Účinek jakékoliv `excepts` hodnota argumentu není definován.  
  
 Chcete-li tuto funkci použít, je nutné vypnout s plovoucí desetinnou čárkou optimalizace, které může zabránit přístupu pomocí `#pragma fenv_access(on)` direktivy před volání. Další informace najdete v tématu [fenv_access –](../../preprocessor/fenv-access.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Hlavička C|Hlavička C++|  
|--------------|--------------|------------------|  
|`fetestexcept`|\<fenv.h >|\<cfenv >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace funkcí abecedně](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [feclearexcept](../../c-runtime-library/reference/feclearexcept1.md)   
 [feraiseexcept](../../c-runtime-library/reference/feraiseexcept.md)