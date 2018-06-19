---
title: '&lt;forward_list –&gt; operátory | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- forward_list/std::operator!=
- forward_list/std::operator==
- forward_list/std::operatoroperator&gt;
- forward_list/std::operatoroperator&gt=;
- forward_list/std::operatoroperator&lt;
- forward_list/std::operatoroperator&lt;=
dev_langs:
- C++
ms.assetid: 57492e09-3836-4dbc-9ae5-78ecf506c190
helpviewer_keywords:
- std::operator!= (forward_list)
- std::operator== (forward_list)
- std::operatoroperator&gt; (forward_list)
- std::operatoroperator&gt=; (forward_list)
- std::operatoroperator&lt; (forward_list)
- std::operatoroperator&lt;= (forward_list)
ms.openlocfilehash: 7966d428dd200f0cbb280c679c4072e1ad75757a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33846747"
---
# <a name="ltforwardlistgt-operators"></a>&lt;forward_list –&gt; operátory

||||
|-|-|-|
|[operator!=](#op_neq)|[Operátor&gt;](#op_gt)|[Operátor&gt;=](#op_gt_eq)|
|[Operátor&lt;](#op_lt)|[Operátor&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|

## <a name="op_eq_eq"></a>  Operator ==

Testy, pokud se objekt dopředného seznamu na levé straně operátoru rovná objektu dopředného seznamu na pravé straně.

```cpp
bool operator==(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`left`|Objekt typu `forward_list`.|
|`right`|Objekt typu `forward_list`.|

### <a name="remarks"></a>Poznámky

Tato funkce šablony přetížení `operator==` k porovnání dvou objektů třídy šablony `forward_list`. Funkce vrátí hodnotu `distance(left.begin(), end()) == distance(right.begin(),right.end()) && equal(left. begin(),left. end(),right.begin())`.

## <a name="op_neq"></a>  Operator! =

Testy, pokud není objekt dopředného seznamu na levé straně operátoru rovná objektu dopředného seznamu na pravé straně.

```cpp
bool operator!=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`left`|Objekt typu `forward_list`.|
|`right`|Objekt typu `forward_list`.|

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud seznamy není stejný; **false** Pokud seznamy jsou stejné.

### <a name="remarks"></a>Poznámky

Šablona funkce vrátí hodnotu `!(left == right)`.

## <a name="op_lt"></a>  Operátor&lt;

Testy, pokud objekt dopředného seznamu na levé straně operátoru je menší než dopředného list objekt na pravé straně.

```cpp
bool operator<(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`left`|Objekt typu `forward_list`.|
|`right`|Objekt typu `forward_list`.|

### <a name="return-value"></a>Návratová hodnota

`true` Pokud v seznamu na levé straně operátor je menší než, ale není rovno v seznamu na pravé straně operátoru; v opačném případě `false`.

### <a name="remarks"></a>Poznámky

Tato funkce šablony přetížení `operator<` k porovnání dvou objektů třídy šablony `forward_list`. Funkce vrátí hodnotu `lexicographical_compare(lhs. begin(), lhs. end(), rhs.begin(), rhs.end())`.

## <a name="op_lt_eq"></a>  Operátor&lt;=

Pokud seznamu dopředného objekt na levé straně operátoru testů je menší než nebo rovna hodnotě dopředného list objekt na pravé straně.

```cpp
bool operator<=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`left`|Objekt typu `forward_list`.|
|`right`|Objekt typu `forward_list`.|

### <a name="return-value"></a>Návratová hodnota

`true` Pokud v seznamu na levé straně operátor je menší než nebo rovna v seznamu na pravé straně operátoru; v opačném případě `false`.

### <a name="remarks"></a>Poznámky

Šablona funkce vrátí hodnotu `!(right < left)`.

## <a name="op_gt"></a>  Operátor&gt;

Testy, pokud objekt dopředného seznamu na levé straně operátoru je větší než dopředného list objekt na pravé straně.

```cpp
bool operator>(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`left`|Objekt typu `forward_list`.|
|`right`|Objekt typu `forward_list`.|

### <a name="return-value"></a>Návratová hodnota

`true` Pokud v seznamu na levé straně operátor je větší než v seznamu na pravé straně operátoru; v opačném případě `false`.

### <a name="remarks"></a>Poznámky

Šablona funkce vrátí hodnotu `right < left`.

## <a name="op_gt_eq"></a>  Operátor&gt;=

Testy, pokud objekt dopředného seznamu na levé straně operátoru je větší než nebo rovna hodnotě dopředného list objekt na pravé straně.

```cpp
bool operator>=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`left`|Objekt typu `forward_list`.|
|`right`|Objekt typu `forward_list`.|

### <a name="return-value"></a>Návratová hodnota

`true` Pokud dopředného seznamu na levé straně operátoru je větší než nebo rovno dopředného seznamu na pravé straně operátoru; v opačném případě `false`.

### <a name="remarks"></a>Poznámky

Funkce šablony vrátí `!(left < right)`.

## <a name="see-also"></a>Viz také

[<forward_list>](../standard-library/forward-list.md)<br/>
