---
title: _CrtMemCheckpoint
ms.date: 11/04/2016
api_name:
- _CrtMemCheckpoint
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
- CrtMemCheckpoint
- _CrtMemCheckpoint
- crtdbg/_CrtMemCheckpoint
helpviewer_keywords:
- CrtMemCheckpoint function
- _CrtMemCheckpoint function
ms.assetid: f1bacbaa-5a0c-498a-ac7a-b6131d83dfbc
ms.openlocfilehash: edf91cd8c76fd080326e2e5eeac98f7f81ab90cf
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942362"
---
# <a name="_crtmemcheckpoint"></a>_CrtMemCheckpoint

Získá aktuální stav haldy ladění a uloží je do **_CrtMemState** struktury dodané aplikací (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
void _CrtMemCheckpoint(
   _CrtMemState *state
);
```

### <a name="parameters"></a>Parametry

*státech*<br/>
Ukazatel na strukturu **_CrtMemState** , která se zaplní pomocí kontrolního bodu paměti.

## <a name="remarks"></a>Poznámky

Funkce **_CrtMemCheckpoint** vytvoří snímek aktuálního stavu haldy ladění v daném okamžiku. Tento snímek můžou použít jiné funkce stavu haldy, jako je [_CrtMemDifference](crtmemdifference.md) , které vám pomůžou detekovat nevracení paměti a další problémy. Když není definovaný [_DEBUG](../../c-runtime-library/debug.md) , volání **_CrtMemState** se během předběžného zpracování odeberou.

Aplikace musí předat ukazatel na dříve přidělenou instanci struktury **_CrtMemState** definované v souboru Crtdbg. h v parametru *State* . Pokud **_CrtMemCheckpoint** při vytváření kontrolního bodu narazí na chybu, funkce vygeneruje zprávu ladění **_CRT_WARN** popisující problém.

Další informace o funkcích stavu haldy a struktuře **_CrtMemState** naleznete v tématu [funkce vytváření sestav o stavu haldy](/visualstudio/debugger/crt-debug-heap-details). Další informace o způsobu přidělování, inicializace a správy paměťových bloků v ladicí verzi základní haldy najdete v [podrobnostech o haldě ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

Pokud je stav **null**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) je nastaveno na **EINVAL** a funkce vrátí.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtMemCheckpoint**|\<crtdbg.h>, \<errno.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

**Knihovna** Ladit verze pouze UCRT.

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[_CrtMemDifference](crtmemdifference.md)<br/>
