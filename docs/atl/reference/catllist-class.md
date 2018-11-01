---
title: Catllist – třída
ms.date: 11/04/2016
f1_keywords:
- CAtlList
- ATLCOLL/ATL::CAtlList
- ATLCOLL/ATL::CAtlList::INARGTYPE
- ATLCOLL/ATL::CAtlList::CAtlList
- ATLCOLL/ATL::CAtlList::AddHead
- ATLCOLL/ATL::CAtlList::AddHeadList
- ATLCOLL/ATL::CAtlList::AddTail
- ATLCOLL/ATL::CAtlList::AddTailList
- ATLCOLL/ATL::CAtlList::AssertValid
- ATLCOLL/ATL::CAtlList::Find
- ATLCOLL/ATL::CAtlList::FindIndex
- ATLCOLL/ATL::CAtlList::GetAt
- ATLCOLL/ATL::CAtlList::GetCount
- ATLCOLL/ATL::CAtlList::GetHead
- ATLCOLL/ATL::CAtlList::GetHeadPosition
- ATLCOLL/ATL::CAtlList::GetNext
- ATLCOLL/ATL::CAtlList::GetPrev
- ATLCOLL/ATL::CAtlList::GetTail
- ATLCOLL/ATL::CAtlList::GetTailPosition
- ATLCOLL/ATL::CAtlList::InsertAfter
- ATLCOLL/ATL::CAtlList::InsertBefore
- ATLCOLL/ATL::CAtlList::IsEmpty
- ATLCOLL/ATL::CAtlList::MoveToHead
- ATLCOLL/ATL::CAtlList::MoveToTail
- ATLCOLL/ATL::CAtlList::RemoveAll
- ATLCOLL/ATL::CAtlList::RemoveAt
- ATLCOLL/ATL::CAtlList::RemoveHead
- ATLCOLL/ATL::CAtlList::RemoveHeadNoReturn
- ATLCOLL/ATL::CAtlList::RemoveTail
- ATLCOLL/ATL::CAtlList::RemoveTailNoReturn
- ATLCOLL/ATL::CAtlList::SetAt
- ATLCOLL/ATL::CAtlList::SwapElements
helpviewer_keywords:
- CAtlList class
ms.assetid: 09e98053-64b2-4efa-99ab-d0542caaf981
ms.openlocfilehash: 9e657bbf375a8babf1c03cc7254310956131d62b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449363"
---
# <a name="catllist-class"></a>Catllist – třída

Tato třída poskytuje metody pro vytváření a správa seznamu objektů.

## <a name="syntax"></a>Syntaxe

```
template<typename E, class ETraits = CElementTraits<E>>
class CAtlList
```

#### <a name="parameters"></a>Parametry

*E*<br/>
Typ elementu.

