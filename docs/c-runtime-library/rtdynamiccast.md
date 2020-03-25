---
title: __RTDynamicCast
ms.date: 11/04/2016
api_name:
- __RTDynamicCast
api_location:
- msvcr90.dll
- msvcr110.dll
- msvcr120.dll
- msvcrt.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __RTDynamicCast
helpviewer_keywords:
- __RTDynamicCast
ms.assetid: 56aa2d7a-aa47-46ef-830d-e37175611239
ms.openlocfilehash: a5384966ff96c4e4831ba06f7c67467156a9ecd2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170069"
---
# <a name="__rtdynamiccast"></a>__RTDynamicCast

Běhová implementace operátoru [dynamic_cast](../cpp/dynamic-cast-operator.md)

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
Ukazatel na polymorfní objekt.

*VfDelta*<br/>
Posun ukazatele virtuální funkce v objektu

*SrcType*<br/>
Statický typ objektu, na který ukazuje parametr `inptr`.

*TargetType*<br/>
Zamýšlený výsledek funkce CAST

*isReference*<br/>
**true** , pokud je vstup odkazem; **false** , pokud je vstup ukazatelem.

## <a name="return-value"></a>Návratová hodnota

Ukazatel na příslušný dílčí objekt, pokud je úspěšný; v opačném případě **hodnota null**.

## <a name="exceptions"></a>Výjimky

`bad_cast()`, pokud je vstup `dynamic_cast<>` odkazem a přetypování se nezdařilo.

## <a name="remarks"></a>Poznámky

Převede `inptr` na objekt typu `TargetType`. Typ `inptr` musí být ukazatel, pokud `TargetType` je ukazatel nebo l-hodnota, pokud je `TargetType` odkazem. `TargetType` musí být ukazatel nebo odkaz na dříve definovaný typ třídy nebo ukazatel na void.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|__RTDynamicCast|rtti.h|
