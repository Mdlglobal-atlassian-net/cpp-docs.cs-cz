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
ms.openlocfilehash: adc065687f0c2c40b7e66326ff9d1e6210a6962c
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754130"
---
# <a name="clist-class"></a>CList – třída

Podporuje seřazené seznamy nejedinečných objektů přístupných postupně nebo podle hodnoty.

## <a name="syntax"></a>Syntaxe

```
template<class TYPE, class ARG_TYPE = const TYPE&>
class CList : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CList::CList](#clist)|Vytvoří prázdný seřazený seznam.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CList::Hlavička](#addhead)|Přidá prvek (nebo všechny prvky v jiném seznamu) do hlavy seznamu (vytvoří novou hlavu).|
|[CList::AddTail](#addtail)|Přidá prvek (nebo všechny prvky v jiném seznamu) na konci seznamu (vytvoří nový ocas).|
|[CList::Najít](#find)|Získá pozici prvku určeného hodnotou ukazatele.|
|[CList::FindIndex](#findindex)|Získá pozici prvku určeného index emitované nula.|
|[CList::Getat](#getat)|Získá prvek na dané pozici.|
|[CList::GetCount](#getcount)|Vrátí počet prvků v tomto seznamu.|
|[CList::Gethead](#gethead)|Vrátí prvek hlavy seznamu (nemůže být prázdný).|
|[CList::GetheadPosition](#getheadposition)|Vrátí pozici prvku hlavy seznamu.|
|[CList::GetNext](#getnext)|Získá další prvek pro iterace.|
|[CList::GetPrev](#getprev)|Získá předchozí prvek pro iterace.|
|[CList::GetSize](#getsize)|Vrátí počet prvků v tomto seznamu.|
|[CList::GetTail](#gettail)|Vrátí ocasní prvek seznamu (nemůže být prázdný).|
|[CList::GetTailPosition](#gettailposition)|Vrátí pozici koncového prvku seznamu.|
|[CList::InsertAfter](#insertafter)|Vloží nový prvek za danou pozici.|
|[CList::Insertbefore](#insertbefore)|Vloží nový prvek před danou pozici.|
|[CList::Jeprázdný](#isempty)|Testy podmínky prázdného seznamu (žádné prvky).|
|[CList::RemoveAll](#removeall)|Odebere všechny prvky z tohoto seznamu.|
|[clist::Removeat](#removeat)|Odebere prvek z tohoto seznamu, určený podle pozice.|
|[CList::RemoveHead](#removehead)|Odebere prvek z hlavy seznamu.|
|[CList::RemoveTail](#removetail)|Odebere prvek z ocasu seznamu.|
|[CList:Setat](#setat)|Nastaví prvek na dané pozici.|

#### <a name="parameters"></a>Parametry

*TYP*<br/>
Typ objektu uloženého v seznamu.

*ARG_TYPE*<br/>
Typ používaný k odkazování na objekty uložené v seznamu. Může to být odkaz.

## <a name="remarks"></a>Poznámky

`CList`seznamy se chovají jako dvojnásob propojené seznamy.

Proměnná typu POSITION je klíčem k seznamu. Proměnnou POSITION můžete použít jako iterátor k postupnému procházení seznamu a jako záložku pro uložení místa. Pozice však není stejná jako index.

Vložení prvku je velmi rychlé v hlavě seznamu, na ocasu a ve známé poloze. Sekvenční vyhledávání je nutné vyhledat prvek podle hodnoty nebo indexu. Toto hledání může být pomalé, pokud je seznam dlouhý.

Pokud potřebujete výpis jednotlivých prvků v seznamu, je nutné nastavit hloubku kontextu výpisu na 1 nebo vyšší.

Některé členské funkce této třídy volají globální pomocné funkce, `CList` které musí být přizpůsobeny pro většinu použití třídy. Viz [Pomocníky třídy kolekce](../../mfc/reference/collection-class-helpers.md) v části "Makra a globální".

Další informace o `CList`použití naleznete v článku [Kolekce](../../mfc/collections.md).

## <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#35](../../mfc/codesnippet/cpp/clist-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CList`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxtempl.h

## <a name="clistaddhead"></a><a name="addhead"></a>CList::Hlavička

Přidá nový prvek nebo seznam prvků do hlavy tohoto seznamu.

