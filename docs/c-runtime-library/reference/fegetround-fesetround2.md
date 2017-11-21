---
title: fegetround fesetround2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- fegetround
- fesetround
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
- fegetround
- fesetround
- fenv/fegetround
- fenv/fesetround
dev_langs: C++
helpviewer_keywords:
- fegetround function
- fesetround function
ms.assetid: 596af00b-be2f-4f57-b2f5-460485f9ff0b
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7bc3fd0359f78e101565b5cb1bd01e0391df8bc6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fegetround-fesetround"></a>fegetround fesetround
Získá nebo nastaví aktuální režim zaokrouhlení s plovoucí desetinnou čárkou.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int fegetround(void);  
  
int fesetround(  
   int round_mode  
);   
```  
  
#### <a name="parameters"></a>Parametry  
 `round_mode`  
 Režim zaokrouhlení nastavit jako jeden z s plovoucí desetinnou čárkou zaokrouhlení makra. Pokud hodnota není jednu s plovoucí desetinnou čárkou zaokrouhlení makra, nedojde ke změně režimu zaokrouhlení.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu `fegetround` vrátí hodnotu režimu zaokrouhlení jako jeden z plovoucí desetinné čárky zaokrouhlení makro hodnoty. Pokud je aktuální režim zaokrouhlení nelze určit vrátí zápornou hodnotu.  
  
 V případě úspěchu `fesetround` vrátí hodnotu 0. Jinak se vrátí nenulovou hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 Operace s plovoucí desetinnou čárkou můžete použít některou z několika režimech zaokrouhlení. Tyto řídit směru výsledky operací s plovoucí desetinnou čárkou se zaokrouhlí směrem k, když jsou uložené výsledky. Jedná se o názvy a chování s plovoucí desetinnou čárkou zaokrouhlení makra definované v \<fenv.h >:  
  
|– Makro|Popis|  
|-----------|-----------------|  
|FE_DOWNWARD|Zaokrouhlí směrem záporné nekonečno.|  
|FE_TONEAREST|Zaokrouhlí směrem na nejbližší.|  
|FE_TOWARDZERO|Zaokrouhlí směrem k nule.|  
|FE_UPWARD|Zaokrouhlí směrem kladné nekonečno.|  
  
 Výchozí chování FE_TONEAREST je zaokrouhlit výsledků uprostřed mezi reprezentovat hodnoty na nejbližší hodnotu s i (0) nejméně významný bit.  
  
 Aktuální režim zaokrouhlení ovlivňují tyto operace:  
  
-   Řetězec převody.  
  
-   Výsledky s plovoucí desetinnou čárkou aritmetické operátory mimo konstantní výrazy.  
  
-   Knihovna zaokrouhlení funkce, jako například `rint` a `nearbyint`.  
  
-   Návratové hodnoty z matematické funkce standardní knihovny.  
  
 Aktuální režim zaokrouhlení nemá vliv na tyto operace:  
  
-   `trunc`, `ceil`, `floor`, A `lround` – funkce knihovny.  
  
-   S plovoucí desetinnou čárkou na celé číslo implicitní přetypování a převody, které vždy zaokrouhlí směrem k nule.  
  
-   Výsledky s plovoucí desetinnou čárkou aritmetických operátorů v konstantní výrazy, které vždy zaokrouhlí na nejbližší hodnotu.  
  
 Použití těchto funkcí, je nutné vypnout s plovoucí desetinnou čárkou optimalizace, které může zabránit přístupu pomocí `#pragma fenv_access(on)` direktivy před volání. Další informace najdete v tématu [fenv_access –](../../preprocessor/fenv-access.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Hlavička C|Hlavička C++|  
|--------------|--------------|------------------|  
|`fegetround`,                `fesetround`|\<fenv.h >|\<cfenv >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace funkcí abecedně](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [nearbyint – nearbyintf –, nearbyintl](../../c-runtime-library/reference/nearbyint-nearbyintf-nearbyintl1.md)   
 [tisknout, rintf, rintl](../../c-runtime-library/reference/rint-rintf-rintl.md)   
 [lrint, lrintf, lrintl, llrint, llrintf, llrintl](../../c-runtime-library/reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)