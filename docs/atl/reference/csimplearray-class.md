---
title: Třída CSimpleArray
ms.date: 11/04/2016
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
helpviewer_keywords:
- CSimpleArray class
ms.assetid: ee0c9f39-b61c-4c18-bc43-4eada21dca3a
ms.openlocfilehash: d3386687757412d09e4df29e84f691f1615c472a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746469"
---
# <a name="csimplearray-class"></a>Třída CSimpleArray

Tato třída poskytuje metody pro správu jednoduché pole.

## <a name="syntax"></a>Syntaxe

```
template <class T, class TEqual = CSimpleArrayEqualHelper<T>>
class CSimpleArray
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ dat, která mají být ukládat v poli.

*TEqual (TEqual)*<br/>
Objekt vlastnosti, definování testu rovnosti pro prvky typu *T*.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CSimpleArray::CSimpleArray](#csimplearray)|Konstruktor pro jednoduché pole.|
|[CSimpleArray::~CSimpleArray](#dtor)|Destruktor pro jednoduché pole.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CSimpleArray::Přidat](#add)|Přidá nový prvek do pole.|
|[CSimpleArray::Najít](#find)|Najde prvek v poli.|
|[CSimpleArray::GetData](#getdata)|Vrátí ukazatel na data uložená v poli.|
|[CSimpleArray::GetSize](#getsize)|Vrátí počet prvků uložených v poli.|
|[CSimpleArray::Odebrat](#remove)|Odebere daný prvek z pole.|
|[CSimpleArray::RemoveAll](#removeall)|Odebere všechny prvky z pole.|
|[CSimpleArray::Removeat](#removeat)|Odebere zadaný prvek z pole.|
|[CSimpleArray::SetatIndex](#setatindex)|Nastaví zadaný prvek v poli.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CSimpleArray::operátor\[\]](#operator_at)|Načte prvek z pole.|
|[CSimpleArray::operátor =](#operator_eq)|Operátor přiřazení.|

## <a name="remarks"></a>Poznámky

`CSimpleArray`poskytuje metody pro vytváření a správu jednoduchého pole libovolného typu `T`.

Parametr `TEqual` poskytuje prostředky definování funkce rovnosti pro dva `T`prvky typu . Vytvořením třídy podobné [CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md), je možné změnit chování testu rovnosti pro dané pole. Například při práci s pole ukazatelů, může být užitečné definovat rovnost jako v závislosti na hodnotách ukazatele odkaz. Výchozí implementace využívá **operator=()**.

Oba `CSimpleArray` a [CSimpleMap](../../atl/reference/csimplemap-class.md) jsou určeny pro malý počet prvků. [CAtlArray](../../atl/reference/catlarray-class.md) a [CAtlMap](../../atl/reference/catlmap-class.md) by měly být použity, pokud pole obsahuje velký počet prvků.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsimpcoll.h

## <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#86](../../atl/codesnippet/cpp/csimplearray-class_1.cpp)]

## <a name="csimplearrayadd"></a><a name="add"></a>CSimpleArray::Přidat

Přidá nový prvek do pole.

```
BOOL Add(const T& t);
```

### <a name="parameters"></a>Parametry

*t*<br/>
Prvek, který chcete přidat do pole.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je prvek úspěšně přidán do pole, JINAK NEPRAVDA.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#87](../../atl/codesnippet/cpp/csimplearray-class_2.cpp)]

## <a name="csimplearraycsimplearray"></a><a name="csimplearray"></a>CSimpleArray::CSimpleArray

Konstruktor pro objekt pole.

```
CSimpleArray(const CSimpleArray<T, TEqual>& src);
CSimpleArray();
```

### <a name="parameters"></a>Parametry

*src*<br/>
Existující objekt `CSimpleArray`.

### <a name="remarks"></a>Poznámky

Inicializuje datové členy a vytvoří `CSimpleArray` nový prázdný objekt nebo `CSimpleArray` kopii existujícího objektu.

## <a name="csimplearraycsimplearray"></a><a name="dtor"></a>CSimpleArray::~CSimpleArray

Destruktor.

```
~CSimpleArray();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené zdroje.

## <a name="csimplearrayfind"></a><a name="find"></a>CSimpleArray::Najít

Najde prvek v poli.

```
int Find(const T& t) const;
```

### <a name="parameters"></a>Parametry

*t*<br/>
Prvek, pro který chcete hledat.

### <a name="return-value"></a>Návratová hodnota

Vrátí index nalezeného prvku nebo -1, pokud není nalezen.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#88](../../atl/codesnippet/cpp/csimplearray-class_3.cpp)]

## <a name="csimplearraygetdata"></a><a name="getdata"></a>CSimpleArray::GetData

Vrátí ukazatel na data uložená v poli.

```
T* GetData() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na data v poli.

## <a name="csimplearraygetsize"></a><a name="getsize"></a>CSimpleArray::GetSize

Vrátí počet prvků uložených v poli.

```
int GetSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet prvků uložených v poli.

## <a name="csimplearrayoperator-"></a><a name="operator_at"></a>CSimpleArray::operátor\[\]

Načte prvek z pole.

```
T& operator[](int nindex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí prvek pole, na který odkazuje *nIndex*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#89](../../atl/codesnippet/cpp/csimplearray-class_4.cpp)]

## <a name="csimplearrayoperator-"></a><a name="operator_eq"></a>CSimpleArray::operátor =

Operátor přiřazení.

```
CSimpleArray<T, TEqual>
& operator=(
    const CSimpleArray<T, TEqual>& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
Pole ke kopírování.

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na `CSimpleArray` aktualizovaný objekt.

### <a name="remarks"></a>Poznámky

Zkopíruje všechny `CSimpleArray` prvky z objektu, na který *odkazuje src,* do aktuálního objektu pole a nahradí všechna existující data.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#90](../../atl/codesnippet/cpp/csimplearray-class_5.cpp)]

## <a name="csimplearrayremove"></a><a name="remove"></a>CSimpleArray::Odebrat

Odebere daný prvek z pole.

```
BOOL Remove(const T& t);
```

### <a name="parameters"></a>Parametry

*t*<br/>
Prvek odebrat z pole.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je prvek nalezen a odebrán, jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Při odebrání prvku jsou zbývající prvky v poli přečíslovány tak, aby vyplnily prázdné místo.

## <a name="csimplearrayremoveall"></a><a name="removeall"></a>CSimpleArray::RemoveAll

Odebere všechny prvky z pole.

```cpp
void RemoveAll();
```

### <a name="remarks"></a>Poznámky

Odebere všechny prvky aktuálně uložené v poli.

## <a name="csimplearrayremoveat"></a><a name="removeat"></a>CSimpleArray::Removeat

Odebere zadaný prvek z pole.

```
BOOL RemoveAtint nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index směřující na prvek odebrat.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud byl prvek odebrán, NEPRAVDA, pokud byl index neplatný.

### <a name="remarks"></a>Poznámky

Při odebrání prvku jsou zbývající prvky v poli přečíslovány tak, aby vyplnily prázdné místo.

## <a name="csimplearraysetatindex"></a><a name="setatindex"></a>CSimpleArray::SetatIndex

Nastavte zadaný prvek v poli.

```
BOOL SetAtIndex(
    int nIndex,
    const T& t);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index prvku změnit.

*t*<br/>
Hodnota přiřadit k zadanému prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je úspěšný, neplatí, pokud index nebyl platný.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
