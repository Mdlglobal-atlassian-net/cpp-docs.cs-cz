---
title: CAtlMap – třída
ms.date: 11/04/2016
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
helpviewer_keywords:
- CAtlMap class
ms.assetid: 5e2fe028-8e6d-4686-93df-1433d2080ec3
ms.openlocfilehash: b79e6cbd796569e6ba11c96158099de6c30b310a
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168056"
---
# <a name="catlmap-class"></a>CAtlMap – třída

Tato třída poskytuje metody pro vytvoření a správu objektu mapy.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename K,
          typename V,
          class KTraits = CElementTraits<K>,
          class VTraits = CElementTraits<V>>
class CAtlMap
```

### <a name="parameters"></a>Parametry

*K*<br/>
Klíčový typ elementu.

*ICES*<br/>
Typ elementu hodnoty.

*KTraits*<br/>
Kód použitý ke kopírování nebo přesunutí klíčových prvků. Další podrobnosti najdete v tématu [Třída CElementTraits](../../atl/reference/celementtraits-class.md) .

*VTraits*<br/>
Kód použitý ke zkopírování nebo přesunutí hodnot prvků.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Název|Popis|
|----------|-----------------|
|[CAtlMap::KINARGTYPE](#kinargtype)|Typ, který se použije, když se klíč předává jako vstupní argument.|
|[CAtlMap::KOUTARGTYPE](#koutargtype)|Typ, který se použije, když se klíč vrátí jako výstupní argument.|
|[CAtlMap::VINARGTYPE](#vinargtype)|Typ, který se použije, když se hodnota předává jako vstupní argument.|
|[CAtlMap::VOUTARGTYPE](#voutargtype)|Typ, který se použije, když se hodnota předává jako výstupní argument.|

### <a name="public-classes"></a>Veřejné třídy

|Název|Popis|
|----------|-----------------|
|[CAtlMap:: CPair – třída](#cpair_class)|Třída obsahující prvky klíče a hodnoty.|

### <a name="cpair-data-members"></a>Datové členy CPair

|Název|Popis|
|----------|-----------------|
|[CPair:: m_key](#m_key)|Datový člen, který ukládá klíč elementu.|
|[CPair:: m_value](#m_value)|Datový člen, který ukládá prvek hodnoty.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAtlMap::CAtlMap](#catlmap)|Konstruktor|
|[CAtlMap:: ~ CAtlMap](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAtlMap::AssertValid](#assertvalid)|Zavolejte tuto metodu, aby způsobila kontrolní výraz `CAtlMap` , pokud není platný.|
|[CAtlMap::D isableAutoRehash](#disableautorehash)|Voláním této metody zakážete automatické přegenerování hodnot hash `CAtlMap` objektu.|
|[CAtlMap::EnableAutoRehash](#enableautorehash)|Zavolejte tuto metodu, pokud chcete povolit automatické převrácení hodnot `CAtlMap` hash objektu.|
|[CAtlMap::GetAt](#getat)|Voláním této metody vrátí prvek na zadané pozici v mapě.|
|[CAtlMap:: GetCount](#getcount)|Voláním této metody načtete počet prvků v mapě.|
|[CAtlMap::GetHashTableSize](#gethashtablesize)|Voláním této metody určíte počet přihrádek v tabulce hash mapy.|
|[CAtlMap::GetKeyAt](#getkeyat)|Voláním této metody načtete klíč uložený na dané pozici v `CAtlMap` objektu.|
|[CAtlMap:: GetNext](#getnext)|Zavolejte tuto metodu, chcete-li získat ukazatel na další pár prvků uložený `CAtlMap` v objektu.|
|[CAtlMap::GetNextAssoc](#getnextassoc)|Získá další prvek pro iteraci.|
|[CAtlMap::GetNextKey](#getnextkey)|Voláním této metody načtete další klíč z `CAtlMap` objektu.|
|[CAtlMap::GetNextValue](#getnextvalue)|Zavolejte tuto metodu pro získání další hodnoty z `CAtlMap` objektu.|
|[CAtlMap::GetStartPosition](#getstartposition)|Voláním této metody spustíte iteraci mapy.|
|[CAtlMap::GetValueAt](#getvalueat)|Voláním této metody načtete hodnotu uloženou v dané pozici v `CAtlMap` objektu.|
|[CAtlMap::InitHashTable](#inithashtable)|Voláním této metody inicializujete zatřiďovací tabulku.|
|[CAtlMap::-Empty](#isempty)|Voláním této metody otestujete prázdný objekt mapy.|
|[CAtlMap:: Lookup](#lookup)|Zavolejte tuto metodu pro vyhledání klíčů nebo hodnot v `CAtlMap` objektu.|
|[CAtlMap:: rehash – hodnota](#rehash)|Voláním této metody znovu vyhodnotit hodnotu hash `CAtlMap` objektu.|
|[CAtlMap::RemoveAll](#removeall)|Voláním této metody odeberete všechny prvky z `CAtlMap` objektu.|
|[CAtlMap::RemoveAtPos](#removeatpos)|Zavolejte tuto metodu pro odebrání prvku na dané pozici v `CAtlMap` objektu.|
|[CAtlMap::RemoveKey](#removekey)|Voláním této metody odeberete prvek z `CAtlMap` objektu, který je daným klíčem.|
|[CAtlMap::SetAt](#setat)|Voláním této metody vložíte dvojici elementů do mapy.|
|[CAtlMap::SetOptimalLoad](#setoptimalload)|Zavolejte tuto metodu pro nastavení optimálního zatížení `CAtlMap` objektu.|
|[CAtlMap::SetValueAt](#setvalueat)|Voláním této metody změníte hodnotu uloženou v dané pozici v `CAtlMap` objektu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CAtlMap:: operator\[\]](catlmap-class.md#operator_at)|Nahradí nebo přidá nový prvek do `CAtlMap`.|

## <a name="remarks"></a>Poznámky

`CAtlMap`poskytuje podporu pro pole mapování libovolného daného typu a spravuje neuspořádané pole klíčových prvků a jejich přidružených hodnot. Prvky (skládající se z klíče a hodnoty) jsou uloženy pomocí algoritmu hash, který umožňuje efektivně Uložit a načíst velké množství dat.

Parametry *KTraits* a *VTraits* jsou vlastnosti třídy, které obsahují jakýkoliv doplňkový kód potřebný ke kopírování nebo přesunutí prvků.

Alternativa k `CAtlMap` je nabízena třídou [CRBMap](../../atl/reference/crbmap-class.md) . `CRBMap`také ukládá páry klíč/hodnota, ale vykazuje různé charakteristiky výkonu. Čas potřebný k vložení položky, vyhledání klíče nebo odstranění klíče z `CRBMap` objektu je pořadí *protokolu (n)*, kde *n* je počet prvků. U `CAtlMap`všech těchto operací obvykle trvá konstantní čas, ale nejhorších případů může být objednávka *n*. Proto `CAtlMap` je v typickém případě rychlejší.

Druhý rozdíl mezi `CRBMap` a `CAtlMap` se projeví při iteraci prostřednictvím uložených prvků. V `CRBMap`, jsou prvky navštíveny v seřazeném pořadí. V `CAtlMap`, prvky nejsou seřazené a nelze odvodit žádnou objednávku.

Pokud je třeba uložit malý počet prvků, zvažte místo toho použití třídy [CSimpleMap](../../atl/reference/csimplemap-class.md) .

Další informace naleznete v tématu [třídy kolekcí ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll. h

## <a name="catlmapassertvalid"></a><a name="assertvalid"></a>CAtlMap::AssertValid

Zavolejte tuto metodu, aby způsobila kontrolní výraz `CAtlMap` , pokud je objekt neplatný.

```cpp
void AssertValid() const;
```

### <a name="remarks"></a>Poznámky

V ladicích sestaveních Tato metoda vyvolá kontrolní výraz, pokud `CAtlMap` je objekt neplatný.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlMap:: CAtlMap](#catlmap).

## <a name="catlmapcatlmap"></a><a name="catlmap"></a>CAtlMap::CAtlMap

Konstruktor

```cpp
CAtlMap(
    UINT nBins = 17,
    float fOptimalLoad = 0.75f,
    float fLoThreshold = 0.25f,
    float fHiThreshold = 2.25f,
    UINT nBlockSize = 10) throw ();
