---
title: _set_controlfp – | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- set_controlfp function
- floating-point functions, setting control word
- _set_controlfp function
ms.assetid: e0689d50-f68a-4028-a9c1-fb23eedee4ad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a2647e9719c2aa3fe303393fcc1da55de0385581
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="setcontrolfp"></a>_set_controlfp

Nastaví s plovoucí desetinnou čárkou řídicího slova.

## <a name="syntax"></a>Syntaxe

```C
void __cdecl _set_controlfp(
    unsigned int newControl,
    unsigned int mask
);
```

### <a name="parameters"></a>Parametry

*newControl*<br/>
Nové hodnoty bit řídicího slova.

*Maska*<br/>
Maska pro novou službu bits řídicího slova nastavit.

## <a name="return-value"></a>Návratová hodnota

Žádné

## <a name="remarks"></a>Poznámky

**_Set_controlfp –** funkce je podobná **_control87 –**, ale jenom nastaví s plovoucí desetinnou čárkou řídicího slova *newControl*. Bity v hodnoty označují stav ovládacího prvku s plovoucí desetinnou čárkou. Stav s plovoucí desetinnou čárkou řízení umožňuje program, který chcete změnit přesnost, zaokrouhlení a infinity režimy v s plovoucí desetinnou čárkou matematického balíku. Můžete také maskování nebo odmaskujte s plovoucí desetinnou čárkou výjimky pomocí **_set_controlfp –**. Další informace najdete v tématu [_control87, _controlfp, \__control87_2](control87-controlfp-control87-2.md).

Tato funkce je zastaralý, když kompilujete s [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) protože modul common language runtime podporuje pouze výchozí přesnost s plovoucí desetinnou čárkou.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Kompatibilita|
|-------------|---------------------|-------------------|
|**_set_controlfp**|\<float.h – >|x86 pouze procesoru|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87, _clearfp](clear87-clearfp.md)<br/>
[_status87, _statusfp, _statusfp2](status87-statusfp-statusfp2.md)<br/>
