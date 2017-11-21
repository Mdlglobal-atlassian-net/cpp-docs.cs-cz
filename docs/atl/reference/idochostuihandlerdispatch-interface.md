---
title: "Rozhraní IDocHostUIHandlerDispatch | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IDocHostUIHandlerDispatch
- atlbase/ATL::IDocHostUIHandlerDispatch
dev_langs: C++
helpviewer_keywords: IDocHostUIHandlerDispatch interface
ms.assetid: 6963a301-601a-4ac3-8bef-f7b252ea2fc6
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: da373672c51dd47b67ee4457bd0d21f82a09c540
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="idochostuihandlerdispatch-interface"></a>IDocHostUIHandlerDispatch rozhraní
Rozhraní Microsoft HTML analýzy a modul vykreslování.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
interface IDocHostUIHandlerDispatch : IDispatch
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
> [!NOTE]
>  Odkazy v následující tabulce jsou na referenční témata INet SDK pro členy [IDocUIHostHandler](https://msdn.microsoft.com/library/aa753260.aspx) rozhraní. `IDocHostUIHandlerDispatch`má stejné funkce jako **IDocUIHostHandler**, s rozdílem je, `IDocHostUIHandlerDispatch` je odesílajícím rozhraním, zatímco **IDocUIHostHandler** je rozhraní, které je vlastní.  
  
|||  
|-|-|  
|[EnableModeless](https://msdn.microsoft.com/library/aa753253.aspx)|Volání z implementace MSHTML [IOleInPlaceActiveObject::EnableModeless](http://msdn.microsoft.com/library/windows/desktop/ms680115). Volá se také při MSHTML zobrazí modální uživatelského rozhraní.|  
|[FilterDataObject](https://msdn.microsoft.com/library/aa753254.aspx)|Volá se na hostiteli pomocí MSHTML hostiteli nahradit MSHTML na datový objekt.|  
|[GetDropTarget](https://msdn.microsoft.com/library/aa753255.aspx)|Voláno rozhraním MSHTML, když ho je používán jako cíle přetažení, aby na hostiteli a poté zadejte alternativu [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679).|  
|[GetExternal](https://msdn.microsoft.com/library/aa753256.aspx)|Voláno rozhraním MSHTML získat rozhraní IDispatch hostitele.|  
|[GetHostInfo](https://msdn.microsoft.com/library/aa753257.aspx)|Načte možnosti uživatelského rozhraní MSHTML hostitele.|  
|[GetOptionKeyPath](https://msdn.microsoft.com/library/aa753258.aspx)|Vrátí klíč registru, pod kterým MSHTML ukládá uživatelské předvolby.|  
|[HideUI](https://msdn.microsoft.com/library/aa753259.aspx)|Volá se při MSHTML odebere jeho nabídek a panelů nástrojů.|  
|[OnDocWindowActivate](https://msdn.microsoft.com/library/aa753261.aspx)|Volání z implementace MSHTML [IOleInPlaceActiveObject::OnDocWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms687281).|  
|[OnFrameWindowActivate](https://msdn.microsoft.com/library/aa753262.aspx)|Volání z implementace MSHTML [IOleInPlaceActiveObject::OnFrameWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms683969).|  
|[ResizeBorder](https://msdn.microsoft.com/library/aa753263.aspx)|Volání z implementace MSHTML [IOleInPlaceActiveObject::ResizeBorder](http://msdn.microsoft.com/library/windows/desktop/ms680053).|  
|[ShowContextMenu](https://msdn.microsoft.com/library/aa753264.aspx)|Volat z MSHTML zobrazíte z kontextové nabídky.|  
|[ShowUI](https://msdn.microsoft.com/library/aa753265.aspx)|Umožňuje na hostiteli a nahraďte MSHTML nabídek a panelů nástrojů.|  
|[TranslateAccelerator](https://msdn.microsoft.com/library/aa753266.aspx)|Voláno rozhraním MSHTML při [IOleInPlaceActiveObject::TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693360) nebo [IOleControlSite::TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693756) je volána.|  
|[TranslateUrl](https://msdn.microsoft.com/library/aa753267.aspx)|Voláno rozhraním MSHTML umožňující hostitele možnost změnit adresu URL, která má být načten.|  
|[UpdateUI](https://msdn.microsoft.com/library/aa753268.aspx)|Upozorní hostitele, že stav příkazu se změnil.|  
  
## <a name="remarks"></a>Poznámky  
 Hostitel může nahradit nabídek, panely nástrojů a kontextové nabídky, které používá Microsoft HTML analýzou a modul vykreslování (MSHTML) implementace tohoto rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 Definice toto rozhraní je k dispozici jako IDL nebo C++, jak je uvedeno níže.  
  
|Definice typu|Soubor|  
|---------------------|----------|  
|IDL|ATLIFace.idl|  
|C++|ATLIFace.h (také obsaženy v ATLBase.h)|  
  
## <a name="see-also"></a>Viz také  
 [IDocUIHostHandler](https://msdn.microsoft.com/library/aa753260.aspx)









