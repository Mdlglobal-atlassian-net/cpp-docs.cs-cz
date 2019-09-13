---
title: fesetenv
ms.date: 04/05/2018
api_name:
- fesetenv
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
- fesetenv
- fenv/fesetenv
helpviewer_keywords:
- fesetenv function
ms.assetid: ffc64fff-8ea7-4d59-9e04-ff96ef8cd012
ms.openlocfilehash: 155b9f635f6e8c3dc5acb61126f41c49cd32601f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941114"
---
# <a name="fesetenv"></a>fesetenv

Nastaví aktuální prostředí s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
int fesetenv(
   const fenv_t *penv
);
```

### <a name="parameters"></a>Parametry

*penv*<br/>
Ukazatel na objekt **fenv_t** , který obsahuje prostředí s plovoucí desetinnou čárkou, jak je nastaveno voláním [fegetenv](fegetenv1.md) nebo [feholdexcept](feholdexcept2.md). Pomocí makra **FE_DFL_ENV** můžete také určit výchozí prostředí s plovoucí desetinnou čárkou, které je spouštěno.

## <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu 0, pokud bylo prostředí úspěšně nastaveno. V opačném případě vrátí nenulovou hodnotu.

## <a name="remarks"></a>Poznámky

Funkce **fesetenv** nastaví aktuální prostředí s plovoucí desetinnou čárkou z hodnoty uložené v objektu **fenv_t** , na kterou odkazuje *penv*. Prostředí s plovoucí desetinnou čárkou je sada příznaků stavu a řídicích režimů, které ovlivňují výpočty s plovoucí desetinnou čárkou. To zahrnuje režim zaokrouhlení a příznaky stavu pro výjimky s plovoucí desetinnou čárkou.  Pokud *penv* není **FE_DFL_ENV** nebo neukazuje na platný objekt **fenv_t** , následné chování není definováno.

Volání této funkce nastaví příznaky stavu výjimky, které jsou v objektu *penv* , ale nevyvolává tyto výjimky.

Chcete-li použít tuto funkci, je nutné vypnout optimalizace plovoucí desetinné čárky, které by mohly zabránit přístupu `#pragma fenv_access(on)` pomocí direktivy před voláním. Další informace najdete v tématu [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička jazyka C|C++hlaviček|
|--------------|--------------|------------------|
|**fesetenv**|\<fenv. h >|\<cfenv>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[fegetenv](fegetenv1.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
