---
title: "Třída CAtlMap | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlMap
- ATLCOLL/ATL::CAtlMap
- ATLCOLL/ATL::CAtlMap::KINARGTYPE
- ATLCOLL/ATL::CAtlMap::KOUTARGTYPE
- ATLCOLL/ATL::CAtlMap::VINARGTYPE
- ATLCOLL/ATL::CAtlMap::VOUTARGTYPE
- ATLCOLL/ATL::CPair::m_key
- ATLCOLL/ATL::CPair::m_value
- ATLCOLL/ATL::CAtlMap::CAtlMap
- ATLCOLL/ATL::CAtlMap::AssertValid
- ATLCOLL/ATL::CAtlMap::DisableAutoRehash
- ATLCOLL/ATL::CAtlMap::EnableAutoRehash
- ATLCOLL/ATL::CAtlMap::GetAt
- ATLCOLL/ATL::CAtlMap::GetCount
- ATLCOLL/ATL::CAtlMap::GetHashTableSize
- ATLCOLL/ATL::CAtlMap::GetKeyAt
- ATLCOLL/ATL::CAtlMap::GetNext
- ATLCOLL/ATL::CAtlMap::GetNextAssoc
- ATLCOLL/ATL::CAtlMap::GetNextKey
- ATLCOLL/ATL::CAtlMap::GetNextValue
- ATLCOLL/ATL::CAtlMap::GetStartPosition
- ATLCOLL/ATL::CAtlMap::GetValueAt
- ATLCOLL/ATL::CAtlMap::InitHashTable
- ATLCOLL/ATL::CAtlMap::IsEmpty
- ATLCOLL/ATL::CAtlMap::Lookup
- ATLCOLL/ATL::CAtlMap::Rehash
- ATLCOLL/ATL::CAtlMap::RemoveAll
- ATLCOLL/ATL::CAtlMap::RemoveAtPos
- ATLCOLL/ATL::CAtlMap::RemoveKey
- ATLCOLL/ATL::CAtlMap::SetAt
- ATLCOLL/ATL::CAtlMap::SetOptimalLoad
- ATLCOLL/ATL::CAtlMap::SetValueAt
dev_langs: C++
helpviewer_keywords: CAtlMap class
ms.assetid: 5e2fe028-8e6d-4686-93df-1433d2080ec3
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9d16ff30313a9346aa25f8febfba2f6e0d8307f1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="catlmap-class"></a>CAtlMap – třída
Tato třída poskytuje metody pro vytváření a správu objekt map.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <typename K,
          typename V, 
          class KTraits = CElementTraits<K>, 
          class VTraits = CElementTraits<V>>
