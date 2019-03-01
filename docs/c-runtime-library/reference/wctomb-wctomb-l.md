---
title: wctomb, _wctomb_l
ms.date: 11/04/2016
apiname:
- _wctomb_l
- wctomb
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
- wctomb
helpviewer_keywords:
- string conversion, wide characters
- wide characters, converting
- _wctomb_l function
- wctomb function
- wctomb_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 4a543f0e-5516-4d81-8ff2-3c5206f02ed5
ms.openlocfilehash: df0abdd644027f9bab8cd177dfd4d0af4c98df35
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210481"
---
# <a name="wctomb-wctombl"></a>wctomb, _wctomb_l

Převeďte na odpovídající vícebajtový znak širokého znaku. Bezpečnější verze těchto funkcí jsou k dispozici. Zobrazit [wctomb_s – _wctomb_s_l –](wctomb-s-wctomb-s-l.md).

## <a name="syntax"></a>Syntaxe

```C
int wctomb(
   char *mbchar,
   wchar_t wchar
);
int _wctomb_l(
   char *mbchar,
   wchar_t wchar,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*mbchar*<br/>
Adresa vícebajtového znaku.

*wchar*<br/>
Široký znak.

## <a name="return-value"></a>Návratová hodnota

Pokud **wctomb –** převede širokého znaku na vícebajtový znak, vrátí počet bajtů (který se nikdy větší než **MB_CUR_MAX**) v širokého znaku. Pokud *wchar* je prázdný znak širokého znaku (L '\0'), **wctomb –** vrátí hodnotu 1. Pokud se ukazatel na cílový *mbchar* je **NULL**, **wctomb –** vrátí hodnotu 0. Pokud převod není v aktuálním národním prostředí, **wctomb –** vrátí hodnotu -1 a **errno** je nastavena na **EILSEQ**.

## <a name="remarks"></a>Poznámky

**Wctomb –** funkce převede její *wchar* argument odpovídající vícebajtový znak a uloží výsledek v *mbchar*. Funkce můžete volat z libovolného bodu v libovolné aplikaci. **wctomb –** používá aktuální národní prostředí pro všechna závislá chování; **_wctomb_l –** je stejný jako **wctomb –** s tím rozdílem, že používá národní prostředí předané. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

**wctomb –** ověří jeho parametry. Pokud *mbchar* je **NULL**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, **errno** je nastavena na **EINVAL** a funkce vrátí hodnotu -1.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**wctomb**|\<stdlib.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Tento program ukazuje chování wctomb – funkce.

```cpp
// crt_wctomb.cpp
// compile with: /W3
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int i;
   wchar_t wc = L'a';
   char *pmb = (char *)malloc( MB_CUR_MAX );

   printf( "Convert a wide character:\n" );
   i = wctomb( pmb, wc ); // C4996
   // Note: wctomb is deprecated; consider using wctomb_s
   printf( "   Characters converted: %u\n", i );
   printf( "   Multibyte character: %.1s\n\n", pmb );
}
```

```Output
Convert a wide character:
   Characters converted: 1
   Multibyte character: a
```

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[WideCharToMultiByte](/windows/desktop/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
