---
title: __dllonexit
ms.date: 11/04/2016
api_name:
- __dllonexit
api_location:
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcr120_clr0400.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __dllonexit
helpviewer_keywords:
- __dllonexit
ms.assetid: 708f2ceb-f95c-46b0-a58d-d68b3fa36f12
ms.openlocfilehash: 61d63c751dd755bf8a7680c674681e114945814b
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940436"
---
# <a name="__dllonexit"></a>__dllonexit

Registruje rutinu, která bude volána v době ukončení.

## <a name="syntax"></a>Syntaxe

```
_onexit_t __dllonexit(   _onexit_t func,
   _PVFV **  pbegin,
   _PVFV **  pend
   )
```

#### <a name="parameters"></a>Parametry

*func*<br/>
Ukazatel na funkci, která má být provedena po ukončení.

*pbegin*<br/>
Ukazatel na proměnnou, která odkazuje na začátek seznamu funkcí, které mají být provedeny při odpojení.

*čekání*<br/>
Ukazatel na proměnnou, která odkazuje na konec seznamu funkcí, které mají být provedeny při odpojení.

## <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, ukazatel na funkci uživatele. V opačném případě ukazatel s **hodnotou null** .

## <a name="remarks"></a>Poznámky

Funkce je analogická funkci _onexit s tím rozdílem, že globální proměnné používané touto funkcí nejsou pro tuto rutinu viditelné. [](../c-runtime-library/reference/onexit-onexit-m.md) `__dllonexit` Namísto globálních proměnných Tato funkce používá `pbegin` parametry a. `pend`

Funkce `_onexit` a`atexit` v knihovně DLL propojené s knihovnou Msvcrt. LIB musí udržovat svůj vlastní seznam atexit/_onexit. Tato rutina je pracovní proces, který volají takové knihovny DLL.

Typ je definován jako `typedef void (__cdecl *_PVFV)(void)`. `_PVFV`

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný soubor|
|-------------|-------------------|
|__dllonexit|onexit.c|

## <a name="see-also"></a>Viz také:

[_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)
