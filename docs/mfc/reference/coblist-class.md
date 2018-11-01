---
title: Coblist – třída
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
ms.openlocfilehash: 66cc4d28e20ced498e4a434efbe41c3f5db59370
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605202"
---
# <a name="coblist-class"></a>Coblist – třída

fSupports seřazené seznam nejedinečných `CObject` ukazatele přístupné sekvenčně nebo podle hodnoty ukazatele.

## <a name="syntax"></a>Syntaxe

```
class CObList : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CObList::CObList](#coblist)|Vytvoří prázdný seznam pro `CObject` ukazatele.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CObList::AddHead](#addhead)|Přidá k začátku seznamu (novou vedoucí díky) elementu (nebo všechny prvky v jiném seznamu).|
|[CObList::AddTail](#addtail)|Přidá na konec seznamu (umožňuje nové funkce tail) elementu (nebo všechny prvky v jiném seznamu).|
|[CObList::Find](#find)|Získá pozici prvku určeného hodnotou ukazatele.|
|[CObList::FindIndex](#findindex)|Získá pozici prvku určený index založený na nule.|
|[CObList::GetAt](#getat)|Získá prvek na dané pozici.|
|[CObList::GetCount](#getcount)|Vrátí počet prvků v tomto seznamu.|
|[CObList::GetHead](#gethead)|Vrátí element head seznamu (nemůže být prázdný).|
|[CObList::GetHeadPosition](#getheadposition)|Vrátí pozici element head seznamu.|
|[CObList::GetNext](#getnext)|Získá další prvek pro iterace.|
|[CObList::GetPrev](#getprev)|Získá předchozí prvek pro iterace.|
|[CObList::GetSize](#getsize)|Vrátí počet prvků v tomto seznamu.|
|[CObList::GetTail](#gettail)|Vrátí element tail seznamu (nemůže být prázdný).|
|[CObList::GetTailPosition](#gettailposition)|Vrátí pozici prvku tail seznamu.|
|[CObList::InsertAfter](#insertafter)|Vloží nový prvek za danou pozici.|
|[CObList::InsertBefore](#insertbefore)|Vloží nový prvek před danou pozici.|
|[CObList::IsEmpty](#isempty)|Testy pro prázdný seznam podmínku (žádné elementy).|
|[CObList::RemoveAll](#removeall)|Odebere všechny prvky z tohoto seznamu.|
|[CObList::RemoveAt](#removeat)|Odebere element z tohoto seznamu, určené pozici.|
|[CObList::RemoveHead](#removehead)|Odebere element z prvního seznamu.|
|[CObList::RemoveTail](#removetail)|Odebere element z konec seznamu.|
|[CObList::SetAt](#setat)|Nastaví element na dané pozici.|

## <a name="remarks"></a>Poznámky

`CObList` seznamy se chovat jako dvakrát propojené seznamy.

Proměnné typu pozice je klíč pro seznam. POZICE proměnné můžete použít jako iterátor procházet seznamem postupně i záložku pro uchování na místě. Pozice není stejný jako index, ale.

Vložení elementu je velmi rychlé zpracování v čele seznamu, na konci a známé pozici. Sekvenčního vyhledávání, je nutné při hledání elementu podle hodnoty nebo index. Toto vyhledávání může být pomalé, pokud je dlouhý seznam.

`CObList` zahrnuje IMPLEMENT_SERIAL – makro na podporu serializace a výpis z jeho prvků. Pokud seznam `CObject` ukazatele je uložit do archivu, s operátorem vložení přetížené nebo se `Serialize` členské funkce se každý `CObject` zase serializuje jako element.

Pokud potřebujete s výpisem paměti jednotlivých `CObject` prvky v seznamu, je nutné nastavit hloubky kontextu výpisu stavu systému na 1 nebo větší.

Když `CObList` odstranění objektu nebo při jeho prvky jsou odebrány, pouze `CObject` ukazatele jsou odebrány, nikoliv objekty, které odkazují.

Můžete odvozovat vlastní třídy z `CObList`. Nová třída seznam navržených pro ukládání ukazatelů na objekty odvozené z `CObject`, přidá nové datové členy a nových funkcí člena. Mějte na paměti, že v rozevíracím seznamu není striktně typově bezpečný, protože umožňuje vložení žádné `CObject` ukazatele.

> [!NOTE]
>  Je nutné použít [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) – makro v implementaci vaší odvozené třídy, pokud chcete serializovat seznamu.

Další informace o používání `CObList`, najdete v článku [kolekce](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CObList`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcoll.h

