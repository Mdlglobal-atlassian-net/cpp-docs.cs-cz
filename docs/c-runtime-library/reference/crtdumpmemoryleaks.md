---
title: _CrtDumpMemoryLeaks
ms.date: 11/04/2016
apiname:
- _CrtDumpMemoryLeaks
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
ms.openlocfilehash: baf4f8d8234ba744acda20541d37bbc3ed076678
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62339452"
---
# <a name="crtdumpmemoryleaks"></a>_CrtDumpMemoryLeaks

Výpisy veškerou paměť blokuje v haldě ladění, když došlo k nevracení paměti (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C

int _CrtDumpMemoryLeaks( void );
```

## <a name="return-value"></a>Návratová hodnota

**_CrtDumpMemoryLeaks** vrátí hodnotu PRAVDA, pokud je nalezen nevracení paměti. V opačném případě vrátí funkce hodnotu FALSE.

## <a name="remarks"></a>Poznámky

**_CrtDumpMemoryLeaks** funkce určuje, zda od spuštění programu došlo k nevracení paměti. Po nalezení nevracení informace hlavičky ladění pro všechny objekty v haldě vypsán ve formě čitelné pro uživatele. Když [_DEBUG](../../c-runtime-library/debug.md) není definován, jsou volání **_CrtDumpMemoryLeaks** odstraněna během předběžného zpracování.

**_CrtDumpMemoryLeaks** se často nazývá na konci provádění programu k ověření, že bylo uvolněno veškerou paměť přidělaná aplikace. Funkci lze volat automaticky při ukončení programu zapnutím **_CRTDBG_LEAK_CHECK_DF** bitové pole [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) příznak pomocí [_CrtSetDbgFlag](crtsetdbgflag.md)funkce.

**_CrtDumpMemoryLeaks** volání [_crtmemcheckpoint –](crtmemcheckpoint.md) získat aktuální stav haldy a pak kontroluje stav pro bloky, které nebyly byla uvolněna. Vyskytne blok neuvolněných **_CrtDumpMemoryLeaks** volání [_CrtMemDumpAllObjectsSince](crtmemdumpallobjectssince.md) na informace z výpisu paměti pro všechny objekty, které jsou přiděleny do haldy od samého začátku provádění programu.

Ve výchozím nastavení vnitřní bloky C run-time (**_CRT_BLOCK**) nejsou součástí operací výpisu paměti. [_CrtSetDbgFlag](crtsetdbgflag.md) funkce je možné zapnout **_CRTDBG_CHECK_CRT_DF** bit z **_crtDbgFlag** pro zahrnutí těchto bloků v procesu zjišťování úniku.

Další informace o funkcích stavu haldy a **_CrtMemState** struktury, přečtěte si téma [funkce vykazování stavu haldy](/visualstudio/debugger/crt-debug-heap-details). Další informace o způsobu jsou bloky paměti přidělené, inicializovat a správy v ladicí verzi základní haldy viz [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtDumpMemoryLeaks**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladicí verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md) pouze.

## <a name="example"></a>Příklad

Pro ukázku toho, jak používat **_CrtDumpMemoryLeaks**, naleznete v tématu [crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1).

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
