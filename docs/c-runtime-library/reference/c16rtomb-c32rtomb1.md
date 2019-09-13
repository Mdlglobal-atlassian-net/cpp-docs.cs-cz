---
title: c16rtomb, c32rtomb
ms.date: 01/22/2018
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
ms.openlocfilehash: a16effe48442ccbb5144b57ead2fb15c908fe898
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943433"
---
# <a name="c16rtomb-c32rtomb"></a>c16rtomb, c32rtomb

Převeďte velký znak UTF-16 nebo UTF-32 na vícebajtový znak v aktuálním národním prostředí.

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
Ukazatel na pole pro uložení vícebajtově převedeného znaku.

*wchar*<br/>
Velký znak pro převod.

*státech*<br/>
Ukazatel na objekt **mbstate_t** .

## <a name="return-value"></a>Návratová hodnota

Počet bajtů uložených v objektu array *mbchar*, včetně všech sekvencí posunutí. Pokud *WCHAR* není platným velkým znakem, vrátí se hodnota (**size_t**) (-1), **errno** je nastavena na **EILSEQ**a hodnota *State* není určena.

## <a name="remarks"></a>Poznámky

Funkce **c16rtomb** PŘEVEDE znak UTF-16 *WCHAR* na ekvivalentní vícebajtovou sekvenci znaků v aktuálním národním prostředí. Pokud *mbchar* není ukazatel s hodnotou null, funkce uloží převedenou sekvenci do objektu Array, na který odkazuje *mbchar*. Až **MB_CUR_MAX** bajty jsou uloženy v *mbchar*a *stav* je nastaven na výsledný vícebajtový stav posunutí.    Pokud *WCHAR* je znak null, sekvence požadovaná pro obnovení počátečního stavu směny je uložena, je-li to nutné, následuje znak null a *stav* je nastaven na počáteční stav převodu. Funkce **c32rtomb** je shodná, ale PŘEVÁDÍ znak UTF-32.

Pokud je *mbchar* ukazatel s hodnotou null, je chování ekvivalentní volání funkce, která nahradí vnitřní vyrovnávací paměť pro *mbchar* a pro WCHAR znak pro.

Stavový objekt konverze *stavu* umožňuje provést následující volání této funkce a další znovu spouštěné funkce, které udržují stav posunu vícebajtových výstupních znaků. Výsledky jsou nedefinovány při kombinaci použití restartované a nepříkazové funkce, nebo pokud je volání **setlocale** provedeno mezi restartací volání funkcí.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**c16rtomb**, **c32rtomb**|C, C++: \<uchar.h>|

Informace o kompatibilitě najdete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtoc16, mbrtoc32](mbrtoc16-mbrtoc323.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
