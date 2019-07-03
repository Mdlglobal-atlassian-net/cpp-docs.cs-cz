---
title: IDocHostUIHandlerDispatch Interface
ms.date: 07/02/2019
f1_keywords:
- IDocHostUIHandlerDispatch
- atlbase/ATL::IDocHostUIHandlerDispatch
helpviewer_keywords:
- IDocHostUIHandlerDispatch interface
ms.assetid: 6963a301-601a-4ac3-8bef-f7b252ea2fc6
ms.openlocfilehash: a60c178eff1e02c3032e792f9a0420dfeab82388
ms.sourcegitcommit: 9b904e490b1e262293a602bd1291a8f3045e755b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2019
ms.locfileid: "67552159"
---
# <a name="idochostuihandlerdispatch-interface"></a>IDocHostUIHandlerDispatch Interface

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
>  Odkazy v následující tabulce jsou na referenční témata INet SDK pro členy [IDocUIHostHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260\(v=vs.85\)) rozhraní. `IDocHostUIHandlerDispatch` má stejné funkce jako `IDocUIHostHandler`, s rozdílem je, který `IDocHostUIHandlerDispatch` vzhledem k tomu je dispinterface `IDocUIHostHandler` je vlastní rozhraní.

|||
|-|-|
|[EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\))|Volání z implementace MSHTML [IOleInPlaceActiveObject::EnableModeless](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless). Také volá se, když MSHTML zobrazí modální uživatelské rozhraní.|
|[FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\))|Volá se na hostiteli pomocí MSHTML aplikace umožňující hostitele k nahrazení MSHTML na datový objekt.|
|[GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\))|Voláno rozhraním MSHTML aplikace, když se používá se jako cíl přetažení k hostiteli umožní zadat alternativní [IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget).|
|[GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\))|Je voláno MSHTML získat rozhraní IDispatch hostitele.|
|[GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\))|Načte možnosti uživatelského rozhraní MSHTML hostitele.|
|[GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\))|Vrátí klíč registru, ve které ukládá MSHTML předvolby uživatele.|
|[HideUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\))|Volá se, když MSHTML odebere jeho nabídek a panelů nástrojů.|
|[OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\))|Volání z implementace MSHTML [IOleInPlaceActiveObject::OnDocWindowActivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate).|
|[OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\))|Volání z implementace MSHTML [IOleInPlaceActiveObject::OnFrameWindowActivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate).|
|[ResizeBorder](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\))|Volání z implementace MSHTML [IOleInPlaceActiveObject::ResizeBorder](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder).|
|[ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\))|Volá se z MSHTML zobrazení místní nabídky.|
|[ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\))|Umožňuje hostiteli nahradit MSHTML nabídek a panelů nástrojů.|
|[TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\))|Volané MSHTML při [IOleInPlaceActiveObject::TranslateAccelerator](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator) nebo [IOleControlSite::TranslateAccelerator](/windows/desktop/api/ocidl/nf-ocidl-iolecontrolsite-translateaccelerator) je volána.|
|[TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\))|Je voláno MSHTML aplikace umožňující hostitele příležitost změnit adresu URL, který se má načíst.|
|[UpdateUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\))|Upozorňuje hostitele, stav příkazu se změnila.|

## <a name="remarks"></a>Poznámky

Hostitele můžete nahradit nabídky, panely nástrojů a kontextové nabídky, které používá Microsoft HTML analýzou a vykreslovací modul (MSHTML) implementace tohoto rozhraní.

## <a name="requirements"></a>Požadavky

Definice toto rozhraní není k dispozici jako IDL nebo C++, jak je znázorněno níže.

|Typ definice|Soubor|
|---------------------|----------|
|IDL|ATLIFace.idl|
|C++|ATLIFace.h (také součástí ATLBase.h)|

## <a name="see-also"></a>Viz také:

[IDocUIHostHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260\(v=vs.85\))
