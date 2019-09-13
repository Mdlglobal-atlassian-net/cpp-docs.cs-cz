---
title: _set_controlfp
ms.date: 04/05/2018
api_name:
- _set_controlfp
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_controlfp
- _set_controlfp
helpviewer_keywords:
- set_controlfp function
- floating-point functions, setting control word
- _set_controlfp function
ms.assetid: e0689d50-f68a-4028-a9c1-fb23eedee4ad
ms.openlocfilehash: 4d39406db0f4c9ba6374776da62aea2dbb61e23d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948675"
---
# <a name="_set_controlfp"></a>_set_controlfp

Nastaví řídicí slovo s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
void __cdecl _set_controlfp(
    unsigned int newControl,
    unsigned int mask
);
```

### <a name="parameters"></a>Parametry

*newControl*<br/>
Nové bitové hodnoty řídicího slova.

*zrušit*<br/>
Maska pro nové bity řídicího slova, které se mají nastavit

## <a name="return-value"></a>Návratová hodnota

Žádné

## <a name="remarks"></a>Poznámky

Funkce **_set_controlfp** je podobná **_control87**, ale nastavuje pouze řídicí slovo s plovoucí desetinnou čárkou na *newControl*. Bity v hodnotách označují stav ovládacího prvku s plovoucí desetinnou čárkou. Stav ovládacího prvku s plovoucí desetinnou čárkou umožňuje programu změnit přesnost, zaokrouhlování a režimy nekonečno v matematickém balíčku s plovoucí desetinnou čárkou. Můžete také maskovat nebo zrušit maskování výjimek s plovoucí desetinnou čárkou pomocí **_set_controlfp**. Další informace najdete v tématu [_control87, _controlfp, \__control87_2](control87-controlfp-control87-2.md).

Tato funkce je při kompilaci s možností [/CLR (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md) zastaralá, protože modul CLR (Common Language Runtime) podporuje jenom výchozí přesnost s plovoucí desetinnou čárkou.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Kompatibilita|
|-------------|---------------------|-------------------|
|**_set_controlfp**|\<float. h >|jenom procesor x86|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87, _clearfp](clear87-clearfp.md)<br/>
[_status87, _statusfp, _statusfp2](status87-statusfp-statusfp2.md)<br/>
