---
title: "_stricmp –, _wcsicmp –, _mbsicmp –, _stricmp_l –, _wcsicmp_l –, _mbsicmp_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _stricmp_l
- _mbsicmp
- _wcsicmp
- _mbsicmp_l
- _stricmp
- _wcsicmp_l
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
- ntoskrnl.exe
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _ftcsicmp
- _stricmp
- wcsicmp_l
- _wcsicmp
- _tcsicmp
- _strcmpi
- stricmp_l
- _mbsicmp
- _fstricmp
- mbsicmp_l
- mbsicmp
dev_langs: C++
helpviewer_keywords:
- _wcsicmp function
- _stricmp_l function
- fstricmp function
- _tcsicmp function
- ftcsicmp function
- string comparison [C++], lowercase
- _wcsicmp_l function
- _fstricmp function
- strings [C++], comparing
- mbsicmp function
- _ftcsicmp function
- _mbsicmp_l function
- wcsicmp_l function
- _stricmp function
- _mbsicmp function
- tcsicmp function
- stricmp_l function
- mbsicmp_l function
- _strcmpi function
ms.assetid: 0e1ee515-0d75-435a-a445-8875d4669b50
caps.latest.revision: "28"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 15b581d0d47da824f1faaade1214d1320e29bb03
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="stricmp-wcsicmp-mbsicmp-stricmpl-wcsicmpl-mbsicmpl"></a>_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l
Provede porovnávání řetězců.  
  
> [!IMPORTANT]
>  `_mbsicmp`a `_mbsicmp_l` nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _stricmp(  
   const char *string1,  
   const char *string2   
);  
int _wcsicmp(  
   const wchar_t *string1,  
   const wchar_t *string2   
);  
int _mbsicmp(  
   const unsigned char *string1,  
   const unsigned char *string2   
);  
int _stricmp_l(  
   const char *string1,  
   const char *string2,  
   _locale_t locale  
);  
int _wcsicmp_l(  
   const wchar_t *string1,  
   const wchar_t *string2,  
   _locale_t locale  
);  
int _mbsicmp_l(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `string1, string2`  
 Řetězce ukončené hodnotou Null pro porovnání.  
  
 `locale`  
 Národní prostředí použít.  
  
## <a name="return-value"></a>Návratová hodnota  
 Návratová hodnota označuje vztah z `string1` k `string2` následujícím způsobem.  
  
|Návratová hodnota|Popis|  
|------------------|-----------------|  
|< 0|`string1`menší než`string2`|  
|0|`string1`stejný jako`string2`|  
|> 0|`string1`větší než`string2`|  
  
 Při chybě `_mbsicmp` vrátí `_NLSCMPERROR`, která je definována v \<string.h > a \<mbstring.h >.  
  
## <a name="remarks"></a>Poznámky  
 `_stricmp` Funkce ordinally porovná `string1` a `string2` po převodu každý znak na malá a vrátí hodnotu, která určuje jejich vztahu. `_stricmp`se liší od `_stricoll` v tom, že `_stricmp` porovnání pouze ovlivněné `LC_CTYPE`, která určuje, jaké znaky jsou malá a velká písmena. `_stricoll` Funkce porovná řetězce podle i `LC_CTYPE` a `LC_COLLATE` kategorie národního prostředí, včetně případu a pořadí kolace. Další informace o `LC_COLLATE` kategorie, najdete v části [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) a [kategorie národního prostředí](../../c-runtime-library/locale-categories.md). Verze tyto funkce bez `_l` příponu použít aktuální národní prostředí pro chování závislých na národním prostředí. Verze s příponou jsou identické s tím rozdílem, že používají místo předaná národní prostředí. Pokud nebyla nastavena jako národní prostředí, použije se národní prostředí C. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
> [!NOTE]
>  `_stricmp`je ekvivalentní `_strcmpi`. Použitím zcela zaměnitelným významem, ale `_stricmp` je upřednostňovaný standard.  
  
 `_strcmpi` Funkce je ekvivalentní volání `_stricmp` a se poskytuje pouze z důvodů zpětné kompatibility.  
  
 Protože `_stricmp` malá písmena porovnání, může vést k neočekávanému chování.  
  
 Pro ilustraci při případ převodu pomocí `_stricmp` ovlivňuje výsledek porovnání, předpokládá, že máte dva řetězce JOHNSTONŮV a JOHN_HENRY. JOHNSTONŮV řetězec JOHN_HENRY bude považovat za méně než protože "_" má na nižší hodnotu než malá S. ASCII Ve skutečnosti libovolný znak, který má hodnotu ASCII mezi 91 a 96 bude považovat za méně než jakékoli písmeno.  
  
 Pokud [strcmp –](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md) místo je použita funkce `_stricmp`, JOHN_HENRY bude větší než JOHNSTONŮV.  
  
 `_wcsicmp`a `_mbsicmp` jsou široká charakterová a vícebajtových znaků verze `_stricmp`. Argumenty a vrací hodnotu `_wcsicmp` jsou široká charakterová řetězce; u `_mbsicmp` jsou řetězců vícebajtových znaků. `_mbsicmp`rozpozná sekvencí vícebajtových znaků podle aktuální vícebajtové znakové stránky a vrátí `_NLSCMPERROR` na chybu. Další informace najdete v tématu [znakové stránky](../../c-runtime-library/code-pages.md). Tyto tři funkce chovají stejně jako jinak.  
  
 `_wcsicmp`a `wcscmp` vyjma toho, že se chovají stejně jako `wcscmp` není převedena na malá písmena před porovnáním je její argumenty. `_mbsicmp`a `_mbscmp` vyjma toho, že se chovají stejně jako `_mbscmp` není převedena na malá písmena před porovnáním je její argumenty.  
  
 Je třeba volat [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) pro `_wcsicmp` pro práci s znaky latinky 1. Národní prostředí C je platí ve výchozím nastavení, tedy například ä nebude porovnat rovna Ä. Volání `setlocale` s kterémkoli národním prostředí než C národní prostředí před voláním `_wcsicmp`. Následující příklad ukazuje, jak `_wcsicmp` je citlivá na národní prostředí:  
  
```  
// crt_stricmp_locale.c  
#include <string.h>  
#include <stdio.h>  
#include <locale.h>  
  
int main() {  
   setlocale(LC_ALL,"C");   // in effect by default  
   printf("\n%d",_wcsicmp(L"ä", L"Ä"));   // compare fails  
   setlocale(LC_ALL,"");  
   printf("\n%d",_wcsicmp(L"ä", L"Ä"));   // compare succeeds  
}  
```  
  
 Alternativou je volat [_create_locale –, _wcreate_locale](../../c-runtime-library/reference/create-locale-wcreate-locale.md) a předejte jako parametr pro objekt vrácený národního prostředí `_wcsicmp_l`.  
  
 Všechny tyto funkce ověřit jejich parametrů. Pokud má jedna `string1` nebo `string2` jsou ukazatelé s hodnotou null, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md) . Pokud je povoleno spuštění chcete-li pokračovat, tyto funkce vracejí `_NLSCMPERROR` a nastavte `errno` k `EINVAL`.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcsicmp`|`_stricmp`|`_mbsicmp`|`_wcsicmp`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_stricmp`, `_stricmp_l`|\<String.h >|  
