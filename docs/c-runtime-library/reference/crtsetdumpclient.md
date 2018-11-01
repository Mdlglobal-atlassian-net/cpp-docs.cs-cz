---
title: _CrtSetDumpClient
ms.date: 11/04/2016
apiname:
- _CrtSetDumpClient
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
- _CrtSetDumpClient
- CrtSetDumpClient
helpviewer_keywords:
- _CrtSetDumpClient function
- CrtSetDumpClient function
ms.assetid: f3dd06d0-c331-4a12-b68d-25378d112033
ms.openlocfilehash: 09f319f6298dbec6b229b2923bd86fc9b50314de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50470744"
---
# <a name="crtsetdumpclient"></a>_CrtSetDumpClient

Nainstaluje definované aplikací funkce pro výpis **_CLIENT_BLOCK** zadejte paměťových bloků (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
_CRT_DUMP_CLIENT _CrtSetDumpClient( _CRT_DUMP_CLIENT dumpClient );
```

### <a name="parameters"></a>Parametry

*dumpClient*<br/>
Novou funkci výpisu paměti definované klienta k připojení do procesu výpisu paměti ladění za běhu C.

## <a name="return-value"></a>Návratová hodnota

Vrátí dříve definované klientský blok funkce výpisu paměti.

## <a name="remarks"></a>Poznámky

**_CrtSetDumpClient** funkce umožňuje, aby aplikace k připojení vlastní funkce pro výpis objektů uložených v **_CLIENT_BLOCK** bloky paměti do jazyka C Runtime ladění procesu výpisu paměti. V důsledku toho se pokaždé, když se ladění výpisu funkce, jako [_CrtMemDumpAllObjectsSince](crtmemdumpallobjectssince.md) nebo [_CrtDumpMemoryLeaks](crtdumpmemoryleaks.md) výpisy stavu systému **_CLIENT_BLOCK** bloku paměti, aplikace také je volána funkce s výpisem paměti. **_CrtSetDumpClient** poskytuje snadno aplikace pro zjištění nevracení paměti a probíhá ověřování nebo vytváření sestav obsah data uložená v **_CLIENT_BLOCK** bloky. Když [_DEBUG](../../c-runtime-library/debug.md) není definován, jsou volání **_CrtSetDumpClient** odstraněna během předběžného zpracování.

**_CrtSetDumpClient** funkce nainstaluje novou funkci s výpisem paměti definované aplikací podle *dumpClient* a vrací funkci dříve definovaná s výpisem paměti. Příklad funkce s výpisem paměti blok klienta vypadá takto:

```C
void DumpClientFunction( void *userPortion, size_t blockSize );
```

*UserPortion* argument je ukazatel na začátku části dat uživatele bloku paměti a *velikost bloku* určuje blokovat velikost přidělené paměti v bajtech. Funkce s výpisem paměti blok klienta musí vracet **void**. Ukazatel na funkci s výpisem paměti klienta, který je předán **_CrtSetDumpClient** je typu **_crt_dump_client –**, jak jsou definovány v souboru Crtdbg.h:

```C
typedef void (__cdecl *_CRT_DUMP_CLIENT)( void *, size_t );
```

Další informace o funkcích, které pracují s **_CLIENT_BLOCK** zadejte bloky paměti naleznete v tématu [funkce háku bloku klienta](/visualstudio/debugger/client-block-hook-functions). [_CrtReportBlockType](crtreportblocktype.md) funkci můžete použít k vrácení informací o typech bloku a podtypy.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtSetDumpClient**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladicí verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md) pouze.

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[_CrtReportBlockType](crtreportblocktype.md)<br/>
[_CrtGetDumpClient](crtgetdumpclient.md)<br/>
