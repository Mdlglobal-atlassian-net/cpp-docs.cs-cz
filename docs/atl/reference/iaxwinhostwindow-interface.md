---
title: Rozhraní IAxWinHostWindow
ms.date: 11/04/2016
f1_keywords:
- IAxWinHostWindow
- ATLIFACE/ATL::IAxWinHostWindow
- ATLIFACE/ATL::AttachControl
- ATLIFACE/ATL::CreateControl
- ATLIFACE/ATL::CreateControlEx
- ATLIFACE/ATL::QueryControl
- ATLIFACE/ATL::SetExternalDispatch
- ATLIFACE/ATL::SetExternalUIHandler
helpviewer_keywords:
- IAxWinHostWindow interface
ms.assetid: 9821c035-cd52-4c46-b58a-9278064f09b4
ms.openlocfilehash: ebecc611660a788ce59bb11beb95bd60eacaf01b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330001"
---
# <a name="iaxwinhostwindow-interface"></a>Rozhraní IAxWinHostWindow

Toto rozhraní poskytuje metody pro manipulaci s ovládacím prvkem a jeho objektem hostitele.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
interface IAxWinHostWindow : IUnknown
```

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[AttachControl](#attachcontrol)|Připojí existující ovládací prvek k hostitelskému objektu.|
|[Vytvořit ovládací prvek](#createcontrol)|Vytvoří ovládací prvek a připojí jej k hostitelskému objektu.|
|[VytvořitOvládací prvek Ex](#createcontrolex)|Vytvoří ovládací prvek, připojí jej k objektu hostitele a volitelně nastaví obslužnou rutinu události.|
|[Ovládací prvek QueryControl](#querycontrol)|Vrátí ukazatel rozhraní hostovanému ovládacímu prvku.|
|[SetExternalDispatch](#setexternaldispatch)|Nastaví `IDispatch` externí rozhraní.|
|[Nakladač nastavení](#setexternaluihandler)|Nastaví `IDocHostUIHandlerDispatch` externí rozhraní.|

## <a name="remarks"></a>Poznámky

Toto rozhraní je vystaveno ovládacím objektům ActiveX společnosti ATL. Volání metody v tomto rozhraní vytvořit nebo připojit ovládací prvek k objektu hostitele, získat rozhraní z hostovaného ovládacího prvku nebo nastavit externí dispinterface nebo obslužné rutiny uživatelského rozhraní pro použití při hostování webového prohlížeče.

## <a name="requirements"></a>Požadavky

Definice tohoto rozhraní je k dispozici jako IDL nebo C ++, jak je znázorněno níže.

|Typ definice|File|
|---------------------|----------|
|Idl|ATLIFace.idl|
|C++|ATLIFace.h (také součástí ATLBase.h)|

## <a name="iaxwinhostwindowattachcontrol"></a><a name="attachcontrol"></a>IAxWinHostWindow::PřipojitOvládací prvek

Připojí existující (a dříve inicializované) ovládací prvek k objektu hostitele pomocí okna *označeného hWnd*.

```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```

### <a name="parameters"></a>Parametry

*pUnkControl*<br/>
[v] Ukazatel na `IUnknown` rozhraní ovládacího prvku, který má být připojen k hostitelskému objektu.

*Hwnd*<br/>
[v] Popisovač do okna, které mají být použity pro hostování.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="iaxwinhostwindowcreatecontrol"></a><a name="createcontrol"></a>IAxWinHostWindow::Ovládací prvek CreateControl

Vytvoří ovládací prvek, inicializuje jej a hostuje v okně označeném *hWnd*.

```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```

### <a name="parameters"></a>Parametry

*lpTricsData*<br/>
[v] Řetězec identifikující ovládací prvek k vytvoření. Může se jednat o kód CLSID (musí obsahovat závorky), progID, adresu URL nebo nezpracovaný kód HTML (předponou **mshtml:**).

*Hwnd*<br/>
[v] Popisovač do okna, které mají být použity pro hostování.

*pStream*<br/>
[v] Ukazatel rozhraní pro datový proud obsahující inicializační data pro ovládací prvek. Může být NULL.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Toto okno bude podtřídou objektem hostitele, který vystavuje toto rozhraní, takže zprávy se mohou odrazit do ovládacího prvku a další funkce kontejneru budou fungovat.

Volání této metody je ekvivalentní volání [IAxWinHostWindow::CreateControlEx](#createcontrolex).

Chcete-li vytvořit licencovaný ovládací prvek ActiveX, přečtěte si informace o tom, že [iAxWinHostWindowLic::CreateControlLic](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex).

## <a name="iaxwinhostwindowcreatecontrolex"></a><a name="createcontrolex"></a>IAxWinHostWindow::CreateControlEx

Vytvoří ovládací prvek ActiveX, inicializuje jej a hostuje v zadaném okně, podobně jako [IAxWinHostWindow::CreateControl](#createcontrol).

```
STDMETHOD(CreateControlEx)(
    LPCOLESTR lpszTricsData,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnk,
    REFIID riidAdvise,
    IUnknown* punkAdvise);
