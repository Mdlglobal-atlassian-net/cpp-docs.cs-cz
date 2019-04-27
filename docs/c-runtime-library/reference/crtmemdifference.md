---
title: _CrtMemDifference
ms.date: 11/04/2016
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
helpviewer_keywords:
- CrtMemDifference function
- _CrtMemDifference function
ms.assetid: 0f327278-b551-482f-958b-76941f796ba4
ms.openlocfilehash: f2c6306bf604737d0ace142674b21845a08e2dee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62339465"
---
# <a name="crtmemdifference"></a>_CrtMemDifference

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
Ukazatel **_CrtMemState** struktura, která se používá k ukládání rozdílů mezi dvěma stavy paměti (vrátil).

*oldState*<br/>
Ukazatel na dřívější stav paměti (**_CrtMemState** struktura).

*Nový stav*<br/>
Ukazatel na pozdější stav paměti (**_CrtMemState** struktura).

## <a name="return-value"></a>Návratová hodnota

Pokud stavy paměti výrazně liší, **_crtmemdifference –** vrátí hodnotu TRUE. V opačném případě vrátí funkce hodnotu FALSE.

## <a name="remarks"></a>Poznámky

**_Crtmemdifference –** funkce porovná *oldState* a *newState* a uloží jejich rozdíl do *stateDiff*, který lze potom používat aplikace pro zjištění nevracení paměti a dalších problémů s pamětí. Když [_DEBUG](../../c-runtime-library/debug.md) není definován, jsou volání **_crtmemdifference –** odstraněna během předběžného zpracování.

*Nový stav* a *oldState* musí být platný ukazatel **_CrtMemState** struktury definované v souboru Crtdbg.h, která byla vyplněna pomocí [_crtmemcheckpoint –](crtmemcheckpoint.md)před voláním **_crtmemdifference –**. *stateDiff* musí být ukazatel na dříve přidělenou instanci **_CrtMemState** struktury. Pokud *stateDiff*, *newState*, nebo *oldState* je **NULL**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [ Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) je nastavena na **EINVAL** a funkce vrátí hodnotu FALSE.

**_Crtmemdifference –** porovnává **_CrtMemState** pole hodnoty bloků v *oldState* těm v *newState* a uloží výsledek v *stateDiff*. Pokud se počet přidělených typů bloků nebo celkový počet přidělených bloků pro jednotlivé typy liší mezi dvěma stavy paměti, stavy se označují jako významně odlišné. Rozdíl mezi největším množstvím, kdy přiděleno současně oběma stavům a rozdíl mezi celkovým přidělením pro dva stavy jsou také uloženy v *stateDiff*.

Ve výchozím nastavení vnitřní bloky C run-time (**_CRT_BLOCK**) nejsou součástí operací stavu paměti. [_CrtSetDbgFlag](crtsetdbgflag.md) funkce je možné zapnout **_CRTDBG_CHECK_CRT_DF** bit z **_crtDbgFlag** pro zahrnutí těchto bloků do detekce nevrácení paměti a dalších stavu paměti operace. Uvolnění paměťových bloků (**_FREE_BLOCK**) nezpůsobí **_crtmemdifference –** vrátí hodnotu TRUE.

Další informace o funkcích stavu haldy a **_CrtMemState** struktury, přečtěte si téma [funkce vykazování stavu haldy](/visualstudio/debugger/crt-debug-heap-details). Informace o způsobu jsou bloky paměti přidělené, inicializovat a správy v ladicí verzi základní haldy viz [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_CrtMemDifference**|\<crtdbg.h>|\<errno.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

**Knihovny:** Ladicí verze [funkce knihovny CRT](../../c-runtime-library/crt-library-features.md) pouze.

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
