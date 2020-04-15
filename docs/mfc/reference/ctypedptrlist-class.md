---
title: Třída CTypedPtrList
ms.date: 11/04/2016
f1_keywords:
- CTypedPtrList
- AFXTEMPL/CTypedPtrList
- AFXTEMPL/CTypedPtrList::AddHead
- AFXTEMPL/CTypedPtrList::AddTail
- AFXTEMPL/CTypedPtrList::GetAt
- AFXTEMPL/CTypedPtrList::GetHead
- AFXTEMPL/CTypedPtrList::GetNext
- AFXTEMPL/CTypedPtrList::GetPrev
- AFXTEMPL/CTypedPtrList::GetTail
- AFXTEMPL/CTypedPtrList::RemoveHead
- AFXTEMPL/CTypedPtrList::RemoveTail
- AFXTEMPL/CTypedPtrList::SetAt
helpviewer_keywords:
- CTypedPtrList [MFC], AddHead
- CTypedPtrList [MFC], AddTail
- CTypedPtrList [MFC], GetAt
- CTypedPtrList [MFC], GetHead
- CTypedPtrList [MFC], GetNext
- CTypedPtrList [MFC], GetPrev
- CTypedPtrList [MFC], GetTail
- CTypedPtrList [MFC], RemoveHead
- CTypedPtrList [MFC], RemoveTail
- CTypedPtrList [MFC], SetAt
ms.assetid: c273096e-1756-4340-864b-4a08b674a65e
ms.openlocfilehash: 40dbfb822e71309e9675aba14d46d333ffa4ee06
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373268"
---
# <a name="ctypedptrlist-class"></a>Třída CTypedPtrList

Poskytuje typově bezpečné "obálky" pro `CPtrList`objekty třídy .

## <a name="syntax"></a>Syntaxe

```
template<class BASE_CLASS, class TYPE>
class CTypedPtrList : public BASE_CLASS
```

#### <a name="parameters"></a>Parametry

*BASE_CLASS*<br/>
Základní třída třídy seznamu zadaných ukazatelů; musí být třída seznamu `CObList` `CPtrList`ukazatelů ( nebo ).

