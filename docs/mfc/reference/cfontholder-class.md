---
title: "Třída CFontHolder | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFontHolder
- AFXCTL/CFontHolder
- AFXCTL/CFontHolder::CFontHolder
- AFXCTL/CFontHolder::GetDisplayString
- AFXCTL/CFontHolder::GetFontDispatch
- AFXCTL/CFontHolder::GetFontHandle
- AFXCTL/CFontHolder::InitializeFont
- AFXCTL/CFontHolder::QueryTextMetrics
- AFXCTL/CFontHolder::ReleaseFont
- AFXCTL/CFontHolder::Select
- AFXCTL/CFontHolder::SetFont
- AFXCTL/CFontHolder::m_pFont
dev_langs: C++
helpviewer_keywords:
- CFontHolder [MFC], CFontHolder
- CFontHolder [MFC], GetDisplayString
- CFontHolder [MFC], GetFontDispatch
- CFontHolder [MFC], GetFontHandle
- CFontHolder [MFC], InitializeFont
- CFontHolder [MFC], QueryTextMetrics
- CFontHolder [MFC], ReleaseFont
- CFontHolder [MFC], Select
- CFontHolder [MFC], SetFont
- CFontHolder [MFC], m_pFont
ms.assetid: 728ab472-0c97-440d-889f-1324c6e1b6b8
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b7561c9765dcbead36335852d457568bd76b46e5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cfontholder-class"></a>CFontHolder – třída
Implementuje uložených vlastností písma a zapouzdřuje funkce Windows objektu písma a `IFont` rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CFontHolder  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CFontHolder::CFontHolder](#cfontholder)|Vytvoří `CFontHolder` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CFontHolder::GetDisplayString](#getdisplaystring)|Načte řetězec zobrazí v prohlížeči vlastností kontejneru.|  
|[CFontHolder::GetFontDispatch](#getfontdispatch)|Vrátí písma `IDispatch` rozhraní.|  
|[CFontHolder::GetFontHandle](#getfonthandle)|Vrátí popisovač písmo Windows.|  
|[CFontHolder::InitializeFont](#initializefont)|Inicializuje `CFontHolder` objektu.|  
|[CFontHolder::QueryTextMetrics](#querytextmetrics)|Načte informace pro související písmo.|  
|[CFontHolder::ReleaseFont](#releasefont)|Odpojí `CFontHolder` objektu z `IFont` a `IFontNotification` rozhraní.|  
|[CFontHolder::Select](#select)|Vybere písmo prostředků v kontextu zařízení.|  
|[CFontHolder::SetFont](#setfont)|Připojí `CFontHolder` do objektu `IFont` rozhraní.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CFontHolder::m_pFont](#m_pfont)|Ukazatel `CFontHolder` objektu `IFont` rozhraní.|  
  
## <a name="remarks"></a>Poznámky  
 `CFontHolder`nemá základní třídu.  
  
 Tato třída slouží k implementaci vlastnosti vlastní písma pro ovládací prvek. Informace o vytváření těchto vlastností najdete v článku [– ovládací prvky ActiveX: použití písem](../../mfc/mfc-activex-controls-using-fonts.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CFontHolder`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxctl.h  
  
##  <a name="cfontholder"></a>CFontHolder::CFontHolder  
 Vytvoří `CFontHolder` objektu.  
  
```  
explicit CFontHolder(LPPROPERTYNOTIFYSINK pNotify);
```  
  
### <a name="parameters"></a>Parametry  
 *pNotify*  
 Ukazatel na písma `IPropertyNotifySink` rozhraní.  
  
### <a name="remarks"></a>Poznámky  
 Je třeba volat `InitializeFont` před jeho použitím inicializovat výsledný objekt.  
  
##  <a name="getdisplaystring"></a>CFontHolder::GetDisplayString  
 Načte řetězec, který lze zobrazit v prohlížeči vlastností kontejneru.  
  
```  
BOOL GetDisplayString(CString& strValue);
```  
  
### <a name="parameters"></a>Parametry  
 `strValue`  
 Odkaz na [CString](../../atl-mfc-shared/reference/cstringt-class.md) , který má obsahovat řetězec zobrazení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud řetězec je úspěšně načetl; jinak 0.  
  
##  <a name="getfontdispatch"></a>CFontHolder::GetFontDispatch  
 Volání této funkce načíst ukazatel na rozhraní dispatch písma.  
  
```  
LPFONTDISP GetFontDispatch();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `CFontHolder` objektu **IFontDisp** rozhraní. Všimněte si, že funkce, která volá `GetFontDispatch` musí volat `IUnknown::Release` na tento ukazatel rozhraní po jeho dokončení.  
  
### <a name="remarks"></a>Poznámky  
 Volání `InitializeFont` před voláním `GetFontDispatch`.  
  
##  <a name="getfonthandle"></a>CFontHolder::GetFontHandle  
 Volání této funkce se získat popisovač pro Windows písmo.  
  
```  
HFONT GetFontHandle();

 
HFONT GetFontHandle(
    long cyLogical,  
    long cyHimetric);
```  
  
### <a name="parameters"></a>Parametry  
 `cyLogical`  
 Výška v logických jednotek, obdélníku, ve kterém se nevykreslí ovládacího prvku.  
  
 `cyHimetric`  
 Výška v `MM_HIMETRIC` jednotky ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro objekt písma; v opačném případě **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Poměr `cyLogical` a `cyHimetric` se používá k výpočtu velikost správné zobrazení v logické jednotky pro velikost písma v bodech vyjádřené v `MM_HIMETRIC` jednotky:  
  
 Zobrazí velikost = ( `cyLogical`  /  `cyHimetric`) X velikost písma  
  
 Verze bez parametrů vrátí popisovač písmo pro obrazovky správnou velikost.  
  
##  <a name="initializefont"></a>CFontHolder::InitializeFont  
 Inicializuje `CFontHolder` objektu.  
  
```  
void InitializeFont(
    const FONTDESC* pFontDesc = NULL,  
    LPDISPATCH pFontDispAmbient = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pFontDesc`  
 Ukazatel na strukturu popis písma ( [FONTDESC](http://msdn.microsoft.com/library/windows/desktop/ms692782)), který určuje vlastnosti písma.  
  
 `pFontDispAmbient`  
 Ukazatel na kontejneru vedlejším Font – vlastnost.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `pFontDispAmbient` není **NULL**, `CFontHolder` klon je připojen objekt `IFont` rozhraní používá kontejneru vedlejším Font – vlastnost.  
  
 Pokud `pFontDispAmbient` je **NULL**, buď z popis písma, na kterou odkazuje je vytvořen nový objekt písma `pFontDesc` nebo, pokud `pFontDesc` je **NULL**, z výchozí popis.  
  
 Po vytváření volání této funkce `CFontHolder` objektu.  
  
##  <a name="m_pfont"></a>CFontHolder::m_pFont  
 Ukazatel `CFontHolder` objektu `IFont` rozhraní.  
  
```  
LPFONT m_pFont;  
```  
  
##  <a name="querytextmetrics"></a>CFontHolder::QueryTextMetrics  
 Načte informace o fyzických písmo reprezentována `CFontHolder` objektu.  
  
```  
void QueryTextMetrics(LPTEXTMETRIC lptm);
```  
  
### <a name="parameters"></a>Parametry  
 `lptm`  
 Ukazatel [TEXTMETRIC](http://msdn.microsoft.com/library/windows/desktop/dd145132) struktura, která bude přijímat informace.  
  
##  <a name="releasefont"></a>CFontHolder::ReleaseFont  
 Tato funkce odpojí `CFontHolder` objekt z jeho `IFont` rozhraní.  
  
```  
void ReleaseFont();
```  
  
##  <a name="select"></a>CFontHolder::Select  
 Volání této funkce vyberte písma ovládacího prvku do kontextu zadané zařízení.  
  
```  
CFont* Select(
    CDC* pDC,  
    long cyLogical,  
    long cyHimetric);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Kontext zařízení, do kterého je vybrána písmo.  
  
 `cyLogical`  
 Výška v logických jednotek, obdélníku, ve kterém se nevykreslí ovládacího prvku.  
  
 `cyHimetric`  
 Výška v `MM_HIMETRIC` jednotky ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na písma, který se nahrazuje.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [GetFontHandle](#getfonthandle) diskuzi o `cyLogical` a `cyHimetric` parametry.  
  
##  <a name="setfont"></a>CFontHolder::SetFont  
 Uvolní všechny existující písma a připojí `CFontHolder` do objektu `IFont` rozhraní.  
  
```  
void SetFont(LPFONT pNewFont);
```  
  
### <a name="parameters"></a>Parametry  
 *pNewFont*  
 Ukazatel na nové `IFont` rozhraní.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CPropExchange – třída](../../mfc/reference/cpropexchange-class.md)
