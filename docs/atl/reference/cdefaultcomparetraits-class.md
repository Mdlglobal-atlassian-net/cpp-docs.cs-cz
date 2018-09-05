---
title: Cdefaultcomparetraits – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElements
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElementsOrdered
dev_langs:
- C++
helpviewer_keywords:
- CDefaultCompareTraits class
ms.assetid: a17e2740-e7b4-48f2-aeb7-c80ce84b63f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f4983984c8bf1cad2996818625091b60cdb732a9
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43758554"
---
# <a name="cdefaultcomparetraits-class"></a>Cdefaultcomparetraits – třída

Tato třída poskytuje výchozí element porovnání funkcí.

## <a name="syntax"></a>Syntaxe

```
template<typename T>  
class CDefaultCompareTraits
```

#### <a name="parameters"></a>Parametry

*T*  
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

*element1*  
První prvek.

*element2*  
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

*element1*  
První prvek.

*element2*  
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

## <a name="see-also"></a>Viz také

[Přehled tříd](../../atl/atl-class-overview.md)