##  <a name="addhead"></a>  CObList::AddHead

Přidá nový prvek nebo seznam elementů na začátku tohoto seznamu.

```
POSITION AddHead(CObject* newElement);
void AddHead(CObList* pNewList);
```

### <a name="parameters"></a>Parametry

*newElement*<br/>
`CObject` Ukazatel přidávané do tohoto seznamu.

*pNewList*<br/>
Ukazatel na jiný `CObList` seznamu. Prvky v *pNewList* budou přidány do tohoto seznamu.

### <a name="return-value"></a>Návratová hodnota

První verze vrátí hodnotu pozice nově vložený prvek.

Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::AddHead`.

|Třída|Členská funkce|
|-----------|---------------------|
|[Cptrlist –](../../mfc/reference/cptrlist-class.md)|**POZICE AddHead (void** <strong>\*</strong> `newElement` **);**<br /><br /> **void AddHead (cptrlist –** <strong>\*</strong> `pNewList` **);**|
|[CStringList –](../../mfc/reference/cstringlist-class.md)|**POZICE AddHead (const CString &** `newElement` **);**<br /><br /> **POZICE AddHead (LPCTSTR** `newElement` **);**<br /><br /> **void AddHead (CStringList** <strong>\*</strong> `pNewList` **);**|

### <a name="remarks"></a>Poznámky

Seznam může být prázdný před provedením operace.

### <a name="example"></a>Příklad

  Zobrazit [CObList::CObList](#coblist) seznam `CAge` třídy.

[!code-cpp[NVC_MFCCollections#89](../../mfc/codesnippet/cpp/coblist-class_1.cpp)]

Výsledky z této aplikace jsou následující:

```Output
AddHead example: A CObList with 2 elements
a CAge at $44A8 40
a CAge at $442A 21
```

##  <a name="addtail"></a>  CObList::AddTail

Přidá nový prvek nebo seznam prvků na konci tohoto seznamu.

```
POSITION AddTail(CObject* newElement);
void AddTail(CObList* pNewList);
```

### <a name="parameters"></a>Parametry

*newElement*<br/>
`CObject` Ukazatel přidávané do tohoto seznamu.

*pNewList*<br/>
Ukazatel na jiný `CObList` seznamu. Prvky v *pNewList* budou přidány do tohoto seznamu.

### <a name="return-value"></a>Návratová hodnota

První verze vrátí hodnotu pozice nově vložený prvek.

### <a name="remarks"></a>Poznámky

Seznam může být prázdný před provedením operace.

Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::AddTail`.

|Třída|Členská funkce|
|-----------|---------------------|
|[Cptrlist –](../../mfc/reference/cptrlist-class.md)|**Addtail – pozice (void** <strong>\*</strong> `newElement` **);**<br /><br /> **addtail – void (cptrlist –** <strong>\*</strong> `pNewList` **);**|
|[CStringList –](../../mfc/reference/cstringlist-class.md)|**Addtail – pozice (const CString &** `newElement` **);**<br /><br /> **Addtail – pozice (LPCTSTR** `newElement` **);**<br /><br /> **addtail – void (CStringList** <strong>\*</strong> `pNewList` **);**|