```
POSITION AddHead(ARG_TYPE newElement);
void AddHead(CList* pNewList);
```

### <a name="parameters"></a>Parametry

*ARG_TYPE*<br/>
Parametr šablony určující typ prvku seznamu (může být odkaz).

*newElement*<br/>
Nový prvek.

*pNewList*<br/>
Ukazatel na `CList` jiný seznam. Prvky v *pNewList* budou přidány do tohoto seznamu.

### <a name="return-value"></a>Návratová hodnota

První verze vrátí hodnotu POSITION nově vloženého prvku.

### <a name="remarks"></a>Poznámky

Seznam může být před operací prázdný.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#36](../../mfc/codesnippet/cpp/clist-class_2.cpp)]

## <a name="clistaddtail"></a><a name="addtail"></a>CList::AddTail

Přidá nový prvek nebo seznam prvků na konci tohoto seznamu.

```
POSITION AddTail(ARG_TYPE newElement);
void AddTail(CList* pNewList);
```

### <a name="parameters"></a>Parametry

*ARG_TYPE*<br/>
Parametr šablony určující typ prvku seznamu (může být odkaz).

*newElement*<br/>
Prvek, který má být přidán do tohoto seznamu.

*pNewList*<br/>
Ukazatel na `CList` jiný seznam. Prvky v *pNewList* budou přidány do tohoto seznamu.

### <a name="return-value"></a>Návratová hodnota

První verze vrátí hodnotu POSITION nově vloženého prvku.

### <a name="remarks"></a>Poznámky

Seznam může být před operací prázdný.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#37](../../mfc/codesnippet/cpp/clist-class_3.cpp)]

## <a name="clistclist"></a><a name="clist"></a>CList::CList

Vytvoří prázdný seřazený seznam.

```
CList(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Parametry

*nBlockSize*<br/>
Rozlišovací schopnost přidělení paměti pro rozšíření seznamu.

### <a name="remarks"></a>Poznámky

Jak seznam roste, paměť je přidělena v jednotkách *nBlockSize* položek.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#38](../../mfc/codesnippet/cpp/clist-class_4.cpp)]

## <a name="clistfind"></a><a name="find"></a>CList::Najít

Postupně vyhledá seznam a vyhledá první prvek odpovídající zadané *hodnotě hledat .*

```
POSITION Find(
    ARG_TYPE searchValue,
    POSITION startAfter = NULL) const;
