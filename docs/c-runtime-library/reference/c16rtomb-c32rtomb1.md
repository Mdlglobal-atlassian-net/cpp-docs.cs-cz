---
title: c16rtomb c32rtomb
ms.date: 01/22/2018
apiname:
- c16rtomb
- c32rtomb
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
- c16rtomb
- c32rtomb
- uchar/c16rtomb
- uchar/c32rtomb
helpviewer_keywords:
- c16rtomb function
- c32rtomb function
ms.assetid: 7f5743ca-a90e-4e3f-a310-c73e16f4e14d
ms.openlocfilehash: ad58184c7bab6f95a842bda5f9eb545f09434a3e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62341753"
---
# <a name="c16rtomb-c32rtomb"></a>c16rtomb c32rtomb

Převeďte na UTF-16 nebo UTF-32 širokého znaku vícebajtového znaku v aktuálním národním prostředí.

## <a name="syntax"></a>Syntaxe

```C
size_t c16rtomb(
    char *mbchar,
    char16_t wchar,
    mbstate_t *state
);
size_t c32rtomb(
    char *mbchar,
    char32_t wchar,
    mbstate_t *state
);
```

### <a name="parameters"></a>Parametry

*mbchar*<br/>
Ukazatel na pole pro uložení převedený vícebajtového znaku.

*wchar*<br/>
Široký znak pro převod.

*state*<br/>
Ukazatel **mbstate_t** objektu.

## <a name="return-value"></a>Návratová hodnota

Počet bajtů uložených v objektu array *mbchar*, včetně nějaké sekvence shift. Pokud *wchar* není platný široký znak, hodnotu (**size_t**)(-1) je vrácena, **errno** je nastavena na **EILSEQ**a hodnota *stavu* není zadána.

## <a name="remarks"></a>Poznámky

**C16rtomb** funkce převede znak kódování UTF-16 *wchar* pořadí ekvivalentních vícebajtového znaku úzký v aktuálním národním prostředí. Pokud *mbchar* není ukazatel s hodnotou null, funkce úložiště převedený pořadí v objektu pole odkazované *mbchar*. Až **MB_CUR_MAX** bajty jsou uloženy v *mbchar*, a *stavu* je nastavena na výsledný stav vícebajtové shift.    Pokud *wchar* je null široký znak, pořadí požadované pro obnovení stav počáteční posun je uložen, v případě potřeby, za nímž následuje znak null a *stavu* nastavena do stavu počáteční převodu. **C32rtomb** funkcí jsou identické, ale převede znak kódování UTF-32.

Pokud *mbchar* je ukazatel s hodnotou null, je ekvivalentní volání funkce, která nahradí vnitřní vyrovnávací paměť pro chování *mbchar* a široké znaky null, pro *wchar*.

*Stavu* převodu stav objektu umožňuje zajistit následných volání této funkce a další restartovatelnou službu funkcí, které zajišťují shift stav výstupní vícebajtové znaky. Výsledky nejsou definovány, když je kombinovat použití funkcí restartování a bez restartování, nebo pokud volání **setlocale** mezi restartovatelnou službu funkce volání.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**c16rtomb**, **c32rtomb**|C, C++: \<uchar.h>|

Informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtoc16, mbrtoc32](mbrtoc16-mbrtoc323.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
