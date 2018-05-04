---
title: Třída CRBMap | Microsoft Docs
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
ms.openlocfilehash: b32b21c8785bb5e28058c51f2345c5ffcb6de1f3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="crbmap-class"></a>CRBMap – třída
Tato třída reprezentuje strukturou mapování pomocí binárního stromu Red černé.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <typename K,
          typename V, 
          class KTraits = CElementTraits<K>, 
          class VTraits = CElementTraits<V>> 
class CRBMap : public CRBTree<K, V, KTraits, VTraits>
```    
  
#### <a name="parameters"></a>Parametry  
 `K`  
 Typ klíče elementu.  
  
 *V*  
 Typ elementu hodnotu.  
  
 `KTraits`  
 Kód používaný k zkopírovat nebo přesunout klíčové prvky. V tématu [CElementTraits třída](../../atl/reference/celementtraits-class.md) další podrobnosti.  
  
 `VTraits`  
 Kód používaný k zkopírovat nebo přesunout hodnotu elementy.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CRBMap::CRBMap](#crbmap)|Konstruktor|  
|[CRBMap:: ~ CRBMap](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CRBMap::Lookup](#lookup)|Volat tuto metodu za účelem vyhledání klíče nebo hodnoty ve `CRBMap` objektu.|  
|[CRBMap::RemoveKey](#removekey)|Voláním této metody lze odebrat element z `CRBMap` objekt, daný klíč.|  
|[CRBMap::SetAt](#setat)|Volejte tuto metodu za účelem vložení dvojici element do mapy.|  
  
## <a name="remarks"></a>Poznámky  
 `CRBMap` poskytuje podporu pro mapování pole daného typu, Správa uspořádaného pole klíčové prvky a jejich přidružené hodnoty. Každý klíč může mít pouze jeden přidružené hodnoty. Elementy (tvořený klíč a hodnotu) se ukládají do binárního stromu struktury, pomocí [CRBMap::SetAt](#setat) metoda. Elementy se dá odebrat pomocí [CRBMap::RemoveKey](#removekey) metoda, která odstraňuje element s danou hodnotou klíče.  
  
 Procházení stromu je možné provádět pomocí metod, jako [CRBTree::GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition), [CRBTree::GetNext](../../atl/reference/crbtree-class.md#getnext), a [CRBTree::GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue).  
  
 `KTraits` a `VTraits` parametry jsou třídy vlastností, které obsahují žádný doplňkový kód potřebné k zkopírovat nebo přesunout elementy.  
  
 `CRBMap` je odvozený od [CRBTree](../../atl/reference/crbtree-class.md), který implementuje pomocí algoritmu Red černé binárního stromu. [CRBMultiMap](../../atl/reference/crbmultimap-class.md) je variace, která umožňuje více hodnot pro každý klíč. Příliš je odvozen od `CRBTree`a proto sdílí mnoho funkcí s `CRBMap`.  
  
 Alternativu obou `CRBMap` a `CRBMultiMap` nabízí [CAtlMap](../../atl/reference/catlmap-class.md) třídy. Když pouze malý počet elementů musí být uložen, zvažte použití [CSimpleMap](../../atl/reference/csimplemap-class.md) třídy místo.  
  
 Podrobnější informace o různých třídy kolekce a jejich funkce a vlastnosti výkonu, najdete v části [ATL – třídy kolekce](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CRBTree](../../atl/reference/crbtree-class.md)  
  
 `CRBMap`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcoll.h  
  
##  <a name="crbmap"></a>  CRBMap::CRBMap  
 Konstruktor  
  
```
explicit CRBMap(size_t nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nBlockSize`  
 Velikost bloku.  
  
### <a name="remarks"></a>Poznámky  
 `nBlockSize` Parametr se rozumí míra množství paměti přidělené, pokud je potřeba nového elementu. Bloky o větší velikosti snížit volání rutiny přidělení paměti, ale spotřebovávají více prostředků. Výchozí hodnota se přidělit prostor pro 10 elementy najednou.  
  
 Najdete v dokumentaci pro základní třídu [CRBTree](../../atl/reference/crbtree-class.md) informace o dalších metodách, k dispozici.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#81](../../atl/codesnippet/cpp/crbmap-class_1.cpp)]  
  
##  <a name="dtor"></a>  CRBMap:: ~ CRBMap  
 Destruktor.  
  
```
~CRBMap() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny přidělené prostředky.  
  
 Najdete v dokumentaci pro základní třídu [CRBTree](../../atl/reference/crbtree-class.md) informace o dalších metodách, k dispozici.  
  
##  <a name="lookup"></a>  CRBMap::Lookup  
 Volat tuto metodu za účelem vyhledání klíče nebo hodnoty ve `CRBMap` objektu.  
  
```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const throw(...);
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Určuje klíč, který identifikuje elementu, který chcete vyhledávat.  
  
 *value*  
 Proměnná, která přijímá vyhledaných hodnota.  
  
### <a name="return-value"></a>Návratová hodnota  
 První formulář metoda vrátí hodnotu true, pokud je nalezen klíč, jinak hodnota false. Vrátí ukazatel na druhý a třetí formuláře [CPair](crbtree-class.md#cpair_class).  
  
### <a name="remarks"></a>Poznámky  
 Najdete v dokumentaci pro základní třídu [CRBTree](../../atl/reference/crbtree-class.md) informace o dalších metodách, k dispozici.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#82](../../atl/codesnippet/cpp/crbmap-class_2.cpp)]  
  
##  <a name="removekey"></a>  CRBMap::RemoveKey  
 Voláním této metody lze odebrat element z `CRBMap` objekt, daný klíč.  
  
```
bool RemoveKey(KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klíč odpovídající element pár chcete odebrat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu true Pokud je klíč nalezen a odebrána, false při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Najdete v dokumentaci pro základní třídu [CRBTree](../../atl/reference/crbtree-class.md) informace o dalších metodách, k dispozici.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#83](../../atl/codesnippet/cpp/crbmap-class_3.cpp)]  
  
##  <a name="setat"></a>  CRBMap::SetAt  
 Volejte tuto metodu za účelem vložení dvojici element do mapy.  
  
```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Hodnota klíče pro přidání do `CRBMap` objektu.  
  
 *value*  
 Hodnota k přidání do `CRBMap` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí pozici element dvojice klíč/hodnota v `CRBMap` objektu.  
  
### <a name="remarks"></a>Poznámky  
 `SetAt` nahradí existující elementu, pokud je nalezen odpovídající klíč. Pokud není nalezen klíč, vytvoří se nový pár klíč/hodnota.  
  
 Najdete v dokumentaci pro základní třídu [CRBTree](../../atl/reference/crbtree-class.md) informace o dalších metodách, k dispozici.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#84](../../atl/codesnippet/cpp/crbmap-class_4.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [CRBTree – třída](../../atl/reference/crbtree-class.md)   
 [CAtlMap – třída](../../atl/reference/catlmap-class.md)   
 [CRBMultiMap – třída](../../atl/reference/crbmultimap-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
