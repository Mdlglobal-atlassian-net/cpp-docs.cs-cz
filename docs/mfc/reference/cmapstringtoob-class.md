---
title: CMapStringToOb Class
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
ms.openlocfilehash: b56e9052533269ba62d248312f07ac16db71bf4a
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418536"
---
# <a name="cmapstringtoob-class"></a>CMapStringToOb Class

Třída kolekce slovníku, která mapuje jedinečné `CString` objektů na ukazatele `CObject`.

## <a name="syntax"></a>Syntaxe

```
class CMapStringToOb : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMapStringToOb::CMapStringToOb](#cmapstringtoob)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMapStringToOb:: GetCount](#getcount)|Vrátí počet prvků v této mapě.|
|[CMapStringToOb::GetHashTableSize](#gethashtablesize)|Určuje aktuální počet prvků v zatřiďovací tabulce.|
|[CMapStringToOb::GetNextAssoc](#getnextassoc)|Získá další prvek pro iteraci.|
|[CMapStringToOb:: GetSize](#getsize)|Vrátí počet prvků v této mapě.|
|[CMapStringToOb::GetStartPosition](#getstartposition)|Vrátí pozici prvního prvku.|
|[CMapStringToOb::HashKey](#hashkey)|Vypočítá hodnotu hash zadaného klíče.|
|[CMapStringToOb::InitHashTable](#inithashtable)|Inicializuje zatřiďovací tabulku.|
|[CMapStringToOb::-Empty](#isempty)|Testuje podmínku prázdné mapy (žádné elementy).|
|[CMapStringToOb:: Lookup](#lookup)|Vyhledá ukazatel void na základě klíče ukazatele void. Hodnota ukazatele, nikoli entita, na kterou odkazuje, se používá pro porovnání klíčů.|
|[CMapStringToOb:: LookupKey](#lookupkey)|Vrátí odkaz na klíč přidružený k zadané hodnotě klíče.|
|[CMapStringToOb::RemoveAll](#removeall)|Odebere všechny prvky z této mapy.|
|[CMapStringToOb::RemoveKey](#removekey)|Odebere prvek určený klíčem.|
|[CMapStringToOb::SetAt](#setat)|Vloží prvek do mapy; nahradí existující prvek, pokud se najde shodný klíč.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CMapStringToOb:: operator \[ \]](#operator_at)|Vloží prvek do mapy – nahrazení operátoru pro `SetAt`.|

## <a name="remarks"></a>Poznámky

Po vložení `CString`- `CObject*` dvojici (elementu) do mapy lze efektivně načíst nebo odstranit dvojici pomocí řetězce nebo hodnoty `CString` jako klíče. Můžete také iterovat přes všechny prvky v mapě.

Proměnná typu POSITION se používá pro alternativní přístup k položkám ve všech variacích map. Můžete použít pozici pro "zapamatování" záznamu a iterovat přes mapu. Můžete si všimnout, že je tato iterace sekvenční podle hodnoty klíče. Nejedná se o. Sekvence načtených elementů je neurčitá.

`CMapStringToOb` zahrnuje makro `IMPLEMENT_SERIAL` pro podporu serializace a dumpingu jeho prvků. Každý prvek je serializován v případě, že je mapa uložena do archivu, buď pomocí operátoru přetížení ( **<<** ), nebo pomocí členské funkce `Serialize`.

Pokud potřebujete diagnostické výpisy jednotlivých prvků v mapě (hodnota `CString` a obsah `CObject`), je nutné nastavit hloubku kontextu výpisu na hodnotu 1 nebo vyšší.

Když je odstraněn objekt `CMapStringToOb` nebo když jsou jeho prvky odebrány, jsou objekty `CString` a `CObject` ukazatele odebrány. Objekty odkazované ukazateli `CObject` nebudou zničeny.

Odvození třídy map je podobné odvození seznamu. Ilustraci odvození třídy seznamu pro speciální účely najdete v [kolekcích](../../mfc/collections.md) článků.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

`CMapStringToOb`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcoll. h

##  <a name="cmapstringtoob"></a>CMapStringToOb::CMapStringToOb

Vytvoří prázdnou mapu `CString`-to-`CObject*`.

```
CMapStringToOb(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Parametry

*nBlockSize*<br/>
Určuje členitost přidělení paměti pro rozšíření mapy.

### <a name="remarks"></a>Poznámky

Jak se mapa zvětšuje, paměť se přiděluje v jednotkách *nBlockSizech* položek.

V následující tabulce jsou uvedeny jiné členské funkce, které jsou podobné `CMapStringToOb:: CMapStringToOb`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**CMapPtrToPtr (INT_PTR** `nBlockSize` **= 10);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**CMapPtrToWord (INT_PTR** `nBlockSize` **= 10);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**CMapStringToPtr (INT_PTR** `nBlockSize` **= 10);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CMapStringToString (INT_PTR** `nBlockSize` **= 10);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CMapWordToOb (INT_PTR** `nBlockSize` **= 10);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**MapWordToPtr (INT_PTR** `nBlockSize` **= 10);**|

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#63](../../mfc/codesnippet/cpp/cmapstringtoob-class_1.cpp)]

Seznam `CAge` třídy používané ve všech příkladech kolekce naleznete v tématu [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) .

##  <a name="getcount"></a>CMapStringToOb:: GetCount

Určuje, kolik prvků je v mapě.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků v této mapě.

### <a name="remarks"></a>Poznámky

V následující tabulce jsou uvedeny jiné členské funkce, které jsou podobné `CMapStringToOb::GetCount`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR GetCount () const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR GetCount () const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR GetCount () const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR GetCount () const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR GetCount () const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR GetCount () const;**|

### <a name="example"></a>Příklad

Seznam `CAge` třídy používané ve všech příkladech kolekce naleznete v tématu [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) .

[!code-cpp[NVC_MFCCollections#64](../../mfc/codesnippet/cpp/cmapstringtoob-class_2.cpp)]

##  <a name="gethashtablesize"></a>CMapStringToOb::GetHashTableSize

Určuje aktuální počet prvků v zatřiďovací tabulce.

```
UINT GetHashTableSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet prvků v zatřiďovací tabulce.

### <a name="remarks"></a>Poznámky

V následující tabulce jsou uvedeny jiné členské funkce, které jsou podobné `CMapStringToOb::GetHashTableSize`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT GetHashTableSize () const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT GetHashTableSize () const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT GetHashTableSize () const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT GetHashTableSize () const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**UINT GetHashTableSize () const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**UINT GetHashTableSize () const;**|

##  <a name="getnextassoc"></a>CMapStringToOb::GetNextAssoc

Načte mapový element na *rNextPosition*a pak aktualizuje *rNextPosition* , aby odkazoval na další prvek v mapě.

```
void GetNextAssoc(
    POSITION& rNextPosition,
    CString& rKey,
    CObject*& rValue) const;
```

### <a name="parameters"></a>Parametry

*rNextPosition*<br/>
Určuje odkaz na hodnotu pozice vrácenou předchozí `GetNextAssoc` nebo volání `GetStartPosition`.

*rKey*<br/>
Určuje vrácený klíč načteného elementu (řetězec).

*r*<br/>
Určuje vrácenou hodnotu načteného prvku (`CObject` ukazatel). Další informace o tomto parametru najdete v části poznámky.

### <a name="remarks"></a>Poznámky

Tato funkce je nejužitečnější pro iteraci všech prvků v mapě. Všimněte si, že sekvence pozice není nutně stejná jako sekvence hodnoty klíče.

Pokud je načtený prvek poslední v mapě, je nová hodnota *rNextPosition* nastavena na hodnotu null.

Pro parametr *rValue* nezapomeňte přetypovat typ objektu na **CObject\*&** , což je to, co kompilátor vyžaduje, jak je znázorněno v následujícím příkladu:

[!code-cpp[NVC_MFCCollections#65](../../mfc/codesnippet/cpp/cmapstringtoob-class_3.cpp)]

To není pravdivé `GetNextAssoc` pro mapy založené na šablonách.

V následující tabulce jsou uvedeny jiné členské funkce, které jsou podobné `CMapStringToOb::GetNextAssoc`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void GetNextAssoc (pozice &** *rNextPosition* **, void\*&** *rKey* **, void\*&** *rValue* **) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void GetNextAssoc (pozice &** *rNextPosition* **, void\*&** *rKey* **, wordový &** *rValue* **) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void GetNextAssoc (POSITION &** *rNextPosition* **, CString &** *rKey* **, void\*&** *rValue* **) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void GetNextAssoc (POSITION &** *rNextPosition* **, cstring &** *rKey* **, CString &** *rValue* **) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void GetNextAssoc (POSITION &** *rNextPosition* **, WORD &** *rKey* **, CObject\*&** *rValue* **) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void GetNextAssoc (POSITION &** *rNextPosition* **, WORD &** *rKey* **, void\*&** *rValue* **) const;**|

### <a name="example"></a>Příklad

Seznam `CAge` třídy používané ve všech příkladech kolekce naleznete v tématu [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) .

[!code-cpp[NVC_MFCCollections#66](../../mfc/codesnippet/cpp/cmapstringtoob-class_4.cpp)]

Výsledky z tohoto programu jsou následující:

```Output
Lisa : a CAge at $4724 11
Marge : a CAge at $47A8 35
Homer : a CAge at $4766 36
Bart : a CAge at $45D4 13
```

##  <a name="getsize"></a>CMapStringToOb:: GetSize

Vrátí počet prvků mapy.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v mapě.

### <a name="remarks"></a>Poznámky

Voláním této metody načtete počet prvků v mapě.

V následující tabulce jsou uvedeny jiné členské funkce, které jsou podobné `CMapStringToOb::GetSize`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR GetSize () const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR GetSize () const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR GetSize () const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR GetSize () const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR GetSize () const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR GetSize () const;**|

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#67](../../mfc/codesnippet/cpp/cmapstringtoob-class_5.cpp)]

##  <a name="getstartposition"></a>CMapStringToOb::GetStartPosition

Spustí iteraci mapy vrácením hodnoty pozice, kterou lze předat `GetNextAssoc` volání.

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota pozice označující počáteční pozici pro iteraci mapy; nebo hodnotu NULL, pokud je mapa prázdná.

### <a name="remarks"></a>Poznámky

Posloupnost iterace není předvídatelná; Proto "první prvek v mapě" nemá žádný zvláštní význam.

V následující tabulce jsou uvedeny jiné členské funkce, které jsou podobné `CMapStringToOb::GetStartPosition`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**POZICE GetStartPosition () const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**POZICE GetStartPosition () const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**POZICE GetStartPosition () const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**POZICE GetStartPosition () const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**POZICE GetStartPosition () const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**POZICE GetStartPosition () const;**|

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CMapStringToOb:: GetNextAssoc](#getnextassoc).

##  <a name="hashkey"></a>CMapStringToOb::HashKey

Vypočítá hodnotu hash zadaného klíče.

```
UINT HashKey(LPCTSTR key) const;
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč, jehož hodnota hash má být vypočítána.

### <a name="return-value"></a>Návratová hodnota

Hodnota hash klíče

### <a name="remarks"></a>Poznámky

V následující tabulce jsou uvedeny jiné členské funkce, které jsou podobné `CMapStringToOb::HashKey`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Uint HashKey (void** <strong>\*</strong> `key` **) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Uint HashKey (void** <strong>\*</strong> `key` **) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Uint HashKey (LPCTSTR** `key` **) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Uint HashKey (LPCTSTR** `key` **) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**Uint HashKey (WORD** `key` **) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**Uint HashKey (WORD** `key` **) const;**|

##  <a name="inithashtable"></a>CMapStringToOb::InitHashTable

Inicializuje zatřiďovací tabulku.

```
void InitHashTable(
    UINT hashSize,
    BOOL bAllocNow = TRUE);
```

### <a name="parameters"></a>Parametry

*hashSize*<br/>
Počet položek v zatřiďovací tabulce.

*bAllocNow*<br/>
Je-li nastavena hodnota TRUE, při inicializaci přidělí zatřiďovací tabulku; v opačném případě je tabulka přidělena v případě potřeby.

### <a name="remarks"></a>Poznámky

Pro dosažení nejlepšího výkonu by měla být velikost tabulky hash primárním číslem. Chcete-li minimalizovat kolizí, velikost by měla být přibližně 20 procent větší než největší předpokládaná sada dat.

V následující tabulce jsou uvedeny jiné členské funkce, které jsou podobné `CMapStringToOb::InitHashTable`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void InitHashTable (UINT** `hashSize` **, bool** `bAllocNow` **= true);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void InitHashTable (UINT** `hashSize` **, bool** `bAllocNow` **= true);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void InitHashTable (UINT** `hashSize` **, bool** `bAllocNow` **= true);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void InitHashTable (UINT** `hashSize` **, bool** `bAllocNow` **= true);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void InitHashTable (UINT** `hashSize` **, bool** `bAllocNow` **= true);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void InitHashTable (UINT** `hashSize` **, bool** `bAllocNow` **= true);**|

##  <a name="isempty"></a>CMapStringToOb::-Empty

Určuje, zda je mapa prázdná.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud tato mapa neobsahuje žádné elementy; v opačném případě 0.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [RemoveAll](#removeall).

### <a name="remarks"></a>Poznámky

V následující tabulce jsou uvedeny jiné členské funkce, které jsou podobné **CMapStringToOb::-Empty**.

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL = Empty () const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL = Empty () const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL = Empty () const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL = Empty () const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL = Empty () const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL = Empty () const;**|

##  <a name="lookup"></a>CMapStringToOb:: Lookup

Vrátí `CObject` ukazatel na základě `CString` hodnoty.

```
BOOL Lookup(
    LPCTSTR key,
    CObject*& rValue) const;
```

### <a name="parameters"></a>Parametry

*key*<br/>
Určuje klíč řetězce, který identifikuje prvek, který má být vyhledán.

*r*<br/>
Určuje vrácenou hodnotu z vyhledaného prvku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byl element nalezen; v opačném případě 0.

### <a name="remarks"></a>Poznámky

`Lookup` používá algoritmus hash k rychlému nalezení mapového prvku s klíčem, který přesně odpovídá (`CString` hodnota).

V následující tabulce jsou uvedeny jiné členské funkce, které jsou podobné `CMapStringToOb::LookUp`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Vyhledávání bool (void** <strong>\*</strong> `key` **, void\*&** `rValue` **) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Vyhledávání bool (void** <strong>\*</strong> `key` **, Word &** `rValue` **) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Vyhledávání bool (LPCTSTR** `key` **, void\*&** `rValue` **) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Vyhledávání bool (LPCTSTR** `key` **, CString &** `rValue` **) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**Vyhledávání bool (WORD** `key` **, CObject\*&** `rValue` **) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**Vyhledávání bool (WORD** `key` **, void\*&** `rValue` **) const;**|

### <a name="example"></a>Příklad

Seznam `CAge` třídy používané ve všech příkladech kolekce naleznete v tématu [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) .

[!code-cpp[NVC_MFCCollections#68](../../mfc/codesnippet/cpp/cmapstringtoob-class_6.cpp)]

##  <a name="lookupkey"></a>CMapStringToOb:: LookupKey

Vrátí odkaz na klíč přidružený k zadané hodnotě klíče.

```
BOOL LookupKey(
    LPCTSTR key,
    LPCTSTR& rKey) const;
```

### <a name="parameters"></a>Parametry

*key*<br/>
Určuje klíč řetězce, který identifikuje prvek, který má být vyhledán.

*rKey*<br/>
Odkaz na přidružený klíč.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byl klíč nalezen; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Použití odkazu na klíč není bezpečné, pokud je použit po odebrání přidruženého prvku z mapy nebo po zničení mapy.

V následující tabulce jsou uvedeny jiné členské funkce, které jsou podobné `CMapStringToOb:: LookupKey`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Bool LookupKey (LPCTSTR** `key` **, LPCTSTR &** `rKey` **) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Bool LookupKey (LPCTSTR** `key` **, LPCTSTR &** `rKey` **) const;**|

##  <a name="operator_at"></a>CMapStringToOb:: operator [] – operátor

Užitečná náhrada za `SetAt` členskou funkci.

```
CObject*& operator[ ](lpctstr key);
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na ukazatel na objekt `CObject`; nebo hodnotu NULL, pokud je mapa prázdná nebo je *klíč* mimo rozsah.

### <a name="remarks"></a>Poznámky

Proto se dá použít jenom na levé straně příkazu přiřazení (l-hodnota). Pokud není k dispozici žádný element mapy se zadaným klíčem, je vytvořen nový prvek.

Neexistuje žádná "pravá strana" (r-value) ekvivalentní tomuto operátoru, protože existuje možnost, že na mapě nelze najít klíč. Pro načtení elementu použijte členskou funkci `Lookup`.

V následující tabulce jsou uvedeny jiné členské funkce, které jsou podobné `CMapStringToOb::operator []`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|<strong>void\*& operátor\[] (void \*</strong> `key` **\);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**\[operátoru & slova] (void** <strong>\*</strong> `key` **\);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void\*& operátor\[] (lpctstr** `key` **\);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CString & operátor\[] (lpctstr** `key` **\);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CObject\*& operátor\[] (wordová** `key` **\);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void\*& operátor\[] (wordový** `key` **\);**|

### <a name="example"></a>Příklad

Seznam `CAge` třídy používané ve všech příkladech kolekce naleznete v tématu [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) .

[!code-cpp[NVC_MFCCollections#72](../../mfc/codesnippet/cpp/cmapstringtoob-class_7.cpp)]

Výsledky z tohoto programu jsou následující:

```Output
Operator [] example: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $4A02 11
[Bart] = a CAge at $497E 13
```

##  <a name="removeall"></a>CMapStringToOb::RemoveAll

Odebere všechny prvky z této mapy a odstraní objekty `CString` klíče.

```
void RemoveAll();
```

### <a name="remarks"></a>Poznámky

Objekty `CObject`, na které se odkazuje každý klíč, nebudou zničeny. Funkce `RemoveAll` může způsobit nevracení paměti, pokud nezajistíte zničení odkazovaných `CObject` objektů.

Funkce funguje správně, pokud je již mapa prázdná.

V následující tabulce jsou uvedeny jiné členské funkce, které jsou podobné `CMapStringToOb::RemoveAll`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void RemoveAll ();**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void RemoveAll ();**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void RemoveAll ();**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void RemoveAll ();**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void RemoveAll ();**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void RemoveAll ();**|

### <a name="example"></a>Příklad

Seznam `CAge` třídy používané ve všech příkladech kolekce naleznete v tématu [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) .

[!code-cpp[NVC_MFCCollections#69](../../mfc/codesnippet/cpp/cmapstringtoob-class_8.cpp)]

##  <a name="removekey"></a>CMapStringToOb::RemoveKey

Vyhledá položku mapy odpovídající zadanému klíči. Pokud se klíč najde, odebere položku.

```
BOOL RemoveKey(LPCTSTR key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Určuje řetězec, který se používá pro vyhledávání v mapě.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud se položka našla a úspěšně odebrala; v opačném případě 0.

### <a name="remarks"></a>Poznámky

To může způsobit nevracení paměti, pokud se `CObject` objekt neodstraní jinde.

V následující tabulce jsou uvedeny jiné členské funkce, které jsou podobné `CMapStringToOb::RemoveKey`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Bool RemoveKey (void** <strong>\*</strong> `key` **);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Bool RemoveKey (void** <strong>\*</strong> `key` **);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Bool RemoveKey (LPCTSTR** `key` **);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Bool RemoveKey (LPCTSTR** `key` **);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**Bool RemoveKey (WORD** `key` **);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**Bool RemoveKey (WORD** `key` **);**|

### <a name="example"></a>Příklad

Seznam `CAge` třídy používané ve všech příkladech kolekce naleznete v tématu [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) .

[!code-cpp[NVC_MFCCollections#70](../../mfc/codesnippet/cpp/cmapstringtoob-class_9.cpp)]

Výsledky z tohoto programu jsou následující:

```Output
RemoveKey example: A CMapStringToOb with 3 elements
[Marge] = a CAge at $49A0 35
[Homer] = a CAge at $495E 36
[Bart] = a CAge at $4634 13
```

##  <a name="setat"></a>CMapStringToOb::SetAt

Primární způsob vložení prvku do mapy.

```
void SetAt(
    LPCTSTR key,
    CObject* newValue);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Určuje řetězec, který je klíčem nového prvku.

*newValue*<br/>
Určuje `CObject` ukazatel, který je hodnotou nového prvku.

### <a name="remarks"></a>Poznámky

Nejprve se vyhledá klíč. Pokud se klíč najde, změní se odpovídající hodnota. v opačném případě je vytvořen nový prvek klíčové hodnoty.

V následující tabulce jsou uvedeny jiné členské funkce, které jsou podobné `CMapStringToOb::SetAt`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void SetAt (void** <strong>\*</strong> `key` **, void** <strong>\*</strong> `newValue` **);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void SetAt (void** <strong>\*</strong> `key` **, Word** `newValue` **);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void SetAt (LPCTSTR** `key` **, void** <strong>\*</strong> `newValue` **);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void SetAt (LPCTSTR** `key` **, LPCTSTR** `newValue` **);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void SetAt (wordová** `key` **, CObject** <strong>\*</strong> `newValue` **);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void SetAt (WORD** `key` **, void** <strong>\*</strong> `newValue` **);**|

### <a name="example"></a>Příklad

Seznam `CAge` třídy používané ve všech příkladech kolekce naleznete v tématu [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) .

[!code-cpp[NVC_MFCCollections#71](../../mfc/codesnippet/cpp/cmapstringtoob-class_10.cpp)]

Výsledky z tohoto programu jsou následující:

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
[CMapPtrToPtr – třída](../../mfc/reference/cmapptrtoptr-class.md)<br/>
[CMapPtrToWord – třída](../../mfc/reference/cmapptrtoword-class.md)<br/>
[CMapStringToPtr – třída](../../mfc/reference/cmapstringtoptr-class.md)<br/>
[CMapStringToString – třída](../../mfc/reference/cmapstringtostring-class.md)<br/>
[CMapWordToOb – třída](../../mfc/reference/cmapwordtoob-class.md)<br/>
[CMapWordToPtr – třída](../../mfc/reference/cmapwordtoptr-class.md)
