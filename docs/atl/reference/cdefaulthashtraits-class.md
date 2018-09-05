---
title: Cdefaulthashtraits – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits::Hash
dev_langs:
- C++
helpviewer_keywords:
- CDefaultHashTraits class
ms.assetid: d8ec4b37-6d58-447b-a0c1-8580c5b1ab85
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2143b84a8a8906643b9fc8befd49ffd244aa9625
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43764989"
---
# <a name="cdefaulthashtraits-class"></a>Cdefaulthashtraits – třída

Tato třída poskytuje statické funkce pro výpočet hodnoty hash.

## <a name="syntax"></a>Syntaxe

```
template<typename T>  
class CDefaultHashTraits
```

#### <a name="parameters"></a>Parametry

*T*  
Typ dat uložených v kolekci.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDefaultHashTraits::Hash](#hash)|(Statické) Voláním této funkce pro výpočet hodnoty hash pro daný element.|

## <a name="remarks"></a>Poznámky

Tato třída obsahuje jednu statickou funkci, která vrátí hodnotu hash pro daný element. Tato třída je využíváno [cdefaultelementtraits – třída](../../atl/reference/cdefaultelementtraits-class.md).

Další informace najdete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

##  <a name="hash"></a>  CDefaultHashTraits::Hash

Voláním této funkce pro výpočet hodnoty hash pro daný element.

```
static ULONG Hash(const T& element) throw();
```

### <a name="parameters"></a>Parametry

*– Element*  
Element.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu hash.

### <a name="remarks"></a>Poznámky

Výchozí algoritmus hash je velmi jednoduchý: Vrácená hodnota je číslo prvku. Potlačí tuto funkci v případě složitější algoritmus je povinný.

## <a name="see-also"></a>Viz také

[Přehled tříd](../../atl/atl-class-overview.md)
