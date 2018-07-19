---
title: Iquickactivateimpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IQuickActivateImpl
- ATLCTL/ATL::IQuickActivateImpl
- ATLCTL/ATL::IQuickActivateImpl::GetContentExtent
- ATLCTL/ATL::IQuickActivateImpl::QuickActivate
- ATLCTL/ATL::IQuickActivateImpl::SetContentExtent
dev_langs:
- C++
helpviewer_keywords:
- activating ATL controls
- controls [ATL], activating
- IQuickActivateImpl class
- IQuickActivate ATL implementation
ms.assetid: aa80c056-1041-494e-b21d-2acca7dc27ea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9131a1cc1f8d0c66f2eb3616f4903db74ea4bdf0
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37881370"
---
# <a name="iquickactivateimpl-class"></a>Iquickactivateimpl – třída
Tato třída kombinuje Inicializace řízení kontejnerů do jednoho volání.  
  
> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>  
class ATL_NO_VTABLE IQuickActivateImpl : public IQuickActivate
```  
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Vaše třída odvozena od `IQuickActivateImpl`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IQuickActivateImpl::GetContentExtent](#getcontentextent)|Načte aktuální velikost zobrazení pro ovládací prvek spuštěné.|  
|[IQuickActivateImpl::QuickActivate](#quickactivate)|Provádí rychlé inicializace načítání ovládacích prvků.|  
|[IQuickActivateImpl::SetContentExtent](#setcontentextent)|Informuje o kontrolu nad kolik prostor pro zobrazení je přiřazeno kontejneru.|  
  
## <a name="remarks"></a>Poznámky  
 [IQuickActivate](http://msdn.microsoft.com/library/windows/desktop/ms690146) rozhraní pomáhá kontejnery vyhnuli prodlevám při načítání ovládacích prvků kombinací inicializace v jednom volání. `QuickActivate` Metoda umožňuje předat ukazatel na kontejneru [QACONTAINER](http://msdn.microsoft.com/library/windows/desktop/ms688630) potřebuje struktura, která obsahuje odkazy na všechna rozhraní ovládacího prvku. Při návratu, ovládací prvek předává zpět ukazatel [QACONTROL](http://msdn.microsoft.com/library/windows/desktop/ms693721) struktura, která obsahuje odkazy na vlastní rozhraní, které jsou používány obalu. Třída `IQuickActivateImpl` poskytuje výchozí implementaci třídy `IQuickActivate` a implementuje `IUnknown` posíláním informací o k výpisu paměti zařízení v ladění sestavení.  
  
 **Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IQuickActivate`  
  
 `IQuickActivateImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlctl.h  
  
##  <a name="getcontentextent"></a>  IQuickActivateImpl::GetContentExtent  
 Načte aktuální velikost zobrazení pro ovládací prvek spuštěné.  
  
```
STDMETHOD(GetContentExtent)(LPSIZEL pSize);
```  
  
### <a name="remarks"></a>Poznámky  
 Velikost je pro úplné vykreslování ovládacího prvku a je zadán v jednotkách HIMETRIC.  
  
 Zobrazit [IQuickActivate::GetContentExtent](http://msdn.microsoft.com/library/windows/desktop/ms693792) ve Windows SDK.  
  
##  <a name="quickactivate"></a>  IQuickActivateImpl::QuickActivate  
 Provádí rychlé inicializace načítání ovládacích prvků.  
  
```
STDMETHOD(QuickActivate)(
    QACONTAINER* pQACont,
    QACONTROL* pQACtrl);
```  
  
### <a name="remarks"></a>Poznámky  
 Struktura obsahuje odkazy na rozhraní, které jsou potřeba pro ovládací prvek a hodnoty vlastnosti některé prostředí. Po návratu, ovládací prvek předává ukazatel [QACONTROL](http://msdn.microsoft.com/library/windows/desktop/ms693721) strukturu, která obsahuje odkazy na vlastní rozhraní, které vyžaduje kontejneru a doplňkové informace o stavu.  
  
 Zobrazit [IQuickActivate::QuickActivate](http://msdn.microsoft.com/library/windows/desktop/ms682421) ve Windows SDK.  
  
##  <a name="setcontentextent"></a>  IQuickActivateImpl::SetContentExtent  
 Informuje o kontrolu nad kolik prostor pro zobrazení je přiřazeno kontejneru.  
  
```
STDMETHOD(SetContentExtent)(LPSIZEL pSize);
```  
  
### <a name="remarks"></a>Poznámky  
 Velikost se zadává v jednotkách HIMETRIC.  
  
 Zobrazit [IQuickActivate::SetContentExtent](http://msdn.microsoft.com/library/windows/desktop/ms678806) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Ccomcontrol – třída](../../atl/reference/ccomcontrol-class.md)   
 [Přehled tříd](../../atl/atl-class-overview.md)