class CAtlMap
```  
  
#### <a name="parameters"></a>Parametry  
 `K`  
 Typ klíče elementu.  
  
 V  
 Typ elementu hodnotu.  
  
 `KTraits`  
 Kód používaný k zkopírovat nebo přesunout klíčové prvky. V tématu [CElementTraits třída](../../atl/reference/celementtraits-class.md) další podrobnosti.  
  
 `VTraits`  
 Kód používaný k zkopírovat nebo přesunout hodnotu elementy.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlMap::KINARGTYPE](#kinargtype)|Typ použitý při klíč se předá jako vstupní argument|  
|[CAtlMap::KOUTARGTYPE](#koutargtype)|Typ použitý při klíč se vrátí jako argument výstup.|  
|[CAtlMap::VINARGTYPE](#vinargtype)|Typ použitý při hodnotu se předá jako vstupní argument.|  
|[CAtlMap::VOUTARGTYPE](#voutargtype)|Typ použitý při hodnotu je předat jako argument výstup.|  
  
### <a name="public-classes"></a>Veřejné třídy  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlMap::CPair – třída](#cpair_class)|Třída obsahující prvky klíč a hodnotu.|  

  
### <a name="cpair-data-members"></a>CPair datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CPair::m_key](#m_key)|Datový člen ukládání klíče elementu.|  
|[CPair::m_value](#m_value)|Datový člen ukládání prvku hodnoty.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlMap::CAtlMap](#catlmap)|Konstruktor|  
|[CAtlMap:: ~ CAtlMap](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlMap::AssertValid](#assertvalid)|Volat tuto metodu za účelem způsobit ASSERT, pokud `CAtlMap` není platný.|  
|[CAtlMap::DisableAutoRehash](#disableautorehash)|Voláním této metody lze zakázat automatické rehashing z `CAtlMap` objektu.|  
|[CAtlMap::EnableAutoRehash](#enableautorehash)|Voláním této metody lze povolit automatické rehashing z `CAtlMap` objektu.|  
|[CAtlMap::GetAt](#getat)|Volejte tuto metodu za účelem vrátí prvek na zadané pozici v mapě.|  
|[CAtlMap::GetCount](#getcount)|Volejte tuto metodu za účelem načtení počet elementů v mapě.|  
|[CAtlMap::GetHashTableSize](#gethashtablesize)|Volejte tuto metodu můžete určit počet přihrádek v mapy zatřiďovací tabulku.|  
|[CAtlMap::GetKeyAt](#getkeyat)|Voláním této metody lze načíst klíč uložený na dané pozici v `CAtlMap` objektu.|  
|[CAtlMap::GetNext](#getnext)|Volat tuto metodu za účelem získání ukazatele na další prvek pár uložené v `CAtlMap` objektu.|  
|[CAtlMap::GetNextAssoc](#getnextassoc)|Získá další prvek pro iterace.|  
|[CAtlMap::GetNextKey](#getnextkey)|Volat tuto metodu pro načtení Další klíč z `CAtlMap` objektu.|  
|[CAtlMap::GetNextValue](#getnextvalue)|Voláním této metody lze získat další hodnotu z `CAtlMap` objektu.|  
|[CAtlMap::GetStartPosition](#getstartposition)|Volejte tuto metodu za účelem spuštění iterace mapy.|  
|[CAtlMap::GetValueAt](#getvalueat)|Volat tuto metodu za účelem načtení s hodnotou uloženou na dané pozici v `CAtlMap` objektu.|  
|[CAtlMap::InitHashTable](#inithashtable)|Volejte tuto metodu za účelem inicializace zatřiďovací tabulku.|  
|[CAtlMap::IsEmpty](#isempty)|Volejte tuto metodu za účelem testování pro objekt prázdný mapy.|  
|[CAtlMap::Lookup](#lookup)|Volat tuto metodu za účelem vyhledání klíče nebo hodnoty ve `CAtlMap` objektu.|  
|[CAtlMap::Rehash](#rehash)|Volat tuto metodu za účelem rehash `CAtlMap` objektu.|  
|[CAtlMap::RemoveAll](#removeall)|Voláním této metody lze odebrat všechny elementy z `CAtlMap` objektu.|  
|[CAtlMap::RemoveAtPos](#removeatpos)|Voláním této metody lze odebrat – element na dané pozici v `CAtlMap` objektu.|  
|[CAtlMap::RemoveKey](#removekey)|Voláním této metody lze odebrat element z `CAtlMap` objekt, daný klíč.|  
|[CAtlMap::SetAt](#setat)|Volejte tuto metodu za účelem vložení dvojici element do mapy.|  
|[CAtlMap::SetOptimalLoad](#setoptimalload)|Volat tuto metodu a nastavit optimální zátěž `CAtlMap` objektu.|  
|[CAtlMap::SetValueAt](#setvalueat)|Voláním této metody lze změnit hodnotu uloženou na dané pozici v `CAtlMap` objektu.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlMap::operator\[\]](catlmap-class.md#operator_at)|Nahradí nebo ho přidá nového elementu na `CAtlMap`.|  

  
## <a name="remarks"></a>Poznámky  
 `CAtlMap`poskytuje podporu pro mapování pole daného typu, Správa neuspořádaný pole klíčové prvky a jejich přidružené hodnoty. Elementy (tvořený klíč a hodnotu) jsou uloženy pomocí algoritmu hash, což velké množství dat efektivně ukládat a načíst.  
  
 `KTraits` a `VTraits` parametry jsou třídy vlastností, které obsahují žádný doplňkový kód potřebné k zkopírovat nebo přesunout elementy.  
  
 Alternativu k `CAtlMap` nabízí [CRBMap](../../atl/reference/crbmap-class.md) třídy. `CRBMap`také ukládá dvojice klíč/hodnota, ale vykazuje různých výkonové charakteristiky. Čas potřebný k vložení prvku, vyhledejte klíč nebo odstranění klíče z `CRBMap` objekt je pořadí *log(n)*, kde  *n*  je počet elementů. Pro `CAtlMap`, všechny tyto operace obvykle časově konstantní, i když nejhorších možných scénářů může být pořadí  *n* . Proto v případě typické `CAtlMap` je rychlejší.  
  
 Rozdíl mezi `CRBMap` a `CAtlMap` vyvstává zřejmá při iterace v rámci uložené elementy. V `CRBMap`, jsou seřazené podle navštívené elementy. V `CAtlMap`elementy nejsou seřazené a lze odvodit žádné pořadí.  
  
 Pokud malý počet elementů musí být uložena, zvažte použití [CSimpleMap](../../atl/reference/csimplemap-class.md) třídy místo.  
  
 Další informace najdete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcoll.h  
  
##  <a name="assertvalid"></a>CAtlMap::AssertValid  
 Volat tuto metodu za účelem způsobit ASSERT, pokud `CAtlMap` objekt není platný.  
  
```
void AssertValid() const;
```  
  
### <a name="remarks"></a>Poznámky  
 V sestavení pro ladění způsobí metoda ASSERT, pokud `CAtlMap` objekt není platný.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CAtlMap::CAtlMap](#catlmap).  
  
##  <a name="catlmap"></a>CAtlMap::CAtlMap  
 Konstruktor  
  
```
CAtlMap(
    UINT nBins = 17,
    float fOptimalLoad = 0.75f,
    float fLoThreshold = 0.25f,
    float fHiThreshold = 2.25f,
    UINT nBlockSize = 10) throw ();
