---
title: Třída CMapStringToob
ms.date: 11/04/2016
f1_keywords:
- CMapStringToOb
- AFXCOLL/CMapStringToOb
- AFXCOLL/CMapStringToOb::CMapStringToOb
- AFXCOLL/CMapStringToOb::GetCount
- AFXCOLL/CMapStringToOb::GetHashTableSize
- AFXCOLL/CMapStringToOb::GetNextAssoc
- AFXCOLL/CMapStringToOb::GetSize
- AFXCOLL/CMapStringToOb::GetStartPosition
- AFXCOLL/CMapStringToOb::HashKey
- AFXCOLL/CMapStringToOb::InitHashTable
- AFXCOLL/CMapStringToOb::IsEmpty
- AFXCOLL/CMapStringToOb::Lookup
- AFXCOLL/CMapStringToOb::LookupKey
- AFXCOLL/CMapStringToOb::RemoveAll
- AFXCOLL/CMapStringToOb::RemoveKey
- AFXCOLL/CMapStringToOb::SetAt
helpviewer_keywords:
- CMapStringToOb [MFC], CMapStringToOb
- CMapStringToOb [MFC], GetCount
- CMapStringToOb [MFC], GetHashTableSize
- CMapStringToOb [MFC], GetNextAssoc
- CMapStringToOb [MFC], GetSize
- CMapStringToOb [MFC], GetStartPosition
- CMapStringToOb [MFC], HashKey
- CMapStringToOb [MFC], InitHashTable
- CMapStringToOb [MFC], IsEmpty
- CMapStringToOb [MFC], Lookup
- CMapStringToOb [MFC], LookupKey
- CMapStringToOb [MFC], RemoveAll
- CMapStringToOb [MFC], RemoveKey
- CMapStringToOb [MFC], SetAt
ms.assetid: 09653980-b885-4f3a-8594-0aeb7f94c601
ms.openlocfilehash: 12de7bd72f643f08cebf948634703172d6725ce6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370106"
---
# <a name="cmapstringtoob-class"></a>Třída CMapStringToob

Třída kolekce slovníku, `CString` která `CObject` mapuje jedinečné objekty na ukazatele.

## <a name="syntax"></a>Syntaxe

```
class CMapStringToOb : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMapStringToob::CMapStringToob](#cmapstringtoob)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMapStringToob::GetCount](#getcount)|Vrátí počet prvků v této mapě.|
|[CMapStringToOb::GetHashTableSize](#gethashtablesize)|Určuje aktuální počet prvků v tabulce hash.|
|[CMapStringToOb::GetNextAssoc](#getnextassoc)|Získá další prvek pro iterace.|
|[CMapStringToob::GetSize](#getsize)|Vrátí počet prvků v této mapě.|
|[CMapStringToob::GetStartPozice](#getstartposition)|Vrátí pozici prvního prvku.|
|[CMapStringToOb::HashKey](#hashkey)|Vypočítá hodnotu hash zadaného klíče.|
|[CMapStringToOb::InitHashTable](#inithashtable)|Inicializuje tabulku hash.|
|[CMapStringToob::Jeprázdný](#isempty)|Testy pro podmínku prázdné mapy (žádné prvky).|
|[CMapStringToOb::Vyhledávání](#lookup)|Vyhledá ukazatel void na základě klávesy ukazatele void. Hodnota ukazatele, nikoli entita, na kterou odkazuje, se používá pro porovnání klíčů.|
|[CMapStringToOb::Vyhledávací klíč](#lookupkey)|Vrátí odkaz na klíč přidružený k zadané hodnotě klíče.|
|[CMapStringToob::Removeall](#removeall)|Odebere všechny prvky z této mapy.|
|[CMapStringToob::Odstranit klíč](#removekey)|Odebere prvek určený klíčem.|
|[CMapStringToob::Setat](#setat)|Vloží prvek do mapy; nahradí existující prvek, pokud je nalezen odpovídající klíč.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CMapStringToOb::operátor \[\]](#operator_at)|Vloží prvek do mapy – substituce operátora pro `SetAt`.|

## <a name="remarks"></a>Poznámky

Jakmile vložíte pár `CString` -  `CObject*` (prvek) do mapy, můžete efektivně načíst nebo odstranit pár `CString` pomocí řetězce nebo hodnoty jako klíče. Můžete také itrovat všechny prvky v mapě.

Proměnná typu POSITION se používá pro alternativní přístup k položkám ve všech variantách mapy. Pozici můžete použít k "zapamatování" položky a k itetování mapy. Můžete si myslet, že tato iterace je sekvenční podle hodnoty klíče; to není. Posloupnost načtených prvků je neurčitá.

`CMapStringToOb`obsahuje `IMPLEMENT_SERIAL` makro pro podporu serializace a dumpingu jeho prvků. Každý prvek je serializován v pořadí, pokud je mapa uložena do **<<** archivu, buď `Serialize` s přetíženým operátorem insertion ( nebo s členovou funkcí.

Pokud potřebujete diagnostický výpis jednotlivých prvků v `CString` mapě (hodnota a `CObject` obsah), musíte nastavit hloubku kontextu výpisu na hodnotu 1 nebo vyšší.

Při `CMapStringToOb` odstranění objektu nebo při odebrání jeho `CString` prvků `CObject` jsou odebrány objekty a ukazatele. Objekty odkazované `CObject` ukazateli nejsou zničeny.

Odvození třídy mapy je podobné odvození seznamu. Viz článek [Sbírky](../../mfc/collections.md) pro ilustraci odvození třídy speciální seznam.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CMapStringToOb`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcoll.h

