---
title: "strrchr –, wcsrchr –, _mbsrchr –, _mbsrchr_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- strrchr
- wcsrchr
- _mbsrchr
- _mbsrchr_l
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tcsrchr
- _ftcsrchr
- strrchr
- wcsrchr
- _mbsrchr
dev_langs:
- C++
helpviewer_keywords:
- _mbsrchr function
- tcsrchr function
- mbsrchr_l function
- characters [C++], scanning for
- ftcsrchr function
- _tcsrchr function
- strings [C++], scanning
- mbsrchr function
- strrchr function
- scanning strings
- wcsrchr function
- _ftcsrchr function
- _mbsrchr_l function
ms.assetid: 75cf2664-758e-49bb-bf6b-8a139cd474d2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2381a38dcf3532d50611068811e94101a3512746
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="strrchr-wcsrchr-mbsrchr-mbsrchrl"></a>strrchr, wcsrchr, _mbsrchr, _mbsrchr_l
Prohledá řetězec pro poslední výskyt znaku.  
  
> [!IMPORTANT]
>  `_mbsrchr` a `_mbsrchr_l` nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
char *strrchr(  
   const char *str,  
   int c   
); // C only  
char *strrchr(  
   char *str,  
   int c   
); // C++ only  
const char *strrchr(  
   const char *str,  
   int c   
); // C++ only  
wchar_t *wcsrchr(  
   const wchar_t *str,  
   wchar_t c   
); // C only  
wchar_t *wcsrchr(  
   wchar_t *str,  
   wchar_t c   
); // C++ only  
const wchar_t *wcsrchr(  
   const wchar_t *str,  
   wchar_t c   
); // C++ only  
unsigned char *_mbsrchr(  
   const unsigned char *str,  
   unsigned int c   
); // C only  
unsigned char *_mbsrchr(  
   unsigned char *str,  
   unsigned int c   
); // C++ only  
const unsigned char *_mbsrchr(  
   const unsigned char *str,  
   unsigned int c   
); // C++ only  
unsigned char *_mbsrchr_l(  
   const unsigned char *str,  
   unsigned int c,  
   _locale_t locale  
); // C only  
unsigned char *_mbsrchr_l(  
   unsigned char *str,  
   unsigned int c,  
   _locale_t locale  
); // C++ only  
const unsigned char *_mbsrchr_l(  
   const unsigned char *str,  
   unsigned int c,  
   _locale_t locale  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 `str`  
 Řetězce ukončené hodnotou Null pro vyhledávání.  
  
 `c`  
 Znak, který má být umístěn.  
  
 `locale`  
 Národní prostředí použít.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrací ukazatel na posledním výskytem `c` v `str`, nebo `NULL` Pokud `c` nebyl nalezen.  
  
## <a name="remarks"></a>Poznámky  
 `strrchr` Funkce vyhledá poslední výskyt `c` (převést na `char`) v `str`. Hledání zahrnuje ukončující znak hodnoty null.  
  
 `wcsrchr` a `_mbsrchr` jsou široká charakterová a vícebajtových znaků verze `strrchr`. Argumenty a vrací hodnotu `wcsrchr` jsou široká charakterová řetězce; u `_mbsrchr` jsou řetězců vícebajtových znaků.  
  
 V jazyce C, proveďte tyto funkce `const` pro první argument ukazatel. V jazyce C++ jsou k dispozici dva přetížení. Přetížení trvá ukazatel na `const` vrací ukazatel na `const`; na verzi, která přebírá ukazatel na jinou hodnotu než`const` vrací ukazatel na jinou hodnotu než`const`. Makro `_CRT_CONST_CORRECT_OVERLOADS` je definována, pokud obě `const` a jiných-`const` verze tyto funkce jsou k dispozici. Pokud budete potřebovat jinou hodnotu než`const` chování pro obě přetížení C++ definujte symbol `_CONST_RETURN`.  
  
 `_mbsrchr` ověří jeho parametry. Pokud `str` je `NULL`, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění `errno` je nastaven na `EINVAL` a `_mbsrchr` vrátí hodnotu 0. `strrchr` a `wcsrchr` neověřují jejich parametrů. Tyto tři funkce chovají stejně jako jinak.  
  
 Výstupní hodnota je ovlivňován nastavením `LC_CTYPE` kategorie nastavení národního prostředí; Další informace najdete v části [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md). Verze tyto funkce bez `_l` příponu využívání aktuální národní prostředí pro toto chování závislých na národním prostředí, verze s `_l` příponu jsou shodné s tím rozdílem, že používají předaný v místo toho parametr národního prostředí. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcsrchr`|`strrchr`|`_mbsrchr`|`wcsrchr`|  
|**n/a**|**n/a**|`_mbsrchr_l`|**n/a**|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`strrchr`|\<String.h >|  
|`wcsrchr`|\<String.h > nebo \<wchar.h >|  
|`_mbsrchr`, `_mbsrchr_l`|\<Mbstring.h >|  
  
 Další informace o kompatibilitě najdete v tématu [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
 Příklad použití `strrchr`, najdete v části [strchr –](../../c-runtime-library/reference/strchr-wcschr-mbschr-mbschr-l.md).  
  
## <a name="see-also"></a>Viz také  
 [Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)   
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [strchr, wcschr, _mbschr, _mbschr_l](../../c-runtime-library/reference/strchr-wcschr-mbschr-mbschr-l.md)   
 [strcspn, wcscspn, _mbscspn, _mbscspn_l](../../c-runtime-library/reference/strcspn-wcscspn-mbscspn-mbscspn-l.md)   
 [_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l](../../c-runtime-library/reference/strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)   
 [strspn, wcsspn, _mbsspn, _mbsspn_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)