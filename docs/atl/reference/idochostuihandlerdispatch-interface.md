---
title: Rozhraní iDocHostuiHandlerDispatch
ms.date: 07/02/2019
f1_keywords:
- IDocHostUIHandlerDispatch
- atlbase/ATL::IDocHostUIHandlerDispatch
helpviewer_keywords:
- IDocHostUIHandlerDispatch interface
ms.assetid: 6963a301-601a-4ac3-8bef-f7b252ea2fc6
ms.openlocfilehash: b7072b80b738aa12635427a2604b38fb3585b452
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329728"
---
# <a name="idochostuihandlerdispatch-interface"></a>Rozhraní iDocHostuiHandlerDispatch

Rozhraní k modulu analýzy a vykreslování microsoft html.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
interface IDocHostUIHandlerDispatch : IDispatch
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

> [!NOTE]
> Odkazy v následující tabulce jsou na referenční témata sady INet SDK pro členy rozhraní [IDocUIHostHandler.](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260\(v=vs.85\)) `IDocHostUIHandlerDispatch`má stejné funkce `IDocUIHostHandler`jako , s `IDocHostUIHandlerDispatch` rozdílem je, že `IDocUIHostHandler` je dispinterface vzhledem k tomu, že je vlastní rozhraní.

|||
|-|-|
|[EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\))|Volána z implementace MSHTML [IOleInPlaceActiveObject::EnableModeless](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless). Také volána, když MSHTML zobrazí modální uI.|
|[Objekt FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\))|Volána na hostitele MSHTML, aby hostitel nahradit datový objekt MSHTML.|
|[GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\))|Volat MSHTML, když je používán jako cíl přetažení povolit hostiteli zadat alternativní [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget).|
|[Získat externí](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\))|Volána MSHTML získat hostitele IDispatch rozhraní.|
|[GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\))|Načte možnosti ui hostitele MSHTML.|
|[Cesta GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\))|Vrátí klíč registru, pod kterým mshtml ukládá uživatelské předvolby.|
|[Hideui](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\))|Nazývá se, když mshtml odebere své nabídky a panely nástrojů.|
|[OnDocWindowAktivovat](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\))|Volána z implementace MSHTML [IOleInPlaceActiveObject::OnDocWindowActivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate).|
|[OnFrameWindowAktivovat](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\))|Volána z implementace MSHTML [IOleInPlaceActiveObject::OnFrameWindowActivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate).|
|[Změnit velikost ohraničení](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\))|Volána z implementace MSHTML [IOleInPlaceActiveObject::ResizeBorder](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder).|
|[Nabídka ShowContext](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\))|Volána z MSHTML pro zobrazení místní nabídky.|
|[Showui](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\))|Umožňuje hostiteli nahradit nabídky a panely nástrojů MSHTML.|
|[Akcelerátor překladu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\))|Volána MSHTML při [IOleInPlaceActiveObject::TranslateAccelerator](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator) nebo [IOleControlSite::TranslateAccelerator](/windows/win32/api/ocidl/nf-ocidl-iolecontrolsite-translateaccelerator) se nazývá.|
|[Přeložit url](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\))|Volal MSHTML umožnit hostiteli možnost upravit adresu URL, které mají být načteny.|
|[Aktualizační ui](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\))|Upozorní hostitele, že se změnil stav příkazu.|

## <a name="remarks"></a>Poznámky

Implementací tohoto rozhraní může hostitel nahradit nabídky, panely nástrojů a kontextové nabídky používané modulem analýzy a vykreslování jazyka Microsoft HTML (MSHTML).

## <a name="requirements"></a>Požadavky

Definice tohoto rozhraní je k dispozici jako IDL nebo C ++, jak je znázorněno níže.

|Typ definice|File|
|---------------------|----------|
|Idl|ATLIFace.idl|
|C++|ATLIFace.h (také součástí ATLBase.h)|

## <a name="see-also"></a>Viz také

[Idocuihostman](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260\(v=vs.85\))
