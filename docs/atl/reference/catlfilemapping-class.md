---
title: Třída CAtlFileMapping
ms.date: 11/04/2016
f1_keywords:
- CAtlFileMapping
- atlfile/ATL::CAtlFileMapping
helpviewer_keywords:
- CAtlFileMapping class
ms.assetid: 899fc058-e05e-48b5-aca9-340403bb9e26
ms.openlocfilehash: ca46ccdacf5ea24f1de26cdc75bf808c4ecfaa40
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318961"
---
# <a name="catlfilemapping-class"></a>Třída CAtlFileMapping

Tato třída představuje soubor mapovaný v paměti, přidání operátoru přetypování k metodám [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md).

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <typename T = char>
class CAtlFileMapping : public CAtlFileMappingBase
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ dat použitých pro operátor přetypovaného vysílání.

## <a name="members"></a>Členové

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CAtlFileMapping::operátor T*](#operator_t_star)|Umožňuje implicitní `CAtlFileMapping` převod `T*`objektů na .|

## <a name="remarks"></a>Poznámky

Tato třída přidá jeden operátor přetypádka, který umožňuje implicitní `CAtlFileMapping` převod objektů na `T*`. Ostatní členy jsou dodávány základní třídou [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)

`CAtlFileMapping`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlfile.h

## <a name="catlfilemappingoperator-t"></a><a name="operator_t_star"></a>CAtlFileMapping::operátor T*

Umožňuje implicitní `CAtlFileMapping` převod `T*`objektů na .

```
operator T*() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí `T*` ukazatel na začátek souboru mapované ho paměti.

### <a name="remarks"></a>Poznámky

Volá [CAtlFileMappingBase::GetData](../../atl/reference/catlfilemappingbase-class.md#getdata) a reinterpretuje `T*` vrácený ukazatel jako kde *T* je typ používaný jako parametr šablony této třídy.

## <a name="see-also"></a>Viz také

[Třída CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
