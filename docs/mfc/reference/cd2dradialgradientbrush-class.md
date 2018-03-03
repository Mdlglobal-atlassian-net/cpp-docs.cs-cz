---
title: "Třída CD2DRadialGradientBrush | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::Attach
- AFXRENDERTARGET/CD2DRadialGradientBrush::Create
- AFXRENDERTARGET/CD2DRadialGradientBrush::Destroy
- AFXRENDERTARGET/CD2DRadialGradientBrush::Detach
- AFXRENDERTARGET/CD2DRadialGradientBrush::Get
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetCenter
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetGradientOriginOffset
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetRadiusX
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetRadiusY
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetCenter
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetGradientOriginOffset
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetRadiusX
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetRadiusY
- AFXRENDERTARGET/CD2DRadialGradientBrush::m_pRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::m_RadialGradientBrushProperties
dev_langs:
- C++
helpviewer_keywords:
- CD2DRadialGradientBrush [MFC], CD2DRadialGradientBrush
- CD2DRadialGradientBrush [MFC], Attach
- CD2DRadialGradientBrush [MFC], Create
- CD2DRadialGradientBrush [MFC], Destroy
- CD2DRadialGradientBrush [MFC], Detach
- CD2DRadialGradientBrush [MFC], Get
- CD2DRadialGradientBrush [MFC], GetCenter
- CD2DRadialGradientBrush [MFC], GetGradientOriginOffset
- CD2DRadialGradientBrush [MFC], GetRadiusX
- CD2DRadialGradientBrush [MFC], GetRadiusY
- CD2DRadialGradientBrush [MFC], SetCenter
- CD2DRadialGradientBrush [MFC], SetGradientOriginOffset
- CD2DRadialGradientBrush [MFC], SetRadiusX
- CD2DRadialGradientBrush [MFC], SetRadiusY
- CD2DRadialGradientBrush [MFC], m_pRadialGradientBrush
- CD2DRadialGradientBrush [MFC], m_RadialGradientBrushProperties
ms.assetid: 6c76d84a-d831-4ee2-96f1-82c1f5b0d6a9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8cdac3e2d2df31840ae90b79755b68d916033990
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cd2dradialgradientbrush-class"></a>CD2DRadialGradientBrush – třída
Obálka pro ID2D1RadialGradientBrush.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CD2DRadialGradientBrush : public CD2DGradientBrush;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DRadialGradientBrush::CD2DRadialGradientBrush](#cd2dradialgradientbrush)|Vytvoří objekt CD2DLinearGradientBrush.|  
|[CD2DRadialGradientBrush:: ~ CD2DRadialGradientBrush](#_dtorcd2dradialgradientbrush)|Destruktor. Voláno, když je objekt D2D paprskového štětce přechodu zničen.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DRadialGradientBrush::Attach](#attach)|Připojí existující prostředek rozhraní k objektu|  
|[CD2DRadialGradientBrush::Create](#create)|Vytvoří CD2DRadialGradientBrush. (Přepisuje [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|  
|[CD2DRadialGradientBrush::Destroy](#destroy)|Zničí CD2DRadialGradientBrush objektu. (Přepisuje [CD2DGradientBrush::Destroy](../../mfc/reference/cd2dgradientbrush-class.md#destroy).)|  
|[CD2DRadialGradientBrush::detach](#detach)|Umožňuje odpojit prostředek rozhraní z objektu|  
|[CD2DRadialGradientBrush::Get](#get)|Vrátí ID2D1RadialGradientBrush rozhraní|  
|[CD2DRadialGradientBrush::GetCenter](#getcenter)|Načte středu se třemi tečkami přechodu|  
|[CD2DRadialGradientBrush::GetGradientOriginOffset](#getgradientoriginoffset)|Načte posun přechodu původu relativně k přechodu elipsy center|  
|[CD2DRadialGradientBrush::GetRadiusX](#getradiusx)|Načte x-radius se třemi tečkami přechodu|  
|[CD2DRadialGradientBrush::GetRadiusY](#getradiusy)|Načte y-radius se třemi tečkami přechodu|  
|[CD2DRadialGradientBrush::SetCenter](#setcenter)|Určuje center přechodu elipsy v souřadnicového prostoru štětce|  
|[CD2DRadialGradientBrush::SetGradientOriginOffset](#setgradientoriginoffset)|Určuje posun přechodu původu relativně k přechodu elipsy center|  
|[CD2DRadialGradientBrush::SetRadiusX](#setradiusx)|Určuje x-radius se třemi tečkami přechodu v souřadnicového prostoru štětce|  
|[CD2DRadialGradientBrush::SetRadiusY](#setradiusy)|Určuje y-radius se třemi tečkami přechodu v souřadnicového prostoru štětce|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DRadialGradientBrush::Operator ID2D1RadialGradientBrush *](#operator_id2d1radialgradientbrush_star)|Vrátí ID2D1RadialGradientBrush rozhraní|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DRadialGradientBrush::m_pRadialGradientBrush](#m_pradialgradientbrush)|Ukazatel ID2D1RadialGradientBrush.|  
|[CD2DRadialGradientBrush::m_RadialGradientBrushProperties](#m_radialgradientbrushproperties)|Center, přechodu počátek posunu a x radius a y-radius štětce je přechodu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
 [CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)  
  
 `CD2DRadialGradientBrush`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxrendertarget.h  
  
##  <a name="_dtorcd2dradialgradientbrush"></a>CD2DRadialGradientBrush:: ~ CD2DRadialGradientBrush  
 Destruktor. Voláno, když je objekt D2D paprskového štětce přechodu zničen.  
  
```  
virtual ~CD2DRadialGradientBrush();
```  
  
##  <a name="attach"></a>CD2DRadialGradientBrush::Attach  
 Připojí existující prostředek rozhraní k objektu  
  
```  
void Attach(ID2D1RadialGradientBrush* pResource);
```  
  
### <a name="parameters"></a>Parametry  
 `pResource`  
 Existující rozhraní prostředků. Nemůže mít hodnotu NULL  
  
##  <a name="cd2dradialgradientbrush"></a>CD2DRadialGradientBrush::CD2DRadialGradientBrush  
 Vytvoří objekt CD2DLinearGradientBrush.  
  
```  
CD2DRadialGradientBrush(
    CRenderTarget* pParentTarget,  
    const D2D1_GRADIENT_STOP* gradientStops,  
    UINT gradientStopsCount,  
    D2D1_RADIAL_GRADIENT_BRUSH_PROPERTIES RadialGradientBrushProperties,  
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
  
 `RadialGradientBrushProperties`  
 Center, přechodu počátek posunu a x radius a y-radius štětce je přechodu.  
  
 `colorInterpolationGamma`  
 Místo, na které barevně se provádí interpolace mezi Přechodové zarážky.  
  
 `extendMode`  
 Chování přechodu mimo normalizovaný rozsah [0, 1].  
  
 `pBrushProperties`  
 Ukazatel na krytí a transformace štětce.  
  
 `bAutoDestroy`  
 Označuje, že bude objekt zničí vlastník (pParentTarget).  
  
##  <a name="create"></a>CD2DRadialGradientBrush::Create  
 Vytvoří CD2DRadialGradientBrush.  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `pRenderTarget`  
 Ukazatel na cíl vykreslení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí S_OK. Funkce HRESULT chybový kód.  
  
##  <a name="destroy"></a>CD2DRadialGradientBrush::Destroy  
 Zničí CD2DRadialGradientBrush objektu.  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>CD2DRadialGradientBrush::detach  
 Umožňuje odpojit prostředek rozhraní z objektu  
  
```  
ID2D1RadialGradientBrush* Detach();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel rozhraní odpojit prostředků.  
  
##  <a name="get"></a>CD2DRadialGradientBrush::Get  
 Vrátí ID2D1RadialGradientBrush rozhraní  
  
```  
ID2D1RadialGradientBrush* Get();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na rozhraní ID2D1RadialGradientBrush nebo hodnota NULL, pokud objekt dosud není inicializován.  
  
##  <a name="getcenter"></a>CD2DRadialGradientBrush::GetCenter  
 Načte středu se třemi tečkami přechodu  
  
```  
CD2DPointF GetCenter() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Center se třemi tečkami přechodu. Tato hodnota je vyjádřena v souřadnicového prostoru štětce  
  
##  <a name="getgradientoriginoffset"></a>CD2DRadialGradientBrush::GetGradientOriginOffset  
 Načte posun přechodu původu relativně k přechodu elipsy center  
  
```  
CD2DPointF GetGradientOriginOffset() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Posun přechodu původu z centra přechodu elipsy. Tato hodnota je vyjádřena v souřadnicového prostoru štětce  
  
##  <a name="getradiusx"></a>CD2DRadialGradientBrush::GetRadiusX  
 Načte x-radius se třemi tečkami přechodu  
  
```  
FLOAT GetRadiusX() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 X-radius se třemi tečkami přechodu. Tato hodnota je vyjádřena v souřadnicového prostoru štětce  
  
##  <a name="getradiusy"></a>CD2DRadialGradientBrush::GetRadiusY  
 Načte y-radius se třemi tečkami přechodu  
  
```  
FLOAT GetRadiusY() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Y-radius se třemi tečkami přechodu. Tato hodnota je vyjádřena v souřadnicového prostoru štětce  
  
##  <a name="m_pradialgradientbrush"></a>CD2DRadialGradientBrush::m_pRadialGradientBrush  
 Ukazatel ID2D1RadialGradientBrush.  
  
```  
ID2D1RadialGradientBrush* m_pRadialGradientBrush;  
```  
  
##  <a name="m_radialgradientbrushproperties"></a>CD2DRadialGradientBrush::m_RadialGradientBrushProperties  
 Center, přechodu počátek posunu a x radius a y-radius štětce je přechodu.  
  
```  
D2D1_RADIAL_GRADIENT_BRUSH_PROPERTIES m_RadialGradientBrushProperties;  
```  
  
##  <a name="operator_id2d1radialgradientbrush_star"></a>CD2DRadialGradientBrush::Operator ID2D1RadialGradientBrush *  
 Vrátí ID2D1RadialGradientBrush rozhraní  
  
```  
operator ID2D1RadialGradientBrush*();
```   
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na rozhraní ID2D1RadialGradientBrush nebo hodnota NULL, pokud objekt dosud není inicializován.  
  
##  <a name="setcenter"></a>CD2DRadialGradientBrush::SetCenter  
 Určuje center přechodu elipsy v souřadnicového prostoru štětce  
  
```  
void SetCenter(CD2DPointF point);
```  
  
### <a name="parameters"></a>Parametry  
 `point`  
 Center přechodu elipsy v souřadnicového prostoru štětce  
  
##  <a name="setgradientoriginoffset"></a>CD2DRadialGradientBrush::SetGradientOriginOffset  
 Určuje posun přechodu původu relativně k přechodu elipsy center  
  
```  
void SetGradientOriginOffset(CD2DPointF gradientOriginOffset);
```  
  
### <a name="parameters"></a>Parametry  
 `gradientOriginOffset`  
 Posun přechodu původu z centra přechodu třemi tečkami  
  
##  <a name="setradiusx"></a>CD2DRadialGradientBrush::SetRadiusX  
 Určuje x-radius se třemi tečkami přechodu v souřadnicového prostoru štětce  
  
```  
void SetRadiusX(FLOAT radiusX);
```  
  
### <a name="parameters"></a>Parametry  
 `radiusX`  
 X-radius se třemi tečkami přechodu. Tato hodnota je v prostoru souřadnic štětce  
  
##  <a name="setradiusy"></a>CD2DRadialGradientBrush::SetRadiusY  
 Určuje y-radius se třemi tečkami přechodu v souřadnicového prostoru štětce  
  
```  
void SetRadiusY(FLOAT radiusY);
```  
  
### <a name="parameters"></a>Parametry  
 `radiusY`  
 Y-radius se třemi tečkami přechodu. Tato hodnota je v prostoru souřadnic štětce  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
