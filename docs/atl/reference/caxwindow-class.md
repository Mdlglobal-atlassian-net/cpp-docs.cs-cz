---
title: Třída CAxWindow
ms.date: 11/04/2016
f1_keywords:
- CAxWindow
- ATLWIN/ATL::CAxWindow
- ATLWIN/ATL::AttachControl
- ATLWIN/ATL::CreateControl
- ATLWIN/ATL::CreateControlEx
- ATLWIN/ATL::GetWndClassName
- ATLWIN/ATL::QueryControl
- ATLWIN/ATL::QueryHost
- ATLWIN/ATL::SetExternalDispatch
- ATLWIN/ATL::SetExternalUIHandler
helpviewer_keywords:
- CAxWindow class
- ATL, hosting ActiveX controls
ms.assetid: 85e79261-43e4-4770-bde0-1ff87f222b0f
ms.openlocfilehash: 6f5629370bc1f821dac0a08cc76b5df1450f7a5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318725"
---
# <a name="caxwindow-class"></a>Třída CAxWindow

Tato třída poskytuje metody pro manipulaci s oknem hostujícím ovládací prvek ActiveX.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CAxWindow : public CWindow
```

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[AttachControl](#attachcontrol)|Připojí k `CAxWindow` objektu existující ovládací prvek ActiveX.|
|[Okno CAx](#caxwindow)|Vytvoří `CAxWindow` objekt.|
|[Vytvořit ovládací prvek](#createcontrol)|Vytvoří ovládací prvek ActiveX, inicializuje jej `CAxWindow` a hostuje v okně.|
|[VytvořitOvládací prvek Ex](#createcontrolex)|Vytvoří ovládací prvek ActiveX a načte ukazatel rozhraní (nebo ukazatele) z ovládacího prvku.|
|[GetWndClassName](#getwndclassname)|(Statické) Načte předdefinovaný název třídy objektu. `CAxWindow`|
|[Ovládací prvek QueryControl](#querycontrol)|`IUnknown` Načte hostovaný ovládací prvek ActiveX.|
|[QueryHost](#queryhost)|Načte `IUnknown` ukazatel objektu. `CAxWindow`|
|[SetExternalDispatch](#setexternaldispatch)|Nastaví externí expediční `CAxWindow` rozhraní používané objektem.|
|[Nakladač nastavení](#setexternaluihandler)|Nastaví `IDocHostUIHandler` externí rozhraní `CAxWindow` používané objektem.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor =](#operator_eq)|Přiřadí HWND existujícímu `CAxWindow` objektu.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje metody pro manipulaci s oknem, které je hostitelem ovládacího prvku ActiveX. Hosting je poskytován **"AtlAxWin80"**, který je `CAxWindow`zabalen .

Třída `CAxWindow` je implementována jako `CAxWindowT` specializace třídy. Tato specializace je deklarována jako:

`typedef CAxWindowT<CWindow> CAxWindow;`

Pokud potřebujete změnit základní třídu, `CAxWindowT` můžete použít a určit novou základní třídu jako argument šablony.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="caxwindowattachcontrol"></a><a name="attachcontrol"></a>CAxWindow::AttachControl

Vytvoří nový objekt hostitele, pokud ještě není přítomen a připojí zadaný ovládací prvek k hostiteli.

```
HRESULT AttachControl(
    IUnknown* pControl,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>Parametry

*pOvládací prvek*<br/>
[v] Ukazatel na `IUnknown` ovládací prvek.

*ppUnkContainer*<br/>
[out] Ukazatel na `IUnknown` hostitele `AxWin` (objekt).

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Připojený objekt ovládacího prvku musí být `AttachControl`před voláním správně inicializován .

## <a name="caxwindowcaxwindow"></a><a name="caxwindow"></a>CAxWindow::CAxWindow

Vytvoří `CAxWindow` objekt pomocí existujícího popisovače objektu okna.

```
CAxWindow(HWND hWnd = NULL);
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
Popisovač existujícího objektu okna.

## <a name="caxwindowcreatecontrol"></a><a name="createcontrol"></a>CAxWindow::CreateControl

Vytvoří, inicializuje a hostuje ovládací prvek ActiveX v zadaném okně.

```
HRESULT CreateControl(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL);

HRESULT CreateControl(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL);
```

### <a name="parameters"></a>Parametry

*název lpsz*<br/>
Ukazatel na řetězec k vytvoření ovládacího prvku. Musí být formátován jedním z následujících způsobů:

- ProgID, jako je`"MSCAL.Calendar.7"`

- CLSID, jako je`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Adresa URL, například`"<https://www.microsoft.com>"`

- Odkaz na aktivní dokument, například`"file://\\\Documents\MyDoc.doc"`

- Fragment HTML, například`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`musí předcházet fragmentu HTML tak, aby byl označen jako datový proud MSHTML. V platformách Windows Mobile jsou podporovány pouze ProgID a CLSID. Vestavěné platformy systému Windows CE, jiné než Windows Mobile s podporou ce IE podporují všechny typy včetně ProgID, CLSID, URL, odkaz na aktivní dokument a fragment HTML.

*pStream*<br/>
[v] Ukazatel na datový proud, který se používá k inicializaci vlastností ovládacího prvku. Může být NULL.

*ppUnkContainer*<br/>
[out] Adresa ukazatele, který obdrží `IUnknown` kontejneru. Může být NULL.

*dwResID*<br/>
ID prostředku prostředku HTML. Ovládací prvek WebBrowser bude vytvořen a načten se zadaným prostředkem.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Pokud je použita druhá verze této metody, je vytvořen ovládací prvek HTML a vázán na prostředek identifikovaný *dwResID*.

Tato metoda poskytuje stejný výsledek jako volání:

[!code-cpp[NVC_ATL_Windowing#42](../../atl/codesnippet/cpp/caxwindow-class_1.cpp)]

Viz [CAxWindow2T::CreateControlLic](../../atl/reference/caxwindow2t-class.md#createcontrollic) vytvořit, inicializovat a hostit licencovaný ovládací prvek ActiveX.

### <a name="example"></a>Příklad

Viz [Hostování ovládacích prvků ActiveX pomocí ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pro ukázku, která používá `CreateControl`.

## <a name="caxwindowcreatecontrolex"></a><a name="createcontrolex"></a>CAxWindow::CreateControlEx

Vytvoří, inicializuje a hostuje ovládací prvek ActiveX v zadaném okně.

```
HRESULT CreateControlEx(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL);

HRESULT CreateControlEx(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL);
```

### <a name="parameters"></a>Parametry

*název lpsz*<br/>
Ukazatel na řetězec k vytvoření ovládacího prvku. Musí být formátován jedním z následujících způsobů:

- ProgID, jako je`"MSCAL.Calendar.7"`

- CLSID, jako je`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Adresa URL, například`"<https://www.microsoft.com>"`

- Odkaz na aktivní dokument, například`"file://\\\Documents\MyDoc.doc"`

- Fragment HTML, například`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`musí předcházet fragmentu HTML tak, aby byl označen jako datový proud MSHTML. V platformách Windows Mobile jsou podporovány pouze ProgID a CLSID. Vestavěné platformy systému Windows CE, jiné než Windows Mobile s podporou ce IE podporují všechny typy včetně ProgID, CLSID, URL, odkaz na aktivní dokument a fragment HTML.

*pStream*<br/>
[v] Ukazatel na datový proud, který se používá k inicializaci vlastností ovládacího prvku. Může být NULL.

*ppUnkContainer*<br/>
[out] Adresa ukazatele, který obdrží `IUnknown` kontejneru. Může být NULL.

*ppUnkControl*<br/>
[out] Adresa ukazatele, který obdrží `IUnknown` ovládací prvek. Může být NULL.

*IidSink*<br/>
[v] Identifikátor rozhraní odchozí rozhraní na obsažený objekt. Může být IID_NULL.

*punkSink*<br/>
[v] Ukazatel na `IUnknown` rozhraní objektu jímky, který má být připojen k bodu připojení na obsaženém objektu určeném *iidSink*.

*dwResID*<br/>
[v] ID prostředku prostředku HTML. Ovládací prvek WebBrowser bude vytvořen a načten se zadaným prostředkem.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Tato metoda je podobná [CAxWindow::CreateControl](#createcontrol), `CreateControlEx` ale na rozdíl od této metody také umožňuje přijímat ukazatel rozhraní na nově vytvořený ovládací prvek a nastavit jímka událostí přijímat události aktivována ovládacího prvku.

Viz [CAxWindow2T::CreateControlLicEx](../../atl/reference/caxwindow2t-class.md#createcontrollicex) vytvořit, inicializovat a hostit licencovaný ovládací prvek ActiveX.

### <a name="example"></a>Příklad

Viz [Hostování ovládacích prvků ActiveX pomocí ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pro ukázku, která používá `CreateControlEx`.

## <a name="caxwindowgetwndclassname"></a><a name="getwndclassname"></a>CAxWindow::GetWndClassName

Načte název třídy okna.

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na řetězec obsahující název třídy okna, která může hostovat nelicencované ovládací prvky ActiveX.

## <a name="caxwindowoperator-"></a><a name="operator_eq"></a>CAxWindow::operátor =

Přiřadí HWND existujícímu `CAxWindow` objektu.

```
CAxWindow<TBase>& operator=(HWND hWnd);
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
Popisovač existujícího okna.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na `CAxWindow` aktuální objekt.

## <a name="caxwindowquerycontrol"></a><a name="querycontrol"></a>CAxWindow::Ovládací prvek QueryControl

Načte zadané rozhraní hostovaného ovládacího prvku.

```
HRESULT QueryControl(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryControl(Q** ppUnk);
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
[v] Určuje IID rozhraní ovládacího prvku.

*ppUnk*<br/>
[out] Ukazatel na rozhraní ovládacího prvku. Ve verzi šablony této metody není potřeba id odkazu, pokud je předáno zadané rozhraní s přidruženým UUID.

*Q*<br/>
[v] Rozhraní, které je dotazován.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="caxwindowqueryhost"></a><a name="queryhost"></a>CAxWindow::QueryHost

Vrátí zadané rozhraní hostitele.

```
HRESULT QueryHost(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryHost(Q** ppUnk);
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
[v] Určuje IID rozhraní ovládacího prvku.

*ppUnk*<br/>
[out] Ukazatel na rozhraní na hostiteli. Ve verzi šablony této metody není potřeba id odkazu, pokud je předáno zadané rozhraní s přidruženým UUID.

*Q*<br/>
[v] Rozhraní, které je dotazován.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Rozhraní hostitele umožňuje přístup k základní funkce okna-hosting kód, `AxWin`implementovaný .

## <a name="caxwindowsetexternaldispatch"></a><a name="setexternaldispatch"></a>CAxWindow::SetExternalDispatch

Nastaví externí rozhraní `CAxWindow` pro odesílání objektu.

```
HRESULT SetExternalDispatch(IDispatch* pDisp);
```

### <a name="parameters"></a>Parametry

*pDisp*<br/>
[v] Ukazatel na `IDispatch` rozhraní.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="caxwindowsetexternaluihandler"></a><a name="setexternaluihandler"></a>CAxWindow::SetExternalUIHandler

Nastaví externí rozhraní [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) pro `CAxWindow` objekt.

```
HRESULT SetExternalUIHandler(IDocHostUIHandlerDispatch* pUIHandler);
```

### <a name="parameters"></a>Parametry

*pUIHandler*<br/>
[v] Ukazatel na `IDocHostUIHandlerDispatch` rozhraní.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Externí `IDocHostUIHandlerDispatch` rozhraní používají ovládací prvky, které dotaz `IDocHostUIHandlerDispatch` hostitele webu pro rozhraní. Ovládací prvek WebBrowser je jeden ovládací prvek, který to dělá.

## <a name="see-also"></a>Viz také

[Vzorek ATLCON](../../overview/visual-cpp-samples.md)<br/>
[Třída CWindow](../../atl/reference/cwindow-class.md)<br/>
[Základy kompozitního řízení](../../atl/atl-composite-control-fundamentals.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Nejčastější dotazy týkající se omezení řízení](../../atl/atl-control-containment-faq.md)
