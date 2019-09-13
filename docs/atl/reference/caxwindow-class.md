---
title: CAxWindow – třída
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
ms.openlocfilehash: 6f5c178090a970906209e41da9298be61a61c639
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927860"
---
# <a name="caxwindow-class"></a>CAxWindow – třída

Tato třída poskytuje metody pro práci s oknem, který je hostitelem ovládacího prvku ActiveX.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CAxWindow : public CWindow
```

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[AttachControl](#attachcontrol)|Připojí k `CAxWindow` objektu existující ovládací prvek ActiveX.|
|[CAxWindow](#caxwindow)|`CAxWindow` Vytvoří objekt.|
|[CreateControl](#createcontrol)|Vytvoří ovládací prvek ActiveX, inicializuje ho a hostuje ho v `CAxWindow` okně.|
|[CreateControlEx](#createcontrolex)|Vytvoří ovládací prvek ActiveX a načte ukazatel rozhraní (nebo ukazatele) z ovládacího prvku.|
|[GetWndClassName](#getwndclassname)|Tras Načte předdefinovaný název `CAxWindow` třídy objektu.|
|[QueryControl](#querycontrol)|`IUnknown` Načte hostovaný ovládací prvek ActiveX.|
|[QueryHost](#queryhost)|`IUnknown` Načte ukazatel`CAxWindow` objektu.|
|[SetExternalDispatch](#setexternaldispatch)|Nastaví externí odesílající rozhraní používané `CAxWindow` objektem.|
|[SetExternalUIHandler](#setexternaluihandler)|Nastaví externí `IDocHostUIHandler` rozhraní používané `CAxWindow` objektem.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor =](#operator_eq)|Přiřadí HWND k existujícímu `CAxWindow` objektu.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje metody pro práci s oknem, který je hostitelem ovládacího prvku ActiveX. Hostování poskytuje " **AtlAxWin80"** , který je zabalený pomocí `CAxWindow`.

Třída `CAxWindow` je implementována jako specializace `CAxWindowT` třídy. Tato specializace je deklarována jako:

`typedef CAxWindowT<CWindow> CAxWindow;`

Pokud potřebujete změnit základní třídu, můžete použít `CAxWindowT` a zadat novou základní třídu jako argument šablony.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="attachcontrol"></a>CAxWindow::AttachControl

Vytvoří nový objekt hostitele, pokud ještě neexistuje, a připojí určený ovládací prvek k hostiteli.

```
HRESULT AttachControl(
    IUnknown* pControl,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>Parametry

*pControl*<br/>
pro Ukazatel na `IUnknown` ovládací prvek.

*ppUnkContainer*<br/>
mimo Ukazatel na `IUnknown` hostitele `AxWin` (objekt).

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Objekt ovládacího prvku, který se má připojit, musí být `AttachControl`před voláním správně inicializován.

##  <a name="caxwindow"></a>CAxWindow::CAxWindow

`CAxWindow` Vytvoří objekt pomocí existujícího popisovače objektu okna.

```
CAxWindow(HWND hWnd = NULL);
```

### <a name="parameters"></a>Parametry

*hWnd*<br/>
Popisovač existujícího objektu okna.

##  <a name="createcontrol"></a>CAxWindow::CreateControl

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

*lpszName*<br/>
Ukazatel na řetězec pro vytvoření ovládacího prvku. Musí být formátován jedním z následujících způsobů:

- Identifikátor ProgID, například`"MSCAL.Calendar.7"`

- Identifikátor CLSID, jako např.`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Adresa URL jako`"<https://www.microsoft.com>"`

- Odkaz na aktivní dokument, jako např.`"file://\\\Documents\MyDoc.doc"`

- Fragment kódu HTML, jako např.`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`musí předcházet fragment HTML, aby byl označený jako datový proud MSHTML. V platformách Windows Mobile jsou podporovány pouze identifikátory ProgID a CLSID. Systém Windows CE integrované platformy, jiné než Windows Mobile s podporou pro CE IE, podporují všechny typy, včetně ProgID, CLSID, URL, odkazů na aktivní dokument a fragment kódu HTML.

*pStream*<br/>
pro Ukazatel na datový proud, který slouží k inicializaci vlastností ovládacího prvku. Může mít hodnotu NULL.

*ppUnkContainer*<br/>
mimo Adresa ukazatele, který `IUnknown` dostane z kontejneru. Může mít hodnotu NULL.

*dwResID*<br/>
ID prostředku prostředku HTML. Ovládací prvek WebBrowser bude vytvořen a načten se zadaným prostředkem.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Pokud je použita druhá verze této metody, je vytvořen ovládací prvek HTML a svázán s prostředkem identifikovaným *dwResID*.

Tato metoda poskytuje stejný výsledek jako volání:

[!code-cpp[NVC_ATL_Windowing#42](../../atl/codesnippet/cpp/caxwindow-class_1.cpp)]

V tématu [CAxWindow2T:: CreateControlLic](../../atl/reference/caxwindow2t-class.md#createcontrollic) můžete vytvořit, inicializovat a hostovat licencovaný ovládací prvek ActiveX.

### <a name="example"></a>Příklad

Viz [hostování ovládacích prvků ActiveX pomocí ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pro ukázku, která `CreateControl`používá.

##  <a name="createcontrolex"></a>  CAxWindow::CreateControlEx

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

*lpszName*<br/>
Ukazatel na řetězec pro vytvoření ovládacího prvku. Musí být formátován jedním z následujících způsobů:

- Identifikátor ProgID, například`"MSCAL.Calendar.7"`

- Identifikátor CLSID, jako např.`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Adresa URL jako`"<https://www.microsoft.com>"`

- Odkaz na aktivní dokument, jako např.`"file://\\\Documents\MyDoc.doc"`

- Fragment kódu HTML, jako např.`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`musí předcházet fragment HTML, aby byl označený jako datový proud MSHTML. V platformách Windows Mobile jsou podporovány pouze identifikátory ProgID a CLSID. Systém Windows CE integrované platformy, jiné než Windows Mobile s podporou pro CE IE, podporují všechny typy, včetně ProgID, CLSID, URL, odkazů na aktivní dokument a fragment kódu HTML.

*pStream*<br/>
pro Ukazatel na datový proud, který slouží k inicializaci vlastností ovládacího prvku. Může mít hodnotu NULL.

*ppUnkContainer*<br/>
mimo Adresa ukazatele, který `IUnknown` dostane z kontejneru. Může mít hodnotu NULL.

*ppUnkControl*<br/>
mimo Adresa ukazatele, který `IUnknown` získá ovládací prvek. Může mít hodnotu NULL.

*iidSink*<br/>
pro Identifikátor rozhraní odchozího rozhraní u objektu, který ho obsahuje. Může být IID_NULL.

*punkSink*<br/>
pro Ukazatel na `IUnknown` rozhraní objektu jímky, který má být připojen k bodu připojení v objektu, který je určen parametrem *iidSink*.

*dwResID*<br/>
pro ID prostředku prostředku HTML. Ovládací prvek WebBrowser bude vytvořen a načten se zadaným prostředkem.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Tato metoda je podobná jako [CAxWindow:: CreateControl](#createcontrol), ale na rozdíl od této `CreateControlEx` metody, umožňuje také získat ukazatel rozhraní na nově vytvořený ovládací prvek a nastavit jímku událostí pro příjem událostí vyvolaných ovládacím prvkem.

V tématu [CAxWindow2T:: CreateControlLicEx](../../atl/reference/caxwindow2t-class.md#createcontrollicex) můžete vytvořit, inicializovat a hostovat licencovaný ovládací prvek ActiveX.

### <a name="example"></a>Příklad

Viz [hostování ovládacích prvků ActiveX pomocí ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pro ukázku, která `CreateControlEx`používá.

##  <a name="getwndclassname"></a>CAxWindow::GetWndClassName

Načte název třídy okna.

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na řetězec obsahující název třídy okna, která může hostovat nelicencované ovládací prvky ActiveX.

##  <a name="operator_eq"></a>CAxWindow:: operator =

Přiřadí HWND k existujícímu `CAxWindow` objektu.

```
CAxWindow<TBase>& operator=(HWND hWnd);
```

### <a name="parameters"></a>Parametry

*hWnd*<br/>
Popisovač pro existující okno.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na aktuální `CAxWindow` objekt.

##  <a name="querycontrol"></a>  CAxWindow::QueryControl

Načte určené rozhraní hostovaného ovládacího prvku.

```
HRESULT QueryControl(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryControl(Q** ppUnk);
```

### <a name="parameters"></a>Parametry

*iid*<br/>
pro Určuje IID rozhraní ovládacího prvku.

*ppUnk*<br/>
mimo Ukazatel na rozhraní ovládacího prvku. V šabloně verze této metody není nutné referenční ID, pokud je předáno typové rozhraní s přidruženým identifikátorem UUID.

*Q*<br/>
pro Rozhraní, na které se dotazuje.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

##  <a name="queryhost"></a>  CAxWindow::QueryHost

Vrátí zadané rozhraní hostitele.

```
HRESULT QueryHost(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryHost(Q** ppUnk);
```

### <a name="parameters"></a>Parametry

*iid*<br/>
pro Určuje IID rozhraní ovládacího prvku.

*ppUnk*<br/>
mimo Ukazatel na rozhraní na hostiteli. V šabloně verze této metody není nutné referenční ID, pokud je předáno typové rozhraní s přidruženým identifikátorem UUID.

*Q*<br/>
pro Rozhraní, na které se dotazuje.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Rozhraní hostitele umožňuje přístup k základní funkci kódu hostujícího okno, který implementuje `AxWin`.

##  <a name="setexternaldispatch"></a>CAxWindow::SetExternalDispatch

Nastaví externí rozhraní pro `CAxWindow` odeslání objektu.

```
HRESULT SetExternalDispatch(IDispatch* pDisp);
```

### <a name="parameters"></a>Parametry

*pDisp*<br/>
pro Ukazatel na `IDispatch` rozhraní.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

##  <a name="setexternaluihandler"></a>CAxWindow::SetExternalUIHandler

Nastaví externí rozhraní [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) pro `CAxWindow` objekt.

```
HRESULT SetExternalUIHandler(IDocHostUIHandlerDispatch* pUIHandler);
```

### <a name="parameters"></a>Parametry

*pUIHandler*<br/>
pro Ukazatel na `IDocHostUIHandlerDispatch` rozhraní.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Externí `IDocHostUIHandlerDispatch` rozhraní je používáno ovládacími prvky, které dotazují lokalitu `IDocHostUIHandlerDispatch` hostitele na rozhraní. Ovládací prvek WebBrowser je jeden ovládací prvek, který to dělá.

## <a name="see-also"></a>Viz také:

[Ukázka ATLCON](../../overview/visual-cpp-samples.md)<br/>
[CWindow – třída](../../atl/reference/cwindow-class.md)<br/>
[Složené základní prvky](../../atl/atl-composite-control-fundamentals.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Nejčastější dotazy k omezením řízení](../../atl/atl-control-containment-faq.md)
