---
title: Iaxwinhostwindow – rozhraní | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IAxWinHostWindow
- ATLIFACE/ATL::IAxWinHostWindow
- ATLIFACE/ATL::AttachControl
- ATLIFACE/ATL::CreateControl
- ATLIFACE/ATL::CreateControlEx
- ATLIFACE/ATL::QueryControl
- ATLIFACE/ATL::SetExternalDispatch
- ATLIFACE/ATL::SetExternalUIHandler
dev_langs:
- C++
helpviewer_keywords:
- IAxWinHostWindow interface
ms.assetid: 9821c035-cd52-4c46-b58a-9278064f09b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bee312cd5e7a88dd0798778d5f8385df265d78a1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099770"
---
# <a name="iaxwinhostwindow-interface"></a>Iaxwinhostwindow – rozhraní

Toto rozhraní poskytuje metody pro práci s ovládacím prvkem a jeho objekt hostitele.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
interface IAxWinHostWindow : IUnknown
```

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[AttachControl](#attachcontrol)|Připojí ke objekt hostitele existujícího ovládacího prvku.|
|[CreateControl](#createcontrol)|Vytvoří ovládací prvek a připojí ho k objektu hostitele.|
|[CreateControlEx](#createcontrolex)|Vytvoří ovládací prvek a připojí ho k objektu hostitele volitelně nastaví obslužnou rutinu události.|
|[QueryControl](#querycontrol)|Vrátí ukazatel rozhraní do hostovaného ovládacího prvku.|
|[SetExternalDispatch](#setexternaldispatch)|Nastaví externí `IDispatch` rozhraní.|
|[SetExternalUIHandler](#setexternaluihandler)|Nastaví externí `IDocHostUIHandlerDispatch` rozhraní.|

## <a name="remarks"></a>Poznámky

Toto rozhraní je zveřejněný prostřednictvím ovládací prvek ActiveX knihovny ATL pro hostování objektů. Volání metody na tomto rozhraní můžete vytvořit nebo připojit ovládací prvek do objektu hostitele získat rozhraní z hostovaného ovládacího prvku, nebo nastavit externí dispinterface nebo obslužné rutiny UI pro použití při hostování webového prohlížeče.

## <a name="requirements"></a>Požadavky

Definice toto rozhraní není k dispozici jako IDL nebo C++, jak je znázorněno níže.

|Typ definice|Soubor|
|---------------------|----------|
|IDL|ATLIFace.idl|
|C++|ATLIFace.h (také součástí ATLBase.h)|

##  <a name="attachcontrol"></a>  IAxWinHostWindow::AttachControl

Ovládací prvek existující (a dřív inicializovaný) připojí ke objekt hostitele pomocí okna identifikovaný *hWnd*.

```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```

### <a name="parameters"></a>Parametry

*pUnkControl*<br/>
[in] Ukazatel `IUnknown` rozhraní připojené k hostitelský objekt ovládacího prvku.

*hWnd*<br/>
[in] Popisovač okna pro hostování.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

##  <a name="createcontrol"></a>  IAxWinHostWindow::CreateControl

Vytvoří ovládací prvek, inicializuje ji a hostuje ji v okně identifikovaný *hWnd*.

```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```

### <a name="parameters"></a>Parametry

*lpTricsData*<br/>
[in] Řetězec, který identifikuje ovládací prvek k vytvoření. Může být identifikátor CLSID (musí obsahovat složené závorky), ProgID, adresa URL nebo nezpracovaný kód HTML (předchází **MSHTML:**).

*hWnd*<br/>
[in] Popisovač okna pro hostování.

*pStream*<br/>
[in] Ukazatel rozhraní pro datový proud obsahující inicializační data pro ovládací prvek. Může mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Toto okno se má rozčlenit do podtříd objektem hostitele vystavení toto rozhraní tak, aby se zprávy můžou projeví do ovládacího prvku a další funkce kontejneru bude fungovat.

Voláním této metody je ekvivalentní volání [IAxWinHostWindow::CreateControlEx](#createcontrolex).

Vytvoření licencovaného ovládacího prvku ActiveX, najdete v tématu [IAxWinHostWindowLic::CreateControlLic](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex).

##  <a name="createcontrolex"></a>  IAxWinHostWindow::CreateControlEx

Vytvoří ovládací prvek ActiveX, inicializuje ji a hostuje ji v zadaném okně, podobně jako [IAxWinHostWindow::CreateControl](#createcontrol).

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
[in] Řetězec, který identifikuje ovládací prvek k vytvoření. Může být identifikátor CLSID (musí obsahovat složené závorky), ProgID, adresa URL nebo nezpracovaný kód HTML (s předponou **MSHTML:**).

*hWnd*<br/>
[in] Popisovač okna pro hostování.

*pStream*<br/>
[in] Ukazatel rozhraní pro datový proud obsahující inicializační data pro ovládací prvek. Může mít hodnotu NULL.

*ppUnk*<br/>
[out] Adresa ukazatel, který se zobrazí `IUnknown` rozhraní vytvořený ovládací prvek. Může mít hodnotu NULL.

*riidAdvise*<br/>
[in] Identifikátor rozhraní odchozí rozhraní v obsažený objekt. Může mít hodnotu IID_NULL.

*punkAdvise*<br/>
[in] Ukazatel `IUnknown` rozhraní jímky objektu k připojení k bodu připojení na obsaženého objektu určeného `iidSink`.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Na rozdíl od `CreateControl` metody `CreateControlEx` také umožňuje přijímat ukazatel rozhraní na nově vytvořený ovládací prvek a nastavit jímky událostí přijímat události vyvolané ovládacího prvku.

Vytvoření licencovaného ovládacího prvku ActiveX, najdete v tématu [IAxWinHostWindowLic::CreateControlLicEx](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex).

##  <a name="querycontrol"></a>  IAxWinHostWindow::QueryControl

Vrátí ukazatel zadané rozhraní poskytovaných hostovaného ovládacího prvku.

```
STDMETHOD(QueryControl)(
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>Parametry

*riid*<br/>
[in] ID rozhraní na ovládací prvek požaduje.

*ppvObject*<br/>
[out] Adresa ukazatel, který se zobrazí zadané rozhraní vytvořený ovládací prvek.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

##  <a name="setexternaldispatch"></a>  IAxWinHostWindow::SetExternalDispatch

Nastaví externí dispinterface, která je k dispozici pro obsažené ovládací prvky prostřednictvím [IDocHostUIHandlerDispatch::GetExternal](../../atl/reference/idochostuihandlerdispatch-interface.md) metody.

```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```

### <a name="parameters"></a>Parametry

*pDisp*<br/>
[in] Ukazatel `IDispatch` rozhraní.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

##  <a name="setexternaluihandler"></a>  IAxWinHostWindow::SetExternalUIHandler

Voláním této funkce nastavíte externí [idochostuihandlerdispatch –](../../atl/reference/idochostuihandlerdispatch-interface.md) rozhraní `CAxWindow` objektu.

```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```

### <a name="parameters"></a>Parametry

*pDisp*<br/>
[in] Ukazatel `IDocHostUIHandlerDispatch` rozhraní.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Tato funkce používá ovládací prvky (jako je například ovládací prvek webového prohlížeče), které se dotazují hostitelský server pro `IDocHostUIHandlerDispatch` rozhraní.

## <a name="see-also"></a>Viz také

[IAxWinAmbientDispatch – rozhraní](../../atl/reference/iaxwinambientdispatch-interface.md)<br/>
[CAxWindow::QueryHost](../../atl/reference/caxwindow-class.md#queryhost)<br/>
[AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)

