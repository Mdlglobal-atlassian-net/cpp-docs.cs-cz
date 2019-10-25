---
title: c16rtomb, c32rtomb
ms.date: 10/22/2019
api_name:
- c16rtomb
- c32rtomb
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- c16rtomb
- c32rtomb
- uchar/c16rtomb
- uchar/c32rtomb
helpviewer_keywords:
- c16rtomb function
- c32rtomb function
ms.assetid: 7f5743ca-a90e-4e3f-a310-c73e16f4e14d
ms.openlocfilehash: 8f480d9b450b528275fea78ae878269fa6a4fa54
ms.sourcegitcommit: 0a5518fdb9d87fcc326a8507ac755936285fcb94
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2019
ms.locfileid: "72811065"
---
# <a name="c16rtomb-c32rtomb"></a>c16rtomb, c32rtomb

Převeďte libovolný znak UTF-16 nebo UTF-32 na vícebajtový znak UTF-8.

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

*mbchar*\
Ukazatel na pole pro uložení převedeného vícebajtového znaku UTF-8.

*wchar*\
Velký znak pro převod.

\ *stavu*
Ukazatel na objekt **mbstate_t** .

## <a name="return-value"></a>Návratová hodnota

Počet bajtů uložených v objektu array *mbchar*, včetně všech sekvencí posunutí. Pokud *WCHAR* není platným velkým znakem, vrátí se hodnota (**size_t**) (-1), **errno** je nastavená na **EILSEQ**a hodnota State ( *stav* ) je neurčená.

## <a name="remarks"></a>Poznámky

Funkce **c16rtomb** převádí znak *WCHAR* UTF-16 Le na ekvivalentní vícebajtovou sekvenci UTF-8 vícebajtových znaků. Pokud *mbchar* není ukazatel s hodnotou null, funkce uloží převedenou sekvenci do objektu Array, na který odkazuje *mbchar*. Až **MB_CUR_MAX** bajty jsou uloženy v *mbchar*a *stav* je nastaven na výsledný vícebajtový stav posunutí.

Pokud *WCHAR* je znak null, sekvence požadovaná pro obnovení počátečního stavu směny je v případě potřeby uložena a za ním následuje znak null. *stav* je nastaven na počáteční stav převodu. Funkce **c32rtomb** je shodná, ale PŘEVÁDÍ znak UTF-32.

Pokud je *mbchar* ukazatel s hodnotou null, je chování ekvivalentní volání funkce, která nahradí vnitřní vyrovnávací paměť pro *mbchar* a pro WCHAR znak pro.

Stavový objekt konverze *stavu* umožňuje provést následující volání této funkce a další znovu spouštěné funkce, které udržují stav posunu vícebajtových výstupních znaků. Pokud kombinujete použití restartných a neopakujících se funkcí, výsledky se nedefinují.

Chcete-li převést znaky UTF-16 na vícebajtové znaky jiné než UTF-8, použijte funkce [wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md), [wcstombs_s nebo _wcstombs_s_l](wcstombs-s-wcstombs-s-l.md) .

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**c16rtomb**, **c32rtomb**|C, C++:\<uchar. h >|

Informace o kompatibilitě najdete v tématu [Kompatibilita](../compatibility.md).

## <a name="see-also"></a>Viz také:

\ [převodu dat](../data-conversion.md)
\ [národního prostředí](../locale.md)
[Interpretace vícebajtových znakových sekvencí](../interpretation-of-multibyte-character-sequences.md)\
[mbrtoc16, mbrtoc32](mbrtoc16-mbrtoc323.md)\
[wcrtomb](wcrtomb.md)\
[wcrtomb_s](wcrtomb-s.md)
