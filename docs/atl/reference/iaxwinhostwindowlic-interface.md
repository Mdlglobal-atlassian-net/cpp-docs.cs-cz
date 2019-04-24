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
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62275987"
---
# <a name="iaxwinhostwindowlic-interface"></a>IAxWinHostWindowLic Interface

Toto rozhraní poskytuje metody pro manipulaci s licencovaného ovládacího prvku a jeho objekt hostitele.

## <a name="syntax"></a>Syntaxe

```
interface IAxWinHostWindowLic : IAxWinHostWindow
```

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[CreateControlLic](#createcontrollic)|Vytvoří licencovaného ovládacího prvku a připojí ho k objektu hostitele.|
|[CreateControlLicEx](#createcontrollicex)|Vytvoří licencovaného ovládacího prvku a připojí ho k objektu hostitele volitelně nastaví obslužnou rutinu události.|

## <a name="remarks"></a>Poznámky

`IAxWinHostWindowLic` dědí z [iaxwinhostwindow –](../../atl/reference/iaxwinhostwindow-interface.md) a přidá metody, které podporují vytváření licencované ovládací prvky.

Zobrazit [hostování ActiveX ovládacích prvků pomocí knihovny ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) ukázku, která používá členy tohoto rozhraní.

## <a name="requirements"></a>Požadavky

Definice toto rozhraní není k dispozici jako IDL nebo C++, jak je znázorněno níže.

|Typ definice|Soubor|
|---------------------|----------|
|IDL|ATLIFace.idl|
|C++|ATLIFace.h (také součástí ATLBase.h)|

##  <a name="createcontrollic"></a>  IAxWinHostWindowLic::CreateControlLic

Vytvoří licencovaného ovládacího prvku, inicializuje ji a hostuje ji v okně identifikovaný `hWnd`.

```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```

### <a name="parameters"></a>Parametry

*bstrLic*<br/>
[in] BSTR, který obsahuje licenční klíč pro ovládací prvek.

### <a name="remarks"></a>Poznámky

Zobrazit [IAxWinHostWindow::CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol) popis zbývající parametry a návratové hodnoty.

Voláním této metody je ekvivalentní volání [IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex)

### <a name="example"></a>Příklad

Zobrazit [hostování ActiveX ovládacích prvků pomocí knihovny ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) ukázku, která používá `IAxWinHostWindowLic::CreateControlLic`.

##  <a name="createcontrollicex"></a>  IAxWinHostWindowLic::CreateControlLicEx

Vytvoří licencovaného ovládacího prvku ActiveX, inicializuje ji a hostuje ji v zadaném okně, podobně jako [IAxWinHostWindow::CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol).

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
[in] BSTR, který obsahuje licenční klíč pro ovládací prvek.

### <a name="remarks"></a>Poznámky

Zobrazit [IAxWinHostWindow::CreateControlEx](../../atl/reference/iaxwinhostwindow-interface.md#createcontrolex) popis zbývající parametry a návratové hodnoty.

### <a name="example"></a>Příklad

Zobrazit [hostování ActiveX ovládacích prvků pomocí knihovny ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) ukázku, která používá `IAxWinHostWindowLic::CreateControlLicEx`.
