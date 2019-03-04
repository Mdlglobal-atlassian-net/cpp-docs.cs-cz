---
title: CAtlAutoThreadModule Class
ms.date: 11/04/2016
f1_keywords:
- CAtlAutoThreadModule
- atlbase/ATL::CAtlAutoThreadModule
helpviewer_keywords:
- CAtlAutoThreadModule class
ms.assetid: 3be834aa-55ef-403e-94ae-41979691b15f
ms.openlocfilehash: 1ec66bf77d8dd705cb2e1e93f70a885ab96420a6
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57280417"
---
# <a name="catlautothreadmodule-class"></a>CAtlAutoThreadModule Class

Tato třída implementuje ve fondu vláken, apartment model modelu COM serveru.

> [!IMPORTANT]
> Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CAtlAutoThreadModule : public CAtlAutoThreadModuleT<CAtlAutoThreadModule>
```

## <a name="remarks"></a>Poznámky

`CAtlAutoThreadModule` je odvozen od [catlautothreadmodulet –](../../atl/reference/catlautothreadmodulet-class.md) a implementuje ve fondu vláken, apartment model modelu COM serveru. `CAtlAutoThreadModule` používá [ccomapartment –](../../atl/reference/ccomapartment-class.md) ke správě typu apartment pro každé vlákno v modulu.

Je nutné použít [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) makra v definici třídy objektu k určení [ccomclassfactoryautothread –](../../atl/reference/ccomclassfactoryautothread-class.md) jako objekt pro vytváření tříd. Měli byste pak přidat jednu instanci třídy odvozené z `CAtlAutoThreadModuleT` například `CAtlAutoThreadModule`. Příklad:

`CAtlAutoThreadModule _AtlAutoModule; // name is immaterial.`

> [!NOTE]
> Nahradí tato třída zastaralá [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md) třídy.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IAtlAutoThreadModule`

[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)

`CAtlAutoThreadModule`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="see-also"></a>Viz také:

[CAtlAutoThreadModuleT – třída](../../atl/reference/catlautothreadmodulet-class.md)<br/>
[IAtlAutoThreadModule – třída](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)<br/>
[Třídy modulů](../../atl/atl-module-classes.md)
