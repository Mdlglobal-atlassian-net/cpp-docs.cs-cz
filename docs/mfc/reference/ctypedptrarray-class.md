---
title: Ctypedptrarray – třída
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
ms.openlocfilehash: 767d4782ec637a0404051e6871d584f73cefdcd2
ms.sourcegitcommit: 53f75afaf3c0b3ed481c5503357ed2b7b87aac6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2018
ms.locfileid: "53657471"
---
# <a name="ctypedptrarray-class"></a>Ctypedptrarray – třída

Poskytuje typově "zabezpečenou obálku" pro objekty třídy `CPtrArray` nebo `CObArray`.

## <a name="syntax"></a>Syntaxe

```
template<class BASE_CLASS, class TYPE>
class CTypedPtrArray : public BASE_CLASS
```

#### <a name="parameters"></a>Parametry

*$BASE_CLASS*<br/>
Základní třída typované ukazatele pole třídy; musí být třída pole ( `CObArray` nebo `CPtrArray`).

*TYP*<br/>
Typ prvků uložených v poli základní třídy.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CTypedPtrArray::Add](#add)|Přidá nový prvek na konec pole. V případě potřeby roste pole|
|[CTypedPtrArray::Append](#append)|Přidá na konec jiné obsah jedno pole. V případě potřeby roste pole|
|[CTypedPtrArray::Copy](#copy)|Zkopíruje jiného objektu array do pole. v případě potřeby se zvětší pole.|
|[CTypedPtrArray::ElementAt](#elementat)|Vrátí dočasný odkaz na ukazatel na prvek v poli.|
|[CTypedPtrArray::GetAt](#getat)|Vrátí hodnotu na daném indexu.|
|[CTypedPtrArray::InsertAt](#insertat)|Vloží zadaný index elementu (nebo všechny prvky v jiného objektu array).|
|[CTypedPtrArray::SetAt](#setat)|Nastaví hodnotu pro daný index; pole nesmí růst.|
|[CTypedPtrArray::SetAtGrow](#setatgrow)|Nastaví hodnotu pro daný index; v případě potřeby se zvětší pole.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CTypedPtrArray::operator \[ \]](#operator_at)|Nastaví nebo získá prvek na zadaném indexu.|

## <a name="remarks"></a>Poznámky

Při použití `CTypedPtrArray` spíše než `CPtrArray` nebo `CObArray`, kontroly typů zařízení C++ pomáhá eliminovat chyby způsobené typy neodpovídající ukazatelů.

Kromě toho `CTypedPtrArray` obálky provádí velkou část přetypování, které by bylo zapotřebí, pokud jste použili `CObArray` nebo `CPtrArray`.

Protože všechny `CTypedPtrArray` jsou vložené funkce, použijte tato šablona nemá vliv na výrazně velikost nebo rychlost kódu.

Další informace o používání `CTypedPtrArray`, najdete v článcích [kolekce](../../mfc/collections.md) a [založené na šablonách třídy](../../mfc/template-based-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`BASE_CLASS`

`CTypedPtrArray`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxtempl.h

##  <a name="add"></a>  CTypedPtrArray::Add

Tato členská funkce volá `BASE_CLASS` **:: Přidat**.

```
INT_PTR Add(TYPE newElement);
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvku, které mají být přidány do pole.

*newElement*<br/>
Elementu, který chcete přidat do tohoto pole.

### <a name="return-value"></a>Návratová hodnota

Index elementu přidal.

### <a name="remarks"></a>Poznámky

Podrobné poznámky, naleznete v tématu [CObArray::Add](../../mfc/reference/cobarray-class.md#add).

##  <a name="append"></a>  CTypedPtrArray::Append

Tato členská funkce volá `BASE_CLASS`:: připojit **.

```
INT_PTR Append(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```

### <a name="parameters"></a>Parametry

*$BASE_CLASS*<br/>
Základní třída typované ukazatele pole třídy; musí být třída pole ( [cobarray –](../../mfc/reference/cobarray-class.md) nebo [cptrarray –](../../mfc/reference/cptrarray-class.md)).

*TYP*<br/>
Typ prvků uložených v poli základní třídy.

*src*<br/>
Zdroj prvky, které je připojeno k matici.

### <a name="return-value"></a>Návratová hodnota

Index první připojený prvek.

### <a name="remarks"></a>Poznámky

Podrobné poznámky, naleznete v tématu [CObArray::Append](../../mfc/reference/cobarray-class.md#append).

##  <a name="copy"></a>  CTypedPtrArray::Copy

Tato členská funkce volá `BASE_CLASS` **:: kopírování**.

```
void Copy(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```

### <a name="parameters"></a>Parametry

*$BASE_CLASS*<br/>
Základní třída typované ukazatele pole třídy; musí být třída pole ( [cobarray –](../../mfc/reference/cobarray-class.md) nebo [cptrarray –](../../mfc/reference/cptrarray-class.md)).

*TYP*<br/>
Typ prvků uložených v poli základní třídy.

*src*<br/>
Zdroj prvky, které mají být zkopírovány do pole.

### <a name="remarks"></a>Poznámky

Podrobné poznámky, naleznete v tématu [CObArray::Copy](../../mfc/reference/cobarray-class.md#copy).

##  <a name="elementat"></a>  CTypedPtrArray::ElementAt

Tato vložená funkce zavolá `BASE_CLASS` **:: ElementAt**.

```
TYPE& ElementAt(INT_PTR nIndex);
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvků uložených v tomto poli.

*nIndex*<br/>
Celočíselný index, který je větší než nebo rovna 0 a menší nebo rovna hodnotě vrácené `BASE_CLASS` **:: GetUpperBound**.

### <a name="return-value"></a>Návratová hodnota

Dočasný odkaz na prvek v umístění určeném *nIndex*. Tento element je určeného parametrem šablony typu *typ*.

### <a name="remarks"></a>Poznámky

Podrobné poznámky, naleznete v tématu [CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat).

##  <a name="getat"></a>  CTypedPtrArray::GetAt

Tato vložená funkce zavolá `BASE_CLASS` **:: GetAt**.

```
TYPE GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvků uložených v poli.

*nIndex*<br/>
Celočíselný index, který je větší než nebo rovna 0 a menší nebo rovna hodnotě vrácené `BASE_CLASS` **:: GetUpperBound**.

### <a name="return-value"></a>Návratová hodnota

Zkopírovat element v místě určeném *nIndex*. Tento element je určeného parametrem šablony typu *typ*.

### <a name="remarks"></a>Poznámky

Podrobné poznámky, naleznete v tématu [CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)

##  <a name="insertat"></a>  CTypedPtrArray::InsertAt

Tato členská funkce volá `BASE_CLASS` **:: InsertAt**.

```
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
Celočíselný index, který může být větší než hodnota vrácená [CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound).

*TYP*<br/>
Typ prvků uložených v poli základní třídy.

*newElement*<br/>
Ukazatel objektu budou umístěny v tomto poli. A *newElement* hodnoty **NULL** je povolen.

*nCount*<br/>
Počet pokusů, které tento prvek by měl být vložen (výchozí nastavení: 1).

*nStartIndex*<br/>
Celočíselný index, který může být větší než hodnota vrácená `CObArray::GetUpperBound`.

*$BASE_CLASS*<br/>
Základní třída typované ukazatele pole třídy; musí být třída pole ( [cobarray –](../../mfc/reference/cobarray-class.md) nebo [cptrarray –](../../mfc/reference/cptrarray-class.md)).

*pNewArray*<br/>
Další pole obsahující prvky, které mají být přidány do tohoto pole.

### <a name="remarks"></a>Poznámky

Podrobné poznámky, naleznete v tématu [CObArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat).

##  <a name="operator_at"></a>  [] Č. CTypedPtrArray::operator

Tyto vložené operátory volání `BASE_CLASS` **:: operator []**.

```
TYPE& operator[ ](int_ptr nindex);
TYPE operator[ ](int_ptr nindex) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvků uložených v poli.

*nIndex*<br/>
Celočíselný index, který je větší než nebo rovna 0 a menší nebo rovna hodnotě vrácené `BASE_CLASS` **:: GetUpperBound**.

### <a name="remarks"></a>Poznámky

Volá se, první operátor pro pole, která nejsou **const**, lze použít na pravé straně (r) nebo (l hodnota) levé straně příkazu přiřazení. Druhá s názvem vyvolána **const** pole, lze použít pouze na pravé straně.

Ladicí verze knihovny vyhodnotí, pokud hodnota argumentu subscript (buď v levé nebo pravé straně příkazu přiřazení) je mimo rozsah.

##  <a name="setat"></a>  CTypedPtrArray::SetAt

Tato členská funkce volá `BASE_CLASS` **:: SetAt**.

```
void SetAt(
    INT_PTR nIndex,
    TYPE ptr);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Celočíselný index, který je větší než nebo rovna 0 a menší nebo rovna hodnotě vrácené [CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound).

*TYP*<br/>
Typ prvků uložených v poli základní třídy.

*ptr*<br/>
Ukazatel na prvek, který má být vložen do pole na nIndex. Je povolena hodnota NULL.

### <a name="remarks"></a>Poznámky

Podrobné poznámky, naleznete v tématu [CObArray::SetAt](../../mfc/reference/cobarray-class.md#setat).

##  <a name="setatgrow"></a>  CTypedPtrArray::SetAtGrow

Tato členská funkce volá `BASE_CLASS` **:: SetAtGrow**.

```
void SetAtGrow(
    INT_PTR nIndex,
    TYPE newElement);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Celočíselný index, který je větší než nebo rovna 0.

*TYP*<br/>
Typ prvků uložených v poli základní třídy.

*newElement*<br/>
Ukazatel objektu, který chcete přidat do tohoto pole. A **NULL** povolená hodnota.

### <a name="remarks"></a>Poznámky

Podrobné poznámky, naleznete v tématu [CObArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow).

## <a name="see-also"></a>Viz také

[Ukázky knihovny MFC shromažďování](../../visual-cpp-samples.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CPtrArray – třída](../../mfc/reference/cptrarray-class.md)<br/>
[CObArray – třída](../../mfc/reference/cobarray-class.md)
