---
title: "Třída CRBMultiMap | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap::CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap::FindFirstWithKey
- ATLCOLL/ATL::CRBMultiMap::GetNextValueWithKey
- ATLCOLL/ATL::CRBMultiMap::GetNextWithKey
- ATLCOLL/ATL::CRBMultiMap::Insert
- ATLCOLL/ATL::CRBMultiMap::RemoveKey
dev_langs: C++
helpviewer_keywords: CRBMultiMap class
ms.assetid: 94d3ec0c-3e30-4ab7-a101-d8da4fb8add3
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 79ef7fdd5799b01ec115befcd50bbe4625d48bea
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="crbmultimap-class"></a>CRBMultiMap – třída
Tato třída reprezentuje strukturu mapování, která umožňuje že každý klíč může být přidružen více než jednu hodnotu, pomocí binárního stromu Red černé.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<typename K,
         typename V, 
         class KTraits = CElementTraits<K>, 
         class VTraits = CElementTraits<V>>  
class CRBMultiMap : public CRBTree<K, V, KTraits, VTraits>
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
|[CRBMultiMap::CRBMultiMap](#crbmultimap)|Konstruktor|  
|[CRBMultiMap:: ~ CRBMultiMap](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CRBMultiMap::FindFirstWithKey](#findfirstwithkey)|Voláním této metody lze najít pozici první prvek s daným klíčem.|  
|[CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)|Voláním této metody lze získat hodnotu přidružené k danému klíči a aktualizujte hodnotu pozici.|  
|[CRBMultiMap::GetNextWithKey](#getnextwithkey)|Voláním této metody lze získat element přidružené k danému klíči a aktualizujte hodnotu pozici.|  
|[CRBMultiMap::Insert](#insert)|Volejte tuto metodu za účelem vložení dvojici element do mapy.|  
|[CRBMultiMap::RemoveKey](#removekey)|Voláním této metody lze odebrat všechny elementy klíč/hodnota pro zadaný klíč.|  
  
## <a name="remarks"></a>Poznámky  
 `CRBMultiMap`poskytuje podporu pro mapování pole daného typu, Správa uspořádaného pole klíčové prvky a hodnot. Na rozdíl od [CRBMap](../../atl/reference/crbmap-class.md) třída, každý klíč může být přidružen více než jednu hodnotu.  
  
 Elementy (tvořený klíč a hodnotu) se ukládají do binárního stromu struktury, pomocí [CRBMultiMap::Insert](#insert) metoda. Elementy se dá odebrat pomocí [CRBMultiMap::RemoveKey](#removekey) metoda, která odstraňuje všechny elementy, které odpovídají danému klíči.  
  
 Procházení stromu je možné provádět pomocí metod, jako [CRBTree::GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition), [CRBTree::GetNext](../../atl/reference/crbtree-class.md#getnext), a [CRBTree::GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue). Přístup k potenciálně vícenásobné hodnoty pro klíč je možné pomocí [CRBMultiMap::FindFirstWithKey](#findfirstwithkey), [CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey), a [CRBMultiMap::GetNextWithKey ](#getnextwithkey) metody. Podívejte se na příklad pro [CRBMultiMap::CRBMultiMap](#crbmultimap) pro ilustraci tohoto v praxi.  
  
 `KTraits` a `VTraits` parametry jsou třídy vlastností, které obsahují žádný doplňkový kód potřebné k zkopírovat nebo přesunout elementy.  
  
 `CRBMultiMap`je odvozený od [CRBTree](../../atl/reference/crbtree-class.md), který implementuje pomocí algoritmu Red černé binárního stromu. Alternativu k `CRBMultiMap` a `CRBMap` nabízí [CAtlMap](../../atl/reference/catlmap-class.md) třídy. Když pouze malý počet elementů musí být uložen, zvažte použití [CSimpleMap](../../atl/reference/csimplemap-class.md) třídy místo.  
  
 Podrobnější informace o různých třídy kolekce a jejich funkce a vlastnosti výkonu, najdete v části [ATL – třídy kolekce](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CRBTree](../../atl/reference/crbtree-class.md)  
  
 `CRBMultiMap`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcoll.h  
  
##  <a name="crbmultimap"></a>CRBMultiMap::CRBMultiMap  
 Konstruktor  
  
```
explicit CRBMultiMap(size_t nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nBlockSize`  
 Velikost bloku.  
  
### <a name="remarks"></a>Poznámky  
 `nBlockSize` Parametr se rozumí míra množství paměti přidělené, pokud je potřeba nového elementu. Bloky o větší velikosti snížit volání rutiny přidělení paměti, ale spotřebovávají více prostředků. Výchozí hodnota se přidělit prostor pro 10 elementy najednou.  
  
 Najdete v dokumentaci pro základní třídu [CRBTree](../../atl/reference/crbtree-class.md) informace o dalších metodách, k dispozici.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#85](../../atl/codesnippet/cpp/crbmultimap-class_1.cpp)]  
  
##  <a name="dtor"></a>CRBMultiMap:: ~ CRBMultiMap  
 Destruktor.  
  
```
~CRBMultiMap() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny přidělené prostředky.  
  
 Najdete v dokumentaci pro základní třídu [CRBTree](../../atl/reference/crbtree-class.md) informace o dalších metodách, k dispozici.  
  
##  <a name="findfirstwithkey"></a>CRBMultiMap::FindFirstWithKey  
 Voláním této metody lze najít pozici první prvek s daným klíčem.  
  
```
POSITION FindFirstWithKey(KINARGTYPE key) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Určuje klíč, který identifikuje elementu, který chcete najít.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud je nalezen klíč, NULL. v opačném případě vrátí POZICI prvního prvku klíč/hodnota.  
  
### <a name="remarks"></a>Poznámky  
 Klíč v `CRBMultiMap` může mít jeden nebo více přidružené hodnoty. Tato metoda zajistí hodnota pozice první hodnoty (které mohou být ve skutečnosti jediná hodnota) přidružené k tomuto klíči konkrétní. Vrácená hodnota pozice lze s [CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey) nebo [CRBMultiMap::GetNextWithKey](#getnextwithkey) získat hodnotu a aktualizovat pozici.  
  
 Najdete v dokumentaci pro základní třídu [CRBTree](../../atl/reference/crbtree-class.md) informace o dalších metodách, k dispozici.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CRBMultiMap::CRBMultiMap](#crbmultimap).  
  
##  <a name="getnextvaluewithkey"></a>CRBMultiMap::GetNextValueWithKey  
 Voláním této metody lze získat hodnotu přidružené k danému klíči a aktualizujte hodnotu pozici.  
  
```
const V& GetNextValueWithKey(
    POSITION& pos,
    KINARGTYPE key) const throw();
V& GetNextValueWithKey(
    POSITION& pos,
    KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Hodnota pozice, byly získány buď volání [CRBMultiMap::FindFirstWithKey](#findfirstwithkey) nebo [CRBMultiMap::GetNextWithKey](#getnextwithkey), nebo předchozí volání `GetNextValueWithKey`.  
  
 `key`  
 Určuje klíč, který identifikuje elementu, který chcete najít.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí element dvojici spojené s daným klíčem.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota pozice je aktualizována tak, aby odkazoval na nejbližší hodnotu přiřazenou klíči. Pokud neexistují žádné další hodnoty, je hodnota pozice nastavena na hodnotu NULL.  
  
 Najdete v dokumentaci pro základní třídu [CRBTree](../../atl/reference/crbtree-class.md) informace o dalších metodách, k dispozici.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CRBMultiMap::CRBMultiMap](#crbmultimap).  
  
##  <a name="getnextwithkey"></a>CRBMultiMap::GetNextWithKey  
 Voláním této metody lze získat element přidružené k danému klíči a aktualizujte hodnotu pozici.  
  
```
const CPair* GetNextWithKey(
    POSITION& pos,
    KINARGTYPE key) const throw();
CPair* GetNextWithKey(
    POSITION& pos,
    KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Hodnota pozice, byly získány buď volání [CRBMultiMap::FindFirstWithKey](#findfirstwithkey) nebo [CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey), nebo předchozí volání `GetNextWithKey`.  
  
 `key`  
 Určuje klíč, který identifikuje elementu, který chcete najít.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací další [CRBTree::CPair třída](crbtree-class.md#cpair_class) element spojené s daným klíčem.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota pozice je aktualizována tak, aby odkazoval na nejbližší hodnotu přiřazenou klíči. Pokud neexistují žádné další hodnoty, je hodnota pozice nastavena na hodnotu NULL.  
  
 Najdete v dokumentaci pro základní třídu [CRBTree](../../atl/reference/crbtree-class.md) informace o dalších metodách, k dispozici.  
  
##  <a name="insert"></a>CRBMultiMap::Insert  
 Volejte tuto metodu za účelem vložení dvojici element do mapy.  
  
```
POSITION Insert(KINARGTYPE key, VINARGTYPE value) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Hodnota klíče pro přidání do `CRBMultiMap` objektu.  
  
 *value*  
 Hodnota k přidání do `CRBMultiMap` objekt, přidružený k `key`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí pozici element dvojice klíč/hodnota v `CRBMultiMap` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Najdete v dokumentaci pro základní třídu [CRBTree](../../atl/reference/crbtree-class.md) informace o dalších metodách, k dispozici.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CRBMultiMap::CRBMultiMap](#crbmultimap).  
  
##  <a name="removekey"></a>CRBMultiMap::RemoveKey  
 Voláním této metody lze odebrat všechny elementy klíč/hodnota pro zadaný klíč.  
  
```
size_t RemoveKey(KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Určuje klíč, který označuje jeden či více elementů k odstranění.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet hodnot, které jsou přidružené k danému klíči.  
  
### <a name="remarks"></a>Poznámky  
 `RemoveKey`Odstraní všechny prvky klíč/hodnota, které mají klíč, který odpovídá `key`.  
  
 Najdete v dokumentaci pro základní třídu [CRBTree](../../atl/reference/crbtree-class.md) informace o dalších metodách, k dispozici.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CRBMultiMap::CRBMultiMap](#crbmultimap).  
  
## <a name="see-also"></a>Viz také  
 [CRBTree – třída](../../atl/reference/crbtree-class.md)   
 [CAtlMap – třída](../../atl/reference/catlmap-class.md)   
 [CRBMap – třída](../../atl/reference/crbmap-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
