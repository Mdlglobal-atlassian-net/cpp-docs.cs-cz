---
title: _set_controlfp
ms.date: 04/05/2018
apiname:
- _set_controlfp
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- set_controlfp
- _set_controlfp
helpviewer_keywords:
- set_controlfp function
- floating-point functions, setting control word
- _set_controlfp function
ms.assetid: e0689d50-f68a-4028-a9c1-fb23eedee4ad
ms.openlocfilehash: 1187502f09849d7ca4d8e595c237cfa511d00c6b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356679"
---
# <a name="setcontrolfp"></a>_set_controlfp

Nastaví slovo ovládacího prvku s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
void __cdecl _set_controlfp(
    unsigned int newControl,
    unsigned int mask
);
```

### <a name="parameters"></a>Parametry

*newControl*<br/>
Nové bitové hodnoty kontrolního slova.

*Maska*<br/>
Maska pro nové bity ovládacího slova, chcete-li nastavit.

## <a name="return-value"></a>Návratová hodnota

Žádné

## <a name="remarks"></a>Poznámky

**_Set_controlfp –** funkce je podobná **_control87**, ale pouze nastaví slovo ovládacího prvku s plovoucí desetinnou čárkou na *newControl*. Bity v hodnotách označují stav ovládacího prvku s plovoucí desetinnou čárkou. Stav ovládacího prvku s plovoucí desetinnou čárkou umožňuje programu změnit přesnost, zaokrouhlení a režimy nekonečna matematickém s plovoucí desetinnou čárkou balíčku. Můžete také maskování nebo odmaskování výjimek plovoucí desetinné čárky pomocí **_set_controlfp –**. Další informace najdete v tématu [_control87 _controlfp, \__control87_2](control87-controlfp-control87-2.md).

Tato funkce je zastaralá při kompilaci s [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) protože modul CLR podporuje pouze základní přesnost s plovoucí desetinnou čárkou.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Kompatibilita|
|-------------|---------------------|-------------------|
|**_set_controlfp**|\<float.h >|x86 pouze procesoru|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87, _clearfp](clear87-clearfp.md)<br/>
[_status87, _statusfp, _statusfp2](status87-statusfp-statusfp2.md)<br/>