```

### <a name="parameters"></a>Parametry

*nBins*<br/>
Počet přihrádek, které poskytují ukazatele na uložené prvky. Vysvětlení přihrádek najdete v části poznámky dále v tomto tématu.

*fOptimalLoad*<br/>
Optimální poměr zatížení.

*fLoThreshold*<br/>
Dolní prahová hodnota poměru zatížení.

*fHiThreshold*<br/>
Horní prahová hodnota pro poměr zatížení.

*nBlockSize*<br/>
Velikost bloku

### <a name="remarks"></a>Poznámky

`CAtlMap`odkazuje na všechny uložené prvky nejprve vytvořením indexu pomocí algoritmu hash na klíč. Tento index odkazuje na "přihrádku", která obsahuje ukazatel na uložené prvky. Pokud je přihrádka již používána, je vytvořen propojený seznam pro přístup k dalším prvkům. Procházení seznamu je pomalejší než přímý přístup ke správnému prvku, takže struktura mapy musí vyvážit požadavky na úložiště proti výkonu. Ve většině případů byly zvoleny výchozí parametry k poskytnutí dobrých výsledků.

Poměr zatížení je poměr počtu přihrádek k počtu prvků uložených v objektu map. Při přepočítání struktury mapy se hodnota parametru *fOptimalLoad* použije k výpočtu počtu požadovaných přihrádek. Tuto hodnotu lze změnit pomocí metody [CAtlMap:: SetOptimalLoad](#setoptimalload) .

Parametr *fLoThreshold* je nižší hodnota, kterou může poměr zatížení dosáhnout, než `CAtlMap` bude přepočítána optimální velikost mapy.

Parametr *fHiThreshold* je horní hodnota, kterou může poměr zatížení dosáhnout, než bude `CAtlMap` objekt přepočítat optimální velikost mapy.

Tento proces přepočítání (označovaný jako rehashing) je ve výchozím nastavení povolený. Pokud chcete tento proces zakázat, třeba při současném zadání velkého množství dat, zavolejte metodu [CAtlMap::D isableautorehash](#disableautorehash) . Znovu ji aktivujte pomocí metody [CAtlMap:: EnableAutoRehash](#enableautorehash) .

Parametr *nBlockSize* je míra množství paměti přidělené při požadování nového prvku. Větší velikosti bloků snižují volání rutin přidělování paměti, ale používají více prostředků.

Předtím, než mohou být data uložena, je nutné inicializovat zatřiďovací tabulku voláním metody [CAtlMap:: InitHashTable](#inithashtable).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#72](../../atl/codesnippet/cpp/catlmap-class_1.cpp)]

## <a name="catlmapcatlmap"></a><a name="dtor"></a>CAtlMap:: ~ CAtlMap

Destruktor.

```cpp
~CAtlMap() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky.

