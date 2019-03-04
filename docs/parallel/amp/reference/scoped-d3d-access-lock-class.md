---
title: scoped_d3d_access_lock – třída
ms.date: 11/04/2016
f1_keywords:
- scoped_d3d_access_lock
- AMPRT/scoped_d3d_access_lock
- AMPRT/concurrency::direct3d::scoped_d3d_access_lock::scoped_d3d_access_lock
ms.assetid: 0ad333e6-9839-4736-a722-16d95d70c4b1
ms.openlocfilehash: e36c3c2cfa9d1b617e377a7e340f98875457bdf1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57272461"
---
# <a name="scopedd3daccesslock-class"></a>scoped_d3d_access_lock – třída

Obálka RAII pro uzamčení přístupu D3D v objektu accelerator_view.

### <a name="syntax"></a>Syntaxe

```
class scoped_d3d_access_lock;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[scoped_d3d_access_lock Constructor](#ctor)|Přetíženo. Vytvoří `scoped_d3d_access_lock` objektu. Zámek je uvolněn, když tento objekt dostane mimo rozsah.|
|[~scoped_d3d_access_lock Destructor](#dtor)|Uvolní zámek přístupu D3D přidruženého `accelerator_view` objektu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operátor =](#operator_eq)|Převezme vlastnictví zámku z jiného `scoped_d3d_access_lock`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`scoped_d3d_access_lock`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amprt.h

**Namespace:** concurrency::direct3d

##  <a name="ctor"></a> scoped_d3d_access_lock

Vytvoří `scoped_d3d_access_lock` objektu. Zámek je uvolněn, když tento objekt dostane mimo rozsah.

```
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
`accelerator_view` Pro zámek přijmout.

*_T*<br/>
`adopt_d3d_access_lock_t` Objektu.

*Ji_né*<br/>
`scoped_d3d_access_lock` Objektu, ze kterého se má přesunout existující uzamčení.

## <a name="construction"></a>Konstrukce

[1] konstruktoru získá zámek přístupu D3D na daný [accelerator_view](accelerator-view-class.md) objektu. Vytvoření je blokováno, dokud je požadován zámek.

[2] konstruktor přijme zámek přístupu D3D z daný [accelerator_view](accelerator-view-class.md) objektu.

[3] přesunout konstruktor přebírá stávající uzamčení přístupu D3D z jiného `scoped_d3d_access_lock` objektu. Konstrukce neblokuje.

##  <a name="dtor"></a> ~scoped_d3d_access_lock

Uvolní zámek přístupu D3D přidruženého `accelerator_view` objektu.

```
~scoped_d3d_access_lock();
```

## <a name="operator_eq"></a> operátor =

Převezme vlastnictví zámku přístupu D3D z jiného `scoped_d3d_access_lock` objekt uvolní uzamčení předchozího.

```
scoped_d3d_access_lock& operator= (scoped_d3d_access_lock&& _Other);
```

### <a name="parameters"></a>Parametry

*Ji_né*<br/>
Accelerator_view, ze kterého chcete přemístit zámek přístupu D3D.

### <a name="return-value"></a>Návratová hodnota

Odkaz na tento `scoped_accelerator_view_lock`.

## <a name="see-also"></a>Viz také:

[Concurrency::direct3d – obor názvů](concurrency-direct3d-namespace.md)