|`_wcsicmp`, `_wcsicmp_l`|\<String.h > nebo \<wchar.h >|  
|`_mbsicmp`, `_mbsicmp_l`|\<Mbstring.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_stricmp.c  
  
#include <string.h>  
#include <stdio.h>  
#include <stdlib.h>  
  
char string1[] = "The quick brown dog jumps over the lazy fox";  
char string2[] = "The QUICK brown dog jumps over the lazy fox";  
  
int main( void )  
{  
   char tmp[20];  
   int result;  
  
   // Case sensitive  
   printf( "Compare strings:\n   %s\n   %s\n\n", string1, string2 );  
   result = strcmp( string1, string2 );  
   if( result > 0 )  
      strcpy_s( tmp, _countof(tmp), "greater than" );  
   else if( result < 0 )  
      strcpy_s( tmp, _countof(tmp), "less than" );  
   else  
      strcpy_s( tmp, _countof(tmp), "equal to" );  
   printf( "   strcmp:   String 1 is %s string 2\n", tmp );  
  
   // Case insensitive (could use equivalent _stricmp)  
   result = _stricmp( string1, string2 );  
   if( result > 0 )  
      strcpy_s( tmp, _countof(tmp), "greater than" );  
   else if( result < 0 )  
      strcpy_s( tmp, _countof(tmp), "less than" );  
   else  
      strcpy_s( tmp, _countof(tmp), "equal to" );  
   printf( "   _stricmp:  String 1 is %s string 2\n", tmp );  
}  
```  
  
```Output  
Compare strings:  
   The quick brown dog jumps over the lazy fox  
   The QUICK brown dog jumps over the lazy fox  
  
   strcmp:   String 1 is greater than string 2  
   _stricmp:  String 1 is equal to string 2  
```  
  
## <a name="see-also"></a>Viz také  
 [Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)   
 [memcmp wmemcmp –](../../c-runtime-library/reference/memcmp-wmemcmp.md)   
 [_memicmp –, _memicmp_l –](../../c-runtime-library/reference/memicmp-memicmp-l.md)   
 [strcmp – wcscmp –, _mbscmp –](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strcoll – funkce](../../c-runtime-library/strcoll-functions.md)   
 [strncmp –, wcsncmp –, _mbsncmp –, _mbsncmp_l –](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [_strnicmp –, _wcsnicmp –, _mbsnicmp –, _strnicmp_l –, _wcsnicmp_l –, _mbsnicmp_l –](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr –, wcsrchr –, _mbsrchr –, _mbsrchr_l –](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [_strset –, _strset_l –, _wcsset –, _wcsset_l –, _mbsset –, _mbsset_l –](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)   
 [strspn, wcsspn, _mbsspn, _mbsspn_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)