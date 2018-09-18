---
title: Catlfilemapping – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlFileMapping
- atlfile/ATL::CAtlFileMapping
dev_langs:
- C++
helpviewer_keywords:
- CAtlFileMapping class
ms.assetid: 899fc058-e05e-48b5-aca9-340403bb9e26
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ccbf3221bddf39c8069e20636c2f2a1deb597866
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116461"
---
# <a name="catlfilemapping-class"></a>Catlfilemapping – třída

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

## <a name="see-also"></a>Viz také

[CAtlFileMappingBase – třída](../../atl/reference/catlfilemappingbase-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
