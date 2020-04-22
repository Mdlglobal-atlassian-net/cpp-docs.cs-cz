---
title: Třída CMap
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
ms.openlocfilehash: fbb34d4db41ef11cd01a6a8a7f20cafa0e737268
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749071"
---
# <a name="cmap-class"></a>Třída CMap

Třída kolekce slovníku, která mapuje jedinečné klíče na hodnoty.

## <a name="syntax"></a>Syntaxe

```
template<class KEY, class ARG_KEY, class VALUE, class ARG_VALUE>class CMap : public CObject
```

#### <a name="parameters"></a>Parametry

*Klíč*<br/>
Třída objektu použitá jako klíč k mapě.

*ARG_KEY*<br/>
Datový typ používaný pro *klíčové* argumenty; obvykle odkaz na *KEY*.

*Hodnotu*<br/>
Třída objektu uloženého v mapě.

*ARG_VALUE*<br/>
Datový typ používaný pro argumenty *VALUE;* obvykle odkaz na *HODNOTU*.

## <a name="members"></a>Členové

### <a name="public-structures"></a>Veřejné struktury

|Název|Popis|
|----------|-----------------|
|[CMap::CPair](#cpair)|Vnořená struktura obsahující hodnotu klíče a hodnotu přidruženého objektu.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMap::CMap](#cmap)|Vytvoří kolekci, která mapuje klíče na hodnoty.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMap::GetCount](#getcount)|Vrátí počet prvků v této mapě.|
|[CMap::GetHashTableSize](#gethashtablesize)|Vrátí počet prvků v tabulce hash.|
|[CMap::GetNextAssoc](#getnextassoc)|Získá další prvek pro iterace.|
|[CMap::GetSize](#getsize)|Vrátí počet prvků v této mapě.|
|[CMap::GetStartPosition](#getstartposition)|Vrátí pozici prvního prvku.|
|[CMap::InitHashTable](#inithashtable)|Inicializuje tabulku hash a určuje její velikost.|
|[CMap::Jeprázdný](#isempty)|Testy pro podmínku prázdné mapy (žádné prvky).|
|[CMap::Vyhledávání](#lookup)|Vyhledá hodnotu namapovanou na daný klíč.|
|[CMap::PGetFirstAssoc](#pgetfirstassoc)|Vrátí ukazatel na první prvek.|
|[CMap::PGetNextAssoc](#pgetnextassoc)|Získá ukazatel na další prvek pro iterace.|
|[CMap::P Vyhledávání](#plookup)|Vrátí ukazatel na klíč, jehož hodnota odpovídá zadané hodnotě.|
|[CMap::RemoveAll](#removeall)|Odebere všechny prvky z této mapy.|
|[CMap::RemoveKey](#removekey)|Odebere prvek určený klíčem.|
|[CMap::Setat](#setat)|Vloží prvek do mapy; nahradí existující prvek, pokud je nalezen odpovídající klíč.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CMap::operátor \[\]](#operator_at)|Vloží prvek do mapy – substituce operátora pro `SetAt`.|

## <a name="remarks"></a>Poznámky

Jakmile vložíte pár klíč-hodnota (prvek) do mapy, můžete efektivně načíst nebo odstranit pár pomocí klíče pro přístup k němu. Můžete také itrovat všechny prvky v mapě.

Proměnná typu POSITION se používá pro alternativní přístup k položkám. Pozici můžete použít k "zapamatování" položky a k itetování mapy. Můžete si myslet, že tato iterace je sekvenční podle hodnoty klíče; to není. Posloupnost načtených prvků je neurčitá.

Některé členské funkce této třídy volají globální pomocné funkce, `CMap` které musí být přizpůsobeny pro většinu použití třídy. Viz [Pomocníky tříd y kolekce](../../mfc/reference/collection-class-helpers.md) v části Makra a globální soubory referenční **knihovny MFC**.

`CMap`přepíše [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) pro podporu serializace a ukládání jeho prvků. Pokud je mapa uložena `Serialize`do archivu pomocí , každý prvek mapy je serializován a zase. Výchozí implementace `SerializeElements` pomocné funkce provádí bitový zápis. Informace o serializaci položek kolekce ukazatelů `CObject` odvozených z nebo jiných typů definovaných uživatelem naleznete v [tématu How to: Make a Type-Safe Collection](../../mfc/how-to-make-a-type-safe-collection.md).

Pokud potřebujete diagnostický výpis jednotlivých prvků v mapě (klíče a hodnoty), musíte nastavit hloubku kontextu výpisu na 1 nebo vyšší.

Při `CMap` odstranění objektu nebo při odebrání jeho prvků jsou odebrány klíče i hodnoty.

Odvození třídy mapy je podobné odvození seznamu. Viz článek [Sbírky](../../mfc/collections.md) pro ilustraci odvození třídy speciální seznam.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CMap`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxtempl.h

## <a name="cmapcmap"></a><a name="cmap"></a>CMap::CMap

Vytvoří prázdnou mapu.

```
CMap(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Parametry

*nBlockSize*<br/>
Určuje rozlišovací schopnost přidělení paměti pro rozšíření mapy.

### <a name="remarks"></a>Poznámky

Jak se mapu zvětšuje, paměť je přidělena v jednotkách položek *nBlockSize.*

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#56](../../mfc/codesnippet/cpp/cmap-class_1.cpp)]

## <a name="cmapcpair"></a><a name="cpair"></a>CMap::CPair

Obsahuje hodnotu klíče a hodnotu přidruženého objektu.

### <a name="remarks"></a>Poznámky

Toto je vnořená struktura v rámci třídy [CMap](../../mfc/reference/cmap-class.md).

Struktura se skládá ze dvou polí:

- `key`Skutečná hodnota typu klíče.

- `value`Hodnota přidruženého objektu.

Používá se k uložení vrácené hodnoty z [CMap::PLookup](#plookup), [CMap::PGetFirstAssoc](#pgetfirstassoc)a [CMap::PGetNextAssoc](#pgetnextassoc).

### <a name="example"></a>Příklad

Příklad použití naleznete v příkladu [cmap::PLookup](#plookup).

## <a name="cmapgetcount"></a><a name="getcount"></a>CMap::GetCount

Načte počet prvků v mapě.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků.

### <a name="example"></a>Příklad

Viz příklad pro [CMap::Lookup](#lookup).

## <a name="cmapgethashtablesize"></a><a name="gethashtablesize"></a>CMap::GetHashTableSize

Určuje počet prvků v tabulce hash pro mapu.

```
UINT GetHashTableSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků v tabulce hash.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#57](../../mfc/codesnippet/cpp/cmap-class_2.cpp)]

## <a name="cmapgetnextassoc"></a><a name="getnextassoc"></a>CMap::GetNextAssoc

Načte prvek mapy `rNextPosition`na `rNextPosition` , pak aktualizuje odkazovat na další prvek v mapě.

```cpp
void GetNextAssoc(
    POSITION& rNextPosition,
    KEY& rKey,
    VALUE& rValue) const;
```

### <a name="parameters"></a>Parametry

*rNextPosition*<br/>
Určuje odkaz na hodnotu POSITION vrácenou předchozím `GetNextAssoc` nebo `GetStartPosition` volacím.

*Klíč*<br/>
Parametr šablony určující typ klíče mapy.

*rKlíč*<br/>
Určuje vrácený klíč načteného prvku.

*Hodnotu*<br/>
Parametr šablony určující typ hodnoty mapy.

*rValue*<br/>
Určuje vrácenou hodnotu načteného prvku.

### <a name="remarks"></a>Poznámky

Tato funkce je nejužitečnější pro iterace přes všechny prvky v mapě. Všimněte si, že pořadí pozic není nutně stejné jako pořadí hodnot klíče.

Pokud načtený prvek je poslední v mapě, pak je nová hodnota *rNextPosition* nastavena na hodnotu NULL.

### <a name="example"></a>Příklad

Viz příklad pro [CMap::SetAt](#setat).

## <a name="cmapgetsize"></a><a name="getsize"></a>CMap::GetSize

Vrátí počet prvků mapy.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v mapě.

### <a name="remarks"></a>Poznámky

Volání této metody načíst počet prvků v mapě.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]

## <a name="cmapgetstartposition"></a><a name="getstartposition"></a>CMap::GetStartPosition

Spustí iteraci mapy vrácením hodnoty POSITION, `GetNextAssoc` která může být předána volání.

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota POSITION, která označuje počáteční pozici pro itace mapy; nebo NULL, pokud je mapa prázdná.

### <a name="remarks"></a>Poznámky

Pořadí iterace není předvídatelné; proto "první prvek v mapě" nemá žádný zvláštní význam.

### <a name="example"></a>Příklad

Viz příklad pro [CMap::SetAt](#setat).

## <a name="cmapinithashtable"></a><a name="inithashtable"></a>CMap::InitHashTable

Inicializuje tabulku hash.

```cpp
void InitHashTable(UINT hashSize, BOOL  bAllocNow = TRUE);
```

### <a name="parameters"></a>Parametry

*velikost hashVelikost*<br/>
Počet položek v tabulce hash.

*bAllocNyní*<br/>
Pokud TRUE, přidělí tabulku hash při inicializaci; jinak je tabulka přidělena v případě potřeby.

### <a name="remarks"></a>Poznámky

Pro nejlepší výkon by velikost tabulky hash měla být prvočíslo. Chcete-li minimalizovat kolize, velikost by měla být zhruba o 20 procent větší než největší očekávaná sada dat.

### <a name="example"></a>Příklad

Viz příklad pro [CMap::Lookup](#lookup).

## <a name="cmapisempty"></a><a name="isempty"></a>CMap::Jeprázdný

Určuje, zda je mapa prázdná.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud tato mapa neobsahuje žádné prvky; jinak 0.

### <a name="example"></a>Příklad

Viz příklad pro [CMap::RemoveAll](#removeall).

## <a name="cmaplookup"></a><a name="lookup"></a>CMap::Vyhledávání

Vyhledá hodnotu namapovanou na daný klíč.

```
BOOL Lookup(ARG_KEY key, VALUE& rValue) const;
```

### <a name="parameters"></a>Parametry

*ARG_KEY*<br/>
Parametr šablony určující typ hodnoty *klíče.*

*key*<br/>
Určuje klíč, který identifikuje prvek, který má být vyhledán.

*Hodnotu*<br/>
Určuje typ hodnoty, která má být vyhledána.

*rValue*<br/>
Obdrží vyhlédnutou hodnotu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byl prvek nalezen; jinak 0.

### <a name="remarks"></a>Poznámky

`Lookup`používá algoritmus hash rychle najít prvek mapy s klíčem, který přesně odpovídá daný klíč.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]

## <a name="cmapoperator--"></a><a name="operator_at"></a>CMap::operátor [ ]

Vhodnou náhradou `SetAt` za člennou funkci.

```
VALUE& operator[](arg_key key);
```

### <a name="parameters"></a>Parametry

*Hodnotu*<br/>
Parametr šablony určující typ hodnoty mapy.

*ARG_KEY*<br/>
Parametr šablony určující typ hodnoty klíče.

*key*<br/>
Klíč použitý k načtení hodnoty z mapy.

### <a name="remarks"></a>Poznámky

Proto jej lze použít pouze na levé straně příkazu přiřazení (hodnota l). Pokud neexistuje žádný prvek mapy se zadaným klíčem, je vytvořen nový prvek.

Neexistuje žádná "pravá strana" (hodnota r) ekvivalentní tomuto operátoru, protože existuje možnost, že klíč nemusí být nalezen v mapě. Pro `Lookup` načítání prvků použijte členská funkci.

### <a name="example"></a>Příklad

Viz příklad pro [CMap::Lookup](#lookup).

## <a name="cmappgetfirstassoc"></a><a name="pgetfirstassoc"></a>CMap::PGetFirstAssoc

Vrátí první položku objektu mapy.

```
const CPair* PGetFirstAssoc() const;
CPair* PGetFirstAssoc();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na první položku v mapě; viz [CMap::CPair](#cpair). Pokud mapa neobsahuje žádné položky, je hodnota NULL.

### <a name="remarks"></a>Poznámky

Volání této funkce vrátí ukazatel první prvek v objektu mapy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#59](../../mfc/codesnippet/cpp/cmap-class_4.cpp)]

## <a name="cmappgetnextassoc"></a><a name="pgetnextassoc"></a>CMap::PGetNextAssoc

Načte prvek mapy, na který se vztahuje *zpráva pAssocRec*.

```
const CPair *PGetNextAssoc(const CPair* pAssocRet) const;

CPair *PGetNextAssoc(const CPair* pAssocRet);
```

### <a name="parameters"></a>Parametry

*pAssocRet*<br/>
Odkazuje na položku mapy vrácené předchozí [PGetNextAssoc](#pgetnextassoc) nebo [CMap::PGetFirstAssoc](#pgetfirstassoc) volání.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na další položku v mapě; viz [CMap::CPair](#cpair). Pokud je prvek poslední v mapě, hodnota je NULL.

### <a name="remarks"></a>Poznámky

Volání této metody iterát přes všechny prvky v mapě. Načíst první prvek s `PGetFirstAssoc` voláním a pak iterate `PGetNextAssoc`prostřednictvím mapy s následná volání .

### <a name="example"></a>Příklad

Viz příklad pro [CMap::PGetFirstAssoc](#pgetfirstassoc).

## <a name="cmapplookup"></a><a name="plookup"></a>CMap::P Vyhledávání

Najde hodnotu mapovanou na daný klíč.

```
const CPair* PLookup(ARG_KEY key) const;
CPair* PLookup(ARG_KEY key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč pro prvek, který má být vyhledán.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na strukturu klíče; viz [CMap::CPair](#cpair). Pokud není nalezena `CMap::PLookup` žádná shoda, vrátí hodnotu NULL.

### <a name="remarks"></a>Poznámky

Volání této metody k hledání prvku mapy s klíčem, který přesně odpovídá daný klíč.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#60](../../mfc/codesnippet/cpp/cmap-class_5.cpp)]

## <a name="cmapremoveall"></a><a name="removeall"></a>CMap::RemoveAll

Odebere všechny hodnoty z této mapy voláním `DestructElements`globální pomocné funkce .

```cpp
void RemoveAll();
```

### <a name="remarks"></a>Poznámky

Funkce funguje správně, pokud je mapa již prázdná.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#61](../../mfc/codesnippet/cpp/cmap-class_6.cpp)]

## <a name="cmapremovekey"></a><a name="removekey"></a>CMap::RemoveKey

Vyhledá položku mapy odpovídající zadanému klíči. pokud je klíč nalezen, odebere položku.

```
BOOL RemoveKey(ARG_KEY key);
```

### <a name="parameters"></a>Parametry

*ARG_KEY*<br/>
Parametr šablony určující typ klíče.

*key*<br/>
Klíč pro prvek, který má být odebrán.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla položka nalezena a úspěšně odebrána; jinak 0.

### <a name="remarks"></a>Poznámky

Pomocná `DestructElements` funkce slouží k odebrání položky.

### <a name="example"></a>Příklad

Viz příklad pro [CMap::SetAt](#setat).

## <a name="cmapsetat"></a><a name="setat"></a>CMap::Setat

Primární prostředky pro vložení prvku do mapy.

```cpp
void SetAt(ARG_KEY key, ARG_VALUE newValue);
```

### <a name="parameters"></a>Parametry

*ARG_KEY*<br/>
Parametr šablony určující typ *klíčového* parametru.

*key*<br/>
Určuje klíč nového prvku.

*ARG_VALUE*<br/>
Parametr šablony určující typ parametru *newValue.*

*Newvalue*<br/>
Určuje hodnotu nového prvku.

### <a name="remarks"></a>Poznámky

Za prvé, klíč je vzhlédl. Pokud je nalezen klíč, změní se odpovídající hodnota; v opačném případě je vytvořen nový pár klíč hodnota.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#62](../../mfc/codesnippet/cpp/cmap-class_7.cpp)]

## <a name="see-also"></a>Viz také

[Odběr vzorku knihovny MFC](../../overview/visual-cpp-samples.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
