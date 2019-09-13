---
title: fegetenv
ms.date: 04/05/2018
api_name:
- fetegenv
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
- fegetenv
- fenv/fegetenv
helpviewer_keywords:
- fetegenv function
ms.assetid: 68962421-6978-4b27-8e4c-ad1577830cf6
ms.openlocfilehash: b2e3566eb96174d0f0ccd6beb401824cc052c995
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941249"
---
# <a name="fegetenv"></a>fegetenv

Ukládá aktuální prostředí s plovoucí desetinnou čárkou v zadaném objektu.

## <a name="syntax"></a>Syntaxe

```C
int fegetenv(
   fenv_t *penv
);
```

### <a name="parameters"></a>Parametry

*penv*<br/>
Ukazatel na objekt **fenv_t** , který obsahuje aktuální hodnoty prostředí s plovoucí desetinnou čárkou.

## <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu 0, pokud bylo prostředí s plovoucí desetinnou čárkou úspěšně uloženo v *penv*. V opačném případě vrátí nenulovou hodnotu.

## <a name="remarks"></a>Poznámky

Funkce **fegetenv** ukládá aktuální prostředí s plovoucí desetinnou čárkou v objektu, na který ukazuje *penv*. Prostředí s plovoucí desetinnou čárkou je sada příznaků stavu a řídicích režimů, které ovlivňují výpočty s plovoucí desetinnou čárkou. To zahrnuje režim směru zaokrouhlení a příznaky stavu pro výjimky s plovoucí desetinnou čárkou.  Pokud *penv* neodkazuje na platný objekt **fenv_t** , následné chování není definováno.

Chcete-li použít tuto funkci, je nutné vypnout optimalizace plovoucí desetinné čárky, které by mohly zabránit přístupu `#pragma fenv_access(on)` pomocí direktivy před voláním. Další informace najdete v tématu [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička jazyka C|C++hlaviček|
|--------------|--------------|------------------|
|**fegetenv**|\<fenv. h >|\<cfenv>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[fesetenv](fesetenv1.md)<br/>
