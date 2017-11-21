---
title: "strxfrm –, wcsxfrm –, _strxfrm_l –, _wcsxfrm_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- strxfrm
- _wcsxfrm_l
- _strxfrm_l
- wcsxfrm
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- strxfrm
- _tcsxfrm
- wcsxfrm
dev_langs: C++
helpviewer_keywords:
- strxfrm_l function
- _tcsxfrm function
- _strxfrm_l function
- strxfrm function
- wcsxfrm_l function
- wcsxfrm function
- string comparison [C++], transforming strings
- tcsxfrm function
- strings [C++], comparing locale
- _wcsxfrm_l function
ms.assetid: 6ba8e1f6-4484-49aa-83b8-bc2373187d9e
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 747639550e05a0e00daadcbd72d25b31c72a7dd5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="strxfrm-wcsxfrm-strxfrml-wcsxfrml"></a>strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l
Transformace řetězec v závislosti na informace specifické pro národní prostředí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
size_t strxfrm(  
   char *strDest,  
   const char *strSource,  
   size_t count   
);  
size_t wcsxfrm(  
   wchar_t *strDest,  
   const wchar_t *strSource,  
   size_t count   
);  
size_t _strxfrm_l(  
   char *strDest,  
   const char *strSource,  
   size_t count,  
   _locale_t locale  
);  
size_t wcsxfrm_l(  
   wchar_t *strDest,  
   const wchar_t *strSource,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `strDest`  
 Cílový řetězec.  
  
 `strSource`  
 Zdrojový řetězec.  
  
 `count`  
 Maximální počet znaků k umístění v `strDest`.  
  
 `locale`  
 Národní prostředí, které se má použít  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí délku transformovaných řetězec, není počítání ukončující znak hodnoty null. Pokud vrácená hodnota je větší než nebo rovna hodnotě `count`, obsah `strDest` předpovědět. Při chybě jednotlivé funkce nastaví `errno` a vrátí `INT_MAX`. Pro neplatný znak `errno` je nastaven na `EILSEQ`.  
  
## <a name="remarks"></a>Poznámky  
 `strxfrm` Funkce transformuje řetězec, na kterou odkazuje `strSource` do nového kompletován formulář, který je uložen v `strDest`. Více než `count` jsou transformuje a umístí do výsledný řetězec znaků, včetně znak hodnoty null. Transformace se uskuteční pomocí jako národní prostředí `LC_COLLATE` kategorie nastavení. Další informace o `LC_COLLATE`, najdete v části [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md). `strxfrm`používá aktuální národní prostředí pro své chování závislých na národním prostředí; `_strxfrm_l` se shoduje s tím rozdílem, že používá národní prostředí předaná místo aktuální národní prostředí. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
 Po transformaci volání `strcmp` s dva řetězce transformovaných dává výsledky, které jsou stejné jako ty volání `strcoll` u původního dva řetězce. Stejně jako u `strcoll` a `stricoll`, `strxfrm` automaticky zpracovává řetězců vícebajtových znaků podle potřeby.  
  
 `wcsxfrm`široká charakterová verze `strxfrm`; argumenty řetězce `wcsxfrm` jsou široká charakterová ukazatele. Pro `wcsxfrm`, po transformaci řetězec, volání `wcscmp` s dva řetězce transformovaných dává výsledky, které jsou stejné jako ty volání `wcscoll` u původního dva řetězce. `wcsxfrm`a `strxfrm` chovat jinak shodně. `wcsxfrm`používá aktuální národní prostředí pro své chování závislých na národním prostředí; `_wcsxfrm_l` používá národní prostředí předaná místo aktuální národní prostředí.  
  
 Tyto funkce ověřit jejich parametrů. Pokud `strSource` je ukazatel s hodnotou null, nebo `strDest` je ukazatele s hodnotou NULL (není-li počet nula), nebo pokud `count` je větší než `INT_MAX`, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md) . Pokud je povoleno spuštění pokračovat, nastavte tyto funkce `errno` k `EINVAL` a vrátí `INT_MAX`.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcsxfrm`|`strxfrm`|`strxfrm`|`wcsxfrm`|  
|`_tcsxfrm_l`|`_strxfrm_l`|`_strxfrm_l`|`_wcsxfrm_l`|  
  
 Pořadí znaky znakové sady (znaková sada ASCII) v národním prostředí "C", je stejná jako lexicographic pořadí znaky. V jiným národním prostředím, ale může pořadí znaků ve znakové sadě liší od pořadí lexicographic znaků. Například v některých evropských národní prostředí znak "a" (hodnota 0x61) předchází znak ' &\#x00E4;. (hodnota 0xE4) v znaková sada, ale znak 'ä' předchází znak "a" lexicographically.  
  
 V národní prostředí, pro které se liší znakovou sadu a znak lexicographic pořadí, použijte `strxfrm` na původní řetězce a potom `strcmp` výsledné řetězce k vytvoření porovnání lexicographic řetězců podle aktuální národní prostředí pro `LC_COLLATE` kategorie nastavení. Proto k porovnání dvou řetězců lexicographically ve výše uvedené národním prostředí použijte `strxfrm` na původní řetězce, pak `strcmp` výsledné řetězce. Alternativně můžete použít `strcoll` místo `strcmp` na původní řetězce.  
  
 `strxfrm`je v podstatě představuje obálku kolem [LCMapString](http://msdn.microsoft.com/library/windows/desktop/dd318700) s `LCMAP_SORTKEY`.  
  
 Následující výraz hodnotu velikost pole potřebné k uchování `strxfrm` transformace řetězec zdroje:  
  
```  
1 + strxfrm( NULL, string, 0 )  
```  
  
 V národním prostředí "C", `strxfrm` je ekvivalentní k následujícímu:  
  
```  
strncpy( _string1, _string2, _count );  
return( strlen( _string1 ) );  
```  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`strxfrm`|\<String.h >|  
|`wcsxfrm`|\<String.h > nebo \<wchar.h >|  
|`_strxfrm_l`|\<String.h >|  
|`_wcsxfrm_l`|\<String.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="see-also"></a>Viz také  
 [Převod dat](../../c-runtime-library/data-conversion.md)   
 [localeconv –](../../c-runtime-library/reference/localeconv.md)   
 [setlocale –, _wsetlocale –](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)   
 [strcoll – funkce](../../c-runtime-library/strcoll-functions.md)   
 [strcmp – wcscmp –, _mbscmp –](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strncmp –, wcsncmp –, _mbsncmp –, _mbsncmp_l –](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)