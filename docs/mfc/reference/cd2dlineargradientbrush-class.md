---
title: "Třída CD2DLinearGradientBrush | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush::CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush::Attach
- AFXRENDERTARGET/CD2DLinearGradientBrush::Create
- AFXRENDERTARGET/CD2DLinearGradientBrush::Destroy
- AFXRENDERTARGET/CD2DLinearGradientBrush::Detach
- AFXRENDERTARGET/CD2DLinearGradientBrush::Get
- AFXRENDERTARGET/CD2DLinearGradientBrush::GetEndPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::GetStartPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::SetEndPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::SetStartPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::m_LinearGradientBrushProperties
- AFXRENDERTARGET/CD2DLinearGradientBrush::m_pLinearGradientBrush
dev_langs: C++
helpviewer_keywords:
- CD2DLinearGradientBrush [MFC], CD2DLinearGradientBrush
- CD2DLinearGradientBrush [MFC], Attach
- CD2DLinearGradientBrush [MFC], Create
- CD2DLinearGradientBrush [MFC], Destroy
- CD2DLinearGradientBrush [MFC], Detach
- CD2DLinearGradientBrush [MFC], Get
- CD2DLinearGradientBrush [MFC], GetEndPoint
- CD2DLinearGradientBrush [MFC], GetStartPoint
- CD2DLinearGradientBrush [MFC], SetEndPoint
- CD2DLinearGradientBrush [MFC], SetStartPoint
- CD2DLinearGradientBrush [MFC], m_LinearGradientBrushProperties
- CD2DLinearGradientBrush [MFC], m_pLinearGradientBrush
ms.assetid: d4be9ff9-0ea8-45e6-9b8d-f3bc5673cbac
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 19c060c846d8dfd12a8b783f0b01153c9a424cfe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cd2dlineargradientbrush-class"></a>CD2DLinearGradientBrush – třída
Obálka pro ID2D1LinearGradientBrush.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CD2DLinearGradientBrush : public CD2DGradientBrush;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DLinearGradientBrush::CD2DLinearGradientBrush](#cd2dlineargradientbrush)|Vytvoří objekt CD2DLinearGradientBrush.|  
|[CD2DLinearGradientBrush:: ~ CD2DLinearGradientBrush](#_dtorcd2dlineargradientbrush)|Destruktor. Voláno, když je objekt D2D lineární štětce přechodu zničen.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DLinearGradientBrush::Attach](#attach)|Připojí existující prostředek rozhraní k objektu|  
|[CD2DLinearGradientBrush::Create](#create)|Vytvoří CD2DLinearGradientBrush. (Přepisuje [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|  
|[CD2DLinearGradientBrush::Destroy](#destroy)|Zničí CD2DLinearGradientBrush objektu. (Přepisuje [CD2DGradientBrush::Destroy](../../mfc/reference/cd2dgradientbrush-class.md#destroy).)|  
|[CD2DLinearGradientBrush::detach](#detach)|Umožňuje odpojit prostředek rozhraní z objektu|  
|[CD2DLinearGradientBrush::Get](#get)|Vrátí ID2D1LinearGradientBrush rozhraní|  
|[CD2DLinearGradientBrush::GetEndPoint](#getendpoint)|Načte koncová souřadnice lineárního přechodu|  
|[CD2DLinearGradientBrush::GetStartPoint](#getstartpoint)|Načte výchozí souřadnice lineárního přechodu|  
|[CD2DLinearGradientBrush::SetEndPoint](#setendpoint)|Nastaví koncovou souřadnice lineárního přechodu v souřadnicového prostoru štětce|  
|[CD2DLinearGradientBrush::SetStartPoint](#setstartpoint)|Nastaví počáteční souřadnice lineárního přechodu v souřadnicového prostoru štětce|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DLinearGradientBrush::Operator ID2D1LinearGradientBrush *](#operator_id2d1lineargradientbrush_star)|Vrátí ID2D1LinearGradientBrush rozhraní|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DLinearGradientBrush::m_LinearGradientBrushProperties](#m_lineargradientbrushproperties)|Počáteční a koncové body barevného přechodu.|  
|[CD2DLinearGradientBrush::m_pLinearGradientBrush](#m_plineargradientbrush)|Ukazatel ID2D1LinearGradientBrush.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
 [CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)  
  
 `CD2DLinearGradientBrush`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxrendertarget.h  
  
##  <a name="_dtorcd2dlineargradientbrush"></a>CD2DLinearGradientBrush:: ~ CD2DLinearGradientBrush  
 Destruktor. Voláno, když je objekt D2D lineární štětce přechodu zničen.  
  
```  
virtual ~CD2DLinearGradientBrush();
```  
  
##  <a name="attach"></a>CD2DLinearGradientBrush::Attach  
 Připojí existující prostředek rozhraní k objektu  
  
```  
void Attach(ID2D1LinearGradientBrush* pResource);
```  
  
### <a name="parameters"></a>Parametry  
 `pResource`  
 Existující rozhraní prostředků. Nemůže mít hodnotu NULL  
  
##  <a name="cd2dlineargradientbrush"></a>CD2DLinearGradientBrush::CD2DLinearGradientBrush  
 Vytvoří objekt CD2DLinearGradientBrush.  
  
```  
CD2DLinearGradientBrush(
    CRenderTarget* pParentTarget,  
    const D2D1_GRADIENT_STOP* gradientStops,  
    UINT gradientStopsCount,  
    D2D1_LINEAR_GRADIENT_BRUSH_PROPERTIES LinearGradientBrushProperties,  
    D2D1_GAMMA colorInterpolationGamma = D2D1_GAMMA_2_2,  
    D2D1_EXTEND_MODE extendMode = D2D1_EXTEND_MODE_CLAMP,  
    CD2DBrushProperties* pBrushProperties = NULL,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentTarget`  
 Ukazatel na cíl vykreslení.  
  
 `gradientStops`  
 Ukazatel na pole D2D1_GRADIENT_STOP struktury.  
  
 `gradientStopsCount`  
 Hodnota větší než nebo rovna 1, která určuje počet Přechodové zarážky v poli gradientStops.  
  
 `LinearGradientBrushProperties`  
 Počáteční a koncové body barevného přechodu.  
  
 `colorInterpolationGamma`  
 Místo, na které barevně se provádí interpolace mezi Přechodové zarážky.  
  
 `extendMode`  
 Chování přechodu mimo normalizovaný rozsah [0, 1].  
  
 `pBrushProperties`  
 Ukazatel na krytí a transformace štětce.  
  
 `bAutoDestroy`  
 Označuje, že bude objekt zničí vlastník (pParentTarget).  
  
##  <a name="create"></a>CD2DLinearGradientBrush::Create  
 Vytvoří CD2DLinearGradientBrush.  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `pRenderTarget`  
 Ukazatel na cíl vykreslení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí S_OK. Funkce HRESULT chybový kód.  
  
##  <a name="destroy"></a>CD2DLinearGradientBrush::Destroy  
 Zničí CD2DLinearGradientBrush objektu.  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>CD2DLinearGradientBrush::detach  
 Umožňuje odpojit prostředek rozhraní z objektu  
  
```  
ID2D1LinearGradientBrush* Detach();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel rozhraní odpojit prostředků.  
  
##  <a name="get"></a>CD2DLinearGradientBrush::Get  
 Vrátí ID2D1LinearGradientBrush rozhraní  
  
```  
ID2D1LinearGradientBrush* Get();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na rozhraní ID2D1LinearGradientBrush nebo hodnota NULL, pokud objekt dosud není inicializován.  
  
##  <a name="getendpoint"></a>CD2DLinearGradientBrush::GetEndPoint  
 Načte koncová souřadnice lineárního přechodu  
  
```  
CD2DPointF GetEndPoint() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Koncová dvourozměrná souřadnice lineárního přechodu v souřadnicového prostoru štětce  
  
##  <a name="getstartpoint"></a>CD2DLinearGradientBrush::GetStartPoint  
 Načte výchozí souřadnice lineárního přechodu  
  
```  
CD2DPointF GetStartPoint() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počáteční dvourozměrná souřadnice lineárního přechodu v souřadnicového prostoru štětce  
  
##  <a name="m_lineargradientbrushproperties"></a>CD2DLinearGradientBrush::m_LinearGradientBrushProperties  
 Počáteční a koncové body barevného přechodu.  
  
```  
D2D1_LINEAR_GRADIENT_BRUSH_PROPERTIES m_LinearGradientBrushProperties;  
```  
  
##  <a name="m_plineargradientbrush"></a>CD2DLinearGradientBrush::m_pLinearGradientBrush  
 Ukazatel ID2D1LinearGradientBrush.  
  
```  
ID2D1LinearGradientBrush* m_pLinearGradientBrush;  
```  
  
##  <a name="operator_id2d1lineargradientbrush_star"></a>CD2DLinearGradientBrush::Operator ID2D1LinearGradientBrush *  
 Vrátí ID2D1LinearGradientBrush rozhraní  
  
```  
operator ID2D1LinearGradientBrush*();
```   
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na rozhraní ID2D1LinearGradientBrush nebo hodnota NULL, pokud objekt dosud není inicializován.  
  
##  <a name="setendpoint"></a>CD2DLinearGradientBrush::SetEndPoint  
 Nastaví koncovou souřadnice lineárního přechodu v souřadnicového prostoru štětce  
  
```  
void SetEndPoint(CD2DPointF point);
```  
  
### <a name="parameters"></a>Parametry  
 `point`  
 Koncová dvourozměrná souřadnice lineárního přechodu v souřadnicového prostoru štětce  
  
##  <a name="setstartpoint"></a>CD2DLinearGradientBrush::SetStartPoint  
 Nastaví počáteční souřadnice lineárního přechodu v souřadnicového prostoru štětce  
  
```  
void SetStartPoint(CD2DPointF point);
```  
  
### <a name="parameters"></a>Parametry  
 `point`  
 Počáteční dvourozměrná souřadnice lineárního přechodu v souřadnicového prostoru štětce  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
