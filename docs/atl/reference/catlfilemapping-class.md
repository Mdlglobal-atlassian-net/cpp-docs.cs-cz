---
title: CAtlFileMapping Class
ms.date: 11/04/2016
f1_keywords:
- CAtlFileMapping
- atlfile/ATL::CAtlFileMapping
helpviewer_keywords:
- CAtlFileMapping class
ms.assetid: 899fc058-e05e-48b5-aca9-340403bb9e26
ms.openlocfilehash: d0a47a6cf0cc86409ceb9ef40d6fc6d738c86aa9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62247168"
---
# <a name="catlfilemapping-class"></a>CAtlFileMapping Class

Tato třída reprezentuje soubor mapovaných do paměti, přidání operátor přetypování na metody [catlfilemappingbase –](../../atl/reference/catlfilemappingbase-class.md).

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <typename T = char>
class CAtlFileMapping : public CAtlFileMappingBase
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ dat použité pro operátor přetypování.

## <a name="members"></a>Členové

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CAtlFileMapping::operator T *](#operator_t_star)|Umožňuje implicitní převod `CAtlFileMapping` objektů `T*`.|

## <a name="remarks"></a>Poznámky

Tato třída přidává operátor přetypování jedné povolit implicitní převod `CAtlFileMapping` objektů `T*`. Ostatní členové jsou poskytována v základní třídě, [catlfilemappingbase –](../../atl/reference/catlfilemappingbase-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)

`CAtlFileMapping`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlfile.h

##  <a name="operator_t_star"></a>  CAtlFileMapping::operator T *

Umožňuje implicitní převod `CAtlFileMapping` objektů `T*`.

```
operator T*() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí `T*` ukazatel na začátek souboru mapovaných do paměti.

### <a name="remarks"></a>Poznámky

Volání [CAtlFileMappingBase::GetData](../../atl/reference/catlfilemappingbase-class.md#getdata) a opětovně interpretuje objekt vrácený ukazatel jako `T*` kde *T* je typ použitý jako parametr této třídy šablony.

## <a name="see-also"></a>Viz také:

[CAtlFileMappingBase – třída](../../atl/reference/catlfilemappingbase-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
