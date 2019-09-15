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
ms.openlocfilehash: c4b0caadf20d6c5494acf47ee5a788b5ee009c47
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957331"
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
Statický typ objektu, na který `inptr` ukazuje parametr.

*TargetType*<br/>
Zamýšlený výsledek funkce CAST

*isReference*<br/>
**true** , pokud je vstup odkazem; **false** , pokud je vstup ukazatelem.

## <a name="return-value"></a>Návratová hodnota

Ukazatel na příslušný dílčí objekt, pokud je úspěšný; v opačném případě **hodnota null**.

## <a name="exceptions"></a>Výjimky

`bad_cast()`Pokud `dynamic_cast<>` je vstupem odkaz a přetypování se nezdařilo.

## <a name="remarks"></a>Poznámky

Převede `inptr` na objekt typu `TargetType`. Typ `inptr` musí být ukazatel, pokud `TargetType` je ukazatel nebo l-hodnota, pokud `TargetType` je odkazem. `TargetType`musí se jednat o ukazatel nebo odkaz na dříve definovaný typ třídy nebo ukazatel na void.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|__RTDynamicCast|rtti.h|