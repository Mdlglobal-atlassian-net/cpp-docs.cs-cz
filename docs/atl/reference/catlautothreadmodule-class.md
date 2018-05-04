---
title: Třída CAtlAutoThreadModule | Microsoft Docs
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
ms.openlocfilehash: 9c89d142254909591ebd01bfa859be5488cbfaf6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="catlautothreadmodule-class"></a>CAtlAutoThreadModule – třída
Tato třída implementuje server COM ve fondu vláken, apartment model.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CAtlAutoThreadModule : public CAtlAutoThreadModuleT<CAtlAutoThreadModule>
```  
  
## <a name="remarks"></a>Poznámky  
 `CAtlAutoThreadModule` odvozená z [CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md) a implementuje server COM ve fondu vláken, apartment model. `CAtlAutoThreadModule` používá [CComApartment](../../atl/reference/ccomapartment-class.md) ke správě izolovaný prostor pro každé vlákno v modulu.  
  
 Je nutné použít [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) makra v definici třídy objektu k určení [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) jako objekt pro vytváření tříd. Měli byste pak přidat jednu instanci třídy odvozené od `CAtlAutoThreadModuleT` například `CAtlAutoThreadModule`. Příklad:  
  
 `CAtlAutoThreadModule _AtlAutoModule; // name is immaterial.`  
  
> [!NOTE]
>  Nahradí tato třída zastaralá [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md) třídy.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IAtlAutoThreadModule`  
  
 [CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)  
  
 `CAtlAutoThreadModule`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
  
## <a name="see-also"></a>Viz také  
 [CAtlAutoThreadModuleT – třída](../../atl/reference/catlautothreadmodulet-class.md)   
 [IAtlAutoThreadModule – třída](../../atl/reference/iatlautothreadmodule-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)   
 [Třídy modulů](../../atl/atl-module-classes.md)