```  
  
### <a name="parameters"></a>Parametry  
 `nBins`  
 Počet přihrádek poskytování ukazatele na uložené elementy. Později v tomto tématu Vysvětlení přihrádek najdete v části poznámky.  
  
 `fOptimalLoad`  
 Poměr optimální zatížení.  
  
 `fLoThreshold`  
 Nižší prahová hodnota pro poměru zatížení.  
  
 `fHiThreshold`  
 Vyšší prahová hodnota pro poměru zatížení.  
  
 `nBlockSize`  
 Velikost bloku.  
  
### <a name="remarks"></a>Poznámky  
 `CAtlMap`všech jejích elementů uložené odkazuje na první vytvořením indexu pomocí algoritmu hash na klíč. Tento index odkazuje "bin" obsahující ukazatel na uložené elementy. Pokud přihrádky je již používán, vytvoří se pro přístup k další prvky propojené seznamu. Procházení seznamu je nižší než přímý přístup k prvku správný, a proto musí strukturu mapy k vyrovnávání požadavků na úložiště pro výkon. Výchozí parametry rozhodli umožnit dobré výsledky ve většině případů.  
  
 Poměr zatížení je poměr počtu přihrádek počet elementů uložené v objektu mapy. Při přepočítání strukturu mapy *fOptimalLoad* hodnota parametru se použije k výpočtu počet přihrádek vyžaduje. Tato hodnota se dá změnit pomocí [CAtlMap::SetOptimalLoad](#setoptimalload) metoda.  
  
 `fLoThreshold` Parametr je nižší hodnotu, která poměru zatížení dosáhnout před `CAtlMap` bude přepočítat optimální velikost mapy.  
  
 `fHiThreshold` Parametr je vyšší hodnotu, která poměru zatížení dosáhnout před `CAtlMap` objektu bude přepočítat optimální velikost mapy.  
  
 Tento proces přepočítání (označované jako rehashing) je ve výchozím nastavení povolené. Pokud chcete zakázat tento proces, třeba při zadávání velké množství dat najednou, volání [CAtlMap::DisableAutoRehash](#disableautorehash) metoda. Znovu aktivovat její [CAtlMap::EnableAutoRehash](#enableautorehash) metoda.  
  
 `nBlockSize` Parametr se rozumí míra množství paměti přidělené, pokud je potřeba nového elementu. Bloky o větší velikosti snížit volání rutiny přidělení paměti, ale spotřebovávají více prostředků.  
  
 Předtím, než mohou být uloženy žádná data, je nutné inicializovat zatřiďovací tabulku s volání [CAtlMap::InitHashTable](#inithashtable).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#72](../../atl/codesnippet/cpp/catlmap-class_1.cpp)]  
  
##  <a name="dtor"></a>CAtlMap:: ~ CAtlMap  
 Destruktor.  
  
```
~CAtlMap() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny přidělené prostředky.  
  
