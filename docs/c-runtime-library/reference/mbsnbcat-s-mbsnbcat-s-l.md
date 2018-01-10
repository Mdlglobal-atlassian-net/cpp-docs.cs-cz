---
title: "_mbsnbcat_s –, _mbsnbcat_s_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbsnbcat_s_l
- _mbsnbcat_s
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _mbsnbcat_s
- mbsnbcat_s
- _mbsnbcat_s_l
- mbsnbcat_s_l
dev_langs: C++
helpviewer_keywords:
- _tcsncat function
- mbsnbcat_s function
- _mbsnbcat_s function
- _mbsnbcat_s_l function
- _tcsncat_s_l function
- tcsncat_s_l function
- mbsnbcat_s_l function
- tcsncat function
ms.assetid: 2c9e9be7-d979-4a54-8ada-23428b6648a9
caps.latest.revision: "28"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7288c00de4f09175d7fffd816267201011892953
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="mbsnbcats-mbsnbcatsl"></a>_mbsnbcat_s, _mbsnbcat_s_l
Připojí k vícebajtový řetězec, maximálně první `n` bajtů jiné řetězce vícebajtových znaků. Toto jsou verze [_mbsnbcat –, _mbsnbcat_l –](../../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md) vylepšení zabezpečení, které mají, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
errno_t _mbsnbcat_s(  
   unsigned char *dest,  
   size_t sizeInBytes,  
   const unsigned char *src,  
   size_t count   
);  
errno_t _mbsnbcat_s_l(  
   unsigned char *dest,  
   size_t sizeInBytes,  
   const unsigned char *src,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
errno_t _mbsnbcat_s(  
   unsigned char (&dest)[size],  
   const unsigned char *src,  
   size_t count   
); // C++ only  
template <size_t size>  
errno_t _mbsnbcat_s_l(  
   unsigned char (&dest)[size],  
   const unsigned char *src,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 `dest`  
 Řetězce ukončené hodnotou Null cílové vícebajtových znaků.  
  
 `sizeInBytes`  
 Velikost `dest` vyrovnávací paměti v bajtech.  
  
 `src`  
 Řetězce ukončené hodnotou Null zdroj vícebajtových znaků.  
  
 `Count`  
 Počet bajtů z `src` připojit k `dest`.  
  
 `locale`  
 Národní prostředí použít.  
  
## <a name="return-value"></a>Návratová hodnota  
 Nula v případě úspěšného; jinak kód chyby.  
  
### <a name="error-conditions"></a>Chybové stavy  
  
|`Dest`|`sizeInBytes`|`src`|Návratová hodnota|  
|------------|-------------------|-----------|------------------|  
|`NULL`|všechny|všechny|`EINVAL`|  
|všechny|<= 0|všechny|`EINVAL`|  
|všechny|všechny|`NULL`|`EINVAL`|  
  
 Pokud některá z podmínek chybě dojde, funkce vygeneruje chybu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud se zpracovává chyba, vrátí funkce `EINVAL` a nastaví `errno` k `EINVAL`.  
  
## <a name="remarks"></a>Poznámky  
 `_mbsnbcat_s` Funkce připojí k `dest`, maximálně první `count` bajtů `src`. Pokud bajtů bezprostředně předchází znak hodnoty null v `dest` je úvodní bajt je přepsány počáteční bajt `src`. V opačném počáteční bajt `src` přepíše ukončující znak null `dest`. Pokud se objeví null bajtů v `src` před `count` bajtů se připojují, `_mbsnbcat_s` připojí všechny bajtů z `src`, až do znaku, hodnotu null. Pokud `count` je větší než délka `src`, délka `src` slouží místě `count`. Výsledný řetězec se ukončila příkazem znak hodnoty null. Pokud kopírování probíhá mezi řetězce, které se překrývají, chování nedefinovaný.  
  
 Výstupní hodnota je ovlivňován nastavením `LC_CTYPE` kategorie nastavení národního prostředí; viz [setlocale _wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) Další informace. Verze tyto funkce jsou identické, s tím rozdílem, že ty, které nejsou mít `_l` příponu použít aktuální národní prostředí a ty, které mají `_l` příponu, použijte parametr národního prostředí, který se předává v. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
 V jazyce C++ použití tyto funkce se zjednodušilo díky šabloně přetížení; přetížení můžete automaticky odvození délka vyrovnávací paměti a eliminovat potřeba zadat argument velikost a jejich funkce novější se bezpečnější můžete automaticky použijí k nahrazení starší, méně bezpečné funkce. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).  
  
 Ladicí verze těchto funkcí nejprve vyplnit vyrovnávací paměť s 0xFD. Chcete-li toto chování zakázat, použijte [_crtsetdebugfillthreshold –](../../c-runtime-library/reference/crtsetdebugfillthreshold.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tcsncat`|[strncat –](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|`_mbsnbcat_s`|[wcsncat –](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|  
|`_tcsncat_s_l`|`_strncat_s_l`|`_mbsnbcat_s_l`|`_wcsncat_s_l`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_mbsnbcat_s`|\<Mbstring.h >|  
|`_mbsnbcat_s_l`|\<Mbstring.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)   
 [_mbsnbcmp –, _mbsnbcmp_l –](../../c-runtime-library/reference/mbsnbcmp-mbsnbcmp-l.md)   
 [_strncnt –, _wcsncnt –, _mbsnbcnt –, _mbsnbcnt_l –, _mbsnccnt –, _mbsnccnt_l –](../../c-runtime-library/reference/strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)   
 [_mbsnbcpy –, _mbsnbcpy_l –](../../c-runtime-library/reference/mbsnbcpy-mbsnbcpy-l.md)   
 [_mbsnbcpy_s –, _mbsnbcpy_s_l –](../../c-runtime-library/reference/mbsnbcpy-s-mbsnbcpy-s-l.md)   
 [_mbsnbset –, _mbsnbset_l –](../../c-runtime-library/reference/mbsnbset-mbsnbset-l.md)   
 [strncat –, _strncat_l, wcsncat –, _wcsncat_l, _mbsncat –, _mbsncat_l –](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)   
 [strncat_s, _strncat_s_l, wcsncat_s, _wcsncat_s_l, _mbsncat_s, _mbsncat_s_l](../../c-runtime-library/reference/strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)