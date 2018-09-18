---
title: __dllonexit | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
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
dev_langs:
- C++
helpviewer_keywords:
- __dllonexit
ms.assetid: 708f2ceb-f95c-46b0-a58d-d68b3fa36f12
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0c2c04f623ba8cac2f3b967007079d41689d2346
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062862"
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