## <a name="catlmapcpair-class"></a><a name="cpair_class"></a>CAtlMap:: CPair – třída

Třída obsahující prvky klíče a hodnoty.

```cpp
class CPair : public __POSITION
```

### <a name="remarks"></a>Poznámky

Tuto třídu používají metody [CAtlMap:: GetNext](#getnext) a [CAtlMap:: Lookup](#lookup) pro přístup k klíčovým a hodnotovým prvkům uloženým ve struktuře mapování.

## <a name="catlmapdisableautorehash"></a><a name="disableautorehash"></a>CAtlMap::D isableAutoRehash

Voláním této metody zakážete automatické přegenerování hodnot hash `CAtlMap` objektu.

```cpp
void DisableAutoRehash() throw();
```

### <a name="remarks"></a>Poznámky

Pokud je povoleno automatické opětovné použití algoritmu hash (což je ve výchozím nastavení), počet přihrádek v zatřiďovací tabulce bude automaticky přepočítán, pokud hodnota zatížení (poměr počtu přihrádek k počtu prvků uložených v poli) překračuje maximální nebo minimální hodnoty zadané v době vytvoření mapy.

`DisableAutoRehash`je nejužitečnější, když se do mapy najednou přidá velký počet prvků. Namísto aktivace procesu rehashování při každém překročení omezení je efektivnější volat `DisableAutoRehash`, přidat prvky a nakonec zavolat [CAtlMap:: EnableAutoRehash](#enableautorehash).

## <a name="catlmapenableautorehash"></a><a name="enableautorehash"></a>CAtlMap::EnableAutoRehash

Zavolejte tuto metodu, pokud chcete povolit automatické převrácení hodnot `CAtlMap` hash objektu.

```cpp
void EnableAutoRehash() throw();
```

### <a name="remarks"></a>Poznámky

Pokud je povoleno automatické opětovné použití algoritmu hash (což je ve výchozím nastavení), počet přihrádek v zatřiďovací tabulce bude automaticky přepočítán, pokud hodnota zatížení (poměr počtu přihrádek k počtu prvků uložených v poli) překračuje maximální nebo minimální hodnoty zadané v době vytvoření mapy.

`EnableAutoRefresh`se nejčastěji používá po volání [CAtlMap::D isableautorehash](#disableautorehash).

## <a name="catlmapgetat"></a><a name="getat"></a>CAtlMap::GetAt

Voláním této metody vrátí prvek na zadané pozici v mapě.

```cpp
void GetAt(
    POSITION pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;

CPair* GetAt(POSITION& pos) throw();
```

### <a name="parameters"></a>Parametry

*POS*<br/>
Čítač pozice vrácený předchozím voláním [CAtlMap:: GetNextAssoc](#getnextassoc) nebo [CAtlMap:: GetStartPosition](#getstartposition).

*zkrat*<br/>
Parametr šablony určující typ klíče mapy.

*value*<br/>
Parametr šablony určující typ hodnoty mapy.

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na aktuální dvojici prvků klíč/hodnota uložených v mapě.

### <a name="remarks"></a>Poznámky

V sestavení ladění dojde k chybě kontrolního výrazu, pokud je *POS* rovna hodnotě null.

## <a name="catlmapgetcount"></a><a name="getcount"></a>CAtlMap:: GetCount

Voláním této metody načtete počet prvků v mapě.

```cpp
size_t GetCount() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet prvků v objektu map. Jediným prvkem je pár klíč/hodnota.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlMap:: CAtlMap](#catlmap).

## <a name="catlmapgethashtablesize"></a><a name="gethashtablesize"></a>CAtlMap::GetHashTableSize

Voláním této metody určíte počet přihrádek v tabulce hash mapy.

```cpp
UINT GetHashTableSize() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet přihrádek v zatřiďovací tabulce. Vysvětlení naleznete v tématu [CAtlMap:: CAtlMap](#catlmap) .

## <a name="catlmapgetkeyat"></a><a name="getkeyat"></a>CAtlMap::GetKeyAt

Voláním této metody načtete klíč uložený na dané pozici v `CAtlMap` objektu.

```cpp
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parametry

*POS*<br/>
Čítač pozice vrácený předchozím voláním [CAtlMap:: GetNextAssoc](#getnextassoc) nebo [CAtlMap:: GetStartPosition](#getstartposition).

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na klíč uložený na dané pozici v `CAtlMap` objektu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlMap:: CAtlMap](#catlmap).

## <a name="catlmapgetnext"></a><a name="getnext"></a>CAtlMap:: GetNext

Zavolejte tuto metodu, chcete-li získat ukazatel na další pár prvků uložený `CAtlMap` v objektu.

```cpp
CPair* GetNext(POSITION& pos) throw();
const CPair* GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parametry

*POS*<br/>
Čítač pozice vrácený předchozím voláním [CAtlMap:: GetNextAssoc](#getnextassoc) nebo [CAtlMap:: GetStartPosition](#getstartposition).

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na další dvojici prvků klíč/hodnota uložených v mapě. Čítač pozice *POS* se aktualizuje po každém volání. Pokud je načtený element poslední v mapě, *POS* je nastaven na hodnotu null.

## <a name="catlmapgetnextassoc"></a><a name="getnextassoc"></a>CAtlMap::GetNextAssoc

Získá další prvek pro iteraci.

```cpp
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>Parametry

*POS*<br/>
Čítač pozice vrácený předchozím voláním [CAtlMap:: GetNextAssoc](#getnextassoc) nebo [CAtlMap:: GetStartPosition](#getstartposition).

*zkrat*<br/>
Parametr šablony určující typ klíče mapy.

*value*<br/>
Parametr šablony určující typ hodnoty mapy.

### <a name="remarks"></a>Poznámky

Čítač pozice *POS* se aktualizuje po každém volání. Pokud je načtený element poslední v mapě, *POS* je nastaven na hodnotu null.

## <a name="catlmapgetnextkey"></a><a name="getnextkey"></a>CAtlMap::GetNextKey

Voláním této metody načtete další klíč z `CAtlMap` objektu.

```cpp
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parametry

*POS*<br/>
Čítač pozice vrácený předchozím voláním [CAtlMap:: GetNextAssoc](#getnextassoc) nebo [CAtlMap:: GetStartPosition](#getstartposition).

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na další klíč v mapě.

### <a name="remarks"></a>Poznámky

Aktualizuje čítač aktuální pozice, *POS*. Pokud na mapě nejsou žádné další položky, je čítač pozice nastaven na hodnotu NULL.

## <a name="catlmapgetnextvalue"></a><a name="getnextvalue"></a>CAtlMap::GetNextValue

Zavolejte tuto metodu pro získání další hodnoty z `CAtlMap` objektu.

```cpp
V& GetNextValue(POSITION& pos) throw();
const V& GetNextValue(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parametry

*POS*<br/>
Čítač pozice vrácený předchozím voláním [CAtlMap:: GetNextAssoc](#getnextassoc) nebo [CAtlMap:: GetStartPosition](#getstartposition).

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na další hodnotu v mapě.

### <a name="remarks"></a>Poznámky

Aktualizuje čítač aktuální pozice, *POS*. Pokud na mapě nejsou žádné další položky, je čítač pozice nastaven na hodnotu NULL.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlMap:: CAtlMap](#catlmap).

## <a name="catlmapgetstartposition"></a><a name="getstartposition"></a>CAtlMap::GetStartPosition

Voláním této metody spustíte iteraci mapy.

```cpp
POSITION GetStartPosition() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počáteční pozici, nebo je vrácena hodnota NULL, pokud je mapa prázdná.

### <a name="remarks"></a>Poznámky

Voláním této metody spustíte iteraci mapy vrácením hodnoty pozice, kterou lze předat `GetNextAssoc` metodě.

> [!NOTE]
> Posloupnost iterace není předvídatelná.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlMap:: CAtlMap](#catlmap).

## <a name="catlmapgetvalueat"></a><a name="getvalueat"></a>CAtlMap::GetValueAt

Voláním této metody načtete hodnotu uloženou v dané pozici v `CAtlMap` objektu.

```cpp
V& GetValueAt(POSITION pos) throw();
const V& GetValueAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parametry

*POS*<br/>
Čítač pozice vrácený předchozím voláním [CAtlMap:: GetNextAssoc](#getnextassoc) nebo [CAtlMap:: GetStartPosition](#getstartposition).

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na hodnotu uloženou na dané pozici v `CAtlMap` objektu.

## <a name="catlmapinithashtable"></a><a name="inithashtable"></a>CAtlMap::InitHashTable

Voláním této metody inicializujete zatřiďovací tabulku.

```cpp
bool InitHashTable(
    UINT nBins,
    bool bAllocNow = true);
```

### <a name="parameters"></a>Parametry

*nBins*<br/>
Počet přihrádek využívaných zatřiďovací tabulkou. Vysvětlení naleznete v tématu [CAtlMap:: CAtlMap](#catlmap) .

*bAllocNow*<br/>
Označení příznaku, když má být přidělena paměť

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěšné inicializaci, hodnota FALSE při selhání.

### <a name="remarks"></a>Poznámky

`InitHashTable`musí být volána před tím, než jsou všechny prvky uloženy v zatřiďovací tabulce.  Pokud tato metoda není volána explicitně, bude volána automaticky při prvním přidání prvku pomocí počtu přihrádek určeného `CAtlMap` konstruktorem.  V opačném případě se mapa inicializuje pomocí nového počtu přihrádek zadaného parametrem *nBins* .

Pokud má parametr *bAllocNow* hodnotu false, paměť vyžadovaná zatřiďovací tabulkou nebude přidělena, dokud není nejprve vyžadováno. To může být užitečné, pokud není jisté, jestli se mapa použije.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlMap:: CAtlMap](#catlmap).

## <a name="catlmapisempty"></a><a name="isempty"></a>CAtlMap::-Empty

Voláním této metody otestujete prázdný objekt mapy.

```cpp
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je mapa prázdná, jinak FALSE.

## <a name="catlmapkinargtype"></a><a name="kinargtype"></a>CAtlMap::KINARGTYPE

Typ, který se použije, když se klíč předává jako vstupní argument.

```cpp
typedef KTraits::INARGTYPE KINARGTYPE;
```

## <a name="catlmapkoutargtype"></a><a name="koutargtype"></a>CAtlMap::KOUTARGTYPE

Typ, který se použije, když se klíč vrátí jako výstupní argument.

```cpp
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

## <a name="catlmaplookup"></a><a name="lookup"></a>CAtlMap:: Lookup

Zavolejte tuto metodu pro vyhledání klíčů nebo hodnot v `CAtlMap` objektu.

```cpp
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const;
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parametry

*zkrat*<br/>
Určuje klíč, který identifikuje prvek, který má být vyhledán.

*value*<br/>
Proměnná, která přijímá vyhledaná hodnotu.

### <a name="return-value"></a>Návratová hodnota

První forma metody vrátí hodnotu true, pokud je klíč nalezen, v opačném případě false. Druhý a třetí formulář vrátí ukazatel na [CPair](#cpair_class) , který lze použít jako pozici pro volání [CAtlMap:: GetNext](#getnext) a tak dále.

### <a name="remarks"></a>Poznámky

`Lookup`používá algoritmus hash k rychlému nalezení mapového prvku obsahujícího klíč, který přesně odpovídá zadanému klíčovému parametru.

## <a name="catlmapoperator-"></a><a name="operator_at"></a>CAtlMap:: operator\[\]

Nahradí nebo přidá nový prvek do `CAtlMap`.

```cpp
V& operator[](kinargtype key) throw();
```

### <a name="parameters"></a>Parametry

*zkrat*<br/>
Klíč elementu, který má být přidán nebo nahrazen.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na hodnotu přidruženou k danému klíči.

### <a name="example"></a>Příklad

Pokud klíč již existuje, element je nahrazen. Pokud klíč neexistuje, je přidán nový prvek. Podívejte se na příklad pro [CAtlMap:: CAtlMap](#catlmap).

## <a name="catlmaprehash"></a><a name="rehash"></a>CAtlMap:: rehash – hodnota

Voláním této metody znovu vyhodnotit hodnotu hash `CAtlMap` objektu.

```cpp
void Rehash(UINT nBins = 0);
```

### <a name="parameters"></a>Parametry

*nBins*<br/>
Nový počet přihrádek, které se mají použít v zatřiďovací tabulce. Vysvětlení naleznete v tématu [CAtlMap:: CAtlMap](#catlmap) .

### <a name="remarks"></a>Poznámky

Pokud je *nBins* 0, `CAtlMap` vypočítá přiměřené číslo na základě počtu prvků v mapě a optimálního nastavení zatížení. Proces rehashování je obvykle automatický, ale pokud byl volán [CAtlMap::D isableautorehash](#disableautorehash) , tato metoda provede potřebné změny velikosti.

## <a name="catlmapremoveall"></a><a name="removeall"></a>CAtlMap::RemoveAll

Voláním této metody odeberete všechny prvky z `CAtlMap` objektu.

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>Poznámky

Vymaže `CAtlMap` objekt a uvolní paměť, která se používá k uložení prvků.

## <a name="catlmapremoveatpos"></a><a name="removeatpos"></a>CAtlMap::RemoveAtPos

Zavolejte tuto metodu pro odebrání prvku na dané pozici v `CAtlMap` objektu.

```cpp
void RemoveAtPos(POSITION pos) throw();
```

### <a name="parameters"></a>Parametry

*POS*<br/>
Čítač pozice vrácený předchozím voláním [CAtlMap:: GetNextAssoc](#getnextassoc) nebo [CAtlMap:: GetStartPosition](#getstartposition).

### <a name="remarks"></a>Poznámky

Odebere dvojici klíč/hodnota uloženou na určené pozici. Paměť použitá k uložení elementu je uvolněna. POZICE, na kterou se odkazuje v *POS* , se změní na neplatnou, a když pozice všech ostatních prvků v mapě zůstane platná, nemusí nutně uchovávat stejnou objednávku.

## <a name="catlmapremovekey"></a><a name="removekey"></a>CAtlMap::RemoveKey

Voláním této metody odeberete prvek z `CAtlMap` objektu, který je daným klíčem.

```cpp
bool RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parametry

*zkrat*<br/>
Klíč odpovídající páru prvků, který chcete odebrat.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud se klíč najde a odebere, hodnota FALSE při selhání.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlMap:: CAtlMap](#catlmap).

## <a name="catlmapsetat"></a><a name="setat"></a>CAtlMap::SetAt

Voláním této metody vložíte dvojici elementů do mapy.

```cpp
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value);
```

### <a name="parameters"></a>Parametry

*zkrat*<br/>
Hodnota klíče, která se má přidat `CAtlMap` do objektu.

*value*<br/>
Hodnota, která má být přidána `CAtlMap` do objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí pozici páru prvků klíč/hodnota v `CAtlMap` objektu.

### <a name="remarks"></a>Poznámky

`SetAt`nahradí existující prvek, pokud se najde shodný klíč. Pokud se klíč nenajde, vytvoří se nový pár klíč/hodnota.

## <a name="catlmapsetoptimalload"></a><a name="setoptimalload"></a>CAtlMap::SetOptimalLoad

Zavolejte tuto metodu pro nastavení optimálního zatížení `CAtlMap` objektu.

```cpp
void SetOptimalLoad(
    float fOptimalLoad,
    float fLoThreshold,
    float fHiThreshold,
    bool bRehashNow = false);
```

### <a name="parameters"></a>Parametry

*fOptimalLoad*<br/>
Optimální poměr zatížení.

*fLoThreshold*<br/>
Dolní prahová hodnota poměru zatížení.

*fHiThreshold*<br/>
Horní prahová hodnota pro poměr zatížení.

*bRehashNow*<br/>
Příznak označující, zda by měla být přepočítána zatřiďovací tabulka

### <a name="remarks"></a>Poznámky

Tato metoda předefinuje optimální hodnotu zatížení `CAtlMap` objektu. Diskuzi o různých parametrech najdete v tématu [CAtlMap:: CAtlMap](#catlmap) . Pokud má *bRehashNow* hodnotu true a počet prvků je mimo minimální a maximální hodnoty, zatřiďovací tabulka se přepočítá.

## <a name="catlmapsetvalueat"></a><a name="setvalueat"></a>CAtlMap::SetValueAt

Voláním této metody změníte hodnotu uloženou v dané pozici v `CAtlMap` objektu.

```cpp
void SetValueAt(
    POSITION pos,
    VINARGTYPE value);
```

### <a name="parameters"></a>Parametry

*POS*<br/>
Čítač pozice vrácený předchozím voláním [CAtlMap:: GetNextAssoc](#getnextassoc) nebo [CAtlMap:: GetStartPosition](#getstartposition).

*value*<br/>
Hodnota, která má být přidána `CAtlMap` do objektu.

### <a name="remarks"></a>Poznámky

Změní element Value uložený na dané pozici v `CAtlMap` objektu.

## <a name="catlmapvinargtype"></a><a name="vinargtype"></a>CAtlMap::VINARGTYPE

Typ, který se použije, když se hodnota předává jako vstupní argument.

```cpp
typedef VTraits::INARGTYPE VINARGTYPE;
```

## <a name="catlmapvoutargtype"></a><a name="voutargtype"></a>CAtlMap::VOUTARGTYPE

Typ, který se použije, když se hodnota předává jako výstupní argument.

```cpp
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

## <a name="catlmapcpairm_key"></a><a name="m_key"></a>CAtlMap:: CPair:: m_key

Datový člen, který ukládá klíč elementu.

```cpp
const K m_key;
```

### <a name="parameters"></a>Parametry

*K*<br/>
Klíčový typ elementu.

## <a name="catlmapcpairm_value"></a><a name="m_value"></a>CAtlMap:: CPair:: m_value

Datový člen, který ukládá prvek hodnoty.

```cpp
V  m_value;
```

### <a name="parameters"></a>Parametry

*ICES*<br/>
Typ elementu hodnoty.

## <a name="see-also"></a>Viz také

[Ukázka běžícího textu](../../overview/visual-cpp-samples.md)<br/>
[Ukázka UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
