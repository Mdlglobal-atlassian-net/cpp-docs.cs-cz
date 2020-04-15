---
title: Třída CAtlMap
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
ms.openlocfilehash: 8a89ca7f7dedcd386abdd41e7487f1b838260c83
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321444"
---
# <a name="catlmap-class"></a>Třída CAtlMap

Tato třída poskytuje metody pro vytváření a správu objektu mapy.

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
Typ klíčového prvku.

*V*<br/>
Typ prvku hodnoty.

*KTraity*<br/>
Kód používaný ke kopírování nebo přesunutí klíčových prvků. Další podrobnosti najdete v [části CElementTraits Class.](../../atl/reference/celementtraits-class.md)

*VTraits*<br/>
Kód používaný ke kopírování nebo přesouvání prvků hodnoty.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

|Name (Název)|Popis|
|----------|-----------------|
|[CAtlMap::KINARGTYPE](#kinargtype)|Typ použitý při předání klíče jako vstupní argument|
|[CAtlMap::KOUTARGTYPE](#koutargtype)|Typ použitý při vrácení klíče jako výstupního argumentu.|
|[CAtlMap::VINARGTYPE](#vinargtype)|Typ použitý při předání hodnoty jako vstupní argument.|
|[CAtlMap::VOUTARGTYPE](#voutargtype)|Typ použitý při předání hodnoty jako výstupní argument.|

### <a name="public-classes"></a>Veřejné třídy

|Name (Název)|Popis|
|----------|-----------------|
|[CAtlMap::Třída CPair](#cpair_class)|Třída obsahující klíčové a hodnotové prvky.|

### <a name="cpair-data-members"></a>CPair Data Members

|Name (Název)|Popis|
|----------|-----------------|
|[CPair::m_key](#m_key)|Datový člen ukládání klíčový prvek.|
|[CPair::m_value](#m_value)|Datový člen ukládání elementvalue.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CAtlMap::CAtlMap](#catlmap)|Konstruktor|
|[CAtlMap::~CAtlMap](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CAtlMap::AssertValid](#assertvalid)|Volání této metody způsobit ASSERT, `CAtlMap` pokud není platný.|
|[CAtlMap::DisableAutoRehash](#disableautorehash)|Volání této metody zakázat automatické předhasování objektu. `CAtlMap`|
|[CAtlMap::Povolitautorehash](#enableautorehash)|Volání této metody povolit automatické předhasování objektu. `CAtlMap`|
|[CAtlMap::GetAt](#getat)|Volání této metody vrátit prvek na zadanou pozici v mapě.|
|[CAtlMap::GetCount](#getcount)|Volání této metody načíst počet prvků v mapě.|
|[CAtlMap::GetHashTableSize](#gethashtablesize)|Volánítéto metody k určení počtu přihrádek v tabulce hash mapy.|
|[CAtlMap::GetKeyAt](#getkeyat)|Volání této metody načíst klíč uložený `CAtlMap` na dané pozici v objektu.|
|[CAtlMap::GetNext](#getnext)|Volání této metody získat ukazatel na další dvojici elementu uložené v objektu. `CAtlMap`|
|[CAtlMap::GetNextAssoc](#getnextassoc)|Získá další prvek pro iterace.|
|[CAtlMap::GetNextKey](#getnextkey)|Volání této metody načíst další `CAtlMap` klíč z objektu.|
|[CAtlMap::Hodnota GetNextValue](#getnextvalue)|Volání této metody získat další `CAtlMap` hodnotu z objektu.|
|[CAtlMap::GetStartPosition](#getstartposition)|Volání této metody ke spuštění iterace mapy.|
|[CAtlMap::GetValueAt](#getvalueat)|Volání této metody načíst hodnotu uloženou `CAtlMap` na dané pozici v objektu.|
|[CAtlMap::InitHashTable](#inithashtable)|Volání této metody k inicializaci tabulky hash.|
|[CAtlMap::IsEmpty](#isempty)|Volání této metody k testování objektu prázdné mapy.|
|[CAtlMap::Vyhledávání](#lookup)|Volání této metody vyhledat klíče nebo `CAtlMap` hodnoty v objektu.|
|[CAtlMap::Přehasit](#rehash)|Volání této metody přemístit `CAtlMap` objekt.|
|[CAtlMap::OdstranitVše](#removeall)|Volání této metody odebrat `CAtlMap` všechny prvky z objektu.|
|[CAtlMap::RemoveAtPos](#removeatpos)|Volání této metody odebrat prvek na `CAtlMap` dané pozici v objektu.|
|[CAtlMap::Odebrat klíč](#removekey)|Volání této metody odebrat `CAtlMap` prvek z objektu, daný klíč.|
|[CAtlMap::SetAt](#setat)|Volání této metody vložit pár elementů do mapy.|
|[CAtlMap::SetOptimalLoad](#setoptimalload)|Volání této metody nastavit optimální `CAtlMap` zatížení objektu.|
|[CAtlMap::SetValueAt](#setvalueat)|Volání této metody změnit hodnotu uloženou `CAtlMap` na dané pozici v objektu.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CAtlMap::operátor\[\]](catlmap-class.md#operator_at)|Nahradí nebo přidá nový prvek `CAtlMap`do .|

## <a name="remarks"></a>Poznámky

`CAtlMap`poskytuje podporu pro mapování pole libovolného daného typu, správa neuspořádané pole klíčových prvků a jejich přidružené hodnoty. Prvky (skládající se z klíče a hodnoty) jsou uloženy pomocí algoritmu hash, což umožňuje efektivně ukládat a načítat velké množství dat.

*Parametry KTraits* a *VTraits* jsou třídy vlastností, které obsahují jakýkoli doplňkový kód potřebný ke kopírování nebo přesouvání prvků.

Alternativu `CAtlMap` k nabízí třída [CRBMap.](../../atl/reference/crbmap-class.md) `CRBMap`také ukládá dvojice klíč/hodnota, ale vykazuje různé charakteristiky výkonu. Doba, která byla doba, která byla tázat `CRBMap` vložením položky, vyhledáním klíče nebo odstraněním klíče z objektu, je *příkazlog(n)*, kde *n* je počet prvků. Pro `CAtlMap`všechny tyto operace obvykle trvat konstantní čas, i když nejhorší scénáře mohou být pořadí *n*. Proto `CAtlMap` je v typickém případě rychlejší.

Další rozdíl `CRBMap` mezi `CAtlMap` a se projeví při itací prostřednictvím uložených prvků. V `CRBMap`a , prvky jsou navštíveny v seřazené pořadí. V `CAtlMap`a , prvky nejsou uspořádány a nelze odvodit žádné pořadí.

Když malý počet prvků, které mají být uloženy, zvažte použití [CSimpleMap](../../atl/reference/csimplemap-class.md) třídy místo.

Další informace naleznete v tématu [třídy kolekce klíčů ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

## <a name="catlmapassertvalid"></a><a name="assertvalid"></a>CAtlMap::AssertValid

Volání této metody způsobit ASSERT, `CAtlMap` pokud objekt není platný.

```
void AssertValid() const;
```

### <a name="remarks"></a>Poznámky

V sestavení ladění tato metoda způsobí ASSERT, `CAtlMap` pokud objekt není platný.

### <a name="example"></a>Příklad

Viz příklad pro [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmapcatlmap"></a><a name="catlmap"></a>CAtlMap::CAtlMap

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
Počet přihrádek poskytujících ukazatele na uložené prvky. Vysvětlení přihrádek naleznete dále v tématu poznámky.

*fOptimalLoad*<br/>
Optimální poměr zatížení.

*fLoThreshold*<br/>
Nižší prahová hodnota pro poměr zatížení.

*fHiThreshold*<br/>
Horní práh pro poměr zatížení.

*nBlockSize*<br/>
Velikost bloku.

### <a name="remarks"></a>Poznámky

`CAtlMap`odkazuje na všechny jeho uložené prvky nejprve vytvořením indexu pomocí algoritmu hash na klíč. Tento index odkazuje na "bin", který obsahuje ukazatel na uložené prvky. Pokud je přihrádka již používána, vytvoří se propojený seznam pro přístup k následujícím prvkům. Procházení seznamu je pomalejší než přímý přístup ke správnému prvku, a proto struktura mapy potřebuje vyvážit požadavky na úložiště oproti výkonu. Výchozí parametry byly vybrány tak, aby ve většině případů poskytly dobré výsledky.

Poměr vytížení je poměr počtu přihrádek k počtu prvků uložených v objektu mapy. Po přepočítání struktury mapy se hodnota *parametru fOptimalLoad* použije k výpočtu počtu požadovaných přihrádek. Tuto hodnotu lze změnit pomocí metody [CAtlMap::SetOptimalLoad.](#setoptimalload)

Parametr *fLoThreshold* je nižší hodnota, které může `CAtlMap` poměr zatížení dosáhnout, než přepočítá optimální velikost mapy.

Parametr *fHiThreshold* je horní hodnota, které může `CAtlMap` poměr zatížení dosáhnout, než objekt přepočítá optimální velikost mapy.

Tento proces přepočtu (označovaný jako předhasování) je ve výchozím nastavení povolen. Pokud chcete zakázat tento proces, možná při zadávání velké množství dat najednou, volejte [CAtlMap::DisableAutoRehash](#disableautorehash) metoda. Znovu jej aktivujte metodou [CAtlMap::EnableAutoRehash.](#enableautorehash)

Parametr *nBlockSize* je míra velikosti paměti přidělené při použití nového prvku. Větší velikosti bloků snižují volání rutiny přidělení paměti, ale používají více prostředků.

Před uložením všech dat je nutné inicializovat tabulku hash voláním [CAtlMap::InitHashTable](#inithashtable).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#72](../../atl/codesnippet/cpp/catlmap-class_1.cpp)]

## <a name="catlmapcatlmap"></a><a name="dtor"></a>CAtlMap::~CAtlMap

Destruktor.

```
~CAtlMap() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené zdroje.

## <a name="catlmapcpair-class"></a><a name="cpair_class"></a>CAtlMap::Třída CPair

Třída obsahující klíčové a hodnotové prvky.

```
class CPair : public __POSITION
```

### <a name="remarks"></a>Poznámky

Tato třída se používá metody [CAtlMap::GetNext](#getnext) a [CAtlMap::Lookup](#lookup) pro přístup ke klíči a hodnotě prvků uložených ve struktuře mapování.

## <a name="catlmapdisableautorehash"></a><a name="disableautorehash"></a>CAtlMap::DisableAutoRehash

Volání této metody zakázat automatické předhasování objektu. `CAtlMap`

```
void DisableAutoRehash() throw();
```

### <a name="remarks"></a>Poznámky

Pokud je povoleno automatické předělávka (což je ve výchozím nastavení), počet přihrádek v tabulce hash bude automaticky přepočítán, pokud hodnota načtení (poměr počtu přihrádek k počtu prvků uložených v poli) překročí maximální nebo minimální hodnoty zadané v době, kdy byla mapa vytvořena.

`DisableAutoRehash`je nejužitečnější, když bude na mapu přidáno velké množství prvků najednou. Namísto spuštění procesu předhasování pokaždé, když jsou překročeny limity, `DisableAutoRehash`je efektivnější volat , přidat prvky a nakonec volat [CAtlMap::EnableAutoRehash](#enableautorehash).

## <a name="catlmapenableautorehash"></a><a name="enableautorehash"></a>CAtlMap::Povolitautorehash

Volání této metody povolit automatické předhasování objektu. `CAtlMap`

```
void EnableAutoRehash() throw();
```

### <a name="remarks"></a>Poznámky

Pokud je povoleno automatické předělávka (což je ve výchozím nastavení), počet přihrádek v tabulce hash bude automaticky přepočítán, pokud hodnota načtení (poměr počtu přihrádek k počtu prvků uložených v poli) překročí maximální nebo minimální hodnoty zadané v době vytvoření mapy.

`EnableAutoRefresh`se nejčastěji používá po volání [CAtlMap::DisableAutoRehash](#disableautorehash).

## <a name="catlmapgetat"></a><a name="getat"></a>CAtlMap::GetAt

Volání této metody vrátit prvek na zadanou pozici v mapě.

```
void GetAt(
    POSITION pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;

CPair* GetAt(POSITION& pos) throw();
```

### <a name="parameters"></a>Parametry

*Pos*<br/>
Čítač pozice vrácený předchozím voláním [CAtlMap::GetNextAssoc](#getnextassoc) nebo [CAtlMap::GetStartPosition](#getstartposition).

*key*<br/>
Parametr šablony určující typ klíče mapy.

*Hodnotu*<br/>
Parametr šablony určující typ hodnoty mapy.

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na aktuální dvojici prvků klíč/hodnota uložená v mapě.

### <a name="remarks"></a>Poznámky

V sestaveních ladění dojde k chybě kontrolního výrazu, pokud *se pos* rovná hodnotě NULL.

## <a name="catlmapgetcount"></a><a name="getcount"></a>CAtlMap::GetCount

Volání této metody načíst počet prvků v mapě.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet prvků v objektu mapy. Jeden prvek je pár klíč/hodnota.

### <a name="example"></a>Příklad

Viz příklad pro [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmapgethashtablesize"></a><a name="gethashtablesize"></a>CAtlMap::GetHashTableSize

Volánítéto metody k určení počtu přihrádek v tabulce hash mapy.

```
UINT GetHashTableSize() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet přihrádek v tabulce hash. Vysvětlení naleznete [v tématu CAtlMap::CAtlMap.](#catlmap)

## <a name="catlmapgetkeyat"></a><a name="getkeyat"></a>CAtlMap::GetKeyAt

Volání této metody načíst klíč uložený `CAtlMap` na dané pozici v objektu.

```
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parametry

*Pos*<br/>
Čítač pozice vrácený předchozím voláním [CAtlMap::GetNextAssoc](#getnextassoc) nebo [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na klíč uložený na `CAtlMap` dané pozici v objektu.

### <a name="example"></a>Příklad

Viz příklad pro [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmapgetnext"></a><a name="getnext"></a>CAtlMap::GetNext

Volání této metody získat ukazatel na další dvojici elementu uložené v objektu. `CAtlMap`

```
CPair* GetNext(POSITION& pos) throw();
const CPair* GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parametry

*Pos*<br/>
Čítač pozice vrácený předchozím voláním [CAtlMap::GetNextAssoc](#getnextassoc) nebo [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na další dvojici prvků klíč/hodnota uložená v mapě. Čítač pozice *pos* je aktualizován po každém volání. Pokud načtený prvek je poslední v mapě, *pos* je nastavena na HODNOTU NULL.

## <a name="catlmapgetnextassoc"></a><a name="getnextassoc"></a>CAtlMap::GetNextAssoc

Získá další prvek pro iterace.

```
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>Parametry

*Pos*<br/>
Čítač pozice vrácený předchozím voláním [CAtlMap::GetNextAssoc](#getnextassoc) nebo [CAtlMap::GetStartPosition](#getstartposition).

*key*<br/>
Parametr šablony určující typ klíče mapy.

*Hodnotu*<br/>
Parametr šablony určující typ hodnoty mapy.

### <a name="remarks"></a>Poznámky

Čítač pozice *pos* je aktualizován po každém volání. Pokud načtený prvek je poslední v mapě, *pos* je nastavena na HODNOTU NULL.

## <a name="catlmapgetnextkey"></a><a name="getnextkey"></a>CAtlMap::GetNextKey

Volání této metody načíst další `CAtlMap` klíč z objektu.

```
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parametry

*Pos*<br/>
Čítač pozice vrácený předchozím voláním [CAtlMap::GetNextAssoc](#getnextassoc) nebo [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na další klíč v mapě.

### <a name="remarks"></a>Poznámky

Aktualizuje aktuální čítač *pozice, pos*. Pokud nejsou žádné další položky v mapě, čítač pozice je nastavena na hodnotu NULL.

## <a name="catlmapgetnextvalue"></a><a name="getnextvalue"></a>CAtlMap::Hodnota GetNextValue

Volání této metody získat další `CAtlMap` hodnotu z objektu.

```
V& GetNextValue(POSITION& pos) throw();
const V& GetNextValue(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parametry

*Pos*<br/>
Čítač pozice vrácený předchozím voláním [CAtlMap::GetNextAssoc](#getnextassoc) nebo [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na další hodnotu v mapě.

### <a name="remarks"></a>Poznámky

Aktualizuje aktuální čítač *pozice, pos*. Pokud nejsou žádné další položky v mapě, čítač pozice je nastavena na hodnotu NULL.

### <a name="example"></a>Příklad

Viz příklad pro [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmapgetstartposition"></a><a name="getstartposition"></a>CAtlMap::GetStartPosition

Volání této metody ke spuštění iterace mapy.

```
POSITION GetStartPosition() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počáteční pozici nebo null je vrácena, pokud je mapa prázdná.

### <a name="remarks"></a>Poznámky

Volání této metody spustit iteraci mapy vrácením position hodnotu, která může být předána metodě. `GetNextAssoc`

> [!NOTE]
> Pořadí iterace není předvídatelné.

### <a name="example"></a>Příklad

Viz příklad pro [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmapgetvalueat"></a><a name="getvalueat"></a>CAtlMap::GetValueAt

Volání této metody načíst hodnotu uloženou `CAtlMap` na dané pozici v objektu.

```
V& GetValueAt(POSITION pos) throw();
const V& GetValueAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parametry

*Pos*<br/>
Čítač pozice vrácený předchozím voláním [CAtlMap::GetNextAssoc](#getnextassoc) nebo [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na hodnotu uloženou na `CAtlMap` dané pozici v objektu.

## <a name="catlmapinithashtable"></a><a name="inithashtable"></a>CAtlMap::InitHashTable

Volání této metody k inicializaci tabulky hash.

```
bool InitHashTable(
    UINT nBins,
    bool bAllocNow = true);
```

### <a name="parameters"></a>Parametry

*nBins*<br/>
Počet přihrádek používaných v tabulce hash. Vysvětlení naleznete [v tématu CAtlMap::CAtlMap.](#catlmap)

*bAllocNyní*<br/>
Označení příznaku, kdy by měla být přidělena paměť.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěšné inicializaci, nepravda při selhání.

### <a name="remarks"></a>Poznámky

`InitHashTable`musí být volána před uložením všech prvků do tabulky hash.  Pokud tato metoda není volána explicitně, bude volána automaticky při prvním přidání `CAtlMap` prvku pomocí výpočtu přihrádky určeného konstruktorem.  V opačném případě bude mapa inicializována pomocí nového počtu přihrádek určeného parametrem *nBins.*

Pokud je parametr *bAllocNow* false, paměť vyžadovaná tabulkou hash nebude přidělena, dokud nebude nejprve požadována. To může být užitečné, pokud není jisté, zda bude mapa použita.

### <a name="example"></a>Příklad

Viz příklad pro [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmapisempty"></a><a name="isempty"></a>CAtlMap::IsEmpty

Volání této metody k testování objektu prázdné mapy.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je mapa prázdná, jinak NEPRAVDA.

## <a name="catlmapkinargtype"></a><a name="kinargtype"></a>CAtlMap::KINARGTYPE

Typ použitý při předání klíče jako vstupní argument.

```
typedef KTraits::INARGTYPE KINARGTYPE;
```

## <a name="catlmapkoutargtype"></a><a name="koutargtype"></a>CAtlMap::KOUTARGTYPE

Typ použitý při vrácení klíče jako výstupního argumentu.

```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

## <a name="catlmaplookup"></a><a name="lookup"></a>CAtlMap::Vyhledávání

Volání této metody vyhledat klíče nebo `CAtlMap` hodnoty v objektu.

```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const;
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parametry

*key*<br/>
Určuje klíč, který identifikuje prvek, který má být vyhledán.

*Hodnotu*<br/>
Proměnná, která obdrží hodnotu vyhledat.

### <a name="return-value"></a>Návratová hodnota

První forma metody vrátí true, pokud je nalezen klíč, jinak false. Druhý a třetí formulář vrátit ukazatel [CPair,](#cpair_class) který lze použít jako pozici pro volání [CAtlMap::GetNext](#getnext) a tak dále.

### <a name="remarks"></a>Poznámky

`Lookup`používá algoritmus hash rychle najít prvek mapy obsahující klíč, který přesně odpovídá danému klíčovému parametru.

## <a name="catlmapoperator-"></a><a name="operator_at"></a>CAtlMap::operátor\[\]

Nahradí nebo přidá nový prvek `CAtlMap`do .

```
V& operator[](kinargtype key) throw();
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč prvku přidat nebo nahradit.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na hodnotu přidruženou k danému klíči.

### <a name="example"></a>Příklad

Pokud klíč již existuje, prvek je nahrazen. Pokud klíč neexistuje, je přidán nový prvek. Viz příklad pro [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmaprehash"></a><a name="rehash"></a>CAtlMap::Přehasit

Volání této metody přemístit `CAtlMap` objekt.

```
void Rehash(UINT nBins = 0);
```

### <a name="parameters"></a>Parametry

*nBins*<br/>
Nový počet přihrádek, které mají být v tabulce hash používány. Vysvětlení naleznete [v tématu CAtlMap::CAtlMap.](#catlmap)

### <a name="remarks"></a>Poznámky

Pokud *nBins* je `CAtlMap` 0, vypočítá přiměřené číslo na základě počtu prvků v mapě a optimální nastavení zatížení. Normálně proces předhasování je automatické, ale pokud [CAtlMap::DisableAutoRehash](#disableautorehash) byla volána, tato metoda provede potřebnou velikost.

## <a name="catlmapremoveall"></a><a name="removeall"></a>CAtlMap::OdstranitVše

Volání této metody odebrat `CAtlMap` všechny prvky z objektu.

```
void RemoveAll() throw();
```

### <a name="remarks"></a>Poznámky

Vymaže `CAtlMap` objekt, uvolnění paměti používané k uložení prvků.

## <a name="catlmapremoveatpos"></a><a name="removeatpos"></a>CAtlMap::RemoveAtPos

Volání této metody odebrat prvek na `CAtlMap` dané pozici v objektu.

```
void RemoveAtPos(POSITION pos) throw();
```

### <a name="parameters"></a>Parametry

*Pos*<br/>
Čítač pozice vrácený předchozím voláním [CAtlMap::GetNextAssoc](#getnextassoc) nebo [CAtlMap::GetStartPosition](#getstartposition).

### <a name="remarks"></a>Poznámky

Odebere dvojici klíč/hodnota uloženou na zadané pozici. Paměť použitá k uložení prvku je uvolněna. POZICE odkazovaná *pos* se stane neplatnou a zatímco POZICE jiných prvků v mapě zůstává platná, nemusí nutně zachovat stejné pořadí.

## <a name="catlmapremovekey"></a><a name="removekey"></a>CAtlMap::Odebrat klíč

Volání této metody odebrat `CAtlMap` prvek z objektu, daný klíč.

```
bool RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč odpovídající dvojici prvků, kterou chcete odebrat.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je klíč nalezen a odebrán, nepravda při selhání.

### <a name="example"></a>Příklad

Viz příklad pro [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmapsetat"></a><a name="setat"></a>CAtlMap::SetAt

Volání této metody vložit pár elementů do mapy.

```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Hodnota klíče, kterou `CAtlMap` chcete přidat k objektu.

*Hodnotu*<br/>
Hodnota, kterou chcete `CAtlMap` přidat k objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí pozici páru prvků klíč/hodnota `CAtlMap` v objektu.

### <a name="remarks"></a>Poznámky

`SetAt`nahradí existující prvek, pokud je nalezen odpovídající klíč. Pokud klíč není nalezen, vytvoří se nový pár klíč/hodnota.

## <a name="catlmapsetoptimalload"></a><a name="setoptimalload"></a>CAtlMap::SetOptimalLoad

Volání této metody nastavit optimální `CAtlMap` zatížení objektu.

```
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
Nižší prahová hodnota pro poměr zatížení.

*fHiThreshold*<br/>
Horní práh pro poměr zatížení.

*bRehashNow*<br/>
Příznak označující, zda má být tabulka hash přepočítána.

### <a name="remarks"></a>Poznámky

Tato metoda předefinuje optimální hodnotu `CAtlMap` zatížení pro objekt. Viz [CAtlMap::CAtlMap](#catlmap) pro diskusi o různých parametrech. Pokud *bRehashNow* je true a počet prvků je mimo minimální a maximální hodnoty, je přepočítána tabulka hash.

## <a name="catlmapsetvalueat"></a><a name="setvalueat"></a>CAtlMap::SetValueAt

Volání této metody změnit hodnotu uloženou `CAtlMap` na dané pozici v objektu.

```
void SetValueAt(
    POSITION pos,
    VINARGTYPE value);
```

### <a name="parameters"></a>Parametry

*Pos*<br/>
Čítač pozice vrácený předchozím voláním [CAtlMap::GetNextAssoc](#getnextassoc) nebo [CAtlMap::GetStartPosition](#getstartposition).

*Hodnotu*<br/>
Hodnota, kterou chcete `CAtlMap` přidat k objektu.

### <a name="remarks"></a>Poznámky

Změní prvek hodnoty uložený v `CAtlMap` dané pozici v objektu.

## <a name="catlmapvinargtype"></a><a name="vinargtype"></a>CAtlMap::VINARGTYPE

Typ použitý při předání hodnoty jako vstupní argument.

```
typedef VTraits::INARGTYPE VINARGTYPE;
```

## <a name="catlmapvoutargtype"></a><a name="voutargtype"></a>CAtlMap::VOUTARGTYPE

Typ použitý při předání hodnoty jako výstupní argument.

```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

## <a name="catlmapcpairm_key"></a><a name="m_key"></a>CAtlMap::CPair::m_key

Datový člen ukládání klíčový prvek.

```
const K m_key;
```

### <a name="parameters"></a>Parametry

*K*<br/>
Typ klíčového prvku.

## <a name="catlmapcpairm_value"></a><a name="m_value"></a>CAtlMap::CPair::m_value

Datový člen ukládání elementvalue.

```
V  m_value;
```

### <a name="parameters"></a>Parametry

*V*<br/>
Typ prvku hodnoty.

## <a name="see-also"></a>Viz také

[Vzorek výběru](../../overview/visual-cpp-samples.md)<br/>
[Ukázka updatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
