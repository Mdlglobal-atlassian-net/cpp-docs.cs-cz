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
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78864724"
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
|[AttachControl](#attachcontrol)|Připojí existující ovládací prvek ActiveX k objektu `CAxWindow`.|
|[CAxWindow](#caxwindow)|Vytvoří objekt `CAxWindow`.|
|[CreateControl](#createcontrol)|Vytvoří ovládací prvek ActiveX, inicializuje ho a hostuje ho v okně `CAxWindow`.|
|[CreateControlEx](#createcontrolex)|Vytvoří ovládací prvek ActiveX a načte ukazatel rozhraní (nebo ukazatele) z ovládacího prvku.|
|[GetWndClassName](#getwndclassname)|Tras Načte předdefinovaný název třídy objektu `CAxWindow`.|
|[QueryControl](#querycontrol)|Načte `IUnknown` hostovaného ovládacího prvku ActiveX.|
|[QueryHost](#queryhost)|Načte ukazatel `IUnknown` objektu `CAxWindow`.|
|[SetExternalDispatch](#setexternaldispatch)|Nastaví externí odesílající rozhraní používané objektem `CAxWindow`.|
|[SetExternalUIHandler](#setexternaluihandler)|Nastaví externí rozhraní `IDocHostUIHandler` používané objektem `CAxWindow`.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor =](#operator_eq)|Přiřadí HWND k existujícímu objektu `CAxWindow`.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje metody pro práci s oknem, který je hostitelem ovládacího prvku ActiveX. Hostování poskytuje " **AtlAxWin80"** , který je zabalen pomocí `CAxWindow`.

`CAxWindow` třídy je implementována jako specializace `CAxWindowT` třídy. Tato specializace je deklarována jako:

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
pro Ukazatel na `IUnknown` ovládacího prvku.

*ppUnkContainer*<br/>
mimo Ukazatel na `IUnknown` hostitele (objekt `AxWin`).

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Objekt ovládacího prvku, který se má připojit, musí být před voláním `AttachControl`správně inicializován.

##  <a name="caxwindow"></a>CAxWindow::CAxWindow

Vytvoří objekt `CAxWindow` pomocí existujícího popisovače objektu okna.

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

- Identifikátor ProgID, například `"MSCAL.Calendar.7"`

- Identifikátor CLSID, například `"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Adresa URL jako `"<https://www.microsoft.com>"`

- Odkaz na aktivní dokument, například `"file://\\\Documents\MyDoc.doc"`

- Fragment kódu HTML, například `"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"` musí předcházet fragment kódu HTML, aby byl označený jako datový proud MSHTML. V platformách Windows Mobile jsou podporovány pouze identifikátory ProgID a CLSID. Systém Windows CE integrované platformy, jiné než Windows Mobile s podporou pro CE IE, podporují všechny typy, včetně ProgID, CLSID, URL, odkazů na aktivní dokument a fragment kódu HTML.

*pStream*<br/>
pro Ukazatel na datový proud, který slouží k inicializaci vlastností ovládacího prvku. Může mít hodnotu NULL.

*ppUnkContainer*<br/>
mimo Adresa ukazatele, který získá `IUnknown` kontejneru. Může mít hodnotu NULL.

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

Ukázku, která používá `CreateControl`, najdete v tématu [hostování ovládacích prvků ActiveX pomocí ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) .

##  <a name="createcontrolex"></a>CAxWindow::CreateControlEx

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

- Identifikátor ProgID, například `"MSCAL.Calendar.7"`

- Identifikátor CLSID, například `"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Adresa URL jako `"<https://www.microsoft.com>"`

- Odkaz na aktivní dokument, například `"file://\\\Documents\MyDoc.doc"`

- Fragment kódu HTML, například `"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"` musí předcházet fragment kódu HTML, aby byl označený jako datový proud MSHTML. V platformách Windows Mobile jsou podporovány pouze identifikátory ProgID a CLSID. Systém Windows CE integrované platformy, jiné než Windows Mobile s podporou pro CE IE, podporují všechny typy, včetně ProgID, CLSID, URL, odkazů na aktivní dokument a fragment kódu HTML.

*pStream*<br/>
pro Ukazatel na datový proud, který slouží k inicializaci vlastností ovládacího prvku. Může mít hodnotu NULL.

*ppUnkContainer*<br/>
mimo Adresa ukazatele, který získá `IUnknown` kontejneru. Může mít hodnotu NULL.

*ppUnkControl*<br/>
mimo Adresa ukazatele, který dostane `IUnknown` ovládacího prvku. Může mít hodnotu NULL.

*iidSink*<br/>
pro Identifikátor rozhraní odchozího rozhraní u objektu, který ho obsahuje. Lze IID_NULL.

*punkSink*<br/>
pro Ukazatel na `IUnknown` rozhraní objektu jímky, který má být připojen k bodu připojení v objektu, který je určen parametrem *iidSink*.

*dwResID*<br/>
pro ID prostředku prostředku HTML. Ovládací prvek WebBrowser bude vytvořen a načten se zadaným prostředkem.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Tato metoda je podobná jako [CAxWindow:: CreateControl](#createcontrol), ale na rozdíl od této metody, `CreateControlEx` také umožňuje získat ukazatel rozhraní na nově vytvořený ovládací prvek a nastavit jímku událostí pro příjem událostí, které ovládací prvek vyvolal.

V tématu [CAxWindow2T:: CreateControlLicEx](../../atl/reference/caxwindow2t-class.md#createcontrollicex) můžete vytvořit, inicializovat a hostovat licencovaný ovládací prvek ActiveX.

### <a name="example"></a>Příklad

Ukázku, která používá `CreateControlEx`, najdete v tématu [hostování ovládacích prvků ActiveX pomocí ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) .

##  <a name="getwndclassname"></a>CAxWindow::GetWndClassName

Načte název třídy okna.

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na řetězec obsahující název třídy okna, která může hostovat nelicencované ovládací prvky ActiveX.

##  <a name="operator_eq"></a>CAxWindow:: operator =

Přiřadí HWND k existujícímu objektu `CAxWindow`.

```
CAxWindow<TBase>& operator=(HWND hWnd);
```

### <a name="parameters"></a>Parametry

*hWnd*<br/>
Popisovač pro existující okno.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na aktuální objekt `CAxWindow`.

##  <a name="querycontrol"></a>CAxWindow::QueryControl

Načte určené rozhraní hostovaného ovládacího prvku.

```
HRESULT QueryControl(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryControl(Q** ppUnk);
```

### <a name="parameters"></a>Parametry

*identifikátor*<br/>
pro Určuje IID rozhraní ovládacího prvku.

*ppUnk*<br/>
mimo Ukazatel na rozhraní ovládacího prvku. V šabloně verze této metody není nutné referenční ID, pokud je předáno typové rozhraní s přidruženým identifikátorem UUID.

*Č*<br/>
pro Rozhraní, na které se dotazuje.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

##  <a name="queryhost"></a>CAxWindow::QueryHost

Vrátí zadané rozhraní hostitele.

```
HRESULT QueryHost(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryHost(Q** ppUnk);
```

### <a name="parameters"></a>Parametry

*identifikátor*<br/>
pro Určuje IID rozhraní ovládacího prvku.

*ppUnk*<br/>
mimo Ukazatel na rozhraní na hostiteli. V šabloně verze této metody není nutné referenční ID, pokud je předáno typové rozhraní s přidruženým identifikátorem UUID.

*Č*<br/>
pro Rozhraní, na které se dotazuje.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Rozhraní hostitele umožňuje přístup k základní funkci kódu hostujícího okno, implementovaného `AxWin`.

##  <a name="setexternaldispatch"></a>CAxWindow::SetExternalDispatch

Nastaví externí odesílající rozhraní pro objekt `CAxWindow`.

```
HRESULT SetExternalDispatch(IDispatch* pDisp);
```

### <a name="parameters"></a>Parametry

*pDisp*<br/>
pro Ukazatel na rozhraní `IDispatch`.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

##  <a name="setexternaluihandler"></a>CAxWindow::SetExternalUIHandler

Nastaví externí rozhraní [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) pro objekt `CAxWindow`.

```
HRESULT SetExternalUIHandler(IDocHostUIHandlerDispatch* pUIHandler);
```

### <a name="parameters"></a>Parametry

*pUIHandler*<br/>
pro Ukazatel na rozhraní `IDocHostUIHandlerDispatch`.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Rozhraní External `IDocHostUIHandlerDispatch` je používáno ovládacími prvky, které dotazují lokalitu hostitele na rozhraní `IDocHostUIHandlerDispatch`. Ovládací prvek WebBrowser je jeden ovládací prvek, který to dělá.

## <a name="see-also"></a>Viz také

[Ukázka ATLCON](../../overview/visual-cpp-samples.md)<br/>
[CWindow – třída](../../atl/reference/cwindow-class.md)<br/>
[Složené základní prvky](../../atl/atl-composite-control-fundamentals.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Nejčastější dotazy k omezením řízení](../../atl/atl-control-containment-faq.md)
