---
title: scoped_d3d_access_lock – třída
ms.date: 11/04/2016
f1_keywords:
- scoped_d3d_access_lock
- AMPRT/scoped_d3d_access_lock
- AMPRT/concurrency::direct3d::scoped_d3d_access_lock::scoped_d3d_access_lock
ms.assetid: 0ad333e6-9839-4736-a722-16d95d70c4b1
ms.openlocfilehash: b5a2d9dab9cba7b19fa0d0b1627f653f2c7fdc57
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126393"
---
# <a name="scoped_d3d_access_lock-class"></a>scoped_d3d_access_lock – třída

Obálka RAII pro zámek přístupu D3D u objektu accelerator_view.

## <a name="syntax"></a>Syntaxe

```cpp
class scoped_d3d_access_lock;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[scoped_d3d_access_lock – konstruktor](#ctor)|Přetíženo. Vytvoří objekt `scoped_d3d_access_lock`. Zámek se uvolní, když se tento objekt dostane mimo rozsah.|
|[~ scoped_d3d_access_lock destruktor](#dtor)|Uvolní zámek přístupu D3D u přidruženého objektu `accelerator_view`.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operátor =](#operator_eq)|Převezme vlastnictví zámku z jiné `scoped_d3d_access_lock`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`scoped_d3d_access_lock`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amprt. h

**Obor názvů:** concurrency::d irect3d

## <a name="ctor"></a>scoped_d3d_access_lock

Vytvoří objekt `scoped_d3d_access_lock`. Zámek se uvolní, když se tento objekt dostane mimo rozsah.

```cpp
explicit scoped_d3d_access_lock(// [1] constructor
    accelerator_view& _Av);

explicit scoped_d3d_access_lock(// [2] constructor
    accelerator_view& _Av,
    adopt_d3d_access_lock_t _T);

scoped_d3d_access_lock(// [3] move constructor
    scoped_d3d_access_lock&& _Other);
```

### <a name="parameters"></a>Parametry

*_Av*<br/>
`accelerator_view`, který má zámek přijmout.

*_T*<br/>
Objekt `adopt_d3d_access_lock_t`

*_Other*<br/>
Objekt `scoped_d3d_access_lock`, ze kterého se má přesunout existující zámek.

## <a name="construction"></a>Stavbě

[1] konstruktor získá zámek přístupu D3D na daném objektu [accelerator_view](accelerator-view-class.md) . Stavební bloky, dokud se zámek nezíská.

[2] konstruktor přijímá zámek přístupu D3D z daného objektu [accelerator_view](accelerator-view-class.md) .

Konstruktor Move [3] přebírá existující zámek přístupu D3D z jiného objektu `scoped_d3d_access_lock`. Konstrukce neblokuje.

## <a name="dtor"></a>~ scoped_d3d_access_lock

Uvolní zámek přístupu D3D u přidruženého objektu `accelerator_view`.

```cpp
~scoped_d3d_access_lock();
```

## <a name="operator_eq"></a>operátor =

Převezme vlastnictví zámku přístupu D3D z jiného objektu `scoped_d3d_access_lock` a uvolní předchozí zámek.

```cpp
scoped_d3d_access_lock& operator= (scoped_d3d_access_lock&& _Other);
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
Accelerator_view, ze kterého se má přesunout zámek přístupu D3D

### <a name="return-value"></a>Návratová hodnota

Odkaz na tento `scoped_accelerator_view_lock`.

## <a name="see-also"></a>Viz také

[Concurrency::direct3d – obor názvů](concurrency-direct3d-namespace.md)