##  <a name="cpair_class"></a>CAtlMap::CPair – třída  
 Třída obsahující prvky klíč a hodnotu.  
  
```
class CPair : public __POSITION
```  
  
### <a name="remarks"></a>Poznámky  
 Tato třída se používá metodami [CAtlMap::GetNext](#getnext) a [CAtlMap::Lookup](#lookup) pro přístup k klíč a hodnotu elementy, které jsou uložené ve struktuře mapování.  
  
##  <a name="disableautorehash"></a>CAtlMap::DisableAutoRehash  
 Voláním této metody lze zakázat automatické rehashing z `CAtlMap` objektu.  
  
```
void DisableAutoRehash() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Při automatické rehashing jsou povoleny (je ve výchozím nastavení), počet přihrádek v zatřiďovací tabulce bude být přepočítána automaticky, pokud hodnota zatížení (poměr počtu přihrádek počet elementů uložené v poli) přesahuje maximální nebo minimální hodnoty zadaný v době, kdy byla vytvořena mapy.  
  
 `DisableAutoRehash`je nejvhodnější pro velký počet elementů se zařadí do mapy najednou. Namísto spuštění rehashing procesu pokaždé, když se překročí mezní hodnoty, je efektivnější volání `DisableAutoRehash`, přidejte elementy a nakonec volání [CAtlMap::EnableAutoRehash](#enableautorehash).  
  
##  <a name="enableautorehash"></a>CAtlMap::EnableAutoRehash  
 Voláním této metody lze povolit automatické rehashing z `CAtlMap` objektu.  
  
```
void EnableAutoRehash() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Při automatické rehashing jsou povoleny (je ve výchozím nastavení), počet přihrádek v zatřiďovací tabulce bude být přepočítána automaticky, pokud hodnota zatížení (poměr počtu přihrádek počet elementů uložené v poli) přesahuje maximální nebo minimální hodnoty zadaný v době, kdy se vytvoří mapy.  
  
 **EnableAutoRefresh** se nejčastěji používá po volání [CAtlMap::DisableAutoRehash](#disableautorehash).  
  
##  <a name="getat"></a>CAtlMap::GetAt  
 Volejte tuto metodu za účelem vrátí prvek na zadané pozici v mapě.  
  
```
void GetAt(
    POSITION pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;

CPair* GetAt(POSITION& pos) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Čítač pozice vrácené z předchozího volání [CAtlMap::GetNextAssoc](#getnextassoc) nebo [CAtlMap::GetStartPosition](#getstartposition).  
  
 `key`  
 Určení typu klíče mapy pro parametr šablony.  
  
 *Hodnota*  
 Parametr šablony určující typ hodnoty na mapě.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí ukazatel na aktuální pár klíč/hodnota elementů uložené v mapě.  
  
### <a name="remarks"></a>Poznámky  
 V sestavení pro ladění, dojde k chybě assertion Pokud `pos` rovná hodnotu NULL.  
  
##  <a name="getcount"></a>CAtlMap::GetCount  
 Volejte tuto metodu za účelem načtení počet elementů v mapě.  
  
```
size_t GetCount() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet elementů v objektu mapy. Jediným elementem je dvojice klíč/hodnota.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CAtlMap::CAtlMap](#catlmap).  
  
##  <a name="gethashtablesize"></a>CAtlMap::GetHashTableSize  
 Volejte tuto metodu můžete určit počet přihrádek v mapy zatřiďovací tabulku.  
  
```
UINT GetHashTableSize() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet přihrádek v zatřiďovací tabulce. V tématu [CAtlMap::CAtlMap](#catlmap) vysvětlení.  
  
##  <a name="getkeyat"></a>CAtlMap::GetKeyAt  
 Voláním této metody lze načíst klíč uložený na dané pozici v `CAtlMap` objektu.  
  
```
const K& GetKeyAt(POSITION pos) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Čítač pozice vrácené z předchozího volání [CAtlMap::GetNextAssoc](#getnextassoc) nebo [CAtlMap::GetStartPosition](#getstartposition).  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí odkaz na klíč uložený na dané pozici v `CAtlMap` objektu.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CAtlMap::CAtlMap](#catlmap).  
  
##  <a name="getnext"></a>CAtlMap::GetNext  
 Volat tuto metodu za účelem získání ukazatele na další prvek pár uložené v `CAtlMap` objektu.  
  
```
CPair* GetNext(POSITION& pos) throw();
const CPair* GetNext(POSITION& pos) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Čítač pozice vrácené z předchozího volání [CAtlMap::GetNextAssoc](#getnextassoc) nebo [CAtlMap::GetStartPosition](#getstartposition).  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí ukazatel na další pár klíč/hodnota elementů uložené v mapě. `pos` Pozice počítadlo je aktualizováno po každé volání. Pokud je načtený element posledních v mapě, `pos` je nastaven na hodnotu NULL.  
  
##  <a name="getnextassoc"></a>CAtlMap::GetNextAssoc  
 Získá další prvek pro iterace.  
  
```
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Čítač pozice vrácené z předchozího volání [CAtlMap::GetNextAssoc](#getnextassoc) nebo [CAtlMap::GetStartPosition](#getstartposition).  
  
 `key`  
 Určení typu klíče mapy pro parametr šablony.  
  
 *Hodnota*  
 Parametr šablony určující typ hodnoty na mapě.  
  
### <a name="remarks"></a>Poznámky  
 `pos` Pozice počítadlo je aktualizováno po každé volání. Pokud je načtený element posledních v mapě, `pos` je nastaven na hodnotu NULL.  
  
##  <a name="getnextkey"></a>CAtlMap::GetNextKey  
 Volat tuto metodu pro načtení Další klíč z `CAtlMap` objektu.  
  
```
const K& GetNextKey(POSITION& pos) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Čítač pozice vrácené z předchozího volání [CAtlMap::GetNextAssoc](#getnextassoc) nebo [CAtlMap::GetStartPosition](#getstartposition).  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí odkaz na další klíč v mapě.  
  
### <a name="remarks"></a>Poznámky  
 Čítač aktuální pozici aktualizace `pos`. Pokud nejsou žádné další položky v mapě, je pozice čítač nastaven na hodnotu NULL.  
  
##  <a name="getnextvalue"></a>CAtlMap::GetNextValue  
 Voláním této metody lze získat další hodnotu z `CAtlMap` objektu.  
  
```
V& GetNextValue(POSITION& pos) throw();
const V& GetNextValue(POSITION& pos) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Čítač pozice vrácené z předchozího volání [CAtlMap::GetNextAssoc](#getnextassoc) nebo [CAtlMap::GetStartPosition](#getstartposition).  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí odkaz na nejbližší hodnotu v mapě.  
  
### <a name="remarks"></a>Poznámky  
 Čítač aktuální pozici aktualizace `pos`. Pokud nejsou žádné další položky v mapě, je pozice čítač nastaven na hodnotu NULL.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CAtlMap::CAtlMap](#catlmap).  
  
##  <a name="getstartposition"></a>CAtlMap::GetStartPosition  
 Volejte tuto metodu za účelem spuštění iterace mapy.  
  
```
POSITION GetStartPosition() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí že počáteční pozici nebo hodnota NULL, je vrácena v případě, že mapy je prázdný.  
  
### <a name="remarks"></a>Poznámky  
 Volat tuto metodu za účelem spuštění mapy iterace vrácením **pozice** hodnotu, která se dá předat do `GetNextAssoc` metoda.  
  
> [!NOTE]
>  Iterace pořadí není předvídatelný  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CAtlMap::CAtlMap](#catlmap).  
  
##  <a name="getvalueat"></a>CAtlMap::GetValueAt  
 Volat tuto metodu za účelem načtení s hodnotou uloženou na dané pozici v `CAtlMap` objektu.  
  
```
V& GetValueAt(POSITION pos) throw();
const V& GetValueAt(POSITION pos) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Čítač pozice vrácené z předchozího volání [CAtlMap::GetNextAssoc](#getnextassoc) nebo [CAtlMap::GetStartPosition](#getstartposition).  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí odkaz na s hodnotou uloženou na dané pozici v `CAtlMap` objektu.  
  
##  <a name="inithashtable"></a>CAtlMap::InitHashTable  
 Volejte tuto metodu za účelem inicializace zatřiďovací tabulku.  
  
```
bool InitHashTable(
    UINT nBins,
    bool bAllocNow = true);
```  
  
### <a name="parameters"></a>Parametry  
 `nBins`  
 Počet přihrádek používané zatřiďovací tabulku. V tématu [CAtlMap::CAtlMap](#catlmap) vysvětlení.  
  
 `bAllocNow`  
 Příznak označení, pokud by měl být přidělit paměť.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** na úspěšné inicializace **false** při selhání.  
  
### <a name="remarks"></a>Poznámky  
 `InitHashTable`musí být voláno před všechny elementy jsou uložené v zatřiďovací tabulce.  Pokud tato metoda není volána explicitně, bude zavolána automaticky poprvé element přidána pomocí počet bin určeného **CAtlMap** konstruktor.  Jinak, mapy, budou inicializována pomocí počet nových bin určeného `nBins` parametr.  
  
 Pokud `bAllocNow` parametr je hodnota false, paměť vyžadovanou zatřiďovací tabulku nebude přidělují, dokud je nejdřív potřeba. To může být užitečné, pokud je jisti, zda se použije mapy.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CAtlMap::CAtlMap](#catlmap).  
  
##  <a name="isempty"></a>CAtlMap::IsEmpty  
 Volejte tuto metodu za účelem testování pro objekt prázdný mapy.  
  
```
bool IsEmpty() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud mapy je prázdný, **false** jinak.  
  
##  <a name="kinargtype"></a>CAtlMap::KINARGTYPE  
 Typ použitý při klíč se předá jako vstupní argument.  
  
```
typedef KTraits::INARGTYPE KINARGTYPE;
```  
  
##  <a name="koutargtype"></a>CAtlMap::KOUTARGTYPE  
 Typ použitý při klíč se vrátí jako argument výstup.  
  
```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```  
  
##  <a name="lookup"></a>CAtlMap::Lookup  
 Volat tuto metodu za účelem vyhledání klíče nebo hodnoty ve `CAtlMap` objektu.  
  
```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const;
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Určuje klíč, který identifikuje elementu, který chcete vyhledávat.  
  
 *Hodnota*  
 Proměnná, která přijímá vyhledaných hodnota.  
  
### <a name="return-value"></a>Návratová hodnota  
 První formulář metoda vrátí hodnotu true, pokud je nalezen klíč, jinak hodnota false. Vrátí ukazatel na druhý a třetí formuláře [CPair](#cpair_class) který můžete použít jako pozice pro volání [CAtlMap::GetNext](#getnext) a tak dále.  
  
### <a name="remarks"></a>Poznámky  
 `Lookup`používá algoritmus hash a rychle tak najít elementu mapy obsahující klíč, který přesně odpovídá zadanému parametru klíče.  
  
##  <a name="operator_at"></a>CAtlMap::operator\[\]  
 Nahradí nebo ho přidá nového elementu na `CAtlMap`.  
  
```
V& operator[](kinargtype key) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klíč elementu, který chcete přidat nebo nahradit.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí odkaz na hodnotu spojené s daným klíčem.  
  
### <a name="example"></a>Příklad  
 Pokud klíč již existuje, je nahradí element. Pokud klíč neexistuje, bude přidán nový element. Podívejte se na příklad pro [CAtlMap::CAtlMap](#catlmap).  
  
##  <a name="rehash"></a>CAtlMap::Rehash  
 Volat tuto metodu za účelem rehash `CAtlMap` objektu.  
  
```
void Rehash(UINT nBins = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `nBins`  
 Nové číslo přihrádek pro použití v zatřiďovací tabulce. V tématu [CAtlMap::CAtlMap](#catlmap) vysvětlení.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `nBins` 0, `CAtlMap` vypočítá přiměřené číslo na základě počtu elementů v mapě a zatížení optimální nastavení. Normálně rehashing proces je automatické, avšak v tom případě [CAtlMap::DisableAutoRehash](#disableautorehash) byla volána, tato metoda provede potřebné změny velikosti.  
  
##  <a name="removeall"></a>CAtlMap::RemoveAll  
 Voláním této metody lze odebrat všechny elementy z `CAtlMap` objektu.  
  
```
void RemoveAll() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Vymaže `CAtlMap` objekt, uvolnění paměti používá k ukládání elementy.  
  
##  <a name="removeatpos"></a>CAtlMap::RemoveAtPos  
 Voláním této metody lze odebrat – element na dané pozici v `CAtlMap` objektu.  
  
```
void RemoveAtPos(POSITION pos) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Čítač pozice vrácené z předchozího volání [CAtlMap::GetNextAssoc](#getnextassoc) nebo [CAtlMap::GetStartPosition](#getstartposition).  
  
### <a name="remarks"></a>Poznámky  
 Odebere dvojice klíč/hodnota, které jsou uložené na zadané pozici. Je uvolnit paměť, používá k ukládání elementu. POZICE odkazuje `pos` stává neplatným a při pozice další prvky v mapě zůstane platná, nemusí nutně jít udělají zachovat stejné pořadí.  
  
##  <a name="removekey"></a>CAtlMap::RemoveKey  
 Voláním této metody lze odebrat element z `CAtlMap` objekt, daný klíč.  
  
```
bool RemoveKey(KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klíč odpovídající element pár chcete odebrat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud je klíč nalezen a odebrat, **false** při selhání.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CAtlMap::CAtlMap](#catlmap).  
  
##  <a name="setat"></a>CAtlMap::SetAt  
 Volejte tuto metodu za účelem vložení dvojici element do mapy.  
  
```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value);
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Hodnota klíče pro přidání do `CAtlMap` objektu.  
  
 *Hodnota*  
 Hodnota k přidání do `CAtlMap` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí pozici element dvojice klíč/hodnota v `CAtlMap` objektu.  
  
### <a name="remarks"></a>Poznámky  
 `SetAt`nahradí existující elementu, pokud je nalezen odpovídající klíč. Pokud není nalezen klíč, vytvoří se nový pár klíč/hodnota.  
  
##  <a name="setoptimalload"></a>CAtlMap::SetOptimalLoad  
 Volat tuto metodu a nastavit optimální zátěž `CAtlMap` objektu.  
  
```
void SetOptimalLoad(
    float fOptimalLoad,
    float fLoThreshold,
    float fHiThreshold,
    bool bRehashNow = false);
```  
  
### <a name="parameters"></a>Parametry  
 `fOptimalLoad`  
 Poměr optimální zatížení.  
  
 `fLoThreshold`  
 Nižší prahová hodnota pro poměru zatížení.  
  
 `fHiThreshold`  
 Vyšší prahová hodnota pro poměru zatížení.  
  
 `bRehashNow`  
 Příznak, označuje, zda by měla být přepočítána zatřiďovací tabulku.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda znovu definuje hodnotu optimální zatížení `CAtlMap` objektu. V tématu [CAtlMap::CAtlMap](#catlmap) diskuzi o různé parametry. Pokud `bRehashNow` má hodnotu true a počet elementů je mimo minimální a maximální hodnoty, jsou přepočítána zatřiďovací tabulku.  
  
##  <a name="setvalueat"></a>CAtlMap::SetValueAt  
 Voláním této metody lze změnit hodnotu uloženou na dané pozici v `CAtlMap` objektu.  
  
```
void SetValueAt(
    POSITION pos,
    VINARGTYPE value);
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Čítač pozice vrácené z předchozího volání [CAtlMap::GetNextAssoc](#getnextassoc) nebo [CAtlMap::GetStartPosition](#getstartposition).  
  
 *Hodnota*  
 Hodnota k přidání do `CAtlMap` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Změní hodnotu elementu uložené na dané pozici v `CAtlMap` objektu.  
  
##  <a name="vinargtype"></a>CAtlMap::VINARGTYPE  
 Typ použitý při hodnotu se předá jako vstupní argument.  
  
```
typedef VTraits::INARGTYPE VINARGTYPE;
```  
  
##  <a name="voutargtype"></a>CAtlMap::VOUTARGTYPE  
 Typ použitý při hodnotu je předat jako argument výstup.  
  
```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```  
  
##  <a name="m_key"></a>CAtlMap::CPair::m_key  
 Datový člen ukládání klíče elementu.  
  
```
const K m_key;
```    
  
### <a name="parameters"></a>Parametry  
 `K`  
 Typ klíče elementu.  
  
##  <a name="m_value"></a>CAtlMap::CPair::m_value  
 Datový člen ukládání prvku hodnoty.  
  
```
V  m_value;
```    
  
### <a name="parameters"></a>Parametry  
 *V*  
 Typ elementu hodnotu.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka rámeček](../../visual-cpp-samples.md)   
 [Příklad UpdatePV](../../visual-cpp-samples.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
