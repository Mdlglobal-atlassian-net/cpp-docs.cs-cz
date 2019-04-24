---
title: CList – třída
ms.date: 11/04/2016
f1_keywords:
- CList
- AFXTEMPL/CList
- AFXTEMPL/CList::CList
- AFXTEMPL/CList::AddHead
- AFXTEMPL/CList::AddTail
- AFXTEMPL/CList::Find
- AFXTEMPL/CList::FindIndex
- AFXTEMPL/CList::GetAt
- AFXTEMPL/CList::GetCount
- AFXTEMPL/CList::GetHead
- AFXTEMPL/CList::GetHeadPosition
- AFXTEMPL/CList::GetNext
- AFXTEMPL/CList::GetPrev
- AFXTEMPL/CList::GetSize
- AFXTEMPL/CList::GetTail
- AFXTEMPL/CList::GetTailPosition
- AFXTEMPL/CList::InsertAfter
- AFXTEMPL/CList::InsertBefore
- AFXTEMPL/CList::IsEmpty
- AFXTEMPL/CList::RemoveAll
- AFXTEMPL/CList::RemoveAt
- AFXTEMPL/CList::RemoveHead
- AFXTEMPL/CList::RemoveTail
- AFXTEMPL/CList::SetAt
helpviewer_keywords:
- CList [MFC], CList
- CList [MFC], AddHead
- CList [MFC], AddTail
- CList [MFC], Find
- CList [MFC], FindIndex
- CList [MFC], GetAt
- CList [MFC], GetCount
- CList [MFC], GetHead
- CList [MFC], GetHeadPosition
- CList [MFC], GetNext
- CList [MFC], GetPrev
- CList [MFC], GetSize
- CList [MFC], GetTail
- CList [MFC], GetTailPosition
- CList [MFC], InsertAfter
- CList [MFC], InsertBefore
- CList [MFC], IsEmpty
- CList [MFC], RemoveAll
- CList [MFC], RemoveAt
- CList [MFC], RemoveHead
- CList [MFC], RemoveTail
- CList [MFC], SetAt
ms.assetid: 6f6273c3-c8f6-47f5-ac2a-0a950379ae5d
ms.openlocfilehash: 383222e4892bccc653f010ce4939bca23f2adc93
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62225292"
---
# <a name="clist-class"></a>CList – třída

Podporuje seřazené seznam nejedinečných objektů dostupných postupně sekvenčně nebo podle hodnoty.

## <a name="syntax"></a>Syntaxe

```
template<class TYPE, class ARG_TYPE = const TYPE&>
class CList : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CList::CList](#clist)|Vytvoří prázdný uspořádaného seznamu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CList::AddHead](#addhead)|Přidá k začátku seznamu (novou vedoucí díky) elementu (nebo všechny prvky v jiném seznamu).|
|[CList::AddTail](#addtail)|Přidá na konec seznamu (umožňuje nové funkce tail) elementu (nebo všechny prvky v jiném seznamu).|
|[CList::Find](#find)|Získá pozici prvku určeného hodnotou ukazatele.|
|[CList::FindIndex](#findindex)|Získá pozici prvku určený index založený na nule.|
|[CList::GetAt](#getat)|Získá prvek na dané pozici.|
|[CList::GetCount](#getcount)|Vrátí počet prvků v tomto seznamu.|
|[CList::GetHead](#gethead)|Vrátí element head seznamu (nemůže být prázdný).|
|[CList::GetHeadPosition](#getheadposition)|Vrátí pozici element head seznamu.|
|[CList::GetNext](#getnext)|Získá další prvek pro iterace.|
|[CList::GetPrev](#getprev)|Získá předchozí prvek pro iterace.|
|[CList::GetSize](#getsize)|Vrátí počet prvků v tomto seznamu.|
|[CList::GetTail](#gettail)|Vrátí element tail seznamu (nemůže být prázdný).|
|[CList::GetTailPosition](#gettailposition)|Vrátí pozici prvku tail seznamu.|
|[CList::InsertAfter](#insertafter)|Vloží nový prvek za danou pozici.|
|[CList::InsertBefore](#insertbefore)|Vloží nový prvek před danou pozici.|
|[CList::IsEmpty](#isempty)|Testy pro prázdný seznam podmínku (žádné elementy).|
|[CList::RemoveAll](#removeall)|Odebere všechny prvky z tohoto seznamu.|
|[CList::RemoveAt](#removeat)|Odebere element z tohoto seznamu, určené pozici.|
|[CList::RemoveHead](#removehead)|Odebere element z prvního seznamu.|
|[CList::RemoveTail](#removetail)|Odebere element z konec seznamu.|
|[CList::SetAt](#setat)|Nastaví element na dané pozici.|

#### <a name="parameters"></a>Parametry

*TYP*<br/>
Typ objektu, které jsou uloženy v seznamu.

*ARG_TYPE*<br/>
Typ slouží k odkazování objektů uložených v seznamu. Může být referencí.

## <a name="remarks"></a>Poznámky

`CList` seznamy se chovat jako dvakrát propojené seznamy.

Proměnné typu pozice je klíč pro seznam. Proměnnou POZICI jako iterátor můžete procházet seznamem postupně a jako záložku pro uchování na místě. Pozice není stejný jako index, ale.

Vložení elementu je velmi rychlé zpracování v čele seznamu, na konci a známé pozici. Sekvenčního vyhledávání, je nutné při hledání elementu podle hodnoty nebo index. Toto vyhledávání může být pomalé, pokud je dlouhý seznam.

Pokud potřebujete s výpisem paměti jednotlivých prvků v seznamu, nastavte na 1 nebo větší hloubky kontextu s výpisem paměti.

Určité členské funkce třídy volání globální pomocné funkce, které je nutné upravit pro většina použití `CList` třídy. Zobrazit [pomocné rutiny třídy kolekce](../../mfc/reference/collection-class-helpers.md) v části "Makra a globální prvky".

Další informace o používání `CList`, najdete v článku [kolekce](../../mfc/collections.md).

## <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#35](../../mfc/codesnippet/cpp/clist-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CList`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxtempl.h

