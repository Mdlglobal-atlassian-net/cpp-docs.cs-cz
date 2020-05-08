---
title: wcstombs, _wcstombs_l
ms.date: 4/2/2020
api_name:
- wcstombs
- _wcstombs_l
- _o__wcstombs_l
- _o_wcstombs
api_location:
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 33c7554f1ab5c9822a1908a4b50d0ee0764615ae
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910639"
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

*locale*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Pokud **wcstombs** úspěšně převede vícebajtový řetězec, vrátí počet bajtů zapsaných do vícebajtového výstupního řetězce s výjimkou ukončujícího znaku null (pokud existuje). Pokud má argument *Mbstr* **hodnotu null**, **wcstombs** vrátí požadovanou velikost v bajtech cílového řetězce. Pokud **wcstombs** narazí na velký znak, nemůže převést na vícebajtový znak, vrátí-1 přetypování na typ **size_t** a nastaví **errno** na **EILSEQ**.

## <a name="remarks"></a>Poznámky

Funkce **wcstombs** převede řetězec s velkým znakem, na který odkazuje *wcstr* na odpovídající vícebajtové znaky, a uloží výsledky do pole *mbstr* . Parametr *Count* označuje maximální počet bajtů, které mohou být uloženy ve vícebajtovém výstupním řetězci (tj. velikost *mbstr*). Obecně není známo, kolik bajtů bude vyžadováno při převodu řetězce širokého znaku. Některé velké znaky budou vyžadovat pouze jeden bajt ve výstupním řetězci; jiné vyžadují dva. Pokud jsou v vícebajtovém výstupním řetězci dva bajty pro každý velký znak ve vstupním řetězci (včetně širšího znaku null), je zaručeno, že je výsledek přizpůsoben.

Pokud **wcstombs** nalezne znak null znaků (L ' \ 0 ') před *nebo po* výskytu, převede ho na 8 bitů 0 a zastaví. Proto je řetězec vícebajtového znaku na *mbstr* zakončený hodnotou null pouze v případě, že při převodu dojde v **wcstombs** k znaku null znaků s velkým znakem. Pokud se sekvence, na které ukazuje *wcstr* a *mbstr* , překrývají, chování **wcstombs** není definováno.

Pokud má argument *Mbstr* **hodnotu null**, **wcstombs** vrátí požadovanou velikost v bajtech cílového řetězce.

**wcstombs** ověří své parametry. Pokud *wcstr* má Wcstr **hodnotu null**nebo je-li *počet* větší než **INT_MAX**, vyvolá tato funkce obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md) . Pokud provádění může pokračovat, funkce nastaví **errno** na **EINVAL** a vrátí-1.

**wcstombs** používá aktuální národní prostředí pro jakékoli chování závislé na národním prostředí; **_wcstombs_l** je totožný s tím rozdílem, že místo toho používá národní prostředí předané. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

V jazyce C++ mají tyto funkce přetížení šablony, které vyvolávají novější a zabezpečené protějšky těchto funkcí. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**wcstombs**|\<Stdlib. h>|
|**_wcstombs_l**|\<Stdlib. h>|

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

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Jazyka](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
