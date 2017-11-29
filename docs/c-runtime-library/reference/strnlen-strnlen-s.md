---
title: "strnlen –, strnlen_s –, wcsnlen –, wcsnlen_s –, _mbsnlen –, _mbsnlen_l –, _mbstrnlen –, _mbstrnlen_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- wcsnlen
- strnlen_s
- _mbstrnlen
- _mbsnlen_l
- _mbstrnlen_l
- strnlen
- wcsnlen_s
- _mbsnlen
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
- wcsnlen
- strnlen_s
- _mbsnlen
- _mbsnlen_l
- _tcsnlen
- _tcscnlen
- _mbstrnlen_l
- wcsnlen_s
- _mbstrnlen
- strnlen
- _tcscnlen_l
dev_langs: C++
helpviewer_keywords:
- _tcscnlen function
- _mbstrnlen function
- _mbsnlen_l function
- lengths, strings
- mbstrnlen function
- mbsnlen_l function
- _mbstrnlen_l function
- _tcscnlen_l function
- wcsnlen_l function
- _tcsnlen function
- _mbsnlen function
- strnlen function
- mbsnlen function
- wcsnlen_s function
- strnlen_s function
- mbstrnlen_l function
- wcsnlen function
- string length
- strnlen_l function
ms.assetid: cc05ce1c-72ea-4ae4-a7e7-4464e56e5f80
caps.latest.revision: "35"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0dfc872694485262386d0858e97b9835a2d507b3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="strnlen-strnlens-wcsnlen-wcsnlens-mbsnlen-mbsnlenl-mbstrnlen-mbstrnlenl"></a>strnlen –, strnlen_s –, wcsnlen –, wcsnlen_s –, _mbsnlen –, _mbsnlen_l –, _mbstrnlen –, _mbstrnlen_l –
Získá délku řetězce pomocí aktuální národní prostředí nebo ten, který byl předán v. Toto jsou bezpečnější verzích [strlen –, wcslen –, _mbslen –, _mbslen_l –, _mbstrlen –, _mbstrlen_l –](../../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md).  
  
