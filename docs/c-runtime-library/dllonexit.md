---
title: __dllonexit
ms.date: 11/04/2016
apiname:
- __dllonexit
apilocation:
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcr120_clr0400.dll
apitype: DLLExport
f1_keywords:
- __dllonexit
helpviewer_keywords:
- __dllonexit
ms.assetid: 708f2ceb-f95c-46b0-a58d-d68b3fa36f12
ms.openlocfilehash: 70e69952e350f96179298e2d64ec6ddf7b9167bc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50625417"
---
# <a name="dllonexit"></a>__dllonexit

Registruje rutiny volat na čas ukončení.

## <a name="syntax"></a>Syntaxe

```
_onexit_t __dllonexit(   _onexit_t func,
   _PVFV **  pbegin,
   _PVFV **  pend
   )
```

#### <a name="parameters"></a>Parametry

*Func*<br/>
Ukazatel na funkci má být spuštěn při ukončení.

*pbegin*<br/>
Ukazatel na proměnnou, která odkazuje na začátku seznamu funkcí se promítnou u odpojit.

*Čekání*<br/>
Ukazatel na proměnnou, která odkazuje na konec seznamu funkcí se promítnou u odpojit.

## <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, ukazatel na funkci uživatele. V opačném případě **NULL** ukazatele.

## <a name="remarks"></a>Poznámky

`__dllonexit` Funkce je obdobou [_onexit](../c-runtime-library/reference/onexit-onexit-m.md) fungovat s tím rozdílem, že nejsou viditelné pro tato rutina globálních proměnných používat tuto funkci. Místo globální proměnné, tato funkce využívá `pbegin` a `pend` parametry.

`_onexit` a `atexit` funkce v knihovně DLL propojené s MSVCRT. LIB musíte spravovat vlastní seznam atexit/_onexit. Tato rutina je pracovního procesu, která je volána pomocí těchto knihoven DLL.

`_PVFV` Typ je definován jako `typedef void (__cdecl *_PVFV)(void)`.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný soubor|
|-------------|-------------------|
|__dllonexit|onexit.c|

## <a name="see-also"></a>Viz také

[_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)