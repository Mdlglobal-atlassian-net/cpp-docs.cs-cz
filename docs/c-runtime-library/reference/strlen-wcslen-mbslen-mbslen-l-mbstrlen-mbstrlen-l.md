---
title: "strlen –, wcslen –, _mbslen –, _mbslen_l –, _mbstrlen –, _mbstrlen_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbslen
- _mbslen_l
- _mbstrlen
- wcslen
- _mbstrlen_l
- strlen
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
- _mbstrlen
- wcslen
- _tcslen
- _ftcslen
- strlen
- _mbslen
dev_langs: C++
helpviewer_keywords:
- wcslen function
- string length, getting
- ftcslen function
- lengths, strings
- mbstrlen_l function
- _mbslen_l function
- _tcslen function
- mbslen_l function
- mbslen function
- _mbstrlen function
- strings [C++], getting length
- mbstrlen function
- _mbstrlen_l function
- _ftcslen function
- tcslen function
- strlen function
- _mbslen function
ms.assetid: 16462f2a-1e0f-4eb3-be55-bf1c83f374c2
caps.latest.revision: "32"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: faa9a7eee796bddcdfe67e43ced5e2f10c566bd7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="strlen-wcslen-mbslen-mbslenl-mbstrlen-mbstrlenl"></a>strlen –, wcslen –, _mbslen –, _mbslen_l –, _mbstrlen –, _mbstrlen_l –
Získá délku řetězce, pomocí aktuální národní prostředí nebo zadaný národní prostředí. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [strnlen –, strnlen_s –, wcsnlen –, wcsnlen_s –, _mbsnlen –, _mbsnlen_l –, _mbstrnlen –, _mbstrnlen_l –](../../c-runtime-library/reference/strnlen-strnlen-s.md)  
  
