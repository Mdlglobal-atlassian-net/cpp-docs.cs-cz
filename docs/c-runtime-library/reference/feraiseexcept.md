---
title: feraiseexcept | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname: feraiseexcept
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
apitype: HeaderDef
f1_keywords:
- feraiseexcept
- fenv/feraiseexcept
dev_langs: C++
helpviewer_keywords: feraiseexcept function
ms.assetid: 87e89151-83c2-4563-9a9a-45666245d437
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9ab77da8cee422bab618dc8737ad254b65301ffd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="feraiseexcept"></a>feraiseexcept
Vyvolá zadané výjimky s plovoucí desetinnou čárkou.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int feraiseexcept(  
   int excepts  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `excepts`  
 S plovoucí desetinnou čárkou výjimky vygeneroval.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud všechny zadané výjimky jsou vyvolány úspěšně, vrátí hodnotu 0.  
  
## <a name="remarks"></a>Poznámky  
 `feraiseexcept` Funkce pokusí vyvolat s plovoucí desetinnou čárkou výjimky určeného `excepts`.   `feraiseexcept` Funkce podporuje tyto makra výjimek definované v \<fenv.h >:  
  
|Výjimka – makro|Popis|  
|---------------------|-----------------|  
|FE_DIVBYZERO|V dříve s plovoucí desetinnou čárkou operace; došlo k chybě singularity nebo pólu byl vytvořen nekonečnou hodnotu.|  
|FE_INEXACT|Funkce musela být zaokrouhleno uložený výsledek dříve operace s plovoucí desetinnou čárkou.|  
|FE_INVALID|Došlo k chybě domény v dříve operaci s plovoucí desetinnou čárkou.|  
|FE_OVERFLOW|Rozsah došlo k chybě; výsledek operace s plovoucí desetinnou čárkou starší byl příliš velký a nelze je.|  
|FE_UNDERFLOW|Výsledek operace s plovoucí desetinnou čárkou starší byla příliš malé a nelze na úplné přesnost; Hodnota denormal byla vytvořena.|  
|FE_ALLEXCEPT|Bitová hodnota OR všech podporována s plovoucí desetinnou čárkou výjimky.|  
  
 `excepts` Argument může být nula, jednoho z hodnoty makro výjimky nebo bitové hodnotě nebo dvou nebo více makra podporované výjimek. Je-li makra zadanou výjimkou FE_OVERFLOW nebo FE_UNDERFLOW, může být FE_INEXACT výjimka vyvolána jako vedlejší účinek.  
  
 Chcete-li tuto funkci použít, je nutné vypnout s plovoucí desetinnou čárkou optimalizace, které může zabránit přístupu pomocí `#pragma fenv_access(on)` direktivy před volání. Další informace najdete v tématu [fenv_access –](../../preprocessor/fenv-access.md).  
  
 **Microsoft specifické:** výjimky zadaný v `excepts` jsou vyvolány v pořadí FE_INVALID, FE_DIVBYZERO, FE_OVERFLOW, FE_UNDERFLOW, FE_INEXACT. Ale FE_INEXACT může být vyvolá, když FE_OVERFLOW nebo FE_UNDERFLOW je vyvolána, i když není zadaný v `excepts`. **Konkrétní Microsoft end**  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Hlavička C|Hlavička C++|  
|--------------|--------------|------------------|  
|`feraiseexcept`|\<fenv.h >|\<cfenv >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace funkcí abecedně](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fesetexceptflag](../../c-runtime-library/reference/fesetexceptflag2.md)   
 [feholdexcept](../../c-runtime-library/reference/feholdexcept2.md)   
 [fetestexcept](../../c-runtime-library/reference/fetestexcept1.md)   
 [feupdateenv](../../c-runtime-library/reference/feupdateenv.md)