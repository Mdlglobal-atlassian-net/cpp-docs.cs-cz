---
title: feholdexcept
ms.date: 04/05/2018
apiname:
- feholdexcept
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- feholdexcept
- fenv/feholdexcept
helpviewer_keywords:
- feholdexcept function
ms.assetid: 88e512ae-b5d8-452c-afe9-c824cd3ef1d8
ms.openlocfilehash: 26097398b9f9d498ab4c56690dc9c6cbb950bafb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62334382"
---
# <a name="feholdexcept"></a>feholdexcept

Uloží aktuální prostředí s plovoucí desetinnou čárkou určeném objektu, vymaže příznaky stav s plovoucí desetinnou čárkou a, pokud je to možné, umístí do režimu bez zastavení s plovoucí desetinnou čárkou prostředí.

## <a name="syntax"></a>Syntaxe

```C
int feholdexcept(
   fenv_t *penv
);
```

### <a name="parameters"></a>Parametry

*penv*<br/>
Ukazatel **fenv_t** objekt obsahující kopii prostředí s plovoucí desetinnou čárkou.

## <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu nula a pouze v případě funkce je moct úspěšně zapnout zpracování výjimek s plovoucí desetinnou čárkou bez zastavení.

## <a name="remarks"></a>Poznámky

**Feholdexcept** funkce se používá k uložení stavu aktuální prostředí s plovoucí desetinnou čárkou bod v **fenv_t** objekt, který odkazuje *penv*a nastavit prostředí přerušit provádění na výjimky s plovoucí desetinnou čárkou. To se označuje jako režim bez zastavení.  Tento režim pokračuje, dokud prostředí je obnovit pomocí [fesetenv](fesetenv1.md) nebo [feupdateenv](feupdateenv.md).

Tuto funkci můžete použít na začátku podprogram, který je potřeba skrýt jeden nebo více výjimek plovoucí desetinné čárky od volajícího. Chcete-li ohlásit výjimku, jednoduše zrušte nechtěné výjimkami pomocí [feclearexcept,](feclearexcept1.md) a pak ukončit režim bez zastavení voláním **feupdateenv**.

Pokud chcete používat tuto funkci, musíte vypnout s plovoucí desetinnou čárkou optimalizace, které by mohla zabránit přístupu pomocí `#pragma fenv_access(on)` direktiv před voláním. Další informace najdete v tématu [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Požadavky

|Funkce|Záhlaví C|Hlaviček jazyka C++|
|--------------|--------------|------------------|
|**feholdexcept**|\<fenv.h>|\<cfenv>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[fesetenv](fesetenv1.md)<br/>
[feupdateenv](feupdateenv.md)<br/>
