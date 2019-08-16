---
title: Rozhraní IDocHostUIHandlerDispatch
ms.date: 07/02/2019
f1_keywords:
- IDocHostUIHandlerDispatch
- atlbase/ATL::IDocHostUIHandlerDispatch
helpviewer_keywords:
- IDocHostUIHandlerDispatch interface
ms.assetid: 6963a301-601a-4ac3-8bef-f7b252ea2fc6
ms.openlocfilehash: a9e672144160528e6a2fbfe4cb702c4d211ef720
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495911"
---
# <a name="idochostuihandlerdispatch-interface"></a>Rozhraní IDocHostUIHandlerDispatch

Rozhraní pro modul analýzy a vykreslování Microsoft HTML.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
interface IDocHostUIHandlerDispatch : IDispatch
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

> [!NOTE]
>  Odkazy v následující tabulce jsou referenčními tématy sady INet SDK pro členy rozhraní [IDocUIHostHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260\(v=vs.85\)) . `IDocHostUIHandlerDispatch`má stejné funkce jako `IDocUIHostHandler`s rozdílem, že `IDocHostUIHandlerDispatch` se jedná o odesílající rozhraní, `IDocUIHostHandler` zatímco je to vlastní rozhraní.

|||
|-|-|
|[EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\))|Voláno z implementace MSHTML z [IOleInPlaceActiveObject:: EnableModeless](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless). Volá se taky v případě, že MSHTML zobrazuje modální uživatelské rozhraní.|
|[FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\))|Volá se na hostiteli pomocí souboru MSHTML, aby mohl hostitel nahradit datový objekt MSHTML.|
|[GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\))|Volá se modulem MSHTML, když se používá jako cíl přetažení, aby mohl hostitel poskytnout alternativní [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget).|
|[Getexternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\))|Volá se modulem MSHTML, aby získala rozhraní IDispatch hostitele.|
|[GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\))|Načte možnosti uživatelského rozhraní hostitele MSHTML.|
|[GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\))|Vrátí klíč registru, pod kterým MSHTML ukládá předvolby uživatele.|
|[HideUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\))|Volá se, když MSHTML odebere své nabídky a panely nástrojů.|
|[OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\))|Voláno z implementace MSHTML z [IOleInPlaceActiveObject:: OnDocWindowActivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate).|
|[OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\))|Voláno z implementace MSHTML z [IOleInPlaceActiveObject:: OnFrameWindowActivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate).|
|[ResizeBorder](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\))|Voláno z implementace MSHTML z [IOleInPlaceActiveObject:: ResizeBorder](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder).|
|[ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\))|Volá se z MSHTML, aby se zobrazila kontextová nabídka.|
|[ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\))|Umožňuje hostiteli nahradit nabídky a panely nástrojů MSHTML.|
|[TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\))|Volá se pomocí MSHTML, když se volá [IOleInPlaceActiveObject:: TranslateAccelerator](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator) nebo [IOleControlSite:: TranslateAccelerator](/windows/win32/api/ocidl/nf-ocidl-iolecontrolsite-translateaccelerator) .|
|[TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\))|Volá se modulem MSHTML, aby mohl hostitel možnost změnit adresu URL, která se má načíst.|
|[UpdateUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\))|Upozorní hostitele, že došlo ke změně stavu příkazu.|

## <a name="remarks"></a>Poznámky

Hostitel může nahradit nabídky, panely nástrojů a kontextové nabídky, které používá modul Microsoft HTML Analyze and Rendering Engine (MSHTML) implementací tohoto rozhraní.

## <a name="requirements"></a>Požadavky

Definice tohoto rozhraní je k dispozici jako IDL nebo C++, jak je znázorněno níže.

|Typ definice|Soubor|
|---------------------|----------|
|JAZYKA|ATLIFace. idl|
|C++|ATLIFace. h (také zahrnuté v ATLBase. h)|

## <a name="see-also"></a>Viz také:

[IDocUIHostHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260\(v=vs.85\))
