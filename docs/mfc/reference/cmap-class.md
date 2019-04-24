---
title: Cmap – třída
ms.date: 11/04/2016
f1_keywords:
- CMap
- AFXTEMPL/CMap
- AFXTEMPL/CMap::CPair
- AFXTEMPL/CMap::CMap
- AFXTEMPL/CMap::GetCount
- AFXTEMPL/CMap::GetHashTableSize
- AFXTEMPL/CMap::GetNextAssoc
- AFXTEMPL/CMap::GetSize
- AFXTEMPL/CMap::GetStartPosition
- AFXTEMPL/CMap::InitHashTable
- AFXTEMPL/CMap::IsEmpty
- AFXTEMPL/CMap::Lookup
- AFXTEMPL/CMap::PGetFirstAssoc
- AFXTEMPL/CMap::PGetNextAssoc
- AFXTEMPL/CMap::PLookup
- AFXTEMPL/CMap::RemoveAll
- AFXTEMPL/CMap::RemoveKey
- AFXTEMPL/CMap::SetAt
helpviewer_keywords:
- CMap [MFC], CPair
- CMap [MFC], CMap
- CMap [MFC], GetCount
- CMap [MFC], GetHashTableSize
- CMap [MFC], GetNextAssoc
- CMap [MFC], GetSize
- CMap [MFC], GetStartPosition
- CMap [MFC], InitHashTable
- CMap [MFC], IsEmpty
- CMap [MFC], Lookup
- CMap [MFC], PGetFirstAssoc
- CMap [MFC], PGetNextAssoc
- CMap [MFC], PLookup
- CMap [MFC], RemoveAll
- CMap [MFC], RemoveKey
- CMap [MFC], SetAt
ms.assetid: 640a45ab-0993-4def-97ec-42cc78eb10b9
ms.openlocfilehash: 58f9efb19988be8487ec87ce0c63d90ee1a97911
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62296576"
---
# <a name="cmap-class"></a>Cmap – třída

Třída kolekce slovníku, která mapuje jedinečné klíče na hodnoty.

## <a name="syntax"></a>Syntaxe

```
template<class KEY, class ARG_KEY, class VALUE, class ARG_VALUE>class CMap : public CObject
```

#### <a name="parameters"></a>Parametry

*KEY*<br/>
Třída objektu se používá jako klíč do mapy.

*ARG_KEY*<br/>
Datový typ používaný pro *klíč* argumenty; obvykle odkaz na *klíč*.

*HODNOTA*<br/>
Třída objekt uložený v objektu map.

*ARG_VALUE*<br/>
Datový typ používaný pro *hodnotu* argumenty; obvykle odkaz na *hodnota*.

## <a name="members"></a>Členové

### <a name="public-structures"></a>Veřejné struktury

