---
title: CObList – třída
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
ms.openlocfilehash: 2fc3a3643c675394de555f1411030e278bcee775
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416870"
---
# <a name="coblist-class"></a>CObList – třída

fSupports seřazené seznamy nejedinečných ukazatelů `CObject` přístupných postupně nebo podle hodnoty ukazatele.

## <a name="syntax"></a>Syntaxe

```
class CObList : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CObList::CObList](#coblist)|Vytvoří prázdný seznam pro ukazatele `CObject`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CObList::AddHead](#addhead)|Přidá prvek (nebo všechny prvky v jiném seznamu) do záhlaví seznamu (vytvoří novou hlavu).|
|[CObList:: AddTail –](#addtail)|Přidá prvek (nebo všechny prvky v jiném seznamu) na konec seznamu (vytvoří nový konec).|
|[CObList:: Find](#find)|Získá pozici prvku určeného hodnotou ukazatele.|
|[CObList:: FindIndex –](#findindex)|Získá pozici prvku určeného indexem založeným na nule.|
|[CObList::GetAt](#getat)|Získá prvek na dané pozici.|
|[CObList:: GetCount](#getcount)|Vrátí počet prvků v tomto seznamu.|
|[CObList:: GetHead](#gethead)|Vrátí element head seznamu (nemůže být prázdný).|
|[CObList::GetHeadPosition](#getheadposition)|Vrátí pozici elementu Head v seznamu.|
|[CObList:: GetNext](#getnext)|Získá další prvek pro iteraci.|
|[CObList:: getpředchozí](#getprev)|Získá předchozí prvek pro iteraci.|
|[CObList:: GetSize](#getsize)|Vrátí počet prvků v tomto seznamu.|
|[CObList:: GetTail](#gettail)|Vrátí element Tail seznamu (nemůže být prázdný).|
|[CObList::GetTailPosition](#gettailposition)|Vrátí pozici koncového prvku seznamu.|
|[CObList::InsertAfter](#insertafter)|Vloží nový prvek za danou pozici.|
|[CObList::InsertBefore](#insertbefore)|Vloží nový prvek před danou pozici.|
|[CObList::-Empty](#isempty)|Testuje podmínku prázdného seznamu (žádné elementy).|
|[CObList::RemoveAll](#removeall)|Odebere všechny prvky z tohoto seznamu.|
|[CObList:: funkce RemoveAt](#removeat)|Odebere prvek z tohoto seznamu, který je určen pozicí.|
|[CObList::RemoveHead](#removehead)|Odebere prvek ze záhlaví seznamu.|
|[CObList::RemoveTail](#removetail)|Odebere prvek ze strany seznamu.|
|[CObList::SetAt](#setat)|Nastaví prvek na dané pozici.|

## <a name="remarks"></a>Poznámky

seznam `CObList` se chová jako seznamy s obousměrným odkazem.

Proměnná pozice typu je klíč pro seznam. Proměnnou pozice lze použít jak jako iterátor, aby se seznam přesměroval postupně a jako záložka pro uložení místa. Pozice však není stejná jako index, ale.

Vložení elementu je velmi rychlé v hlavičce seznamu, na konci a na známém místě. Sekvenční hledání je nezbytné pro vyhledání prvku podle hodnoty nebo indexu. Toto hledání může být pomalé, pokud je seznam dlouhý.

`CObList` zahrnuje makro IMPLEMENT_SERIAL pro podporu serializace a dumpingu jeho prvků. Pokud je seznam ukazatelů `CObject` uložen do archivu, buď pomocí přetíženého operátoru vložení nebo pomocí `Serialize` členské funkce, je každý prvek `CObject` serializován.

Pokud potřebujete výpis z jednotlivých prvků `CObject` v seznamu, je nutné nastavit hloubku kontextu výpisu na hodnotu 1 nebo vyšší.

Když je odstraněn objekt `CObList` nebo když jsou jeho prvky odebrány, jsou odebrány pouze ukazatele `CObject`, nikoli objekty, na které odkazují.

Z `CObList`můžete odvodit vlastní třídy. Vaše nová třída seznamu navržená tak, aby obsahovala ukazatele na objekty odvozené od `CObject`, přidává nové datové členy a nové členské funkce. Všimněte si, že výsledný seznam není striktně typově bezpečný, protože umožňuje vložení libovolného `CObject` ukazatele.

> [!NOTE]
>  V případě, že máte v úmyslu seznam serializovat, je nutné použít makro [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) v implementaci odvozené třídy.

Další informace o používání `CObList`najdete v článku [kolekce](../../mfc/collections.md)článků.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

`CObList`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcoll. h

##  <a name="addhead"></a>CObList::AddHead

Přidá nový prvek nebo seznam prvků na záhlaví tohoto seznamu.

```
POSITION AddHead(CObject* newElement);
void AddHead(CObList* pNewList);
```

### <a name="parameters"></a>Parametry

*newElement*<br/>
`CObject` ukazatel, který se má přidat do tohoto seznamu.

*pNewList*<br/>
Ukazatel na jiný seznam `CObList`. Prvky v *pNewList* budou přidány do tohoto seznamu.

### <a name="return-value"></a>Návratová hodnota

První verze vrátí hodnotu pozice nově vloženého prvku.

V následující tabulce jsou uvedeny jiné členské funkce, které jsou podobné `CObList::AddHead`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Pozice AddHead (void** <strong>\*</strong> `newElement` **);**<br /><br /> **void AddHead (CPtrList** <strong>\*</strong> `pNewList` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**AddHead pozice (const CString &** `newElement` **);**<br /><br /> **Pozice AddHead (LPCTSTR** `newElement` **);**<br /><br /> **void AddHead (CStringList** <strong>\*</strong> `pNewList` **);**|

### <a name="remarks"></a>Poznámky

Seznam může být před operací prázdný.

### <a name="example"></a>Příklad

  Seznam `CAge` třídy naleznete v tématu [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#89](../../mfc/codesnippet/cpp/coblist-class_1.cpp)]

Výsledky z tohoto programu jsou následující:

```Output
AddHead example: A CObList with 2 elements
a CAge at $44A8 40
a CAge at $442A 21
```

##  <a name="addtail"></a>CObList:: AddTail –

Přidá nový prvek nebo seznam prvků na konec seznamu.

```
POSITION AddTail(CObject* newElement);
void AddTail(CObList* pNewList);
```

### <a name="parameters"></a>Parametry

*newElement*<br/>
`CObject` ukazatel, který se má přidat do tohoto seznamu.

*pNewList*<br/>
Ukazatel na jiný seznam `CObList`. Prvky v *pNewList* budou přidány do tohoto seznamu.

### <a name="return-value"></a>Návratová hodnota

První verze vrátí hodnotu pozice nově vloženého prvku.

### <a name="remarks"></a>Poznámky

Seznam může být před operací prázdný.

V následující tabulce jsou uvedeny jiné členské funkce, které jsou podobné `CObList::AddTail`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Pozice AddTail – (void** <strong>\*</strong> `newElement` **);**<br /><br /> **void AddTail – (CPtrList** <strong>\*</strong> `pNewList` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**AddTail – pozice (const CString &** `newElement` **);**<br /><br /> **Pozice AddTail – (LPCTSTR** `newElement` **);**<br /><br /> **void AddTail – (CStringList** <strong>\*</strong> `pNewList` **);**|

### <a name="example"></a>Příklad

  Seznam `CAge` třídy naleznete v tématu [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#90](../../mfc/codesnippet/cpp/coblist-class_2.cpp)]

Výsledky z tohoto programu jsou následující:

```Output
AddTail example: A CObList with 2 elements
a CAge at $444A 21
a CAge at $4526 40
```

##  <a name="coblist"></a>CObList::CObList

Vytvoří prázdný seznam ukazatelů `CObject`.

```
CObList(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Parametry

*nBlockSize*<br/>
Členitost přidělení paměti pro rozšíření seznamu.

### <a name="remarks"></a>Poznámky

Jak se seznam zvětšuje, paměť se přiděluje v jednotkách *nBlockSizech* položek. Pokud není přidělení paměti úspěšné, je vyvolána `CMemoryException`.

V následující tabulce jsou uvedeny jiné členské funkce, které jsou podobné `CObList::CObList`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**CPtrList (INT_PTR** `nBlockSize` **= 10);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CStringList (INT_PTR** `nBlockSize` **= 10);**|

### <a name="example"></a>Příklad

  Níže je uveden seznam `CAge` třídy odvozené od `CObject`, která se používá ve všech příkladech kolekce:

[!code-cpp[NVC_MFCCollections#91](../../mfc/codesnippet/cpp/coblist-class_3.h)]

Níže je uveden příklad použití konstruktoru `CObList`:

[!code-cpp[NVC_MFCCollections#92](../../mfc/codesnippet/cpp/coblist-class_4.cpp)]

##  <a name="find"></a>CObList:: Find

Vyhledá v seznamu postupně, aby se našel první `CObject` ukazatel, který odpovídá zadanému ukazateli `CObject`.

```
POSITION Find(
    CObject* searchValue,
    POSITION startAfter = NULL) const;
```

### <a name="parameters"></a>Parametry

*searchValue*<br/>
Ukazatel na objekt, který se má najít v tomto seznamu.

*startAfter*<br/>
Počáteční pozice pro hledání.

### <a name="return-value"></a>Návratová hodnota

Hodnota pozice, která se dá použít pro načtení ukazatele iterace nebo objektu; Hodnota NULL, pokud objekt nebyl nalezen.

### <a name="remarks"></a>Poznámky

Všimněte si, že hodnoty ukazatelů jsou porovnávány, nikoli obsah objektů.

V následující tabulce jsou uvedeny jiné členské funkce, které jsou podobné `CObList::Find`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Pozice Find (void** <strong>\*</strong> `searchValue` **, pozice** `startAfter` **= null) const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Pozice Find (LPCTSTR** `searchValue` **, pozice** `startAfter` **= null) const;**|

### <a name="example"></a>Příklad

Seznam `CAge` třídy naleznete v tématu [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#93](../../mfc/codesnippet/cpp/coblist-class_5.cpp)]

##  <a name="findindex"></a>CObList:: FindIndex –

Použije hodnotu *nIndex* jako index do seznamu.

```
POSITION FindIndex(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index založený na nule prvku seznamu, který se má najít

### <a name="return-value"></a>Návratová hodnota

Hodnota pozice, která se dá použít pro načtení ukazatele iterace nebo objektu; Hodnota NULL, pokud je *nIndex* příliš velká. (Rozhraní generuje kontrolní výraz, pokud je *nIndex* záporné.)

### <a name="remarks"></a>Poznámky

Spustí sekvenční prohledávání z hlavičky seznamu a zastavuje se na *n*-tý prvek.

V následující tabulce jsou uvedeny jiné členské funkce, které jsou podobné `CObList::FindIndex`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Pozice FindIndex – (INT_PTR** `nIndex` **) const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Pozice FindIndex – (INT_PTR** `nIndex` **) const;**|

### <a name="example"></a>Příklad

Seznam `CAge` třídy naleznete v tématu [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#94](../../mfc/codesnippet/cpp/coblist-class_6.cpp)]

##  <a name="getat"></a>CObList::GetAt

Proměnná pozice typu je klíč pro seznam.

```
CObject*& GetAt(POSITION position);
const CObject*& GetAt(POSITION position) const;
```

### <a name="parameters"></a>Parametry

*poziční*<br/>
Hodnota pozice vrácená předchozím `GetHeadPosition` nebo `Find` volání členské funkce.

### <a name="return-value"></a>Návratová hodnota

Podívejte se na popis návratové hodnoty pro [GetHead](#gethead).

### <a name="remarks"></a>Poznámky

Není stejný jako index a nemůžete pracovat s hodnotou pozice sami. `GetAt` načte ukazatel `CObject` přidružený k dané pozici.

Je nutné zajistit, aby hodnota pozice představovala platné umístění v seznamu. Pokud je neplatný, ladicí verze knihovna Microsoft Foundation Class výrazy.

V následující tabulce jsou uvedeny jiné členské funkce, které jsou podobné `CObList::GetAt`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const void\*& GetAt (** *pozice* pozice **) const;**<br /><br /> **void\*& GetAt (** *pozice* pozice **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const CString & GetAt (** *pozice* pozice **) const;**<br /><br /> **CString & GetAt (pozice pozice** **);**|

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [FindIndex –](#findindex).

##  <a name="getcount"></a>CObList:: GetCount

Získá počet prvků v tomto seznamu.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Celočíselná hodnota obsahující počet prvků.

V následující tabulce jsou uvedeny jiné členské funkce, které jsou podobné `CObList::GetCount`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR GetCount () const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**INT_PTR GetCount () const;**|

### <a name="example"></a>Příklad

Seznam `CAge` třídy naleznete v tématu [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#95](../../mfc/codesnippet/cpp/coblist-class_7.cpp)]

##  <a name="gethead"></a>CObList:: GetHead

Získá ukazatel `CObject`, který představuje element head tohoto seznamu.

```
CObject*& GetHead();
const CObject*& GetHead() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud je seznam k dispozici prostřednictvím ukazatele na `const CObList`, pak `GetHead` vrátí `CObject` ukazatel. To umožňuje použití funkce pouze na pravé straně příkazu přiřazení, čímž se seznam chrání před úpravami.

Pokud je seznam k dispozici přímo nebo prostřednictvím ukazatele na `CObList`, pak `GetHead` vrátí odkaz na `CObject` ukazatel. To umožňuje použití funkce na obou stranách příkazu přiřazení, což umožňuje upravovat položky seznamu.

### <a name="remarks"></a>Poznámky

Před voláním `GetHead`je nutné zajistit, aby seznam nebyl prázdný. Pokud je seznam prázdný, ladicí verze knihovna Microsoft Foundation Class Assert. Chcete-li ověřit, zda seznam obsahuje prvky, použijte pole [neprázdné](#isempty) .

V následující tabulce jsou uvedeny jiné členské funkce, které jsou podobné `CObList::GetHead`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const void\*& GetHead () const; void\*& GetHead ();**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const CString & GetHead () const; CString & GetHead ();**|

### <a name="example"></a>Příklad

Seznam `CAge` třídy naleznete v tématu [CObList:: CObList](#coblist) .

Následující příklad ilustruje použití `GetHead` na levé straně příkazu přiřazení.

[!code-cpp[NVC_MFCCollections#96](../../mfc/codesnippet/cpp/coblist-class_8.cpp)]

##  <a name="getheadposition"></a>CObList::GetHeadPosition

Získá pozici elementu Head v tomto seznamu.

```
POSITION GetHeadPosition() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota pozice, která se dá použít pro načtení ukazatele iterace nebo objektu; Hodnota NULL, pokud je seznam prázdný.

V následující tabulce jsou uvedeny jiné členské funkce, které jsou podobné `CObList::GetHeadPosition`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POZICE GetHeadPosition () const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POZICE GetHeadPosition () const;**|

### <a name="example"></a>Příklad

Seznam `CAge` třídy naleznete v tématu [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#97](../../mfc/codesnippet/cpp/coblist-class_9.cpp)]

##  <a name="getnext"></a>CObList:: GetNext

Získá element seznamu identifikovaný *rPosition.* a pak nastaví *rposition.* na hodnotu `POSITION` další položky v seznamu.

```
CObject*& GetNext(POSITION& rPosition);
const CObject* GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parametry

*rPosition.*<br/>
Odkaz na hodnotu pozice vrácenou předchozí `GetNext`, `GetHeadPosition`nebo jiné volání členské funkce.

### <a name="return-value"></a>Návratová hodnota

Podívejte se na popis návratové hodnoty pro [GetHead](#gethead).

### <a name="remarks"></a>Poznámky

Pokud vytvoříte počáteční pozici s voláním `GetHeadPosition` nebo `Find`, můžete použít `GetNext` ve smyčce dopředné iteraci.

Je nutné zajistit, aby hodnota pozice představovala platné umístění v seznamu. Pokud je neplatný, ladicí verze knihovna Microsoft Foundation Class výrazy.

Pokud je načtený prvek poslední v seznamu, pak je nová hodnota *rPosition.* nastavena na hodnotu null.

Je možné odebrat prvek během iterace. Podívejte se na příklad pro [funkce RemoveAt](#removeat).

> [!NOTE]
>  Počínaje verzí MFC 8,0 se verze const této metody změnila tak, aby vracela `const CObject*` místo `const CObject*&`.  Tato změna byla provedena k tomu, aby kompilátor byl v souladu se C++ standardem.

V následující tabulce jsou uvedeny jiné členské funkce, které jsou podobné `CObList::GetNext`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const void* GetNext( POSITION&` `rPosition` `) const;`|
|[CStringList](../../mfc/reference/cstringlist-class.md)|`CString& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetNext( POSITION&` `rPosition` `) const;`|

### <a name="example"></a>Příklad

  Seznam `CAge` třídy naleznete v tématu [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#98](../../mfc/codesnippet/cpp/coblist-class_10.cpp)]

Výsledky z tohoto programu jsou následující:

```Output
a CAge at $479C 40
a CAge at $46C0 21
```

##  <a name="getprev"></a>CObList:: getpředchozí

Získá element seznamu identifikovaný *rPosition.* a pak nastaví *RPOSITION.* na hodnotu pozice předchozí položky v seznamu.

```
CObject*& GetPrev(POSITION& rPosition);
const CObject* GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parametry

*rPosition.*<br/>
Odkaz na hodnotu pozice vrácenou předchozí `GetPrev` nebo jiným voláním členské funkce.

### <a name="return-value"></a>Návratová hodnota

Podívejte se na popis návratové hodnoty pro [GetHead](#gethead).

### <a name="remarks"></a>Poznámky

Pokud vytvoříte počáteční pozici s voláním `GetTailPosition` nebo `Find`, můžete použít `GetPrev` ve smyčce reverzní iterace.

Je nutné zajistit, aby hodnota pozice představovala platné umístění v seznamu. Pokud je neplatný, ladicí verze knihovna Microsoft Foundation Class výrazy.

Pokud je načtený element v seznamu první, pak je nová hodnota *rPosition.* nastavena na hodnotu null.

> [!NOTE]
>  Počínaje verzí MFC 8,0 se verze const této metody změnila tak, aby vracela `const CObject*` místo `const CObject*&`.  Tato změna byla provedena k tomu, aby kompilátor byl v souladu se C++ standardem.

V následující tabulce jsou uvedeny jiné členské funkce, které jsou podobné `CObList::GetPrev`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const void* GetPrev( POSITION&` `rPosition` `) const;`|
|[CStringList](../../mfc/reference/cstringlist-class.md)|`CString& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetPrev( POSITION&` `rPosition` `) const;`|

### <a name="example"></a>Příklad

  Seznam `CAge` třídy naleznete v tématu [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#99](../../mfc/codesnippet/cpp/coblist-class_11.cpp)]

Výsledky z tohoto programu jsou následující:

```Output
a CAge at $421C 21
a CAge at $421C 40
```

##  <a name="getsize"></a>CObList:: GetSize

Vrátí počet prvků seznamu.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v seznamu.

### <a name="remarks"></a>Poznámky

Voláním této metody načtete počet prvků v seznamu.

V následující tabulce jsou uvedeny jiné členské funkce, které jsou podobné `CObList::GetSize`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR GetSize () const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**INT_PTR GetSize () const;**|

### <a name="example"></a>Příklad

Seznam `CAge` třídy naleznete v tématu [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#100](../../mfc/codesnippet/cpp/coblist-class_12.cpp)]

##  <a name="gettail"></a>CObList:: GetTail

Získá ukazatel `CObject`, který představuje element Tail tohoto seznamu.

```
CObject*& GetTail();
const CObject*& GetTail() const;
```

### <a name="return-value"></a>Návratová hodnota

Podívejte se na popis návratové hodnoty pro [GetHead](#gethead).

### <a name="remarks"></a>Poznámky

Před voláním `GetTail`je nutné zajistit, aby seznam nebyl prázdný. Pokud je seznam prázdný, ladicí verze knihovna Microsoft Foundation Class Assert. Chcete-li ověřit, zda seznam obsahuje prvky, použijte pole [neprázdné](#isempty) .

V následující tabulce jsou uvedeny jiné členské funkce, které jsou podobné `CObList::GetTail`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const void\*& GetTail () const; void\*& GetTail ();**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const CString & GetTail () const; CString & GetTail ();**|

### <a name="example"></a>Příklad

Seznam `CAge` třídy naleznete v tématu [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#101](../../mfc/codesnippet/cpp/coblist-class_13.cpp)]

##  <a name="gettailposition"></a>CObList::GetTailPosition

Získá pozici koncového elementu tohoto seznamu; **Hodnota null** , pokud je seznam prázdný.

```
POSITION GetTailPosition() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota pozice, která se dá použít pro načtení ukazatele iterace nebo objektu; Hodnota NULL, pokud je seznam prázdný.

V následující tabulce jsou uvedeny jiné členské funkce, které jsou podobné `CObList::GetTailPosition`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POZICE GetTailPosition () const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POZICE GetTailPosition () const;**|

### <a name="example"></a>Příklad

Seznam `CAge` třídy naleznete v tématu [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#102](../../mfc/codesnippet/cpp/coblist-class_14.cpp)]

##  <a name="insertafter"></a>CObList::InsertAfter

Přidá prvek do tohoto seznamu za element na zadané pozici.

```
POSITION InsertAfter(
    POSITION position,
    CObject* newElement);
```

### <a name="parameters"></a>Parametry

*poziční*<br/>
Hodnotu pozice vrácenou předchozí `GetNext`, `GetPrev`nebo `Find` volání členské funkce.

*newElement*<br/>
Ukazatel objektu, který má být přidán do tohoto seznamu.

V následující tabulce jsou uvedeny jiné členské funkce, které jsou podobné `CObList::InsertAfter`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**InsertAfter pozice (pozice pozice** **, void** <strong>\*</strong> `newElement` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**InsertAfter pozice (pozice pozice** **, const CString &** `newElement` **);**<br /><br /> **InsertAfter pozice (** *pozice* **, LPCTSTR** `newElement` **);**|

### <a name="return-value"></a>Návratová hodnota

Hodnota pozice, která je stejná jako parametr *pozice* .

### <a name="example"></a>Příklad

  Seznam `CAge` třídy naleznete v tématu [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#103](../../mfc/codesnippet/cpp/coblist-class_15.cpp)]

Výsledky z tohoto programu jsou následující:

```Output
InsertAfter example: A CObList with 3 elements
a CAge at $4A44 40
a CAge at $4A64 65
a CAge at $4968 21
```

##  <a name="insertbefore"></a>CObList::InsertBefore

Přidá prvek do tohoto seznamu před element na zadané pozici.

```
POSITION InsertBefore(
    POSITION position,
    CObject* newElement);
```

### <a name="parameters"></a>Parametry

*poziční*<br/>
Hodnotu pozice vrácenou předchozí `GetNext`, `GetPrev`nebo `Find` volání členské funkce.

*newElement*<br/>
Ukazatel objektu, který má být přidán do tohoto seznamu.

### <a name="return-value"></a>Návratová hodnota

Hodnota pozice, která se dá použít pro načtení ukazatele iterace nebo objektu; Hodnota NULL, pokud je seznam prázdný.

V následující tabulce jsou uvedeny jiné členské funkce, které jsou podobné `CObList::InsertBefore`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**InsertBefore pozice (pozice pozice** **, void** <strong>\*</strong> `newElement` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**InsertBefore pozice (pozice pozice** **, const CString &** `newElement` **);**<br /><br /> **InsertBefore pozice (** *pozice* **, LPCTSTR** `newElement` **);**|

### <a name="example"></a>Příklad

  Seznam `CAge` třídy naleznete v tématu [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#104](../../mfc/codesnippet/cpp/coblist-class_16.cpp)]

Výsledky z tohoto programu jsou následující:

```Output
InsertBefore example: A CObList with 3 elements
a CAge at $4AE2 40
a CAge at $4B02 65
a CAge at $49E6 21
```

##  <a name="isempty"></a>CObList::-Empty

Určuje, zda tento seznam neobsahuje žádné prvky.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je tento seznam prázdný; v opačném případě 0.

V následující tabulce jsou uvedeny jiné členské funkce, které jsou podobné `CObList::IsEmpty`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**BOOL = Empty () const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**BOOL = Empty () const;**|

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [RemoveAll](#removeall).

##  <a name="removeall"></a>CObList::RemoveAll

Odebere všechny prvky z tohoto seznamu a uvolní přidruženou `CObList` paměť.

```
void RemoveAll();
```

### <a name="remarks"></a>Poznámky

Pokud je seznam již prázdný, není vygenerována žádná chyba.

Když odeberete prvky z `CObList`, odeberete ukazatelé na objekty ze seznamu. Je vaší zodpovědností odstranit samotné objekty.

V následující tabulce jsou uvedeny jiné členské funkce, které jsou podobné `CObList::RemoveAll`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void RemoveAll ();**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void RemoveAll ();**|

### <a name="example"></a>Příklad

Seznam `CAge` třídy naleznete v tématu [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#105](../../mfc/codesnippet/cpp/coblist-class_17.cpp)]

##  <a name="removeat"></a>CObList:: funkce RemoveAt

Odebere zadaný prvek z tohoto seznamu.

```
void RemoveAt(POSITION position);
```

### <a name="parameters"></a>Parametry

*poziční*<br/>
Pozice prvku, který má být odebrán ze seznamu.

### <a name="remarks"></a>Poznámky

Když odeberete prvek z `CObList`, odeberete ukazatel objektu ze seznamu. Je vaší zodpovědností odstranit samotné objekty.

Je nutné zajistit, aby hodnota pozice představovala platné umístění v seznamu. Pokud je neplatný, ladicí verze knihovna Microsoft Foundation Class výrazy.

V následující tabulce jsou uvedeny jiné členské funkce, které jsou podobné `CObList::RemoveAt`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void funkce RemoveAt (pozice pozice** **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void funkce RemoveAt (pozice pozice** **);**|

### <a name="example"></a>Příklad

  Buďte opatrní při odebírání elementu během iterace seznamu. Následující příklad ukazuje techniku odebrání, která garantuje platnou hodnotu **pozice** pro [GetNext](#getnext).

Seznam `CAge` třídy naleznete v tématu [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#106](../../mfc/codesnippet/cpp/coblist-class_18.cpp)]

Výsledky z tohoto programu jsou následující:

`RemoveAt example: A CObList with 2 elements`

`a CAge at $4C1E 65`

`a CAge at $4B22 21`

##  <a name="removehead"></a>CObList::RemoveHead

Odebere prvek z hlavičky seznamu a vrátí na něj ukazatel.

```
CObject* RemoveHead();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel `CObject` dříve v záhlaví seznamu.

### <a name="remarks"></a>Poznámky

Před voláním `RemoveHead`je nutné zajistit, aby seznam nebyl prázdný. Pokud je seznam prázdný, ladicí verze knihovna Microsoft Foundation Class Assert. Chcete-li ověřit, zda seznam obsahuje prvky, použijte pole [neprázdné](#isempty) .

V následující tabulce jsou uvedeny jiné členské funkce, které jsou podobné `CObList::RemoveHead`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void\* RemoveHead ();**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CString RemoveHead ();**|

### <a name="example"></a>Příklad

Seznam `CAge` třídy naleznete v tématu [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#107](../../mfc/codesnippet/cpp/coblist-class_19.cpp)]

##  <a name="removetail"></a>CObList::RemoveTail

Odstraní prvek ze strany seznamu a vrátí ukazatel na něj.

```
CObject* RemoveTail();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt, který byl na konci seznamu.

### <a name="remarks"></a>Poznámky

Před voláním `RemoveTail`je nutné zajistit, aby seznam nebyl prázdný. Pokud je seznam prázdný, ladicí verze knihovna Microsoft Foundation Class Assert. Chcete-li ověřit, zda seznam obsahuje prvky, použijte pole [neprázdné](#isempty) .

V následující tabulce jsou uvedeny jiné členské funkce, které jsou podobné `CObList::RemoveTail`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void\* RemoveTail ();**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CString RemoveTail ();**|

### <a name="example"></a>Příklad

Seznam `CAge` třídy naleznete v tématu [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#108](../../mfc/codesnippet/cpp/coblist-class_20.cpp)]

##  <a name="setat"></a>CObList::SetAt

Nastaví prvek na dané pozici.

```
void SetAt(
    POSITION pos,
    CObject* newElement);
```

### <a name="parameters"></a>Parametry

*POS*<br/>
POZICE prvku, který má být nastaven.

*newElement*<br/>
`CObject` ukazatel, který se má zapsat do seznamu.

### <a name="remarks"></a>Poznámky

Proměnná pozice typu je klíč pro seznam. Není stejný jako index a nemůžete pracovat s hodnotou pozice sami. `SetAt` zapisuje ukazatel `CObject` na určenou pozici v seznamu.

Je nutné zajistit, aby hodnota pozice představovala platné umístění v seznamu. Pokud je neplatný, ladicí verze knihovna Microsoft Foundation Class výrazy.

V následující tabulce jsou uvedeny jiné členské funkce, které jsou podobné `CObList::SetAt`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void SetAt (pozice** `pos` **, const CString &** `newElement` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void SetAt (pozice** `pos` **, LPCTSTR** `newElement` **);**|

### <a name="example"></a>Příklad

  Seznam `CAge` třídy naleznete v tématu [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#109](../../mfc/codesnippet/cpp/coblist-class_21.cpp)]

Výsledky z tohoto programu jsou následující:

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
