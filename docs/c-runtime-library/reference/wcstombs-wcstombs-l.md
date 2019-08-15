---
title: wcstombs, _wcstombs_l
ms.date: 11/04/2016
apiname:
- wcstombs
- _wcstombs_l
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- wcstombs
- _wcstombs_l
helpviewer_keywords:
- _wcstombs_l function
- wcstombs function
- string conversion, wide characters
- wide characters, converting
- wcstombs_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 91234252-9ea1-423a-af99-e9d0ce4a40e3
ms.openlocfilehash: b5ee2a0e5636e9c1d1f3fc204b2b6cbf8b733d45
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498987"
---
# <a name="wcstombs-_wcstombs_l"></a>wcstombs, _wcstombs_l

Převede sekvenci velkých znaků na odpovídající sekvenci vícebajtových znaků. K dispozici jsou bezpečnější verze těchto funkcí; viz [wcstombs_s, _wcstombs_s_l](wcstombs-s-wcstombs-s-l.md).

## <a name="syntax"></a>Syntaxe

```C
size_t wcstombs(
   char *mbstr,
   const wchar_t *wcstr,
   size_t count
);
size_t _wcstombs_l(
   char *mbstr,
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
);
template <size_t size>
size_t wcstombs(
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count
); // C++ only
template <size_t size>
size_t _wcstombs_l(
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parametry

*mbstr*<br/>
Adresa posloupnosti vícebajtových znaků.

*wcstr*<br/>
Adresa sekvence velkých znaků.

*výpočtu*<br/>
Maximální počet bajtů, které mohou být uloženy ve vícebajtovém výstupním řetězci.

*jazyka*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Pokud **wcstombs** úspěšně převede vícebajtový řetězec, vrátí počet bajtů zapsaných do vícebajtového výstupního řetězce s výjimkou ukončujícího znaku null (pokud existuje). Pokud má argument *Mbstr* **hodnotu null**, **wcstombs** vrátí požadovanou velikost v bajtech cílového řetězce. Pokud **wcstombs** narazí na velký znak, nemůže převést na vícebajtový znak, vrátí-1 přetypování na typ **size_t** a nastaví **errno** na **EILSEQ**.

## <a name="remarks"></a>Poznámky

Funkce **wcstombs** převede řetězec s velkým znakem, na který odkazuje *wcstr* na odpovídající vícebajtové znaky, a uloží výsledky do pole *mbstr* . Parametr *Count* označuje maximální počet bajtů, které mohou být uloženy ve vícebajtovém výstupním řetězci (tj. velikost *mbstr*). Obecně není známo, kolik bajtů bude vyžadováno při převodu řetězce širokého znaku. Některé velké znaky budou vyžadovat pouze jeden bajt ve výstupním řetězci; jiné vyžadují dva. Pokud jsou v vícebajtovém výstupním řetězci dva bajty pro každý velký znak ve vstupním řetězci (včetně širšího znaku null), je zaručeno, že je výsledek přizpůsoben.

Pokud **wcstombs** nalezne znak null znaků (L ' \ 0 ') před nebo po výskytu, převede ho na 8 bitů 0 a zastaví. Proto je řetězec vícebajtového znaku na *mbstr* zakončený hodnotou null pouze v případě, že při převodu dojde v **wcstombs** k znaku null znaků s velkým znakem. Pokud se sekvence, na které ukazuje *wcstr* a *mbstr* , překrývají, chování **wcstombs** není definováno.

Pokud má argument *Mbstr* **hodnotu null**, **wcstombs** vrátí požadovanou velikost v bajtech cílového řetězce.

**wcstombs** ověří své parametry. Pokud má Wcstr **hodnotu null**nebo je-li *počet* větší než **INT_MAX**, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md) . Pokud provádění může pokračovat, funkce nastaví **errno** na **EINVAL** a vrátí-1.

**wcstombs** používá aktuální národní prostředí pro jakékoli chování závislé na národním prostředí; **_wcstombs_l** je totožný s tím rozdílem, že místo toho používá národní prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

V C++nástroji mají tyto funkce přetížení šablony, které vyvolávají novější a zabezpečené protějšky těchto funkcí. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**wcstombs**|\<stdlib.h>|
|**_wcstombs_l**|\<stdlib.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Tento program ilustruje chování funkce **wcstombs** .

```C
// crt_wcstombs.c
// compile with: /W3
// This example demonstrates the use
// of wcstombs, which converts a string
// of wide characters to a string of
// multibyte characters.

#include <stdlib.h>
#include <stdio.h>

#define BUFFER_SIZE 100

int main( void )
{
    size_t  count;
    char    *pMBBuffer = (char *)malloc( BUFFER_SIZE );
    wchar_t *pWCBuffer = L"Hello, world.";

    printf("Convert wide-character string:\n" );

    count = wcstombs(pMBBuffer, pWCBuffer, BUFFER_SIZE ); // C4996
    // Note: wcstombs is deprecated; consider using wcstombs_s instead
    printf("   Characters converted: %u\n",
            count );
    printf("    Multibyte character: %s\n\n",
           pMBBuffer );

    free(pMBBuffer);
}
```

```Output
Convert wide-character string:
   Characters converted: 13
    Multibyte character: Hello, world.
```

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
