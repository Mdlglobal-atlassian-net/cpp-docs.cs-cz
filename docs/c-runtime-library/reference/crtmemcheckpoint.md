---
title: _CrtMemCheckpoint
ms.date: 11/04/2016
apiname:
- _CrtMemCheckpoint
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
- CrtMemCheckpoint
- _CrtMemCheckpoint
- crtdbg/_CrtMemCheckpoint
helpviewer_keywords:
- CrtMemCheckpoint function
- _CrtMemCheckpoint function
ms.assetid: f1bacbaa-5a0c-498a-ac7a-b6131d83dfbc
ms.openlocfilehash: ee435ba3e9e40795280dee0f97feaad32c8b0fc3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50589514"
---
# <a name="crtmemcheckpoint"></a>_CrtMemCheckpoint

Získá aktuální stav haldy ladění a uloží do poskytované aplikací **_CrtMemState** strukturu (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
void _CrtMemCheckpoint(
   _CrtMemState *state
);
```

### <a name="parameters"></a>Parametry

*Stav*<br/>
Ukazatel na **_CrtMemState** struktura, která se zaplnit kontrolním bodem paměti.

## <a name="remarks"></a>Poznámky

**_Crtmemcheckpoint –** funkce vytvoří snímek aktuálního stavu haldy ladění v kterémkoli daném okamžiku. Tento snímek mohou využívat jiné funkce stavu haldy jako [_crtmemdifference –](crtmemdifference.md) pro zjištění nevracení paměti a dalších problémů. Když [_DEBUG](../../c-runtime-library/debug.md) není definován, jsou volání **_CrtMemState** odstraněna během předběžného zpracování.

Aplikace musí předat ukazatel dříve přiřazenou instanci **_CrtMemState** struktury definované v souboru Crtdbg.h, v *stavu* parametru. Pokud **_crtmemcheckpoint –** zjistí chybu během vytváření kontrolních bodů, funkce vygeneruje **_CRT_WARN** ladění zprávu s popisem problému.

Další informace o funkcích stavu haldy a **_CrtMemState** struktury, přečtěte si téma [funkce vykazování stavu haldy](/visualstudio/debugger/crt-debug-heap-details). Další informace o způsobu jsou bloky paměti přidělené, inicializovat a správy v ladicí verzi základní haldy viz [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

Pokud *stavu* je **NULL**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) je nastavena na **EINVAL** a funkce vrátí.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtMemCheckpoint**|\<crtdbg.h>, \<errno.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

**Knihovny:** verze ladění knihoven pouze UCRT.

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[_CrtMemDifference](crtmemdifference.md)<br/>
