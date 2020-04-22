---
title: Třída CObList
ms.date: 11/04/2016
f1_keywords:
- CObList
- AFXCOLL/CObList
- AFXCOLL/CObList::CObList
- AFXCOLL/CObList::AddHead
- AFXCOLL/CObList::AddTail
- AFXCOLL/CObList::Find
- AFXCOLL/CObList::FindIndex
- AFXCOLL/CObList::GetAt
- AFXCOLL/CObList::GetCount
- AFXCOLL/CObList::GetHead
- AFXCOLL/CObList::GetHeadPosition
- AFXCOLL/CObList::GetNext
- AFXCOLL/CObList::GetPrev
- AFXCOLL/CObList::GetSize
- AFXCOLL/CObList::GetTail
- AFXCOLL/CObList::GetTailPosition
- AFXCOLL/CObList::InsertAfter
- AFXCOLL/CObList::InsertBefore
- AFXCOLL/CObList::IsEmpty
- AFXCOLL/CObList::RemoveAll
- AFXCOLL/CObList::RemoveAt
- AFXCOLL/CObList::RemoveHead
- AFXCOLL/CObList::RemoveTail
- AFXCOLL/CObList::SetAt
helpviewer_keywords:
- CObList [MFC], CObList
- CObList [MFC], AddHead
- CObList [MFC], AddTail
- CObList [MFC], Find
- CObList [MFC], FindIndex
- CObList [MFC], GetAt
- CObList [MFC], GetCount
- CObList [MFC], GetHead
- CObList [MFC], GetHeadPosition
- CObList [MFC], GetNext
- CObList [MFC], GetPrev
- CObList [MFC], GetSize
- CObList [MFC], GetTail
- CObList [MFC], GetTailPosition
- CObList [MFC], InsertAfter
- CObList [MFC], InsertBefore
- CObList [MFC], IsEmpty
- CObList [MFC], RemoveAll
- CObList [MFC], RemoveAt
- CObList [MFC], RemoveHead
- CObList [MFC], RemoveTail
- CObList [MFC], SetAt
ms.assetid: 80699c93-33d8-4f8b-b8cf-7b58aeab64ca
ms.openlocfilehash: f24965357e0b71f28ba39b82d045600e7e1a44e2
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749682"
---
# <a name="coblist-class"></a>Třída CObList

fPodporuje seřazené seřazené seznamy nejedinečných `CObject` ukazatelů přístupných postupně nebo podle hodnoty ukazatele.

## <a name="syntax"></a>Syntaxe

```
class CObList : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CobList::CobList](#coblist)|Vytvoří prázdný seznam `CObject` pro ukazatele.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CobList::Hlavička](#addhead)|Přidá prvek (nebo všechny prvky v jiném seznamu) do hlavy seznamu (vytvoří novou hlavu).|
|[CobList::Addtail](#addtail)|Přidá prvek (nebo všechny prvky v jiném seznamu) na konci seznamu (vytvoří nový ocas).|
|[CobList::Najít](#find)|Získá pozici prvku určeného hodnotou ukazatele.|
|[CobList::FindIndex](#findindex)|Získá pozici prvku určeného index emitované nula.|
|[Coblist::Getat](#getat)|Získá prvek na dané pozici.|
|[CobList::GetCount](#getcount)|Vrátí počet prvků v tomto seznamu.|
|[CobList::Gethead](#gethead)|Vrátí prvek hlavy seznamu (nemůže být prázdný).|
|[CobList::GetheadPozice](#getheadposition)|Vrátí pozici prvku hlavy seznamu.|
|[CobList::GetNext](#getnext)|Získá další prvek pro iterace.|
|[CObList::GetPrev](#getprev)|Získá předchozí prvek pro iterace.|
|[CobList::GetSize](#getsize)|Vrátí počet prvků v tomto seznamu.|
|[CobList::GetTail](#gettail)|Vrátí ocasní prvek seznamu (nemůže být prázdný).|
|[CobList::GettailPozice](#gettailposition)|Vrátí pozici koncového prvku seznamu.|
|[CobList::InsertAfter](#insertafter)|Vloží nový prvek za danou pozici.|
|[Coblist::Insertbefore](#insertbefore)|Vloží nový prvek před danou pozici.|
|[Coblist::JePrázdný](#isempty)|Testy podmínky prázdného seznamu (žádné prvky).|
|[CobList::RemoveAll](#removeall)|Odebere všechny prvky z tohoto seznamu.|
|[coblist::Removeat](#removeat)|Odebere prvek z tohoto seznamu, určený podle pozice.|
|[CobList::RemoveHead](#removehead)|Odebere prvek z hlavy seznamu.|
|[CobList::RemoveTail](#removetail)|Odebere prvek z ocasu seznamu.|
|[Coblist::Setat](#setat)|Nastaví prvek na dané pozici.|

## <a name="remarks"></a>Poznámky

`CObList`seznamy se chovají jako dvojnásob propojené seznamy.

Proměnná typu POSITION je klíčem k seznamu. Proměnnou POSITION můžete použít jako iterátor k postupnému procházení seznamu a jako záložku pro uložení místa. Pozice však není stejná jako index.

Vložení prvku je velmi rychlé v hlavě seznamu, na ocasu a ve známé poloze. Sekvenční vyhledávání je nutné vyhledat prvek podle hodnoty nebo indexu. Toto hledání může být pomalé, pokud je seznam dlouhý.

`CObList`obsahuje makro IMPLEMENT_SERIAL pro podporu serializace a dumpingu jeho prvků. Pokud je `CObject` seznam ukazatelů uložen do archivu, buď s přetíženým operátorem vložení nebo s členovou `Serialize` funkcí, každý `CObject` prvek je serializován podle pořadí.

Pokud potřebujete výpis jednotlivých `CObject` prvků v seznamu, je nutné nastavit hloubku kontextu výpisu na 1 nebo vyšší.

Při `CObList` odstranění objektu nebo při odebrání jeho `CObject` prvků jsou odebrány pouze ukazatele, nikoli objekty, na které odkazují.

Vlastní třídy můžete `CObList`odvodit z aplikace . Nová třída seznamu, navržená tak, aby `CObject`uchovávala ukazatele na objekty odvozené z aplikace , přidává nové datové členy a nové členské funkce. Všimněte si, že výsledný seznam není přísně typ bezpečné, `CObject` protože umožňuje vložení libovolného ukazatele.

> [!NOTE]
> Pokud chcete seznam serializovat, musíte použít [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) makro při implementaci odvozené třídy.

Další informace o `CObList`použití naleznete v článku [Kolekce](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CObList`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcoll.h

