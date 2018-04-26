---
title: _Crtmemdumpstatistics – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
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
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 69a96cf29d4cb9d7f6dbec3f079852beb528778d
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
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

*Stav* ukazatel na stavu haldy vypsat.

## <a name="remarks"></a>Poznámky

**_Crtmemdumpstatistics –** funkce výpisy ladění informace ze záhlaví zadaného stavu haldy ve formě uživatelem čitelný. Pomocí statistiky výpisu lze v aplikaci sledovat přidělování a vyhledávat problémy s pamětí. Stav paměti může obsahovat specifický stav haldy nebo rozdíl mezi dvěma stavy. Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, volání **_crtmemdumpstatistics –** jsou odebrány při předběžném zpracování.

*Stavu* parametr musí být ukazatel na **_crtmemstate –** struktura, která má byla vyplněna objektem [_crtmemcheckpoint –](crtmemcheckpoint.md) nebo vrácený [_ Crtmemdifference –](crtmemdifference.md) před **_crtmemdumpstatistics –** je volána. Pokud *stavu* je **NULL**, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění **errno** je nastaven na **einval –** a nebyla provedena žádná akce. Další informace najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Další informace o stavu funkce hald a **_crtmemstate –** struktury najdete v tématu [funkce vytváření sestav stavu haldy](/visualstudio/debugger/crt-debug-heap-details). Další informace o tom, jak jsou bloky paměti přidělené, inicializovat a spravovat ladicí verze základní heap najdete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné hlavičky|
|-------------|---------------------|----------------------|
|**_CrtMemDumpStatistics**|\<crtdbg.h>|\<errno.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

**Knihovny:** ladicí verze [funkce knihovny CRT](../../c-runtime-library/crt-library-features.md) pouze.

## <a name="see-also"></a>Viz také

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
