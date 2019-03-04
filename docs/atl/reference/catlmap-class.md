---
title: Catlmap – třída
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
ms.openlocfilehash: 80975047b300f270c0ac58c8b8abfc59ff2b17ef
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57293781"
---
# <a name="catlmap-class"></a>Catlmap – třída

Tato třída poskytuje metody pro vytváření a správu objektu map.

## <a name="syntax"></a>Syntaxe

```
template <typename K,
          typename V,
          class KTraits = CElementTraits<K>,
          class VTraits = CElementTraits<V>>
class CAtlMap
```

#### <a name="parameters"></a>Parametry

*K*<br/>
Typ klíče prvku.

*V*<br/>
Typ elementu hodnota.

*KTraits*<br/>
Kód použitý má zkopírovat nebo přesunout klíčové prvky. Zobrazit [celementtraits – třída](../../atl/reference/celementtraits-class.md) další podrobnosti.

*VTraits*<br/>
Kód použitý má zkopírovat nebo přesunout elementy hodnotu.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|[CAtlMap::KINARGTYPE](#kinargtype)|Typ použitý klíč je předána jako vstupní argument|
|[CAtlMap::KOUTARGTYPE](#koutargtype)|Typ použitý při klíč se vrátí jako výstup argument.|
|[CAtlMap::VINARGTYPE](#vinargtype)|Typ použitý jako vstupní argument je předána hodnota.|
|[CAtlMap::VOUTARGTYPE](#voutargtype)|Typ použitý při je hodnota předána jako argument výstup.|

### <a name="public-classes"></a>Veřejné třídy

|Název|Popis|
|----------|-----------------|
|[CAtlMap::CPair Class](#cpair_class)|Třída obsahující prvky klíč a hodnotu.|

### <a name="cpair-data-members"></a>CPair datové členy

|Název|Popis|
|----------|-----------------|
|[CPair::m_key](#m_key)|Datový člen ukládání klíčovým prvkem.|
|[CPair::m_value](#m_value)|Datový člen ukládání prvku hodnoty.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAtlMap::CAtlMap](#catlmap)|Konstruktor|
|[CAtlMap::~CAtlMap](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAtlMap::AssertValid](#assertvalid)|Volejte tuto metodu za účelem způsobit ASSERT, pokud `CAtlMap` není platný.|
|[CAtlMap::DisableAutoRehash](#disableautorehash)|Voláním této metody lze zakázat automatické rehashing z `CAtlMap` objektu.|
|[CAtlMap::EnableAutoRehash](#enableautorehash)|Volejte tuto metodu za účelem povolení automatické rehashing z `CAtlMap` objektu.|
|[CAtlMap::GetAt](#getat)|Volání této metody k vrácení prvku na určené pozici v objektu map.|
|[CAtlMap::GetCount](#getcount)|Voláním této metody lze načíst počet prvků v objektu map.|
|[CAtlMap::GetHashTableSize](#gethashtablesize)|Voláním této metody lze určit počet přihrádek v zatřiďovací tabulky na mapě.|
|[CAtlMap::GetKeyAt](#getkeyat)|Voláním této metody lze načíst klíč uložený na dané pozici v `CAtlMap` objektu.|
|[CAtlMap::GetNext](#getnext)|Volejte tuto metodu za účelem získání ukazatele na další prvek pár ukládá v `CAtlMap` objektu.|
|[CAtlMap::GetNextAssoc](#getnextassoc)|Získá další prvek pro iterace.|
|[CAtlMap::GetNextKey](#getnextkey)|Voláním této metody lze načíst další klíč z `CAtlMap` objektu.|
|[CAtlMap::GetNextValue](#getnextvalue)|Volejte tuto metodu za účelem získání další hodnoty z `CAtlMap` objektu.|
|[CAtlMap::GetStartPosition](#getstartposition)|Volejte tuto metodu za účelem spuštění iterace mapy.|
|[CAtlMap::GetValueAt](#getvalueat)|Volejte tuto metodu za účelem načtení hodnoty uložené na dané pozici v `CAtlMap` objektu.|
|[CAtlMap::InitHashTable](#inithashtable)|Volejte tuto metodu za účelem inicializace zatřiďovací tabulku.|
|[CAtlMap::IsEmpty](#isempty)|Volejte tuto metodu za účelem testování pro objekt map prázdný.|
|[CAtlMap::Lookup](#lookup)|Volejte tuto metodu za účelem vyhledání klíče nebo hodnoty `CAtlMap` objektu.|
|[CAtlMap::Rehash](#rehash)|Volejte tuto metodu za účelem rehash `CAtlMap` objektu.|
|[CAtlMap::RemoveAll](#removeall)|Voláním této metody lze odebrat všechny prvky z `CAtlMap` objektu.|
|[CAtlMap::RemoveAtPos](#removeatpos)|Volejte tuto metodu za účelem odebrání elementu na dané pozici v `CAtlMap` objektu.|
|[CAtlMap::RemoveKey](#removekey)|Voláním této metody lze odebrat element z `CAtlMap` objekt daný klíč.|
|[CAtlMap::SetAt](#setat)|Voláním této metody lze vložit páru prvek do objektu map.|
|[CAtlMap::SetOptimalLoad](#setoptimalload)|Voláním této metody lze nastavit optimální zatížení `CAtlMap` objektu.|
|[CAtlMap::SetValueAt](#setvalueat)|Voláním této metody lze změnit hodnotu uloženou v dané pozici v `CAtlMap` objektu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CAtlMap::operator\[\]](catlmap-class.md#operator_at)|Nahradí nebo přidá nový prvek do `CAtlMap`.|

## <a name="remarks"></a>Poznámky

`CAtlMap` poskytuje podporu pro mapování pole daného typu, Správa Neseřazený pole klíčové prvky a jejich přidružené hodnoty. Elementy (skládající se z klíče a hodnoty) jsou uložené, pomocí algoritmu hash, povolení velké množství dat, efektivně uložit a načíst.

*KTraits* a *VTraits* parametry jsou třídy, které obsahují žádný doplňkový kód potřeba zkopírovat nebo přesunout prvky.

Alternativa k `CAtlMap` nabízí [crbmap –](../../atl/reference/crbmap-class.md) třídy. `CRBMap` také ukládá páry klíč/hodnota, ale je třeba jiné výkonové charakteristiky. Čas potřebný k vložení položky, vyhledejte klíč nebo odstranění klíče z `CRBMap` objekt je pořadí *log(n)*, kde *n* je počet elementů. Pro `CAtlMap`, všechny tyto operace obvykle trvá konstantním času, ačkoli nejhorším scénářích může být pořadí *n*. Proto se v typické případy `CAtlMap` je rychlejší.

Rozdíl mezi `CRBMap` a `CAtlMap` začíná být zřejmá při procházení uložené prvků. V `CRBMap`, prvky jsou zobrazeny v seřazeném pořadí. V `CAtlMap`prvky nejsou seřazené a jde odvodit žádné pořadí.

Pokud malý počet elementů musí být uložena, zvažte použití [csimplemap –](../../atl/reference/csimplemap-class.md) namísto třídy.

Další informace najdete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

##  <a name="assertvalid"></a>  CAtlMap::AssertValid

Volejte tuto metodu za účelem způsobit ASSERT, pokud `CAtlMap` objekt není platný.

```
void AssertValid() const;
```

### <a name="remarks"></a>Poznámky

V sestavení ladění, způsobí této metody ASSERT, pokud `CAtlMap` objekt není platný.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlMap::CAtlMap](#catlmap).

##  <a name="catlmap"></a>  CAtlMap::CAtlMap

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

*nBins*<br/>
Počet přihrádek poskytuje odkazy na prvky uložené. Viz poznámky níže v tomto tématu pro vysvětlení intervalů.

*fOptimalLoad*<br/>
Poměr optimální zatížení.

*fLoThreshold*<br/>
Nižší prahová hodnota pro poměr zatížení.

*fHiThreshold*<br/>
Horní prahová hodnota pro poměr zatížení.

*nBlockSize*<br/>
Velikost bloku.

### <a name="remarks"></a>Poznámky

`CAtlMap` všechny své uložené prvky odkazuje na první vytvořením indexu pomocí algoritmu hash klíče. Tento index odkazuje "bin" který obsahuje ukazatel na uložený elementy. Pokud přihrádky se už používá, vytvoří se pro přístup k prvkům následné propojené seznamy. Procházení seznamu je pomalejší než přímý přístup k elementu správné, a proto strukturu mapy musí k vyrovnávání požadavků na úložiště pro výkon. Poskytnout dobré výsledky ve většině případů být zvolena výchozí parametry.

Poměr zatížení je poměr počtu intervalů počtu prvků uloženou v objektu map. Při přepočtu strukturu mapy *fOptimalLoad* hodnota parametru se použije k výpočtu počet přihrádek vyžaduje. Tuto hodnotu můžete změnit pomocí [CAtlMap::SetOptimalLoad](#setoptimalload) metody.

*FLoThreshold* parametr je hodnota nižší, se kterým dosáhnete poměr zatížení před `CAtlMap` přepočítá optimální velikost mapy.

*FHiThreshold* parametr je horní hodnota, se kterým dosáhnete poměr zatížení před `CAtlMap` objekt přepočítá optimální velikost mapy.

Tento proces přepočet (označuje se jako rehashing) je standardně povolená. Pokud chcete zakázat tento proces, třeba při zadávání velké množství dat v jednom okamžiku volání [CAtlMap::DisableAutoRehash](#disableautorehash) metody. Znovu aktivovat ji [CAtlMap::EnableAutoRehash](#enableautorehash) metody.

*NBlockSize* parametr je míra množství paměti přidělené, pokud je nutné použít nový prvek. Bloky o větší velikosti snížit volání rutiny přidělení paměti, ale spotřebovávají více prostředků.

Předtím, než mohou být uloženy žádná data, je potřeba inicializovat zatřiďovací tabulku s voláním [CAtlMap::InitHashTable](#inithashtable).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#72](../../atl/codesnippet/cpp/catlmap-class_1.cpp)]

##  <a name="dtor"></a>  CAtlMap::~CAtlMap

Destruktor.

```
~CAtlMap() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky.

##  <a name="cpair_class"></a>  Třída CAtlMap::CPair

Třída obsahující prvky klíč a hodnotu.

```
class CPair : public __POSITION
```

### <a name="remarks"></a>Poznámky

Tato třída se používá metody [CAtlMap::GetNext](#getnext) a [CAtlMap::Lookup](#lookup) pro přístup k klíče a hodnoty prvků uložených ve struktuře mapování.

##  <a name="disableautorehash"></a>  CAtlMap::DisableAutoRehash

Voláním této metody lze zakázat automatické rehashing z `CAtlMap` objektu.

```
void DisableAutoRehash() throw();
```

### <a name="remarks"></a>Poznámky

Když automatické rehashing je povolené (která je ve výchozím nastavení), počet přihrádek v zatřiďovací tabulce se automaticky přepočítá Pokud se hodnota načtení (poměr počet přihrádek počtu prvků uložených v poli) překračuje maximální nebo minimální hodnoty zadaná v době, kdy byla vytvořena na mapě.

`DisableAutoRehash` je nejvhodnější pro velký počet elementů se přidají do mapy najednou. Místo spuštění rehashing procesu pokaždé, když překročení mezní hodnoty, je efektivnější volání `DisableAutoRehash`přidat prvky a nakonec zavolat [CAtlMap::EnableAutoRehash](#enableautorehash).

##  <a name="enableautorehash"></a>  CAtlMap::EnableAutoRehash

Volejte tuto metodu za účelem povolení automatické rehashing z `CAtlMap` objektu.

```
void EnableAutoRehash() throw();
```

### <a name="remarks"></a>Poznámky

Když automatické rehashing je povolené (která je ve výchozím nastavení), počet přihrádek v zatřiďovací tabulce se automaticky přepočítá Pokud se hodnota načtení (poměr počet přihrádek počtu prvků uložených v poli) překračuje maximální nebo minimální hodnoty zadaná v době, kdy je vytvořen na mapě.

`EnableAutoRefresh` nejčastěji se používá po volání [CAtlMap::DisableAutoRehash](#disableautorehash).

##  <a name="getat"></a>  CAtlMap::GetAt

Volání této metody k vrácení prvku na určené pozici v objektu map.

```
void GetAt(
    POSITION pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;

CPair* GetAt(POSITION& pos) throw();
```

### <a name="parameters"></a>Parametry

*pos*<br/>
Čítač pozice vrácené z předchozího volání [CAtlMap::GetNextAssoc](#getnextassoc) nebo [CAtlMap::GetStartPosition](#getstartposition).

*key*<br/>
Parametr šablony určující typ klíče na mapě.

*value*<br/>
Parametr šablony určující typ hodnoty na mapě.

### <a name="return-value"></a>Návratová hodnota

Vrací ukazatel na aktuální dvojice klíč/hodnota prvků uložených v objektu map.

### <a name="remarks"></a>Poznámky

V sestavení ladění, dojde k chybě kontrolního výrazu Pokud *pos* je rovna hodnotě NULL.

##  <a name="getcount"></a>  CAtlMap::GetCount

Voláním této metody lze načíst počet prvků v objektu map.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet prvků v objektu map. Jeden prvek je dvojice klíč/hodnota.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlMap::CAtlMap](#catlmap).

##  <a name="gethashtablesize"></a>  CAtlMap::GetHashTableSize

Voláním této metody lze určit počet přihrádek v zatřiďovací tabulky na mapě.

```
UINT GetHashTableSize() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet přihrádek v zatřiďovací tabulce. Zobrazit [CAtlMap::CAtlMap](#catlmap) vysvětlení.

##  <a name="getkeyat"></a>  CAtlMap::GetKeyAt

Voláním této metody lze načíst klíč uložený na dané pozici v `CAtlMap` objektu.

```
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parametry

*pos*<br/>
Čítač pozice vrácené z předchozího volání [CAtlMap::GetNextAssoc](#getnextassoc) nebo [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na klíč uložený na dané pozici v `CAtlMap` objektu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlMap::CAtlMap](#catlmap).

##  <a name="getnext"></a>  CAtlMap::GetNext

Volejte tuto metodu za účelem získání ukazatele na další prvek pár ukládá v `CAtlMap` objektu.

```
CPair* GetNext(POSITION& pos) throw();
const CPair* GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parametry

*pos*<br/>
Čítač pozice vrácené z předchozího volání [CAtlMap::GetNextAssoc](#getnextassoc) nebo [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Návratová hodnota

Vrací ukazatel na další dvojici klíč/hodnota prvků uložených v objektu map. *Pos* pozice čítače je aktualizována po každém volání. Pokud je načtený element poslední v objektu map *pos* nastaven na hodnotu NULL.

##  <a name="getnextassoc"></a>  CAtlMap::GetNextAssoc

Získá další prvek pro iterace.

```
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>Parametry

*pos*<br/>
Čítač pozice vrácené z předchozího volání [CAtlMap::GetNextAssoc](#getnextassoc) nebo [CAtlMap::GetStartPosition](#getstartposition).

*key*<br/>
Parametr šablony určující typ klíče na mapě.

*value*<br/>
Parametr šablony určující typ hodnoty na mapě.

### <a name="remarks"></a>Poznámky

*Pos* pozice čítače je aktualizována po každém volání. Pokud je načtený element poslední v objektu map *pos* nastaven na hodnotu NULL.

##  <a name="getnextkey"></a>  CAtlMap::GetNextKey

Voláním této metody lze načíst další klíč z `CAtlMap` objektu.

```
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parametry

*pos*<br/>
Čítač pozice vrácené z předchozího volání [CAtlMap::GetNextAssoc](#getnextassoc) nebo [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na další klíče v objektu map.

### <a name="remarks"></a>Poznámky

Aktualizuje aktuální pozice čítače, *pos*. Pokud nejsou žádné další položky na mapě, čítač pozice je nastaven na hodnotu NULL.

##  <a name="getnextvalue"></a>  CAtlMap::GetNextValue

Volejte tuto metodu za účelem získání další hodnoty z `CAtlMap` objektu.

```
V& GetNextValue(POSITION& pos) throw();
const V& GetNextValue(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parametry

*pos*<br/>
Čítač pozice vrácené z předchozího volání [CAtlMap::GetNextAssoc](#getnextassoc) nebo [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na nejbližší hodnotu v objektu map.

### <a name="remarks"></a>Poznámky

Aktualizuje aktuální pozice čítače, *pos*. Pokud nejsou žádné další položky na mapě, čítač pozice je nastaven na hodnotu NULL.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlMap::CAtlMap](#catlmap).

##  <a name="getstartposition"></a>  CAtlMap::GetStartPosition

Volejte tuto metodu za účelem spuštění iterace mapy.

```
POSITION GetStartPosition() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí že počáteční pozici nebo hodnota NULL, je vrácena, pokud mapa je prázdný.

### <a name="remarks"></a>Poznámky

Volání tuto metodu za účelem spuštění iterace mapování tak, že vrací POZICI hodnota, která mohou být předány `GetNextAssoc` metody.

> [!NOTE]
>  Iterace sekvence není předvídatelné

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlMap::CAtlMap](#catlmap).

##  <a name="getvalueat"></a>  CAtlMap::GetValueAt

Volejte tuto metodu za účelem načtení hodnoty uložené na dané pozici v `CAtlMap` objektu.

```
V& GetValueAt(POSITION pos) throw();
const V& GetValueAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parametry

*pos*<br/>
Čítač pozice vrácené z předchozího volání [CAtlMap::GetNextAssoc](#getnextassoc) nebo [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na hodnotu uloženou v dané pozici v `CAtlMap` objektu.

##  <a name="inithashtable"></a>  CAtlMap::InitHashTable

Volejte tuto metodu za účelem inicializace zatřiďovací tabulku.

```
bool InitHashTable(
    UINT nBins,
    bool bAllocNow = true);
```

### <a name="parameters"></a>Parametry

*nBins*<br/>
Počet přihrádek používá zatřiďovací tabulku. Zobrazit [CAtlMap::CAtlMap](#catlmap) vysvětlení.

*bAllocNow*<br/>
Příznak uvedení, když by měla být paměť přidělena.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE na úspěšné inicializaci, při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

`InitHashTable` musí být volána před všechny prvky jsou uloženy v zatřiďovací tabulce.  Pokud tato metoda není explicitně volána, bude zavolána automaticky při prvním prvek přidána pomocí počet intervalů, které jsou určené `CAtlMap` konstruktoru.  V opačném případě mapy se inicializuje pomocí nové počet intervalů, které jsou určené *nBins* parametru.

Pokud *bAllocNow* parametr má hodnotu false, nebude přiděleno paměti vyžadované zatřiďovací tabulky, dokud je nejprve nutné. To může být užitečné, pokud nejistoty. Pokud se použije na mapě.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlMap::CAtlMap](#catlmap).

##  <a name="isempty"></a>  CAtlMap::IsEmpty

Volejte tuto metodu za účelem testování pro objekt map prázdný.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud mapa je prázdný, FALSE v opačném případě.

##  <a name="kinargtype"></a>  CAtlMap::KINARGTYPE

Typ použitý klíč je předána jako vstupní argument.

```
typedef KTraits::INARGTYPE KINARGTYPE;
```

##  <a name="koutargtype"></a>  CAtlMap::KOUTARGTYPE

Typ použitý při klíč se vrátí jako výstup argument.

```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

##  <a name="lookup"></a>  CAtlMap::Lookup

Volejte tuto metodu za účelem vyhledání klíče nebo hodnoty `CAtlMap` objektu.

```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const;
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parametry

*key*<br/>
Určuje klíč, který identifikuje elementu, který chcete vyhledávat.

*value*<br/>
Proměnná, která přijímá hodnotu vyhledaných.

### <a name="return-value"></a>Návratová hodnota

První forma metoda vrátí hodnotu true, pokud je nalezen klíč, jinak hodnota false. Druhý a třetí formuláře vrátí ukazatel na [CPair](#cpair_class) které slouží jako pozici pro volání [CAtlMap::GetNext](#getnext) a tak dále.

### <a name="remarks"></a>Poznámky

`Lookup` Pokud chcete rychle najít elementu mapy, který obsahuje klíč, který přesně odpovídá dané parametr klíče používá algoritmus hash.

##  <a name="operator_at"></a>  CAtlMap::operator \[\]

Nahradí nebo přidá nový prvek do `CAtlMap`.

```
V& operator[](kinargtype key) throw();
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč elementu, který chcete přidat nebo nahradit.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na hodnotu přidruženou k danému klíči.

### <a name="example"></a>Příklad

Pokud klíč již existuje, se nahradí elementu. Pokud klíč neexistuje, je přidán nový prvek. Podívejte se na příklad pro [CAtlMap::CAtlMap](#catlmap).

##  <a name="rehash"></a>  CAtlMap::Rehash

Volejte tuto metodu za účelem rehash `CAtlMap` objektu.

```
void Rehash(UINT nBins = 0);
```

### <a name="parameters"></a>Parametry

*nBins*<br/>
Nový počet přihrádek používat v zatřiďovací tabulce. Zobrazit [CAtlMap::CAtlMap](#catlmap) vysvětlení.

### <a name="remarks"></a>Poznámky

Pokud *nBins* je 0, `CAtlMap` vypočítá přiměřené číslo na základě počtu prvků v mapě a nastavení optimální zatížení. Obvykle rehashing proces je automatické, avšak v tom případě [CAtlMap::DisableAutoRehash](#disableautorehash) byla volána, tato metoda provede nezbytné změny velikosti.

##  <a name="removeall"></a>  CAtlMap::RemoveAll

Voláním této metody lze odebrat všechny prvky z `CAtlMap` objektu.

```
void RemoveAll() throw();
```

### <a name="remarks"></a>Poznámky

Vymaže navýšení kapacity `CAtlMap` objektu, uvolňování paměti pro ukládání prvky.

##  <a name="removeatpos"></a>  CAtlMap::RemoveAtPos

Volejte tuto metodu za účelem odebrání elementu na dané pozici v `CAtlMap` objektu.

```
void RemoveAtPos(POSITION pos) throw();
```

### <a name="parameters"></a>Parametry

*pos*<br/>
Čítač pozice vrácené z předchozího volání [CAtlMap::GetNextAssoc](#getnextassoc) nebo [CAtlMap::GetStartPosition](#getstartposition).

### <a name="remarks"></a>Poznámky

Odebere dvojice klíč/hodnota, které jsou uložené na zadané pozici. Je uvolněna paměť pro ukládání elementu. Odkazuje na POZICI *pos* stává neplatným a při pozice všech elementů v objektu map zůstává v platnosti, ne tedy nutně dělají zachovat stejné pořadí.

##  <a name="removekey"></a>  CAtlMap::RemoveKey

Voláním této metody lze odebrat element z `CAtlMap` objekt daný klíč.

```
bool RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč odpovídající dvojice elementů chcete odebrat.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je klíč nalezen a odebrané, při neúspěchu hodnotu FALSE.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlMap::CAtlMap](#catlmap).

##  <a name="setat"></a>  CAtlMap::SetAt

Voláním této metody lze vložit páru prvek do objektu map.

```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Hodnotu klíče pro přidání do `CAtlMap` objektu.

*value*<br/>
Hodnota k přidání do `CAtlMap` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí pozici prvku dvojice klíč/hodnota v `CAtlMap` objektu.

### <a name="remarks"></a>Poznámky

`SetAt` nahradí existující prvek, pokud je nalezen odpovídající klíč. Pokud klíč není nalezen, vytvoří se nový pár klíč/hodnota.

##  <a name="setoptimalload"></a>  CAtlMap::SetOptimalLoad

Voláním této metody lze nastavit optimální zatížení `CAtlMap` objektu.

```
void SetOptimalLoad(
    float fOptimalLoad,
    float fLoThreshold,
    float fHiThreshold,
    bool bRehashNow = false);
```

### <a name="parameters"></a>Parametry

*fOptimalLoad*<br/>
Poměr optimální zatížení.

*fLoThreshold*<br/>
Nižší prahová hodnota pro poměr zatížení.

*fHiThreshold*<br/>
Horní prahová hodnota pro poměr zatížení.

*bRehashNow*<br/>
Příznak označující, jestli by měly být přepočítány zatřiďovací tabulku.

### <a name="remarks"></a>Poznámky

Tato metoda předefinuje hodnota optimální zatížení `CAtlMap` objektu. Zobrazit [CAtlMap::CAtlMap](#catlmap) diskuzi o různých parametrů. Pokud *bRehashNow* má hodnotu true a počet prvků, které je mimo minimální a maximální hodnoty, jsou přepočítána zatřiďovací tabulku.

##  <a name="setvalueat"></a>  CAtlMap::SetValueAt

Voláním této metody lze změnit hodnotu uloženou v dané pozici v `CAtlMap` objektu.

```
void SetValueAt(
    POSITION pos,
    VINARGTYPE value);
```

### <a name="parameters"></a>Parametry

*pos*<br/>
Čítač pozice vrácené z předchozího volání [CAtlMap::GetNextAssoc](#getnextassoc) nebo [CAtlMap::GetStartPosition](#getstartposition).

*value*<br/>
Hodnota k přidání do `CAtlMap` objektu.

### <a name="remarks"></a>Poznámky

Změní hodnotu prvek uložený na dané pozici v `CAtlMap` objektu.

##  <a name="vinargtype"></a>  CAtlMap::VINARGTYPE

Typ použitý jako vstupní argument je předána hodnota.

```
typedef VTraits::INARGTYPE VINARGTYPE;
```

##  <a name="voutargtype"></a>  CAtlMap::VOUTARGTYPE

Typ použitý při je hodnota předána jako argument výstup.

```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

##  <a name="m_key"></a>  CAtlMap::CPair::m_key

Datový člen ukládání klíčovým prvkem.

```
const K m_key;
```

### <a name="parameters"></a>Parametry

*K*<br/>
Typ klíče prvku.

##  <a name="m_value"></a>  CAtlMap::CPair::m_value

Datový člen ukládání prvku hodnoty.

```
V  m_value;
```

### <a name="parameters"></a>Parametry

*V*<br/>
Typ elementu hodnota.

## <a name="see-also"></a>Viz také:

[Výběr ukázky](../../visual-cpp-samples.md)<br/>
[Příklad UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
