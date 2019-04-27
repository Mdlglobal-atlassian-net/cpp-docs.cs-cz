---
title: _CrtGetReportHook
ms.date: 11/04/2016
apiname:
- _CrtGetReportHook
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
apitype: DLLExport
f1_keywords:
- CrtGetReportHook
- _CrtGetReportHook
helpviewer_keywords:
- CrtGetReportHook function
- _CrtGetReportHook function
ms.assetid: 922758ed-7edd-4359-9c92-0535192dc11a
ms.openlocfilehash: 0b8b666093807c95312d4328ca9b3043ad1e09df
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62339413"
---
# <a name="crtgetreporthook"></a>_CrtGetReportHook

Načte klienta definované vytváření sestav funkce pro zapojení do C spuštění pro ladění reporting procesu (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
_CRT_REPORT_HOOK _CrtGetReportHook( void );
```

## <a name="return-value"></a>Návratová hodnota

Vrátí aktuální funkci generování sestav definované klienta.

## <a name="remarks"></a>Poznámky

**_Crtgetreporthook –** umožňuje aplikaci načíst aktuální funkce vytváření sestav pro knihovnu ladění za běhu C proces vytváření sestav.

Další informace o použití jiné funkce háku podporující za běhu a psaní vlastních klienta definované funkce háku naleznete v tématu [ladění zápis funkce háku](/visualstudio/debugger/debug-hook-function-writing).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtGetReportHook**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladicí verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md) pouze.

## <a name="example"></a>Příklad

Pro ukázku toho, jak používat **_CrtSetReportHook**, naleznete v tématu [sestavy](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/report).

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetReportHook](crtsetreporthook.md)<br/>
