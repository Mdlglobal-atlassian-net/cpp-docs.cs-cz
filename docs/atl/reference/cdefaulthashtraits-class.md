---
title: Cdefaulthashtraits – třída
ms.date: 11/04/2016
f1_keywords:
- CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits::Hash
helpviewer_keywords:
- CDefaultHashTraits class
ms.assetid: d8ec4b37-6d58-447b-a0c1-8580c5b1ab85
ms.openlocfilehash: a51b4460d7fcdf778fce24b6e404b75190f598f6
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57257293"
---
# <a name="cdefaulthashtraits-class"></a>Cdefaulthashtraits – třída

Tato třída poskytuje statické funkce pro výpočet hodnoty hash.

## <a name="syntax"></a>Syntaxe

```
template<typename T>
class CDefaultHashTraits
```

#### <a name="parameters"></a>Parametry

*T*<br/>
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

*– Element*<br/>
Element.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu hash.

### <a name="remarks"></a>Poznámky

Výchozí algoritmus hash je velmi jednoduchý: Vrácená hodnota je číslo prvku. Potlačí tuto funkci v případě složitější algoritmus je povinný.

## <a name="see-also"></a>Viz také:

[Přehled tříd](../../atl/atl-class-overview.md)
