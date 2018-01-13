---
title: "mbstowcs –, _mbstowcs_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- mbstowcs
- _mbstowcs_l
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords: mbstowcs
dev_langs: C++
helpviewer_keywords:
- _mbstowcs_l function
- mbstowcs_l function
- mbstowcs function
ms.assetid: 96696b27-e068-4eeb-8006-3f7a0546ae6d
caps.latest.revision: "30"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 63036262536adea68a4c44bde735a48b2f896b5f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="mbstowcs-mbstowcsl"></a>mbstowcs, _mbstowcs_l
Převede posloupnost více-bajtové znaky na odpovídající posloupnost široké znaky. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [mbstowcs_s –, _mbstowcs_s_l –](../../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
size_t mbstowcs(  
   wchar_t *wcstr,  
   const char *mbstr,  
   size_t count   
);  
size_t _mbstowcs_l(  
   wchar_t *wcstr,  
   const char *mbstr,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
size_t mbstowcs(  
   wchar_t (&wcstr)[size],  
   const char *mbstr,  
   size_t count   
); // C++ only  
template <size_t size>  
size_t _mbstowcs_l(  
   wchar_t (&wcstr)[size],  
   const char *mbstr,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 [out]`wcstr`  
 Adresa posloupnost široké znaky.  
  
 [v]`mbstr`  
 Adresu pořadí Null byla ukončena více-bajtové znaky.  
  
 [v]`count`  
 Maximální počet více-bajtové znaky převést.  
  
 [v]`locale`  
 Národní prostředí, které se má použít  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud `mbstowcs` úspěšně převede zdrojový řetězec, vrátí počet převedený více-bajtové znaky. Pokud `wcstr` argument je `NULL`, funkce vrátí hodnotu požadovaná velikost (v široké znaky) cílové řetězce. Pokud `mbstowcs` zaznamená neplatný vícebajtových znaků, vrátí hodnotu -1. Pokud je vrácenou hodnotou `count`, není široká charakterová řetězce ukončené hodnotou null.  
  
> [!IMPORTANT]
>  Ujistěte se, že `wcstr` a `mbstr` se nepřekrývají a že `count` správně odpovídá počtu více-bajtové znaky převést.  
  
## <a name="remarks"></a>Poznámky  
 `mbstowcs` Funkce převede až do maximální počet `count` více-bajtové znaky na kterou odkazuje `mbstr` na řetězec odpovídající široké znaky, které vyplývají z aktuální národní prostředí. Ukládá výsledný řetězec široká charakterová na adrese reprezentována `wcstr`. Výsledkem je podobná řadu volání `mbtowc`. Pokud `mbstowcs` zaznamená znak hodnoty null jednobajtové (\0) před nebo po `count` dojde, převede ji hodnotu null znak, který má prázdný znak široká charakterová (L '\0') a zastaví. Proto široká charakterová řetězce na `wcstr` je ukončené hodnotou null jenom v případě, že je během převodu došlo k znak hodnoty null. Pokud daná pořadí na kterou odkazuje `wcstr` a `mbstr` překrývají, chování není definován.  
  
 Pokud `wcstr` argument je `NULL`, `mbstowcs` vrátí počet široké znaky, které by mohly být výsledkem převodu není včetně zakončením hodnotu null. Zdrojový řetězec musí být ukončen null pro správnou hodnotu, která má být vrácen. Pokud potřebujete výsledné široká znaková řetězec, který má být ukončené hodnotou null, přidejte jednu pro vrácené hodnoty.  
  
 Pokud `mbstr` argument je `NULL`, nebo pokud `count` je > `INT_MAX`, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md) . Pokud je povoleno provádění pokračovat, kód chyby je nastavena na `EINVAL` a funkce vrátí hodnotu -1.  
  
 `mbstowcs`používá aktuální národní prostředí pro chování všech závislých na národním prostředí; `_mbstowcs_l` se shoduje s tím rozdílem, že používá národní prostředí předaná místo. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
 V jazyce C++ tyto funkce mají šabloně přetížení, které vyvolání novější a zabezpečené svými protějšky tyto funkce. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`mbstowcs`|\<stdlib.h >|  
|`_mbstowcs_l`|\<stdlib.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_mbstowcs.c  
// compile with: /W3  
// illustrates the behavior of the mbstowcs function  
  
#include <stdlib.h>  
#include <stdio.h>  
#include <locale.h>  
  
int main( void )  
{  
    size_t size;  
    int nChar = 2; // number of characters to convert  
    int requiredSize;  
  
    unsigned char    *pmbnull  = NULL;  
    unsigned char    *pmbhello = NULL;  
    char* localeInfo;  
  
    wchar_t *pwchello = L"\x3042\x3043"; // 2 Hiragana characters  
    wchar_t *pwc;  
  
    /* Enable the Japanese locale and codepage */  
    localeInfo = setlocale(LC_ALL, "Japanese_Japan.932");  
    printf("Locale information set to %s\n", localeInfo);  
  
    printf( "Convert to multibyte string:\n" );  
  
    requiredSize = wcstombs( NULL, pwchello, 0); // C4996  
    // Note: wcstombs is deprecated; consider using wcstombs_s  
    printf("  Required Size: %d\n", requiredSize);  
  
    /* Add one to leave room for the null terminator. */  
    pmbhello = (unsigned char *)malloc( requiredSize + 1);  
    if (! pmbhello)  
    {  
        printf("Memory allocation failure.\n");  
        return 1;  
    }  
    size = wcstombs( pmbhello, pwchello, requiredSize + 1); // C4996  
    // Note: wcstombs is deprecated; consider using wcstombs_s  
    if (size == (size_t) (-1))  
    {  
        printf("Couldn't convert string. Code page 932 may"  
                " not be available.\n");  
        return 1;  
    }  
    printf( "  Number of bytes written to multibyte string: %u\n",  
            (unsigned int) size );  
    printf( "  Hex values of the " );  
    printf( " multibyte characters: %#.2x %#.2x %#.2x %#.2x\n",  
            pmbhello[0], pmbhello[1], pmbhello[2], pmbhello[3] );  
    printf( "  Codepage 932 uses 0x81 to 0x9f as lead bytes.\n\n");  
  
    printf( "Convert back to wide-character string:\n" );  
  
    /* Assume we don't know the length of the multibyte string.  
     Get the required size in characters, and allocate enough space. */  
  
    requiredSize = mbstowcs(NULL, pmbhello, 0); // C4996  
    /* Add one to leave room for the NULL terminator */  
    pwc = (wchar_t *)malloc( (requiredSize + 1) * sizeof( wchar_t ));  
    if (! pwc)  
    {  
        printf("Memory allocation failure.\n");  
        return 1;  
    }  
    size = mbstowcs( pwc, pmbhello, requiredSize + 1); // C4996  
    if (size == (size_t) (-1))  
    {  
       printf("Couldn't convert string--invalid multibyte character.\n");  
    }  
    printf( "  Characters converted: %u\n", (unsigned int)size );  
    printf( "  Hex value of first 2" );  
    printf( " wide characters: %#.4x %#.4x\n\n", pwc[0], pwc[1] );  
    free(pwc);  
    free(pmbhello);  
}  
```  
  
```Output  
Locale information set to Japanese_Japan.932  
Convert to multibyte string:  
  Required Size: 4  
  Number of bytes written to multibyte string: 4  
  Hex values of the  multibyte characters: 0x82 0xa0 0x82 0xa1  
  Codepage 932 uses 0x81 to 0x9f as lead bytes.  
  
Convert back to wide-character string:  
  Characters converted: 2  
  Hex value of first 2 wide characters: 0x3042 0x3043  
```  
  
## <a name="see-also"></a>Viz také  
 [Převod dat](../../c-runtime-library/data-conversion.md)   
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [_mbclen – mblen –, _mblen_l –](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [mbtowc –, _mbtowc_l –](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [wcstombs –, _wcstombs_l –](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [wctomb –, _wctomb_l –](../../c-runtime-library/reference/wctomb-wctomb-l.md)   
 [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072)