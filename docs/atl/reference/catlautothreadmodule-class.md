---
title: CAtlAutoThreadModule – třída
ms.date: 11/04/2016
f1_keywords:
- CAtlAutoThreadModule
- atlbase/ATL::CAtlAutoThreadModule
helpviewer_keywords:
- CAtlAutoThreadModule class
ms.assetid: 3be834aa-55ef-403e-94ae-41979691b15f
ms.openlocfilehash: f4bd1071380bf3e31c69c593c5db81112fdf21de
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168303"
---
# <a name="catlautothreadmodule-class"></a>CAtlAutoThreadModule – třída

Tato třída implementuje Server COM ve fondu vláken s modelem Apartment.

> [!IMPORTANT]
> Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
class CAtlAutoThreadModule : public CAtlAutoThreadModuleT<CAtlAutoThreadModule>
```

## <a name="remarks"></a>Poznámky

`CAtlAutoThreadModule`je odvozen z [CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md) a implementuje Server modelu COM ve fondu vláken. `CAtlAutoThreadModule`používá [CComApartment](../../atl/reference/ccomapartment-class.md) ke správě izolovaného prostoru pro každé vlákno v modulu.

K určení [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) jako objektu pro vytváření tříd je nutné použít makro [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) v definici třídy vašeho objektu. Pak byste měli přidat jednu instanci třídy odvozené z `CAtlAutoThreadModuleT` , jako je. `CAtlAutoThreadModule` Příklad:

`CAtlAutoThreadModule _AtlAutoModule; // name is immaterial.`

> [!NOTE]
> Tato třída nahrazuje zastaralou třídu [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md) .

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IAtlAutoThreadModule`

[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)

`CAtlAutoThreadModule`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

## <a name="see-also"></a>Viz také

[CAtlAutoThreadModuleT – třída](../../atl/reference/catlautothreadmodulet-class.md)<br/>
[IAtlAutoThreadModule – třída](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Třídy modulů](../../atl/atl-module-classes.md)
