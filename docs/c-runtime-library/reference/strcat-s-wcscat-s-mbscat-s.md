---
title: "strcat_s – wcscat_s –, _mbscat_s – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- strcat_s
- _mbscat_s
- wcscat_s
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- strcat_s
- wcscat_s
- _mbscat_s
dev_langs:
- C++
helpviewer_keywords:
- wcscat_s function
- strcat_s function
- mbscat_s function
- strings [C++], appending
- _mbscat_s function
- appending strings
ms.assetid: 0f2f9901-c5c5-480b-98bc-f8f690792fc0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c0dba645ab6caf7399bf4e1120c8c4a5a7139300
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="strcats-wcscats-mbscats"></a>strcat_s, wcscat_s, _mbscat_s
Přidá řetězec. Tyto verze nástroje [strcat – wcscat –, _mbscat –](../../c-runtime-library/reference/strcat-wcscat-mbscat.md) mít vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
> [!IMPORTANT]
>  `_mbscat_s` nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
errno_t strcat_s(  
   char *strDestination,  
   size_t numberOfElements,  
   const char *strSource   
);  
errno_t wcscat_s(  
   wchar_t *strDestination,  
   size_t numberOfElements,  
   const wchar_t *strSource   
);  
errno_t _mbscat_s(  
   unsigned char *strDestination,  
   size_t numberOfElements,  
   const unsigned char *strSource   
);  
template <size_t size>  
errno_t strcat_s(  
   char (&strDestination)[size],  
   const char *strSource   
); // C++ only  
template <size_t size>  
errno_t wcscat_s(  
   wchar_t (&strDestination)[size],  
   const wchar_t *strSource   
); // C++ only  
template <size_t size>  
errno_t _mbscat_s(  
   unsigned char (&strDestination)[size],  
   const unsigned char *strSource   
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 `strDestination`  
 Ukončené hodnotou Null cílové vyrovnávací paměti.  
  
 `numberOfElements`  
 Velikost cílové vyrovnávací paměti řetězců.  
  
 `strSource`  
 Vyrovnávací paměť řetězce ukončené hodnotou Null zdroje.  
  
## <a name="return-value"></a>Návratová hodnota  
 Nula v případě úspěšného; Kód chyby při selhání.  
  
### <a name="error-conditions"></a>Chybové stavy  
  
|`strDestination`|`numberOfElements`|`strSource`|Návratová hodnota|Obsah `strDestination`|  
|----------------------|------------------------|-----------------|------------------|----------------------------------|  
|`NULL` nebo neukončený|všechny|všechny|`EINVAL`|nedojde ke změně|  
|všechny|všechny|`NULL`|`EINVAL`|`strDestination`[0] nastaven na 0|  
|všechny|0, nebo příliš malá|všechny|`ERANGE`|`strDestination`[0] nastaven na 0|  
  
## <a name="remarks"></a>Poznámky  
 `strcat_s` Funkce připojí `strSource` k `strDestination` a ukončí výsledný řetězec s znak hodnoty null. Počáteční znak `strSource` přepíše ukončující znak null `strDestination`. Chování `strcat_s` není definován, pokud se překrývají zdrojové a cílové řetězce.  
  
 Všimněte si, že druhý parametr je celková velikost vyrovnávací paměti, ne podle zbývající velikosti:  
  
```  
char buf[16];  
strcpy_s(buf, 16, "Start");  
strcat_s(buf, 16, " End");               // Correct  
strcat_s(buf, 16 - strlen(buf), " End"); // Incorrect  
```  
  
 `wcscat_s` a `_mbscat_s` jsou široká charakterová a vícebajtových znaků verze `strcat_s`. Argumenty a vrací hodnotu `wcscat_s` jsou široká charakterová řetězce; u `_mbscat_s` jsou řetězců vícebajtových znaků. Tyto tři funkce chovají stejně jako jinak.  
  
 Pokud `strDestination` ukazatele null, nebo není ukončené hodnotou null, nebo pokud `strSource` je `NULL` ukazatele, nebo pokud cílový řetězec je příliš malá, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, tyto funkce vracejí `EINVAL` a nastavte `errno` k `EINVAL`.  
  
 V jazyce C++ pomocí těchto funkcí se zjednodušilo díky šabloně přetížení; přetížení automaticky odvození délka vyrovnávací paměti (takže není nutné zadat argument velikost) a starší, nezabezpečené funkce můžou automaticky nahradit se svými protějšky novější a zabezpečené. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).  
  
 Ladicí verze těchto funkcí nejprve vyplnit vyrovnávací paměť s 0xFD. Chcete-li toto chování zakázat, použijte [_crtsetdebugfillthreshold –](../../c-runtime-library/reference/crtsetdebugfillthreshold.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcscat_s`|`strcat_s`|`_mbscat_s`|`wcscat_s`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`strcat_s`|\<String.h >|  
|`wcscat_s`|\<String.h > nebo \<wchar.h >|  
|`_mbscat_s`|\<Mbstring.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad kódu v [strcpy_s – wcscpy_s –, _mbscpy_s –](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md).  
  
## <a name="see-also"></a>Viz také  
 [Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)   
 [strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)   
 [strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [strncpy –, _strncpy_l –, wcsncpy –, _wcsncpy_l –, _mbsncpy –, _mbsncpy_l –](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)   
 [_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [strspn, wcsspn, _mbsspn, _mbsspn_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)