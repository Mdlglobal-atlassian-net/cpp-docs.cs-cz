---
title: CAtlFileMapping – třída
ms.date: 11/04/2016
f1_keywords:
- CAtlFileMapping
- atlfile/ATL::CAtlFileMapping
helpviewer_keywords:
- CAtlFileMapping class
ms.assetid: 899fc058-e05e-48b5-aca9-340403bb9e26
ms.openlocfilehash: 7516349e4ec54d8cb90fa6ff23b0ded954aa043b
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168121"
---
# <a name="catlfilemapping-class"></a>CAtlFileMapping – třída

Tato třída reprezentuje soubor mapované paměti a přidává do metod [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)operátor přetypování.

> [!IMPORTANT]
> Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T = char>
class CAtlFileMapping : public CAtlFileMappingBase
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ dat použitý pro operátor přetypování.

## <a name="members"></a>Členové

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CAtlFileMapping:: operator T *](#operator_t_star)|Umožňuje implicitní převod `CAtlFileMapping` objektů na `T*`.|

## <a name="remarks"></a>Poznámky

Tato třída přidá jeden operátor přetypování pro povolení implicitního převodu `CAtlFileMapping` objektů na `T*`. Ostatní členové jsou dodány základní třídou [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)

`CAtlFileMapping`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlfile. h

## <a name="catlfilemappingoperator-t"></a><a name="operator_t_star"></a>CAtlFileMapping:: operator T *

Umožňuje implicitní převod `CAtlFileMapping` objektů na `T*`.

```cpp
operator T*() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí `T*` ukazatel na začátek souboru mapované paměti.

### <a name="remarks"></a>Poznámky

Volá [CAtlFileMappingBase:: GetData](../../atl/reference/catlfilemappingbase-class.md#getdata) a přeloží vrácený ukazatel jako, `T*` kde *T* je typ použitý jako parametr šablony této třídy.

## <a name="see-also"></a>Viz také

[CAtlFileMappingBase – třída](../../atl/reference/catlfilemappingbase-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
