---
title: "Třída COleDispatchDriver | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleDispatchDriver
- AFXDISP/COleDispatchDriver
- AFXDISP/COleDispatchDriver::COleDispatchDriver
- AFXDISP/COleDispatchDriver::AttachDispatch
- AFXDISP/COleDispatchDriver::CreateDispatch
- AFXDISP/COleDispatchDriver::DetachDispatch
- AFXDISP/COleDispatchDriver::GetProperty
- AFXDISP/COleDispatchDriver::InvokeHelper
- AFXDISP/COleDispatchDriver::ReleaseDispatch
- AFXDISP/COleDispatchDriver::SetProperty
- AFXDISP/COleDispatchDriver::m_bAutoRelease
- AFXDISP/COleDispatchDriver::m_lpDispatch
dev_langs:
- C++
helpviewer_keywords:
- COleDispatchDriver [MFC], COleDispatchDriver
- COleDispatchDriver [MFC], AttachDispatch
- COleDispatchDriver [MFC], CreateDispatch
- COleDispatchDriver [MFC], DetachDispatch
- COleDispatchDriver [MFC], GetProperty
- COleDispatchDriver [MFC], InvokeHelper
- COleDispatchDriver [MFC], ReleaseDispatch
- COleDispatchDriver [MFC], SetProperty
- COleDispatchDriver [MFC], m_bAutoRelease
- COleDispatchDriver [MFC], m_lpDispatch
ms.assetid: 3ed98daf-cdc7-4374-8a0c-cf695a8d3657
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 059ff922689eaf354d4b4ae9b89fb49ab8c5a885
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="coledispatchdriver-class"></a>COleDispatchDriver – třída
Implementuje OLE – automatizace na straně klienta.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleDispatchDriver  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[COleDispatchDriver::COleDispatchDriver](#coledispatchdriver)|Vytvoří `COleDispatchDriver` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleDispatchDriver::AttachDispatch](#attachdispatch)|Připojí `IDispatch` připojení k `COleDispatchDriver` objektu.|  
|[COleDispatchDriver::CreateDispatch](#createdispatch)|Vytvoří `IDispatch` připojení a připojí jej k `COleDispatchDriver` objektu.|  
|[COleDispatchDriver::DetachDispatch](#detachdispatch)|Umožňuje odpojit `IDispatch` připojení ho ukončil bez uvolnění.|  
|[COleDispatchDriver::GetProperty](#getproperty)|Získá vlastnost služby automation.|  
|[COleDispatchDriver::InvokeHelper](#invokehelper)|Pomocník pro volání metod automatizace.|  
|[COleDispatchDriver::ReleaseDispatch](#releasedispatch)|Verze `IDispatch` připojení.|  
|[COleDispatchDriver::SetProperty](#setproperty)|Nastaví vlastnost služby automation.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[COleDispatchDriver::operator =](#operator_eq)|Zkopíruje zdrojové hodnoty do `COleDispatchDriver` objektu.|  
|[COleDispatchDriver::operator LPDISPATCH](#operator_lpdispatch)|Přistupuje k základní `IDispatch` ukazatel.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[COleDispatchDriver::m_bAutoRelease](#m_bautorelease)|Určuje, jestli se k uvolnění `IDispatch` během `ReleaseDispatch` nebo odstranění objektu.|  
|[COleDispatchDriver::m_lpDispatch](#m_lpdispatch)|Označuje ukazatele myši `IDispatch` rozhraní připojených k tomuto `COleDispatchDriver`.|  
  
## <a name="remarks"></a>Poznámky  
 `COleDispatchDriver`nemá základní třídu.  
  
 OLE – rozhraní dispatch poskytnout přístup k metody a vlastnosti objektu. Členské funkce `COleDispatchDriver` připojení, odpojení, vytvořte a vydání odesílání připojení typu `IDispatch`. Použití jiné členské funkce seznamy argumentů proměnných ke zjednodušení volání **volání metody IDispatch::Invoke**.  
  
 Tato třída slouží přímo, ale obecně se používá pouze pomocí třídy vytvořený pomocí průvodce Přidat třídu. Když vytvoříte nové třídy C++ importováním knihovny typů, jsou nové třídy odvozené od `COleDispatchDriver`.  
  
 Další informace o používání `COleDispatchDriver`, najdete v následujících článcích:  
  
- [Klienti automatizace](../../mfc/automation-clients.md)  
  
- [Automatizační servery](../../mfc/automation-servers.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `COleDispatchDriver`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdisp.h  
  
##  <a name="attachdispatch"></a>COleDispatchDriver::AttachDispatch  
 Volání `AttachDispatch` – členská funkce pro připojení `IDispatch` ukazatel `COleDispatchDriver` objektu. Další informace najdete v tématu [implementace rozhraní IDispatch](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945).  
  
```  
void AttachDispatch(
        LPDISPATCH lpDispatch,  
        BOOL bAutoRelease = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `lpDispatch`  
 Ukazatel na OLE `IDispatch` objekt, který má být připojen k `COleDispatchDriver` objektu.  
  
 `bAutoRelease`  
 Určuje, zda odesílání se uvolní, když tento objekt je mimo rozsah.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce uvolní všechny `IDispatch` ukazatele, který je již připojen k `COleDispatchDriver` objektu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCOleContainer#3](../../mfc/codesnippet/cpp/coledispatchdriver-class_1.cpp)]  
  
##  <a name="coledispatchdriver"></a>COleDispatchDriver::COleDispatchDriver  
 Vytvoří `COleDispatchDriver` objektu.  
  
```  
COleDispatchDriver();  
COleDispatchDriver(LPDISPATCH lpDispatch, BOOL bAutoRelease = TRUE);  
  COleDispatchDriver(const COleDispatchDriver& dispatchSrc);
```  
  
### <a name="parameters"></a>Parametry  
 `lpDispatch`  
 Ukazatel na OLE `IDispatch` objekt, který má být připojen k `COleDispatchDriver` objektu.  
  
 `bAutoRelease`  
 Určuje, zda odesílání se uvolní, když tento objekt je mimo rozsah.  
  
 `dispatchSrc`  
 Odkaz na existující `COleDispatchDriver` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Formulář `COleDispatchDriver`( `LPDISPATCH lpDispatch`, **BOOL**`bAutoRelease` = **TRUE**) připojí [IDispatch](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945) rozhraní.  
  
 Formulář `COleDispatchDriver`( **const**`COleDispatchDriver`& `dispatchSrc`) zkopíruje existující `COleDispatchDriver` objektu a zvýší počet odkazů.  
  
 Formulář `COleDispatchDriver`() vytvoří `COleDispatchDriver` objektu, ale není `IDispatch` rozhraní. Před použitím `COleDispatchDriver`() bez argumentů, můžete připojit `IDispatch` se buď pomocí [COleDispatchDriver::CreateDispatch](#createdispatch) nebo [COleDispatchDriver::AttachDispatch](#attachdispatch). Další informace najdete v tématu [implementace rozhraní IDispatch](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945).  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [COleDispatchDriver::CreateDispatch](#createdispatch).  
  
##  <a name="createdispatch"></a>COleDispatchDriver::CreateDispatch  
 Vytvoří [IDispatch](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945) objekt rozhraní a připojí jej k `COleDispatchDriver` objektu.  
  
```  
BOOL CreateDispatch(
        REFCLSID clsid,  
        COleException* pError = NULL);

 
BOOL CreateDispatch(
    LPCTSTR lpszProgID,  
    COleException* pError = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `clsid`  
 ID třídy `IDispatch` objekt připojení, který se má vytvořit.  
  
 `pError`  
 Ukazatel na objekt výjimky OLE, který bude obsahovat kód stavu vyplývající z vytvoření.  
  
 `lpszProgID`  
 Ukazatel na programový identifikátor, jako je například "Excel.Document.5" automatizace objektu, pro kterou má být vytvořen objekt odeslání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCOleContainer#4](../../mfc/codesnippet/cpp/coledispatchdriver-class_2.cpp)]  
  
##  <a name="detachdispatch"></a>COleDispatchDriver::DetachDispatch  
 Odpojí aktuální `IDispatch` připojení z tohoto objektu.  
  
```  
LPDISPATCH DetachDispatch();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na dříve připojené OLE `IDispatch` objektu.  
  
### <a name="remarks"></a>Poznámky  
 `IDispatch` Se neuvolní.  
  
 Další informace o `LPDISPATCH` zadejte najdete v tématu [implementace rozhraní IDispatch](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCOleContainer#5](../../mfc/codesnippet/cpp/coledispatchdriver-class_3.cpp)]  
  
##  <a name="getproperty"></a>COleDispatchDriver::GetProperty  
 Získá vlastnost objektu určeného `dwDispID`.  
  
```  
void GetProperty(
    DISPID dwDispID,  
    VARTYPE vtProp,  
    void* pvProp) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `dwDispID`  
 Určuje vlastnost, která má být načtena.  
  
 `vtProp`  
 Určuje vlastnost, která má být načtena. Možné hodnoty, najdete v části poznámky pro [COleDispatchDriver::InvokeHelper](#invokehelper).  
  
 `pvProp`  
 Adresa proměnné, která se zobrazí hodnota vlastnosti. Musí se shodovat s typem zadaným ve `vtProp`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCOleContainer#6](../../mfc/codesnippet/cpp/coledispatchdriver-class_4.cpp)]  
  
##  <a name="invokehelper"></a>COleDispatchDriver::InvokeHelper  
 Volá metodu objekt nebo vlastnost určeného `dwDispID`, v rámci určeného `wFlags`.  
  
```  
void AFX_CDECL InvokeHelper(
        DISPID dwDispID,  
        WORD wFlags,  
        VARTYPE vtRet,  
        void* pvRet,  
        const BYTE* pbParamInfo, ...);
```  
  
### <a name="parameters"></a>Parametry  
 `dwDispID`  
 Určuje metodu nebo vlastnost, která má být volána.  
  
 `wFlags`  
 Příznaky popisující kontext volání **volání metody IDispatch::Invoke**. . Seznam možných hodnot najdete v tématu `wFlags` parametr v [volání metody IDispatch::Invoke](http://msdn.microsoft.com/library/windows/desktop/ms221479\(v=vs.85\).aspx) ve Windows SDK.  
  
 `vtRet`  
 Určuje typ vrácené hodnoty. Možné hodnoty najdete v části poznámky.  
  
 `pvRet`  
 Adresa proměnné, která bude přijímat hodnota vlastnosti nebo vrátit hodnotu. Musí se shodovat s typem zadaným ve `vtRet`.  
  
 `pbParamInfo`  
 Ukazatel na řetězce ukončené hodnotou null bajtů určení typů parametrů následující `pbParamInfo`.  
  
 *...*  
 Seznam proměnných parametrů typů zadaný v `pbParamInfo`.  
  
### <a name="remarks"></a>Poznámky  
 `pbParamInfo` Parametr určuje typy parametrů předaných pracovnímu metody nebo vlastnosti. Proměnné seznam argumentů je reprezentována **...**  v deklaraci syntaxe.  
  
 Možné hodnoty `vtRet` argument jsou převzaty z `VARENUM` výčtu. Možné hodnoty jsou následující:  
  
|Symbol|Návratový typ|  
|------------|-----------------|  
|`VT_EMPTY`|`void`|  
|`VT_I2`|**short**|  
|`VT_I4`|**long**|  
|`VT_R4`|**float**|  
|`VT_R8`|**double**|  
|`VT_CY`|**CY**|  
|`VT_DATE`|**DATUM**|  
|`VT_BSTR`|`BSTR`|  
|**VT_DISPATCH**|`LPDISPATCH`|  
|`VT_ERROR`|`SCODE`|  
|`VT_BOOL`|**BOOL**|  
|**VT_VARIANT**|**VARIANT**|  
|**HODNOTA VT_UNKNOWN**|`LPUNKNOWN`|  
  
 `pbParamInfo` Argument je seznam oddělených mezerami **VTS_** konstanty. Jeden nebo více z těchto hodnot, oddělené mezerami (ne čárkami), určuje seznam parametrů funkce. Možné hodnoty jsou uvedena s [event_custom –](event-maps.md#event_custom) makro.  
  
 Tato funkce převede parametry, které chcete **VARIANTARG** hodnoty a potom volá [volání metody IDispatch::Invoke](http://msdn.microsoft.com/library/windows/desktop/ms221479\(v=vs.85\).aspx) metoda. Pokud volání `Invoke` selže, tato funkce vyvolá výjimku. Pokud `SCODE` vrácený (kód stavu) **volání metody IDispatch::Invoke** je `DISP_E_EXCEPTION`, funkce vyvolá [COleException](../../mfc/reference/coleexception-class.md) objektu; jinak vyvolá [ COleDispatchException](../../mfc/reference/coledispatchexception-class.md).  
  
 Další informace najdete v tématu [VARIANTARG](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118), [implementace rozhraní IDispatch](http://msdn.microsoft.com/library/windows/desktop/ms221037\(v=vs.85\).aspx), [volání metody IDispatch::Invoke](http://msdn.microsoft.com/library/windows/desktop/ms221479\(v=vs.85\).aspx), a [struktura z COM kódy chyb](http://msdn.microsoft.com/library/windows/desktop/ms690088) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [COleDispatchDriver::CreateDispatch](#createdispatch).  
  
##  <a name="m_bautorelease"></a>COleDispatchDriver::m_bAutoRelease  
 Pokud **TRUE**, objekt COM [m_lpDispatch](#m_lpdispatch) budou automaticky vydané při [ReleaseDispatch](#releasedispatch) nazývá nebo pokud to `COleDispatchDriver` objekt způsobem zničena.  
  
```  
BOOL m_bAutoRelease;  
```  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení `m_bAutoRelease` je nastaven na **TRUE** v konstruktoru.  
  
 Další informace o uvolnění objektů COM najdete v tématu [implementace počítání odkazů](http://msdn.microsoft.com/library/windows/desktop/ms693431) a [IUnknown::Release](http://msdn.microsoft.com/library/windows/desktop/ms682317) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCOleContainer#9](../../mfc/codesnippet/cpp/coledispatchdriver-class_5.cpp)]  
  
##  <a name="m_lpdispatch"></a>COleDispatchDriver::m_lpDispatch  
 Ukazatele myši `IDispatch` rozhraní připojených k tomuto `COleDispatchDriver`.  
  
```  
LPDISPATCH m_lpDispatch;  
```  
  
### <a name="remarks"></a>Poznámky  
 `m_lpDispatch` – Datový člen je veřejné proměnné typu `LPDISPATCH`.  
  
 Další informace najdete v tématu [IDispatch](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [COleDispatchDriver::AttachDispatch](#attachdispatch).  
  
##  <a name="operator_eq"></a>COleDispatchDriver::operator =  
 Zkopíruje zdrojové hodnoty do `COleDispatchDriver` objektu.  
  
```  
const COleDispatchDriver& operator=(const COleDispatchDriver& dispatchSrc);
```  
  
### <a name="parameters"></a>Parametry  
 `dispatchSrc`  
 Ukazatele na existující `COleDispatchDriver` objektu.  
  
##  <a name="operator_lpdispatch"></a>COleDispatchDriver::operator LPDISPATCH  
 Přistupuje k základní `IDispatch` ukazatel `COleDispatchDriver` objektu.  
  
```  
operator LPDISPATCH();
```   
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCOleContainer#8](../../mfc/codesnippet/cpp/coledispatchdriver-class_6.cpp)]  
  
##  <a name="releasedispatch"></a>COleDispatchDriver::ReleaseDispatch  
 Verze `IDispatch` připojení. Další informace najdete v tématu [implementace rozhraní IDispatch](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945)  
  
```  
void ReleaseDispatch();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud automaticky verze byla nastavena pro toto připojení, tato funkce volá **IDispatch::Release** před uvolněním rozhraní.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [COleDispatchDriver::AttachDispatch](#attachdispatch).  
  
##  <a name="setproperty"></a>COleDispatchDriver::SetProperty  
 Nastaví vlastnost objektu OLE určeného `dwDispID`.  
  
```  
void AFX_CDECL SetProperty(
    DISPID dwDispID,  
    VARTYPE vtProp, ...);
```  
  
### <a name="parameters"></a>Parametry  
 `dwDispID`  
 Určuje vlastnost, která má být nastavena.  
  
 `vtProp`  
 Určuje typ vlastnosti, která má být nastavena. Možné hodnoty, najdete v části poznámky pro [COleDispatchDriver::InvokeHelper](#invokehelper).  
  
 *...*  
 Jeden parametr v typu zadaném pomocí `vtProp`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCOleContainer#7](../../mfc/codesnippet/cpp/coledispatchdriver-class_7.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC CALCDRIV](../../visual-cpp-samples.md)   
 [Ukázka MFC acdual –](../../visual-cpp-samples.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)
