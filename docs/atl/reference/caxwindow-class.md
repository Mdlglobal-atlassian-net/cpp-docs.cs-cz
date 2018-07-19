---
title: Caxwindow – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: b577e9ffdce651af1e8fcbec741ec259a37c65d6
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37880983"
---
# <a name="caxwindow-class"></a>Caxwindow – třída
Tato třída poskytuje metody pro práci s okno hostování ovládacího prvku ActiveX.  
  
> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CAxWindow : public CWindow
```  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[AttachControl](#attachcontrol)|Připojí existující ovládací prvek ActiveX `CAxWindow` objektu.|  
|[CAxWindow](#caxwindow)|Vytvoří `CAxWindow` objektu.|  
|[CreateControl](#createcontrol)|Vytvoří ovládací prvek ActiveX, inicializuje ji a hostuje ho `CAxWindow` okna.|  
|[CreateControlEx](#createcontrolex)|Vytvoří ovládací prvek ActiveX a načte ukazatel rozhraní (nebo ukazatele) z ovládacího prvku.|  
|[GetWndClassName](#getwndclassname)|(Statické) Načte název předdefinovaného třídy `CAxWindow` objektu.|  
|[QueryControl](#querycontrol)|Načte `IUnknown` hostovaného ovládacího prvku ActiveX.|  
|[QueryHost](#queryhost)|Načte `IUnknown` ukazatel `CAxWindow` objektu.|  
|[SetExternalDispatch](#setexternaldispatch)|Nastaví rozhraní externí odbavení používané `CAxWindow` objektu.|  
|[SetExternalUIHandler](#setexternaluihandler)|Nastaví externí `IDocHostUIHandler` rozhraní `CAxWindow` objektu.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operátor =](#operator_eq)|Přiřadí existující popisovačem HWND `CAxWindow` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída poskytuje metody pro práci, který je hostitelem okna ovládacího prvku ActiveX. Hostování je poskytován " **AtlAxWin80"**, která je zabalena `CAxWindow`.  
  
 Třída `CAxWindow` je implementovaný jako specializací `CAxWindowT` třídy. Tato specializace je deklarován jako:  
  
 `typedef CAxWindowT<CWindow> CAxWindow;`  
  
 Pokud potřebujete změnit základní třídy, můžete použít `CAxWindowT` a zadejte novou základní třídu jako argument šablony.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h  
  
##  <a name="attachcontrol"></a>  CAxWindow::AttachControl  
 Vytvoří nový objekt hostitele, pokud jeden není již k dispozici a připojí zadaný ovládací prvek k hostiteli.  
  
```
HRESULT AttachControl(
    IUnknown* pControl,
    IUnknown** ppUnkContainer);
