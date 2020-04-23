---
title: Třída CTypedPtrArray
ms.date: 11/04/2016
f1_keywords:
- CTypedPtrArray
- AFXTEMPL/CTypedPtrArray
- AFXTEMPL/CTypedPtrArray::Add
- AFXTEMPL/CTypedPtrArray::Append
- AFXTEMPL/CTypedPtrArray::Copy
- AFXTEMPL/CTypedPtrArray::ElementAt
- AFXTEMPL/CTypedPtrArray::GetAt
- AFXTEMPL/CTypedPtrArray::InsertAt
- AFXTEMPL/CTypedPtrArray::SetAt
- AFXTEMPL/CTypedPtrArray::SetAtGrow
helpviewer_keywords:
- CTypedPtrArray [MFC], Add
- CTypedPtrArray [MFC], Append
- CTypedPtrArray [MFC], Copy
- CTypedPtrArray [MFC], ElementAt
- CTypedPtrArray [MFC], GetAt
- CTypedPtrArray [MFC], InsertAt
- CTypedPtrArray [MFC], SetAt
- CTypedPtrArray [MFC], SetAtGrow
ms.assetid: e3ecdf1a-a889-4156-92dd-ddbd36ccd919
ms.openlocfilehash: 20cf147e955b6b19919f35750b0f46a8b5a67ad0
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752059"
---
# <a name="ctypedptrarray-class"></a>Třída CTypedPtrArray

Poskytuje typově bezpečné "obálky" pro `CPtrArray` `CObArray`objekty třídy nebo .

## <a name="syntax"></a>Syntaxe

```
template<class BASE_CLASS, class TYPE>
class CTypedPtrArray : public BASE_CLASS
```

#### <a name="parameters"></a>Parametry

*BASE_CLASS*<br/>
Základní třída zadané třídy pole ukazatele; musí být třída `CObArray` pole `CPtrArray`(nebo).

