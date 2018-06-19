---
title: _Crtmemdifference – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtMemDifference
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
- _CrtMemDifference
- CrtMemDifference
dev_langs:
- C++
helpviewer_keywords:
- CrtMemDifference function
- _CrtMemDifference function
ms.assetid: 0f327278-b551-482f-958b-76941f796ba4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 66bb770c2f24c0312277d23c14beef09e2265f88
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32398044"
---
# <a name="crtmemdifference"></a>_CrtMemDifference

Porovná dva paměti stavy a vrátí rozdíly mezi nimi (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
int _CrtMemDifference(
   _CrtMemState *stateDiff,
   const _CrtMemState *oldState,
   const _CrtMemState *newState
);
```

### <a name="parameters"></a>Parametry

*stateDiff*<br/>
Ukazatel na **_crtmemstate –** struktura, která se používá k ukládání rozdíly mezi stavy dvě paměti (nevrátil).

*oldState*<br/>
Ukazatel předchozího stavu paměti (**_crtmemstate –** struktura).

*Nový stav*<br/>
Ukazatel na novější stav paměti (**_crtmemstate –** struktura).

## <a name="return-value"></a>Návratová hodnota

Pokud stavy paměť se výrazně liší, **_crtmemdifference –** vrátí hodnotu TRUE. Funkce, jinak vrátí hodnotu FALSE.

## <a name="remarks"></a>Poznámky

**_Crtmemdifference –** funkce porovná *oldState* a *nový stav* a ukládá jejich rozdíly v *stateDiff*, což může potom se používá aplikace ke zjišťování nevracení paměti a jiných problémů paměti. Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, volání **_crtmemdifference –** jsou odebrány při předběžném zpracování.

*Nový stav* a *oldState* musí být platný ukazatel **_crtmemstate –** struktuře, definované v Crtdbg.h, který má byla vyplněna objektem [_crtmemcheckpoint –](crtmemcheckpoint.md)před voláním **_crtmemdifference –**. *stateDiff* musí být ukazatel na dříve přidělené instanci **_crtmemstate –** struktura. Pokud *stateDiff*, *nový stav*, nebo *oldState* je **NULL**, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) je nastaven na **einval –** , funkce vrátí hodnotu FALSE.

**_Crtmemdifference –** porovná **_crtmemstate –** pole hodnoty bloků v *oldState* na hodnoty v *nový stav* a ukládá výsledky v *stateDiff*. Počet přidělené bloku typů nebo mezi dvěma paměti stavy liší celkový počet přidělených bloků pro každý typ, jsou stavy označeny jako výrazně lišit. Rozdíl mezi největší velikost někdy přidělené najednou dva stavy a rozdíl mezi celkový přidělení pro dva stavy jsou také uloženy v *stateDiff*.

Ve výchozím nastavení, interní bloky C Runtime (**_crt_block –**) nejsou zahrnuty v operacích stavu paměti. [_Crtsetdbgflag –](crtsetdbgflag.md) funkce slouží k zapnutí **_crtdbg_check_crt_df –** bit z **_crtdbgflag –** zahrnout tyto bloky v úniku zjišťování a další stav paměti operace. Vydání bloky paměti (**_free_block –**) nezpůsobí **_crtmemdifference –** vrátí hodnotu TRUE.

Další informace o stavu funkce hald a **_crtmemstate –** struktury najdete v tématu [funkce vytváření sestav stavu haldy](/visualstudio/debugger/crt-debug-heap-details). Informace o tom, jak jsou bloky paměti přidělené, inicializovat a spravovat ladicí verze základní heap najdete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|
|-------------|---------------------|---------------------|
|**_CrtMemDifference**|\<crtdbg.h>|\<errno.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

**Knihovny:** ladicí verze [funkce knihovny CRT](../../c-runtime-library/crt-library-features.md) pouze.

## <a name="see-also"></a>Viz také

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
