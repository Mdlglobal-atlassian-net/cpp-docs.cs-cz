---
title: "Třída IQuickActivateImpl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7c6f5bc1798bc8ec40fb6f6d9d22f48c06b19745
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="iquickactivateimpl-class"></a>IQuickActivateImpl – třída
Tato třída kombinuje Inicializace řízení kontejnerů do jednoho volání.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>  
class ATL_NO_VTABLE IQuickActivateImpl : public IQuickActivate
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od `IQuickActivateImpl`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IQuickActivateImpl::GetContentExtent](#getcontentextent)|Načte aktuální velikost zobrazení pro ovládací prvek spuštěné.|  
|[IQuickActivateImpl::QuickActivate](#quickactivate)|Provede rychlé inicializace ovládacích prvků načítá.|  
|[IQuickActivateImpl::SetContentExtent](#setcontentextent)|Informuje o tom, kolik místa zobrazení má přiřazen kontejneru ovládacího prvku.|  
  
## <a name="remarks"></a>Poznámky  
 [IQuickActivate](http://msdn.microsoft.com/library/windows/desktop/ms690146) rozhraní pomáhá kontejnery vyhnout zpoždění při načítání ovládacích prvků kombinací inicializace v jediném volání. `QuickActivate` Metoda umožňuje předat ukazatel na kontejneru [QACONTAINER](http://msdn.microsoft.com/library/windows/desktop/ms688630) musí struktura, která obsahuje ukazatele na všechna rozhraní ovládacího prvku. Při návratu, ovládací prvek předává zpět ukazatel [QACONTROL](http://msdn.microsoft.com/library/windows/desktop/ms693721) struktura, která obsahuje ukazatele na svůj vlastní rozhraní, které jsou používány kontejneru. Třída `IQuickActivateImpl` poskytuje výchozí implementaci třídy **IQuickActivate** a implementuje **IUnknown** posíláním informací o k výpisu zařízení ladění sestavení.  
  
 **Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytváření projektu knihovny ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IQuickActivate`  
  
 `IQuickActivateImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlctl.h  
  
##  <a name="getcontentextent"></a>IQuickActivateImpl::GetContentExtent  
 Načte aktuální velikost zobrazení pro ovládací prvek spuštěné.  
  
```
STDMETHOD(GetContentExtent)(LPSIZEL pSize);
```  
  
### <a name="remarks"></a>Poznámky  
 Velikost je pro úplné vykreslování ovládacího prvku a je uveden v HIMETRIC jednotky.  
  
 V tématu [IQuickActivate::GetContentExtent](http://msdn.microsoft.com/library/windows/desktop/ms693792) ve Windows SDK.  
  
##  <a name="quickactivate"></a>IQuickActivateImpl::QuickActivate  
 Provede rychlé inicializace ovládacích prvků načítá.  
  
```
STDMETHOD(QuickActivate)(
    QACONTAINER* pQACont,
    QACONTROL* pQACtrl);
```  
  
### <a name="remarks"></a>Poznámky  
 Struktura obsahuje odkazy na rozhraní vyžaduje ovládací prvek a hodnoty některých vedlejším vlastnostem. Po návratu, ovládací prvek předává ukazatel [QACONTROL](http://msdn.microsoft.com/library/windows/desktop/ms693721) struktura, která obsahuje odkazy na vlastní rozhraní, která vyžaduje kontejneru a informace o dalších stavu.  
  
 V tématu [IQuickActivate::QuickActivate](http://msdn.microsoft.com/library/windows/desktop/ms682421) ve Windows SDK.  
  
##  <a name="setcontentextent"></a>IQuickActivateImpl::SetContentExtent  
 Informuje o tom, kolik místa zobrazení má přiřazen kontejneru ovládacího prvku.  
  
```
STDMETHOD(SetContentExtent)(LPSIZEL pSize);
```  
  
### <a name="remarks"></a>Poznámky  
 Velikost se zadává v HIMETRIC jednotkách.  
  
 V tématu [IQuickActivate::SetContentExtent](http://msdn.microsoft.com/library/windows/desktop/ms678806) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [CComControl – třída](../../atl/reference/ccomcontrol-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