*ETraits*<br/>
Kód použitý má zkopírovat nebo přesunout prvky. Zobrazit [celementtraits – třída](../../atl/reference/celementtraits-class.md) další podrobnosti.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|[CAtlList::INARGTYPE](#inargtype)||

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAtlList::CAtlList](#catllist)|Konstruktor|
|[Catllist –:: ~ catllist –](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAtlList::AddHead](#addhead)|Voláním této metody lze přidat element do začátku seznamu.|
|[CAtlList::AddHeadList](#addheadlist)|Voláním této metody lze přidat existující seznam k začátku seznamu.|
|[CAtlList::AddTail](#addtail)|Voláním této metody lze přidat element do zadní části tohoto seznamu.|
|[CAtlList::AddTailList](#addtaillist)|Voláním této metody lze přidat existující seznam na konci tohoto seznamu.|
|[CAtlList::AssertValid](#assertvalid)|Voláním této metody zkontrolujte, že v seznamu je platný.|
|[CAtlList::Find](#find)|Voláním této metody lze pro zadaný element v seznamu vyhledejte.|
|[CAtlList::FindIndex](#findindex)|Volejte tuto metodu za účelem získání pozici elementu, danou hodnotu indexu.|
|[CAtlList::GetAt](#getat)|Volání této metody k vrácení prvku na určené pozici v seznamu.|
|[CAtlList::GetCount](#getcount)|Voláním této metody vrátí počet objektů v seznamu.|
|[CAtlList::GetHead](#gethead)|Voláním této metody vrátí prvek na začátku seznamu.|
|[CAtlList::GetHeadPosition](#getheadposition)|Volejte tuto metodu za účelem získání pozici první pozice v seznamu.|
|[CAtlList::GetNext](#getnext)|Voláním této metody vrátit další prvek ze seznamu.|
|[CAtlList::GetPrev](#getprev)|Voláním této metody vrátit předchozí prvek ze seznamu.|
|[CAtlList::GetTail](#gettail)|Voláním této metody vrátí prvek na konec seznamu.|
|[CAtlList::GetTailPosition](#gettailposition)|Volejte tuto metodu za účelem získání pozice konec seznamu.|
|[CAtlList::InsertAfter](#insertafter)|Voláním této metody lze vložit nový prvek do seznamu za určené pozici.|
|[CAtlList::InsertBefore](#insertbefore)|Volejte tuto metodu za účelem vloží nový prvek do seznamu před určené pozici.|
|[CAtlList::IsEmpty](#isempty)|Volejte tuto metodu za účelem určení, zda je seznam prázdný.|
|[CAtlList::MoveToHead](#movetohead)|Voláním této metody lze přesunout zadaný prvek na začátku seznamu.|
|[CAtlList::MoveToTail](#movetotail)|Voláním této metody lze přesunout zadaný prvek na konec seznamu.|
|[CAtlList::RemoveAll](#removeall)|Volejte tuto metodu, která odebere všechny prvky ze seznamu.|
|[CAtlList::RemoveAt](#removeat)|Voláním této metody lze odebrat ze seznamu jediný prvek.|
|[CAtlList::RemoveHead](#removehead)|Volejte tuto metodu za účelem odstranění prvku na začátku seznamu.|
|[CAtlList::RemoveHeadNoReturn](#removeheadnoreturn)|Volejte tuto metodu za účelem odebrání prvek na začátku seznamu bez návratová hodnota.|
|[CAtlList::RemoveTail](#removetail)|Volejte tuto metodu za účelem odebrání prvek na konec seznamu.|
|[CAtlList::RemoveTailNoReturn](#removetailnoreturn)|Volejte tuto metodu za účelem odebrání prvek na konec seznamu bez návratová hodnota.|
|[CAtlList::SetAt](#setat)|Voláním této metody nastavte hodnotu prvku na dané pozici v seznamu.|
|[CAtlList::SwapElements](#swapelements)|Voláním této metody lze zaměnit prvky v seznamu.|

## <a name="remarks"></a>Poznámky

`CAtlList` Třídy podporuje seřazené seznam nejedinečných objektů dostupných postupně sekvenčně nebo podle hodnoty. `CAtlList` seznamy se chovat jako dvakrát propojené seznamy. Každý seznam obsahuje head a koncovou část a nové prvky (nebo v některých případech seznamů) lze přidat na oba konce tohoto seznamu, nebo vložit před nebo po konkrétní prvky.

Většina `CAtlList` metody změní použití hodnoty pozice. Tato hodnota se používá metody skutečná paměť umístění, kde prvky jsou uloženy a by neměly být vypočtena nebo předpovědět přímo odkazovat. Pokud je potřeba přístup *n*tý prvek v seznamu Metoda [CAtlList::FindIndex](#findindex) vrátí odpovídající hodnotu pozice pro daný index. Metody [CAtlList::GetNext](#getnext) a [CAtlList::GetPrev](#getprev) lze použít k iteraci v rámci objektů v seznamu.

Další informace týkající se třídy kolekcí k dispozici s technologií ATL naleznete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

##  <a name="addhead"></a>  CAtlList::AddHead

Voláním této metody lze přidat element do začátku seznamu.

```
POSITION AddHead();
POSITION AddHead(INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*– Element*<br/>
Nový prvek.

### <a name="return-value"></a>Návratová hodnota

Vrátí pozici nově přidaný prvek.

### <a name="remarks"></a>Poznámky

Pokud je použita první verze, je prázdný element vytvořený pomocí jeho výchozí konstruktor, nikoli jeho kopírovací konstruktor.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#13](../../atl/codesnippet/cpp/catllist-class_1.cpp)]

##  <a name="addheadlist"></a>  CAtlList::AddHeadList

Voláním této metody lze přidat existující seznam k začátku seznamu.

```
void AddHeadList(const CAtlList<E, ETraits>* plNew);
```

### <a name="parameters"></a>Parametry

*plNew*<br/>
Seznam, který chcete přidat.

### <a name="remarks"></a>Poznámky

V seznamu na které odkazuje *plNew* se vloží na začátek seznamu existujících. V sestavení pro ladění k selhání kontrolního výrazu dojde, pokud *plNew* je rovna hodnotě NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#14](../../atl/codesnippet/cpp/catllist-class_2.cpp)]

##  <a name="addtail"></a>  CAtlList::AddTail

Voláním této metody lze přidat element do zadní části tohoto seznamu.

```
POSITION AddTail();
POSITION AddTail(INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*– Element*<br/>
Elementu, který chcete přidat.

### <a name="return-value"></a>Návratová hodnota

Vrátí POZICI nově přidaný prvek.

### <a name="remarks"></a>Poznámky

Pokud je použita první verze, je prázdný element vytvořený pomocí jeho výchozí konstruktor, nikoli jeho kopírovací konstruktor. Bude prvek přidán na konec seznamu a tak ho teď bude konci. Tuto metodu lze použít s prázdným seznamem.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#15](../../atl/codesnippet/cpp/catllist-class_3.cpp)]

##  <a name="addtaillist"></a>  CAtlList::AddTailList

Voláním této metody lze přidat existující seznam na konci tohoto seznamu.

```
void AddTailList(const CAtlList<E, ETraits>* plNew);
```

### <a name="parameters"></a>Parametry

*plNew*<br/>
Seznam, který chcete přidat.

### <a name="remarks"></a>Poznámky

V seznamu na které odkazuje *plNew* je vložen za posledním prvkem (pokud existuje) v seznamu objektů. Po posledním prvku v *plNew* seznam stane proto funkce tail. V sestavení pro ladění k selhání kontrolního výrazu dojde, pokud *plNew* je rovna hodnotě NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#16](../../atl/codesnippet/cpp/catllist-class_4.cpp)]

##  <a name="assertvalid"></a>  CAtlList::AssertValid

Voláním této metody zkontrolujte, že v seznamu je platný.

```
void AssertValid() const;
```

### <a name="remarks"></a>Poznámky

V sestavení ladění bude selhání kontrolního výrazu dojít, pokud objekt seznamu není platný. Aby byla platná, musí mít prázdný seznam, head a tail odkazuje na hodnotu NULL a seznam, který není prázdný musí mít hlavní i funkce tail odkazující na platné adresy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#17](../../atl/codesnippet/cpp/catllist-class_5.cpp)]

##  <a name="catllist"></a>  CAtlList::CAtlList

Konstruktor

```
CAtlList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parametry

*nBlockSize*<br/>
Velikost bloku.

### <a name="remarks"></a>Poznámky

Konstruktor pro `CAtlList` objektu. Velikost bloku je míra množství paměti přidělené, pokud je nutné použít nový prvek. Bloky o větší velikosti snížit volání rutiny přidělení paměti, ale spotřebovávají více prostředků.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#18](../../atl/codesnippet/cpp/catllist-class_6.cpp)]

##  <a name="dtor"></a>  Catllist –:: ~ catllist –

Destruktor.

```
~CAtlList() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky, včetně volání [CAtlList::RemoveAll](#removeall) odebrat všechny prvky ze seznamu.

V sestavení pro ladění k selhání kontrolního výrazu dojde, pokud seznam stále obsahuje některé prvky po volání `RemoveAll`.

##  <a name="find"></a>  CAtlList::Find

Voláním této metody lze pro zadaný element v seznamu vyhledejte.

```
POSITION Find(INARGTYPE element, POSITION posStartAfter = NULL) const throw();
```

### <a name="parameters"></a>Parametry

*– Element*<br/>
Elementu, který chcete nalézt v seznamu.

*posStartAfter*<br/>
Počáteční pozice pro vyhledávání. Pokud není zadána žádná hodnota, začíná hledání head element.

### <a name="return-value"></a>Návratová hodnota

Vrací hodnotu pozice prvku, pokud najde, jinak vrátí hodnotu NULL.

### <a name="remarks"></a>Poznámky

V sestavení ladění, dojde k selhání kontrolního výrazu objekt seznamu není platný nebo pokud *posStartAfter* hodnota je mimo rozsah.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#19](../../atl/codesnippet/cpp/catllist-class_7.cpp)]

##  <a name="findindex"></a>  CAtlList::FindIndex

Volejte tuto metodu za účelem získání pozici elementu, danou hodnotu indexu.

```
POSITION FindIndex(size_t iElement) const throw();
```

### <a name="parameters"></a>Parametry

*iElement*<br/>
Index založený na nule element seznamu požadavků.

### <a name="return-value"></a>Návratová hodnota

Vrátí odpovídající hodnota pozice nebo hodnota NULL, pokud *iElement* je mimo rozsah.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí POZICI umožňuje přístup k odpovídající hodnotě daný index, *n*tý prvek v seznamu.

V sestavení ladění bude selhání kontrolního výrazu dojít, pokud objekt seznamu není platný.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#20](../../atl/codesnippet/cpp/catllist-class_8.cpp)]

##  <a name="getat"></a>  CAtlList::GetAt

Volání této metody k vrácení prvku na určené pozici v seznamu.

```
E& GetAt(POSITION pos) throw();
const E& GetAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parametry

*POS*<br/>
Hodnota pozice, zadání konkrétní elementu.

### <a name="return-value"></a>Návratová hodnota

Odkaz na nebo kopie elementu.

### <a name="remarks"></a>Poznámky

Pokud je seznam **const**, `GetAt` vrátí kopii objektu elementu. To umožňuje metoda má být použit pouze na pravé straně příkazu přiřazení a chrání před úpravy seznamu.

Pokud seznam není **const**, `GetAt` vrátí odkaz na element. To umožňuje metody, který se má použít na obou stranách příkazu přiřazení a tím umožňuje položky seznamu, který má být upraven.

V sestavení pro ladění k selhání kontrolního výrazu dojde, pokud *pos* je rovna hodnotě NULL.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlList::FindIndex](#findindex).

##  <a name="getcount"></a>  CAtlList::GetCount

Voláním této metody vrátí počet objektů v seznamu.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet prvků v seznamu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlList::Find](#find).

##  <a name="gethead"></a>  CAtlList::GetHead

Voláním této metody vrátí prvek na začátku seznamu.

```
E& GetHead() throw();
const E& GetHead() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na nebo kopii tohoto prvku na začátku seznamu.

### <a name="remarks"></a>Poznámky

Pokud je seznam **const**, `GetHead` vrátí kopii objektu prvek na začátku seznamu. To umožňuje metoda má být použit pouze na pravé straně příkazu přiřazení a chrání před úpravy seznamu.

Pokud seznam není **const**, `GetHead` vrátí odkaz na prvek na začátku seznamu. To umožňuje metody, který se má použít na obou stranách příkazu přiřazení a tím umožňuje položky seznamu, který má být upraven.

V sestavení ladění bude selhání kontrolního výrazu dojít, pokud první pozice v seznamu odkazuje na hodnotu NULL.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlList::AddHead](#addhead).

##  <a name="getheadposition"></a>  CAtlList::GetHeadPosition

Volejte tuto metodu za účelem získání pozici první pozice v seznamu.

```
POSITION GetHeadPosition() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí POZICI hodnotu odpovídající prvek na začátku seznamu.

### <a name="remarks"></a>Poznámky

Pokud je seznam prázdný, vrácená hodnota je NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#21](../../atl/codesnippet/cpp/catllist-class_9.cpp)]

##  <a name="getnext"></a>  CAtlList::GetNext

Voláním této metody vrátit další prvek ze seznamu.

```
E& GetNext(POSITION& pos) throw();
const E& GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parametry

*POS*<br/>
Hodnota pozice, vrácený z předchozího volání `GetNext`, [CAtlList::GetHeadPosition](#getheadposition), nebo jiné `CAtlList` metody.

### <a name="return-value"></a>Návratová hodnota

Pokud je seznam **const**, `GetNext` vrátí kopii objektu další prvek seznamu. To umožňuje metoda má být použit pouze na pravé straně příkazu přiřazení a chrání před úpravy seznamu.

Pokud seznam není **const**, `GetNext` vrátí odkaz na další prvek seznamu. To umožňuje metody, který se má použít na obou stranách příkazu přiřazení a tím umožňuje položky seznamu, který má být upraven.

### <a name="remarks"></a>Poznámky

Čítač pozice *pos*, je aktualizován, aby ukazoval na další prvek v seznamu, nebo hodnota NULL, pokud neexistují žádné další prvky. V sestavení pro ladění k selhání kontrolního výrazu dojde, pokud *pos* je rovna hodnotě NULL.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlList::GetHeadPosition](#getheadposition).

##  <a name="getprev"></a>  CAtlList::GetPrev

Voláním této metody vrátit předchozí prvek ze seznamu.

```
E& GetPrev(POSITION& pos) throw();
const E& GetPrev(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parametry

*POS*<br/>
Hodnota pozice, vrácený z předchozího volání `GetPrev`, [CAtlList::GetTailPosition](#gettailposition), nebo jiné `CAtlList` metody.

### <a name="return-value"></a>Návratová hodnota

Pokud je seznam **const**, `GetPrev` vrátí kopii objektu element seznamu. To umožňuje metoda má být použit pouze na pravé straně příkazu přiřazení a chrání před úpravy seznamu.

Pokud seznam není **const**, `GetPrev` vrátí odkaz na element seznamu. To umožňuje metody, který se má použít na obou stranách příkazu přiřazení a tím umožňuje položky seznamu, který má být upraven.

### <a name="remarks"></a>Poznámky

Čítač pozice *pos*, je aktualizován, aby ukazoval na předchozí prvek v seznamu, nebo hodnota NULL, pokud neexistují žádné další prvky. V sestavení pro ladění k selhání kontrolního výrazu dojde, pokud *pos* je rovna hodnotě NULL.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlList::GetTailPosition](#gettailposition).

##  <a name="gettail"></a>  CAtlList::GetTail

Voláním této metody vrátí prvek na konec seznamu.

```
E& GetTail() throw();
const E& GetTail() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na nebo kopie, prvek na konec seznamu.

### <a name="remarks"></a>Poznámky

Pokud je seznam **const**, `GetTail` vrátí kopii objektu prvek na začátku seznamu. To umožňuje metoda má být použit pouze na pravé straně příkazu přiřazení a chrání před úpravy seznamu.

Pokud seznam není **const**, `GetTail` vrátí odkaz na prvek na začátku seznamu. To umožňuje metody, který se má použít na obou stranách příkazu přiřazení a tím umožňuje položky seznamu, který má být upraven.

V sestavení ladění dojde k selhání kontrolního výrazu Pokud konec seznamu odkazuje na hodnotu NULL.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlList::AddTail](#addtail).

##  <a name="gettailposition"></a>  CAtlList::GetTailPosition

Volejte tuto metodu za účelem získání pozice konec seznamu.

```
POSITION GetTailPosition() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí POZICI hodnotu odpovídající prvek na konec seznamu.

### <a name="remarks"></a>Poznámky

Pokud je seznam prázdný, vrácená hodnota je NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#22](../../atl/codesnippet/cpp/catllist-class_10.cpp)]

##  <a name="inargtype"></a>  CAtlList::INARGTYPE

Typ použitý při prvek se předá jako vstupní argument.

```
typedef ETraits::INARGTYPE INARGTYPE;
```

##  <a name="insertafter"></a>  CAtlList::InsertAfter

Voláním této metody lze vložit nový prvek do seznamu za určené pozici.

```
POSITION InsertAfter(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*POS*<br/>
Hodnota pozice, po jejímž uplynutí se vloží nový prvek.

*– Element*<br/>
Element, který má být vložen.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu POZICI nového elementu.

### <a name="remarks"></a>Poznámky

V sestavení ladění dojde k selhání kontrolního výrazu Pokud seznam není platná, pokud insert selže nebo pokud je proveden pokus o vložení prvku po konci.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#23](../../atl/codesnippet/cpp/catllist-class_11.cpp)]

##  <a name="insertbefore"></a>  CAtlList::InsertBefore

Volejte tuto metodu za účelem vloží nový prvek do seznamu před určené pozici.

```
POSITION InsertBefore(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*POS*<br/>
Nový prvek se vloží do seznamu před tuto hodnotu pozice.

*– Element*<br/>
Element, který má být vložen.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu POZICI nového elementu.

### <a name="remarks"></a>Poznámky

V sestavení ladění dojde k selhání kontrolního výrazu Pokud seznam není platná, pokud insert selže nebo pokud je proveden pokus o vložení elementu před první pozice.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#24](../../atl/codesnippet/cpp/catllist-class_12.cpp)]

##  <a name="isempty"></a>  CAtlList::IsEmpty

Volejte tuto metodu za účelem určení, zda je seznam prázdný.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí true, pokud seznam neobsahuje žádné objekty, jinak hodnota false.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#25](../../atl/codesnippet/cpp/catllist-class_13.cpp)]

##  <a name="movetohead"></a>  CAtlList::MoveToHead

Voláním této metody lze přesunout zadaný prvek na začátku seznamu.

```
void MoveToHead(POSITION pos) throw();
```

### <a name="parameters"></a>Parametry

*POS*<br/>
Hodnota pozice prvku, který chcete přesunout.

### <a name="remarks"></a>Poznámky

Zadaný element se přesune z aktuálního umístění do začátku seznamu. V sestavení pro ladění k selhání kontrolního výrazu dojde, pokud *pos* je rovna hodnotě NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#26](../../atl/codesnippet/cpp/catllist-class_14.cpp)]

##  <a name="movetotail"></a>  CAtlList::MoveToTail

Voláním této metody lze přesunout zadaný prvek na konec seznamu.

```
void MoveToTail(POSITION pos) throw();
```

### <a name="parameters"></a>Parametry

*POS*<br/>
Hodnota pozice prvku, který chcete přesunout.

### <a name="remarks"></a>Poznámky

Zadaný element se přesune z aktuálního umístění na konec seznamu. V sestavení pro ladění k selhání kontrolního výrazu dojde, pokud *pos* je rovna hodnotě NULL.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlList::MoveToHead](#movetohead).

##  <a name="removeall"></a>  CAtlList::RemoveAll

Volejte tuto metodu, která odebere všechny prvky ze seznamu.

```
void RemoveAll() throw();
```

### <a name="remarks"></a>Poznámky

Tato metoda odebere všechny prvky ze seznamu a uvolní přidělené paměti. V sestaveních ladí ATLASSERT, bude vyvolána pokud se neodstraní všechny elementy nebo pokud byla poškozena struktura seznamu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlList::IsEmpty](#isempty).

##  <a name="removeat"></a>  CAtlList::RemoveAt

Voláním této metody lze odebrat ze seznamu jediný prvek.

```
void RemoveAt(POSITION pos) throw();
```

### <a name="parameters"></a>Parametry

*POS*<br/>
Hodnota pozice prvku, který chcete odebrat.

### <a name="remarks"></a>Poznámky

Element odkazuje *pos* Odebereme, vystavení a uvolnění paměti. To je nepřijatelné využívat `RemoveAt` odebrat head nebo konec seznamu.

V sestavení ladění dojde k selhání kontrolního výrazu Pokud seznam není platný nebo pokud prvek způsobí, že se seznamem, aby přístup k paměti, která není součástí struktury seznamu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#27](../../atl/codesnippet/cpp/catllist-class_15.cpp)]

##  <a name="removehead"></a>  CAtlList::RemoveHead

Volejte tuto metodu za účelem odstranění prvku na začátku seznamu.

```
E RemoveHead();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí prvek na začátku seznamu.

### <a name="remarks"></a>Poznámky

Head element se odstraní ze seznamu a uvolnění paměti. Kopii tohoto elementu je vrácena. V sestavení ladění dojde k selhání kontrolního výrazu Pokud je seznam prázdný.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#28](../../atl/codesnippet/cpp/catllist-class_16.cpp)]

##  <a name="removeheadnoreturn"></a>  CAtlList::RemoveHeadNoReturn

Volejte tuto metodu za účelem odebrání prvek na začátku seznamu bez návratová hodnota.

```
void RemoveHeadNoReturn() throw();
```

### <a name="remarks"></a>Poznámky

Head element se odstraní ze seznamu a uvolnění paměti. V sestavení ladění dojde k selhání kontrolního výrazu Pokud je seznam prázdný.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlList::IsEmpty](#isempty).

##  <a name="removetail"></a>  CAtlList::RemoveTail

Volejte tuto metodu za účelem odebrání prvek na konec seznamu.

```
E RemoveTail();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí prvek na konec seznamu.

### <a name="remarks"></a>Poznámky

Tail prvek je odstraněn ze seznamu a uvolnění paměti. Kopii tohoto elementu je vrácena. V sestavení ladění dojde k selhání kontrolního výrazu Pokud je seznam prázdný.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#29](../../atl/codesnippet/cpp/catllist-class_17.cpp)]

##  <a name="removetailnoreturn"></a>  CAtlList::RemoveTailNoReturn

Volejte tuto metodu za účelem odebrání prvek na konec seznamu bez návratová hodnota.

```
void RemoveTailNoReturn() throw();
```

### <a name="remarks"></a>Poznámky

Tail prvek je odstraněn ze seznamu a uvolnění paměti. V sestavení ladění dojde k selhání kontrolního výrazu Pokud je seznam prázdný.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlList::IsEmpty](#isempty).

##  <a name="setat"></a>  CAtlList::SetAt

Voláním této metody nastavte hodnotu prvku na dané pozici v seznamu.

```
void SetAt(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*POS*<br/>
Hodnota pozice odpovídá elementu, který chcete změnit.

*– Element*<br/>
Nová hodnota prvku.

### <a name="remarks"></a>Poznámky

Nahradí existující hodnotu *element*. V sestavení pro ladění k selhání kontrolního výrazu dojde, pokud *pos* je rovna hodnotě NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#30](../../atl/codesnippet/cpp/catllist-class_18.cpp)]

##  <a name="swapelements"></a>  CAtlList::SwapElements

Voláním této metody lze zaměnit prvky v seznamu.

```
void SwapElements(POSITION pos1, POSITION pos2) throw();
```

### <a name="parameters"></a>Parametry

*pos1*<br/>
První hodnota pozice.

*pos2*<br/>
Druhá hodnota pozice.

### <a name="remarks"></a>Poznámky

Zamění prvky ve dvou pozic určený. V sestavení ladění bude selhání kontrolního výrazu dojít, pokud buď hodnota pozice se nerovná hodnotě NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#31](../../atl/codesnippet/cpp/catllist-class_19.cpp)]

## <a name="see-also"></a>Viz také

[CList – třída](../../mfc/reference/clist-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
