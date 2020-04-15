---
title: Třída CDefaultCharits
ms.date: 11/04/2016
f1_keywords:
- CDefaultCharTraits
- ATLCOLL/ATL::CDefaultCharTraits
- ATLCOLL/ATL::CDefaultCharTraits::CharToLower
- ATLCOLL/ATL::CDefaultCharTraits::CharToUpper
helpviewer_keywords:
- CDefaultCharTraits class
ms.assetid: f94a3934-597f-401d-8513-ed6924ae069a
ms.openlocfilehash: 40c4d107d05e6d7b610e7c46be920d91d8fe6086
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327096"
---
# <a name="cdefaultchartraits-class"></a>Třída CDefaultCharits

Tato třída poskytuje dvě statické funkce pro převod znaků mezi velkými a velkými písmeny.

## <a name="syntax"></a>Syntaxe

```
template <typename T>
class CDefaultCharTraits
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ dat, která mají být uložena v kolekci.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CDefaultCharTraits::CharToLower](#chartolower)|(Statické) Volánítéto funkce převést znak na velká písmena.|
|[CDefaultCharTraits::CharToUpper](#chartoupper)|(Statické) Volání této funkce převést znak na malá písmena.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje funkce, které jsou využívány třídy [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

## <a name="cdefaultchartraitschartolower"></a><a name="chartolower"></a>CDefaultCharTraits::CharToLower

Volání této funkce převést znak na malá písmena.

```
static wchar_t CharToLower(wchar_t x);
static char CharToLower(char x);
```

### <a name="parameters"></a>Parametry

*X*<br/>
Znak převést na malá písmena.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#132](../../atl/codesnippet/cpp/cdefaultchartraits-class_1.cpp)]

## <a name="cdefaultchartraitschartoupper"></a><a name="chartoupper"></a>CDefaultCharTraits::CharToUpper

Volánítéto funkce převést znak na velká písmena.

```
static wchar_t CharToUpper(wchar_t x);
static char CharToUpper(char x);
```

### <a name="parameters"></a>Parametry

*X*<br/>
Znak převést na velká písmena.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
