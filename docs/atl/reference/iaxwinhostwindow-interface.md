---
title: "Rozhraní IAxWinHostWindow | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IAxWinHostWindow
- No header/ATL::IAxWinHostWindow
- No header/ATL::AttachControl
- No header/ATL::CreateControl
- No header/ATL::CreateControlEx
- No header/ATL::QueryControl
- No header/ATL::SetExternalDispatch
- No header/ATL::SetExternalUIHandler
dev_langs: C++
helpviewer_keywords: IAxWinHostWindow interface
ms.assetid: 9821c035-cd52-4c46-b58a-9278064f09b4
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 28fdc1a3a26fc2bb6117c345da3588ff0d2de193
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="iaxwinhostwindow-interface"></a>IAxWinHostWindow rozhraní
Toto rozhraní poskytuje metody pro manipulaci s ovládacího prvku a jeho objekt hostitele.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
interface IAxWinHostWindow : IUnknown
```  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[AttachControl](#attachcontrol)|Prvek připojí k objektu hostitele.|  
|[CreateControl –](#createcontrol)|Vytvoří ovládacího prvku a připojí jej k objektu hostitele.|  
|[CreateControlEx](#createcontrolex)|Vytvoří ovládací prvek, připojí k objektu hostitele a volitelně nastaví obslužnou rutinu události.|  
|[QueryControl](#querycontrol)|Vrátí ukazatele rozhraní do hostovaného ovládacího prvku.|  
|[SetExternalDispatch](#setexternaldispatch)|Nastaví externí `IDispatch` rozhraní.|  
|[SetExternalUIHandler](#setexternaluihandler)|Nastaví externí `IDocHostUIHandlerDispatch` rozhraní.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní je zveřejněný prostřednictvím ovládacího prvku ActiveX knihovny ATL pro hostování objekty. Volání metody na tomto rozhraní vytvořit nebo připojit ovládacího prvku k objektu hostitele, chcete-li získat rozhraní z ovládacího prvku hostované nebo nastavit externí dispinterface nebo obslužná rutina uživatelského rozhraní pro použití při hostování webového prohlížeče.  
  
## <a name="requirements"></a>Požadavky  
 Definice toto rozhraní je k dispozici jako IDL nebo C++, jak je uvedeno níže.  
  
|Definice typu|Soubor|  
|---------------------|----------|  
|IDL|ATLIFace.idl|  
|C++|ATLIFace.h (také obsaženy v ATLBase.h)|  
  
##  <a name="attachcontrol"></a>IAxWinHostWindow::AttachControl  
 Připojí ovládacího prvku existující (a dříve inicializovaného) k objektu hostitele pomocí okna identifikovaný `hWnd`.  
  
```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```  
  
### <a name="parameters"></a>Parametry  
 *pUnkControl*  
 [v] Ukazatel **IUnknown** rozhraní ovládacího prvku být připojen k objektu hostitele.  
  
 `hWnd`  
 [v] Obslužná rutina do okna má být použit pro hostování.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
##  <a name="createcontrol"></a>IAxWinHostWindow::CreateControl  
 Vytvoří ovládací prvek, inicializuje ji a hostuje v okně identifikovaný `hWnd`.  
  
```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```  
  
### <a name="parameters"></a>Parametry  
 `lpTricsData`  
 [v] Řetězec identifikující k vytvoření ovládacího prvku. Může být CLSID (musí zahrnovat složené závorky), ProgID, adresa URL nebo kód HTML (s předponou podle **MSHTML:**).  
  
 `hWnd`  
 [v] Obslužná rutina do okna má být použit pro hostování.  
  
 `pStream`  
 [v] Ukazatel rozhraní pro datový proud obsahující inicializační data pro ovládací prvek. Může být **NULL**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Toto okno se rozčlenění objektem hostitele vystavení toto rozhraní tak, aby se zprávy můžou odrážet do ovládacího prvku a další funkce kontejneru, budou fungovat.  
  
 Voláním této metody je ekvivalentní volání [IAxWinHostWindow::CreateControlEx](#createcontrolex).  
  
 Vytvořit licencované ovládací prvek ActiveX, najdete v části [IAxWinHostWindowLic::CreateControlLic](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex).  
  
##  <a name="createcontrolex"></a>IAxWinHostWindow::CreateControlEx  
 Vytvoří ovládací prvek ActiveX, inicializuje ji a hostuje v zadané okno podobné [IAxWinHostWindow::CreateControl](#createcontrol).  
  
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
 `lpTricsData`  
 [v] Řetězec identifikující k vytvoření ovládacího prvku. Může být CLSID (musí zahrnovat složené závorky), ProgID, adresa URL nebo kód HTML (s předponou **MSHTML:**).  
  
 `hWnd`  
 [v] Obslužná rutina do okna má být použit pro hostování.  
  
 `pStream`  
 [v] Ukazatel rozhraní pro datový proud obsahující inicializační data pro ovládací prvek. Může být **NULL**.  
  
 `ppUnk`  
 [out] Adresu ukazatele, který se zobrazí **IUnknown** rozhraní vytvořený ovládacího prvku. Může být **NULL**.  
  
 *riidAdvise*  
 [v] Identifikátor rozhraní odchozí rozhraní na obsažený objekt. Může být **IID_NULL**.  
  
 *punkAdvise*  
 [v] Ukazatel **IUnknown** rozhraní podřízený objekt, který má být připojen k bodu připojení na obsažený objekt určeného `iidSink`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Na rozdíl od `CreateControl` metody `CreateControlEx` můžete taky přijímat ukazatele rozhraní do ovládacího prvku nově vytvořený a nastavení jímky událostí pro příjem událostí aktivováno pomocí ovládacího prvku.  
  
 Vytvořit licencované ovládací prvek ActiveX, najdete v části [IAxWinHostWindowLic::CreateControlLicEx](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex).  
  
##  <a name="querycontrol"></a>IAxWinHostWindow::QueryControl  
 Vrátí ukazatel zadaný rozhraní poskytované hostovaného ovládacího prvku.  
  
```
STDMETHOD(QueryControl)(
    REFIID riid,
    void** ppvObject);
