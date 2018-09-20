---
title: Cmapstringtoob – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0d00faec0ac65ded0c8e4ddc9f1ab50796bdecd6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396321"
---
# <a name="cmapstringtoob-class"></a>Cmapstringtoob – třída

Třída kolekce slovníku, která mapuje jedinečné `CString` objektů `CObject` ukazatele.

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
|[CMapStringToOb::GetCount](#getcount)|Vrátí počet prvků, které na této mapě.|
|[CMapStringToOb::GetHashTableSize](#gethashtablesize)|Určuje aktuální počet prvků v zatřiďovací tabulce.|
|[CMapStringToOb::GetNextAssoc](#getnextassoc)|Získá další prvek pro iterace.|
|[CMapStringToOb::GetSize](#getsize)|Vrátí počet prvků, které na této mapě.|
|[CMapStringToOb::GetStartPosition](#getstartposition)|Vrátí pozici prvního prvku.|
|[CMapStringToOb::HashKey](#hashkey)|Vypočítá hodnotu hash zadaný klíč.|
|[CMapStringToOb::InitHashTable](#inithashtable)|Inicializuje zatřiďovací tabulku.|
|[CMapStringToOb::IsEmpty](#isempty)|Testy pro podmínku prázdný mapy (žádné elementy).|
|[CMapStringToOb::Lookup](#lookup)|Vyhledá neplatný ukazatel na základě klíče ukazatele. Hodnota ukazatele, není entita, na kterou odkazuje, je použita pro porovnání klíčů.|
|[CMapStringToOb::LookupKey](#lookupkey)|Vrátí odkaz na klíč přidružený k zadanou hodnotou klíče.|
|[CMapStringToOb::RemoveAll](#removeall)|Odebere všechny prvky z této mapy.|
|[CMapStringToOb::RemoveKey](#removekey)|Odebere element určený klíč.|
|[CMapStringToOb::SetAt](#setat)|Vloží prvek do mapy; nahradí existující prvek, pokud je nalezen odpovídající klíč.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[[] Č. CMapStringToOb::operator](#operator_at)|Vloží prvek do mapy – operátor nahrazení pro `SetAt`.|

## <a name="remarks"></a>Poznámky

Po vložení `CString` -  `CObject*` pár (element) do objektu map, můžete efektivně načíst nebo odstranit pár pomocí řetězce nebo `CString` hodnotu jako klíč. Můžete také iterovat přes všechny prvky v objektu map.

Proměnné typu umístění se používá pro alternativní vstupní přístup ve všech změn mapy. Můžete na POZICI "pamatovat" záznam a k iteraci v rámci mapy. Si možná myslíte, že je sekvenční podle hodnoty klíče; této iterace není. Je neurčité, sekvence načtených prvků.

`CMapStringToOb` zahrnuje `IMPLEMENT_SERIAL` – makro na podporu serializace a výpis z jeho prvků. Každý prvek je zase serializovat, když mapy je uložit do archivu, buď pomocí přetížených vložení ( **<<**) – operátor nebo se `Serialize` členskou funkci.

Pokud potřebujete diagnostiky s výpisem paměti jednotlivých prvků v objektu map ( `CString` hodnotu a `CObject` obsah), hloubka kontextu výpisu stavu systému je nutné nastavit na 1 nebo větší.

Když `CMapStringToOb` odstranění objektu, nebo když se odeberou jeho prvky, `CString` objekty a `CObject` ukazatele se odeberou. Objekty, odkazuje `CObject` ukazatele nejsou zničeny.

Odvození třídy map se podobá seznamu odvození. Přečtěte si článek [kolekce](../../mfc/collections.md) ilustraci odvození třídy seznamu zvláštní účely.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CMapStringToOb`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcoll.h

##  <a name="cmapstringtoob"></a>  CMapStringToOb::CMapStringToOb

Vytvoří prázdnou `CString`- na - `CObject*` mapy.

```
CMapStringToOb(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Parametry

*nBlockSize*<br/>
Určuje členitosti přidělení paměti pro rozšíření na mapě.

### <a name="remarks"></a>Poznámky

S růstem mapy je paměť přidělena v jednotkách, které *nBlockSize* položky.

Následující tabulka uvádí další členské funkce, které jsou podobné `CMapStringToOb:: CMapStringToOb`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**CMapPtrToPtr( INT_PTR** `nBlockSize` **= 10 );**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**CMapPtrToWord( INT_PTR** `nBlockSize` **= 10 );**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**CMapStringToPtr( INT_PTR** `nBlockSize` **= 10 );**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CMapStringToString( INT_PTR** `nBlockSize` **= 10 );**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CMapWordToOb( INT_PTR** `nBlockSize` **= 10 );**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**MapWordToPtr( INT_PTR** `nBlockSize` **= 10 );**|

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#63](../../mfc/codesnippet/cpp/cmapstringtoob-class_1.cpp)]

Zobrazit [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` Třída použitá ve všech příkladech kolekce.

##  <a name="getcount"></a>  CMapStringToOb::GetCount

Určuje počet prvků v objektu map.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet elementů v této mapy.

### <a name="remarks"></a>Poznámky

Následující tabulka uvádí další členské funkce, které jsou podobné `CMapStringToOb::GetCount`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR GetCount (const;)**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR GetCount (const;)**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR GetCount (const;)**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR GetCount (const;)**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR GetCount (const;)**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR GetCount (const;)**|

### <a name="example"></a>Příklad

Zobrazit [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` Třída použitá ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#64](../../mfc/codesnippet/cpp/cmapstringtoob-class_2.cpp)]

##  <a name="gethashtablesize"></a>  CMapStringToOb::GetHashTableSize

Určuje aktuální počet prvků v zatřiďovací tabulce.

```
UINT GetHashTableSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet prvků v zatřiďovací tabulce.

### <a name="remarks"></a>Poznámky

Následující tabulka uvádí další členské funkce, které jsou podobné `CMapStringToOb::GetHashTableSize`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT GetHashTableSize (const;)**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT GetHashTableSize (const;)**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT GetHashTableSize (const;)**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT GetHashTableSize (const;)**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**UINT GetHashTableSize (const;)**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**UINT GetHashTableSize (const;)**|

##  <a name="getnextassoc"></a>  CMapStringToOb::GetNextAssoc

Načte prvek mapy v *rNextPosition*, pak aktualizuje *rNextPosition* odkazovat na další prvek v objektu map.

```
void GetNextAssoc(
    POSITION& rNextPosition,
    CString& rKey,
    CObject*& rValue) const;
```

### <a name="parameters"></a>Parametry

*rNextPosition*<br/>
Určuje referenci na POZICI hodnotu vrácenou předchozím `GetNextAssoc` nebo `GetStartPosition` volání.

*rKey*<br/>
Určuje vrácené klíč načtený elementu (řetězec).

*r-hodnoty*<br/>
Určuje vrácené hodnoty načtené prvek ( `CObject` ukazatele). Další informace o tomto parametru najdete v poznámky.

### <a name="remarks"></a>Poznámky

Tato funkce je zvláště užitečná pro procházení všech prvků v objektu map. Všimněte si, že sekvence pozice není nutně stejné jako pořadí klíč-hodnota.

Pokud je načtený element poslední v objektu map, pak nová hodnota *rNextPosition* nastaven na hodnotu NULL.

Pro *rValue* parametr, je nutné převést objekt typu **CObject\*&**, což je co vyžaduje kompilátor, jak je znázorněno v následujícím příkladu:

[!code-cpp[NVC_MFCCollections#65](../../mfc/codesnippet/cpp/cmapstringtoob-class_3.cpp)]

To neplatí z `GetNextAssoc` pro mapy založené na šablonách.

Následující tabulka uvádí další členské funkce, které jsou podobné `CMapStringToOb::GetNextAssoc`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void GetNextAssoc (pozice &** *rNextPosition* **, void\* &**  *rKey* **, void\* &**  *rValue* **) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void GetNextAssoc (pozice &** *rNextPosition* **, void\* &**  *rKey* **, WORD a** *rValue* **) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void GetNextAssoc (pozice &** *rNextPosition* **, CString &** *rKey* **, void\* &**  *rValue* **) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void GetNextAssoc (pozice &** *rNextPosition* **, CString &** *rKey* **, CString &** *rValue* **) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void GetNextAssoc (pozice &** *rNextPosition* **, WORD &** *rKey* **, CObject\* &**  *rValue* **) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void GetNextAssoc (pozice &** *rNextPosition* **, WORD &** *rKey* **, void\* &**  *rValue* **) const;**|

### <a name="example"></a>Příklad

Zobrazit [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` Třída použitá ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#66](../../mfc/codesnippet/cpp/cmapstringtoob-class_4.cpp)]

Výsledky z této aplikace jsou následující:

```Output
Lisa : a CAge at $4724 11
Marge : a CAge at $47A8 35
Homer : a CAge at $4766 36
Bart : a CAge at $45D4 13
```

##  <a name="getsize"></a>  CMapStringToOb::GetSize

Vrátí počet prvků na mapě.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v objektu map.

### <a name="remarks"></a>Poznámky

Voláním této metody lze načíst počet prvků v objektu map.

Následující tabulka uvádí další členské funkce, které jsou podobné `CMapStringToOb::GetSize`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR getsize – (const;)**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR getsize – (const;)**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR getsize – (const;)**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR getsize – (const;)**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR getsize – (const;)**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR getsize – (const;)**|

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#67](../../mfc/codesnippet/cpp/cmapstringtoob-class_5.cpp)]

##  <a name="getstartposition"></a>  CMapStringToOb::GetStartPosition

Spuštění iterace mapování tak, že vrací hodnotu POZICI, která mohou být předány `GetNextAssoc` volání.

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Návratová hodnota

POZICE určující počáteční pozice pro iterace v mapě. nebo hodnota NULL, pokud mapa je prázdný.

### <a name="remarks"></a>Poznámky

Iterace sekvence není předvídatelný; "první prvek v objektu map", proto nemá žádný speciální význam.

Následující tabulka uvádí další členské funkce, které jsou podobné `CMapStringToOb::GetStartPosition`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**POZICE GetStartPosition (const;)**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**POZICE GetStartPosition (const;)**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**POZICE GetStartPosition (const;)**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**POZICE GetStartPosition (const;)**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**POZICE GetStartPosition (const;)**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**POZICE GetStartPosition (const;)**|

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CMapStringToOb::GetNextAssoc](#getnextassoc).

##  <a name="hashkey"></a>  CMapStringToOb::HashKey

Vypočítá hodnotu hash zadaný klíč.

```
UINT HashKey(LPCTSTR key) const;
```

### <a name="parameters"></a>Parametry

*Klíč*<br/>
Klíč, jehož hodnota hash je vypočítán.

### <a name="return-value"></a>Návratová hodnota

Hodnota hash klíče

### <a name="remarks"></a>Poznámky

Následující tabulka uvádí další členské funkce, které jsou podobné `CMapStringToOb::HashKey`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**HashKey – UINT (void** <strong>\*</strong> `key` **) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**HashKey – UINT (void** <strong>\*</strong> `key` **) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**HashKey – UINT (LPCTSTR** `key` **) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**HashKey – UINT (LPCTSTR** `key` **) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**HashKey – UINT (slovo** `key` **) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**HashKey – UINT (slovo** `key` **) const;**|

##  <a name="inithashtable"></a>  CMapStringToOb::InitHashTable

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
Při hodnotě TRUE se přiděluje zatřiďovací tabulku při inicializaci; jinak v tabulce je přidělena v případě potřeby.

### <a name="remarks"></a>Poznámky

Pro zajištění nejlepšího výkonu by měl být velikost tabulky hash Prvočíslo. Chcete-li minimalizovat kolize, velikost musí mít zhruba 20 procent větší než největší očekávané datové sady.

Následující tabulka uvádí další členské funkce, které jsou podobné `CMapStringToOb::InitHashTable`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|

##  <a name="isempty"></a>  CMapStringToOb::IsEmpty

Určuje, zda na mapě je prázdný.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud neobsahuje žádné elementy; toto mapování jinak 0.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [RemoveAll](#removeall).

### <a name="remarks"></a>Poznámky

Následující tabulka uvádí další členské funkce, které jsou podobné **cmapstringtoob –:: IsEmpty**.

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL IsEmpty (const;)**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL IsEmpty (const;)**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL IsEmpty (const;)**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL IsEmpty (const;)**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL IsEmpty (const;)**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL IsEmpty (const;)**|

##  <a name="lookup"></a>  CMapStringToOb::Lookup

Vrátí `CObject` ukazatel na základě `CString` hodnotu.

```
BOOL Lookup(
    LPCTSTR key,
    CObject*& rValue) const;
```

### <a name="parameters"></a>Parametry

*Klíč*<br/>
Určuje klíč řetězec, který identifikuje elementu, který chcete vyhledávat.

*r-hodnoty*<br/>
Určuje vrácenou hodnotu z prvku vyhledaných.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud element nebyl nalezen; jinak 0.

### <a name="remarks"></a>Poznámky

`Lookup` používá algoritmus hash a rychle najít prvek mapy s klíčem, který přesně odpovídá ( `CString` hodnota).

Následující tabulka uvádí další členské funkce, které jsou podobné `CMapStringToOb::LookUp`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Vyhledávání BOOL (void** <strong>\*</strong> `key` **, void\* &**  `rValue` **) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Vyhledávání BOOL (void** <strong>\*</strong> `key` **, WORD &** `rValue` **) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Vyhledávání BOOL (LPCTSTR** `key` **, void\* &**  `rValue` **) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Vyhledávání BOOL (LPCTSTR** `key` **, CString &** `rValue` **) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**Vyhledávání BOOL (slovo** `key` **, CObject\* &**  `rValue` **) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**Vyhledávání BOOL (slovo** `key` **, void\* &**  `rValue` **) const;**|

### <a name="example"></a>Příklad

Zobrazit [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` Třída použitá ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#68](../../mfc/codesnippet/cpp/cmapstringtoob-class_6.cpp)]

##  <a name="lookupkey"></a>  CMapStringToOb::LookupKey

Vrátí odkaz na klíč přidružený k zadanou hodnotou klíče.

```
BOOL LookupKey(
    LPCTSTR key,
    LPCTSTR& rKey) const;
```

### <a name="parameters"></a>Parametry

*Klíč*<br/>
Určuje klíč řetězec, který identifikuje elementu, který chcete vyhledávat.

*rKey*<br/>
Odkaz na přidružený klíč.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byl klíč nalezen; jinak 0.

### <a name="remarks"></a>Poznámky

Pomocí odkazu na klíč nebezpečné, pokud se používá po přidruženého prvku byl odebrán z mapy nebo po mapy se zničil.

Následující tabulka uvádí další členské funkce, které jsou podobné `CMapStringToOb:: LookupKey`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL LookupKey (LPCTSTR** `key` **, LPCTSTR &** `rKey` **) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL LookupKey (LPCTSTR** `key` **, LPCTSTR &** `rKey` **) const;**|

##  <a name="operator_at"></a>  [] Č. CMapStringToOb::operator

Pohodlné náhradou za `SetAt` členskou funkci.

```
CObject*& operator[ ](lpctstr key);
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na ukazatel `CObject` objektu; nebo hodnota NULL, pokud mapa je prázdný nebo *klíč* je mimo rozsah.

### <a name="remarks"></a>Poznámky

Proto jej lze použít pouze na levé straně příkazu přiřazení (l hodnota). Pokud neexistuje žádné mapování element se zadaným klíčem, se vytvoří nový prvek.

Ekvivalentní pro tento operátor není žádný "pravému" (r), protože je možné, že klíče nemusí být nalezen v objektu map. Použití `Lookup` členskou funkci pro prvek načítání.

Následující tabulka uvádí další členské funkce, které jsou podobné `CMapStringToOb::operator []`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|<strong>void\*& – operátor\[] (void \*</strong>  `key`  **\);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Operátor & WORD\[] (void** <strong>\*</strong> `key`  **\);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void\*& – operátor\[] (lpctstr** `key`  **\);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CString – & – operátor\[] (lpctstr** `key`  **\);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CObject –\*& – operátor\[] (slovo** `key`  **\);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void\*& – operátor\[] (slovo** `key`  **\);**|

### <a name="example"></a>Příklad

Zobrazit [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` Třída použitá ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#72](../../mfc/codesnippet/cpp/cmapstringtoob-class_7.cpp)]

Výsledky z této aplikace jsou následující:

```Output
Operator [] example: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $4A02 11
[Bart] = a CAge at $497E 13
```

##  <a name="removeall"></a>  CMapStringToOb::RemoveAll

Odebere všechny prvky z této mapy a odstraní `CString` klíče objekty.

```
void RemoveAll();
```

### <a name="remarks"></a>Poznámky

`CObject` Objekty odkazuje každý klíč nejsou zničeny. `RemoveAll` Funkce může způsobit nevracení paměti, pokud není zajistíte, že odkazované `CObject` objekty jsou zničeny.

Funkce funguje správně, pokud mapa je prázdný.

Následující tabulka uvádí další členské funkce, které jsou podobné `CMapStringToOb::RemoveAll`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void (RemoveAll);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void (RemoveAll);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void (RemoveAll);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void (RemoveAll);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void (RemoveAll);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void (RemoveAll);**|

### <a name="example"></a>Příklad

Zobrazit [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` Třída použitá ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#69](../../mfc/codesnippet/cpp/cmapstringtoob-class_8.cpp)]

##  <a name="removekey"></a>  CMapStringToOb::RemoveKey

Vyhledá položku mapování odpovídající zadaný klíč; potom Pokud je nalezen klíč, odebere položku.

```
BOOL RemoveKey(LPCTSTR key);
```

### <a name="parameters"></a>Parametry

*Klíč*<br/>
Určuje řetězec, používají pro vyhledávání v mapě.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byl nalezen a úspěšně odebral; položka jinak 0.

### <a name="remarks"></a>Poznámky

To může způsobit nevracení paměti, pokud `CObject` objekt není odstraněn, jinde.

Následující tabulka uvádí další členské funkce, které jsou podobné `CMapStringToOb::RemoveKey`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL RemoveKey (void** <strong>\*</strong> `key` **);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL RemoveKey (void** <strong>\*</strong> `key` **);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL RemoveKey (LPCTSTR** `key` **);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL RemoveKey (LPCTSTR** `key` **);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL RemoveKey (slovo** `key` **);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL RemoveKey (slovo** `key` **);**|

### <a name="example"></a>Příklad

Zobrazit [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` Třída použitá ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#70](../../mfc/codesnippet/cpp/cmapstringtoob-class_9.cpp)]

Výsledky z této aplikace jsou následující:

```Output
RemoveKey example: A CMapStringToOb with 3 elements
[Marge] = a CAge at $49A0 35
[Homer] = a CAge at $495E 36
[Bart] = a CAge at $4634 13
```

##  <a name="setat"></a>  CMapStringToOb::SetAt

Primární znamená, že vkládání elementů v objektu map.

```
void SetAt(
    LPCTSTR key,
    CObject* newValue);
```

### <a name="parameters"></a>Parametry

*Klíč*<br/>
Určuje řetězec, který je klíč nového elementu.

*newValue*<br/>
Určuje, `CObject` ukazatel, který je hodnota nového elementu.

### <a name="remarks"></a>Poznámky

Nejprve je klíč vyhledávat. Pokud je nalezen klíč, pak odpovídající hodnota, která se změnily. v opačném případě se vytvoří nový prvek klíč hodnota.

Následující tabulka uvádí další členské funkce, které jsou podobné `CMapStringToOb::SetAt`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void SetAt (void** <strong>\*</strong> `key` **, void** <strong>\*</strong> `newValue` **);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void SetAt (void** <strong>\*</strong> `key` **, WORD** `newValue` **);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void SetAt (LPCTSTR** `key` **, void** <strong>\*</strong> `newValue` **);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void SetAt (LPCTSTR** `key` **, LPCTSTR** `newValue` **);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void SetAt (slovo** `key` **, CObject** <strong>\*</strong> `newValue` **);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void SetAt (slovo** `key` **, void** <strong>\*</strong> `newValue` **);**|

### <a name="example"></a>Příklad

Zobrazit [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` Třída použitá ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#71](../../mfc/codesnippet/cpp/cmapstringtoob-class_10.cpp)]

Výsledky z této aplikace jsou následující:

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
