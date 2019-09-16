---
title: _CrtDumpMemoryLeaks
ms.date: 11/04/2016
api_name:
- _CrtDumpMemoryLeaks
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- CRTDBG_LEAK_CHECK_DF
- CRTDBG_CHECK_CRT_DF
- _CRTDBG_LEAK_CHECK_DF
- CrtDumpMemoryLeaks
- _CrtDumpMemoryLeaks
- _CRTDBG_CHECK_CRT_DF
helpviewer_keywords:
- CrtDumpMemoryLeaks function
- CRTDBG_LEAK_CHECK_DF macro
- _CRTDBG_LEAK_CHECK_DF macro
- _CrtDumpMemoryLeaks function
- CRTDBG_CHECK_CRT_DF macro
- _CRTDBG_CHECK_CRT_DF macro
ms.assetid: 71b2eab4-7f55-44e8-a55a-bfea4f32d34c
ms.openlocfilehash: dae93577f5c0c0297606577c05d6b6ef2040c831
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938820"
---
# <a name="_crtdumpmemoryleaks"></a>_CrtDumpMemoryLeaks

Vypíše všechny bloky paměti v haldě ladění při výskytu nevrácené paměti (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C

int _CrtDumpMemoryLeaks( void );
```

## <a name="return-value"></a>Návratová hodnota

**_CrtDumpMemoryLeaks** vrací hodnotu true, pokud je nalezena nevrácená paměť. V opačném případě vrátí funkce hodnotu FALSE.

## <a name="remarks"></a>Poznámky

Funkce **_CrtDumpMemoryLeaks** určuje, zda došlo od spuštění programu k nevrácení paměti. Při nalezení nevracení jsou informace hlavičky ladění pro všechny objekty v haldě dumpingové ve formě čitelné uživatelem. Když není definovaný [_DEBUG](../../c-runtime-library/debug.md) , volání **_CrtDumpMemoryLeaks** se během předběžného zpracování odeberou.

**_CrtDumpMemoryLeaks** se často volá na konci provádění programu, aby se ověřilo, že byla uvolněna veškerá paměť přidělená aplikací. Funkci lze volat automaticky při ukončení programu zapnutím **_CRTDBG_LEAK_CHECK_DF** bitového pole příznaku [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) pomocí funkce [_CrtSetDbgFlag](crtsetdbgflag.md) .

**_CrtDumpMemoryLeaks** volá [_CrtMemCheckpoint](crtmemcheckpoint.md) , aby získal aktuální stav haldy, a pak vyhledá ve stavu Neuvolněné bloky. Když dojde k neuvolněnému bloku, **_CrtDumpMemoryLeaks** zavolá [_CrtMemDumpAllObjectsSince](crtmemdumpallobjectssince.md) pro výpis informací pro všechny objekty, které jsou přiděleny v haldě od spuštění programu.

Ve výchozím nastavení nejsou interní bloky C run-time ( **_CRT_BLOCK**) zahrnuty do operací výpisu paměti. Funkci [_CrtSetDbgFlag](crtsetdbgflag.md) lze použít k zapnutí **_CRTDBG_CHECK_CRT_DF** bitu **_crtDbgFlag** pro zahrnutí těchto bloků do procesu detekce nevracení.

Další informace o funkcích stavu haldy a struktuře **_CrtMemState** naleznete v tématu [funkce vytváření sestav o stavu haldy](/visualstudio/debugger/crt-debug-heap-details). Další informace o způsobu přidělování, inicializace a správy paměťových bloků v ladicí verzi základní haldy najdete v [podrobnostech o haldě ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtDumpMemoryLeaks**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladit verze pouze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md) .

## <a name="example"></a>Příklad

Ukázku použití **_CrtDumpMemoryLeaks**naleznete v tématu [crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1).

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