## <a name="cmapstringtoobcmapstringtoob"></a><a name="cmapstringtoob"></a>CMapStringToob::CMapStringToob

Vytvoří prázdnou `CString`mapu `CObject*` -to-map.

```
CMapStringToOb(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Parametry

*nBlockSize*<br/>
Určuje rozlišovací schopnost přidělení paměti pro rozšíření mapy.

### <a name="remarks"></a>Poznámky

Jak se mapu zvětšuje, paměť je přidělena v jednotkách položek *nBlockSize.*

V následující tabulce jsou uvedeny `CMapStringToOb:: CMapStringToOb`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**CMapPtrToPtr( INT_PTR** `nBlockSize` **= 10 );**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**CMapPtrToWord( INT_PTR** `nBlockSize` **= 10 );**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**CMapStringToPtr( INT_PTR** `nBlockSize` **= 10 );**|
|[Řetězec CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CMapStringToString( INT_PTR** `nBlockSize` **= 10 );**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CMapWordToOb( INT_PTR** `nBlockSize` **= 10 );**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**MapWordToPtr( INT_PTR** `nBlockSize` **= 10 );**|

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#63](../../mfc/codesnippet/cpp/cmapstringtoob-class_1.cpp)]

Viz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pro výpis `CAge` třídy používané ve všech příkladech kolekce.

## <a name="cmapstringtoobgetcount"></a><a name="getcount"></a>CMapStringToob::GetCount

Určuje, kolik prvků je v mapě.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků v této mapě.

### <a name="remarks"></a>Poznámky

V následující tabulce jsou uvedeny `CMapStringToOb::GetCount`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR GetCount( ) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR GetCount( ) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR GetCount( ) const;**|
|[Řetězec CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR GetCount( ) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR GetCount( ) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR GetCount( ) const;**|

### <a name="example"></a>Příklad

Viz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pro výpis `CAge` třídy používané ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#64](../../mfc/codesnippet/cpp/cmapstringtoob-class_2.cpp)]

## <a name="cmapstringtoobgethashtablesize"></a><a name="gethashtablesize"></a>CMapStringToOb::GetHashTableSize

Určuje aktuální počet prvků v tabulce hash.

```
UINT GetHashTableSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet prvků v tabulce hash.

### <a name="remarks"></a>Poznámky