### <a name="example"></a>Příklad

  Zobrazit [CObList::CObList](#coblist) seznam `CAge` třídy.

[!code-cpp[NVC_MFCCollections#90](../../mfc/codesnippet/cpp/coblist-class_2.cpp)]

Výsledky z této aplikace jsou následující:

```Output
AddTail example: A CObList with 2 elements
a CAge at $444A 21
a CAge at $4526 40
```

##  <a name="coblist"></a>  CObList::CObList

Vytvoří prázdnou `CObject` seznamu ukazatele.

```
CObList(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Parametry

*nBlockSize*<br/>
Členitost přidělení paměti pro rozšíření seznamu.

### <a name="remarks"></a>Poznámky

S růstem seznamu je paměť přidělena v jednotkách, které *nBlockSize* položky. Pokud selže přidělování paměti `CMemoryException` je vyvolána výjimka.

Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::CObList`.

|Třída|Členská funkce|
|-----------|---------------------|
|[Cptrlist –](../../mfc/reference/cptrlist-class.md)|**Cptrlist – (INT_PTR** `nBlockSize` **= 10);**|
|[CStringList –](../../mfc/reference/cstringlist-class.md)|**CStringList (INT_PTR** `nBlockSize` **= 10);**|

### <a name="example"></a>Příklad

  Níže je seznam `CObject`-odvozené třídy `CAge` používá ve všech příkladech kolekce:

[!code-cpp[NVC_MFCCollections#91](../../mfc/codesnippet/cpp/coblist-class_3.h)]

Níže je příklad `CObList` využití konstruktor:

[!code-cpp[NVC_MFCCollections#92](../../mfc/codesnippet/cpp/coblist-class_4.cpp)]

##  <a name="find"></a>  CObList::Find

Prohledává postupně seznamu vyhledejte první `CObject` ukazatel odpovídající zadané `CObject` ukazatele.

```
POSITION Find(
    CObject* searchValue,
    POSITION startAfter = NULL) const;
```

### <a name="parameters"></a>Parametry

*searchValue*<br/>
Ukazatel objektu, který má být vyhledána v tomto seznamu.

*startAfter*<br/>
Počáteční pozice pro vyhledávání.

### <a name="return-value"></a>Návratová hodnota

POZICE hodnotu, která lze použít pro iteraci nebo načtení objektu ukazatele; Hodnota NULL, pokud objekt nebyl nalezen.

### <a name="remarks"></a>Poznámky

Všimněte si, že jsou porovnány hodnoty ukazatele, nikoli jejich obsah objektů.

Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::Find`.

|Třída|Členská funkce|
|-----------|---------------------|
|[Cptrlist –](../../mfc/reference/cptrlist-class.md)|**Hledání pozice (void** <strong>\*</strong> `searchValue` **, pozice** `startAfter` **= NULL) const;**|
|[CStringList –](../../mfc/reference/cstringlist-class.md)|**Hledání pozice (LPCTSTR** `searchValue` **, pozice** `startAfter` **= NULL) const;**|

### <a name="example"></a>Příklad

Zobrazit [CObList::CObList](#coblist) seznam `CAge` třídy.

[!code-cpp[NVC_MFCCollections#93](../../mfc/codesnippet/cpp/coblist-class_5.cpp)]

##  <a name="findindex"></a>  CObList::FindIndex

Používá hodnotu *nIndex* jako index do seznamu.

```
POSITION FindIndex(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index založený na nule prvku seznam, který chcete najít.

### <a name="return-value"></a>Návratová hodnota

POZICE hodnotu, která lze použít pro iteraci nebo načtení objektu ukazatele; Hodnota NULL, pokud *nIndex* je moc velká. (Rozhraní framework generuje kontrolní výraz Pokud *nIndex* je záporná.)

### <a name="remarks"></a>Poznámky

Spuštěním kontroly sekvenční od začátku seznamu zastavování na *n*tý prvek.

Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::FindIndex`.

|Třída|Členská funkce|
|-----------|---------------------|
|[Cptrlist –](../../mfc/reference/cptrlist-class.md)|**Findindex – pozice (INT_PTR** `nIndex` **) const;**|
|[CStringList –](../../mfc/reference/cstringlist-class.md)|**Findindex – pozice (INT_PTR** `nIndex` **) const;**|

### <a name="example"></a>Příklad

Zobrazit [CObList::CObList](#coblist) seznam `CAge` třídy.

[!code-cpp[NVC_MFCCollections#94](../../mfc/codesnippet/cpp/coblist-class_6.cpp)]

##  <a name="getat"></a>  CObList::GetAt

Proměnné typu pozice je klíč pro seznam.

```
CObject*& GetAt(POSITION position);
const CObject*& GetAt(POSITION position) const;
```

### <a name="parameters"></a>Parametry

*Pozice*<br/>
Hodnota pozice vrácené předchozím `GetHeadPosition` nebo `Find` volání členské funkce.

### <a name="return-value"></a>Návratová hodnota

Naleznete v popisu návratovou hodnotu pro [GetHead](#gethead).

### <a name="remarks"></a>Poznámky

Není stejný jako index a nemůžete pracovat na základě hodnoty pozice sami. `GetAt` načte `CObject` ukazatel spojené s danou pozici.

Ujistěte se, že hodnota pozice představuje platná pozice v seznamu. Pokud je neplatná, ladicí verze knihovny Microsoft Foundation Class se vyhodnotí.

Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::GetAt`.

|Třída|Členská funkce|
|-----------|---------------------|
|[Cptrlist –](../../mfc/reference/cptrlist-class.md)|**Const void\*& GetAt (pozice** *pozice* **) const;**<br /><br /> **void\*& GetAt (pozice** *pozice* **);**|
|[CStringList –](../../mfc/reference/cstringlist-class.md)|**Const CString & GetAt (pozice** *pozice* **) const;**<br /><br /> **CString – & GetAt (pozice** *pozice* **);**|

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [findindex –](#findindex).

##  <a name="getcount"></a>  CObList::GetCount

Získá počet elementů v tomto seznamu.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Celočíselnou hodnotu obsahující počet prvků.

Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::GetCount`.

|Třída|Členská funkce|
|-----------|---------------------|
|[Cptrlist –](../../mfc/reference/cptrlist-class.md)|**INT_PTR GetCount (const;)**|
|[CStringList –](../../mfc/reference/cstringlist-class.md)|**INT_PTR GetCount (const;)**|

### <a name="example"></a>Příklad

Zobrazit [CObList::CObList](#coblist) seznam `CAge` třídy.

[!code-cpp[NVC_MFCCollections#95](../../mfc/codesnippet/cpp/coblist-class_7.cpp)]

##  <a name="gethead"></a>  CObList::GetHead

Získá `CObject` ukazatel, který reprezentuje element head tohoto seznamu.

```
CObject*& GetHead();
const CObject*& GetHead() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud v seznamu se přistupuje přes ukazatel `const CObList`, pak `GetHead` vrátí `CObject` ukazatel. To umožňuje funkce, která se použije pouze na pravé straně příkazu přiřazení a tedy chrání před změnou seznamu.

Pokud se v seznamu přistupuje přímo nebo prostřednictvím ukazatele na `CObList`, pak `GetHead` vrátí odkaz na `CObject` ukazatele. To umožňuje funkce, která se použije na obou stranách příkazu přiřazení a tím umožňuje položky seznamu, který má být upraven.

### <a name="remarks"></a>Poznámky

Ujistěte se, že seznam není prázdný před voláním `GetHead`. Pokud je seznam prázdný, pak vyhodnotí ladicí verze knihovny Microsoft Foundation Class. Použití [IsEmpty](#isempty) ověřit, zda seznam obsahuje prvky.

Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::GetHead`.

|Třída|Členská funkce|
|-----------|---------------------|
|[Cptrlist –](../../mfc/reference/cptrlist-class.md)|**Const void\*& () GetHead const; void\*& GetHead ();**|
|[CStringList –](../../mfc/reference/cstringlist-class.md)|**Const CString & GetHead () const; CString – & GetHead ();**|

### <a name="example"></a>Příklad

Zobrazit [CObList::CObList](#coblist) seznam `CAge` třídy.

Následující příklad ukazuje použití `GetHead` na levé straně příkazu přiřazení.

[!code-cpp[NVC_MFCCollections#96](../../mfc/codesnippet/cpp/coblist-class_8.cpp)]

##  <a name="getheadposition"></a>  CObList::GetHeadPosition

Získá pozici element head tohoto seznamu.

```
POSITION GetHeadPosition() const;
```

### <a name="return-value"></a>Návratová hodnota

POZICE hodnotu, která lze použít pro iteraci nebo načtení objektu ukazatele; Hodnota NULL, pokud je seznam prázdný.

Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::GetHeadPosition`.

|Třída|Členská funkce|
|-----------|---------------------|
|[Cptrlist –](../../mfc/reference/cptrlist-class.md)|**POZICE GetHeadPosition (const;)**|
|[CStringList –](../../mfc/reference/cstringlist-class.md)|**POZICE GetHeadPosition (const;)**|

### <a name="example"></a>Příklad

Zobrazit [CObList::CObList](#coblist) seznam `CAge` třídy.

[!code-cpp[NVC_MFCCollections#97](../../mfc/codesnippet/cpp/coblist-class_9.cpp)]

##  <a name="getnext"></a>  CObList::GetNext

Získá seznam prvek identifikovaný *rposition*, pak nastaví *rposition* k `POSITION` hodnotu další položky v seznamu.

```
CObject*& GetNext(POSITION& rPosition);
const CObject* GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parametry

*rposition.*<br/>
Odkaz na POZICI hodnotu vrácenou předchozím `GetNext`, `GetHeadPosition`, nebo jiné členské funkce volání.

### <a name="return-value"></a>Návratová hodnota

Naleznete v popisu návratovou hodnotu pro [GetHead](#gethead).

### <a name="remarks"></a>Poznámky

Můžete použít `GetNext` v dopředné iteraci smyčky, Pokud zavedete počáteční pozici voláním `GetHeadPosition` nebo `Find`.

Ujistěte se, že hodnota pozice představuje platná pozice v seznamu. Pokud je neplatná, ladicí verze knihovny Microsoft Foundation Class se vyhodnotí.

Pokud je načtený element poslední v seznamu, pak nová hodnota *rposition* nastaven na hodnotu NULL.

Je možné odebrat element během iterace. Podívejte se na příklad pro [RemoveAt](#removeat).

> [!NOTE]
>  Od verze MFC 8.0 změnila const verze této metody vrátit `const CObject*` místo `const CObject*&`.  Tato změna byla provedena, aby kompilátor v souladu s C++ standard.

Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::GetNext`.

|Třída|Členská funkce|
|-----------|---------------------|
|[Cptrlist –](../../mfc/reference/cptrlist-class.md)|`void*& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const void* GetNext( POSITION&` `rPosition` `) const;`|
|[CStringList –](../../mfc/reference/cstringlist-class.md)|`CString& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetNext( POSITION&` `rPosition` `) const;`|

### <a name="example"></a>Příklad

  Zobrazit [CObList::CObList](#coblist) seznam `CAge` třídy.

[!code-cpp[NVC_MFCCollections#98](../../mfc/codesnippet/cpp/coblist-class_10.cpp)]

Výsledky z této aplikace jsou následující:

```Output
a CAge at $479C 40
a CAge at $46C0 21
```

##  <a name="getprev"></a>  CObList::GetPrev

Získá seznam prvek identifikovaný *rposition*, pak nastaví *rposition* pozice hodnotu předchozí položka v seznamu.

```
CObject*& GetPrev(POSITION& rPosition);
const CObject* GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parametry

*rposition.*<br/>
Odkaz na POZICI hodnotu vrácenou předchozím `GetPrev` nebo jiné členské funkce volání.

### <a name="return-value"></a>Návratová hodnota

Naleznete v popisu návratovou hodnotu pro [GetHead](#gethead).

### <a name="remarks"></a>Poznámky

Můžete použít `GetPrev` v reverzní iteraci smyčky, Pokud zavedete počáteční pozici voláním `GetTailPosition` nebo `Find`.

Ujistěte se, že hodnota pozice představuje platná pozice v seznamu. Pokud je neplatná, ladicí verze knihovny Microsoft Foundation Class se vyhodnotí.

Je-li načíst prvek je první v seznamu, pak nová hodnota *rposition* nastaven na hodnotu NULL.

> [!NOTE]
>  Od verze MFC 8.0 změnila const verze této metody vrátit `const CObject*` místo `const CObject*&`.  Tato změna byla provedena, aby kompilátor v souladu s C++ standard.

Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::GetPrev`.

|Třída|Členská funkce|
|-----------|---------------------|
|[Cptrlist –](../../mfc/reference/cptrlist-class.md)|`void*& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const void* GetPrev( POSITION&` `rPosition` `) const;`|
|[CStringList –](../../mfc/reference/cstringlist-class.md)|`CString& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetPrev( POSITION&` `rPosition` `) const;`|

### <a name="example"></a>Příklad

  Zobrazit [CObList::CObList](#coblist) seznam `CAge` třídy.

[!code-cpp[NVC_MFCCollections#99](../../mfc/codesnippet/cpp/coblist-class_11.cpp)]

Výsledky z této aplikace jsou následující:

```Output
a CAge at $421C 21
a CAge at $421C 40
```

##  <a name="getsize"></a>  CObList::GetSize

Vrátí počet prvků seznamu.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v seznamu.

### <a name="remarks"></a>Poznámky

Voláním této metody lze načíst počet prvků v seznamu.

Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::GetSize`.

|Třída|Členská funkce|
|-----------|---------------------|
|[Cptrlist –](../../mfc/reference/cptrlist-class.md)|**INT_PTR getsize – (const;)**|
|[CStringList –](../../mfc/reference/cstringlist-class.md)|**INT_PTR getsize – (const;)**|

### <a name="example"></a>Příklad

Zobrazit [CObList::CObList](#coblist) seznam `CAge` třídy.

[!code-cpp[NVC_MFCCollections#100](../../mfc/codesnippet/cpp/coblist-class_12.cpp)]

##  <a name="gettail"></a>  CObList::GetTail

Získá `CObject` ukazatel, který reprezentuje element tail tohoto seznamu.

```
CObject*& GetTail();
const CObject*& GetTail() const;
```

### <a name="return-value"></a>Návratová hodnota

Naleznete v popisu návratovou hodnotu pro [GetHead](#gethead).

### <a name="remarks"></a>Poznámky

Ujistěte se, že seznam není prázdný před voláním `GetTail`. Pokud je seznam prázdný, pak vyhodnotí ladicí verze knihovny Microsoft Foundation Class. Použití [IsEmpty](#isempty) ověřit, zda seznam obsahuje prvky.

Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::GetTail`.

|Třída|Členská funkce|
|-----------|---------------------|
|[Cptrlist –](../../mfc/reference/cptrlist-class.md)|**Const void\*& () GetTail const; void\*& GetTail ();**|
|[CStringList –](../../mfc/reference/cstringlist-class.md)|**Const CString & GetTail () const; CString – & GetTail ();**|

### <a name="example"></a>Příklad

Zobrazit [CObList::CObList](#coblist) seznam `CAge` třídy.

[!code-cpp[NVC_MFCCollections#101](../../mfc/codesnippet/cpp/coblist-class_13.cpp)]

##  <a name="gettailposition"></a>  CObList::GetTailPosition

Získá pozici prvku tail tohoto seznamu; **NULL** Pokud je seznam prázdný.

```
POSITION GetTailPosition() const;
```

### <a name="return-value"></a>Návratová hodnota

POZICE hodnotu, která lze použít pro iteraci nebo načtení objektu ukazatele; Hodnota NULL, pokud je seznam prázdný.

Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::GetTailPosition`.

|Třída|Členská funkce|
|-----------|---------------------|
|[Cptrlist –](../../mfc/reference/cptrlist-class.md)|**POZICE GetTailPosition (const;)**|
|[CStringList –](../../mfc/reference/cstringlist-class.md)|**POZICE GetTailPosition (const;)**|

### <a name="example"></a>Příklad

Zobrazit [CObList::CObList](#coblist) seznam `CAge` třídy.

[!code-cpp[NVC_MFCCollections#102](../../mfc/codesnippet/cpp/coblist-class_14.cpp)]

##  <a name="insertafter"></a>  CObList::InsertAfter

Přidá prvek do tohoto seznamu za elementem na zadané pozici.

```
POSITION InsertAfter(
    POSITION position,
    CObject* newElement);
```

### <a name="parameters"></a>Parametry

*Pozice*<br/>
Hodnota pozice vrácené předchozím `GetNext`, `GetPrev`, nebo `Find` volání členské funkce.

*newElement*<br/>
Ukazatel objektu přidávané do tohoto seznamu.

Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::InsertAfter`.

|Třída|Členská funkce|
|-----------|---------------------|
|[Cptrlist –](../../mfc/reference/cptrlist-class.md)|**POZICE InsertAfter (pozice** *pozice* **, void** <strong>\*</strong> `newElement` **);**|
|[CStringList –](../../mfc/reference/cstringlist-class.md)|**POZICE InsertAfter (pozice** *pozice* **, const CString &** `newElement` **);**<br /><br /> **POZICE InsertAfter (pozice** *pozice* **, LPCTSTR** `newElement` **);**|

### <a name="return-value"></a>Návratová hodnota

Hodnota pozice, který je stejný jako *pozice* parametru.

### <a name="example"></a>Příklad

  Zobrazit [CObList::CObList](#coblist) seznam `CAge` třídy.

[!code-cpp[NVC_MFCCollections#103](../../mfc/codesnippet/cpp/coblist-class_15.cpp)]

Výsledky z této aplikace jsou následující:

```Output
InsertAfter example: A CObList with 3 elements
a CAge at $4A44 40
a CAge at $4A64 65
a CAge at $4968 21
```

##  <a name="insertbefore"></a>  CObList::InsertBefore

Přidá prvek do tohoto seznamu před elementem na zadané pozici.

```
POSITION InsertBefore(
    POSITION position,
    CObject* newElement);
```

### <a name="parameters"></a>Parametry

*Pozice*<br/>
Hodnota pozice vrácené předchozím `GetNext`, `GetPrev`, nebo `Find` volání členské funkce.

*newElement*<br/>
Ukazatel objektu přidávané do tohoto seznamu.

### <a name="return-value"></a>Návratová hodnota

POZICE hodnotu, která lze použít pro iteraci nebo načtení objektu ukazatele; Hodnota NULL, pokud je seznam prázdný.

Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::InsertBefore`.

|Třída|Členská funkce|
|-----------|---------------------|
|[Cptrlist –](../../mfc/reference/cptrlist-class.md)|**POZICE InsertBefore (pozice** *pozice* **, void** <strong>\*</strong> `newElement` **);**|
|[CStringList –](../../mfc/reference/cstringlist-class.md)|**POZICE InsertBefore (pozice** *pozice* **, const CString &** `newElement` **);**<br /><br /> **POZICE InsertBefore (pozice** *pozice* **, LPCTSTR** `newElement` **);**|

### <a name="example"></a>Příklad

  Zobrazit [CObList::CObList](#coblist) seznam `CAge` třídy.

[!code-cpp[NVC_MFCCollections#104](../../mfc/codesnippet/cpp/coblist-class_16.cpp)]

Výsledky z této aplikace jsou následující:

```Output
InsertBefore example: A CObList with 3 elements
a CAge at $4AE2 40
a CAge at $4B02 65
a CAge at $49E6 21
```

##  <a name="isempty"></a>  CObList::IsEmpty

Určuje, zda tento seznam neobsahuje žádné elementy.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je tento seznam prázdný; jinak 0.

Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::IsEmpty`.

|Třída|Členská funkce|
|-----------|---------------------|
|[Cptrlist –](../../mfc/reference/cptrlist-class.md)|**BOOL IsEmpty (const;)**|
|[CStringList –](../../mfc/reference/cstringlist-class.md)|**BOOL IsEmpty (const;)**|

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [RemoveAll](#removeall).

##  <a name="removeall"></a>  CObList::RemoveAll

Odebere všechny prvky v tomto seznamu a uvolní přidruženého `CObList` paměti.

```
void RemoveAll();
```

### <a name="remarks"></a>Poznámky

Pokud už je seznam prázdný, nevygeneruje se žádná chyba.

Když odeberete elementy ze `CObList`, odeberte objekt ukazatele ze seznamu. Je vaší odpovědností, abyste odstranit samotných objektech.

Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::RemoveAll`.

|Třída|Členská funkce|
|-----------|---------------------|
|[Cptrlist –](../../mfc/reference/cptrlist-class.md)|**void (RemoveAll);**|
|[CStringList –](../../mfc/reference/cstringlist-class.md)|**void (RemoveAll);**|

### <a name="example"></a>Příklad

Zobrazit [CObList::CObList](#coblist) seznam `CAge` třídy.

[!code-cpp[NVC_MFCCollections#105](../../mfc/codesnippet/cpp/coblist-class_17.cpp)]

##  <a name="removeat"></a>  CObList::RemoveAt

Odebere zadaný prvek z tohoto seznamu.

```
void RemoveAt(POSITION position);
```

### <a name="parameters"></a>Parametry

*Pozice*<br/>
Pozice prvku, který chcete odebrat ze seznamu.

### <a name="remarks"></a>Poznámky

Když odeberete prvek z `CObList`, odeberte ukazatel na objekt ze seznamu. Je vaší odpovědností, abyste odstranit samotných objektech.

Ujistěte se, že hodnota pozice představuje platná pozice v seznamu. Pokud je neplatná, ladicí verze knihovny Microsoft Foundation Class se vyhodnotí.

Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::RemoveAt`.

|Třída|Členská funkce|
|-----------|---------------------|
|[Cptrlist –](../../mfc/reference/cptrlist-class.md)|**void RemoveAt (pozice** *pozice* **);**|
|[CStringList –](../../mfc/reference/cstringlist-class.md)|**void RemoveAt (pozice** *pozice* **);**|

### <a name="example"></a>Příklad

  Buďte opatrní při odstranění prvku během iterace seznamu. Následující příklad ukazuje odstranění technika, která zaručuje platný **pozice** hodnota [GetNext](#getnext).

Zobrazit [CObList::CObList](#coblist) seznam `CAge` třídy.

[!code-cpp[NVC_MFCCollections#106](../../mfc/codesnippet/cpp/coblist-class_18.cpp)]

Výsledky z této aplikace jsou následující:

`RemoveAt example: A CObList with 2 elements`

`a CAge at $4C1E 65`

`a CAge at $4B22 21`

##  <a name="removehead"></a>  CObList::RemoveHead

Odebere element z prvního seznamu a vrátí ukazatel na něj.

```
CObject* RemoveHead();
```

### <a name="return-value"></a>Návratová hodnota

`CObject` Ukazatel dříve na začátku seznamu.

### <a name="remarks"></a>Poznámky

Ujistěte se, že seznam není prázdný před voláním `RemoveHead`. Pokud je seznam prázdný, pak vyhodnotí ladicí verze knihovny Microsoft Foundation Class. Použití [IsEmpty](#isempty) ověřit, zda seznam obsahuje prvky.

Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::RemoveHead`.

|Třída|Členská funkce|
|-----------|---------------------|
|[Cptrlist –](../../mfc/reference/cptrlist-class.md)|**void\* RemoveHead ();**|
|[CStringList –](../../mfc/reference/cstringlist-class.md)|**CString – RemoveHead ();**|

### <a name="example"></a>Příklad

Zobrazit [CObList::CObList](#coblist) seznam `CAge` třídy.

[!code-cpp[NVC_MFCCollections#107](../../mfc/codesnippet/cpp/coblist-class_19.cpp)]

##  <a name="removetail"></a>  CObList::RemoveTail

Odebere element z konec seznamu a vrátí ukazatel na něj.

```
CObject* RemoveTail();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt, který byl na konci seznamu.

### <a name="remarks"></a>Poznámky

Ujistěte se, že seznam není prázdný před voláním `RemoveTail`. Pokud je seznam prázdný, pak vyhodnotí ladicí verze knihovny Microsoft Foundation Class. Použití [IsEmpty](#isempty) ověřit, zda seznam obsahuje prvky.

Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::RemoveTail`.

|Třída|Členská funkce|
|-----------|---------------------|
|[Cptrlist –](../../mfc/reference/cptrlist-class.md)|**void\* RemoveTail ();**|
|[CStringList –](../../mfc/reference/cstringlist-class.md)|**CString – RemoveTail ();**|

### <a name="example"></a>Příklad

Zobrazit [CObList::CObList](#coblist) seznam `CAge` třídy.

[!code-cpp[NVC_MFCCollections#108](../../mfc/codesnippet/cpp/coblist-class_20.cpp)]

##  <a name="setat"></a>  CObList::SetAt

Nastaví element na dané pozici.

```
void SetAt(
    POSITION pos,
    CObject* newElement);
```

### <a name="parameters"></a>Parametry

*POS*<br/>
Pozice prvku, který chcete nastavit.

*newElement*<br/>
`CObject` Ukazatel k zápisu do seznamu.

### <a name="remarks"></a>Poznámky

Proměnné typu pozice je klíč pro seznam. Není stejný jako index a nemůžete pracovat na základě hodnoty pozice sami. `SetAt` zapíše `CObject` ukazatel na určenou pozici v seznamu.

Ujistěte se, že hodnota pozice představuje platná pozice v seznamu. Pokud je neplatná, ladicí verze knihovny Microsoft Foundation Class se vyhodnotí.

Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::SetAt`.

|Třída|Členská funkce|
|-----------|---------------------|
|[Cptrlist –](../../mfc/reference/cptrlist-class.md)|**void SetAt (pozice** `pos` **, const CString &** `newElement` **);**|
|[CStringList –](../../mfc/reference/cstringlist-class.md)|**void SetAt (pozice** `pos` **, LPCTSTR** `newElement` **);**|

### <a name="example"></a>Příklad

  Zobrazit [CObList::CObList](#coblist) seznam `CAge` třídy.

[!code-cpp[NVC_MFCCollections#109](../../mfc/codesnippet/cpp/coblist-class_21.cpp)]

Výsledky z této aplikace jsou následující:

```Output
SetAt example: A CObList with 2 elements
a CAge at $4D98 40
a CAge at $4DB8 65
```

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CStringList – třída](../../mfc/reference/cstringlist-class.md)<br/>
[CPtrList – třída](../../mfc/reference/cptrlist-class.md)
