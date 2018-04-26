---
title: mbstowcs –, _mbstowcs_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
f1_keywords:
- mbstowcs
dev_langs:
- C++
helpviewer_keywords:
- _mbstowcs_l function
- mbstowcs_l function
- mbstowcs function
ms.assetid: 96696b27-e068-4eeb-8006-3f7a0546ae6d
caps.latest.revision: 30
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cd81ff7e082dbb35b8ea05f1e60f88fda2b86f0c
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="mbstowcs-mbstowcsl"></a>mbstowcs, _mbstowcs_l

Převede posloupnost více-bajtové znaky na odpovídající posloupnost široké znaky. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [mbstowcs_s –, _mbstowcs_s_l –](mbstowcs-s-mbstowcs-s-l.md).

## <a name="syntax"></a>Syntaxe

```C
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

### <a name="parameters"></a>Parametry

*wcstr*<br/>
Adresa posloupnost široké znaky.

*mbstr*<br/>
Adresu pořadí Null byla ukončena více-bajtové znaky.

*Počet*<br/>
Maximální počet více-bajtové znaky převést.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Pokud **mbstowcs –** úspěšně převede zdrojový řetězec, vrátí počet převedený více-bajtové znaky. Pokud *wcstr* argument je **NULL**, funkce vrátí hodnotu požadovaná velikost (v široké znaky) cílové řetězce. Pokud **mbstowcs –** zaznamená neplatný vícebajtových znaků, vrátí hodnotu -1. Pokud je vrácenou hodnotou *počet*, není široká charakterová řetězce ukončené hodnotou null.

> [!IMPORTANT]
> Ujistěte se, že *wcstr* a *mbstr* se nepřekrývají a že *počet* správně odpovídá počtu více-bajtové znaky převést.

## <a name="remarks"></a>Poznámky

**Mbstowcs –** funkce převede až do maximální počet *počet* více-bajtové znaky na kterou odkazuje *mbstr* na řetězec odpovídající široké znaky, které jsou Určuje aktuální národní prostředí. Ukládá výsledný řetězec široká charakterová na adrese reprezentována *wcstr*. Výsledkem je podobná řadu volání [mbtowc –](mbtowc-mbtowc-l.md). Pokud **mbstowcs –** zaznamená znak hodnoty null jednobajtové (\0) před nebo po *počet* dojde, převede ji hodnotu null znak, který má prázdný znak široká charakterová (L '\0') a zastaví. Proto široká charakterová řetězce na *wcstr* je ukončené hodnotou null jenom v případě, že je během převodu došlo k znak hodnoty null. Pokud daná pořadí na kterou odkazuje *wcstr* a *mbstr* překrývají, chování není definován.

Pokud *wcstr* argument je **NULL**, **mbstowcs –** vrátí počet široké znaky, které by mohly být výsledkem převodu není včetně zakončením hodnotu null. Zdrojový řetězec musí být ukončen null pro správnou hodnotu, která má být vrácen. Pokud potřebujete výsledné široká znaková řetězec, který má být ukončené hodnotou null, přidejte jednu pro vrácené hodnoty.

Pokud *mbstr* argument je **NULL**, nebo pokud *počet* je > **INT_MAX**, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ Ověření parametru](../../c-runtime-library/parameter-validation.md) . Pokud je povoleno provádění pokračovat, kód chyby je nastavena na **einval –** a funkce vrátí hodnotu -1.

**mbstowcs –** používá aktuální národní prostředí pro chování všech závislých na národním prostředí; **_mbstowcs_l –** se shoduje s tím rozdílem, že používá národní prostředí předaná místo. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).

V jazyce C++ tyto funkce mají šabloně přetížení, které vyvolání novější a zabezpečené svými protějšky tyto funkce. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**mbstowcs –**|\<stdlib.h>|
|**_mbstowcs_l**|\<stdlib.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
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
    printf("   Required Size: %d\n", requiredSize);

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
    printf( "   Number of bytes written to multibyte string: %u\n",
            (unsigned int) size );
    printf( "   Hex values of the" );
    printf( " multibyte characters: %#.2x %#.2x %#.2x %#.2x\n",
            pmbhello[0], pmbhello[1], pmbhello[2], pmbhello[3] );
    printf( "   Codepage 932 uses 0x81 to 0x9f as lead bytes.\n\n");

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
    printf( "   Characters converted: %u\n", (unsigned int)size );
    printf( "   Hex value of first 2" );
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

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072)<br/>
