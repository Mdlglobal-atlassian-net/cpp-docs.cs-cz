---
title: _Crtmemdumpstatistics – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _CrtMemDumpStatistics function
- CrtMemDumpStatistics function
ms.assetid: 27b9d731-3184-4a2d-b9a7-6566ab28a9fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 655d9be75fa031cc2cbebfd65c4634528f410e85
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44110523"
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