## <a name="coblistaddhead"></a><a name="addhead"></a>CobList::Hlavička

Přidá nový prvek nebo seznam prvků do hlavy tohoto seznamu.

```
POSITION AddHead(CObject* newElement);
void AddHead(CObList* pNewList);
```

### <a name="parameters"></a>Parametry

*newElement*<br/>
Ukazatel, `CObject` který má být přidán do tohoto seznamu.

*pNewList*<br/>
Ukazatel na `CObList` jiný seznam. Prvky v *pNewList* budou přidány do tohoto seznamu.

### <a name="return-value"></a>Návratová hodnota

První verze vrátí hodnotu POSITION nově vloženého prvku.

V následující tabulce jsou uvedeny `CObList::AddHead`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[Seznam CPtrList](../../mfc/reference/cptrlist-class.md)|**POZICE AddHead( void** <strong>\*</strong> `newElement` **);**<br /><br /> **void AddHead( CPtrList** <strong>\*</strong> `pNewList` **);**|
|[Seznam cstring](../../mfc/reference/cstringlist-class.md)|**POZICE AddHead (const CString** `newElement` **&);**<br /><br /> **POZICE Addhead (LPCTSTR);** `newElement` **);**<br /><br /> **void AddHead(CStringList);** <strong>\*</strong> `pNewList` **);**|

### <a name="remarks"></a>Poznámky

Seznam může být před operací prázdný.

