---
title: feholdexcept
ms.date: 04/05/2018
api_name:
- feholdexcept
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- feholdexcept
- fenv/feholdexcept
helpviewer_keywords:
- feholdexcept function
ms.assetid: 88e512ae-b5d8-452c-afe9-c824cd3ef1d8
ms.openlocfilehash: bd55a4ed627d731f7246d589d4b74b4173e31d4e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941191"
---
# <a name="feholdexcept"></a>feholdexcept

Uloží aktuální prostředí s plovoucí desetinnou čárkou v zadaném objektu, vymaže příznaky stavu s plovoucí desetinnou čárkou a pokud je to možné, umístí prostředí s plovoucí desetinnou čárkou do režimu bez zastavení.

## <a name="syntax"></a>Syntaxe

```C
int feholdexcept(
   fenv_t *penv
);
```

### <a name="parameters"></a>Parametry

*penv*<br/>
Ukazatel na objekt **fenv_t** , který obsahuje kopii prostředí s plovoucí desetinnou čárkou.

## <a name="return-value"></a>Návratová hodnota

Vrátí nulu pouze v případě, že funkce může úspěšně zapnout zpracování výjimek s plovoucí desetinnou čárkou.

## <a name="remarks"></a>Poznámky

Funkce **feholdexcept** se používá k uložení stavu aktuálního prostředí s plovoucí desetinnou čárkou v objektu **fenv_t** , na který odkazuje *penv*, a k nastavení prostředí tak, aby se nepřerušilo provádění u výjimek s plovoucí desetinnou čárkou. Tento stav je známý jako režim bez zastavení.  Tento režim pokračuje, dokud se prostředí neobnoví pomocí [fesetenv](fesetenv1.md) nebo [feupdateenv](feupdateenv.md).

Tuto funkci můžete použít na začátku subrutiny, které potřebují skrýt jednu nebo více výjimek s plovoucí desetinnou čárkou od volajícího. Chcete-li ohlásit výjimku, můžete jednoduše vymazat nechtěné výjimky pomocí [feclearexcept](feclearexcept1.md) a poté ukončit režim bez zastavení volání **feupdateenv**.

Chcete-li použít tuto funkci, je nutné vypnout optimalizace plovoucí desetinné čárky, které by mohly zabránit přístupu `#pragma fenv_access(on)` pomocí direktivy před voláním. Další informace najdete v tématu [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička jazyka C|C++hlaviček|
|--------------|--------------|------------------|
|**feholdexcept**|\<fenv. h >|\<cfenv>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[fesetenv](fesetenv1.md)<br/>
[feupdateenv](feupdateenv.md)<br/>
