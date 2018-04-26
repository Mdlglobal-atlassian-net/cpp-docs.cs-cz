---
title: _Crtmemcheckpoint – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CrtMemCheckpoint function
- _CrtMemCheckpoint function
ms.assetid: f1bacbaa-5a0c-498a-ac7a-b6131d83dfbc
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 80f9d0b88e5bf1195ca8097e4cfbab5ba97942d7
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="crtmemcheckpoint"></a>_CrtMemCheckpoint

Získá aktuální stav haldy ladění a ukládá do poskytované aplikací **_crtmemstate –** struktury (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
void _CrtMemCheckpoint(
   _CrtMemState *state
);
```

### <a name="parameters"></a>Parametry

*Stav* ukazatel na **_crtmemstate –** struktura vyplníte paměti kontrolního bodu.

## <a name="remarks"></a>Poznámky

**_Crtmemcheckpoint –** funkce vytvoří snímek aktuálního stavu haldy ladění jakémkoli okamžiku. Tento snímek mohou být využívána jiných haldy stav funkcí, jako [_crtmemdifference –](crtmemdifference.md) abyste odhalili nevracení paměti a jiné problémy. Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, volání **_crtmemstate –** jsou odebrány při předběžném zpracování.

Aplikace musí předat ukazatel dříve přidělené instanci **_crtmemstate –** struktuře, které jsou definované v Crtdbg.h, v *stavu* parametr. Pokud **_crtmemcheckpoint –** generuje pro komunikaci se chyba při vytváření kontrolního bodu, funkce **_CRT_WARN** ladění sestava popisující problém.

Další informace o stavu funkce hald a **_crtmemstate –** struktury najdete v tématu [funkce vytváření sestav stavu haldy](/visualstudio/debugger/crt-debug-heap-details). Další informace o tom, jak jsou bloky paměti přidělené, inicializovat a spravovat ladicí verze základní heap najdete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

Pokud *stavu* je **NULL**, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) je nastaven na **einval –** a funkce vrátí hodnotu.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtMemCheckpoint**|\<crtdbg.h>, \<errno.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

**Knihovny:** ladicí verze pouze UCRT.

## <a name="see-also"></a>Viz také

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[_CrtMemDifference](crtmemdifference.md)<br/>
