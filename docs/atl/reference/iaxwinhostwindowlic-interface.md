---
title: Rozhraní IAxWinHostWindowLic
ms.date: 11/04/2016
f1_keywords:
- IAxWinHostWindowLic
- ATLIFACE/ATL::IAxWinHostWindowLic
- ATLIFACE/ATL::CreateControlLic
- ATLIFACE/ATL::CreateControlLicEx
helpviewer_keywords:
- IAxWinHostWindowLic interface
ms.assetid: 750f1520-6bce-428c-aca0-fccbe3f063c7
ms.openlocfilehash: 561a65702f1d4f57b4db1afc75769ce4cc523c1c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329911"
---
# <a name="iaxwinhostwindowlic-interface"></a>Rozhraní IAxWinHostWindowLic

Toto rozhraní poskytuje metody pro manipulaci s licencovaným ovládacím prvkem a jeho objektem hostitele.

## <a name="syntax"></a>Syntaxe

```
interface IAxWinHostWindowLic : IAxWinHostWindow
```

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[VytvořitControlLic](#createcontrollic)|Vytvoří licencovaný ovládací prvek a připojí jej k hostitelskému objektu.|
|[VytvořitControlLicEx](#createcontrollicex)|Vytvoří licencovaný ovládací prvek, připojí jej k objektu hostitele a volitelně nastaví obslužnou rutinu události.|

## <a name="remarks"></a>Poznámky

`IAxWinHostWindowLic`dědí z [IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md) a přidává metody, které podporují vytváření licencovaných ovládacích prvků.

Viz [Hostování ovládacích prvků ActiveX pomocí KNIHOVNY ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pro ukázku, která používá členy tohoto rozhraní.

## <a name="requirements"></a>Požadavky

Definice tohoto rozhraní je k dispozici jako IDL nebo C ++, jak je znázorněno níže.

|Typ definice|File|
|---------------------|----------|
|Idl|ATLIFace.idl|
|C++|ATLIFace.h (také součástí ATLBase.h)|

## <a name="iaxwinhostwindowliccreatecontrollic"></a><a name="createcontrollic"></a>IAxWinHostWindowLic::CreateControlLic

Vytvoří licencovaný ovládací prvek, inicializuje jej a hostuje v okně určeném `hWnd`.

```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```

### <a name="parameters"></a>Parametry

*bstrlic*<br/>
[v] BSTR, který obsahuje licenční klíč pro ovládací prvek.

### <a name="remarks"></a>Poznámky

Viz [IAxWinHostWindow::CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol) pro popis zbývajících parametrů a vrácené hodnoty.

Volání této metody je ekvivalentní volání [IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex)

### <a name="example"></a>Příklad

Viz [Hostování ovládacích prvků ActiveX pomocí ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pro ukázku, která používá `IAxWinHostWindowLic::CreateControlLic`.

## <a name="iaxwinhostwindowliccreatecontrollicex"></a><a name="createcontrollicex"></a>IAxWinHostWindowLic::CreateControlLicEx

Vytvoří licencovaný ovládací prvek ActiveX, inicializuje jej a hostuje v zadaném okně, podobně jako [IAxWinHostWindow::CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol).

```
STDMETHOD(CreateControlLicEx)(
    LPCOLESTR lpszTricsData,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnk,
    REFIID riidAdvise,
    IUnknown* punkAdvise,
    BSTR bstrLic);
```

### <a name="parameters"></a>Parametry

*bstrlic*<br/>
[v] BSTR, který obsahuje licenční klíč pro ovládací prvek.

### <a name="remarks"></a>Poznámky

Viz [IAxWinHostWindow::CreateControlEx](../../atl/reference/iaxwinhostwindow-interface.md#createcontrolex) popis zbývajících parametrů a vrácená hodnota.

### <a name="example"></a>Příklad

Viz [Hostování ovládacích prvků ActiveX pomocí ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pro ukázku, která používá `IAxWinHostWindowLic::CreateControlLicEx`.
