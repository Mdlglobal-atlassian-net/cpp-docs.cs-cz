---
title: Třída CAxWindow | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CAxWindow class
- ATL, hosting ActiveX controls
ms.assetid: 85e79261-43e4-4770-bde0-1ff87f222b0f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 052e7ad2bfa8cc03c4eadd4926dbd84c4fd60223
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364314"
---
# <a name="caxwindow-class"></a>CAxWindow – třída
Tato třída poskytuje metody pro práci s okno hostování ovládacího prvku ActiveX.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CAxWindow : public CWindow
```  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[AttachControl](#attachcontrol)|Připojí existujícího ovládacího prvku ActiveX k `CAxWindow` objektu.|  
|[CAxWindow](#caxwindow)|Vytvoří `CAxWindow` objektu.|  
|[CreateControl –](#createcontrol)|Vytvoří ovládací prvek ActiveX, inicializuje ho a hostuje ji v `CAxWindow` okno.|  
|[CreateControlEx](#createcontrolex)|Vytvoří ovládacího prvku ActiveX a načte ukazatele rozhraní (nebo ukazatele) z ovládacího prvku.|  
|[GetWndClassName](#getwndclassname)|(Statické) Načte název předdefinované třídy `CAxWindow` objektu.|  
|[QueryControl](#querycontrol)|Načte **IUnknown** hostované ovládacího prvku ActiveX.|  
|[QueryHost](#queryhost)|Načte **IUnknown** ukazatel `CAxWindow` objektu.|  
|[SetExternalDispatch](#setexternaldispatch)|Nastaví rozhraní externí odesílání používané `CAxWindow` objektu.|  
|[SetExternalUIHandler](#setexternaluihandler)|Nastaví externí **IDocHostUIHandler** rozhraní používaných `CAxWindow` objektu.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operátor =](#operator_eq)|Přiřadí **HWND** na stávající **CAxWindow** objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída poskytuje metody pro práci s časového období, který je hostitelem ovládacího prvku ActiveX. Který je hostitelem zajišťuje " **AtlAxWin80"**, který je zabalen `CAxWindow`.  
  
 Třída `CAxWindow` je implementovaný jako specializace z `CAxWindowT` třídy. Tato specializace je deklarován jako:  
  
 `typedef CAxWindowT<CWindow> CAxWindow;`  
  
 Pokud potřebujete změnit základní třídy, můžete použít `CAxWindowT` a zadejte novou základní třídu pro argument šablony.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h  
  
##  <a name="attachcontrol"></a>  CAxWindow::AttachControl  
 Vytvoří nový objekt hostitele, pokud jeden už není přítomen a daný ovládací prvek připojí k hostiteli.  
  
```
HRESULT AttachControl(
    IUnknown* pControl,
    IUnknown** ppUnkContainer);
