---
title: IAxWinHostWindowLic Interface
ms.date: 11/04/2016
f1_keywords:
- IAxWinHostWindowLic
- ATLIFACE/ATL::IAxWinHostWindowLic
- ATLIFACE/ATL::CreateControlLic
- ATLIFACE/ATL::CreateControlLicEx
helpviewer_keywords:
- IAxWinHostWindowLic interface
ms.assetid: 750f1520-6bce-428c-aca0-fccbe3f063c7
ms.openlocfilehash: aca3970d13db53ffa04fe9582bbe9b8db78e820d
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417640"
---
# <a name="iaxwinhostwindowlic-interface"></a>IAxWinHostWindowLic Interface

Toto rozhraní poskytuje metody pro manipulaci s licencovaným ovládacím prvkem a jeho hostitelským objektem.

## <a name="syntax"></a>Syntaxe

```
interface IAxWinHostWindowLic : IAxWinHostWindow
```

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[CreateControlLic](#createcontrollic)|Vytvoří licencovaný ovládací prvek a připojí ho k objektu hostitele.|
|[CreateControlLicEx](#createcontrollicex)|Vytvoří licencovaný ovládací prvek, připojí ho k objektu hostitele a volitelně nastaví obslužnou rutinu události.|

## <a name="remarks"></a>Poznámky

`IAxWinHostWindowLic` dědí z [IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md) a přidává metody, které podporují vytváření licencovaných ovládacích prvků.

Viz [hostování ovládacích prvků ActiveX pomocí ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pro ukázku, která používá členy tohoto rozhraní.

## <a name="requirements"></a>Požadavky

Definice tohoto rozhraní je k dispozici jako IDL nebo C++, jak je znázorněno níže.

|Typ definice|Soubor|
|---------------------|----------|
|JAZYKA|ATLIFace. idl|
|C++|ATLIFace. h (také zahrnuté v ATLBase. h)|

##  <a name="createcontrollic"></a>IAxWinHostWindowLic::CreateControlLic

Vytvoří licencovaný ovládací prvek, inicializuje ho a hostuje ho v okně určeném `hWnd`.

```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```

### <a name="parameters"></a>Parametry

*bstrLic*<br/>
pro BSTR, který obsahuje licenční klíč pro ovládací prvek.

### <a name="remarks"></a>Poznámky

Popis zbývajících parametrů a návratové hodnoty naleznete v tématu [IAxWinHostWindow:: CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol) .

Volání této metody je ekvivalentní volání metody [IAxWinHostWindowLic:: CreateControlLicEx](#createcontrollicex)

### <a name="example"></a>Příklad

Ukázku, která používá `IAxWinHostWindowLic::CreateControlLic`, najdete v tématu [hostování ovládacích prvků ActiveX pomocí ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) .

##  <a name="createcontrollicex"></a>IAxWinHostWindowLic::CreateControlLicEx

Vytvoří licencovaný ovládací prvek ActiveX, inicializuje ho a hostuje v zadaném okně, podobně jako [IAxWinHostWindow:: CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol).

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

*bstrLic*<br/>
pro BSTR, který obsahuje licenční klíč pro ovládací prvek.

### <a name="remarks"></a>Poznámky

Popis zbývajících parametrů a návratové hodnoty naleznete v tématu [IAxWinHostWindow:: CreateControlEx](../../atl/reference/iaxwinhostwindow-interface.md#createcontrolex) .

### <a name="example"></a>Příklad

Ukázku, která používá `IAxWinHostWindowLic::CreateControlLicEx`, najdete v tématu [hostování ovládacích prvků ActiveX pomocí ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) .
