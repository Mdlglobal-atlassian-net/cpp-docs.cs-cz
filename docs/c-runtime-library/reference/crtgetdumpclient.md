---
title: _CrtGetDumpClient
ms.date: 11/04/2016
apiname:
- _CrtGetDumpClient
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
- CrtGetDumpClient
- _CrtGetDumpClient
helpviewer_keywords:
- _CrtGetDumpClient function
- CrtGetDumpClient function
ms.assetid: 9051867f-341b-493b-b53d-45d2b454a3ad
ms.openlocfilehash: e4700bd936bec97014508c4a971f6e6c278c6a11
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50550732"
---
# <a name="crtgetdumpclient"></a>_CrtGetDumpClient

Načte aktuální definovaného aplikací funkce pro výpis **_CLIENT_BLOCK** zadejte paměťových bloků (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
_CRT_DUMP_CLIENT _CrtGetDumpClient( void );
```

## <a name="return-value"></a>Návratová hodnota

Vrátí aktuální rutinu s výpisem paměti.

## <a name="remarks"></a>Poznámky

**_Crtgetdumpclient –** funkce načte aktuální funkci připojení pro výpis objektů uložených v **_CLIENT_BLOCK** bloky paměti jazyka C run-time ladění procesu výpisu paměti.

Další informace o použití jiné funkce háku podporující za běhu a psaní vlastních klienta definované funkce háku naleznete v tématu [ladění zápis funkce háku](/visualstudio/debugger/debug-hook-function-writing).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtGetDumpClient**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladicí verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md) pouze.

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[_CrtReportBlockType](crtreportblocktype.md)<br/>
[_CrtSetDumpClient](crtsetdumpclient.md)<br/>
