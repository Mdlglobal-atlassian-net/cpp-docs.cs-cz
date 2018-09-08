---
title: Catlautothreadmodule – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlAutoThreadModule
- atlbase/ATL::CAtlAutoThreadModule
dev_langs:
- C++
helpviewer_keywords:
- CAtlAutoThreadModule class
ms.assetid: 3be834aa-55ef-403e-94ae-41979691b15f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4b534190a4e7243f5192e6d703b056d8bcb327ca
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44110640"
---
# <a name="catlautothreadmodule-class"></a>Catlautothreadmodule – třída

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

[Catlautothreadmodulet –](../../atl/reference/catlautothreadmodulet-class.md)

`CAtlAutoThreadModule`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="see-also"></a>Viz také

[Catlautothreadmodulet – třída](../../atl/reference/catlautothreadmodulet-class.md)   
[Iatlautothreadmodule – třída](../../atl/reference/iatlautothreadmodule-class.md)   
[Přehled tříd](../../atl/atl-class-overview.md)   
[Třídy modulů](../../atl/atl-module-classes.md)
