---
title: _Crtgetreporthook – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CrtGetReportHook function
- _CrtGetReportHook function
ms.assetid: 922758ed-7edd-4359-9c92-0535192dc11a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d78c176d5d4de54f4ae5eea84b0483b9e6bc3bec
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="crtgetreporthook"></a>_CrtGetReportHook

Načte klienta definované generování sestav funkce pro zapojení do C dobu spuštění pro ladění reporting procesu (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
_CRT_REPORT_HOOK _CrtGetReportHook( void );
```

## <a name="return-value"></a>Návratová hodnota

Vrátí aktuální funkci generování sestav definované klienta.

## <a name="remarks"></a>Poznámky

**_Crtgetreporthook –** umožňuje aplikaci načíst aktuální funkce vytváření sestav pro ladicí běhové knihovny jazyka C reporting procesu.

Další informace o použití jiných podporující háku běhové funkce a psaní vlastního klienta definované funkce háku najdete v tématu [ladění zápis funkce háku](/visualstudio/debugger/debug-hook-function-writing).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtGetReportHook**|\<crtdbg.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladicí verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md) pouze.

## <a name="example"></a>Příklad

Příklad, jak pomocí **_crtsetreporthook –**, najdete v části [sestavy](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/report).

## <a name="see-also"></a>Viz také

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetReportHook](crtsetreporthook.md)<br/>
