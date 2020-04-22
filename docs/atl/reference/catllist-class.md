---
title: Třída CAtlList
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
ms.openlocfilehash: 0e4ea8eef51431c100f5d3119d7f75e9673e276e
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748735"
---
# <a name="catllist-class"></a>Třída CAtlList

Tato třída poskytuje metody pro vytváření a správu objektu seznamu.

## <a name="syntax"></a>Syntaxe

```
template<typename E, class ETraits = CElementTraits<E>>
class CAtlList
```

#### <a name="parameters"></a>Parametry

*E*<br/>
Typ prvku.

*ETraits*<br/>
Kód používaný ke kopírování nebo přesouvání prvků. Další podrobnosti najdete v [části CElementTraits Class.](../../atl/reference/celementtraits-class.md)

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

|Název|Popis|
|----------|-----------------|
|[CAtlList::INARGTYPE](#inargtype)||

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAtlList::CAtlList](#catllist)|Konstruktor|
|[CAtlList::~CAtlList](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAtlList::Přidat hlavu](#addhead)|Volání této metody přidat prvek do hlavy seznamu.|
|[CAtlList::AddHeadList](#addheadlist)|Volání této metody přidat existující seznam do hlavního seznamu.|
|[CAtlList::AddTail](#addtail)|Volání této metody přidat prvek do ocasu tohoto seznamu.|
|[CAtlList::AddTailList](#addtaillist)|Volání této metody přidat existující seznam na konci tohoto seznamu.|
|[CAtlList::AssertValid](#assertvalid)|Volání této metody pro potvrzení, že seznam je platný.|
|[CAtlList::Najít](#find)|Volání této metody hledat v seznamu pro zadaný prvek.|
|[CAtlList::FindIndex](#findindex)|Volání této metody získat pozici prvku, dané hodnoty indexu.|
|[CAtlList::GetAt](#getat)|Volání této metody vrátit prvek na zadané pozici v seznamu.|
|[CAtlList::GetCount](#getcount)|Volání této metody vrátit počet objektů v seznamu.|
|[CAtlList::GetHead](#gethead)|Volání této metody vrátit prvek v čele seznamu.|
|[CAtlList::GetHeadPosition](#getheadposition)|Volání této metody získat pozici vedoucího seznamu.|
|[CAtlList::GetNext](#getnext)|Volání této metody vrátit další prvek ze seznamu.|
|[CAtlList::GetPrev](#getprev)|Volání této metody vrátit předchozí prvek ze seznamu.|
|[CAtlList::GetTail](#gettail)|Volání této metody vrátit prvek na konci seznamu.|
|[CAtlList::GetTailPosition](#gettailposition)|Volání této metody získat pozici ocasu seznamu.|
|[CAtlList::InsertAfter](#insertafter)|Volání této metody vložit nový prvek do seznamu za zadanou pozici.|
|[CAtlList::InsertBefore](#insertbefore)|Volání této metody vložit nový prvek do seznamu před zadané pozice.|
|[CAtlList::IsEmpty](#isempty)|Volání této metody k určení, zda je seznam prázdný.|
|[CAtlList::MoveToHead](#movetohead)|Volání této metody přesunout zadaný prvek do čela seznamu.|
|[CAtlList::MoveToTail](#movetotail)|Volání této metody přesunout zadaný prvek na konec seznamu.|
|[CAtlList::OdebratVše](#removeall)|Volání této metody odebrat všechny prvky ze seznamu.|
|[CAtlList::RemoveAt](#removeat)|Volání této metody odebrat jeden prvek ze seznamu.|
|[CAtlList::RemoveHead](#removehead)|Volání této metody odebrat prvek v čele seznamu.|
|[CAtlList::RemoveHeadNoReturn](#removeheadnoreturn)|Volání této metody odebrat prvek v čele seznamu bez vrácení hodnoty.|
|[CAtlList::RemoveTail](#removetail)|Volání této metody odebrat prvek na konci seznamu.|
|[CAtlList::RemoveTailNoReturn](#removetailnoreturn)|Volání této metody odebrat prvek na konci seznamu bez vrácení hodnoty.|
|[CAtlList::SetAt](#setat)|Volání této metody nastavit hodnotu prvku na dané pozici v seznamu.|
|[CAtlList::SwapElements](#swapelements)|Volání této metody pro zamění prvky v seznamu.|

## <a name="remarks"></a>Poznámky

Třída `CAtlList` podporuje seřazené seznamy nejedinečných objektů přístupných postupně nebo podle hodnoty. `CAtlList`seznamy se chovají jako dvojnásob propojené seznamy. Každý seznam má hlavu a ocas a nové prvky (nebo seznamy v některých případech) mohou být přidány na jeden konec seznamu nebo vloženy před nebo za určité prvky.

Většina `CAtlList` metod využívá hodnotu pozice. Tato hodnota se používá metody odkazovat na umístění skutečné paměti, kde jsou uloženy prvky a by neměly být vypočteny nebo předpovědět přímo. Pokud je nutné získat přístup k *n*th element v seznamu, metoda [CAtlList::FindIndex](#findindex) vrátí odpovídající hodnotu pozice pro daný index. Metody [CAtlList::GetNext](#getnext) a [CAtlList::GetPrev](#getprev) lze iterate prostřednictvím objektů v seznamu.

Další informace týkající se tříd kolekce, které jsou k dispozici s atl, naleznete [v tématu TŘÍDY kolekce atl](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

## <a name="catllistaddhead"></a><a name="addhead"></a>CAtlList::Přidat hlavu

Volání této metody přidat prvek do hlavy seznamu.

```
POSITION AddHead();
POSITION AddHead(INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*Prvek*<br/>
Nový prvek.

### <a name="return-value"></a>Návratová hodnota

Vrátí pozici nově přidaného prvku.

### <a name="remarks"></a>Poznámky

Pokud je použita první verze, prázdný prvek je vytvořen pomocí jeho výchozí konstruktor, spíše než jeho kopie konstruktoru.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#13](../../atl/codesnippet/cpp/catllist-class_1.cpp)]

## <a name="catllistaddheadlist"></a><a name="addheadlist"></a>CAtlList::AddHeadList

Volání této metody přidat existující seznam do hlavního seznamu.

```cpp
void AddHeadList(const CAtlList<E, ETraits>* plNew);
```

### <a name="parameters"></a>Parametry

*plNovinka*<br/>
Seznam, který má být přidán.

### <a name="remarks"></a>Poznámky

Seznam, na který odkazem *plNew* ukazuje, je vložen na začátek existujícího seznamu. V sestaveních ladění dojde k selhání kontrolního výrazu, pokud *plNew* se rovná hodnotě NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#14](../../atl/codesnippet/cpp/catllist-class_2.cpp)]

## <a name="catllistaddtail"></a><a name="addtail"></a>CAtlList::AddTail

Volání této metody přidat prvek do ocasu tohoto seznamu.

```
POSITION AddTail();
POSITION AddTail(INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*Prvek*<br/>
Prvek přidat.

### <a name="return-value"></a>Návratová hodnota

Vrátí pozici nově přidaného prvku.

### <a name="remarks"></a>Poznámky

Pokud je použita první verze, prázdný prvek je vytvořen pomocí jeho výchozí konstruktor, spíše než jeho kopie konstruktoru. Prvek je přidán na konec seznamu, a tak se nyní stane ocasem. Tuto metodu lze použít s prázdným seznamem.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#15](../../atl/codesnippet/cpp/catllist-class_3.cpp)]

## <a name="catllistaddtaillist"></a><a name="addtaillist"></a>CAtlList::AddTailList

Volání této metody přidat existující seznam na konci tohoto seznamu.

```cpp
void AddTailList(const CAtlList<E, ETraits>* plNew);
```

### <a name="parameters"></a>Parametry

*plNovinka*<br/>
Seznam, který má být přidán.

### <a name="remarks"></a>Poznámky

Seznam odkazovaný *na plNew* je vložen za poslední prvek (pokud existuje) v objektu seznamu. Poslední prvek v *seznamu plNew* se proto stává ocasem. V sestaveních ladění dojde k selhání kontrolního výrazu, pokud *plNew* se rovná hodnotě NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#16](../../atl/codesnippet/cpp/catllist-class_4.cpp)]

## <a name="catllistassertvalid"></a><a name="assertvalid"></a>CAtlList::AssertValid

Volání této metody pro potvrzení, že seznam je platný.

```cpp
void AssertValid() const;
```

### <a name="remarks"></a>Poznámky

V sestaveních ladění dojde k selhání kontrolního výrazu, pokud objekt seznamu není platný. Aby byl prázdný seznam platný, musí mít hlavu i zadní strana směřující na hodnotu NULL a seznam, který není prázdný, musí mít hlavu i zadní strana směřující na platné adresy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#17](../../atl/codesnippet/cpp/catllist-class_5.cpp)]

## <a name="catllistcatllist"></a><a name="catllist"></a>CAtlList::CAtlList

Konstruktor

```
CAtlList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parametry

*nBlockSize*<br/>
Velikost bloku.

### <a name="remarks"></a>Poznámky

Konstruktor pro `CAtlList` objekt. Velikost bloku je míra množství paměti přidělené při je požadováno nový prvek. Větší velikosti bloků snižují volání rutiny přidělení paměti, ale používají více prostředků.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#18](../../atl/codesnippet/cpp/catllist-class_6.cpp)]

## <a name="catllistcatllist"></a><a name="dtor"></a>CAtlList::~CAtlList

Destruktor.

```
~CAtlList() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky, včetně volání [CAtlList::RemoveAll](#removeall) odebrat všechny prvky ze seznamu.

V sestaveních ladění dojde k selhání kontrolního výrazu, pokud `RemoveAll`seznam stále obsahuje některé prvky po volání .

## <a name="catllistfind"></a><a name="find"></a>CAtlList::Najít

Volání této metody hledat v seznamu pro zadaný prvek.

```
POSITION Find(INARGTYPE element, POSITION posStartAfter = NULL) const throw();
```

### <a name="parameters"></a>Parametry

*Prvek*<br/>
Prvek, který se nachází v seznamu.

*posStartAfter*<br/>
Počáteční pozice pro hledání. Pokud není zadána žádná hodnota, hledání začíná prvkem head.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu POSITION prvku, pokud byl nalezen, jinak vrátí hodnotu NULL.

### <a name="remarks"></a>Poznámky

V sestaveních ladění dojde k selhání kontrolního výrazu, pokud objekt seznamu není platný nebo pokud je hodnota *posStartAfter* mimo rozsah.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#19](../../atl/codesnippet/cpp/catllist-class_7.cpp)]

## <a name="catllistfindindex"></a><a name="findindex"></a>CAtlList::FindIndex

Volání této metody získat pozici prvku, dané hodnoty indexu.

```
POSITION FindIndex(size_t iElement) const throw();
```

### <a name="parameters"></a>Parametry

*iElement*<br/>
Index na základě nuly prvku seznamu požadovaný.

### <a name="return-value"></a>Návratová hodnota

Vrátí odpovídající hodnotu POSITION nebo HODNOTU NULL, pokud je *prvek iElement* mimo rozsah.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí POZICI odpovídající dané hodnotě indexu, což umožňuje přístup k *n*th element v seznamu.

V sestaveních ladění dojde k selhání kontrolního výrazu, pokud objekt seznamu není platný.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#20](../../atl/codesnippet/cpp/catllist-class_8.cpp)]

## <a name="catllistgetat"></a><a name="getat"></a>CAtlList::GetAt

Volání této metody vrátit prvek na zadané pozici v seznamu.

```
E& GetAt(POSITION pos) throw();
const E& GetAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parametry

*Pos*<br/>
Hodnota POSITION určující určitý prvek.

### <a name="return-value"></a>Návratová hodnota

Odkaz na prvek nebo jeho kopii.

### <a name="remarks"></a>Poznámky

Pokud je seznam **const**, `GetAt` vrátí kopii prvku. To umožňuje metodu, která má být použita pouze na pravé straně příkazu přiřazení a chrání seznam před úpravou.

Pokud seznam není **const**, `GetAt` vrátí odkaz na prvek. To umožňuje metodu, která má být použita na obou stranách příkazu přiřazení a tím umožňuje položky seznamu, které mají být změněny.

V sestaveních ladění dojde k selhání kontrolního výrazu, pokud *se pos* rovná hodnotě NULL.

### <a name="example"></a>Příklad

Viz příklad pro [CAtlList::FindIndex](#findindex).

## <a name="catllistgetcount"></a><a name="getcount"></a>CAtlList::GetCount

Volání této metody vrátit počet objektů v seznamu.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet prvků v seznamu.

### <a name="example"></a>Příklad

Viz příklad pro [CAtlList::Find](#find).

## <a name="catllistgethead"></a><a name="gethead"></a>CAtlList::GetHead

Volání této metody vrátit prvek v čele seznamu.

```
E& GetHead() throw();
const E& GetHead() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na prvek v čele seznamu nebo jeho kopii.

### <a name="remarks"></a>Poznámky

Pokud je seznam **const**, `GetHead` vrátí kopii prvku v čele seznamu. To umožňuje metodu, která má být použita pouze na pravé straně příkazu přiřazení a chrání seznam před úpravou.

Pokud seznam není **const**, `GetHead` vrátí odkaz na prvek v čele seznamu. To umožňuje metodu, která má být použita na obou stranách příkazu přiřazení a tím umožňuje položky seznamu, které mají být změněny.

V sestaveních ladění dojde k selhání kontrolního výrazu, pokud vedoucí seznamu odkazuje na hodnotu NULL.

### <a name="example"></a>Příklad

Viz příklad pro [CAtlList::AddHead](#addhead).

## <a name="catllistgetheadposition"></a><a name="getheadposition"></a>CAtlList::GetHeadPosition

Volání této metody získat pozici vedoucího seznamu.

```
POSITION GetHeadPosition() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu POZICE odpovídající prvku v čele seznamu.

### <a name="remarks"></a>Poznámky

Pokud je seznam prázdný, vrácená hodnota je NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#21](../../atl/codesnippet/cpp/catllist-class_9.cpp)]

## <a name="catllistgetnext"></a><a name="getnext"></a>CAtlList::GetNext

Volání této metody vrátit další prvek ze seznamu.

```
E& GetNext(POSITION& pos) throw();
const E& GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parametry

*Pos*<br/>
Hodnota POSITION vrácená předchozím voláním `GetNext`, [CAtlList::GetHeadPosition](#getheadposition)nebo jinou `CAtlList` metodou.

### <a name="return-value"></a>Návratová hodnota

Pokud je seznam **const**, `GetNext` vrátí kopii dalšího prvku seznamu. To umožňuje metodu, která má být použita pouze na pravé straně příkazu přiřazení a chrání seznam před úpravou.

Pokud seznam není **const**, `GetNext` vrátí odkaz na další prvek seznamu. To umožňuje metodu, která má být použita na obou stranách příkazu přiřazení a tím umožňuje položky seznamu, které mají být změněny.

### <a name="remarks"></a>Poznámky

Čítač *POZICE, pos*, je aktualizován tak, aby ukazoval na další prvek v seznamu nebo NULL, pokud neexistují žádné další prvky. V sestaveních ladění dojde k selhání kontrolního výrazu, pokud *se pos* rovná hodnotě NULL.

### <a name="example"></a>Příklad

Viz příklad pro [CAtlList::GetHeadPosition](#getheadposition).

## <a name="catllistgetprev"></a><a name="getprev"></a>CAtlList::GetPrev

Volání této metody vrátit předchozí prvek ze seznamu.

```
E& GetPrev(POSITION& pos) throw();
const E& GetPrev(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parametry

*Pos*<br/>
Hodnota POSITION vrácená předchozím voláním `GetPrev`, [CAtlList::GetTailPosition](#gettailposition)nebo jinou `CAtlList` metodou.

### <a name="return-value"></a>Návratová hodnota

Pokud je seznam **const**, `GetPrev` vrátí kopii prvku seznamu. To umožňuje metodu, která má být použita pouze na pravé straně příkazu přiřazení a chrání seznam před úpravou.

Pokud seznam není **const**, `GetPrev` vrátí odkaz na prvek seznamu. To umožňuje metodu, která má být použita na obou stranách příkazu přiřazení a tím umožňuje položky seznamu, které mají být změněny.

### <a name="remarks"></a>Poznámky

Čítač *POZICE, pos*, je aktualizován tak, aby ukazoval na předchozí prvek v seznamu nebo NULL, pokud neexistují žádné další prvky. V sestaveních ladění dojde k selhání kontrolního výrazu, pokud *se pos* rovná hodnotě NULL.

### <a name="example"></a>Příklad

Viz příklad pro [CAtlList::GetTailPosition](#gettailposition).

## <a name="catllistgettail"></a><a name="gettail"></a>CAtlList::GetTail

Volání této metody vrátit prvek na konci seznamu.

```
E& GetTail() throw();
const E& GetTail() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na prvek nebo jeho kopii na konci seznamu.

### <a name="remarks"></a>Poznámky

Pokud je seznam **const**, `GetTail` vrátí kopii prvku v čele seznamu. To umožňuje metodu, která má být použita pouze na pravé straně příkazu přiřazení a chrání seznam před úpravou.

Pokud seznam není **const**, `GetTail` vrátí odkaz na prvek v čele seznamu. To umožňuje metodu, která má být použita na obou stranách příkazu přiřazení a tím umožňuje položky seznamu, které mají být změněny.

V sestaveních ladění dojde k selhání kontrolního výrazu, pokud ocas seznamu odkazuje na hodnotu NULL.

### <a name="example"></a>Příklad

Viz příklad pro [CAtlList::AddTail](#addtail).

## <a name="catllistgettailposition"></a><a name="gettailposition"></a>CAtlList::GetTailPosition

Volání této metody získat pozici ocasu seznamu.

```
POSITION GetTailPosition() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu POZICE odpovídající prvku na konci seznamu.

### <a name="remarks"></a>Poznámky

Pokud je seznam prázdný, vrácená hodnota je NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#22](../../atl/codesnippet/cpp/catllist-class_10.cpp)]

## <a name="catllistinargtype"></a><a name="inargtype"></a>CAtlList::INARGTYPE

Typ používaný při předání prvku jako vstupní argument.

```
typedef ETraits::INARGTYPE INARGTYPE;
```

## <a name="catllistinsertafter"></a><a name="insertafter"></a>CAtlList::InsertAfter

Volání této metody vložit nový prvek do seznamu za zadanou pozici.

```
POSITION InsertAfter(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*Pos*<br/>
Hodnota POSITION, po kterou bude vložen nový prvek.

*Prvek*<br/>
Prvek, který má být vložen.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu POSITION nového prvku.

### <a name="remarks"></a>Poznámky

V sestaveních ladění dojde k selhání kontrolního výrazu, pokud seznam není platný, pokud se příkaz insert nezdaří nebo pokud je proveden pokus o vložení prvku za ocas.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#23](../../atl/codesnippet/cpp/catllist-class_11.cpp)]

## <a name="catllistinsertbefore"></a><a name="insertbefore"></a>CAtlList::InsertBefore

Volání této metody vložit nový prvek do seznamu před zadané pozice.

```
POSITION InsertBefore(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*Pos*<br/>
Nový prvek bude vložen do seznamu před tuto hodnotu POSITION.

*Prvek*<br/>
Prvek, který má být vložen.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu POSITION nového prvku.

### <a name="remarks"></a>Poznámky

V sestaveních ladění dojde k selhání kontrolního výrazu, pokud seznam není platný, pokud se příkaz insert nezdaří nebo pokud je proveden pokus o vložení prvku před hlavu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#24](../../atl/codesnippet/cpp/catllist-class_12.cpp)]

## <a name="catllistisempty"></a><a name="isempty"></a>CAtlList::IsEmpty

Volání této metody k určení, zda je seznam prázdný.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud seznam neobsahuje žádné objekty, jinak false.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#25](../../atl/codesnippet/cpp/catllist-class_13.cpp)]

## <a name="catllistmovetohead"></a><a name="movetohead"></a>CAtlList::MoveToHead

Volání této metody přesunout zadaný prvek do čela seznamu.

```cpp
void MoveToHead(POSITION pos) throw();
```

### <a name="parameters"></a>Parametry

*Pos*<br/>
Hodnota POSITION prvku přesunout.

### <a name="remarks"></a>Poznámky

Zadaný prvek je přesunut z aktuální pozice do hlavy seznamu. V sestaveních ladění dojde k selhání kontrolního výrazu, pokud *se pos* rovná hodnotě NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#26](../../atl/codesnippet/cpp/catllist-class_14.cpp)]

## <a name="catllistmovetotail"></a><a name="movetotail"></a>CAtlList::MoveToTail

Volání této metody přesunout zadaný prvek na konec seznamu.

```cpp
void MoveToTail(POSITION pos) throw();
```

### <a name="parameters"></a>Parametry

*Pos*<br/>
Hodnota POSITION prvku přesunout.

### <a name="remarks"></a>Poznámky

Zadaný prvek je přesunut z aktuální polohy na konec seznamu. V sestaveních ladění dojde k selhání kontrolního výrazu, pokud *se pos* rovná hodnotě NULL.

### <a name="example"></a>Příklad

Viz příklad pro [CAtlList::MoveToHead](#movetohead).

## <a name="catllistremoveall"></a><a name="removeall"></a>CAtlList::OdebratVše

Volání této metody odebrat všechny prvky ze seznamu.

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>Poznámky

Tato metoda odebere všechny prvky ze seznamu a uvolní přidělené paměti. V sestaveních debugs bude vyvolána ATLASSERT, pokud nejsou odstraněny všechny prvky nebo pokud došlo k poškození struktury seznamu.

### <a name="example"></a>Příklad

Viz příklad pro [CAtlList::IsEmpty](#isempty).

## <a name="catllistremoveat"></a><a name="removeat"></a>CAtlList::RemoveAt

Volání této metody odebrat jeden prvek ze seznamu.

```cpp
void RemoveAt(POSITION pos) throw();
```

### <a name="parameters"></a>Parametry

*Pos*<br/>
Hodnota POSITION prvku odebrat.

### <a name="remarks"></a>Poznámky

Prvek odkazovaný *pos* je odebrán a paměť je uvolněna. Je přijatelné použít `RemoveAt` k odstranění hlavy nebo ocasu seznamu.

V sestaveních ladění dojde k selhání kontrolního výrazu, pokud seznam není platný nebo pokud odebrání prvku způsobí, že seznam má přístup k paměti, která není součástí struktury seznamu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#27](../../atl/codesnippet/cpp/catllist-class_15.cpp)]

## <a name="catllistremovehead"></a><a name="removehead"></a>CAtlList::RemoveHead

Volání této metody odebrat prvek v čele seznamu.

```
E RemoveHead();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí prvek v čele seznamu.

### <a name="remarks"></a>Poznámky

Prvek head je odstraněn ze seznamu a paměť je uvolněna. Je vrácena kopie prvku. V sestaveních ladění dojde k selhání kontrolního výrazu, pokud je seznam prázdný.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#28](../../atl/codesnippet/cpp/catllist-class_16.cpp)]

## <a name="catllistremoveheadnoreturn"></a><a name="removeheadnoreturn"></a>CAtlList::RemoveHeadNoReturn

Volání této metody odebrat prvek v čele seznamu bez vrácení hodnoty.

```cpp
void RemoveHeadNoReturn() throw();
```

### <a name="remarks"></a>Poznámky

Prvek head je odstraněn ze seznamu a paměť je uvolněna. V sestaveních ladění dojde k selhání kontrolního výrazu, pokud je seznam prázdný.

### <a name="example"></a>Příklad

Viz příklad pro [CAtlList::IsEmpty](#isempty).

## <a name="catllistremovetail"></a><a name="removetail"></a>CAtlList::RemoveTail

Volání této metody odebrat prvek na konci seznamu.

```
E RemoveTail();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí prvek na konci seznamu.

### <a name="remarks"></a>Poznámky

Prvek ocasu je odstraněn ze seznamu a paměť je uvolněna. Je vrácena kopie prvku. V sestaveních ladění dojde k selhání kontrolního výrazu, pokud je seznam prázdný.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#29](../../atl/codesnippet/cpp/catllist-class_17.cpp)]

## <a name="catllistremovetailnoreturn"></a><a name="removetailnoreturn"></a>CAtlList::RemoveTailNoReturn

Volání této metody odebrat prvek na konci seznamu bez vrácení hodnoty.

```cpp
void RemoveTailNoReturn() throw();
```

### <a name="remarks"></a>Poznámky

Prvek ocasu je odstraněn ze seznamu a paměť je uvolněna. V sestaveních ladění dojde k selhání kontrolního výrazu, pokud je seznam prázdný.

### <a name="example"></a>Příklad

Viz příklad pro [CAtlList::IsEmpty](#isempty).

## <a name="catllistsetat"></a><a name="setat"></a>CAtlList::SetAt

Volání této metody nastavit hodnotu prvku na dané pozici v seznamu.

```cpp
void SetAt(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*Pos*<br/>
Hodnota POSITION odpovídající prvku změnit.

*Prvek*<br/>
Hodnota nového prvku.

### <a name="remarks"></a>Poznámky

Nahradí existující hodnotu *elementem*. V sestaveních ladění dojde k selhání kontrolního výrazu, pokud *se pos* rovná hodnotě NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#30](../../atl/codesnippet/cpp/catllist-class_18.cpp)]

## <a name="catllistswapelements"></a><a name="swapelements"></a>CAtlList::SwapElements

Volání této metody pro zamění prvky v seznamu.

```cpp
void SwapElements(POSITION pos1, POSITION pos2) throw();
```

### <a name="parameters"></a>Parametry

*pos1*<br/>
První hodnota POSITION.

*pos2*<br/>
Druhá hodnota POSITION.

### <a name="remarks"></a>Poznámky

Zamění prvky na obou zadaných pozicích. V sestaveních ladění dojde k selhání kontrolního výrazu, pokud je hodnota pozice rovna hodnotě NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#31](../../atl/codesnippet/cpp/catllist-class_19.cpp)]

## <a name="see-also"></a>Viz také

[CList – třída](../../mfc/reference/clist-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
