---
title: Csimplearray – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray::CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray::Add
- ATLSIMPCOLL/ATL::CSimpleArray::Find
- ATLSIMPCOLL/ATL::CSimpleArray::GetData
- ATLSIMPCOLL/ATL::CSimpleArray::GetSize
- ATLSIMPCOLL/ATL::CSimpleArray::Remove
- ATLSIMPCOLL/ATL::CSimpleArray::RemoveAll
- ATLSIMPCOLL/ATL::CSimpleArray::RemoveAt
- ATLSIMPCOLL/ATL::CSimpleArray::SetAtIndex
dev_langs:
- C++
helpviewer_keywords:
- CSimpleArray class
ms.assetid: ee0c9f39-b61c-4c18-bc43-4eada21dca3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fd3e6809a8204b9a2380e896e4e458512e79fa2b
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43766659"
---
# <a name="csimplearray-class"></a>Csimplearray – třída

Tato třída poskytuje metody pro správu jednoduché pole.

## <a name="syntax"></a>Syntaxe

```
template <class T, class TEqual = CSimpleArrayEqualHelper<T>>  
class CSimpleArray
```

#### <a name="parameters"></a>Parametry

*T*  
Typ dat pro uložení v poli.

*TEqual*  
Objekt vlastností definující test rovnosti pro prvky typu *T*.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CSimpleArray::CSimpleArray](#csimplearray)|Konstruktor pro jednoduché pole.|
|[Csimplearray –:: ~ csimplearray –](#dtor)|Destruktor pro jednoduché pole.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CSimpleArray::Add](#add)|Přidá nový prvek k poli.|
|[CSimpleArray::Find](#find)|Vyhledá prvek v poli.|
|[CSimpleArray::GetData](#getdata)|Vrací ukazatel na data uložená v poli.|
|[CSimpleArray::GetSize](#getsize)|Vrátí počet prvků uložených v poli.|
|[CSimpleArray::Remove](#remove)|Odebere daného prvku z pole.|
|[CSimpleArray::RemoveAll](#removeall)|Odebere všechny prvky z pole.|
|[CSimpleArray::RemoveAt](#removeat)|Odebere zadaný prvek z pole.|
|[CSimpleArray::SetAtIndex](#setatindex)|Nastaví zadaný prvek v poli.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CSimpleArray::operator\[\]](#operator_at)|Načte prvek z pole.|
|[CSimpleArray::operator =](#operator_eq)|Operátor přiřazení.|  

## <a name="remarks"></a>Poznámky

`CSimpleArray` poskytuje metody pro vytváření a správu jednoduché pole daného typu `T`.

Parametr `TEqual` poskytuje způsob definice funkce protokolem rovnosti dvou prvků typu `T`. Vytvořením třídy podobný [csimplearrayequalhelper –](../../atl/reference/csimplearrayequalhelper-class.md), je možné změnit chování test rovnosti pro jakékoli dané pole. Například při práci s pole ukazatelů, může být vhodné definovat rovnost jako v závislosti na hodnoty, které odkazují ukazatele. Výchozí implementace využívá **operator=()**.

Obě `CSimpleArray` a [csimplemap –](../../atl/reference/csimplemap-class.md) jsou určeny pro malý počet elementů. [Catlarray –](../../atl/reference/catlarray-class.md) a [catlmap –](../../atl/reference/catlmap-class.md) má být použit při pole obsahuje velký počet prvků.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsimpcoll.h

## <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#86](../../atl/codesnippet/cpp/csimplearray-class_1.cpp)]

##  <a name="add"></a>  CSimpleArray::Add

Přidá nový prvek k poli.

```
BOOL Add(const T& t);
```

### <a name="parameters"></a>Parametry

*t*  
Elementu, který chcete přidat do pole.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud prvek se úspěšně přidal do pole, FALSE v opačném případě.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#87](../../atl/codesnippet/cpp/csimplearray-class_2.cpp)]

##  <a name="csimplearray"></a>  CSimpleArray::CSimpleArray

Konstruktor objektu array.

```
CSimpleArray(const CSimpleArray<T, TEqual>& src);  
CSimpleArray();
```

### <a name="parameters"></a>Parametry

*src*  
Existující objekt `CSimpleArray`.

### <a name="remarks"></a>Poznámky

Inicializuje datové členy, vytváří se nová prázdná `CSimpleArray` objektu nebo kopii existující `CSimpleArray` objektu.

##  <a name="dtor"></a>  Csimplearray –:: ~ csimplearray –

Destruktor.

```
~CSimpleArray();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky.

##  <a name="find"></a>  CSimpleArray::Find

Vyhledá prvek v poli.

```
int Find(const T& t) const;
```

### <a name="parameters"></a>Parametry

*t*  
Element, který chcete vyhledat.

### <a name="return-value"></a>Návratová hodnota

Vrátí index elementu nalezena, nebo -1, pokud element nebyl nalezen.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#88](../../atl/codesnippet/cpp/csimplearray-class_3.cpp)]

##  <a name="getdata"></a>  CSimpleArray::GetData

Vrací ukazatel na data uložená v poli.

```
T* GetData() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrací ukazatel na data v poli.

##  <a name="getsize"></a>  CSimpleArray::GetSize

Vrátí počet prvků uložených v poli.

```
int GetSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet prvků uložených v poli.

##  <a name="operator_at"></a>  CSimpleArray::operator \[\]

Načte prvek z pole.

```
T& operator[](int nindex);
```

### <a name="parameters"></a>Parametry

*nIndex*  
Index prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí prvek pole odkazuje *nIndex*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#89](../../atl/codesnippet/cpp/csimplearray-class_4.cpp)]

##  <a name="operator_eq"></a>  CSimpleArray::operator =

Operátor přiřazení.

```
CSimpleArray<T, TEqual>
& operator=(
    const CSimpleArray<T, TEqual>& src);
```

### <a name="parameters"></a>Parametry

*src*  
Pole, které chcete kopírovat.

### <a name="return-value"></a>Návratová hodnota

Vrací ukazatel na aktualizovaný `CSimpleArray` objektu.

### <a name="remarks"></a>Poznámky

Zkopíruje všechny elementy z `CSimpleArray` objekt odkazovaný zadaným parametrem *src* do aktuálního pole objektu, nahraďte všechna existující data.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#90](../../atl/codesnippet/cpp/csimplearray-class_5.cpp)]

##  <a name="remove"></a>  CSimpleArray::Remove

Odebere daného prvku z pole.

```
BOOL Remove(const T& t);
```

### <a name="parameters"></a>Parametry

*t*  
Elementu, který chcete odebrat z pole.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud element je nalezen a odebrané, FALSE, jinak.

### <a name="remarks"></a>Poznámky

Odebraný prvek zbývající prvky v poli se označuje jako tak, aby vyplnil prázdný.

##  <a name="removeall"></a>  CSimpleArray::RemoveAll

Odebere všechny prvky z pole.

```
void RemoveAll();
```

### <a name="remarks"></a>Poznámky

Odebere všechny prvky, které jsou aktuálně uloženy v poli.

##  <a name="removeat"></a>  CSimpleArray::RemoveAt

Odebere zadaný prvek z pole.

```
BOOL RemoveAtint nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*  
Index, přejdete na elementu, který chcete odebrat.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud byl prvek odebrán, FALSE, pokud byl neplatný index.

### <a name="remarks"></a>Poznámky

Odebraný prvek zbývající prvky v poli se označuje jako tak, aby vyplnil prázdný.

##  <a name="setatindex"></a>  CSimpleArray::SetAtIndex

Nastavte Zadaný prvek v poli.

```
BOOL SetAtIndex(
    int nIndex,
    const T& t);
```

### <a name="parameters"></a>Parametry

*nIndex*  
Index prvku, který chcete změnit.

*t*  
Hodnota pro přiřazení k zadanému prvku.

### <a name="return-value"></a>Návratová hodnota

Vrací TRUE, pokud úspěšné, FALSE, pokud index nebyl platný.

## <a name="see-also"></a>Viz také

[Přehled tříd](../../atl/atl-class-overview.md)
