---
title: CAtlList – třída
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
ms.openlocfilehash: 2c16713af11a915772085165ed294cba4ae337f2
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168043"
---
# <a name="catllist-class"></a>CAtlList – třída

Tato třída poskytuje metody pro vytváření a správu objektu seznamu.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename E, class ETraits = CElementTraits<E>>
class CAtlList
```

### <a name="parameters"></a>Parametry

*Cerebrální*<br/>
Typ elementu.

*ETraits*<br/>
Kód použitý ke zkopírování nebo přesunutí prvků. Další podrobnosti najdete v tématu [Třída CElementTraits](../../atl/reference/celementtraits-class.md) .

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Název|Popis|
|----------|-----------------|
|[CAtlList::INARGTYPE](#inargtype)||

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAtlList::CAtlList](#catllist)|Konstruktor|
|[CAtlList:: ~ CAtlList](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAtlList::AddHead](#addhead)|Voláním této metody přidáte prvek do záhlaví seznamu.|
|[CAtlList::AddHeadList](#addheadlist)|Voláním této metody přidáte existující seznam do záhlaví seznamu.|
|[CAtlList:: AddTail –](#addtail)|Voláním této metody přidáte element na konec seznamu.|
|[CAtlList::AddTailList](#addtaillist)|Voláním této metody přidáte existující seznam na konec tohoto seznamu.|
|[CAtlList::AssertValid](#assertvalid)|Voláním této metody potvrďte, že seznam je platný.|
|[CAtlList:: Find](#find)|Voláním této metody můžete hledat v seznamu zadaného elementu.|
|[CAtlList:: FindIndex –](#findindex)|Zavolejte tuto metodu pro získání pozice prvku s ohledem na hodnotu indexu.|
|[CAtlList::GetAt](#getat)|Voláním této metody vrátí prvek na zadané pozici v seznamu.|
|[CAtlList:: GetCount](#getcount)|Voláním této metody vrátíte počet objektů v seznamu.|
|[CAtlList:: GetHead](#gethead)|Voláním této metody vrátíte prvek v záhlaví seznamu.|
|[CAtlList::GetHeadPosition](#getheadposition)|Voláním této metody získáte pozici záhlaví seznamu.|
|[CAtlList:: GetNext](#getnext)|Voláním této metody vrátíte další prvek ze seznamu.|
|[CAtlList:: getpředchozí](#getprev)|Voláním této metody vrátíte předchozí prvek ze seznamu.|
|[CAtlList:: GetTail](#gettail)|Zavolejte tuto metodu, chcete-li vrátit prvek na konec seznamu.|
|[CAtlList::GetTailPosition](#gettailposition)|Voláním této metody získá pozice konce seznamu.|
|[CAtlList::InsertAfter](#insertafter)|Zavolejte tuto metodu pro vložení nového elementu do seznamu po zadané pozici.|
|[CAtlList::InsertBefore](#insertbefore)|Zavolejte tuto metodu pro vložení nového prvku do seznamu před určenou pozicí.|
|[CAtlList::-Empty](#isempty)|Voláním této metody určíte, zda je seznam prázdný.|
|[CAtlList::MoveToHead](#movetohead)|Voláním této metody přesunete zadaný element na záhlaví seznamu.|
|[CAtlList::MoveToTail](#movetotail)|Zavolejte tuto metodu pro přesun zadaného elementu na konec seznamu.|
|[CAtlList::RemoveAll](#removeall)|Voláním této metody odeberete všechny prvky ze seznamu.|
|[CAtlList:: funkce RemoveAt](#removeat)|Zavolejte tuto metodu pro odebrání jednoho prvku ze seznamu.|
|[CAtlList::RemoveHead](#removehead)|Zavolejte tuto metodu pro odebrání elementu v záhlaví seznamu.|
|[CAtlList::RemoveHeadNoReturn](#removeheadnoreturn)|Zavolejte tuto metodu pro odebrání elementu na začátku seznamu bez vrácení hodnoty.|
|[CAtlList::RemoveTail](#removetail)|Zavolejte tuto metodu pro odebrání elementu na konci seznamu.|
|[CAtlList::RemoveTailNoReturn](#removetailnoreturn)|Zavolejte tuto metodu pro odebrání elementu na konci seznamu bez vrácení hodnoty.|
|[CAtlList::SetAt](#setat)|Voláním této metody nastavíte hodnotu prvku na dané pozici v seznamu.|
|[CAtlList::SwapElements](#swapelements)|Zavolejte tuto metodu pro prohození prvků v seznamu.|

## <a name="remarks"></a>Poznámky

`CAtlList` Třída podporuje seřazené seznamy nejedinečných objektů, které jsou přístupné sekvenčně nebo podle hodnoty. `CAtlList`seznamy se chovají jako dvojité propojené seznamy. Každý seznam má hlavní a koncovou položku a nové prvky (nebo seznamy v některých případech) mohou být přidány na konec seznamu nebo vloženy před nebo za konkrétní prvky.

Většina `CAtlList` metod používá hodnotu pozice. Tuto hodnotu používají metody pro odkazování na skutečné umístění v paměti, kde jsou prvky uloženy a neměly by být vypočteny nebo předpovězeny přímo. Pokud je nutné přístup k elementu *n*th v seznamu, metoda [CAtlList:: FindIndex –](#findindex) vrátí odpovídající hodnotu pozice pro daný index. Metody [CAtlList:: GetNext](#getnext) a [CAtlList:: getpředchozí](#getprev) lze použít k iterování objektů v seznamu.

Další informace o třídách kolekcí dostupných v knihovně ATL naleznete v tématu [třídy kolekcí ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll. h

## <a name="catllistaddhead"></a><a name="addhead"></a>CAtlList::AddHead

Voláním této metody přidáte prvek do záhlaví seznamu.

```cpp
POSITION AddHead();
POSITION AddHead(INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*objekt*<br/>
Nový prvek.

### <a name="return-value"></a>Návratová hodnota

Vrátí pozici nově přidaného prvku.

### <a name="remarks"></a>Poznámky

Pokud je použita první verze, prázdný prvek je vytvořen pomocí výchozího konstruktoru, nikoli jeho kopírovací konstruktor.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#13](../../atl/codesnippet/cpp/catllist-class_1.cpp)]

## <a name="catllistaddheadlist"></a><a name="addheadlist"></a>CAtlList::AddHeadList

Voláním této metody přidáte existující seznam do záhlaví seznamu.

```cpp
void AddHeadList(const CAtlList<E, ETraits>* plNew);
```

### <a name="parameters"></a>Parametry

*plNew*<br/>
Seznam, který se má přidat

### <a name="remarks"></a>Poznámky

Seznam, na který odkazuje *plNew* , je vložen na začátek existujícího seznamu. V sestavení ladění dojde k selhání kontrolního výrazu, pokud je *plNew* ROVNO hodnotě null.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#14](../../atl/codesnippet/cpp/catllist-class_2.cpp)]

## <a name="catllistaddtail"></a><a name="addtail"></a>CAtlList:: AddTail –

Voláním této metody přidáte element na konec seznamu.

```cpp
POSITION AddTail();
POSITION AddTail(INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*objekt*<br/>
Prvek, který chcete přidat.

### <a name="return-value"></a>Návratová hodnota

Vrátí pozici nově přidaného prvku.

### <a name="remarks"></a>Poznámky

Pokud je použita první verze, prázdný prvek je vytvořen pomocí výchozího konstruktoru, nikoli jeho kopírovací konstruktor. Prvek se přidá na konec seznamu, takže teď se stalo koncovým. Tuto metodu lze použít s prázdným seznamem.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#15](../../atl/codesnippet/cpp/catllist-class_3.cpp)]

## <a name="catllistaddtaillist"></a><a name="addtaillist"></a>CAtlList::AddTailList

Voláním této metody přidáte existující seznam na konec tohoto seznamu.

```cpp
void AddTailList(const CAtlList<E, ETraits>* plNew);
```

### <a name="parameters"></a>Parametry

*plNew*<br/>
Seznam, který se má přidat

### <a name="remarks"></a>Poznámky

Seznam, na který odkazuje *plNew* , je vložen za poslední prvek (pokud existuje) v objektu list. Poslední prvek v seznamu *plNew* se proto stal koncovým prvkem. V sestavení ladění dojde k selhání kontrolního výrazu, pokud je *plNew* ROVNO hodnotě null.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#16](../../atl/codesnippet/cpp/catllist-class_4.cpp)]

## <a name="catllistassertvalid"></a><a name="assertvalid"></a>CAtlList::AssertValid

Voláním této metody potvrďte, že seznam je platný.

```cpp
void AssertValid() const;
```

### <a name="remarks"></a>Poznámky

V sestavení ladění dojde k selhání kontrolního výrazu, pokud objekt seznamu není platný. Aby bylo možné tento prázdný seznam zadat jako platný, musí mít hlavní a koncová ukazatel na hodnotu NULL a seznam, který není prázdný, musí mít hlavní a koncovou položku ukazující na platné adresy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#17](../../atl/codesnippet/cpp/catllist-class_5.cpp)]

## <a name="catllistcatllist"></a><a name="catllist"></a>CAtlList::CAtlList

Konstruktor

```cpp
CAtlList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parametry

*nBlockSize*<br/>
Velikost bloku

### <a name="remarks"></a>Poznámky

Konstruktor pro `CAtlList` objekt. Velikost bloku je míra množství paměti přidělené při požadování nového prvku. Větší velikosti bloků snižují volání rutin přidělování paměti, ale používají více prostředků.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#18](../../atl/codesnippet/cpp/catllist-class_6.cpp)]

## <a name="catllistcatllist"></a><a name="dtor"></a>CAtlList:: ~ CAtlList

Destruktor.

```cpp
~CAtlList() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky, včetně volání [CAtlList:: RemoveAll](#removeall) pro odebrání všech prvků ze seznamu.

V sestavení ladění dojde k selhání kontrolního výrazu, pokud seznam stále obsahuje některé prvky po volání `RemoveAll`.

## <a name="catllistfind"></a><a name="find"></a>CAtlList:: Find

Voláním této metody můžete hledat v seznamu zadaného elementu.

```cpp
POSITION Find(INARGTYPE element, POSITION posStartAfter = NULL) const throw();
```

### <a name="parameters"></a>Parametry

*objekt*<br/>
Element, který se má v seznamu najít.

*posStartAfter*<br/>
Počáteční pozice pro hledání. Pokud není zadána žádná hodnota, hledání začíná prvkem head.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu pozice elementu, pokud je nalezen, jinak vrátí hodnotu NULL.

### <a name="remarks"></a>Poznámky

V sestavení ladění dojde k selhání kontrolního výrazu, pokud objekt seznamu není platný nebo pokud hodnota *posStartAfter* je mimo rozsah.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#19](../../atl/codesnippet/cpp/catllist-class_7.cpp)]

## <a name="catllistfindindex"></a><a name="findindex"></a>CAtlList:: FindIndex –

Zavolejte tuto metodu pro získání pozice prvku s ohledem na hodnotu indexu.

```cpp
POSITION FindIndex(size_t iElement) const throw();
```

### <a name="parameters"></a>Parametry

*iElement*<br/>
Index požadovaného prvku seznamu založený na nule.

### <a name="return-value"></a>Návratová hodnota

Vrátí odpovídající hodnotu pozice nebo hodnotu NULL, pokud je *IElement* mimo rozsah.

### <a name="remarks"></a>Poznámky

Tato metoda vrací pozici odpovídající dané hodnotě indexu a umožňuje přístup k elementu *n*th v seznamu.

V sestavení ladění dojde k selhání kontrolního výrazu, pokud objekt seznamu není platný.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#20](../../atl/codesnippet/cpp/catllist-class_8.cpp)]

## <a name="catllistgetat"></a><a name="getat"></a>CAtlList::GetAt

Voláním této metody vrátí prvek na zadané pozici v seznamu.

```cpp
E& GetAt(POSITION pos) throw();
const E& GetAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parametry

*POS*<br/>
Hodnota pozice určující konkrétní prvek.

### <a name="return-value"></a>Návratová hodnota

Odkaz na nebo kopii elementu.

### <a name="remarks"></a>Poznámky

Pokud je seznam **const**, `GetAt` vrátí kopii elementu. To umožňuje, aby se metoda použila jenom na pravé straně příkazu přiřazení a aby se seznam předalo upravovat.

Pokud seznam není **const**, `GetAt` vrátí odkaz na prvek. To umožňuje, aby se metoda použila na obou stranách příkazu přiřazení, a tím umožňuje změnit položky seznamu.

V sestavení ladění dojde k selhání kontrolního výrazu, pokud je *POS* rovna hodnotě null.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlList:: FindIndex –](#findindex).

## <a name="catllistgetcount"></a><a name="getcount"></a>CAtlList:: GetCount

Voláním této metody vrátíte počet objektů v seznamu.

```cpp
size_t GetCount() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet prvků v seznamu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlList:: Find](#find).

## <a name="catllistgethead"></a><a name="gethead"></a>CAtlList:: GetHead

Voláním této metody vrátíte prvek v záhlaví seznamu.

```cpp
E& GetHead() throw();
const E& GetHead() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na nebo kopii prvku v záhlaví seznamu.

### <a name="remarks"></a>Poznámky

Pokud je seznam **const**, `GetHead` vrátí kopii elementu v záhlaví seznamu. To umožňuje, aby se metoda použila jenom na pravé straně příkazu přiřazení a aby se seznam předalo upravovat.

Pokud seznam není **const**, `GetHead` vrátí odkaz na prvek v záhlaví seznamu. To umožňuje, aby se metoda použila na obou stranách příkazu přiřazení, a tím umožňuje změnit položky seznamu.

V sestavení ladění dojde k selhání kontrolního výrazu, pokud je záhlaví seznamu ukazovat na hodnotu NULL.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlList:: AddHead](#addhead).

## <a name="catllistgetheadposition"></a><a name="getheadposition"></a>CAtlList::GetHeadPosition

Voláním této metody získáte pozici záhlaví seznamu.

```cpp
POSITION GetHeadPosition() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu pozice odpovídající elementu v záhlaví seznamu.

### <a name="remarks"></a>Poznámky

Pokud je seznam prázdný, vrácená hodnota je NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#21](../../atl/codesnippet/cpp/catllist-class_9.cpp)]

## <a name="catllistgetnext"></a><a name="getnext"></a>CAtlList:: GetNext

Voláním této metody vrátíte další prvek ze seznamu.

```cpp
E& GetNext(POSITION& pos) throw();
const E& GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parametry

*POS*<br/>
Hodnota pozice vrácená předchozím voláním `GetNext`, [CAtlList:: GetHeadPosition](#getheadposition)nebo jinou `CAtlList` metodou.

### <a name="return-value"></a>Návratová hodnota

Pokud je seznam **const**, `GetNext` vrátí kopii dalšího prvku seznamu. To umožňuje, aby se metoda použila jenom na pravé straně příkazu přiřazení a aby se seznam předalo upravovat.

Pokud seznam není **const**, `GetNext` vrátí odkaz na další prvek seznamu. To umožňuje, aby se metoda použila na obou stranách příkazu přiřazení, a tím umožňuje změnit položky seznamu.

### <a name="remarks"></a>Poznámky

Čítač pozice, *POS*, je aktualizován tak, aby odkazoval na další prvek v seznamu, nebo hodnotu null, pokud nejsou k dispozici žádné další prvky. V sestavení ladění dojde k selhání kontrolního výrazu, pokud je *POS* rovna hodnotě null.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlList:: GetHeadPosition](#getheadposition).

## <a name="catllistgetprev"></a><a name="getprev"></a>CAtlList:: getpředchozí

Voláním této metody vrátíte předchozí prvek ze seznamu.

```cpp
E& GetPrev(POSITION& pos) throw();
const E& GetPrev(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parametry

*POS*<br/>
Hodnota pozice vrácená předchozím voláním `GetPrev`, [CAtlList:: GetTailPosition](#gettailposition)nebo jinou `CAtlList` metodou.

### <a name="return-value"></a>Návratová hodnota

Pokud je seznam **const**, `GetPrev` vrátí kopii prvku seznamu. To umožňuje, aby se metoda použila jenom na pravé straně příkazu přiřazení a aby se seznam předalo upravovat.

Pokud seznam není **const**, `GetPrev` vrátí odkaz na prvek seznamu. To umožňuje, aby se metoda použila na obou stranách příkazu přiřazení, a tím umožňuje změnit položky seznamu.

### <a name="remarks"></a>Poznámky

Čítač pozice, *POS*, je aktualizován tak, aby odkazoval na předchozí prvek v seznamu, nebo hodnotu null, pokud nejsou k dispozici žádné další prvky. V sestavení ladění dojde k selhání kontrolního výrazu, pokud je *POS* rovna hodnotě null.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlList:: GetTailPosition](#gettailposition).

## <a name="catllistgettail"></a><a name="gettail"></a>CAtlList:: GetTail

Zavolejte tuto metodu, chcete-li vrátit prvek na konec seznamu.

```cpp
E& GetTail() throw();
const E& GetTail() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na nebo kopii prvku na konci seznamu.

### <a name="remarks"></a>Poznámky

Pokud je seznam **const**, `GetTail` vrátí kopii elementu v záhlaví seznamu. To umožňuje, aby se metoda použila jenom na pravé straně příkazu přiřazení a aby se seznam předalo upravovat.

Pokud seznam není **const**, `GetTail` vrátí odkaz na prvek v záhlaví seznamu. To umožňuje, aby se metoda použila na obou stranách příkazu přiřazení, a tím umožňuje změnit položky seznamu.

V sestavení ladění dojde k selhání kontrolního výrazu, pokud konec seznamu odkazuje na hodnotu NULL.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlList:: AddTail –](#addtail).

## <a name="catllistgettailposition"></a><a name="gettailposition"></a>CAtlList::GetTailPosition

Voláním této metody získá pozice konce seznamu.

```cpp
POSITION GetTailPosition() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu pozice odpovídající prvku na konci seznamu.

### <a name="remarks"></a>Poznámky

Pokud je seznam prázdný, vrácená hodnota je NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#22](../../atl/codesnippet/cpp/catllist-class_10.cpp)]

## <a name="catllistinargtype"></a><a name="inargtype"></a>CAtlList::INARGTYPE

Typ použitý při předání prvku jako vstupní argument.

```cpp
typedef ETraits::INARGTYPE INARGTYPE;
```

## <a name="catllistinsertafter"></a><a name="insertafter"></a>CAtlList::InsertAfter

Zavolejte tuto metodu pro vložení nového elementu do seznamu po zadané pozici.

```cpp
POSITION InsertAfter(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*POS*<br/>
Hodnota pozice, po jejímž uplynutí bude nový prvek vložen.

*objekt*<br/>
Prvek, který má být vložen.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu pozice nového prvku.

### <a name="remarks"></a>Poznámky

V sestavení ladění dojde k selhání kontrolního výrazu, pokud seznam není platný, pokud vložení selže nebo pokud je proveden pokus o vložení prvku za konec.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#23](../../atl/codesnippet/cpp/catllist-class_11.cpp)]

## <a name="catllistinsertbefore"></a><a name="insertbefore"></a>CAtlList::InsertBefore

Zavolejte tuto metodu pro vložení nového prvku do seznamu před určenou pozicí.

```cpp
POSITION InsertBefore(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*POS*<br/>
Nový prvek bude vložen do seznamu před touto hodnotou pozice.

*objekt*<br/>
Prvek, který má být vložen.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu pozice nového prvku.

### <a name="remarks"></a>Poznámky

V sestavení ladění dojde k selhání kontrolního výrazu, pokud seznam není platný, pokud vložení selže, nebo pokud je proveden pokus o vložení elementu před záhlavím.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#24](../../atl/codesnippet/cpp/catllist-class_12.cpp)]

## <a name="catllistisempty"></a><a name="isempty"></a>CAtlList::-Empty

Voláním této metody určíte, zda je seznam prázdný.

```cpp
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud seznam neobsahuje žádné objekty, v opačném případě false.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#25](../../atl/codesnippet/cpp/catllist-class_13.cpp)]

## <a name="catllistmovetohead"></a><a name="movetohead"></a>CAtlList::MoveToHead

Voláním této metody přesunete zadaný element na záhlaví seznamu.

```cpp
void MoveToHead(POSITION pos) throw();
```

### <a name="parameters"></a>Parametry

*POS*<br/>
Hodnota pozice prvku, který se má přesunout

### <a name="remarks"></a>Poznámky

Zadaný element je přesunut z jeho aktuální pozice do záhlaví seznamu. V sestavení ladění dojde k selhání kontrolního výrazu, pokud je *POS* rovna hodnotě null.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#26](../../atl/codesnippet/cpp/catllist-class_14.cpp)]

## <a name="catllistmovetotail"></a><a name="movetotail"></a>CAtlList::MoveToTail

Zavolejte tuto metodu pro přesun zadaného elementu na konec seznamu.

```cpp
void MoveToTail(POSITION pos) throw();
```

### <a name="parameters"></a>Parametry

*POS*<br/>
Hodnota pozice prvku, který se má přesunout

### <a name="remarks"></a>Poznámky

Zadaný prvek je přesunut z jeho aktuální pozice na konec seznamu. V sestavení ladění dojde k selhání kontrolního výrazu, pokud je *POS* rovna hodnotě null.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlList:: MoveToHead](#movetohead).

## <a name="catllistremoveall"></a><a name="removeall"></a>CAtlList::RemoveAll

Voláním této metody odeberete všechny prvky ze seznamu.

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>Poznámky

Tato metoda odebere všechny prvky ze seznamu a uvolní přidělenou paměť. V sestavách ladění se vyvolá ATLASSERT, pokud se všechny prvky neodstraní nebo pokud je struktura seznamu poškozená.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlList::-Empty](#isempty).

## <a name="catllistremoveat"></a><a name="removeat"></a>CAtlList:: funkce RemoveAt

Zavolejte tuto metodu pro odebrání jednoho prvku ze seznamu.

```cpp
void RemoveAt(POSITION pos) throw();
```

### <a name="parameters"></a>Parametry

*POS*<br/>
Hodnota pozice prvku, který má být odebrán.

### <a name="remarks"></a>Poznámky

Element, na který odkazuje *POS* , se odebere a uvolní se paměť. Je přijatelné použít `RemoveAt` k odebrání záhlaví nebo konce seznamu.

V sestavení ladění dojde k selhání kontrolního výrazu, pokud seznam není platný nebo pokud odebrání elementu způsobí, že seznam přistupuje k paměti, která není součástí struktury seznamu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#27](../../atl/codesnippet/cpp/catllist-class_15.cpp)]

## <a name="catllistremovehead"></a><a name="removehead"></a>CAtlList::RemoveHead

Zavolejte tuto metodu pro odebrání elementu v záhlaví seznamu.

```cpp
E RemoveHead();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí prvek v záhlaví seznamu.

### <a name="remarks"></a>Poznámky

Hlavní element je odstraněn ze seznamu a je uvolněna paměť. Vrátí se kopie elementu. V sestavení ladění dojde k selhání kontrolního výrazu, pokud je seznam prázdný.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#28](../../atl/codesnippet/cpp/catllist-class_16.cpp)]

## <a name="catllistremoveheadnoreturn"></a><a name="removeheadnoreturn"></a>CAtlList::RemoveHeadNoReturn

Zavolejte tuto metodu pro odebrání elementu na začátku seznamu bez vrácení hodnoty.

```cpp
void RemoveHeadNoReturn() throw();
```

### <a name="remarks"></a>Poznámky

Hlavní element je odstraněn ze seznamu a je uvolněna paměť. V sestavení ladění dojde k selhání kontrolního výrazu, pokud je seznam prázdný.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlList::-Empty](#isempty).

## <a name="catllistremovetail"></a><a name="removetail"></a>CAtlList::RemoveTail

Zavolejte tuto metodu pro odebrání elementu na konci seznamu.

```cpp
E RemoveTail();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí prvek na konec seznamu.

### <a name="remarks"></a>Poznámky

Element Tail je odstraněn ze seznamu a je uvolněna paměť. Vrátí se kopie elementu. V sestavení ladění dojde k selhání kontrolního výrazu, pokud je seznam prázdný.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#29](../../atl/codesnippet/cpp/catllist-class_17.cpp)]

## <a name="catllistremovetailnoreturn"></a><a name="removetailnoreturn"></a>CAtlList::RemoveTailNoReturn

Zavolejte tuto metodu pro odebrání elementu na konci seznamu bez vrácení hodnoty.

```cpp
void RemoveTailNoReturn() throw();
```

### <a name="remarks"></a>Poznámky

Element Tail je odstraněn ze seznamu a je uvolněna paměť. V sestavení ladění dojde k selhání kontrolního výrazu, pokud je seznam prázdný.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlList::-Empty](#isempty).

## <a name="catllistsetat"></a><a name="setat"></a>CAtlList::SetAt

Voláním této metody nastavíte hodnotu prvku na dané pozici v seznamu.

```cpp
void SetAt(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*POS*<br/>
Hodnota pozice odpovídající prvku, který má být změněn.

*objekt*<br/>
Nová hodnota elementu.

### <a name="remarks"></a>Poznámky

Nahradí existující hodnotu *elementem*. V sestavení ladění dojde k selhání kontrolního výrazu, pokud je *POS* rovna hodnotě null.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#30](../../atl/codesnippet/cpp/catllist-class_18.cpp)]

## <a name="catllistswapelements"></a><a name="swapelements"></a>CAtlList::SwapElements

Zavolejte tuto metodu pro prohození prvků v seznamu.

```cpp
void SwapElements(POSITION pos1, POSITION pos2) throw();
```

### <a name="parameters"></a>Parametry

*pos1*<br/>
Hodnota první pozice

*pos2*<br/>
Hodnota druhé pozice.

### <a name="remarks"></a>Poznámky

Zamění elementy na dvou zadaných pozicích. V sestavení ladění dojde k selhání kontrolního výrazu, pokud je buď hodnota pozice rovna hodnotě NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#31](../../atl/codesnippet/cpp/catllist-class_19.cpp)]

## <a name="see-also"></a>Viz také

[CList – třída](../../mfc/reference/clist-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