##  <a name="addhead"></a>  CList::AddHead

Přidá nový prvek nebo seznam elementů na začátku tohoto seznamu.

```
POSITION AddHead(ARG_TYPE newElement);
void AddHead(CList* pNewList);
```

### <a name="parameters"></a>Parametry

*ARG_TYPE*<br/>
Parametr šablony určující typ prvku seznam (může být referencí s).

*newElement*<br/>
Nový prvek.

*pNewList*<br/>
Ukazatel na jiný `CList` seznamu. Prvky v *pNewList* budou přidány do tohoto seznamu.

### <a name="return-value"></a>Návratová hodnota

První verze vrátí hodnotu pozice nově vložený prvek.

### <a name="remarks"></a>Poznámky

Seznam může být prázdný před provedením operace.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#36](../../mfc/codesnippet/cpp/clist-class_2.cpp)]

##  <a name="addtail"></a>  CList::AddTail

Přidá nový prvek nebo seznam prvků na konci tohoto seznamu.

```
POSITION AddTail(ARG_TYPE newElement);
void AddTail(CList* pNewList);
```

### <a name="parameters"></a>Parametry

*ARG_TYPE*<br/>
Parametr šablony určující typ prvku seznam (může být referencí s).

*newElement*<br/>
Elementu, který chcete přidat do tohoto seznamu.

*pNewList*<br/>
Ukazatel na jiný `CList` seznamu. Prvky v *pNewList* budou přidány do tohoto seznamu.

### <a name="return-value"></a>Návratová hodnota

První verze vrátí hodnotu pozice nově vložený prvek.

### <a name="remarks"></a>Poznámky

Seznam může být prázdný před provedením operace.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#37](../../mfc/codesnippet/cpp/clist-class_3.cpp)]

##  <a name="clist"></a>  CList::CList

Vytvoří prázdný uspořádaného seznamu.

```
CList(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Parametry

*nBlockSize*<br/>
Členitost přidělení paměti pro rozšíření seznamu.

### <a name="remarks"></a>Poznámky

S růstem seznamu je paměť přidělena v jednotkách, které *nBlockSize* položky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#38](../../mfc/codesnippet/cpp/clist-class_4.cpp)]

##  <a name="find"></a>  CList::Find

Prohledává postupně seznamu vyhledejte první prvek odpovídající zadané *searchValue*.

```
POSITION Find(
    ARG_TYPE searchValue,
    POSITION startAfter = NULL) const;