> [!IMPORTANT]
>  `_mbsnlen`, `_mbsnlen_l`, `_mbstrnlen`, a `_mbstrnlen_l` nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
size_t strnlen(  
   const char *str,  
   size_t numberOfElements   
);  
size_t strnlen_s(  
   const char *str,  
   size_t numberOfElements   
);  
size_t wcsnlen(  
   const wchar_t *str,  
   size_t numberOfElements  
);  
size_t wcsnlen_s(  
   const wchar_t *str,  
   size_t numberOfElements  
);  
size_t _mbsnlen(  
   const unsigned char *str,  
   size_t numberOfElements  
);  
size_t _mbsnlen_l(  
   const unsigned char *str,  
   size_t numberOfElements,  
   _locale_t locale  
);  
size_t _mbstrnlen(  
   const char *str,  
   size_t numberOfElements  
);  
size_t _mbstrnlen_l(  
   const char *str,  
   size_t numberOfElements,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `str`  
 Řetězce ukončené hodnotou Null.  
  
 `numberOfElements`  
 Velikost vyrovnávací paměti řetězců.  
  
 `locale`  
 Národní prostředí použít.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tyto funkce vrátí počet znaků v řetězci, není včetně ukončující znak hodnoty null. Pokud je null nebyl v rámci první `numberOfElements` bajtů řetězce (nebo široké znaky pro `wcsnlen`), pak `numberOfElements` se vrátí k označení chybový stav; délky, které jsou striktně menší než mítřetězceukončenéhodnotounull`numberOfElements`.  
  
 `_mbstrnlen`a `_mbstrnlen_l` vrátí hodnotu -1, pokud řetězec obsahuje neplatný vícebajtových znaků.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  `strnlen`není to náhrada za `strlen`; `strnlen` je určena pro použití pouze k výpočtu velikosti příchozí nedůvěryhodné dat do vyrovnávací paměti o velikosti známé – například síťového paketu. `strnlen`Vypočítá délku, ale není provede za koncem vyrovnávací paměti, zda je řetězec neukončený. Pro další případy použití `strlen`. (Totéž platí i pro `wcsnlen`, `_mbsnlen`, a `_mbstrnlen`.)  
  
 Každá z těchto funkcí vrátí počet znaků v `str`, není včetně ukončující znak hodnoty null. Ale `strnlen` a `strnlen_s` interpretovat řetězec jako řetězec znaků jednobajtové a proto návratovou hodnotu se vždy rovná počet bajtů, i v případě, že řetězec obsahuje více-bajtové znaky. `wcsnlen`a `wcsnlen_s` jsou verze široká charakterová `strnlen` a `strnlen_s` ; argumenty pro `wcsnlen` a `wcsnlen_s` jsou široká charakterová řetězce a počet znaků v jednotkách široká charakterová. V opačném `wcsnlen` a `strnlen` chovají stejně jako, stejně jako `strnlen_s` a `wcsnlen_s`.  
  
 `strnlen`, `wcsnlen`, a `_mbsnlen` neověřují jejich parametrů. Pokud `str` je `NULL`, dojde k porušení přístupu.  
  
 `strnlen_s`a `wcsnlen_s` ověřit jejich parametrů. Pokud `str` je `NULL`, funkce vrátí 0.  
  
 `_mbstrnlen`zároveň ověří jeho parametry. Pokud `str` je `NULL`, nebo pokud `numberOfElements` je větší než `INT_MAX`, `_mbstrnlen` vygeneruje výjimku neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění `_mbstrnlen` nastaví `errno` k `EINVAL` a vrátí hodnotu -1.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcsnlen`|`strnlen`|`strnlen`|`wcsnlen`|  
|`_tcscnlen`|`strnlen`|`_mbsnlen`|`wcsnlen`|  
|`_tcscnlen_l`|`strnlen`|`_mbsnlen_l`|`wcsnlen`|  
  
 `_mbsnlen`a `_mbstrnlen` vrátí počet více-bajtové znaky v řetězci vícebajtových znaků. `_mbsnlen`rozpozná sekvencí vícebajtových znaků podle vícebajtové znakové stránky, který je aktuálně používán nebo podle národního prostředí, který se předává v; je testování pro platnosti vícebajtových znaků. `_mbstrnlen`testů pro platnosti vícebajtových znaků a rozpozná sekvencí vícebajtových znaků. Pokud řetězec, který je předán `_mbstrnlen` obsahuje neplatný znak vícebajtové, `errno` je nastaven na `EILSEQ`.  
  
 Výstupní hodnota je ovlivňován nastavením `LC_CTYPE` kategorie nastavení národního prostředí; viz [setlocale _wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) Další informace. Verze tyto funkce jsou identické, s tím rozdílem, že ty, které nejsou mít `_l` příponu použít aktuální národní prostředí pro toto chování závislých na národním prostředí a verzí, které mají `_l` příponu, použijte parametr národního prostředí to je Předaná. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`strnlen`, `strnlen_s`|\<String.h >|  
|`wcsnlen`, `wcsnlen_s`|\<String.h > nebo \<wchar.h >|  
|`_mbsnlen`, `_mbsnlen_l`|\<Mbstring.h >|  
|`_mbstrnlen`, `_mbstrnlen_l`|\<stdlib.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```C  
// crt_strnlen.c  
  
#include <string.h>  
  
int main()  
{  
   // str1 is 82 characters long. str2 is 159 characters long   
  
   char* str1 = "The length of a string is the number of characters\n"  
               "excluding the terminating null.";  
   char* str2 = "strnlen takes a maximum size. If the string is longer\n"  
                "than the maximum size specified, the maximum size is\n"  
                "returned rather than the actual size of the string.";  
   size_t len;  
   size_t maxsize = 100;  
  
   len = strnlen(str1, maxsize);  
   printf("%s\n Length: %d \n\n", str1, len);  
  
   len = strnlen(str2, maxsize);  
   printf("%s\n Length: %d \n", str2, len);  
}  
```  
  
```Output  
The length of a string is the number of characters  
excluding the terminating null.  
 Length: 82   
  
strnlen takes a maximum size. If the string is longer  
than the maximum size specified, the maximum size is  
returned rather than the actual size of the string.  
 Length: 100   
```  
  
## <a name="see-also"></a>Viz také  
 [Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)   
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [setlocale –, _wsetlocale –](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strncat –, _strncat_l, wcsncat –, _wcsncat_l, _mbsncat –, _mbsncat_l –](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)   
 [strncmp –, wcsncmp –, _mbsncmp –, _mbsncmp_l –](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [strcoll – funkce](../../c-runtime-library/strcoll-functions.md)   
 [strncpy_s –, _strncpy_s_l –, wcsncpy_s –, _wcsncpy_s_l –, _mbsncpy_s, _mbsncpy_s_l](../../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)   
 [strrchr –, wcsrchr –, _mbsrchr –, _mbsrchr_l –](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [_strset –, _strset_l –, _wcsset –, _wcsset_l –, _mbsset –, _mbsset_l –](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)   
 [strspn –, wcsspn –, _mbsspn –, _mbsspn_l –](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)