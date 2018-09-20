---
title: Ctypedptrlist – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 758be6cfec0c4d70ebf632eaf90e3623632ffbe5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417511"
---
# <a name="ctypedptrlist-class"></a>Ctypedptrlist – třída

Poskytuje typově "zabezpečenou obálku" pro objekty třídy `CPtrList`.

## <a name="syntax"></a>Syntaxe

```
template<class BASE_CLASS, class TYPE>
class CTypedPtrList : public BASE_CLASS
```

#### <a name="parameters"></a>Parametry

*$BASE_CLASS*<br/>
Základní třída typované ukazatele seznamu třídy; musí být třída seznamu ukazatel ( `CObList` nebo `CPtrList`).

*TYP*<br/>
Typ prvků uložených v seznamu základní třídy.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CTypedPtrList::AddHead](#addhead)|Přidá k začátku seznamu (novou vedoucí díky) elementu (nebo všechny prvky v jiném seznamu).|
|[CTypedPtrList::AddTail](#addtail)|Přidá na konec seznamu (umožňuje nové funkce tail) elementu (nebo všechny prvky v jiném seznamu).|
|[CTypedPtrList::GetAt](#getat)|Získá prvek na dané pozici.|
|[CTypedPtrList::GetHead](#gethead)|Vrátí element head seznamu (nemůže být prázdný).|
|[CTypedPtrList::GetNext](#getnext)|Získá další prvek pro iterace.|
|[CTypedPtrList::GetPrev](#getprev)|Získá předchozí prvek pro iterace.|
|[CTypedPtrList::GetTail](#gettail)|Vrátí element tail seznamu (nemůže být prázdný).|
|[CTypedPtrList::RemoveHead](#removehead)|Odebere element z prvního seznamu.|
|[CTypedPtrList::RemoveTail](#removetail)|Odebere element z konec seznamu.|
|[CTypedPtrList::SetAt](#setat)|Nastaví element na dané pozici.|

## <a name="remarks"></a>Poznámky

Při použití `CTypedPtrList` spíše než `CObList` nebo `CPtrList`, kontroly typů zařízení C++ pomáhá eliminovat chyby způsobené typy neodpovídající ukazatelů.

Kromě toho `CTypedPtrList` obálky provádí velkou část přetypování, které by bylo zapotřebí, pokud jste použili `CObList` nebo `CPtrList`.

Protože všechny `CTypedPtrList` jsou vložené funkce, použijte tato šablona nemá vliv na výrazně velikost nebo rychlost kódu.

Seznam je odvozen z `CObList` lze serializovat, ale které pocházejí z `CPtrList` nelze.

Když `CTypedPtrList` odstranění objektu nebo při jeho prvky jsou odebrány, odeberou se jenom ukazatele, není entity, které odkazují.

Další informace o používání `CTypedPtrList`, najdete v článcích [kolekce](../../mfc/collections.md) a [založené na šablonách třídy](../../mfc/template-based-classes.md).

## <a name="example"></a>Příklad

Tento příklad vytvoří instanci `CTypedPtrList`, přidá jeden objekt, serializuje seznamu na disk a poté odstraní objekt:

[!code-cpp[NVC_MFCCollections#110](../../mfc/codesnippet/cpp/ctypedptrlist-class_1.cpp)]

[!code-cpp[NVC_MFCCollections#111](../../mfc/codesnippet/cpp/ctypedptrlist-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`BASE_CLASS`

`_CTypedPtrList`

`CTypedPtrList`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxtempl.h

##  <a name="addhead"></a>  CTypedPtrList::AddHead

Tato členská funkce volá `BASE_CLASS` **:: AddHead**.

```
POSITION AddHead(TYPE newElement);
void AddHead(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Typ prvků uložených v seznamu základní třídy.

*newElement*<br/>
Ukazatel objektu přidávané do tohoto seznamu. Je povolena hodnota NULL.

*$BASE_CLASS*<br/>
Základní třída typované ukazatele seznamu třídy; musí být třída seznamu ukazatel ( [coblist –](../../mfc/reference/coblist-class.md) nebo [cptrlist –](../../mfc/reference/cptrlist-class.md)).

*pNewList*<br/>
Ukazatel na jiný [ctypedptrlist –](../../mfc/reference/ctypedptrlist-class.md) objektu. Prvky v *pNewList* budou přidány do tohoto seznamu.

### <a name="return-value"></a>Návratová hodnota

První verze vrátí hodnotu pozice nově vložený prvek.

### <a name="remarks"></a>Poznámky

První verze přidá nový prvek před první pozice v seznamu. Druhá verze přidá jiného seznamu elementů před první pozice.

##  <a name="addtail"></a>  CTypedPtrList::AddTail

Tato členská funkce volá `BASE_CLASS` **:: addtail –**.

```
POSITION AddTail(TYPE newElement);
void AddTail(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Typ prvků uložených v seznamu základní třídy.

*newElement*<br/>
Ukazatel objektu přidávané do tohoto seznamu. Je povolena hodnota NULL.

*$BASE_CLASS*<br/>
Základní třída typované ukazatele seznamu třídy; musí být třída seznamu ukazatel ( [coblist –](../../mfc/reference/coblist-class.md) nebo [cptrlist –](../../mfc/reference/cptrlist-class.md)).

*pNewList*<br/>
Ukazatel na jiný [ctypedptrlist –](../../mfc/reference/ctypedptrlist-class.md) objektu. Prvky v *pNewList* budou přidány do tohoto seznamu.

### <a name="return-value"></a>Návratová hodnota

První verze vrátí hodnotu pozice nově vložený prvek.

### <a name="remarks"></a>Poznámky

První verze přidá nový prvek po konec seznamu. Druhá verze přidá jiného seznamu prvků po konec seznamu.

##  <a name="getat"></a>  CTypedPtrList::GetAt

Proměnné typu pozice je klíč pro seznam.

```
TYPE& GetAt(POSITION position);
TYPE GetAt(POSITION position) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvků uložených v seznamu.

*Pozice*<br/>
Hodnota pozice vrácené předchozím `GetHeadPosition` nebo `Find` volání členské funkce.

### <a name="return-value"></a>Návratová hodnota

Pokud v seznamu se přistupuje přes ukazatel `const CTypedPtrList`, pak `GetAt` vrací ukazatel určeného parametrem šablony typu *typ*. To umožňuje funkce, která se použije pouze na pravé straně příkazu přiřazení a tedy chrání před změnou seznamu.

Pokud se v seznamu přistupuje přímo nebo prostřednictvím ukazatele na `CTypedPtrList`, pak `GetAt` vrátí odkaz na ukazatel typu určeného parametrem šablony *typ*. To umožňuje funkce, která se použije na obou stranách příkazu přiřazení a tím umožňuje položky seznamu, který má být upraven.

### <a name="remarks"></a>Poznámky

Není stejný jako index a nemůžete pracovat na základě hodnoty pozice sami. `GetAt` načte `CObject` ukazatel spojené s danou pozici.

Ujistěte se, že hodnota pozice představuje platná pozice v seznamu. Pokud je neplatná, ladicí verze knihovny Microsoft Foundation Class se vyhodnotí.

Tato vložená funkce zavolá `BASE_CLASS` **:: GetAt**.

##  <a name="gethead"></a>  CTypedPtrList::GetHead

Získá ukazatel, který reprezentuje element head tohoto seznamu.

```
TYPE& GetHead();
TYPE GetHead() const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvků uložených v seznamu.

### <a name="return-value"></a>Návratová hodnota

Pokud v seznamu se přistupuje přes ukazatel `const CTypedPtrList`, pak `GetHead` vrací ukazatel určeného parametrem šablony typu *typ*. To umožňuje funkce, která se použije pouze na pravé straně příkazu přiřazení a tedy chrání před změnou seznamu.

Pokud se v seznamu přistupuje přímo nebo prostřednictvím ukazatele na `CTypedPtrList`, pak `GetHead` vrátí odkaz na ukazatel typu určeného parametrem šablony *typ*. To umožňuje funkce, která se použije na obou stranách příkazu přiřazení a tím umožňuje položky seznamu, který má být upraven.

### <a name="remarks"></a>Poznámky

Ujistěte se, že seznam není prázdný před voláním `GetHead`. Pokud je seznam prázdný, pak vyhodnotí ladicí verze knihovny Microsoft Foundation Class. Použití [IsEmpty](../../mfc/reference/coblist-class.md#isempty) ověřit, zda seznam obsahuje prvky.

##  <a name="getnext"></a>  CTypedPtrList::GetNext

Získá seznam prvek identifikovaný *rposition*, pak nastaví *rposition* hodnotu pozice další položky v seznamu.

```
TYPE& GetNext(POSITION& rPosition);
TYPE GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ elementů obsažených v tomto seznamu.

*rposition.*<br/>
Odkaz na POZICI hodnotu vrácenou předchozím `GetNext`, `GetHeadPosition`, nebo jiné členské funkce volání.

### <a name="return-value"></a>Návratová hodnota

Pokud v seznamu se přistupuje přes ukazatel `const CTypedPtrList`, pak `GetNext` vrací ukazatel určeného parametrem šablony typu *typ*. To umožňuje funkce, která se použije pouze na pravé straně příkazu přiřazení a tedy chrání před změnou seznamu.

Pokud se v seznamu přistupuje přímo nebo prostřednictvím ukazatele na `CTypedPtrList`, pak `GetNext` vrátí odkaz na ukazatel typu určeného parametrem šablony *typ*. To umožňuje funkce, která se použije na obou stranách příkazu přiřazení a tím umožňuje položky seznamu, který má být upraven.

### <a name="remarks"></a>Poznámky

Můžete použít `GetNext` v dopředné iteraci smyčky, Pokud zavedete počáteční pozici voláním `GetHeadPosition` nebo [CPtrList::Find](../../mfc/reference/coblist-class.md#find).

Ujistěte se, že hodnota pozice představuje platná pozice v seznamu. Pokud je neplatná, ladicí verze knihovny Microsoft Foundation Class se vyhodnotí.

Pokud je načtený element poslední v seznamu, pak nová hodnota *rposition* nastaven na hodnotu NULL.

Je možné odebrat element během iterace. Podívejte se na příklad pro [CObList::RemoveAt](../../mfc/reference/coblist-class.md#removeat).

##  <a name="getprev"></a>  CTypedPtrList::GetPrev

Získá seznam prvek identifikovaný *rposition*, pak nastaví *rposition* pozice hodnotu předchozí položka v seznamu.

```
TYPE& GetPrev(POSITION& rPosition);
TYPE GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ elementů obsažených v tomto seznamu.

*rposition.*<br/>
Odkaz na POZICI hodnotu vrácenou předchozím `GetPrev` nebo jiné členské funkce volání.

### <a name="return-value"></a>Návratová hodnota

Pokud v seznamu se přistupuje přes ukazatel `const CTypedPtrList`, pak `GetPrev` vrací ukazatel určeného parametrem šablony typu *typ*. To umožňuje funkce, která se použije pouze na pravé straně příkazu přiřazení a tedy chrání před změnou seznamu.

Pokud se v seznamu přistupuje přímo nebo prostřednictvím ukazatele na `CTypedPtrList`, pak `GetPrev` vrátí odkaz na ukazatel typu určeného parametrem šablony *typ*. To umožňuje funkce, která se použije na obou stranách příkazu přiřazení a tím umožňuje položky seznamu, který má být upraven.

### <a name="remarks"></a>Poznámky

Můžete použít `GetPrev` v reverzní iteraci smyčky, Pokud zavedete počáteční pozici voláním `GetTailPosition` nebo `Find`.

Ujistěte se, že hodnota pozice představuje platná pozice v seznamu. Pokud je neplatná, ladicí verze knihovny Microsoft Foundation Class se vyhodnotí.

Je-li načíst prvek je první v seznamu, pak nová hodnota *rposition* nastaven na hodnotu NULL.

##  <a name="gettail"></a>  CTypedPtrList::GetTail

Získá ukazatel, který reprezentuje element head tohoto seznamu.

```
TYPE& GetTail();
TYPE GetTail() const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvků uložených v seznamu.

### <a name="return-value"></a>Návratová hodnota

Pokud v seznamu se přistupuje přes ukazatel `const CTypedPtrList`, pak `GetTail` vrací ukazatel určeného parametrem šablony typu *typ*. To umožňuje funkce, která se použije pouze na pravé straně příkazu přiřazení a tedy chrání před změnou seznamu.

Pokud se v seznamu přistupuje přímo nebo prostřednictvím ukazatele na `CTypedPtrList`, pak `GetTail` vrátí odkaz na ukazatel typu určeného parametrem šablony *typ*. To umožňuje funkce, která se použije na obou stranách příkazu přiřazení a tím umožňuje položky seznamu, který má být upraven.

### <a name="remarks"></a>Poznámky

Ujistěte se, že seznam není prázdný před voláním `GetTail`. Pokud je seznam prázdný, pak vyhodnotí ladicí verze knihovny Microsoft Foundation Class. Použití [IsEmpty](../../mfc/reference/coblist-class.md#isempty) ověřit, zda seznam obsahuje prvky.

##  <a name="removehead"></a>  CTypedPtrList::RemoveHead

Odebere element z prvního seznamu a vrátí jej.

```
TYPE RemoveHead();
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvků uložených v seznamu.

### <a name="return-value"></a>Návratová hodnota

Ukazatel dříve na začátku seznamu. Tento ukazatel je určeného parametrem šablony typu *typ*.

### <a name="remarks"></a>Poznámky

Ujistěte se, že seznam není prázdný před voláním `RemoveHead`. Pokud je seznam prázdný, pak vyhodnotí ladicí verze knihovny Microsoft Foundation Class. Použití [IsEmpty](../../mfc/reference/coblist-class.md#isempty) ověřit, zda seznam obsahuje prvky.

##  <a name="removetail"></a>  CTypedPtrList::RemoveTail

Odebere element z konec seznamu a vrátí jej.

```
TYPE RemoveTail();
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvků uložených v seznamu.

### <a name="return-value"></a>Návratová hodnota

Ukazatel dříve na konec seznamu. Tento ukazatel je určeného parametrem šablony typu *typ*.

### <a name="remarks"></a>Poznámky

Ujistěte se, že seznam není prázdný před voláním `RemoveTail`. Pokud je seznam prázdný, pak vyhodnotí ladicí verze knihovny Microsoft Foundation Class. Použití [IsEmpty](../../mfc/reference/coblist-class.md#isempty) ověřit, zda seznam obsahuje prvky.

##  <a name="setat"></a>  CTypedPtrList::SetAt

Tato členská funkce volá `BASE_CLASS` **:: SetAt**.

```
void SetAt(POSITION pos, TYPE newElement);
```

### <a name="parameters"></a>Parametry

*POS*<br/>
Pozice prvku, který chcete nastavit.

*TYP*<br/>
Typ prvků uložených v seznamu základní třídy.

*newElement*<br/>
Ukazatel objektu, který má být zapsán do seznamu.

### <a name="remarks"></a>Poznámky

Proměnné typu pozice je klíč pro seznam. Není stejný jako index a nemůžete pracovat na základě hodnoty pozice sami. `SetAt` zapíše objekt ukazatel na určenou pozici v seznamu.

Ujistěte se, že hodnota pozice představuje platná pozice v seznamu. Pokud je neplatná, ladicí verze knihovny Microsoft Foundation Class se vyhodnotí.

Podrobné poznámky, naleznete v tématu [CObList::SetAt](../../mfc/reference/coblist-class.md#setat).

## <a name="see-also"></a>Viz také

[Ukázky knihovny MFC shromažďování](../../visual-cpp-samples.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CPtrList – třída](../../mfc/reference/cptrlist-class.md)<br/>
[CObList – třída](../../mfc/reference/coblist-class.md)
