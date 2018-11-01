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
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605124"
---
# <a name="crtmemdumpstatistics"></a>_CrtMemDumpStatistics

Vypíše informace hlavičky ladění pro zadaný stav haldy ve formě čitelné pro uživatele (pouze pro ladicí verzi).

## <a name="syntax"></a>Syntaxe

```C
void _CrtMemDumpStatistics(
   const _CrtMemState *state
);
```

### <a name="parameters"></a>Parametry

*Stav*<br/>
Ukazatel na stav haldy pro výpis.

## <a name="remarks"></a>Poznámky

**_Crtmemdumpstatistics –** funkce Vypíše informace hlavičky ladění pro určitý stav haldy ve formě čitelné pro uživatele. Pomocí statistiky výpisu lze v aplikaci sledovat přidělování a vyhledávat problémy s pamětí. Stav paměti může obsahovat specifický stav haldy nebo rozdíl mezi dvěma stavy. Když [_DEBUG](../../c-runtime-library/debug.md) není definován, jsou volání **_crtmemdumpstatistics –** odstraněna během předběžného zpracování.

*Stavu* parametr musí být ukazatel **_CrtMemState** struktura, která byla vyplněna pomocí [_crtmemcheckpoint –](crtmemcheckpoint.md) nebo vrácena funkcí [_ Crtmemdifference –](crtmemdifference.md) před **_crtmemdumpstatistics –** je volána. Pokud *stavu* je **NULL**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, **errno** je nastavena na **EINVAL** a nebyla provedena žádná akce. Další informace najdete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Další informace o funkcích stavu haldy a **_CrtMemState** struktury, přečtěte si téma [funkce vykazování stavu haldy](/visualstudio/debugger/crt-debug-heap-details). Další informace o způsobu jsou bloky paměti přidělené, inicializovat a správy v ladicí verzi základní haldy viz [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelná záhlaví|
|-------------|---------------------|----------------------|
|**_CrtMemDumpStatistics**|\<crtdbg.h>|\<errno.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

**Knihovny:** ladicí verze [funkce knihovny CRT](../../c-runtime-library/crt-library-features.md) pouze.

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