|Název|Popis|
|----------|-----------------|
|[CMap::CPair](#cpair)|Vnořené struktury obsahující hodnotu klíče a hodnoty přidruženého objektu.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMap::CMap](#cmap)|Sestaví kolekci, který mapuje klíče na hodnoty.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMap::GetCount](#getcount)|Vrátí počet prvků, které na této mapě.|
|[CMap::GetHashTableSize](#gethashtablesize)|Vrátí počet prvků v zatřiďovací tabulce.|
|[CMap::GetNextAssoc](#getnextassoc)|Získá další prvek pro iterace.|
|[CMap::GetSize](#getsize)|Vrátí počet prvků, které na této mapě.|
|[CMap::GetStartPosition](#getstartposition)|Vrátí pozici prvního prvku.|
|[CMap::InitHashTable](#inithashtable)|Inicializuje zatřiďovací tabulky a určuje jeho velikost.|
|[CMap::IsEmpty](#isempty)|Testy pro podmínku prázdný mapy (žádné elementy).|
|[CMap::Lookup](#lookup)|Vyhledá hodnotu namapována na daný klíč.|
|[CMap::PGetFirstAssoc](#pgetfirstassoc)|Vrací ukazatel na první prvek.|
|[CMap::PGetNextAssoc](#pgetnextassoc)|Získá ukazatel na další prvek pro iterace.|
|[CMap::PLookup](#plookup)|Vrací ukazatel na klíč, jejíž hodnota odpovídá zadané hodnotě.|
|[CMap::RemoveAll](#removeall)|Odebere všechny prvky z této mapy.|
|[CMap::RemoveKey](#removekey)|Odebere element určený klíč.|
|[CMap::SetAt](#setat)|Vloží prvek do mapy; nahradí existující prvek, pokud je nalezen odpovídající klíč.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CMap::operator \[ \]](#operator_at)|Vloží prvek do mapy – operátor nahrazení pro `SetAt`.|

## <a name="remarks"></a>Poznámky

Po vložení pár klíč hodnota (element) do objektu map lze efektivně načíst nebo odstranit pár pomocí klíče k němu přistupovat. Můžete také iterovat přes všechny prvky v objektu map.

Proměnné typu umístění se používá pro alternativní přístup k položkám. Můžete na POZICI "pamatovat" záznam a k iteraci v rámci mapy. Si možná myslíte, že je sekvenční podle hodnoty klíče; této iterace není. Je neurčité, sekvence načtených prvků.

Určité členské funkce třídy volání globální pomocné funkce, které je nutné upravit pro většina použití `CMap` třídy. Zobrazit [pomocné rutiny třídy kolekce](../../mfc/reference/collection-class-helpers.md) v části makra a globální prvky **odkaz knihovny MFC**.

`CMap` přepíše [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) na podporu serializace a výpis z jeho prvků. Pokud je mapy uložen do archivu pomocí `Serialize`, pak serializován každý prvek mapy. Výchozí implementace `SerializeElements` pomocnou funkci neodpovídá bitové operace zápisu. Pro informace o serializaci položek kolekce ukazatel odvozen od `CObject` nebo jiné typy definované uživatelem, najdete v článku [jak: Typově bezpečné kolekce](../../mfc/how-to-make-a-type-safe-collection.md).

Pokud potřebujete diagnostiky s výpisem paměti jednotlivých prvků v objektu map (klíče a hodnoty), nastavte na 1 nebo větší hloubky kontextu s výpisem paměti.

Když `CMap` odstranění objektu nebo při jeho prvky jsou odebrány, odeberou se klíče a hodnoty.

Odvození třídy map se podobá seznamu odvození. Přečtěte si článek [kolekce](../../mfc/collections.md) ilustraci odvození třídy seznamu zvláštní účely.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CMap`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxtempl.h

##  <a name="cmap"></a>  CMap::CMap

Vytvoří prázdné mapování.

```
CMap(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Parametry

*nBlockSize*<br/>
Určuje členitosti přidělení paměti pro rozšíření na mapě.

### <a name="remarks"></a>Poznámky

S růstem mapy je paměť přidělena v jednotkách, které *nBlockSize* položky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#56](../../mfc/codesnippet/cpp/cmap-class_1.cpp)]

##  <a name="cpair"></a>  CMap::CPair

Obsahuje hodnotu klíče a hodnoty přidruženého objektu.

### <a name="remarks"></a>Poznámky

Toto je vnořené struktury v rámci třídy [CMap](../../mfc/reference/cmap-class.md).

Struktura se skládá ze dvou polí:

- `key` Skutečná hodnota typ klíče.

- `value` Hodnota přidruženého objektu.

Se používá k ukládání vrácené hodnoty z [CMap::PLookup](#plookup), [CMap::PGetFirstAssoc](#pgetfirstassoc), a [CMap::PGetNextAssoc](#pgetnextassoc).

### <a name="example"></a>Příklad

Příklad použití, podívejte se na příklad pro [CMap::PLookup](#plookup).

##  <a name="getcount"></a>  CMap::GetCount

Získá počet elementů v objektu map.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CMap::Lookup](#lookup).

##  <a name="gethashtablesize"></a>  CMap::GetHashTableSize

Určuje počet prvků v zatřiďovací tabulce pro mapu.

```
UINT GetHashTableSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků v zatřiďovací tabulce.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#57](../../mfc/codesnippet/cpp/cmap-class_2.cpp)]

##  <a name="getnextassoc"></a>  CMap::GetNextAssoc

Načte prvek mapy v `rNextPosition`, pak aktualizuje `rNextPosition` odkazovat na další prvek v objektu map.

```
void GetNextAssoc(
    POSITION& rNextPosition,
    KEY& rKey,
    VALUE& rValue) const;
```

### <a name="parameters"></a>Parametry

*rNextPosition*<br/>
Určuje referenci na POZICI hodnotu vrácenou předchozím `GetNextAssoc` nebo `GetStartPosition` volání.

*KEY*<br/>
Parametr šablony určující typ klíče na mapě.

*rKey*<br/>
Určuje vrácené klíč načtený elementu.

*HODNOTA*<br/>
Parametr šablony určující typ hodnoty na mapě.

*rValue*<br/>
Určuje, vrácená hodnota elementu načtený.

### <a name="remarks"></a>Poznámky

Tato funkce je zvláště užitečná pro procházení všech prvků v objektu map. Všimněte si, že sekvence pozice není nutně stejné jako pořadí klíč-hodnota.

Pokud je načtený element poslední v objektu map, pak nová hodnota *rNextPosition* nastaven na hodnotu NULL.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CMap::SetAt](#setat).

##  <a name="getsize"></a>  CMap::GetSize

Vrátí počet prvků na mapě.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v objektu map.

### <a name="remarks"></a>Poznámky

Voláním této metody lze načíst počet prvků v objektu map.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]

##  <a name="getstartposition"></a>  CMap::GetStartPosition

Spuštění iterace mapování tak, že vrací hodnotu POZICI, která mohou být předány `GetNextAssoc` volání.

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Návratová hodnota

POZICE určující počáteční pozice pro iterace v mapě. nebo hodnota NULL, pokud mapa je prázdný.

### <a name="remarks"></a>Poznámky

Iterace sekvence není předvídatelný; "první prvek v objektu map", proto nemá žádný speciální význam.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CMap::SetAt](#setat).

##  <a name="inithashtable"></a>  CMap::InitHashTable

Inicializuje zatřiďovací tabulku.

```
void InitHashTable(UINT hashSize, BOOL  bAllocNow = TRUE);
```

### <a name="parameters"></a>Parametry

*hashSize*<br/>
Počet položek v zatřiďovací tabulce.

*bAllocNow*<br/>
Při hodnotě TRUE se přiděluje zatřiďovací tabulku při inicializaci; jinak v tabulce je přidělena v případě potřeby.

### <a name="remarks"></a>Poznámky

Pro zajištění nejlepšího výkonu by měl být velikost tabulky hash Prvočíslo. Chcete-li minimalizovat kolize, velikost musí mít zhruba 20 procent větší než největší očekávané datové sady.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CMap::Lookup](#lookup).

##  <a name="isempty"></a>  CMap::IsEmpty

Určuje, zda na mapě je prázdný.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud neobsahuje žádné elementy; toto mapování jinak 0.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CMap::RemoveAll](#removeall).

##  <a name="lookup"></a>  CMap::Lookup

Vyhledá hodnotu namapována na daný klíč.

```
BOOL Lookup(ARG_KEY key, VALUE& rValue) const;
```

### <a name="parameters"></a>Parametry

*ARG_KEY*<br/>
Parametr šablony určující typ *klíč* hodnotu.

*key*<br/>
Určuje klíč, který identifikuje elementu, který chcete vyhledávat.

*HODNOTA*<br/>
Určuje typ hodnoty, které chcete vyhledávat.

*rValue*<br/>
Přijímá hodnotu vyhledaných.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud element nebyl nalezen; jinak 0.

### <a name="remarks"></a>Poznámky

`Lookup` používá algoritmus hash a rychle najít prvek mapy s klíčem, který přesně odpovídá danému klíči.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]

##  <a name="operator_at"></a>  [] Č. CMap::operator

Pohodlné náhradou za `SetAt` členskou funkci.

```
VALUE& operator[](arg_key key);
```

### <a name="parameters"></a>Parametry

*HODNOTA*<br/>
Parametr šablony určující typ hodnoty mapování.

*ARG_KEY*<br/>
Parametr šablony určující typ hodnoty klíče.

*key*<br/>
Klíč používaný k načtení hodnoty z mapy.

### <a name="remarks"></a>Poznámky

Proto jej lze použít pouze na levé straně příkazu přiřazení (l hodnota). Pokud neexistuje žádné mapování element se zadaným klíčem, se vytvoří nový prvek.

Ekvivalentní pro tento operátor není žádný "pravému" (r), protože je možné, že klíče nemusí být nalezen v objektu map. Použití `Lookup` členskou funkci pro prvek načítání.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CMap::Lookup](#lookup).

##  <a name="pgetfirstassoc"></a>  CMap::PGetFirstAssoc

Vrátí první položku v objektu map.

```
const CPair* PGetFirstAssoc() const;
CPair* PGetFirstAssoc();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na první položku v mapě. Zobrazit [CMap::CPair](#cpair). Pokud mapa obsahuje žádné položky, hodnota je NULL.

### <a name="remarks"></a>Poznámky

Voláním této funkce vrací ukazatel první prvek v objektu map.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#59](../../mfc/codesnippet/cpp/cmap-class_4.cpp)]

##  <a name="pgetnextassoc"></a>  CMap::PGetNextAssoc

Načte prvek mapy, na které odkazuje *pAssocRec*.

```
const CPair *PGetNextAssoc(const CPair* pAssocRet) const;

CPair *PGetNextAssoc(const CPair* pAssocRet);
```

### <a name="parameters"></a>Parametry

*pAssocRet*<br/>
Odkazuje na položku mapování vrácený předchozím [PGetNextAssoc](#pgetnextassoc) nebo [CMap::PGetFirstAssoc](#pgetfirstassoc) volání.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na další položky na mapě; Zobrazit [CMap::CPair](#cpair). Pokud prvek je poslední v objektu map, hodnota je NULL.

### <a name="remarks"></a>Poznámky

Voláním této metody lze iterovat přes všechny prvky v objektu map. Načíst první prvek voláním `PGetFirstAssoc` a potom iteraci v rámci mapy při následných voláních na `PGetNextAssoc`.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CMap::PGetFirstAssoc](#pgetfirstassoc).

##  <a name="plookup"></a>  CMap::PLookup

Najde hodnotu namapována na daný klíč.

```
const CPair* PLookup(ARG_KEY key) const;
CPair* PLookup(ARG_KEY key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč elementu, který chcete vyhledávat.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na strukturu klíče; Zobrazit [CMap::CPair](#cpair). Pokud není nalezena žádná shoda, `CMap::PLookup` vrátí hodnotu NULL.

### <a name="remarks"></a>Poznámky

Volejte tuto metodu za účelem vyhledání prvek mapy s klíčem, který přesně odpovídá danému klíči.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#60](../../mfc/codesnippet/cpp/cmap-class_5.cpp)]

##  <a name="removeall"></a>  CMap::RemoveAll

Odebere všechny hodnoty z této mapy voláním globální pomocnou funkci `DestructElements`.

```
void RemoveAll();
```

### <a name="remarks"></a>Poznámky

Funkce funguje správně, pokud mapa je prázdný.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#61](../../mfc/codesnippet/cpp/cmap-class_6.cpp)]

##  <a name="removekey"></a>  CMap::RemoveKey

Vyhledá položku mapování odpovídající zadaný klíč; potom Pokud je nalezen klíč, odebere položku.

```
BOOL RemoveKey(ARG_KEY key);
```

### <a name="parameters"></a>Parametry

*ARG_KEY*<br/>
Parametr šablony určující typ klíče.

*key*<br/>
Klíč elementu, který chcete odebrat.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byl nalezen a úspěšně odebral; položka jinak 0.

### <a name="remarks"></a>Poznámky

`DestructElements` Pomocná funkce slouží k odebrání položky.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CMap::SetAt](#setat).

##  <a name="setat"></a>  CMap::SetAt

Primární znamená, že vkládání elementů v objektu map.

```
void SetAt(ARG_KEY key, ARG_VALUE newValue);
```

### <a name="parameters"></a>Parametry

*ARG_KEY*<br/>
Parametr šablony určující typ *klíč* parametru.

*key*<br/>
Určuje klíč nového elementu.

*ARG_VALUE*<br/>
Parametr šablony určující typ *newValue* parametru.

*newValue*<br/>
Určuje hodnotu nového elementu.

### <a name="remarks"></a>Poznámky

Nejprve je klíč vyhledávat. Pokud je nalezen klíč, pak odpovídající hodnota, která se změnily. v opačném případě se vytvoří nový pár klíč hodnota.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#62](../../mfc/codesnippet/cpp/cmap-class_7.cpp)]

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC shromažďování](../../overview/visual-cpp-samples.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
