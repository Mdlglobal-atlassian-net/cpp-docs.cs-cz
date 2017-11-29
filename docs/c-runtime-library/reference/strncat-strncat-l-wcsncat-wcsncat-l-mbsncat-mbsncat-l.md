---
title: "strncat –, _strncat_l, wcsncat –, _wcsncat_l, _mbsncat –, _mbsncat_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- strncat
- _strncat_l
- _mbsncat
- _mbsncat_l
- wcsncat
- wcsncat_l
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
- _tcsncat_l
- _wcsncat_l
- _tcsnccat_l
- _mbsncat
- _strncat_l
- strncat
- _tcsnccat
- _mbsncat_l
- _ftcsncat
- wcsncat
- _tcsncat
dev_langs: C++
helpviewer_keywords:
- concatenating strings
- ftcsncat function
- tcsncat_l function
- _tcsnccat_l function
- _tcsncat function
- strncat function
- _ftcsncat function
- mbsncat function
- mbsncat_l function
- strings [C++], appending
- wcsncat function
- tcsnccat function
- tcsnccat_l function
- _tcsnccat function
- string concatenation [C++]
- appending strings
- characters [C++], appending to strings
- _mbsncat function
- _tcsncat_l function
- _mbsncat_l function
- tcsncat function
ms.assetid: de67363b-68c6-4ca5-91e3-478610ad8159
caps.latest.revision: "27"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 658c012461dab9a70672070689c9ddb0482028b7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="strncat-strncatl-wcsncat-wcsncatl-mbsncat-mbsncatl"></a>strncat –, _strncat_l, wcsncat –, _wcsncat_l, _mbsncat –, _mbsncat_l –
Připojí znaky řetězce. Bezpečnější verze tyto funkce jsou k dispozici, najdete v části [strncat_s –, _strncat_s_l, wcsncat_s –, _wcsncat_s_l, _mbsncat_s –, _mbsncat_s_l –](../../c-runtime-library/reference/strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md) .  
  