```

### <a name="parameters"></a>Parametry

*lpTricsData*<br/>
[v] Řetězec identifikující ovládací prvek k vytvoření. Může se jednat o kód CLSID (musí obsahovat závorky), progID, adresu URL nebo nezpracovaný kód HTML (s předponou **mshtml:**).

*Hwnd*<br/>
[v] Popisovač do okna, které mají být použity pro hostování.

*pStream*<br/>
[v] Ukazatel rozhraní pro datový proud obsahující inicializační data pro ovládací prvek. Může být NULL.

*ppUnk*<br/>
[out] Adresa ukazatele, který obdrží `IUnknown` rozhraní vytvořeného ovládacího prvku. Může být NULL.

*riidAdvise*<br/>
[v] Identifikátor rozhraní odchozí rozhraní na obsažený objekt. Může být IID_NULL.

*punkAdviseace*<br/>
[v] Ukazatel na `IUnknown` rozhraní objektu jímky, který má být připojen k `iidSink`spojovacímu bodu na obsaženém objektu určeném programem .

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Na `CreateControl` rozdíl `CreateControlEx` od metody také umožňuje přijímat ukazatel rozhraní na nově vytvořený ovládací prvek a nastavit jímka událostí pro příjem událostí vyvolaným ovládacím prvkem.

Chcete-li vytvořit licencovaný ovládací prvek ActiveX, přečtěte si informace o tom, že [iAxWinHostWindowLic::CreateControlLicEx](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex).

## <a name="iaxwinhostwindowquerycontrol"></a><a name="querycontrol"></a>IAxWinHostWindow::Ovládací prvek QueryControl

Vrátí zadaný ukazatel rozhraní poskytoovaný hostovaným ovládacím prvkem.

```
STDMETHOD(QueryControl)(
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>Parametry

*riid řekl:*<br/>
[v] ID rozhraní na ovládací prvek je požadováno.

*ppvObjekt*<br/>
[out] Adresa ukazatele, který obdrží zadané rozhraní vytvořeného ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="iaxwinhostwindowsetexternaldispatch"></a><a name="setexternaldispatch"></a>IAxWinHostWindow::SetExternalDispatch

Nastaví externí rozhraní dispinterface, které je k dispozici pro obsažené ovládací prvky prostřednictvím metody [IDocHostUIHandlerDispatch::GetExternal.](../../atl/reference/idochostuihandlerdispatch-interface.md)

```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```

### <a name="parameters"></a>Parametry

*pDisp*<br/>
[v] Ukazatel na `IDispatch` rozhraní.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="iaxwinhostwindowsetexternaluihandler"></a><a name="setexternaluihandler"></a>IAxWinHostWindow::SetExternalUIHandler

Voláním této funkce nastavte externí rozhraní [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) pro `CAxWindow` objekt.

```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```

### <a name="parameters"></a>Parametry

*pDisp*<br/>
[v] Ukazatel na `IDocHostUIHandlerDispatch` rozhraní.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Tato funkce je používána ovládacími prvky (například ovládacím prvkem `IDocHostUIHandlerDispatch` webového prohlížeče), které dotazují na web hostitele pro rozhraní.

## <a name="see-also"></a>Viz také

[Rozhraní IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)<br/>
[CAxWindow::QueryHost](../../atl/reference/caxwindow-class.md#queryhost)<br/>
[AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)