```  
  
### <a name="parameters"></a>Parametry  
 `pControl`  
 [v] Ukazatel **IUnknown** ovládacího prvku.  
  
 `ppUnkContainer`  
 [out] Ukazatel **IUnknown** hostitele ( **AxWin** objekt).  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Připojovaný objekt ovládacího prvku se musí správně inicializovat před voláním `AttachControl`.  
  
##  <a name="caxwindow"></a>  CAxWindow::CAxWindow  
 Vytvoří `CAxWindow` pomocí existující objekt popisovač okna.  
  
```
CAxWindow(HWND hWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `hWnd`  
 Popisovač pro existující objekt okno.  
  
##  <a name="createcontrol"></a>  CAxWindow::CreateControl  
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
 `lpszName`  
 Ukazatel na řetězec vytvoření ovládacího prvku. Musí být ve formátu v jednom z následujících způsobů:  
  
-   ProgID jako je například "MSCAL. Calendar.7 "  
  
-   CLSID, jako je například "{8E27C92B-1264-101C-8A2F-040224009C02}"  
  
-   Adresu URL, například "http://www.microsoft.com"  
  
-   Odkaz na aktivní dokument jako "file://\\\Documents\MyDoc.doc"  
  
-   Fragment HTML, například "MSHTML:\<HTML >\<textu > Toto je na řádku textu\</BODY > \< /HTML >"  
  
    > [!NOTE]
    >  "MSHTML:" musí předcházet HTML fragment, tak, aby je určený jako MSHTML datového proudu. V platformách systému Windows Mobile jsou podporované jenom ProgID a CLSID. Systém Windows CE vložených platformy, než Windows Mobile s podporou pro podporu CE IE všechny typy včetně ProgID, CLSID, adresa URL, odkaz na aktivní dokument a fragment HTML.  
  
 `pStream`  
 [v] Ukazatel na datový proud, který se používá k chybě při inicializaci vlastností ovládacího prvku. Může být **NULL**.  
  
 `ppUnkContainer`  
 [out] Adresu ukazatele, který se zobrazí **IUnknown** kontejneru. Může být **NULL**.  
  
 `dwResID`  
 ID prostředku prostředek HTML. Vytváření ovládacího prvku WebBrowser a načíst zadaný prostředek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Pokud se druhá verze tato metoda používá, se vytvoří a vázána na prostředek určený ovládací prvek jazyka HTML `dwResID`.  
  
 Tato metoda získáte stejný výsledek jako volání:  
  
 [!code-cpp[NVC_ATL_Windowing#42](../../atl/codesnippet/cpp/caxwindow-class_1.cpp)]  
  
 V tématu [CAxWindow2T::CreateControlLic](../../atl/reference/caxwindow2t-class.md#createcontrollic) k vytváření, inicializace a hostiteli licencovanou ovládacího prvku ActiveX.  
  
### <a name="example"></a>Příklad  
 V tématu [hostování ActiveX ovládacích prvků pomocí knihovny ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) příklad, který používá `CreateControl`.  
  
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
 `lpszName`  
 Ukazatel na řetězec vytvoření ovládacího prvku. Musí být ve formátu v jednom z následujících způsobů:  
  
-   ProgID jako je například "MSCAL. Calendar.7 "  
  
-   CLSID, jako je například "{8E27C92B-1264-101C-8A2F-040224009C02}"  
  
-   Adresu URL, například "http://www.microsoft.com"  
  
-   Odkaz na aktivní dokument jako "file://\\\Documents\MyDoc.doc"  
  
-   Fragment HTML, například "MSHTML:\<HTML >\<textu > Toto je na řádku textu\</BODY > \< /HTML >"  
  
    > [!NOTE]
    >  "MSHTML:" musí předcházet HTML fragment, tak, aby je určený jako MSHTML datového proudu. V platformách systému Windows Mobile jsou podporované jenom ProgID a CLSID. Systém Windows CE vložených platformy, než Windows Mobile s podporou pro podporu CE IE všechny typy včetně ProgID, CLSID, adresa URL, odkaz na aktivní dokument a fragment HTML.  
  
 `pStream`  
 [v] Ukazatel na datový proud, který se používá k chybě při inicializaci vlastností ovládacího prvku. Může být **NULL**.  
  
 `ppUnkContainer`  
 [out] Adresu ukazatele, který se zobrazí **IUnknown** kontejneru. Může být **NULL**.  
  
 `ppUnkControl`  
 [out] Adresu ukazatele, který se zobrazí **IUnknown** ovládacího prvku. Může být **NULL**.  
  
 `iidSink`  
 [v] Identifikátor rozhraní odchozí rozhraní na obsažený objekt. Může být **IID_NULL**.  
  
 *punkSink*  
 [v] Ukazatel **IUnknown** rozhraní podřízený objekt, který má být připojen k bodu připojení na obsažený objekt určeného `iidSink`.  
  
 `dwResID`  
 [v] ID prostředku prostředek HTML. Vytváření ovládacího prvku WebBrowser a načíst zadaný prostředek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je podobná [CAxWindow::CreateControl](#createcontrol), ale na rozdíl od dané metody `CreateControlEx` můžete taky přijímat ukazatele rozhraní do ovládacího prvku nově vytvořený a nastavení jímky událostí pro příjem událostí aktivováno pomocí ovládacího prvku.  
  
 V tématu [CAxWindow2T::CreateControlLicEx](../../atl/reference/caxwindow2t-class.md#createcontrollicex) k vytváření, inicializace a hostiteli licencovanou ovládacího prvku ActiveX.  
  
### <a name="example"></a>Příklad  
 V tématu [hostování ActiveX ovládacích prvků pomocí knihovny ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) příklad, který používá `CreateControlEx`.  
  
##  <a name="getwndclassname"></a>  CAxWindow::GetWndClassName  
 Načte název třídy oken.  
  
```
static LPCTSTR GetWndClassName();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na řetězec obsahující název třídy oken, který může hostovat nonlicensed ovládací prvky ActiveX.  
  
##  <a name="operator_eq"></a>  CAxWindow::operator =  
 Přiřadí `HWND` na stávající `CAxWindow` objektu.  
  
```
CAxWindow<TBase>& operator=(HWND hWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `hWnd`  
 Popisovač pro existujícího okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí odkaz na aktuální `CAxWindow` objektu.  
  
##  <a name="querycontrol"></a>  CAxWindow::QueryControl  
 Načte zadaný rozhraní hostované ovládacího prvku.  
  
```
HRESULT QueryControl(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryControl(Q** ppUnk);
```  
  
### <a name="parameters"></a>Parametry  
 `iid`  
 [v] Určuje identifikátory IID rozhraní ovládacího prvku.  
  
 `ppUnk`  
 [out] Ukazatel rozhraní ovládacího prvku. V šabloně verzi tuto metodu není třeba pro ID odkazu tak dlouho, dokud se předá typu rozhraní s přidružené UUID.  
  
 `Q`  
 [v] Rozhraní, který je dotazován na.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
##  <a name="queryhost"></a>  CAxWindow::QueryHost  
 Vrátí rozhraní zadaného hostitele.  
  
```
HRESULT QueryHost(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryHost(Q** ppUnk);
```  
  
### <a name="parameters"></a>Parametry  
 `iid`  
 [v] Určuje identifikátory IID rozhraní ovládacího prvku.  
  
 `ppUnk`  
 [out] Ukazatel rozhraní na hostiteli. V šabloně verzi tuto metodu není třeba pro ID odkazu tak dlouho, dokud se předá typu rozhraní s přidružené UUID.  
  
 `Q`  
 [v] Rozhraní, který je dotazován na.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní hostitele, které umožňuje přístup k základní funkce hostování okno kódu implementované **AxWin**.  
  
##  <a name="setexternaldispatch"></a>  CAxWindow::SetExternalDispatch  
 Nastaví odesílání externí rozhraní pro `CAxWindow` objektu.  
  
```
HRESULT SetExternalDispatch(IDispatch* pDisp);
```  
  
### <a name="parameters"></a>Parametry  
 `pDisp`  
 [v] Ukazatel na `IDispatch` rozhraní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
##  <a name="setexternaluihandler"></a>  CAxWindow::SetExternalUIHandler  
 Nastaví externí [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) rozhraní `CAxWindow` objektu.  
  
```
HRESULT SetExternalUIHandler(IDocHostUIHandlerDispatch* pUIHandler);
```  
  
### <a name="parameters"></a>Parametry  
 *pUIHandler*  
 [v] Ukazatel na **IDocHostUIHandlerDispatch** rozhraní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Externí `IDocHostUIHandlerDispatch` rozhraní používá ovládací prvky, které lokality hostitele pro dotazování `IDocHostUIHandlerDispatch` rozhraní. Ovládacího prvku WebBrowser je jeden ovládací prvek, který to.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka ATLCON](../../visual-cpp-samples.md)   
 [CWindow – třída](../../atl/reference/cwindow-class.md)   
 [Principy vytváření složených prvků](../../atl/atl-composite-control-fundamentals.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)   
 [Uzavření ovládacího prvku – nejčastější dotazy](../../atl/atl-control-containment-faq.md)

