---
title: Idochostuihandlerdispatch – rozhraní | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IDocHostUIHandlerDispatch
- atlbase/ATL::IDocHostUIHandlerDispatch
dev_langs:
- C++
helpviewer_keywords:
- IDocHostUIHandlerDispatch interface
ms.assetid: 6963a301-601a-4ac3-8bef-f7b252ea2fc6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 57dbb9e5ed73ce8ed85d7c90d05705cefdd4ed9b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43194764"
---
# <a name="idochostuihandlerdispatch-interface"></a>Idochostuihandlerdispatch – rozhraní
Rozhraní pro parsování Microsoft HTML a vykreslovací modul.  
  
> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
interface IDocHostUIHandlerDispatch : IDispatch
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
> [!NOTE]
>  Odkazy v následující tabulce jsou na referenční témata INet SDK pro členy [IDocUIHostHandler](https://msdn.microsoft.com/library/aa753260.aspx) rozhraní. `IDocHostUIHandlerDispatch` má stejné funkce jako `IDocUIHostHandler`, s rozdílem je, který `IDocHostUIHandlerDispatch` vzhledem k tomu je dispinterface `IDocUIHostHandler` je vlastní rozhraní.  
  
|||  
|-|-|  
|[EnableModeless](https://msdn.microsoft.com/library/aa753253.aspx)|Volání z implementace MSHTML [IOleInPlaceActiveObject::EnableModeless](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless). Také volá se, když MSHTML zobrazí modální uživatelské rozhraní.|  
|[FilterDataObject](https://msdn.microsoft.com/library/aa753254.aspx)|Volá se na hostiteli pomocí MSHTML aplikace umožňující hostitele k nahrazení MSHTML na datový objekt.|  
|[GetDropTarget](https://msdn.microsoft.com/library/aa753255.aspx)|Voláno rozhraním MSHTML aplikace, když se používá se jako cíl přetažení k hostiteli umožní zadat alternativní [IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget).|  
|[GetExternal](https://msdn.microsoft.com/library/aa753256.aspx)|Je voláno MSHTML získat rozhraní IDispatch hostitele.|  
|[GetHostInfo](https://msdn.microsoft.com/library/aa753257.aspx)|Načte možnosti uživatelského rozhraní MSHTML hostitele.|  
|[GetOptionKeyPath](https://msdn.microsoft.com/library/aa753258.aspx)|Vrátí klíč registru, ve které ukládá MSHTML předvolby uživatele.|  
|[HideUI](https://msdn.microsoft.com/library/aa753259.aspx)|Volá se, když MSHTML odebere jeho nabídek a panelů nástrojů.|  
|[OnDocWindowActivate](https://msdn.microsoft.com/library/aa753261.aspx)|Volání z implementace MSHTML [IOleInPlaceActiveObject::OnDocWindowActivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate).|  
|[OnFrameWindowActivate](https://msdn.microsoft.com/library/aa753262.aspx)|Volání z implementace MSHTML [IOleInPlaceActiveObject::OnFrameWindowActivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate).|  
|[ResizeBorder](https://msdn.microsoft.com/library/aa753263.aspx)|Volání z implementace MSHTML [IOleInPlaceActiveObject::ResizeBorder](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder).|  
|[ShowContextMenu](https://msdn.microsoft.com/library/aa753264.aspx)|Volá se z MSHTML zobrazení místní nabídky.|  
|[ShowUI](https://msdn.microsoft.com/library/aa753265.aspx)|Umožňuje hostiteli nahradit MSHTML nabídek a panelů nástrojů.|  
|[TranslateAccelerator](https://msdn.microsoft.com/library/aa753266.aspx)|Volané MSHTML při [IOleInPlaceActiveObject::TranslateAccelerator](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator) nebo [IOleControlSite::TranslateAccelerator](/windows/desktop/api/ocidl/nf-ocidl-iolecontrolsite-translateaccelerator) je volána.|  
|[TranslateUrl](https://msdn.microsoft.com/library/aa753267.aspx)|Je voláno MSHTML aplikace umožňující hostitele příležitost změnit adresu URL, který se má načíst.|  
|[UpdateUI](https://msdn.microsoft.com/library/aa753268.aspx)|Upozorňuje hostitele, stav příkazu se změnila.|  
  
## <a name="remarks"></a>Poznámky  
 Hostitele můžete nahradit nabídky, panely nástrojů a kontextové nabídky, které používá Microsoft HTML analýzou a vykreslovací modul (MSHTML) implementace tohoto rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 Definice toto rozhraní není k dispozici jako IDL nebo C++, jak je znázorněno níže.  
  
|Typ definice|Soubor|  
|---------------------|----------|  
|IDL|ATLIFace.idl|  
|C++|ATLIFace.h (také součástí ATLBase.h)|  
  
## <a name="see-also"></a>Viz také  
 [IDocUIHostHandler](https://msdn.microsoft.com/library/aa753260.aspx)









