---
title: _CrtMemDumpAllObjectsSince
ms.date: 11/04/2016
apiname:
- _CrtMemDumpAllObjectsSince
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
- CrtMemDumpAllObjectsSince
- _CrtMemDumpAllObjectsSince
helpviewer_keywords:
- _CrtMemDumpAllObjectsSince function
- CrtMemDumpAllObjectsSince function
ms.assetid: c48a447a-e6bb-475c-9271-a3021182a0dc
ms.openlocfilehash: 7de0ee9ff166af6336a8d14aa0dbd07dbd7d23fc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62347454"
---
# <a name="crtmemdumpallobjectssince"></a>_CrtMemDumpAllObjectsSince

Vypíše informace o objektech v haldě od začátku spuštění programu nebo z zadaný stav haldy (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
void _CrtMemDumpAllObjectsSince(
   const _CrtMemState *state
);
```

### <a name="parameters"></a>Parametry

*state*<br/>
Ukazatel na stav haldy zahájíte výpis z nebo **NULL**.

## <a name="remarks"></a>Poznámky

**_CrtMemDumpAllObjectsSince** funkce Vypíše informace hlavičky ladění objektů, které jsou přiděleny do haldy ve formě čitelné pro uživatele. Informace z výpisu paměti lze aplikaci sledovat přidělování a vyhledávat problémy s pamětí. Když [_DEBUG](../../c-runtime-library/debug.md) není definován, jsou volání **_CrtMemDumpAllObjectsSince** odstraněna během předběžného zpracování.

**_CrtMemDumpAllObjectsSince** používá hodnotu *stavu* parametr k určení, kam se zahájit operaci výpisu stavu systému. Začněte výpis z zadaný stav haldy, *stavu* parametr musí být ukazatel na **_CrtMemState** struktura, která byla vyplněna pomocí [_crtmemcheckpoint –](crtmemcheckpoint.md) před **_CrtMemDumpAllObjectsSince** byla volána. Když *stavu* je **NULL**, funkce začíná s výpisem paměti od samého začátku provádění programu.

Pokud aplikace má nainstalovanou funkci připojení s výpisem paměti pomocí volání [_CrtSetDumpClient](crtsetdumpclient.md), pak pokaždé, když **_CrtMemDumpAllObjectsSince** Vypíše informace o **_CLIENT_BLOCK** typ bloku, volá funkci poskytované aplikací s výpisem paměti. Ve výchozím nastavení vnitřní bloky C run-time (**_CRT_BLOCK**) nejsou součástí operací výpisu paměti. [_CrtSetDbgFlag](crtsetdbgflag.md) funkce je možné zapnout **_CRTDBG_CHECK_CRT_DF** bit z **_crtDbgFlag** pro zahrnutí těchto bloků. Kromě toho bloky označené jako uvolněn nebo ignorovat (**_FREE_BLOCK**, **_IGNORE_BLOCK**) nejsou součástí výpis stavu paměti.

Další informace o funkcích stavu haldy a **_CrtMemState** struktury, přečtěte si téma [funkce vykazování stavu haldy](/visualstudio/debugger/crt-debug-heap-details). Další informace o způsobu jsou bloky paměti přidělené, inicializovat a správy v ladicí verzi základní haldy viz [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtMemDumpAll-ObjectsSince**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladicí verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md) pouze.

## <a name="example"></a>Příklad

Pro ukázku toho, jak používat **_CrtMemDumpAllObjectsSince**, naleznete v tématu [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2).

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
