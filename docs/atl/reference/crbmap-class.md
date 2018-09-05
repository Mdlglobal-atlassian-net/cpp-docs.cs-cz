---
title: Crbmap – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CRBMap
- ATLCOLL/ATL::CRBMap
- ATLCOLL/ATL::CRBMap::CRBMap
- ATLCOLL/ATL::CRBMap::Lookup
- ATLCOLL/ATL::CRBMap::RemoveKey
- ATLCOLL/ATL::CRBMap::SetAt
dev_langs:
- C++
helpviewer_keywords:
- CRBMap class
ms.assetid: 658e94dc-e835-4356-aed1-1513e1f66969
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 17f4ce858949aafe1a448fc51b8ecd5591270184
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43764839"
---
# <a name="crbmap-class"></a>Crbmap – třída

Tato třída reprezentuje strukturu mapování pomocí binárního stromu Red Black.

## <a name="syntax"></a>Syntaxe

```
template <typename K,
          typename V, 
          class KTraits = CElementTraits<K>, 
          class VTraits = CElementTraits<V>> 
class CRBMap : public CRBTree<K, V, KTraits, VTraits>
```

#### <a name="parameters"></a>Parametry

*K*  
Typ klíče prvku.

*V*  
Typ elementu hodnota.

*KTraits*  
Kód použitý má zkopírovat nebo přesunout klíčové prvky. Zobrazit [celementtraits – třída](../../atl/reference/celementtraits-class.md) další podrobnosti.

*VTraits*  
Kód použitý má zkopírovat nebo přesunout elementy hodnotu.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CRBMap::CRBMap](#crbmap)|Konstruktor|
|[Crbmap –:: ~ crbmap –](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CRBMap::Lookup](#lookup)|Volejte tuto metodu za účelem vyhledání klíče nebo hodnoty `CRBMap` objektu.|
|[CRBMap::RemoveKey](#removekey)|Voláním této metody lze odebrat element z `CRBMap` objekt daný klíč.|
|[CRBMap::SetAt](#setat)|Voláním této metody lze vložit páru prvek do objektu map.|

## <a name="remarks"></a>Poznámky

`CRBMap` poskytuje podporu pro mapování pole daného typu, Správa uspořádaného pole klíčové prvky a jejich přidružené hodnoty. Každý klíč může mít pouze jednu přidruženou hodnotu. Prvky (skládající se z klíče a hodnoty) jsou uloženy v binárního stromu struktury, pomocí [CRBMap::SetAt](#setat) metody. Prvky lze odebrat prostřednictvím [CRBMap::RemoveKey](#removekey) metoda, která odstraňuje prvek s danou hodnotu klíče.

Procházení stromu je možné provádět pomocí metod, jako [CRBTree::GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition), [CRBTree::GetNext](../../atl/reference/crbtree-class.md#getnext), a [CRBTree::GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue).

*KTraits* a *VTraits* parametry jsou třídy, které obsahují žádný doplňkový kód potřeba zkopírovat nebo přesunout prvky.

`CRBMap` je odvozen z [crbtree –](../../atl/reference/crbtree-class.md), který implementuje pomocí algoritmu Red černé binárního stromu. [Crbmultimap –](../../atl/reference/crbmultimap-class.md) varianta, který umožňuje více hodnot pro každý klíč. Příliš odvozené od `CRBTree`a proto sdílí řadu funkcí s `CRBMap`.

Alternativa k oběma `CRBMap` a `CRBMultiMap` nabízí [catlmap –](../../atl/reference/catlmap-class.md) třídy. Pokud musí být uložen pouze malý počet prvků, zvažte použití [csimplemap –](../../atl/reference/csimplemap-class.md) namísto třídy.

Podrobnější diskuzi o různých třídy kolekcí a jejich funkce a výkonové charakteristiky, naleznete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Crbtree –](../../atl/reference/crbtree-class.md)

`CRBMap`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

##  <a name="crbmap"></a>  CRBMap::CRBMap

Konstruktor

```
explicit CRBMap(size_t nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parametry

*nBlockSize*  
Velikost bloku.

### <a name="remarks"></a>Poznámky

*NBlockSize* parametr je míra množství paměti přidělené, pokud je nutné použít nový prvek. Bloky o větší velikosti snížit volání rutiny přidělení paměti, ale spotřebovávají více prostředků. Výchozí hodnota se přidělit prostor pro 10 prvků v čase.

Najdete v dokumentaci pro základní třídu [crbtree –](../../atl/reference/crbtree-class.md) informace o dalších metodách, k dispozici.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#81](../../atl/codesnippet/cpp/crbmap-class_1.cpp)]

##  <a name="dtor"></a>  Crbmap –:: ~ crbmap –

Destruktor.

```
~CRBMap() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky.

Najdete v dokumentaci pro základní třídu [crbtree –](../../atl/reference/crbtree-class.md) informace o dalších metodách, k dispozici.

##  <a name="lookup"></a>  CRBMap::Lookup

Volejte tuto metodu za účelem vyhledání klíče nebo hodnoty `CRBMap` objektu.

```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const throw(...);
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parametry

*Klíč*  
Určuje klíč, který identifikuje elementu, který chcete vyhledávat.

*value*  
Proměnná, která přijímá hodnotu vyhledaných.

### <a name="return-value"></a>Návratová hodnota

První forma metoda vrátí hodnotu true, pokud je nalezen klíč, jinak hodnota false. Druhý a třetí formuláře vrátí ukazatel [CPair](crbtree-class.md#cpair_class).

### <a name="remarks"></a>Poznámky

Najdete v dokumentaci pro základní třídu [crbtree –](../../atl/reference/crbtree-class.md) informace o dalších metodách, k dispozici.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#82](../../atl/codesnippet/cpp/crbmap-class_2.cpp)]

##  <a name="removekey"></a>  CRBMap::RemoveKey

Voláním této metody lze odebrat element z `CRBMap` objekt daný klíč.

```
bool RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parametry

*Klíč*  
Klíč odpovídající dvojice elementů chcete odebrat.

### <a name="return-value"></a>Návratová hodnota

Vrátí true, pokud je klíč nalezen a odebrané, při neúspěchu hodnotu false.

### <a name="remarks"></a>Poznámky

Najdete v dokumentaci pro základní třídu [crbtree –](../../atl/reference/crbtree-class.md) informace o dalších metodách, k dispozici.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#83](../../atl/codesnippet/cpp/crbmap-class_3.cpp)]

##  <a name="setat"></a>  CRBMap::SetAt

Voláním této metody lze vložit páru prvek do objektu map.

```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value) throw(...);
```

### <a name="parameters"></a>Parametry

*Klíč*  
Hodnotu klíče pro přidání do `CRBMap` objektu.

*value*  
Hodnota k přidání do `CRBMap` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí pozici prvku dvojice klíč/hodnota v `CRBMap` objektu.

### <a name="remarks"></a>Poznámky

`SetAt` nahradí existující prvek, pokud je nalezen odpovídající klíč. Pokud klíč není nalezen, vytvoří se nový pár klíč/hodnota.

Najdete v dokumentaci pro základní třídu [crbtree –](../../atl/reference/crbtree-class.md) informace o dalších metodách, k dispozici.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#84](../../atl/codesnippet/cpp/crbmap-class_4.cpp)]

## <a name="see-also"></a>Viz také

[Crbtree – třída](../../atl/reference/crbtree-class.md)   
[Catlmap – třída](../../atl/reference/catlmap-class.md)   
[Crbmultimap – třída](../../atl/reference/crbmultimap-class.md)   
[Přehled tříd](../../atl/atl-class-overview.md)