```

### <a name="parameters"></a>Parametry

*ARG_TYPE*<br/>
Parametr šablony určující typ prvku seznam (může být referencí s).

*searchValue*<br/>
Hodnota má být nalezen v seznamu.

*startAfter*<br/>
Počáteční pozice pro vyhledávání. Pokud není zadána žádná hodnota, začíná hledání head element.

### <a name="return-value"></a>Návratová hodnota

POZICE hodnotu, která lze použít pro iteraci nebo načtení objektu ukazatele; Hodnota NULL, pokud objekt nebyl nalezen.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#39](../../mfc/codesnippet/cpp/clist-class_5.cpp)]

##  <a name="findindex"></a>  CList::FindIndex

Používá hodnotu *nIndex* jako index do seznamu.

```
POSITION FindIndex(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index založený na nule prvku seznam, který chcete najít.

### <a name="return-value"></a>Návratová hodnota

POZICE hodnotu, která lze použít pro iteraci nebo načtení objektu ukazatele; Hodnota NULL, pokud *nIndex* je záporný nebo moc velký.

### <a name="remarks"></a>Poznámky

Spuštěním kontroly sekvenční od začátku seznamu zastavování na *n*tý prvek.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#40](../../mfc/codesnippet/cpp/clist-class_6.cpp)]

##  <a name="getat"></a>  CList::GetAt

Získá seznam element na dané pozici.

```
TYPE& GetAt(POSITION position);
const TYPE& GetAt(POSITION position) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ objektu v seznamu.

*Pozice*<br/>
Pozice prvku, který chcete získat v seznamu.

### <a name="return-value"></a>Návratová hodnota

Naleznete v popisu návratovou hodnotu pro `GetHead`.

### <a name="remarks"></a>Poznámky

`GetAt` Vrátí hodnotu elementu (nebo odkaz na prvek) přidružené k dané pozici. Není stejný jako index a nemůžete pracovat na základě hodnoty pozice sami. Proměnné typu pozice je klíč pro seznam.

Ujistěte se, že hodnota pozice představuje platná pozice v seznamu. Pokud je neplatná, ladicí verze knihovny Microsoft Foundation Class se vyhodnotí.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CList::GetHeadPosition](#getheadposition).

##  <a name="getcount"></a>  CList::GetCount

Získá počet elementů v tomto seznamu.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Celočíselnou hodnotu obsahující počet prvků.

### <a name="remarks"></a>Poznámky

Voláním této metody bude generovat stejný výsledek jako [CList::GetSize](#getsize) metody.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CList::RemoveHead](#removehead).

##  <a name="gethead"></a>  CList::GetHead

Získá head element (nebo odkaz na head element) z tohoto seznamu.

```
const TYPE& GetHead() const;

TYPE& GetHead();
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ objektu v seznamu.

### <a name="return-value"></a>Návratová hodnota

Pokud je seznam **const**, `GetHead` vrátí kopii objektu prvek na začátku seznamu. To umožňuje funkce, která se použije pouze na pravé straně příkazu přiřazení a chrání před úpravy seznamu.

Pokud seznam není **const**, `GetHead` vrátí odkaz na prvek na začátku seznamu. To umožňuje funkce, která se použije na obou stranách příkazu přiřazení a tím umožňuje položky seznamu, který má být upraven.

### <a name="remarks"></a>Poznámky

Ujistěte se, že seznam není prázdný před voláním `GetHead`. Pokud je seznam prázdný, pak vyhodnotí ladicí verze knihovny Microsoft Foundation Class. Použití [IsEmpty](#isempty) ověřit, zda seznam obsahuje prvky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#41](../../mfc/codesnippet/cpp/clist-class_7.cpp)]

##  <a name="getheadposition"></a>  CList::GetHeadPosition

Získá pozici element head tohoto seznamu.

```
POSITION GetHeadPosition() const;
```

### <a name="return-value"></a>Návratová hodnota

POZICE hodnotu, která lze použít pro iteraci nebo načtení objektu ukazatele; Hodnota NULL, pokud je seznam prázdný.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#42](../../mfc/codesnippet/cpp/clist-class_8.cpp)]

##  <a name="getnext"></a>  CList::GetNext

Získá seznam prvek identifikovaný *rposition*, pak nastaví *rposition* hodnotu pozice další položky v seznamu.

```
TYPE& GetNext(POSITION& rPosition);
const TYPE& GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvků v seznamu.

*rposition.*<br/>
Odkaz na POZICI hodnotu vrácenou předchozím `GetNext`, [GetHeadPosition](#getheadposition), nebo jiné členské funkce volání.

### <a name="return-value"></a>Návratová hodnota

Pokud je seznam **const**, `GetNext` vrátí kopii objektu element seznamu. To umožňuje funkce, která se použije pouze na pravé straně příkazu přiřazení a chrání před úpravy seznamu.

Pokud seznam není **const**, `GetNext` vrátí odkaz na element seznamu. To umožňuje funkce, která se použije na obou stranách příkazu přiřazení a tím umožňuje položky seznamu, který má být upraven.

### <a name="remarks"></a>Poznámky

Můžete použít `GetNext` v dopředné iteraci smyčky, Pokud zavedete počáteční pozici voláním `GetHeadPosition` nebo `Find`.

Ujistěte se, že hodnota pozice představuje platná pozice v seznamu. Pokud je neplatná, ladicí verze knihovny Microsoft Foundation Class se vyhodnotí.

Pokud je načtený element poslední v seznamu, pak nová hodnota `rPosition` nastaven na hodnotu NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#43](../../mfc/codesnippet/cpp/clist-class_9.cpp)]

##  <a name="getprev"></a>  CList::GetPrev

Získá seznam prvek identifikovaný `rPosition`, pak nastaví `rPosition` pozice hodnotu předchozí položka v seznamu.

```
TYPE& GetPrev(POSITION& rPosition);
const TYPE& GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvků v seznamu.

*rposition.*<br/>
Odkaz na POZICI hodnotu vrácenou předchozím `GetPrev` nebo jiné členské funkce volání.

### <a name="return-value"></a>Návratová hodnota

Pokud je seznam **const**, `GetPrev` vrátí kopii objektu prvek na začátku seznamu. To umožňuje funkce, která se použije pouze na pravé straně příkazu přiřazení a chrání před úpravy seznamu.

Pokud seznam není **const**, `GetPrev` vrátí odkaz na element seznamu. To umožňuje funkce, která se použije na obou stranách příkazu přiřazení a tím umožňuje položky seznamu, který má být upraven.

### <a name="remarks"></a>Poznámky

Můžete použít `GetPrev` v reverzní iteraci smyčky, Pokud zavedete počáteční pozici voláním `GetTailPosition` nebo `Find`.

Ujistěte se, že hodnota pozice představuje platná pozice v seznamu. Pokud je neplatná, ladicí verze knihovny Microsoft Foundation Class se vyhodnotí.

Je-li načíst prvek je první v seznamu, pak nová hodnota *rposition* nastaven na hodnotu NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#44](../../mfc/codesnippet/cpp/clist-class_10.cpp)]

##  <a name="getsize"></a>  CList::GetSize

Vrátí počet prvků seznamu.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v seznamu.

### <a name="remarks"></a>Poznámky

Voláním této metody lze načíst počet prvků v seznamu.  Voláním této metody bude generovat stejný výsledek jako [CList::GetCount](#getcount) metody.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#45](../../mfc/codesnippet/cpp/clist-class_11.cpp)]

##  <a name="gettail"></a>  CList::GetTail

Získá `CObject` ukazatel, který reprezentuje element tail tohoto seznamu.

```
TYPE& GetTail();
const TYPE& GetTail() const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvků v seznamu.

### <a name="return-value"></a>Návratová hodnota

Naleznete v popisu návratovou hodnotu pro [GetHead](../../mfc/reference/coblist-class.md#gethead).

### <a name="remarks"></a>Poznámky

Ujistěte se, že seznam není prázdný před voláním `GetTail`. Pokud je seznam prázdný, pak vyhodnotí ladicí verze knihovny Microsoft Foundation Class. Použití [IsEmpty](../../mfc/reference/coblist-class.md#isempty) ověřit, zda seznam obsahuje prvky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#46](../../mfc/codesnippet/cpp/clist-class_12.cpp)]

##  <a name="gettailposition"></a>  CList::GetTailPosition

Získá pozici prvku tail tohoto seznamu; Hodnota NULL, pokud je seznam prázdný.

```
POSITION GetTailPosition() const;
```

### <a name="return-value"></a>Návratová hodnota

POZICE hodnotu, která lze použít pro iteraci nebo načtení objektu ukazatele; Hodnota NULL, pokud je seznam prázdný.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#47](../../mfc/codesnippet/cpp/clist-class_13.cpp)]

##  <a name="insertafter"></a>  CList::InsertAfter

Přidá prvek do tohoto seznamu za elementem na zadané pozici.

```
POSITION InsertAfter(POSITION position, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parametry

*Pozice*<br/>
Hodnota pozice vrácené předchozím `GetNext`, `GetPrev`, nebo `Find` volání členské funkce.

*ARG_TYPE*<br/>
Parametr šablony určující typ prvku seznamu.

*newElement*<br/>
Elementu, který chcete přidat do tohoto seznamu.

### <a name="return-value"></a>Návratová hodnota

Hodnota pozice, který lze použít pro iteraci nebo seznamu elementu načtení.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#48](../../mfc/codesnippet/cpp/clist-class_14.cpp)]

##  <a name="insertbefore"></a>  CList::InsertBefore

Přidá prvek do tohoto seznamu před elementem na zadané pozici.

```
POSITION InsertBefore(POSITION position, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parametry

*Pozice*<br/>
Hodnota pozice vrácené předchozím `GetNext`, `GetPrev`, nebo `Find` volání členské funkce.

*ARG_TYPE*<br/>
Parametr šablony určující typ prvku seznam (může být referencí s).

*newElement*<br/>
Elementu, který chcete přidat do tohoto seznamu.

### <a name="return-value"></a>Návratová hodnota

Hodnota pozice, který lze použít pro iteraci nebo seznamu elementu načtení.

### <a name="remarks"></a>Poznámky

Pokud *pozice* má hodnotu NULL, element bude vložena na začátku seznamu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#49](../../mfc/codesnippet/cpp/clist-class_15.cpp)]

##  <a name="isempty"></a>  CList::IsEmpty

Určuje, zda tento seznam neobsahuje žádné elementy.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je tento seznam prázdný; jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#50](../../mfc/codesnippet/cpp/clist-class_16.cpp)]

##  <a name="removeall"></a>  CList::RemoveAll

Odebere všechny prvky v tomto seznamu a uvolní paměť přidružené.

```
void RemoveAll();
```

### <a name="remarks"></a>Poznámky

Pokud už je seznam prázdný, nevygeneruje se žádná chyba.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#51](../../mfc/codesnippet/cpp/clist-class_17.cpp)]

##  <a name="removeat"></a>  CList::RemoveAt

Odebere zadaný prvek z tohoto seznamu.

```
void RemoveAt(POSITION position);
```

### <a name="parameters"></a>Parametry

*Pozice*<br/>
Pozice prvku, který chcete odebrat ze seznamu.

### <a name="remarks"></a>Poznámky

Ujistěte se, že hodnota pozice představuje platná pozice v seznamu. Pokud je neplatná, ladicí verze knihovny Microsoft Foundation Class se vyhodnotí.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#52](../../mfc/codesnippet/cpp/clist-class_18.cpp)]

##  <a name="removehead"></a>  CList::RemoveHead

Odebere element z prvního seznamu a vrátí ukazatel na něj.

```
TYPE RemoveHead();
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvků v seznamu.

### <a name="return-value"></a>Návratová hodnota

Prvek dříve na začátku seznamu.

### <a name="remarks"></a>Poznámky

Ujistěte se, že seznam není prázdný před voláním `RemoveHead`. Pokud je seznam prázdný, pak vyhodnotí ladicí verze knihovny Microsoft Foundation Class. Použití [IsEmpty](#isempty) ověřit, zda seznam obsahuje prvky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#53](../../mfc/codesnippet/cpp/clist-class_19.cpp)]

##  <a name="removetail"></a>  CList::RemoveTail

Odebere element z konec seznamu a vrátí ukazatel na něj.

```
TYPE RemoveTail();
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvků v seznamu.

### <a name="return-value"></a>Návratová hodnota

Prvek, který byl na konci seznamu.

### <a name="remarks"></a>Poznámky

Ujistěte se, že seznam není prázdný před voláním `RemoveTail`. Pokud je seznam prázdný, pak vyhodnotí ladicí verze knihovny Microsoft Foundation Class. Použití [IsEmpty](#isempty) ověřit, zda seznam obsahuje prvky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#54](../../mfc/codesnippet/cpp/clist-class_20.cpp)]

##  <a name="setat"></a>  CList::SetAt

Proměnné typu pozice je klíč pro seznam.

```
void SetAt(POSITION pos, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parametry

*pos*<br/>
Pozice prvku, který chcete nastavit.

*ARG_TYPE*<br/>
Parametr šablony určující typ prvku seznam (může být referencí s).

*newElement*<br/>
Elementu, který chcete přidat do seznamu.

### <a name="remarks"></a>Poznámky

Není stejný jako index a nemůžete pracovat na základě hodnoty pozice sami. `SetAt` zapíše element na zadanou pozici v seznamu.

Ujistěte se, že hodnota pozice představuje platná pozice v seznamu. Pokud je neplatná, ladicí verze knihovny Microsoft Foundation Class se vyhodnotí.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#55](../../mfc/codesnippet/cpp/clist-class_21.cpp)]

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC shromažďování](../../overview/visual-cpp-samples.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CMap – třída](../../mfc/reference/cmap-class.md)<br/>
[CArray – třída](../../mfc/reference/carray-class.md)
