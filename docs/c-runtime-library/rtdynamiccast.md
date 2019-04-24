---
title: __RTDynamicCast
ms.date: 11/04/2016
apiname:
- __RTDynamicCast
apilocation:
- msvcr90.dll
- msvcr110.dll
- msvcr120.dll
- msvcrt.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
apitype: DLLExport
f1_keywords:
- __RTDynamicCast
helpviewer_keywords:
- __RTDynamicCast
ms.assetid: 56aa2d7a-aa47-46ef-830d-e37175611239
ms.openlocfilehash: f4bf4895af99b2d5c2d61e739c9d49d59cecb020
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62184525"
---
# <a name="rtdynamiccast"></a>__RTDynamicCast

Implementace modulu runtime [dynamic_cast](../cpp/dynamic-cast-operator.md) operátor.

## <a name="syntax"></a>Syntaxe

```cpp
PVOID __RTDynamicCast (
   PVOID inptr,
   LONG VfDelta,
   PVOID SrcType,
   PVOID TargetType,
   BOOL isReference
   ) throw(...)
```

#### <a name="parameters"></a>Parametry

*inptr*<br/>
Ukazatel na objekt polymorfní.

*VfDelta*<br/>
Posun ukazatele virtuální funkce objektu.

*SrcType*<br/>
Statický typ objektu, na které odkazují `inptr` parametru.

*TargetType*<br/>
Požadovaný výsledek přetypování.

*isReference*<br/>
**Hodnota TRUE** Pokud vstup je odkaz; **false** při vstupu ukazatele.

## <a name="return-value"></a>Návratová hodnota

Ukazatel na odpovídající dílčí objekt, v případě úspěchu; v opačném případě **NULL**.

## <a name="exceptions"></a>Výjimky

`bad_cast()` Pokud vstup do `dynamic_cast<>` je odkaz a přetypování se nezdaří.

## <a name="remarks"></a>Poznámky

Převede `inptr` na objekt typu `TargetType`. Typ `inptr` musí být ukazatel, pokud `TargetType` je ukazatel nebo l hodnotou, pokud `TargetType` je odkaz. `TargetType` musí být ukazatel nebo odkaz na typ dříve definicí třídy nebo ukazatel na typ void.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|__RTDynamicCast|rtti.h|