V následující tabulce jsou uvedeny `CMapStringToOb::GetHashTableSize`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT GetHashTableSize( ) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT GetHashTableSize( ) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT GetHashTableSize( ) const;**|
|[Řetězec CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT GetHashTableSize( ) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**UINT GetHashTableSize( ) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**UINT GetHashTableSize( ) const;**|

## <a name="cmapstringtoobgetnextassoc"></a><a name="getnextassoc"></a>CMapStringToOb::GetNextAssoc

Načte prvek mapy na *rNextPosition*, pak aktualizuje *rNextPosition* odkazovat na další prvek v mapě.

```
void GetNextAssoc(
    POSITION& rNextPosition,
    CString& rKey,
    CObject*& rValue) const;
```

### <a name="parameters"></a>Parametry

*rNextPosition*<br/>
Určuje odkaz na hodnotu POSITION vrácenou předchozím `GetNextAssoc` nebo `GetStartPosition` volacím.

*rKlíč*<br/>
Určuje vrácený klíč načteného prvku (řetězec).

*rValue*<br/>
Určuje vrácenou hodnotu načteného prvku `CObject` (ukazatele). Další informace o tomto parametru naleznete v části Poznámky.

### <a name="remarks"></a>Poznámky

Tato funkce je nejužitečnější pro iterace přes všechny prvky v mapě. Všimněte si, že pořadí pozic není nutně stejné jako pořadí hodnot klíče.

Pokud načtený prvek je poslední v mapě, pak je nová hodnota *rNextPosition* nastavena na hodnotu NULL.

U parametru *rValue* nezapomeňte přetypovat typ objektu na **CObject\***, což je to, co kompilátor vyžaduje, jak je znázorněno v následujícím příkladu:

[!code-cpp[NVC_MFCCollections#65](../../mfc/codesnippet/cpp/cmapstringtoob-class_3.cpp)]

To neplatí `GetNextAssoc` pro mapy založené na šablonách.

V následující tabulce jsou uvedeny `CMapStringToOb::GetNextAssoc`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void GetNextAssoc( POSITION&** *rNextPosition* **, void\* ** *rKey* **, void\* ** *rValue)* **const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void GetNextAssoc( POSITION&** *rNextPosition* **, void\* ** *rKey* **, WORD&** *rValue)* **const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void GetNextAssoc( POSITION&** *rNextPosition* **, CString&** *rKey* **, void\* ** *rValue)* **const;**|
|[Řetězec CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void GetNextAssoc( POSITION&** *rNextPosition* **, CString&** *rKey* **, CString&** *rValue)* **const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void GetNextAssoc( POSITION&** *rNextPosition* **, WORD&** *rKey* **, CObject\* ** *rValue)* **const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void GetNextAssoc( POSITION&** *rNextPosition* **, WORD&** *rKey* **, void\* ** *rValue)* **const;**|

### <a name="example"></a>Příklad

Viz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pro výpis `CAge` třídy používané ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#66](../../mfc/codesnippet/cpp/cmapstringtoob-class_4.cpp)]

Výsledky tohoto programu jsou následující:

```Output
Lisa : a CAge at $4724 11
Marge : a CAge at $47A8 35
Homer : a CAge at $4766 36
Bart : a CAge at $45D4 13
```

## <a name="cmapstringtoobgetsize"></a><a name="getsize"></a>CMapStringToob::GetSize

Vrátí počet prvků mapy.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v mapě.

### <a name="remarks"></a>Poznámky

Volání této metody načíst počet prvků v mapě.

V následující tabulce jsou uvedeny `CMapStringToOb::GetSize`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR GetSize( ) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR GetSize( ) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR GetSize( ) const;**|
|[Řetězec CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR GetSize( ) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR GetSize( ) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR GetSize( ) const;**|

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#67](../../mfc/codesnippet/cpp/cmapstringtoob-class_5.cpp)]

## <a name="cmapstringtoobgetstartposition"></a><a name="getstartposition"></a>CMapStringToob::GetStartPozice

Spustí iteraci mapy vrácením hodnoty POSITION, `GetNextAssoc` která může být předána volání.

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota POSITION, která označuje počáteční pozici pro itace mapy; nebo NULL, pokud je mapa prázdná.

### <a name="remarks"></a>Poznámky

Pořadí iterace není předvídatelné; proto "první prvek v mapě" nemá žádný zvláštní význam.

V následující tabulce jsou uvedeny `CMapStringToOb::GetStartPosition`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**POZICE GetStartPosition( ) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**POZICE GetStartPosition( ) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**POZICE GetStartPosition( ) const;**|
|[Řetězec CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**POZICE GetStartPosition( ) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**POZICE GetStartPosition( ) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**POZICE GetStartPosition( ) const;**|

### <a name="example"></a>Příklad

Viz příklad [cmapstringtoob::GetNextAssoc](#getnextassoc).

## <a name="cmapstringtoobhashkey"></a><a name="hashkey"></a>CMapStringToOb::HashKey

Vypočítá hodnotu hash zadaného klíče.

```
UINT HashKey(LPCTSTR key) const;
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč, jehož hodnota hash má být vypočtena.

### <a name="return-value"></a>Návratová hodnota

Hodnota hash klíče

### <a name="remarks"></a>Poznámky

V následující tabulce jsou uvedeny `CMapStringToOb::HashKey`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT HashKey( void** <strong>\*</strong> `key` **) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT HashKey( void** <strong>\*</strong> `key` **) const;**|
|[Řetězec CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT HashKey( LPCTSTR** `key` **) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT HashKey( LPCTSTR** `key` **) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**UINT HashKey( SLOVO** `key` **) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**UINT HashKey( SLOVO** `key` **) const;**|

## <a name="cmapstringtoobinithashtable"></a><a name="inithashtable"></a>CMapStringToOb::InitHashTable

Inicializuje tabulku hash.

```
void InitHashTable(
    UINT hashSize,
    BOOL bAllocNow = TRUE);
```

### <a name="parameters"></a>Parametry

*velikost hashVelikost*<br/>
Počet položek v tabulce hash.

*bAllocNyní*<br/>
Pokud TRUE, přidělí tabulku hash při inicializaci; jinak je tabulka přidělena v případě potřeby.

### <a name="remarks"></a>Poznámky

Pro nejlepší výkon by velikost tabulky hash měla být prvočíslo. Chcete-li minimalizovat kolize, velikost by měla být zhruba o 20 procent větší než největší očekávaná sada dat.

V následující tabulce jsou uvedeny `CMapStringToOb::InitHashTable`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|
|[Řetězec CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|

## <a name="cmapstringtoobisempty"></a><a name="isempty"></a>CMapStringToob::Jeprázdný

Určuje, zda je mapa prázdná.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud tato mapa neobsahuje žádné prvky; jinak 0.

### <a name="example"></a>Příklad

Viz příklad pro [RemoveAll](#removeall).

### <a name="remarks"></a>Poznámky

V následující tabulce jsou uvedeny další členské funkce, které jsou podobné **CMapStringToOb:: IsEmpty**.

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL IsEmpty( ) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL IsEmpty( ) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL IsEmpty( ) const;**|
|[Řetězec CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL IsEmpty( ) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL IsEmpty( ) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL IsEmpty( ) const;**|

## <a name="cmapstringtooblookup"></a><a name="lookup"></a>CMapStringToOb::Vyhledávání

Vrátí `CObject` ukazatel na `CString` základě hodnoty.

```
BOOL Lookup(
    LPCTSTR key,
    CObject*& rValue) const;
```

### <a name="parameters"></a>Parametry

*key*<br/>
Určuje řetězec klíč, který identifikuje prvek, který má být vyhledán.

*rValue*<br/>
Určuje vrácenou hodnotu z prvku vyhledat.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byl prvek nalezen; jinak 0.

### <a name="remarks"></a>Poznámky

`Lookup`používá algoritmus hash k rychlému nalezení prvku mapy `CString` pomocí klíče, který přesně odpovídá (hodnota).

V následující tabulce jsou uvedeny `CMapStringToOb::LookUp`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL Vyhledávání( void** <strong>\*</strong> `key` **\* , void** `rValue` **) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL Vyhledávání( void** <strong>\*</strong> `key` **, WORD&** `rValue` **) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL Vyhledávání( LPCTSTR** `key` **\* , void** `rValue` **) const;**|
|[Řetězec CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL Vyhledávání( LPCTSTR** `key` **, CString&** `rValue` **) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL Vyhledávání( SLOVO** `key` **,\* CObject** `rValue` **) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL Vyhledávání( SLOVO** `key` **\* , void** `rValue` **) const;**|

### <a name="example"></a>Příklad

Viz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pro výpis `CAge` třídy používané ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#68](../../mfc/codesnippet/cpp/cmapstringtoob-class_6.cpp)]

## <a name="cmapstringtooblookupkey"></a><a name="lookupkey"></a>CMapStringToOb::Vyhledávací klíč

Vrátí odkaz na klíč přidružený k zadané hodnotě klíče.

```
BOOL LookupKey(
    LPCTSTR key,
    LPCTSTR& rKey) const;
```

### <a name="parameters"></a>Parametry

*key*<br/>
Určuje řetězec klíč, který identifikuje prvek, který má být vyhledán.

*rKlíč*<br/>
Odkaz na přidružený klíč.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byl klíč nalezen; jinak 0.

### <a name="remarks"></a>Poznámky

Použití odkazu na klíč je nebezpečné, pokud je použito po odebrání přidruženého prvku z mapy nebo po zničení mapy.

V následující tabulce jsou uvedeny `CMapStringToOb:: LookupKey`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL LookupKey( LPCTSTR** `key` **, LPCTSTR&)** `rKey` **const;**|
|[Řetězec CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL LookupKey( LPCTSTR** `key` **, LPCTSTR&)** `rKey` **const;**|

## <a name="cmapstringtooboperator--"></a><a name="operator_at"></a>CMapStringToOb::operátor [ ]

Vhodnou náhradou `SetAt` za člennou funkci.

```
CObject*& operator[ ](lpctstr key);
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na ukazatel na `CObject` objekt; nebo NULL, pokud je mapa prázdná nebo *je klíč* mimo rozsah.

### <a name="remarks"></a>Poznámky

Proto jej lze použít pouze na levé straně příkazu přiřazení (hodnota l). Pokud neexistuje žádný prvek mapy se zadaným klíčem, je vytvořen nový prvek.

Neexistuje žádná "pravá strana" (hodnota r) ekvivalentní tomuto operátoru, protože existuje možnost, že klíč nemusí být nalezen v mapě. Pro `Lookup` načítání prvků použijte členská funkci.

V následující tabulce jsou uvedeny `CMapStringToOb::operator []`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|<strong>\[provozovatel\*& neplatné \* ](void</strong> `key` ** \);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**WORD&\[operátor ](void** <strong>\*</strong> `key` ** \);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**\[operátor\* void& ](lpctstr** `key` ** \);**|
|[Řetězec CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CString&\[operátor ](lpctstr** `key` ** \);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CObject\*&\[operátor ](slovo** `key` ** \);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**\[operátor\* void& ](slovo** `key` ** \);**|

### <a name="example"></a>Příklad

Viz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pro výpis `CAge` třídy používané ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#72](../../mfc/codesnippet/cpp/cmapstringtoob-class_7.cpp)]

Výsledky tohoto programu jsou následující:

```Output
Operator [] example: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $4A02 11
[Bart] = a CAge at $497E 13
```

## <a name="cmapstringtoobremoveall"></a><a name="removeall"></a>CMapStringToob::Removeall

Odstraní všechny prvky z této mapy `CString` a zničí klíčové objekty.

```
void RemoveAll();
```

### <a name="remarks"></a>Poznámky

Objekty `CObject` odkazované jednotlivými klíči nejsou zničeny. Funkce `RemoveAll` může způsobit nevracení paměti, pokud nezajistíte, že odkazované objekty jsou zničeny. `CObject`

Funkce funguje správně, pokud je mapa již prázdná.

V následující tabulce jsou uvedeny `CMapStringToOb::RemoveAll`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void RemoveAll( );**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void RemoveAll( );**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void RemoveAll( );**|
|[Řetězec CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void RemoveAll( );**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void RemoveAll( );**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void RemoveAll( );**|

### <a name="example"></a>Příklad

Viz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pro výpis `CAge` třídy používané ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#69](../../mfc/codesnippet/cpp/cmapstringtoob-class_8.cpp)]

## <a name="cmapstringtoobremovekey"></a><a name="removekey"></a>CMapStringToob::Odstranit klíč

Vyhledá položku mapy odpovídající zadanému klíči. pokud je klíč nalezen, odebere položku.

```
BOOL RemoveKey(LPCTSTR key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Určuje řetězec použitý pro vyhledávání mapy.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla položka nalezena a úspěšně odebrána; jinak 0.

### <a name="remarks"></a>Poznámky

To může způsobit nevracení paměti, `CObject` pokud objekt není odstraněn jinde.

V následující tabulce jsou uvedeny `CMapStringToOb::RemoveKey`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL RemoveKey( void** <strong>\*</strong> `key` **);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL RemoveKey( void** <strong>\*</strong> `key` **);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL RemoveKey( LPCTSTR);** `key` **);**|
|[Řetězec CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL RemoveKey( LPCTSTR);** `key` **);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL RemoveKey(** `key` **SLOVO);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL RemoveKey(** `key` **SLOVO);**|

### <a name="example"></a>Příklad

Viz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pro výpis `CAge` třídy používané ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#70](../../mfc/codesnippet/cpp/cmapstringtoob-class_9.cpp)]

Výsledky tohoto programu jsou následující:

```Output
RemoveKey example: A CMapStringToOb with 3 elements
[Marge] = a CAge at $49A0 35
[Homer] = a CAge at $495E 36
[Bart] = a CAge at $4634 13
```

## <a name="cmapstringtoobsetat"></a><a name="setat"></a>CMapStringToob::Setat

Primární prostředky pro vložení prvku do mapy.

```
void SetAt(
    LPCTSTR key,
    CObject* newValue);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Určuje řetězec, který je klíčem nového prvku.

*Newvalue*<br/>
Určuje `CObject` ukazatel, který je hodnotou nového prvku.

### <a name="remarks"></a>Poznámky

Za prvé, klíč je vzhlédl. Pokud je nalezen klíč, změní se odpovídající hodnota; v opačném případě je vytvořen nový prvek hodnota klíče.

V následující tabulce jsou uvedeny `CMapStringToOb::SetAt`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void Setat( void** <strong>\*</strong> `key` **, void** <strong>\*</strong> `newValue` **);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void Setat( void** <strong>\*</strong> `key` **, WORD** `newValue` **);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void Setat( LPCTSTR** `key` **, void** <strong>\*</strong> `newValue` **);**|
|[Řetězec CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void Setat( LPCTSTR** `key` **, LPCTSTR** `newValue` **);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void Setat( WORD** `key` **, CObject** <strong>\*</strong> `newValue` **);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void Setat( SLOVO** `key` **, void** <strong>\*</strong> `newValue` **);**|

### <a name="example"></a>Příklad

Viz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pro výpis `CAge` třídy používané ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#71](../../mfc/codesnippet/cpp/cmapstringtoob-class_10.cpp)]

Výsledky tohoto programu jsou následující:

```Output
before Lisa's birthday: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $493C 11
[Bart] = a CAge at $4654 13
after Lisa's birthday: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $49C0 12
[Bart] = a CAge at $4654 13
```

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)<br/>
[Třída CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)<br/>
[CMapStringToPtr – třída](../../mfc/reference/cmapstringtoptr-class.md)<br/>
[Třída CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)<br/>
[CMapWordToOb – třída](../../mfc/reference/cmapwordtoob-class.md)<br/>
[CMapWordToPtr – třída](../../mfc/reference/cmapwordtoptr-class.md)
