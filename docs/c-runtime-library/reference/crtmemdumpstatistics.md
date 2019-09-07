---
title: _CrtMemDumpStatistics
ms.date: 11/04/2016
apiname:
- _CrtMemDumpStatistics
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
- CrtMemDumpStatistics
- _CrtMemDumpStatistics
helpviewer_keywords:
- _CrtMemDumpStatistics function
- CrtMemDumpStatistics function
ms.assetid: 27b9d731-3184-4a2d-b9a7-6566ab28a9fe
ms.openlocfilehash: 66eb58b65f3fa20e01ad16d68f3fe1baafd8cd04
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739801"
---
# <a name="_crtmemdumpstatistics"></a>_CrtMemDumpStatistics

Vypíše informace hlavičky ladění pro zadaný stav haldy ve formě čitelné pro uživatele (pouze pro ladicí verzi).

## <a name="syntax"></a>Syntaxe

```C
void _CrtMemDumpStatistics(
   const _CrtMemState *state
);
```

### <a name="parameters"></a>Parametry

*státech*<br/>
Ukazatel na stav haldy pro výpis.

## <a name="remarks"></a>Poznámky

Funkce **_CrtMemDumpStatistics** vypíše informace hlavičky ladění pro zadaný stav haldy ve formě čitelné uživatelem. Pomocí statistiky výpisu lze v aplikaci sledovat přidělování a vyhledávat problémy s pamětí. Stav paměti může obsahovat specifický stav haldy nebo rozdíl mezi dvěma stavy. Když není definovaný [_DEBUG](../../c-runtime-library/debug.md) , volání **_CrtMemDumpStatistics** se během předběžného zpracování odeberou.

Parametr *State* musí být ukazatel na strukturu **_CrtMemState** , která byla vyplněna pomocí [_CrtMemCheckpoint](crtmemcheckpoint.md) nebo vrácená [_CrtMemDifference](crtmemdifference.md) před voláním **_CrtMemDumpStatistics** . Pokud je stav **null**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **errno** je nastaven na **EINVAL** a není provedena žádná akce. Další informace najdete v tématech [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Další informace o funkcích stavu haldy a struktuře **_CrtMemState** naleznete v tématu [funkce vytváření sestav o stavu haldy](/visualstudio/debugger/crt-debug-heap-details). Další informace o způsobu přidělování, inicializace a správy paměťových bloků v ladicí verzi základní haldy najdete v [podrobnostech o haldě ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné hlavičky|
|-------------|---------------------|----------------------|
|**_CrtMemDumpStatistics**|\<crtdbg.h>|\<errno.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

**Knihovna** Ladit verze pouze [funkcí knihoven CRT](../../c-runtime-library/crt-library-features.md) .

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