```

### <a name="parameters"></a>Parametry

*ARG_TYPE*<br/>
Parametr šablony určující typ prvku seznamu (může být odkaz).

*funkce searchValue*<br/>
Hodnota, která se nachází v seznamu.

*startAfter*<br/>
Počáteční pozice pro hledání. Pokud není zadána žádná hodnota, hledání začíná prvkem head.

### <a name="return-value"></a>Návratová hodnota

Hodnota POSITION, kterou lze použít pro iteraci nebo načtení ukazatele objektu; Null, pokud objekt nebyl nalezen.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#39](../../mfc/codesnippet/cpp/clist-class_5.cpp)]

## <a name="clistfindindex"></a><a name="findindex"></a>CList::FindIndex

Používá hodnotu *nIndex* jako index do seznamu.

```
POSITION FindIndex(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Nula na základě indexu list prvek, který má být nalezen.

### <a name="return-value"></a>Návratová hodnota

Hodnota POSITION, kterou lze použít pro iteraci nebo načtení ukazatele objektu; NULL, pokud *nIndex* je negativní nebo příliš velký.

### <a name="remarks"></a>Poznámky

Spustí sekvenční skenování z hlavy seznamu, zastavení na *n*th element.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#40](../../mfc/codesnippet/cpp/clist-class_6.cpp)]

## <a name="clistgetat"></a><a name="getat"></a>CList::Getat

Získá prvek seznamu na dané pozici.

```
TYPE& GetAt(POSITION position);
const TYPE& GetAt(POSITION position) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ objektu v seznamu.

*Pozici*<br/>
Pozice v seznamu prvku získat.

### <a name="return-value"></a>Návratová hodnota

Viz popis vrácené `GetHead`hodnoty pro .

### <a name="remarks"></a>Poznámky

`GetAt`vrátí prvek (nebo odkaz na prvek) přidružený k dané pozici. Není to stejné jako index a nelze pracovat na position hodnotu sami. Proměnná typu POSITION je klíčem k seznamu.

Je nutné zajistit, aby hodnota POZICE představovala platnou pozici v seznamu. Pokud je neplatný, pak ladicí verze Knihovny tříd Microsoft Foundation uplatňuje.

### <a name="example"></a>Příklad

  Viz příklad pro [CList::GetHeadPosition](#getheadposition).

## <a name="clistgetcount"></a><a name="getcount"></a>CList::GetCount

Získá počet prvků v tomto seznamu.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Celá hodnota obsahující počet prvků.

### <a name="remarks"></a>Poznámky

Volání této metody vygeneruje stejný výsledek jako [Metoda CList::GetSize.](#getsize)

### <a name="example"></a>Příklad

  Viz příklad pro [CList::RemoveHead](#removehead).

## <a name="clistgethead"></a><a name="gethead"></a>CList::Gethead

Získá head element (nebo odkaz na head element) tohoto seznamu.

```
const TYPE& GetHead() const;

TYPE& GetHead();
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ objektu v seznamu.

### <a name="return-value"></a>Návratová hodnota

Pokud je seznam **const**, `GetHead` vrátí kopii prvku v čele seznamu. To umožňuje funkci použít pouze na pravé straně příkazu přiřazení a chrání seznam před úpravou.

Pokud seznam není **const**, `GetHead` vrátí odkaz na prvek v čele seznamu. To umožňuje funkci, která má být použita na obou stranách příkazu přiřazení a tím umožňuje položky seznamu, které mají být změněny.

### <a name="remarks"></a>Poznámky

Před voláním `GetHead`je nutné zajistit, aby seznam nebyl prázdný. Pokud je seznam prázdný, bude uplatněna ladicí verze knihovny tříd Microsoft Foundation. Pomocí [isempty](#isempty) ověřte, zda seznam obsahuje prvky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#41](../../mfc/codesnippet/cpp/clist-class_7.cpp)]

## <a name="clistgetheadposition"></a><a name="getheadposition"></a>CList::GetheadPosition

Získá pozici head prvek tohoto seznamu.

```
POSITION GetHeadPosition() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota POSITION, kterou lze použít pro iteraci nebo načtení ukazatele objektu; Null, pokud je seznam prázdný.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#42](../../mfc/codesnippet/cpp/clist-class_8.cpp)]

## <a name="clistgetnext"></a><a name="getnext"></a>CList::GetNext

Získá prvek seznamu identifikovaný *rPosition*, pak nastaví *rPosition* na hodnotu POSITION další položky v seznamu.

```
TYPE& GetNext(POSITION& rPosition);
const TYPE& GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvků v seznamu.

*rPozice*<br/>
Odkaz na hodnotu POSITION vrácenou předchozím `GetNext` [voláním GetHeadPosition](#getheadposition)nebo jiným voláním členské funkce.

### <a name="return-value"></a>Návratová hodnota

Pokud je seznam **const**, `GetNext` vrátí kopii prvku seznamu. To umožňuje funkci použít pouze na pravé straně příkazu přiřazení a chrání seznam před úpravou.

Pokud seznam není **const**, `GetNext` vrátí odkaz na prvek seznamu. To umožňuje funkci, která má být použita na obou stranách příkazu přiřazení a tím umožňuje položky seznamu, které mají být změněny.

### <a name="remarks"></a>Poznámky

Můžete použít `GetNext` ve smyčce dopředné iterace, `GetHeadPosition` pokud `Find`navážete počáteční pozici s voláním nebo .

Je nutné zajistit, aby hodnota POZICE představovala platnou pozici v seznamu. Pokud je neplatný, pak ladicí verze Knihovny tříd Microsoft Foundation uplatňuje.

Pokud načtený prvek je poslední v seznamu, pak `rPosition` je nová hodnota nastavena na hodnotu NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#43](../../mfc/codesnippet/cpp/clist-class_9.cpp)]

## <a name="clistgetprev"></a><a name="getprev"></a>CList::GetPrev

Získá prvek seznamu `rPosition`identifikovaný v `rPosition` , pak nastaví na hodnotu POSITION předchozí položky v seznamu.

```
TYPE& GetPrev(POSITION& rPosition);
const TYPE& GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvků v seznamu.

*rPozice*<br/>
Odkaz na hodnotu POSITION vrácenou předchozím `GetPrev` nebo jiným voláním členské funkce.

### <a name="return-value"></a>Návratová hodnota

Pokud je seznam **const**, `GetPrev` vrátí kopii prvku v čele seznamu. To umožňuje funkci použít pouze na pravé straně příkazu přiřazení a chrání seznam před úpravou.

Pokud seznam není **const**, `GetPrev` vrátí odkaz na prvek seznamu. To umožňuje funkci, která má být použita na obou stranách příkazu přiřazení a tím umožňuje položky seznamu, které mají být změněny.

### <a name="remarks"></a>Poznámky

Můžete použít `GetPrev` ve smyčce zpětné iterace, pokud `GetTailPosition` navážete počáteční pozici s voláním nebo `Find`.

Je nutné zajistit, aby hodnota POZICE představovala platnou pozici v seznamu. Pokud je neplatný, pak ladicí verze Knihovny tříd Microsoft Foundation uplatňuje.

Pokud načtený prvek je první v seznamu, pak je nová hodnota *rPosition* nastavena na hodnotu NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#44](../../mfc/codesnippet/cpp/clist-class_10.cpp)]

## <a name="clistgetsize"></a><a name="getsize"></a>CList::GetSize

Vrátí počet prvků seznamu.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v seznamu

### <a name="remarks"></a>Poznámky

Volání této metody načíst počet prvků v seznamu.  Volání této metody vygeneruje stejný výsledek jako [Metoda CList::GetCount.](#getcount)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#45](../../mfc/codesnippet/cpp/clist-class_11.cpp)]

## <a name="clistgettail"></a><a name="gettail"></a>CList::GetTail

Získá `CObject` ukazatel, který představuje ocas prvek tohoto seznamu.

```
TYPE& GetTail();
const TYPE& GetTail() const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvků v seznamu.

### <a name="return-value"></a>Návratová hodnota

Viz popis vrácené hodnoty pro [GetHead](../../mfc/reference/coblist-class.md#gethead).

### <a name="remarks"></a>Poznámky

Před voláním `GetTail`je nutné zajistit, aby seznam nebyl prázdný. Pokud je seznam prázdný, bude uplatněna ladicí verze knihovny tříd Microsoft Foundation. Pomocí [isempty](../../mfc/reference/coblist-class.md#isempty) ověřte, zda seznam obsahuje prvky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#46](../../mfc/codesnippet/cpp/clist-class_12.cpp)]

## <a name="clistgettailposition"></a><a name="gettailposition"></a>CList::GetTailPosition

Získá pozici ocasprvek tohoto seznamu; Null, pokud je seznam prázdný.

```
POSITION GetTailPosition() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota POSITION, kterou lze použít pro iteraci nebo načtení ukazatele objektu; Null, pokud je seznam prázdný.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#47](../../mfc/codesnippet/cpp/clist-class_13.cpp)]

## <a name="clistinsertafter"></a><a name="insertafter"></a>CList::InsertAfter

Přidá prvek do tohoto seznamu za prvek na zadané pozici.

```
POSITION InsertAfter(POSITION position, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parametry

*Pozici*<br/>
Hodnota POSITION vrácená `GetNext`předchozím `GetPrev`voláním , nebo `Find` členské funkce.

*ARG_TYPE*<br/>
Parametr šablony určující typ prvku seznamu.

*newElement*<br/>
Prvek, který má být přidán do tohoto seznamu.

### <a name="return-value"></a>Návratová hodnota

Hodnota POSITION, kterou lze použít pro iteraci nebo načítání prvků seznamu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#48](../../mfc/codesnippet/cpp/clist-class_14.cpp)]

## <a name="clistinsertbefore"></a><a name="insertbefore"></a>CList::Insertbefore

Přidá prvek do tohoto seznamu před prvek na zadané pozici.

```
POSITION InsertBefore(POSITION position, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parametry

*Pozici*<br/>
Hodnota POSITION vrácená `GetNext`předchozím `GetPrev`voláním , nebo `Find` členské funkce.

*ARG_TYPE*<br/>
Parametr šablony určující typ prvku seznamu (může být odkaz).

*newElement*<br/>
Prvek, který má být přidán do tohoto seznamu.

### <a name="return-value"></a>Návratová hodnota

Hodnota POSITION, kterou lze použít pro iteraci nebo načítání prvků seznamu.

### <a name="remarks"></a>Poznámky

Pokud *position* pozice je NULL, prvek je vložen v čele seznamu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#49](../../mfc/codesnippet/cpp/clist-class_15.cpp)]

## <a name="clistisempty"></a><a name="isempty"></a>CList::Jeprázdný

Označuje, zda tento seznam neobsahuje žádné prvky.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je tento seznam prázdný; jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#50](../../mfc/codesnippet/cpp/clist-class_16.cpp)]

## <a name="clistremoveall"></a><a name="removeall"></a>CList::RemoveAll

Odebere všechny prvky z tohoto seznamu a uvolní přidružené paměti.

```cpp
void RemoveAll();
```

### <a name="remarks"></a>Poznámky

Pokud je seznam již prázdný, není generována žádná chyba.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#51](../../mfc/codesnippet/cpp/clist-class_17.cpp)]

## <a name="clistremoveat"></a><a name="removeat"></a>clist::Removeat

Odebere zadaný prvek z tohoto seznamu.

```cpp
void RemoveAt(POSITION position);
```

### <a name="parameters"></a>Parametry

*Pozici*<br/>
Umístění prvku, který má být odebrán ze seznamu.

### <a name="remarks"></a>Poznámky

Je nutné zajistit, aby hodnota POZICE představovala platnou pozici v seznamu. Pokud je neplatný, pak ladicí verze Knihovny tříd Microsoft Foundation uplatňuje.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#52](../../mfc/codesnippet/cpp/clist-class_18.cpp)]

## <a name="clistremovehead"></a><a name="removehead"></a>CList::RemoveHead

Odebere prvek z hlavy seznamu a vrátí na něj ukazatel.

```
TYPE RemoveHead();
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvků v seznamu.

### <a name="return-value"></a>Návratová hodnota

Prvek dříve v čele seznamu.

### <a name="remarks"></a>Poznámky

Před voláním `RemoveHead`je nutné zajistit, aby seznam nebyl prázdný. Pokud je seznam prázdný, bude uplatněna ladicí verze knihovny tříd Microsoft Foundation. Pomocí [isempty](#isempty) ověřte, zda seznam obsahuje prvky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#53](../../mfc/codesnippet/cpp/clist-class_19.cpp)]

## <a name="clistremovetail"></a><a name="removetail"></a>CList::RemoveTail

Odebere prvek z ocasu seznamu a vrátí na něj ukazatel.

```
TYPE RemoveTail();
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvků v seznamu.

### <a name="return-value"></a>Návratová hodnota

Prvek, který byl na konci seznamu.

### <a name="remarks"></a>Poznámky

Před voláním `RemoveTail`je nutné zajistit, aby seznam nebyl prázdný. Pokud je seznam prázdný, bude uplatněna ladicí verze knihovny tříd Microsoft Foundation. Pomocí [isempty](#isempty) ověřte, zda seznam obsahuje prvky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#54](../../mfc/codesnippet/cpp/clist-class_20.cpp)]

## <a name="clistsetat"></a><a name="setat"></a>CList:Setat

Proměnná typu POSITION je klíčem k seznamu.

```cpp
void SetAt(POSITION pos, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parametry

*Pos*<br/>
POZICE prvku, který má být nastaven.

*ARG_TYPE*<br/>
Parametr šablony určující typ prvku seznamu (může být odkaz).

*newElement*<br/>
Prvek, který má být přidán do seznamu.

### <a name="remarks"></a>Poznámky

Není to stejné jako index a nelze pracovat na position hodnotu sami. `SetAt`zapíše prvek na zadanou pozici v seznamu.

Je nutné zajistit, aby hodnota POZICE představovala platnou pozici v seznamu. Pokud je neplatný, pak ladicí verze Knihovny tříd Microsoft Foundation uplatňuje.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#55](../../mfc/codesnippet/cpp/clist-class_21.cpp)]

## <a name="see-also"></a>Viz také

[Odběr vzorku knihovny MFC](../../overview/visual-cpp-samples.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CMap](../../mfc/reference/cmap-class.md)<br/>
[Třída CArray](../../mfc/reference/carray-class.md)
