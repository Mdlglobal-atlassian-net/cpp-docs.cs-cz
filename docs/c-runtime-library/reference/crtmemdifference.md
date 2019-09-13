---
title: _CrtMemDifference
ms.date: 11/04/2016
api_name:
- _CrtMemDifference
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
- _CrtMemDifference
- CrtMemDifference
helpviewer_keywords:
- CrtMemDifference function
- _CrtMemDifference function
ms.assetid: 0f327278-b551-482f-958b-76941f796ba4
ms.openlocfilehash: 51bfa014d54f55843fcb112f318f143774abf8f3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938713"
---
# <a name="_crtmemdifference"></a>_CrtMemDifference

Porovná dva stavy paměti a vrátí jejich rozdíly (pouze ladicí verze).

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
Ukazatel na strukturu **_CrtMemState** , která se používá k uložení rozdílů mezi dvěma stavy paměti (vráceno).

*oldState*<br/>
Ukazatel na předchozí stav paměti (struktura **_CrtMemState** ).

*newState*<br/>
Ukazatel na pozdější stav paměti (struktura **_CrtMemState** ).

## <a name="return-value"></a>Návratová hodnota

Pokud jsou stavy paměti výrazně odlišné, vrátí **_CrtMemDifference** hodnotu true. V opačném případě vrátí funkce hodnotu FALSE.

## <a name="remarks"></a>Poznámky

Funkce **_CrtMemDifference** porovnává *oldState* a *newState* a ukládá rozdíly v *stateDiff*, které mohou být použity aplikací k detekci nevracení paměti a dalších problémů s pamětí. Když není definovaný [_DEBUG](../../c-runtime-library/debug.md) , volání **_CrtMemDifference** se během předběžného zpracování odeberou.

*newState* a *oldState* musí být platný ukazatel na strukturu **_CrtMemState** definovanou v souboru Crtdbg. h, která byla před voláním metody **_CrtMemCheckpoint**vyplněna [_CrtMemDifference](crtmemcheckpoint.md) . *stateDiff* musí být ukazatel na dříve přidělenou instanci struktury **_CrtMemState** . Pokud je *stateDiff*, *newState*nebo *oldState* **null**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) je nastaveno na **EINVAL** a funkce vrátí false.

**_CrtMemDifference** porovnává hodnoty polí **_CrtMemState** bloků v *oldState* s hodnotami v *newState* a ukládá výsledek do *stateDiff*. Pokud se počet přidělených typů bloku nebo celkový počet přidělených bloků pro každý typ liší mezi dvěma stavy paměti, jsou stavy označeny jako výrazně odlišné. Rozdíl mezi největším množstvím, které se v současné době přiděluje najednou pro tyto dva stavy, a rozdíl mezi celkovým přidělením těchto dvou stavů je také uložený v *stateDiff*.

Ve výchozím nastavení nejsou interní bloky C run-time ( **_CRT_BLOCK**) zahrnuty do operací stavu paměti. Funkci [_CrtSetDbgFlag](crtsetdbgflag.md) lze použít k zapnutí **_CRTDBG_CHECK_CRT_DF** bitu **_crtDbgFlag** pro zahrnutí těchto bloků do detekce nevracení a dalších operací stavu paměti. Uvolněné paměťové bloky ( **_FREE_BLOCK**) nezpůsobí, že **_CrtMemDifference** vrátí hodnotu true.

Další informace o funkcích stavu haldy a struktuře **_CrtMemState** naleznete v tématu [funkce vytváření sestav o stavu haldy](/visualstudio/debugger/crt-debug-heap-details). Informace o způsobu přidělování, inicializace a správy paměťových bloků v ladicí verzi základní haldy najdete v [podrobnostech o haldě ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_CrtMemDifference**|\<crtdbg.h>|\<errno.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

**Knihovna** Ladit verze pouze [funkcí knihoven CRT](../../c-runtime-library/crt-library-features.md) .

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