*TYP*<br/>
Typ prvků uložených v poli základní třídy.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CTypedPtrArray::Přidat](#add)|Přidá nový prvek na konec pole. V případě potřeby pole zvětší|
|[CTypedPtrArray::Připojit](#append)|Přidá obsah jednoho pole na konec jiného. V případě potřeby pole zvětší|
|[CTypedPtrArray::Kopírovat](#copy)|Zkopíruje do pole jiné pole. v případě potřeby pole zvětší.|
|[CTypedPtrArray::ElementAt](#elementat)|Vrátí dočasný odkaz na ukazatel prvku v rámci pole.|
|[CTypedPtrArray::GetAt](#getat)|Vrátí hodnotu v daném indexu.|
|[CTypedPtrArray::InsertAt](#insertat)|Vloží prvek (nebo všechny prvky v jiném poli) v zadaném indexu.|
|[CTypedPtrArray::SetAt](#setat)|Nastaví hodnotu pro daný index; pole nesmí růst.|
|[CTypedPtrArray::SetAtGrow](#setatgrow)|Nastaví hodnotu pro daný index; v případě potřeby pole zvětší.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CTypedPtrArray::operátor \[\]](#operator_at)|Nastaví nebo získá prvek na zadaný index.|

## <a name="remarks"></a>Poznámky

Při použití `CTypedPtrArray` spíše `CPtrArray` `CObArray`než nebo , c++ zařízení kontroly typu pomáhá eliminovat chyby způsobené neodpovídající typy ukazatelů.

Kromě toho `CTypedPtrArray` obálka provádí velkou část odlitku, `CObArray` `CPtrArray`která by byla vyžadována, pokud jste použili nebo .

Vzhledem `CTypedPtrArray` k tomu, že všechny funkce jsou vřadit, použití této šablony nemá významný vliv na velikost nebo rychlost kódu.

Další informace o `CTypedPtrArray`použití naleznete v článcích Kolekce a [Třídy](../../mfc/collections.md) [založené na šablonách](../../mfc/template-based-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`BASE_CLASS`

`CTypedPtrArray`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxtempl.h

## <a name="ctypedptrarrayadd"></a><a name="add"></a>CTypedPtrArray::Přidat

Tato členská `BASE_CLASS`funkce volá **::Add**.

```
INT_PTR Add(TYPE newElement);
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvku, který má být přidán do pole.

*newElement*<br/>
Prvek, který má být přidán do tohoto pole.

### <a name="return-value"></a>Návratová hodnota

Index přidaného prvku.

### <a name="remarks"></a>Poznámky

Podrobnější poznámky naleznete v tématu [CObArray::Add](../../mfc/reference/cobarray-class.md#add).

## <a name="ctypedptrarrayappend"></a><a name="append"></a>CTypedPtrArray::Připojit

Tato členská `BASE_CLASS`funkce volá ::Append**.

```
INT_PTR Append(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```

### <a name="parameters"></a>Parametry

*BASE_CLASS*<br/>
Základní třída zadané třídy pole ukazatele; musí být třída pole [(CObArray](../../mfc/reference/cobarray-class.md) nebo [CPtrArray).](../../mfc/reference/cptrarray-class.md)

*TYP*<br/>
Typ prvků uložených v poli základní třídy.

*src*<br/>
Zdroj prvků, které mají být připojeny k poli.

### <a name="return-value"></a>Návratová hodnota

Index první ho připojit prvek.

### <a name="remarks"></a>Poznámky

Podrobnější poznámky naleznete v tématu [CObArray::Append](../../mfc/reference/cobarray-class.md#append).

## <a name="ctypedptrarraycopy"></a><a name="copy"></a>CTypedPtrArray::Kopírovat

Tato členská `BASE_CLASS`funkce volá **::Copy**.

```cpp
void Copy(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```

### <a name="parameters"></a>Parametry

*BASE_CLASS*<br/>
Základní třída zadané třídy pole ukazatele; musí být třída pole [(CObArray](../../mfc/reference/cobarray-class.md) nebo [CPtrArray).](../../mfc/reference/cptrarray-class.md)

*TYP*<br/>
Typ prvků uložených v poli základní třídy.

*src*<br/>
Zdroj prvků, které mají být zkopírovány do pole.

### <a name="remarks"></a>Poznámky

Podrobnější poznámky naleznete v tématu [CObArray::Copy](../../mfc/reference/cobarray-class.md#copy).

## <a name="ctypedptrarrayelementat"></a><a name="elementat"></a>CTypedPtrArray::ElementAt

Tato inline `BASE_CLASS`funkce volá **::ElementAt**.

```
TYPE& ElementAt(INT_PTR nIndex);
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvků uložených v tomto poli.

*nIndex*<br/>
Index celéčíslo, který je větší nebo roven 0 a menší `BASE_CLASS`než nebo rovno hodnotě vrácené **::GetUpperBound**.

### <a name="return-value"></a>Návratová hodnota

Dočasný odkaz na prvek v umístění určeném *nIndex*. Tento prvek je typu určeného parametrem šablony *TYPE*.

### <a name="remarks"></a>Poznámky

Podrobnější poznámky naleznete v tématu [CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat).

## <a name="ctypedptrarraygetat"></a><a name="getat"></a>CTypedPtrArray::GetAt

Tato inline `BASE_CLASS`funkce volá **::GetAt**.

```
TYPE GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvků uložených v poli.

*nIndex*<br/>
Index celéčíslo, který je větší nebo roven 0 a menší `BASE_CLASS`než nebo rovno hodnotě vrácené **::GetUpperBound**.

### <a name="return-value"></a>Návratová hodnota

Kopie prvku v umístění určeném *nIndex*. Tento prvek je typu určeného parametrem šablony *TYPE*.

### <a name="remarks"></a>Poznámky

Podrobnější poznámky naleznete v tématu [CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)

## <a name="ctypedptrarrayinsertat"></a><a name="insertat"></a>CTypedPtrArray::InsertAt

Tato členská `BASE_CLASS`funkce volá **::InsertAt**.

```cpp
void InsertAt(
    INT_PTR nIndex,
    TYPE newElement,
    INT_PTR nCount = 1);

void InsertAt(
    INT_PTR nStartIndex,
    CTypedPtrArray<BASE_CLASS, TYPE>* pNewArray);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index celéčíslo, který může být větší než hodnota vrácená [CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound).

*TYP*<br/>
Typ prvků uložených v poli základní třídy.

*newElement*<br/>
Ukazatel objektu, který má být umístěn v tomto poli. *NewElement* hodnoty **NULL** je povolena.

*nCount*<br/>
Počet, kolikrát by měl být tento prvek vložen (výchozí hodnota je 1).

*nStartIndex*<br/>
Index celého čísla, který může být `CObArray::GetUpperBound`větší než hodnota vrácená .

*BASE_CLASS*<br/>
Základní třída zadané třídy pole ukazatele; musí být třída pole [(CObArray](../../mfc/reference/cobarray-class.md) nebo [CPtrArray).](../../mfc/reference/cptrarray-class.md)

*pNewArray*<br/>
Jiné pole, které obsahuje prvky, které mají být přidány do tohoto pole.

### <a name="remarks"></a>Poznámky

Podrobnější poznámky naleznete v tématu [CObArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat).

## <a name="ctypedptrarrayoperator--"></a><a name="operator_at"></a>CTypedPtrArray::operátor [ ]

Tyto inline `BASE_CLASS`operátory volají **::operator [ ]**.

```
TYPE& operator[ ](int_ptr nindex);
TYPE operator[ ](int_ptr nindex) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvků uložených v poli.

*nIndex*<br/>
Index celéčíslo, který je větší nebo roven 0 a menší `BASE_CLASS`než nebo rovno hodnotě vrácené **::GetUpperBound**.

### <a name="remarks"></a>Poznámky

První operátor, volaný pro pole, která nejsou **const**, lze použít buď vpravo (hodnota r) nebo vlevo (l-hodnota) příkazu přiřazení. Druhý, vyvolána pro **const** pole, lze použít pouze na pravé straně.

Ladicí verze knihovny uplatňuje, pokud je dolní index (na levé nebo pravé straně příkazu přiřazení) mimo hranice.

## <a name="ctypedptrarraysetat"></a><a name="setat"></a>CTypedPtrArray::SetAt

Tato členská `BASE_CLASS`funkce volá **::SetAt**.

```cpp
void SetAt(
    INT_PTR nIndex,
    TYPE ptr);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index celéčíslo, který je větší nebo roven 0 a menší než nebo rovno hodnotě vrácené [CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound).

*TYP*<br/>
Typ prvků uložených v poli základní třídy.

*Ptr*<br/>
Ukazatel na prvek, který má být vložen do pole na nIndex. Hodnota NULL je povolena.

### <a name="remarks"></a>Poznámky

Podrobnější poznámky naleznete v tématu [CObArray::SetAt](../../mfc/reference/cobarray-class.md#setat).

## <a name="ctypedptrarraysetatgrow"></a><a name="setatgrow"></a>CTypedPtrArray::SetAtGrow

Tato členská `BASE_CLASS`funkce volá **::SetAtGrow**.

```cpp
void SetAtGrow(
    INT_PTR nIndex,
    TYPE newElement);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index celého čísla, který je větší nebo roven 0.

*TYP*<br/>
Typ prvků uložených v poli základní třídy.

*newElement*<br/>
Ukazatel objektu, který má být přidán do tohoto pole. Hodnota **NULL** je povolena.

### <a name="remarks"></a>Poznámky

Podrobnější poznámky naleznete v tématu [CObArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow).

## <a name="see-also"></a>Viz také

[Odběr vzorku knihovny MFC](../../overview/visual-cpp-samples.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CPtrArray](../../mfc/reference/cptrarray-class.md)<br/>
[Třída CObArray](../../mfc/reference/cobarray-class.md)