*TYP*<br/>
Typ prvků uložených v seznamu základní třídy.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CTypedPtrList::Přidat hlavu](#addhead)|Přidá prvek (nebo všechny prvky v jiném seznamu) do hlavy seznamu (vytvoří novou hlavu).|
|[CTypedPtrList::AddTail](#addtail)|Přidá prvek (nebo všechny prvky v jiném seznamu) na konci seznamu (vytvoří nový ocas).|
|[CTypedPtrList::GetAt](#getat)|Získá prvek na dané pozici.|
|[CTypedPtrList::GetHead](#gethead)|Vrátí prvek hlavy seznamu (nemůže být prázdný).|
|[CTypedPtrList::GetNext](#getnext)|Získá další prvek pro iterace.|
|[CTypedPtrList::GetPrev](#getprev)|Získá předchozí prvek pro iterace.|
|[CTypedPtrList::GetTail](#gettail)|Vrátí ocasní prvek seznamu (nemůže být prázdný).|
|[CTypedPtrList::RemoveHead](#removehead)|Odebere prvek z hlavy seznamu.|
|[CTypedPtrList::RemoveTail](#removetail)|Odebere prvek z ocasu seznamu.|
|[CTypedPtrList::SetAt](#setat)|Nastaví prvek na dané pozici.|

## <a name="remarks"></a>Poznámky

Při použití `CTypedPtrList` spíše `CObList` `CPtrList`než nebo , c++ zařízení kontroly typu pomáhá eliminovat chyby způsobené neodpovídající typy ukazatelů.

Kromě toho `CTypedPtrList` obálka provádí velkou část odlitku, `CObList` `CPtrList`která by byla vyžadována, pokud jste použili nebo .

Vzhledem `CTypedPtrList` k tomu, že všechny funkce jsou vřadit, použití této šablony nemá významný vliv na velikost nebo rychlost kódu.

Seznamy odvozené z `CObList` lze serializovat, `CPtrList` ale ty, které jsou odvozeny z nelze.

Při `CTypedPtrList` odstranění objektu nebo při odebrání jeho prvků jsou odebrány pouze ukazatele, nikoli entity, na které odkazují.

Další informace o `CTypedPtrList`použití naleznete v článcích Kolekce a [Třídy](../../mfc/collections.md) [založené na šablonách](../../mfc/template-based-classes.md).

## <a name="example"></a>Příklad

Tento příklad vytvoří `CTypedPtrList`instanci aplikace , přidá jeden objekt, serializuje seznam na disk a poté objekt odstraní:

[!code-cpp[NVC_MFCCollections#110](../../mfc/codesnippet/cpp/ctypedptrlist-class_1.cpp)]

[!code-cpp[NVC_MFCCollections#111](../../mfc/codesnippet/cpp/ctypedptrlist-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`BASE_CLASS`

`_CTypedPtrList`

`CTypedPtrList`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxtempl.h

## <a name="ctypedptrlistaddhead"></a><a name="addhead"></a>CTypedPtrList::Přidat hlavu

Tato členská `BASE_CLASS`funkce volá **::AddHead**.

```
POSITION AddHead(TYPE newElement);
void AddHead(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Typ prvků uložených v seznamu základní třídy.

*newElement*<br/>
Ukazatel objektu, který má být přidán do tohoto seznamu. Hodnota NULL je povolena.

*BASE_CLASS*<br/>
Základní třída třídy seznamu zadaných ukazatelů; musí být třída seznamu ukazatelů [(CObList](../../mfc/reference/coblist-class.md) nebo [CPtrList).](../../mfc/reference/cptrlist-class.md)

*pNewList*<br/>
Ukazatel na jiný objekt [CTypedPtrList.](../../mfc/reference/ctypedptrlist-class.md) Prvky v *pNewList* budou přidány do tohoto seznamu.

### <a name="return-value"></a>Návratová hodnota

První verze vrátí hodnotu POSITION nově vloženého prvku.

### <a name="remarks"></a>Poznámky

První verze přidá nový prvek před hlavní část seznamu. Druhá verze přidá další seznam prvků před hlavou.

## <a name="ctypedptrlistaddtail"></a><a name="addtail"></a>CTypedPtrList::AddTail

Tato členská `BASE_CLASS`funkce volá **::AddTail**.

```
POSITION AddTail(TYPE newElement);
void AddTail(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Typ prvků uložených v seznamu základní třídy.

*newElement*<br/>
Ukazatel objektu, který má být přidán do tohoto seznamu. Hodnota NULL je povolena.

*BASE_CLASS*<br/>
Základní třída třídy seznamu zadaných ukazatelů; musí být třída seznamu ukazatelů [(CObList](../../mfc/reference/coblist-class.md) nebo [CPtrList).](../../mfc/reference/cptrlist-class.md)

*pNewList*<br/>
Ukazatel na jiný objekt [CTypedPtrList.](../../mfc/reference/ctypedptrlist-class.md) Prvky v *pNewList* budou přidány do tohoto seznamu.

### <a name="return-value"></a>Návratová hodnota

První verze vrátí hodnotu POSITION nově vloženého prvku.

### <a name="remarks"></a>Poznámky

První verze přidá nový prvek za ocas seznamu. Druhá verze přidá další seznam prvků za ocas seznamu.

## <a name="ctypedptrlistgetat"></a><a name="getat"></a>CTypedPtrList::GetAt

Proměnná typu POSITION je klíčem k seznamu.

```
TYPE& GetAt(POSITION position);
TYPE GetAt(POSITION position) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvků uložených v seznamu.

*Pozici*<br/>
Hodnota POSITION vrácená `GetHeadPosition` voláním předchozí nebo `Find` členské funkce.

### <a name="return-value"></a>Návratová hodnota

Pokud je seznam přístupný prostřednictvím `const CTypedPtrList`ukazatele `GetAt` na , vrátí ukazatel typu určeného parametrem šablony *TYPE*. To umožňuje funkci použít pouze na pravé straně příkazu přiřazení a tím chrání seznam před úpravou.

Pokud je seznam přístupný přímo nebo prostřednictvím ukazatele na `CTypedPtrList`, vrátí `GetAt` odkaz na ukazatel typu určeného parametrem šablony *TYPE*. To umožňuje funkci, která má být použita na obou stranách příkazu přiřazení a tím umožňuje položky seznamu, které mají být změněny.

### <a name="remarks"></a>Poznámky

Není to stejné jako index a nelze pracovat na position hodnotu sami. `GetAt`načte `CObject` ukazatel přidružený k dané pozici.

Je nutné zajistit, aby hodnota POZICE představovala platnou pozici v seznamu. Pokud je neplatný, pak ladicí verze Knihovny tříd Microsoft Foundation uplatňuje.

Tato inline `BASE_CLASS`funkce volá **::GetAt**.

## <a name="ctypedptrlistgethead"></a><a name="gethead"></a>CTypedPtrList::GetHead

Získá ukazatel, který představuje head element tohoto seznamu.

```
TYPE& GetHead();
TYPE GetHead() const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvků uložených v seznamu.

### <a name="return-value"></a>Návratová hodnota

Pokud je seznam přístupný prostřednictvím `const CTypedPtrList`ukazatele `GetHead` na , vrátí ukazatel typu určeného parametrem šablony *TYPE*. To umožňuje funkci použít pouze na pravé straně příkazu přiřazení a tím chrání seznam před úpravou.

Pokud je seznam přístupný přímo nebo prostřednictvím ukazatele na `CTypedPtrList`, vrátí `GetHead` odkaz na ukazatel typu určeného parametrem šablony *TYPE*. To umožňuje funkci, která má být použita na obou stranách příkazu přiřazení a tím umožňuje položky seznamu, které mají být změněny.

### <a name="remarks"></a>Poznámky

Před voláním `GetHead`je nutné zajistit, aby seznam nebyl prázdný. Pokud je seznam prázdný, bude uplatněna ladicí verze knihovny tříd Microsoft Foundation. Pomocí [isempty](../../mfc/reference/coblist-class.md#isempty) ověřte, zda seznam obsahuje prvky.

## <a name="ctypedptrlistgetnext"></a><a name="getnext"></a>CTypedPtrList::GetNext

Získá prvek seznamu identifikovaný *rPosition*, pak nastaví *rPosition* na hodnotu POSITION další položky v seznamu.

```
TYPE& GetNext(POSITION& rPosition);
TYPE GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvků obsažených v tomto seznamu.

*rPozice*<br/>
Odkaz na hodnotu POSITION vrácenou předchozím `GetNext`voláním `GetHeadPosition`členské funkce nebo jiným voláním členské funkce.

### <a name="return-value"></a>Návratová hodnota

Pokud je seznam přístupný prostřednictvím `const CTypedPtrList`ukazatele `GetNext` na , vrátí ukazatel typu určeného parametrem šablony *TYPE*. To umožňuje funkci použít pouze na pravé straně příkazu přiřazení a tím chrání seznam před úpravou.

Pokud je seznam přístupný přímo nebo prostřednictvím ukazatele na `CTypedPtrList`, vrátí `GetNext` odkaz na ukazatel typu určeného parametrem šablony *TYPE*. To umožňuje funkci, která má být použita na obou stranách příkazu přiřazení a tím umožňuje položky seznamu, které mají být změněny.

### <a name="remarks"></a>Poznámky

Můžete použít `GetNext` ve smyčce iterace vpřed, pokud `GetHeadPosition` navážete počáteční pozici s voláním nebo [CPtrList::Find](../../mfc/reference/coblist-class.md#find).

Je nutné zajistit, aby hodnota POZICE představovala platnou pozici v seznamu. Pokud je neplatný, pak ladicí verze Knihovny tříd Microsoft Foundation uplatňuje.

Pokud načtený prvek je poslední v seznamu, pak je nová hodnota *rPosition* nastavena na hodnotu NULL.

Je možné odebrat prvek během iterace. Viz příklad pro [CObList::RemoveAt](../../mfc/reference/coblist-class.md#removeat).

## <a name="ctypedptrlistgetprev"></a><a name="getprev"></a>CTypedPtrList::GetPrev

Získá prvek seznamu identifikovaný *rPosition*, pak nastaví *rPosition* na hodnotu POSITION předchozí položky v seznamu.

```
TYPE& GetPrev(POSITION& rPosition);
TYPE GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvků obsažených v tomto seznamu.

*rPozice*<br/>
Odkaz na hodnotu POSITION vrácenou předchozím `GetPrev` nebo jiným voláním členské funkce.

### <a name="return-value"></a>Návratová hodnota

Pokud je seznam přístupný prostřednictvím `const CTypedPtrList`ukazatele `GetPrev` na , vrátí ukazatel typu určeného parametrem šablony *TYPE*. To umožňuje funkci použít pouze na pravé straně příkazu přiřazení a tím chrání seznam před úpravou.

Pokud je seznam přístupný přímo nebo prostřednictvím ukazatele na `CTypedPtrList`, vrátí `GetPrev` odkaz na ukazatel typu určeného parametrem šablony *TYPE*. To umožňuje funkci, která má být použita na obou stranách příkazu přiřazení a tím umožňuje položky seznamu, které mají být změněny.

### <a name="remarks"></a>Poznámky

Můžete použít `GetPrev` ve smyčce zpětné iterace, pokud `GetTailPosition` navážete počáteční pozici s voláním nebo `Find`.

Je nutné zajistit, aby hodnota POZICE představovala platnou pozici v seznamu. Pokud je neplatný, pak ladicí verze Knihovny tříd Microsoft Foundation uplatňuje.

Pokud načtený prvek je první v seznamu, pak je nová hodnota *rPosition* nastavena na hodnotu NULL.

## <a name="ctypedptrlistgettail"></a><a name="gettail"></a>CTypedPtrList::GetTail

Získá ukazatel, který představuje head element tohoto seznamu.

```
TYPE& GetTail();
TYPE GetTail() const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvků uložených v seznamu.

### <a name="return-value"></a>Návratová hodnota

Pokud je seznam přístupný prostřednictvím `const CTypedPtrList`ukazatele `GetTail` na , vrátí ukazatel typu určeného parametrem šablony *TYPE*. To umožňuje funkci použít pouze na pravé straně příkazu přiřazení a tím chrání seznam před úpravou.

Pokud je seznam přístupný přímo nebo prostřednictvím ukazatele na `CTypedPtrList`, vrátí `GetTail` odkaz na ukazatel typu určeného parametrem šablony *TYPE*. To umožňuje funkci, která má být použita na obou stranách příkazu přiřazení a tím umožňuje položky seznamu, které mají být změněny.

### <a name="remarks"></a>Poznámky

Před voláním `GetTail`je nutné zajistit, aby seznam nebyl prázdný. Pokud je seznam prázdný, bude uplatněna ladicí verze knihovny tříd Microsoft Foundation. Pomocí [isempty](../../mfc/reference/coblist-class.md#isempty) ověřte, zda seznam obsahuje prvky.

## <a name="ctypedptrlistremovehead"></a><a name="removehead"></a>CTypedPtrList::RemoveHead

Odebere prvek z hlavy seznamu a vrátí jej.

```
TYPE RemoveHead();
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvků uložených v seznamu.

### <a name="return-value"></a>Návratová hodnota

Ukazatel dříve v čele seznamu. Tento ukazatel je typu určeného parametrem šablony *TYPE*.

### <a name="remarks"></a>Poznámky

Před voláním `RemoveHead`je nutné zajistit, aby seznam nebyl prázdný. Pokud je seznam prázdný, bude uplatněna ladicí verze knihovny tříd Microsoft Foundation. Pomocí [isempty](../../mfc/reference/coblist-class.md#isempty) ověřte, zda seznam obsahuje prvky.

## <a name="ctypedptrlistremovetail"></a><a name="removetail"></a>CTypedPtrList::RemoveTail

Odebere prvek z ocasu seznamu a vrátí jej.

```
TYPE RemoveTail();
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvků uložených v seznamu.

### <a name="return-value"></a>Návratová hodnota

Ukazatel dříve na konci seznamu. Tento ukazatel je typu určeného parametrem šablony *TYPE*.

### <a name="remarks"></a>Poznámky

Před voláním `RemoveTail`je nutné zajistit, aby seznam nebyl prázdný. Pokud je seznam prázdný, bude uplatněna ladicí verze knihovny tříd Microsoft Foundation. Pomocí [isempty](../../mfc/reference/coblist-class.md#isempty) ověřte, zda seznam obsahuje prvky.

## <a name="ctypedptrlistsetat"></a><a name="setat"></a>CTypedPtrList::SetAt

Tato členská `BASE_CLASS`funkce volá **::SetAt**.

```
void SetAt(POSITION pos, TYPE newElement);
```

### <a name="parameters"></a>Parametry

*Pos*<br/>
POZICE prvku, který má být nastaven.

*TYP*<br/>
Typ prvků uložených v seznamu základní třídy.

*newElement*<br/>
Ukazatel objektu, který má být zapsán do seznamu.

### <a name="remarks"></a>Poznámky

Proměnná typu POSITION je klíčem k seznamu. Není to stejné jako index a nelze pracovat na position hodnotu sami. `SetAt`zapíše ukazatel objektu na zadanou pozici v seznamu.

Je nutné zajistit, aby hodnota POZICE představovala platnou pozici v seznamu. Pokud je neplatný, pak ladicí verze Knihovny tříd Microsoft Foundation uplatňuje.

Podrobnější poznámky naleznete v tématu [CObList::SetAt](../../mfc/reference/coblist-class.md#setat).

## <a name="see-also"></a>Viz také

[Odběr vzorku knihovny MFC](../../overview/visual-cpp-samples.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CPtrList](../../mfc/reference/cptrlist-class.md)<br/>
[Třída CObList](../../mfc/reference/coblist-class.md)
