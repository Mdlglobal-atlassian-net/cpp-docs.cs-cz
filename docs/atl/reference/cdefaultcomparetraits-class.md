---
title: Třída CDefaultCompareTraits
ms.date: 11/04/2016
f1_keywords:
- CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElements
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElementsOrdered
helpviewer_keywords:
- CDefaultCompareTraits class
ms.assetid: a17e2740-e7b4-48f2-aeb7-c80ce84b63f7
ms.openlocfilehash: 8262800ef613424c37c53931d97dd4b1b1a71321
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327066"
---
# <a name="cdefaultcomparetraits-class"></a>Třída CDefaultCompareTraits

Tato třída poskytuje výchozí funkce porovnání prvků.

## <a name="syntax"></a>Syntaxe

```
template<typename T>
class CDefaultCompareTraits
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ dat, která mají být uložena v kolekci.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CDefaultCompareTraits::Porovnatprvky](#compareelements)|(Statické) Volání této funkce porovnat dva prvky rovnosti.|
|[CDefaultCompareTraits::CompareElementsOrdered](#compareelementsordered)|(Statické) Volání této funkce k určení větší a menší prvek.|

## <a name="remarks"></a>Poznámky

Tato třída obsahuje dvě statické funkce pro porovnání prvků uložených v objektu třídy kolekce. Tato třída je využívána [třídou CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md).

Další informace naleznete v tématu [třídy kolekce klíčů ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

## <a name="cdefaultcomparetraitscompareelements"></a><a name="compareelements"></a>CDefaultCompareTraits::Porovnatprvky

Volání této funkce porovnat dva prvky rovnosti.

```
static bool CompareElements(const T& element1, const T& element2);
```

### <a name="parameters"></a>Parametry

*element1*<br/>
První prvek.

*element2*<br/>
Druhý prvek.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud jsou prvky stejné, false otherwise.

### <a name="remarks"></a>Poznámky

Výchozí implementací této funkce je**==** operátor rovnosti ( ). U jiných objektů než jednoduchých datových typů může být nutné tuto funkci přepsat.

## <a name="cdefaultcomparetraitscompareelementsordered"></a><a name="compareelementsordered"></a>CDefaultCompareTraits::CompareElementsOrdered

Volání této funkce k určení větší a menší prvek.

```
static int CompareElementsOrdered(const T& element1, const T& element2);
```

### <a name="parameters"></a>Parametry

*element1*<br/>
První prvek.

*element2*<br/>
Druhý prvek.

### <a name="return-value"></a>Návratová hodnota

Vrátí celé číslo na základě následující tabulky:

|Podmínka|Návratová hodnota|
|---------------|------------------|
|*element1* < *element2*|<0|
|*element1* == *element2*|0|
|*element1* > *element2*|> 0|

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce **==** používá **\<**, **>** a operátory. U jiných objektů než jednoduchých datových typů může být nutné tuto funkci přepsat.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