```  
  
### <a name="parameters"></a>Parametry  
 *pControl*  
 [in] Ukazatel `IUnknown` ovládacího prvku.  
  
 *ppUnkContainer*  
 [out] Ukazatel `IUnknown` hostitele ( `AxWin` objekt).  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Připojovaný objekt ovládacího prvku musí být správně inicializován před voláním `AttachControl`.  
  
##  <a name="caxwindow"></a>  CAxWindow::CAxWindow  
 Vytvoří `CAxWindow` pomocí existujícího okna popisovač objektu.  
  
```
CAxWindow(HWND hWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *hWnd*  
 Popisovač na existující objekt okna.  
  
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
 *lpszName*  
 Ukazatel na řetězec vytvoření ovládacího prvku. Musí být ve formátu v jednom z následujících způsobů:  
  
-   ProgID jako je například "MSCAL. Calendar.7 "  
  
-   Identifikátor CLSID, jako je například "{8E27C92B-1264-101C-8A2F-040224009C02}"  
  
-   Adresa URL, jako "http://www.microsoft.com"  
  
-   Odkaz na aktivní dokument jako například "file://\\\Documents\MyDoc.doc"  
  
-   Fragment HTML, jako "MSHTML:\<HTML >\<text > to je řádek textu\</BODY > \< /HTML >"  
  
    > [!NOTE]
    >  "MSHTML:" musí předcházet HTML fragment, takže je určený jako proud MSHTML aplikace. Na platformách Windows Mobile jsou podporovány pouze ProgID a CLSID. Windows CE vložené platformy, než mobilní zařízení Windows s podporou pro podporu CE IE všechny typy včetně ProgID, CLSID, adresa URL, odkaz na aktivní dokument a fragment HTML.  
  
 *pStream*  
 [in] Ukazatel na datový proud, který slouží k inicializaci vlastnosti ovládacího prvku. Může mít hodnotu NULL.  
  
 *ppUnkContainer*  
 [out] Adresa ukazatel, který se zobrazí `IUnknown` kontejneru. Může mít hodnotu NULL.  
  
 *dwResID*  
 ID prostředku prostředek ve formátu HTML. Ovládací prvek WebBrowser bude vytvořena a načíst pomocí zadaného prostředku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Pokud použijete druhý verze tuto metodu, ovládací prvek je vytvořen a vázán na zdroj s identifikátorem *dwResID*.  
  
 Tato metoda poskytuje stejný výsledek jako volání funkce:  
  
 [!code-cpp[NVC_ATL_Windowing#42](../../atl/codesnippet/cpp/caxwindow-class_1.cpp)]  
  
 Zobrazit [CAxWindow2T::CreateControlLic](../../atl/reference/caxwindow2t-class.md#createcontrollic) k vytváření, inicializace a hostiteli licencovaného ovládacího prvku ActiveX.  
  
### <a name="example"></a>Příklad  
 Zobrazit [hostování ActiveX ovládacích prvků pomocí knihovny ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) ukázku, která používá `CreateControl`.  
  
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
 *lpszName*  
 Ukazatel na řetězec vytvoření ovládacího prvku. Musí být ve formátu v jednom z následujících způsobů:  
  
-   ProgID jako je například "MSCAL. Calendar.7 "  
  
-   Identifikátor CLSID, jako je například "{8E27C92B-1264-101C-8A2F-040224009C02}"  
  
-   Adresa URL, jako "http://www.microsoft.com"  
  
-   Odkaz na aktivní dokument jako například "file://\\\Documents\MyDoc.doc"  
  
-   Fragment HTML, jako "MSHTML:\<HTML >\<text > to je řádek textu\</BODY > \< /HTML >"  
  
    > [!NOTE]
    >  "MSHTML:" musí předcházet HTML fragment, takže je určený jako proud MSHTML aplikace. Na platformách Windows Mobile jsou podporovány pouze ProgID a CLSID. Windows CE vložené platformy, než mobilní zařízení Windows s podporou pro podporu CE IE všechny typy včetně ProgID, CLSID, adresa URL, odkaz na aktivní dokument a fragment HTML.  
  
 *pStream*  
 [in] Ukazatel na datový proud, který slouží k inicializaci vlastnosti ovládacího prvku. Může mít hodnotu NULL.  
  
 *ppUnkContainer*  
 [out] Adresa ukazatel, který se zobrazí `IUnknown` kontejneru. Může mít hodnotu NULL.  
  
 *ppUnkControl*  
 [out] Adresa ukazatel, který se zobrazí `IUnknown` ovládacího prvku. Může mít hodnotu NULL.  
  
 *iidSink*  
 [in] Identifikátor rozhraní odchozí rozhraní v obsažený objekt. Může mít hodnotu IID_NULL.  
  
 *punkSink*  
 [in] Ukazatel `IUnknown` rozhraní jímky objektu k připojení k bodu připojení na obsaženého objektu určeného *iidSink*.  
  
 *dwResID*  
 [in] ID prostředku prostředek ve formátu HTML. Ovládací prvek WebBrowser bude vytvořena a načíst pomocí zadaného prostředku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je podobný [CAxWindow::CreateControl](#createcontrol), ale na rozdíl od této metodě `CreateControlEx` také umožňuje přijímat ukazatel rozhraní na nově vytvořený ovládací prvek a nastavit jímky událostí přijímat události vyvolané ovládacího prvku.  
  
 Zobrazit [CAxWindow2T::CreateControlLicEx](../../atl/reference/caxwindow2t-class.md#createcontrollicex) k vytváření, inicializace a hostiteli licencovaného ovládacího prvku ActiveX.  
  
### <a name="example"></a>Příklad  
 Zobrazit [hostování ActiveX ovládacích prvků pomocí knihovny ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) ukázku, která používá `CreateControlEx`.  
  
##  <a name="getwndclassname"></a>  CAxWindow::GetWndClassName  
 Načte název třídy okna.  
  
```
static LPCTSTR GetWndClassName();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na řetězec obsahující název třídy okna, který může hostovat nonlicensed ovládací prvky ActiveX.  
  
##  <a name="operator_eq"></a>  CAxWindow::operator =  
 Přiřadí existující popisovačem HWND `CAxWindow` objektu.  
  
```
CAxWindow<TBase>& operator=(HWND hWnd);
```  
  
### <a name="parameters"></a>Parametry  
 *hWnd*  
 Popisovač k existujícímu oknu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí odkaz na aktuální `CAxWindow` objektu.  
  
##  <a name="querycontrol"></a>  CAxWindow::QueryControl  
 Načte zadaný rozhraní hostovaného ovládacího prvku.  
  
```
HRESULT QueryControl(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryControl(Q** ppUnk);
```  
  
### <a name="parameters"></a>Parametry  
 *identifikátor IID*  
 [in] Určuje identifikátor IID rozhraní ovládacího prvku.  
  
 *ppUnk*  
 [out] Ukazatel na rozhraní ovládacího prvku. V této metody na verzi šablony není nutné pro ID odkazu tak dlouho, dokud se předá zadané rozhraní s přidružený identifikátor UUID.  
  
 *Q*  
 [in] Rozhraní, která je dotazována pro.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnoty HRESULT.  
  
##  <a name="queryhost"></a>  CAxWindow::QueryHost  
 Vrátí rozhraní zadané hostitele.  
  
```
HRESULT QueryHost(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryHost(Q** ppUnk);
```  
  
### <a name="parameters"></a>Parametry  
 *identifikátor IID*  
 [in] Určuje identifikátor IID rozhraní ovládacího prvku.  
  
 *ppUnk*  
 [out] Ukazatel rozhraní na hostiteli. V této metody na verzi šablony není nutné pro ID odkazu tak dlouho, dokud se předá zadané rozhraní s přidružený identifikátor UUID.  
  
 *Q*  
 [in] Rozhraní, která je dotazována pro.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Umožňuje přístup k základní funkce okno hostování kódu, které jsou implementované rozhraní hostitele `AxWin`.  
  
##  <a name="setexternaldispatch"></a>  CAxWindow::SetExternalDispatch  
 Nastaví rozhraní externí odbavení pro `CAxWindow` objektu.  
  
```
HRESULT SetExternalDispatch(IDispatch* pDisp);
```  
  
### <a name="parameters"></a>Parametry  
 *pDisp*  
 [in] Ukazatel `IDispatch` rozhraní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnoty HRESULT.  
  
##  <a name="setexternaluihandler"></a>  CAxWindow::SetExternalUIHandler  
 Nastaví externí [idochostuihandlerdispatch –](../../atl/reference/idochostuihandlerdispatch-interface.md) rozhraní `CAxWindow` objektu.  
  
```
HRESULT SetExternalUIHandler(IDocHostUIHandlerDispatch* pUIHandler);
```  
  
### <a name="parameters"></a>Parametry  
 *pUIHandler*  
 [in] Ukazatel `IDocHostUIHandlerDispatch` rozhraní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Externí `IDocHostUIHandlerDispatch` rozhraní používá ovládací prvky, které se dotazují hostitelský server pro `IDocHostUIHandlerDispatch` rozhraní. Jeden ovládací prvek, který to je ovládací prvek WebBrowser.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka ATLCON](../../visual-cpp-samples.md)   
 [Cwindow – třída](../../atl/reference/cwindow-class.md)   
 [Principy vytváření složených prvků](../../atl/atl-composite-control-fundamentals.md)   
 [Přehled tříd](../../atl/atl-class-overview.md)   
 [Nejčastější dotazy k používání kontejnerů ovládacích prvků](../../atl/atl-control-containment-faq.md)

