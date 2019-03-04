---
title: Cdefaultcomparetraits – třída
ms.date: 11/04/2016
f1_keywords:
- CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElements
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElementsOrdered
helpviewer_keywords:
- CDefaultCompareTraits class
ms.assetid: a17e2740-e7b4-48f2-aeb7-c80ce84b63f7
ms.openlocfilehash: c5f4ab3737838af11501c4a0f2037b57087939c9
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57273592"
---
# <a name="cdefaultcomparetraits-class"></a>Cdefaultcomparetraits – třída

Tato třída poskytuje výchozí element porovnání funkcí.

## <a name="syntax"></a>Syntaxe

```
template<typename T>
class CDefaultCompareTraits
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ dat uložených v kolekci.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDefaultCompareTraits::CompareElements](#compareelements)|(Statické) Voláním této funkce porovnání rovnosti dvou prvků.|
|[CDefaultCompareTraits::CompareElementsOrdered](#compareelementsordered)|(Statické) Voláním této funkce pro zjištění větší a menší elementu.|

## <a name="remarks"></a>Poznámky

Tato třída obsahuje dvě statické funkce pro porovnání prvků uložených v objektu třídy kolekce. Tato třída je využíváno [cdefaultelementtraits – třída](../../atl/reference/cdefaultelementtraits-class.md).

Další informace najdete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

##  <a name="compareelements"></a>  CDefaultCompareTraits::CompareElements

Voláním této funkce porovnání rovnosti dvou prvků.

```
static bool CompareElements(const T& element1, const T& element2);
```

### <a name="parameters"></a>Parametry

*element1*<br/>
První prvek.

*element2*<br/>
Druhý prvek.

### <a name="return-value"></a>Návratová hodnota

Vrátí true, pokud prvky jsou stejné, jinak hodnota false.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce je rovnost (**==**) – operátor. Z objektů kromě jednoduché datové typy tato funkce možná muset být přepsána.

##  <a name="compareelementsordered"></a>  CDefaultCompareTraits::CompareElementsOrdered

Voláním této funkce pro zjištění větší a menší elementu.

```
static int CompareElementsOrdered(const T& element1, const T& element2);
```

### <a name="parameters"></a>Parametry

*element1*<br/>
První prvek.

*element2*<br/>
Druhý prvek.

### <a name="return-value"></a>Návratová hodnota

Vrátí celé číslo, na základě následující tabulky:

|Podmínka|Návratová hodnota|
|---------------|------------------|
|*element1* < *element2*|<0|
|*element1* == *element2*|0|
|*element1* > *element2*|>0|

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce používá **==**, **\<**, a **>** operátory. Z objektů kromě jednoduché datové typy tato funkce možná muset být přepsána.

## <a name="see-also"></a>Viz také:

[Přehled tříd](../../atl/atl-class-overview.md)
