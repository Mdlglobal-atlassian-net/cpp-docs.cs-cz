---
title: _CrtMemDumpAllObjectsSince
ms.date: 11/04/2016
api_name:
- _CrtMemDumpAllObjectsSince
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
- CrtMemDumpAllObjectsSince
- _CrtMemDumpAllObjectsSince
helpviewer_keywords:
- _CrtMemDumpAllObjectsSince function
- CrtMemDumpAllObjectsSince function
ms.assetid: c48a447a-e6bb-475c-9271-a3021182a0dc
ms.openlocfilehash: 9e3793e9b88c593968b108e2801e24476417603c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942372"
---
# <a name="_crtmemdumpallobjectssince"></a>_CrtMemDumpAllObjectsSince

Vypíše informace o objektech v haldě od spuštění programu nebo ze zadaného stavu haldy (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
void _CrtMemDumpAllObjectsSince(
   const _CrtMemState *state
);
```

### <a name="parameters"></a>Parametry

*státech*<br/>
Ukazatel na stav haldy, aby bylo možné zahájit výpis z nebo **hodnoty null**.

## <a name="remarks"></a>Poznámky

Funkce **_CrtMemDumpAllObjectsSince** vypíše informace hlavičky ladění objektů přidělených v haldě v uživatelsky čitelné podobě. Informace o výpisu lze pomocí aplikace použít ke sledování přidělení a zjištění problémů s pamětí. Když není definovaný [_DEBUG](../../c-runtime-library/debug.md) , volání **_CrtMemDumpAllObjectsSince** se během předběžného zpracování odeberou.

**_CrtMemDumpAllObjectsSince** používá hodnotu parametru *State* k určení, kde se má iniciovat operace výpisu paměti. Chcete-li zahájit dumping ze zadaného stavu haldy, musí být parametr *stavu* ukazatelem na strukturu **_CrtMemState** , která byla vyplněna pomocí [_CrtMemCheckpoint](crtmemcheckpoint.md) před voláním **_CrtMemDumpAllObjectsSince** . Pokud je stav **null**, funkce spustí výpis z spuštění programu.

Pokud aplikace nainstalovala funkci zavěšení výpisu paměti voláním [_CrtSetDumpClient](crtsetdumpclient.md), pak pokaždé, když **_CrtMemDumpAllObjectsSince** vypíše informace o typu **_CLIENT_BLOCK** bloku, zavolá výpis dodaný aplikací. i funkce. Ve výchozím nastavení nejsou interní bloky C run-time ( **_CRT_BLOCK**) zahrnuty do operací výpisu paměti. Funkci [_CrtSetDbgFlag](crtsetdbgflag.md) lze použít k zapnutí **_CRTDBG_CHECK_CRT_DF** bitu **_crtDbgFlag** pro zahrnutí těchto bloků. Kromě toho nejsou do výpisu paměti zahrnuty bloky označené jako volné nebo ignorované ( **_FREE_BLOCK**, **_IGNORE_BLOCK**).

Další informace o funkcích stavu haldy a struktuře **_CrtMemState** naleznete v tématu [funkce vytváření sestav o stavu haldy](/visualstudio/debugger/crt-debug-heap-details). Další informace o způsobu přidělování, inicializace a správy paměťových bloků v ladicí verzi základní haldy najdete v [podrobnostech o haldě ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtMemDumpAll-ObjectsSince**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladit verze pouze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md) .

## <a name="example"></a>Příklad

Ukázku použití **_CrtMemDumpAllObjectsSince**naleznete v tématu [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2).

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