> [!IMPORTANT]
>  `_mbsncat`a `_mbsncat_l` nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
char *strncat(  
   char *strDest,  
   const char *strSource,  
   size_t count   
);  
wchar_t *wcsncat(  
   wchar_t *strDest,  
   const wchar_t *strSource,  
   size_t count   
);  
unsigned char *_mbsncat(  
   unsigned char *strDest,  
   const unsigned char *strSource,  
   size_t count  
);  
unsigned char *_mbsncat_l(  
   unsigned char *strDest,  
   const unsigned char *strSource,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
char *strncat(  
   char (&strDest)[size],  
   const char *strSource,  
   size_t count   
); // C++ only  
template <size_t size>  
wchar_t *wcsncat(  
   wchar_t (&strDest)[size],  
   const wchar_t *strSource,  
   size_t count   
); // C++ only  
template <size_t size>  
unsigned char *_mbsncat(  
   unsigned char (&strDest)[size],  
   const unsigned char *strSource,  
   size_t count  
); // C++ only  
template <size_t size>  
unsigned char *_mbsncat_l(  
   unsigned char (&strDest)[size],  
   const unsigned char *strSource,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 `strDest`  
 Řetězce ukončené hodnotou Null cílový.  
  
 `strSource`  
 Řetězce ukončené hodnotou Null zdroje.  
  
 `count`  
 Počet znaků pro připojení.  
  
 `locale`  
 Národní prostředí použít.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrací ukazatel na cílový řetězec. Žádnou návratovou hodnotu je vyhrazena indikující chybu.  
  
## <a name="remarks"></a>Poznámky  
 `strncat` Funkce připojí maximálně první `count` znaků `strSource` k `strDest`. Počáteční znak `strSource` přepíše ukončující znak null `strDest`. Pokud se objeví znak hodnoty null v `strSource` před `count` znaky jsou připojena, `strncat` připojí všechny znaky z `strSource`, až do znaku, hodnotu null. Pokud `count` je větší než délka `strSource`, délka `strSource` slouží místě `count`. Všechny případy, výsledný řetězec je byla ukončena s znak hodnoty null. Pokud kopírování probíhá mezi řetězce, které se překrývají, chování nedefinovaný.  
  
> [!IMPORTANT]
>  `strncat`nekontroluje dostatek místa v `strDest`; je proto potenciální příčinou přetečení vyrovnávací paměti. Mějte na paměti, `count` omezuje počet znaků připojí, nejedná se o omezení velikosti `strDest`. Podívejte se na téma níže uvedený příklad. Další informace najdete v tématu [zabraňující způsobí přetečení vyrovnávací paměti](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
 `wcsncat`a `_mbsncat` jsou široká charakterová a vícebajtových znaků verze `strncat`. Argumenty řetězce a návratová hodnota `wcsncat` jsou široká charakterová řetězce; u `_mbsncat` jsou řetězců vícebajtových znaků. Tyto tři funkce chovají stejně jako jinak.  
  
 Výstupní hodnota je ovlivňován nastavením `LC_CTYPE` kategorie nastavení národního prostředí; viz [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) Další informace. Verze tyto funkce bez `_l` příponu využívání aktuální národní prostředí pro toto chování závislých na národním prostředí, verze s `_l` příponu jsou shodné s tím rozdílem, že používají předaný v místo toho parametr národního prostředí. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
 V jazyce C++ tyto funkce mají přetížení šablony. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcsncat`|`strncat`|`_mbsnbcat`|`wcsncat`|  
|`_tcsncat_l`|`_strncat_l`|`_mbsnbcat_l`|`_wcsncat_l`|  
  
> [!NOTE]
>  `_strncat_l`a `_wcsncat_l` mít žádná závislost na národním prostředí a nejsou určeny k přímému volání. Jsou k dispozici pro interní použití rozhraním `_tcsncat_l`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`strncat`|\<String.h >|  
|`wcsncat`|\<String.h > nebo \<wchar.h >|  
|`_mbsncat`|\<Mbstring.h >|  
|`_mbsncat_l`|\<Mbstring.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_strncat.c  
// Use strcat and strncat to append to a string.  
#include <stdlib.h>  
  
#define MAXSTRINGLEN 39  
  
char string[MAXSTRINGLEN+1];  
// or char *string = malloc(MAXSTRINGLEN+1);  
  
void BadAppend( char suffix[], int n )  
{  
   strncat( string, suffix, n );  
}  
  
void GoodAppend( char suffix[], size_t n )  
{  
   strncat( string, suffix, __min( n, MAXSTRINGLEN-strlen(string)) );  
}  
  
int main( void )  
{  
   string[0] = '\0';  
   printf( "string can hold up to %d characters\n", MAXSTRINGLEN );  
  
   strcpy( string, "This is the initial string!" );  
   // concatenate up to 20 characters...  
   BadAppend( "Extra text to add to the string...", 20 );  
   printf( "After BadAppend :  %s (%d chars)\n", string, strlen(string) );  
  
   strcpy( string, "This is the initial string!" );  
   // concatenate up to 20 characters...  
   GoodAppend( "Extra text to add to the string...", 20 );  
   printf( "After GoodAppend:  %s (%d chars)\n", string, strlen(string) );  
}  
```  
  
## <a name="output"></a>Výstup  
  
```  
string can hold up to 39 characters  
After BadAppend :  This is the initial string!Extra text to add to (47 chars)  
After GoodAppend:  This is the initial string!Extra text t (39 chars)  
```  
  
 Všimněte si, že `BadAppend` způsobila přetečení vyrovnávací paměti.  
  
## <a name="see-also"></a>Viz také  
 [Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)   
 [_mbsnbcat –, _mbsnbcat_l –](../../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md)   
 [strcat – wcscat –, _mbscat –](../../c-runtime-library/reference/strcat-wcscat-mbscat.md)   
 [strcmp – wcscmp –, _mbscmp –](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strcpy – wcscpy –, _mbscpy –](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [strncmp –, wcsncmp –, _mbsncmp –, _mbsncmp_l –](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [strncpy –, _strncpy_l –, wcsncpy –, _wcsncpy_l –, _mbsncpy –, _mbsncpy_l –](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)   
 [_strnicmp –, _wcsnicmp –, _mbsnicmp –, _strnicmp_l –, _wcsnicmp_l –, _mbsnicmp_l –](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr –, wcsrchr –, _mbsrchr –, _mbsrchr_l –](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [_strset –, _strset_l –, _wcsset –, _wcsset_l –, _mbsset –, _mbsset_l –](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)   
 [strspn –, wcsspn –, _mbsspn –, _mbsspn_l –](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)   
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)