### <a name="example"></a>Příklad

  Viz [CObList::CObList](#coblist) pro výpis `CAge` třídy.

[!code-cpp[NVC_MFCCollections#89](../../mfc/codesnippet/cpp/coblist-class_1.cpp)]

Výsledky tohoto programu jsou následující:

```Output
AddHead example: A CObList with 2 elements
a CAge at $44A8 40
a CAge at $442A 21
```

## <a name="coblistaddtail"></a><a name="addtail"></a>CobList::Addtail

Přidá nový prvek nebo seznam prvků na konci tohoto seznamu.

```
POSITION AddTail(CObject* newElement);
void AddTail(CObList* pNewList);
```

### <a name="parameters"></a>Parametry

*newElement*<br/>
Ukazatel, `CObject` který má být přidán do tohoto seznamu.

*pNewList*<br/>
Ukazatel na `CObList` jiný seznam. Prvky v *pNewList* budou přidány do tohoto seznamu.

### <a name="return-value"></a>Návratová hodnota

První verze vrátí hodnotu POSITION nově vloženého prvku.

### <a name="remarks"></a>Poznámky

Seznam může být před operací prázdný.

V následující tabulce jsou uvedeny `CObList::AddTail`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[Seznam CPtrList](../../mfc/reference/cptrlist-class.md)|**POZICE AddTail(** <strong>\*</strong> `newElement` **void);**<br /><br /> **void AddTail( CPtrList** <strong>\*</strong> `pNewList` **);**|
|[Seznam cstring](../../mfc/reference/cstringlist-class.md)|**POZICE AddTail( const CString&** `newElement` **);**<br /><br /> **POZICE AddTail( LPCTSTR** `newElement` **);**<br /><br /> **void AddTail( CStringList** <strong>\*</strong> `pNewList` **);**|

### <a name="example"></a>Příklad

  Viz [CObList::CObList](#coblist) pro výpis `CAge` třídy.

[!code-cpp[NVC_MFCCollections#90](../../mfc/codesnippet/cpp/coblist-class_2.cpp)]

Výsledky tohoto programu jsou následující:

```Output
AddTail example: A CObList with 2 elements
a CAge at $444A 21
a CAge at $4526 40
```

## <a name="coblistcoblist"></a><a name="coblist"></a>CobList::CobList

Vytvoří prázdný `CObject` seznam ukazatelů.

```
CObList(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Parametry

*nBlockSize*<br/>
Rozlišovací schopnost přidělení paměti pro rozšíření seznamu.

### <a name="remarks"></a>Poznámky

Jak seznam roste, paměť je přidělena v jednotkách *nBlockSize* položek. Pokud přidělení paměti selže, `CMemoryException` je vyvolána.

V následující tabulce jsou uvedeny `CObList::CObList`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[Seznam CPtrList](../../mfc/reference/cptrlist-class.md)|**CPtrList( INT_PTR** `nBlockSize` **= 10 );**|
|[Seznam cstring](../../mfc/reference/cstringlist-class.md)|**CStringList( INT_PTR** `nBlockSize` **= 10 );**|

### <a name="example"></a>Příklad

  Níže je uveden `CObject`seznam -odvozené třídy `CAge` použité ve všech příkladech kolekce:

[!code-cpp[NVC_MFCCollections#91](../../mfc/codesnippet/cpp/coblist-class_3.h)]

Níže je uveden `CObList` příklad využití konstruktoru:

[!code-cpp[NVC_MFCCollections#92](../../mfc/codesnippet/cpp/coblist-class_4.cpp)]

## <a name="coblistfind"></a><a name="find"></a>CobList::Najít

Postupně vyhledá v seznamu první `CObject` ukazatel odpovídající `CObject` zadanému ukazateli.

```
POSITION Find(
    CObject* searchValue,
    POSITION startAfter = NULL) const;
```

### <a name="parameters"></a>Parametry

*funkce searchValue*<br/>
Ukazatel objektu, který se nachází v tomto seznamu.

*startAfter*<br/>
Počáteční pozice pro hledání.

### <a name="return-value"></a>Návratová hodnota

Hodnota POSITION, kterou lze použít pro iteraci nebo načtení ukazatele objektu; Null, pokud objekt nebyl nalezen.

### <a name="remarks"></a>Poznámky

Všimněte si, že jsou porovnány hodnoty ukazatele, nikoli obsah objektů.

V následující tabulce jsou uvedeny `CObList::Find`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[Seznam CPtrList](../../mfc/reference/cptrlist-class.md)|**POZICE Najít( void** <strong>\*</strong> `searchValue` **, POSITION** `startAfter` **= NULL ) const;**|
|[Seznam cstring](../../mfc/reference/cstringlist-class.md)|**POZICE Najít( LPCTSTR** `searchValue` **, POZICE** `startAfter` **= NULL ) const;**|

### <a name="example"></a>Příklad

Viz [CObList::CObList](#coblist) pro výpis `CAge` třídy.

[!code-cpp[NVC_MFCCollections#93](../../mfc/codesnippet/cpp/coblist-class_5.cpp)]

## <a name="coblistfindindex"></a><a name="findindex"></a>CobList::FindIndex

Používá hodnotu *nIndex* jako index do seznamu.

```
POSITION FindIndex(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Nula na základě indexu list prvek, který má být nalezen.

### <a name="return-value"></a>Návratová hodnota

Hodnota POSITION, kterou lze použít pro iteraci nebo načtení ukazatele objektu; NULL, pokud *nIndex* je příliš velký. (Rozhraní framework generuje kontrolní výraz, pokud *nIndex* je negativní.)

### <a name="remarks"></a>Poznámky

Spustí sekvenční skenování z hlavy seznamu, zastavení na *n*th element.

V následující tabulce jsou uvedeny `CObList::FindIndex`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[Seznam CPtrList](../../mfc/reference/cptrlist-class.md)|**POZICE FindIndex( INT_PTR** `nIndex` **) const;**|
|[Seznam cstring](../../mfc/reference/cstringlist-class.md)|**POZICE FindIndex( INT_PTR** `nIndex` **) const;**|

### <a name="example"></a>Příklad

Viz [CObList::CObList](#coblist) pro výpis `CAge` třídy.

[!code-cpp[NVC_MFCCollections#94](../../mfc/codesnippet/cpp/coblist-class_6.cpp)]

## <a name="coblistgetat"></a><a name="getat"></a>Coblist::Getat

Proměnná typu POSITION je klíčem k seznamu.

```
CObject*& GetAt(POSITION position);
const CObject*& GetAt(POSITION position) const;
```

### <a name="parameters"></a>Parametry

*Pozici*<br/>
Hodnota POSITION vrácená `GetHeadPosition` voláním předchozí nebo `Find` členské funkce.

### <a name="return-value"></a>Návratová hodnota

Viz popis vrácené hodnoty pro [GetHead](#gethead).

### <a name="remarks"></a>Poznámky

Není to stejné jako index a nelze pracovat na position hodnotu sami. `GetAt`načte `CObject` ukazatel přidružený k dané pozici.

Je nutné zajistit, aby hodnota POZICE představovala platnou pozici v seznamu. Pokud je neplatný, pak ladicí verze Knihovny tříd Microsoft Foundation uplatňuje.

V následující tabulce jsou uvedeny `CObList::GetAt`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[Seznam CPtrList](../../mfc/reference/cptrlist-class.md)|**const\* void& GetAt( POZICE** *POZICE* **) const;**<br /><br /> **void\*& GetAt( pozice** *polohy* **);**|
|[Seznam cstring](../../mfc/reference/cstringlist-class.md)|**const CString& GetAt( POZICE** *POZICE* **) const;**<br /><br /> **CString& Getat( pozice** *polohy* **);**|

### <a name="example"></a>Příklad

  Viz příklad pro [FindIndex](#findindex).

## <a name="coblistgetcount"></a><a name="getcount"></a>CobList::GetCount

Získá počet prvků v tomto seznamu.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Celá hodnota obsahující počet prvků.

V následující tabulce jsou uvedeny `CObList::GetCount`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[Seznam CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR GetCount( ) const;**|
|[Seznam cstring](../../mfc/reference/cstringlist-class.md)|**INT_PTR GetCount( ) const;**|

### <a name="example"></a>Příklad

Viz [CObList::CObList](#coblist) pro výpis `CAge` třídy.

[!code-cpp[NVC_MFCCollections#95](../../mfc/codesnippet/cpp/coblist-class_7.cpp)]

## <a name="coblistgethead"></a><a name="gethead"></a>CobList::Gethead

Získá `CObject` ukazatel, který představuje head element tohoto seznamu.

```
CObject*& GetHead();
const CObject*& GetHead() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud je seznam přístupný prostřednictvím `const CObList`ukazatele `GetHead` na `CObject` , vrátí ukazatel. To umožňuje funkci použít pouze na pravé straně příkazu přiřazení a tím chrání seznam před úpravou.

Pokud je seznam přístupný přímo nebo prostřednictvím ukazatele na `CObList`, vrátí `GetHead` odkaz na `CObject` ukazatel. To umožňuje funkci, která má být použita na obou stranách příkazu přiřazení a tím umožňuje položky seznamu, které mají být změněny.

### <a name="remarks"></a>Poznámky

Před voláním `GetHead`je nutné zajistit, aby seznam nebyl prázdný. Pokud je seznam prázdný, bude uplatněna ladicí verze knihovny tříd Microsoft Foundation. Pomocí [isempty](#isempty) ověřte, zda seznam obsahuje prvky.

V následující tabulce jsou uvedeny `CObList::GetHead`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[Seznam CPtrList](../../mfc/reference/cptrlist-class.md)|**const\* void& GetHead( ) const; neplatné\*& GetHead( );**|
|[Seznam cstring](../../mfc/reference/cstringlist-class.md)|**const CString& GetHead( ) const; CString& GetHead( );**|

### <a name="example"></a>Příklad

Viz [CObList::CObList](#coblist) pro výpis `CAge` třídy.

Následující příklad ilustruje použití `GetHead` příkazu přiřazení na levé straně.

[!code-cpp[NVC_MFCCollections#96](../../mfc/codesnippet/cpp/coblist-class_8.cpp)]

## <a name="coblistgetheadposition"></a><a name="getheadposition"></a>CobList::GetheadPozice

Získá pozici head prvek tohoto seznamu.

```
POSITION GetHeadPosition() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota POSITION, kterou lze použít pro iteraci nebo načtení ukazatele objektu; Null, pokud je seznam prázdný.

V následující tabulce jsou uvedeny `CObList::GetHeadPosition`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[Seznam CPtrList](../../mfc/reference/cptrlist-class.md)|**POZICE GetHeadPosition( ) const;**|
|[Seznam cstring](../../mfc/reference/cstringlist-class.md)|**POZICE GetHeadPosition( ) const;**|

### <a name="example"></a>Příklad

Viz [CObList::CObList](#coblist) pro výpis `CAge` třídy.

[!code-cpp[NVC_MFCCollections#97](../../mfc/codesnippet/cpp/coblist-class_9.cpp)]

## <a name="coblistgetnext"></a><a name="getnext"></a>CobList::GetNext

Získá list element identifikován *rPosition*, pak `POSITION` nastaví *rPosition* na hodnotu další položky v seznamu.

```
CObject*& GetNext(POSITION& rPosition);
const CObject* GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parametry

*rPozice*<br/>
Odkaz na hodnotu POSITION vrácenou předchozím `GetNext`voláním `GetHeadPosition`členské funkce nebo jiným voláním členské funkce.

### <a name="return-value"></a>Návratová hodnota

Viz popis vrácené hodnoty pro [GetHead](#gethead).

### <a name="remarks"></a>Poznámky

Můžete použít `GetNext` ve smyčce dopředné iterace, `GetHeadPosition` pokud `Find`navážete počáteční pozici s voláním nebo .

Je nutné zajistit, aby hodnota POZICE představovala platnou pozici v seznamu. Pokud je neplatný, pak ladicí verze Knihovny tříd Microsoft Foundation uplatňuje.

Pokud načtený prvek je poslední v seznamu, pak je nová hodnota *rPosition* nastavena na hodnotu NULL.

Je možné odebrat prvek během iterace. Viz příklad [removeat](#removeat).

> [!NOTE]
> Od knihovny MFC 8.0 const verze této `const CObject*` metody `const CObject*&`se změnil na návrat namísto .  Tato změna byla provedena, aby kompilátor do shody s c++ standard.

V následující tabulce jsou uvedeny `CObList::GetNext`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[Seznam CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const void* GetNext( POSITION&` `rPosition` `) const;`|
|[Seznam cstring](../../mfc/reference/cstringlist-class.md)|`CString& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetNext( POSITION&` `rPosition` `) const;`|

### <a name="example"></a>Příklad

  Viz [CObList::CObList](#coblist) pro výpis `CAge` třídy.

[!code-cpp[NVC_MFCCollections#98](../../mfc/codesnippet/cpp/coblist-class_10.cpp)]

Výsledky tohoto programu jsou následující:

```Output
a CAge at $479C 40
a CAge at $46C0 21
```

## <a name="coblistgetprev"></a><a name="getprev"></a>CObList::GetPrev

Získá prvek seznamu identifikovaný *rPosition*, pak nastaví *rPosition* na hodnotu POSITION předchozí položky v seznamu.

```
CObject*& GetPrev(POSITION& rPosition);
const CObject* GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parametry

*rPozice*<br/>
Odkaz na hodnotu POSITION vrácenou předchozím `GetPrev` nebo jiným voláním členské funkce.

### <a name="return-value"></a>Návratová hodnota

Viz popis vrácené hodnoty pro [GetHead](#gethead).

### <a name="remarks"></a>Poznámky

Můžete použít `GetPrev` ve smyčce zpětné iterace, pokud `GetTailPosition` navážete počáteční pozici s voláním nebo `Find`.

Je nutné zajistit, aby hodnota POZICE představovala platnou pozici v seznamu. Pokud je neplatný, pak ladicí verze Knihovny tříd Microsoft Foundation uplatňuje.

Pokud načtený prvek je první v seznamu, pak je nová hodnota *rPosition* nastavena na hodnotu NULL.

> [!NOTE]
> Od knihovny MFC 8.0 const verze této `const CObject*` metody `const CObject*&`se změnil na návrat namísto .  Tato změna byla provedena, aby kompilátor do shody s c++ standard.

V následující tabulce jsou uvedeny `CObList::GetPrev`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[Seznam CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const void* GetPrev( POSITION&` `rPosition` `) const;`|
|[Seznam cstring](../../mfc/reference/cstringlist-class.md)|`CString& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetPrev( POSITION&` `rPosition` `) const;`|

### <a name="example"></a>Příklad

  Viz [CObList::CObList](#coblist) pro výpis `CAge` třídy.

[!code-cpp[NVC_MFCCollections#99](../../mfc/codesnippet/cpp/coblist-class_11.cpp)]

Výsledky tohoto programu jsou následující:

```Output
a CAge at $421C 21
a CAge at $421C 40
```

## <a name="coblistgetsize"></a><a name="getsize"></a>CobList::GetSize

Vrátí počet prvků seznamu.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v seznamu

### <a name="remarks"></a>Poznámky

Volání této metody načíst počet prvků v seznamu.

V následující tabulce jsou uvedeny `CObList::GetSize`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[Seznam CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR GetSize( ) const;**|
|[Seznam cstring](../../mfc/reference/cstringlist-class.md)|**INT_PTR GetSize( ) const;**|

### <a name="example"></a>Příklad

Viz [CObList::CObList](#coblist) pro výpis `CAge` třídy.

[!code-cpp[NVC_MFCCollections#100](../../mfc/codesnippet/cpp/coblist-class_12.cpp)]

## <a name="coblistgettail"></a><a name="gettail"></a>CobList::GetTail

Získá `CObject` ukazatel, který představuje ocas prvek tohoto seznamu.

```
CObject*& GetTail();
const CObject*& GetTail() const;
```

### <a name="return-value"></a>Návratová hodnota

Viz popis vrácené hodnoty pro [GetHead](#gethead).

### <a name="remarks"></a>Poznámky

Před voláním `GetTail`je nutné zajistit, aby seznam nebyl prázdný. Pokud je seznam prázdný, bude uplatněna ladicí verze knihovny tříd Microsoft Foundation. Pomocí [isempty](#isempty) ověřte, zda seznam obsahuje prvky.

V následující tabulce jsou uvedeny `CObList::GetTail`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[Seznam CPtrList](../../mfc/reference/cptrlist-class.md)|**const\* void& GetTail( ) const; neplatné\*& GetTail( );**|
|[Seznam cstring](../../mfc/reference/cstringlist-class.md)|**const CString& GetTail( ) const; CString& GetTail( );**|

### <a name="example"></a>Příklad

Viz [CObList::CObList](#coblist) pro výpis `CAge` třídy.

[!code-cpp[NVC_MFCCollections#101](../../mfc/codesnippet/cpp/coblist-class_13.cpp)]

## <a name="coblistgettailposition"></a><a name="gettailposition"></a>CobList::GettailPozice

Získá pozici ocasprvek tohoto seznamu; **Null,** pokud je seznam prázdný.

```
POSITION GetTailPosition() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota POSITION, kterou lze použít pro iteraci nebo načtení ukazatele objektu; Null, pokud je seznam prázdný.

V následující tabulce jsou uvedeny `CObList::GetTailPosition`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[Seznam CPtrList](../../mfc/reference/cptrlist-class.md)|**POZICE GetTailPosition( ) const;**|
|[Seznam cstring](../../mfc/reference/cstringlist-class.md)|**POZICE GetTailPosition( ) const;**|

### <a name="example"></a>Příklad

Viz [CObList::CObList](#coblist) pro výpis `CAge` třídy.

[!code-cpp[NVC_MFCCollections#102](../../mfc/codesnippet/cpp/coblist-class_14.cpp)]

## <a name="coblistinsertafter"></a><a name="insertafter"></a>CobList::InsertAfter

Přidá prvek do tohoto seznamu za prvek na zadané pozici.

```
POSITION InsertAfter(
    POSITION position,
    CObject* newElement);
```

### <a name="parameters"></a>Parametry

*Pozici*<br/>
Hodnota POSITION vrácená `GetNext`předchozím `GetPrev`voláním , nebo `Find` členské funkce.

*newElement*<br/>
Ukazatel objektu, který má být přidán do tohoto seznamu.

V následující tabulce jsou uvedeny `CObList::InsertAfter`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[Seznam CPtrList](../../mfc/reference/cptrlist-class.md)|**POZICE InsertAfter( pozice pozice** *position* **, void** <strong>\*</strong> `newElement` **);**|
|[Seznam cstring](../../mfc/reference/cstringlist-class.md)|**POZICE InsertAfter( pozice pozice pozice** *position* **, const CString** `newElement` **&);**<br /><br /> **POZICE InsertAfter( pozice** *polohy* **, LPCTSTR** `newElement` **);**|

### <a name="return-value"></a>Návratová hodnota

Hodnota POSITION, která je stejná jako parametr *pozice.*

### <a name="example"></a>Příklad

  Viz [CObList::CObList](#coblist) pro výpis `CAge` třídy.

[!code-cpp[NVC_MFCCollections#103](../../mfc/codesnippet/cpp/coblist-class_15.cpp)]

Výsledky tohoto programu jsou následující:

```Output
InsertAfter example: A CObList with 3 elements
a CAge at $4A44 40
a CAge at $4A64 65
a CAge at $4968 21
```

## <a name="coblistinsertbefore"></a><a name="insertbefore"></a>Coblist::Insertbefore

Přidá prvek do tohoto seznamu před prvek na zadané pozici.

```
POSITION InsertBefore(
    POSITION position,
    CObject* newElement);
```

### <a name="parameters"></a>Parametry

*Pozici*<br/>
Hodnota POSITION vrácená `GetNext`předchozím `GetPrev`voláním , nebo `Find` členské funkce.

*newElement*<br/>
Ukazatel objektu, který má být přidán do tohoto seznamu.

### <a name="return-value"></a>Návratová hodnota

Hodnota POSITION, kterou lze použít pro iteraci nebo načtení ukazatele objektu; Null, pokud je seznam prázdný.

V následující tabulce jsou uvedeny `CObList::InsertBefore`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[Seznam CPtrList](../../mfc/reference/cptrlist-class.md)|**Pozice InsertBefore( pozice pozice** *position* **, void** <strong>\*</strong> `newElement` **);**|
|[Seznam cstring](../../mfc/reference/cstringlist-class.md)|**POZICE InsertBefore( pozice pozice pozice** *position* **, const CString** `newElement` **&);**<br /><br /> **POZICE InsertBefore( Pozice** *pozice* **, LPCTSTR** `newElement` **);**|

### <a name="example"></a>Příklad

  Viz [CObList::CObList](#coblist) pro výpis `CAge` třídy.

[!code-cpp[NVC_MFCCollections#104](../../mfc/codesnippet/cpp/coblist-class_16.cpp)]

Výsledky tohoto programu jsou následující:

```Output
InsertBefore example: A CObList with 3 elements
a CAge at $4AE2 40
a CAge at $4B02 65
a CAge at $49E6 21
```

## <a name="coblistisempty"></a><a name="isempty"></a>Coblist::JePrázdný

Označuje, zda tento seznam neobsahuje žádné prvky.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je tento seznam prázdný; jinak 0.

V následující tabulce jsou uvedeny `CObList::IsEmpty`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[Seznam CPtrList](../../mfc/reference/cptrlist-class.md)|**BOOL IsEmpty( ) const;**|
|[Seznam cstring](../../mfc/reference/cstringlist-class.md)|**BOOL IsEmpty( ) const;**|

### <a name="example"></a>Příklad

  Viz příklad pro [RemoveAll](#removeall).

## <a name="coblistremoveall"></a><a name="removeall"></a>CobList::RemoveAll

Odebere všechny prvky z tohoto seznamu `CObList` a uvolní přidružené paměti.

```cpp
void RemoveAll();
```

### <a name="remarks"></a>Poznámky

Pokud je seznam již prázdný, není generována žádná chyba.

Při odebrání prvků `CObList`z aplikace a odeberete ukazatele objektu ze seznamu. Je vaší odpovědností odstranit samotné objekty.

V následující tabulce jsou uvedeny `CObList::RemoveAll`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[Seznam CPtrList](../../mfc/reference/cptrlist-class.md)|**void RemoveAll( );**|
|[Seznam cstring](../../mfc/reference/cstringlist-class.md)|**void RemoveAll( );**|

### <a name="example"></a>Příklad

Viz [CObList::CObList](#coblist) pro výpis `CAge` třídy.

[!code-cpp[NVC_MFCCollections#105](../../mfc/codesnippet/cpp/coblist-class_17.cpp)]

## <a name="coblistremoveat"></a><a name="removeat"></a>coblist::Removeat

Odebere zadaný prvek z tohoto seznamu.

```cpp
void RemoveAt(POSITION position);
```

### <a name="parameters"></a>Parametry

*Pozici*<br/>
Umístění prvku, který má být odebrán ze seznamu.

### <a name="remarks"></a>Poznámky

Když odeberete prvek `CObList`z a , odeberete ukazatel objektu ze seznamu. Je vaší odpovědností odstranit samotné objekty.

Je nutné zajistit, aby hodnota POZICE představovala platnou pozici v seznamu. Pokud je neplatný, pak ladicí verze Knihovny tříd Microsoft Foundation uplatňuje.

V následující tabulce jsou uvedeny `CObList::RemoveAt`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[Seznam CPtrList](../../mfc/reference/cptrlist-class.md)|**void Removeat( pozice** *polohy* **);**|
|[Seznam cstring](../../mfc/reference/cstringlist-class.md)|**void Removeat( pozice** *polohy* **);**|

### <a name="example"></a>Příklad

  Buďte opatrní při odebírání prvku během iterace seznamu. Následující příklad ukazuje techniku odebrání, která zaručuje platnou hodnotu **POSITION** pro [GetNext](#getnext).

Viz [CObList::CObList](#coblist) pro výpis `CAge` třídy.

[!code-cpp[NVC_MFCCollections#106](../../mfc/codesnippet/cpp/coblist-class_18.cpp)]

Výsledky tohoto programu jsou následující:

`RemoveAt example: A CObList with 2 elements`

`a CAge at $4C1E 65`

`a CAge at $4B22 21`

## <a name="coblistremovehead"></a><a name="removehead"></a>CobList::RemoveHead

Odebere prvek z hlavy seznamu a vrátí na něj ukazatel.

```
CObject* RemoveHead();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel `CObject` dříve v čele seznamu.

### <a name="remarks"></a>Poznámky

Před voláním `RemoveHead`je nutné zajistit, aby seznam nebyl prázdný. Pokud je seznam prázdný, bude uplatněna ladicí verze knihovny tříd Microsoft Foundation. Pomocí [isempty](#isempty) ověřte, zda seznam obsahuje prvky.

V následující tabulce jsou uvedeny `CObList::RemoveHead`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[Seznam CPtrList](../../mfc/reference/cptrlist-class.md)|**void\* RemoveHead( );**|
|[Seznam cstring](../../mfc/reference/cstringlist-class.md)|**CString Removehead( );**|

### <a name="example"></a>Příklad

Viz [CObList::CObList](#coblist) pro výpis `CAge` třídy.

[!code-cpp[NVC_MFCCollections#107](../../mfc/codesnippet/cpp/coblist-class_19.cpp)]

## <a name="coblistremovetail"></a><a name="removetail"></a>CobList::RemoveTail

Odebere prvek z ocasu seznamu a vrátí na něj ukazatel.

```
CObject* RemoveTail();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt, který byl na konci seznamu.

### <a name="remarks"></a>Poznámky

Před voláním `RemoveTail`je nutné zajistit, aby seznam nebyl prázdný. Pokud je seznam prázdný, bude uplatněna ladicí verze knihovny tříd Microsoft Foundation. Pomocí [isempty](#isempty) ověřte, zda seznam obsahuje prvky.

V následující tabulce jsou uvedeny `CObList::RemoveTail`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[Seznam CPtrList](../../mfc/reference/cptrlist-class.md)|**void\* RemoveTail( );**|
|[Seznam cstring](../../mfc/reference/cstringlist-class.md)|**CString Removetail( );**|

### <a name="example"></a>Příklad

Viz [CObList::CObList](#coblist) pro výpis `CAge` třídy.

[!code-cpp[NVC_MFCCollections#108](../../mfc/codesnippet/cpp/coblist-class_20.cpp)]

## <a name="coblistsetat"></a><a name="setat"></a>Coblist::Setat

Nastaví prvek na dané pozici.

```cpp
void SetAt(
    POSITION pos,
    CObject* newElement);
```

### <a name="parameters"></a>Parametry

*Pos*<br/>
POZICE prvku, který má být nastaven.

*newElement*<br/>
Ukazatel, `CObject` který má být zapsán do seznamu.

### <a name="remarks"></a>Poznámky

Proměnná typu POSITION je klíčem k seznamu. Není to stejné jako index a nelze pracovat na position hodnotu sami. `SetAt`zapíše `CObject` ukazatel na zadanou pozici v seznamu.

Je nutné zajistit, aby hodnota POZICE představovala platnou pozici v seznamu. Pokud je neplatný, pak ladicí verze Knihovny tříd Microsoft Foundation uplatňuje.

V následující tabulce jsou uvedeny `CObList::SetAt`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[Seznam CPtrList](../../mfc/reference/cptrlist-class.md)|**void SetAt( POZICE** `pos` **, const CString&** `newElement` **);**|
|[Seznam cstring](../../mfc/reference/cstringlist-class.md)|**void Setat( POZICE** `pos` **, LPCTSTR** `newElement` **);**|

### <a name="example"></a>Příklad

  Viz [CObList::CObList](#coblist) pro výpis `CAge` třídy.

[!code-cpp[NVC_MFCCollections#109](../../mfc/codesnippet/cpp/coblist-class_21.cpp)]

Výsledky tohoto programu jsou následující:

```Output
SetAt example: A CObList with 2 elements
a CAge at $4D98 40
a CAge at $4DB8 65
```

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CStringList – třída](../../mfc/reference/cstringlist-class.md)<br/>
[Třída CPtrList](../../mfc/reference/cptrlist-class.md)