> [!IMPORTANT]
>  `_mbslen`, `_mbslen_l`, `_mbstrlen`, a `_mbstrlen_l` nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
size_t strlen(  
   const char *str  
);  
size_t wcslen(  
   const wchar_t *str   
);  
size_t _mbslen(  
   const unsigned char *str   
);  
size_t _mbslen_l(  
   const unsigned char *str,  
   _locale_t locale  
);  
size_t _mbstrlen(  
   const char *str  
);  
size_t _mbstrlen_l(  
   const char *str,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `str`  
 Řetězce ukončené hodnotou Null.  
  
 `locale`  
 Národní prostředí použít.  
  
## <a name="return-value"></a>Návratová hodnota  
 Každá z těchto funkcí vrátí počet znaků v `str`, s výjimkou terminálu `NULL`. Je vyhrazené žádnou návratovou hodnotu udávající chybu, s výjimkou `_mbstrlen` a `_mbstrlen_l`, které vrátí `((size_t)(-1))` Pokud řetězec obsahuje neplatný vícebajtových znaků.  
  
## <a name="remarks"></a>Poznámky  
 `strlen`řetězec interpretuje jako řetězec znaků jednobajtové, tak, aby hodnoty vždy počet bajtů, i v případě, že řetězec obsahuje více-bajtové znaky. `wcslen`široká charakterová verze `strlen`; argument `wcslen` je řetězec znaků celou a počet znaků je ve znacích celou (dva bajtů). `wcslen`a `strlen` chovat jinak shodně.  
  
 **Poznámka k zabezpečení** tyto funkce zpoplatněná potenciální hrozbu způsobené problém přetečení vyrovnávací paměti. Přetečení vyrovnávací paměti problémy jsou často metodu systému útoku, výsledkem bude vyplacena neoprávněně zvýšení úrovně oprávnění. Další informace najdete v tématu [zabraňující způsobí přetečení vyrovnávací paměti](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcslen`|`strlen`|`strlen`|`wcslen`|  
|`_tcsclen`|`strlen`|`_mbslen`|`wcslen`|  
|`_tcsclen_l`|`strlen`|`_mbslen_l`|`wcslen`|  
  
 `_mbslen`a `_mbslen_l` vrátí počet více-bajtové znaky v řetězci vícebajtových znaků, ale není testování pro platnosti vícebajtových znaků. `_mbstrlen`a `_mbstrlen_l` test platnosti vícebajtových znaků a rozpoznat sekvencí vícebajtových znaků. Pokud řetězec předaný `_mbstrlen` nebo `_mbstrlen_l` obsahuje neplatný znak vícebajtové znakové stránky, funkce vrátí hodnotu -1 a nastaví `errno` k `EILSEQ`.  
  
 Výstupní hodnota je ovlivňován nastavením `LC_CTYPE` kategorie nastavení národního prostředí; viz [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) Další informace. Verze tyto funkce bez `_l` příponu využívání aktuální národní prostředí pro toto chování závislých na národním prostředí, verze s `_l` příponu jsou shodné s tím rozdílem, že používají předaný v místo toho parametr národního prostředí. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`strlen`|\<String.h >|  
|`wcslen`|\<String.h > nebo \<wchar.h >|  
|`_mbslen`, `_mbslen_l`|\<Mbstring.h >|  
|`_mbstrlen`, `_mbstrlen_l`|\<stdlib.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_strlen.c  
// Determine the length of a string. For the multi-byte character  
// example to work correctly, the Japanese language support for  
// non-Unicode programs must be enabled by the operating system.  
  
#include <string.h>  
#include <locale.h>  
  
int main()  
{  
   char* str1 = "Count.";  
   wchar_t* wstr1 = L"Count.";  
   char * mbstr1;  
   char * locale_string;  
  
   // strlen gives the length of single-byte character string  
   printf("Length of '%s' : %d\n", str1, strlen(str1) );  
  
   // wstrlen gives the length of a wide character string  
   wprintf(L"Length of '%s' : %d\n", wstr1, wcslen(wstr1) );  
  
   // A multibyte string: [A] [B] [C] [katakana A] [D] [\0]  
   // in Code Page 932. For this example to work correctly,  
   // the Japanese language support must be enabled by the  
   // operating system.  
   mbstr1 = "ABC" "\x83\x40" "D";  
  
   locale_string = setlocale(LC_CTYPE, "Japanese_Japan");  
  
   if (locale_string == NULL)  
   {  
      printf("Japanese locale not enabled. Exiting.\n");  
      exit(1);  
   }  
   else  
   {  
      printf("Locale set to %s\n", locale_string);  
   }  
  
   // _mbslen will recognize the Japanese multibyte character if the  
   // current locale used by the operating system is Japanese  
   printf("Length of '%s' : %d\n", mbstr1, _mbslen(mbstr1) );  
  
   // _mbstrlen will recognize the Japanese multibyte character  
   // since the CRT locale is set to Japanese even if the OS locale  
   // isnot.   
   printf("Length of '%s' : %d\n", mbstr1, _mbstrlen(mbstr1) );  
   printf("Bytes in '%s' : %d\n", mbstr1, strlen(mbstr1) );     
  
}  
```  
  
```Output  
Length of 'Count.' : 6  
Length of 'Count.' : 6  
Length of 'ABCァD' : 5  
Length of 'ABCァD' : 5  
Bytes in 'ABCァD' : 6  
```  
  
## <a name="see-also"></a>Viz také  
 [Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)   
 [Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [setlocale –, _wsetlocale –](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strcat – wcscat –, _mbscat –](../../c-runtime-library/reference/strcat-wcscat-mbscat.md)   
 [strcmp – wcscmp –, _mbscmp –](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strcoll – funkce](../../c-runtime-library/strcoll-functions.md)   
 [strcpy – wcscpy –, _mbscpy –](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [strrchr –, wcsrchr –, _mbsrchr –, _mbsrchr_l –](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [_strset –, _strset_l –, _wcsset –, _wcsset_l –, _mbsset –, _mbsset_l –](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)   
 [strspn –, wcsspn –, _mbsspn –, _mbsspn_l –](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)