```  
  
### <a name="parameters"></a>Parametry  
 `riid`  
 [v] ID rozhraní na ovládací prvek požadováno.  
  
 `ppvObject`  
 [out] Adresa ukazatele, která bude přijímat specifikované rozhraní vytvořený ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
##  <a name="setexternaldispatch"></a>IAxWinHostWindow::SetExternalDispatch  
 Nastaví externí dispinterface, která je k dispozici prostřednictvím ovládacím prvkům obsažené [IDocHostUIHandlerDispatch::GetExternal](../../atl/reference/idochostuihandlerdispatch-interface.md) metoda.  
  
```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```  
  
### <a name="parameters"></a>Parametry  
 `pDisp`  
 [v] Ukazatel na `IDispatch` rozhraní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
##  <a name="setexternaluihandler"></a>IAxWinHostWindow::SetExternalUIHandler  
 Volání této funkce nastavit externí [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) rozhraní `CAxWindow` objektu.  
  
```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```  
  
### <a name="parameters"></a>Parametry  
 `pDisp`  
 [v] Ukazatel na **IDocHostUIHandlerDispatch** rozhraní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce používá ovládací prvky (například ovládacího prvku webového prohlížeče), které lokality hostitele pro dotazování `IDocHostUIHandlerDispatch` rozhraní.  
  
## <a name="see-also"></a>Viz také  
 [IAxWinAmbientDispatch rozhraní](../../atl/reference/iaxwinambientdispatch-interface.md)   
 [CAxWindow::QueryHost](../../atl/reference/caxwindow-class.md#queryhost)   
 [AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)









