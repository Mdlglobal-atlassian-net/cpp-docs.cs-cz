---
title: "Třída CD2DBitmapBrush | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::Attach
- AFXRENDERTARGET/CD2DBitmapBrush::Create
- AFXRENDERTARGET/CD2DBitmapBrush::Destroy
- AFXRENDERTARGET/CD2DBitmapBrush::Detach
- AFXRENDERTARGET/CD2DBitmapBrush::Get
- AFXRENDERTARGET/CD2DBitmapBrush::GetBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::GetExtendModeX
- AFXRENDERTARGET/CD2DBitmapBrush::GetExtendModeY
- AFXRENDERTARGET/CD2DBitmapBrush::GetInterpolationMode
- AFXRENDERTARGET/CD2DBitmapBrush::SetBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::SetExtendModeX
- AFXRENDERTARGET/CD2DBitmapBrush::SetExtendModeY
- AFXRENDERTARGET/CD2DBitmapBrush::SetInterpolationMode
- AFXRENDERTARGET/CD2DBitmapBrush::CommonInit
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmapBrushProperties
dev_langs: C++
helpviewer_keywords:
- CD2DBitmapBrush [MFC], CD2DBitmapBrush
- CD2DBitmapBrush [MFC], Attach
- CD2DBitmapBrush [MFC], Create
- CD2DBitmapBrush [MFC], Destroy
- CD2DBitmapBrush [MFC], Detach
- CD2DBitmapBrush [MFC], Get
- CD2DBitmapBrush [MFC], GetBitmap
- CD2DBitmapBrush [MFC], GetExtendModeX
- CD2DBitmapBrush [MFC], GetExtendModeY
- CD2DBitmapBrush [MFC], GetInterpolationMode
- CD2DBitmapBrush [MFC], SetBitmap
- CD2DBitmapBrush [MFC], SetExtendModeX
- CD2DBitmapBrush [MFC], SetExtendModeY
- CD2DBitmapBrush [MFC], SetInterpolationMode
- CD2DBitmapBrush [MFC], CommonInit
- CD2DBitmapBrush [MFC], m_pBitmap
- CD2DBitmapBrush [MFC], m_pBitmapBrush
- CD2DBitmapBrush [MFC], m_pBitmapBrushProperties
ms.assetid: 46ebbe34-66e0-44c8-af1d-d129e851de5e
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3dd588a26b73fb6e5f1b205b20f21aab8272c439
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cd2dbitmapbrush-class"></a>CD2DBitmapBrush – třída
Obálka pro ID2D1BitmapBrush.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CD2DBitmapBrush : public CD2DBrush;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DBitmapBrush::CD2DBitmapBrush](#cd2dbitmapbrush)|Přetíženo. Vytvoří objekt CD2DBitmapBrush ze souboru.|  
|[CD2DBitmapBrush:: ~ CD2DBitmapBrush](#dtor)|Destruktor. Voláno, když je zničen štětce objektu D2D rastrového obrázku.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DBitmapBrush::Attach](#attach)|Připojí existující prostředek rozhraní k objektu|  
|[CD2DBitmapBrush::Create](#create)|Vytvoří CD2DBitmapBrush. (Přepisuje [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|  
|[CD2DBitmapBrush::Destroy](#destroy)|Zničí CD2DBitmapBrush objektu. (Přepisuje [CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy).)|  
|[CD2DBitmapBrush::detach](#detach)|Umožňuje odpojit prostředek rozhraní z objektu|  
|[CD2DBitmapBrush::Get](#get)|Vrátí ID2D1BitmapBrush rozhraní|  
|[CD2DBitmapBrush::GetBitmap](#getbitmap)|Získá zdroj rastrový obrázek, který používá tento štětce k vyplnění|  
|[CD2DBitmapBrush::GetExtendModeX](#getextendmodex)|Získá metodu, pomocí kterého stopy vodorovně dlaždice těchto oblastí, které rozšiřují po jeho rastrového obrázku|  
|[CD2DBitmapBrush::GetExtendModeY](#getextendmodey)|Získá metodu, pomocí kterého stopy svisle dlaždice těchto oblastí, které rozšiřují po jeho rastrového obrázku|  
|[CD2DBitmapBrush::GetInterpolationMode](#getinterpolationmode)|Získá metodu interpolace použít, když je škálovat nebo otáčet rastrový obrázek štětce|  
|[CD2DBitmapBrush::SetBitmap](#setbitmap)|Určuje zdroj rastrový obrázek, který používá tento štětce k vyplnění|  
|[CD2DBitmapBrush::SetExtendModeX](#setextendmodex)|Určuje, jak stopy vodorovně dlaždice těchto oblastí, které rozšiřují po jeho rastrového obrázku|  
|[CD2DBitmapBrush::SetExtendModeY](#setextendmodey)|Určuje, jak stopy svisle dlaždice těchto oblastí, které rozšiřují po jeho rastrového obrázku|  
|[CD2DBitmapBrush::SetInterpolationMode](#setinterpolationmode)|Určuje režim interpolace použít, když je škálovat nebo otáčet rastrový obrázek štětce|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DBitmapBrush::CommonInit](#commoninit)|Inicializuje objekt|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DBitmapBrush::Operator ID2D1BitmapBrush *](#operator_id2d1bitmapbrush_star)|Vrátí ID2D1BitmapBrush rozhraní|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DBitmapBrush::m_pBitmap](#m_pbitmap)|Ukládá ukazatel na objekt CD2DBitmap.|  
|[CD2DBitmapBrush::m_pBitmapBrush](#m_pbitmapbrush)|Ukládá ukazatel na objekt ID2D1BitmapBrush.|  
|[CD2DBitmapBrush::m_pBitmapBrushProperties](#m_pbitmapbrushproperties)|Bitmap stopy vlastnosti.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
 `CD2DBitmapBrush`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxrendertarget.h  
  
##  <a name="dtor"></a>CD2DBitmapBrush:: ~ CD2DBitmapBrush  
 Destruktor. Voláno, když je zničen štětce objektu D2D rastrového obrázku.  
  
```  
virtual ~CD2DBitmapBrush();
```  
  
##  <a name="attach"></a>CD2DBitmapBrush::Attach  
 Připojí existující prostředek rozhraní k objektu  
  
```  
void Attach(ID2D1BitmapBrush* pResource);
```  
  
### <a name="parameters"></a>Parametry  
 `pResource`  
 Existující rozhraní prostředků. Nemůže mít hodnotu NULL  
  
##  <a name="cd2dbitmapbrush"></a>CD2DBitmapBrush::CD2DBitmapBrush  
 Vytvoří objekt CD2DBitmapBrush.  
  
```  
CD2DBitmapBrush(
    CRenderTarget* pParentTarget,  
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,  
    CD2DBrushProperties* pBrushProperties = NULL,  
    BOOL bAutoDestroy = TRUE);

 
CD2DBitmapBrush(
    CRenderTarget* pParentTarget,  
    UINT uiResID,  
    LPCTSTR lpszType = NULL,  
    CD2DSizeU sizeDest = CD2DSizeU(0, 0), 
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,  
    CD2DBrushProperties* pBrushProperties = NULL,  
    BOOL bAutoDestroy = TRUE);

 
CD2DBitmapBrush(
    CRenderTarget* pParentTarget,  
    LPCTSTR lpszImagePath,  
    CD2DSizeU sizeDest = CD2DSizeU(0, 0), 
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,  
    CD2DBrushProperties* pBrushProperties = NULL,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentTarget`  
 Ukazatel na cíl vykreslení.  
  
 `pBitmapBrushProperties`  
 Ukazatel na režimy rozšíření a režim interpolace štětce rastrového obrázku.  
  
 `pBrushProperties`  
 Ukazatel na krytí a transformace štětce.  
  
 `bAutoDestroy`  
 Označuje, že bude objekt zničí vlastník (pParentTarget).  
  
 `uiResID`  
 Číslo ID prostředku prostředku.  
  
 `lpszType`  
 Ukazatel na řetězec ukončené hodnotou null, který obsahuje typ prostředku.  
  
 `sizeDest`  
 Velikost cílového bitmapy.  
  
 `lpszImagePath`  
 Ukazatel na řetězec ukončené hodnotou null, který obsahuje název souboru.  
  
##  <a name="commoninit"></a>CD2DBitmapBrush::CommonInit  
 Inicializuje objekt  
  
```  
void CommonInit(D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties);
```  
  
### <a name="parameters"></a>Parametry  
 `pBitmapBrushProperties`  
 Ukazatel na stopy vlastnosti rastrového obrázku.  
  
##  <a name="create"></a>CD2DBitmapBrush::Create  
 Vytvoří CD2DBitmapBrush.  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `pRenderTarget`  
 Ukazatel na cíl vykreslení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí S_OK. Funkce HRESULT chybový kód.  
  
##  <a name="destroy"></a>CD2DBitmapBrush::Destroy  
 Zničí CD2DBitmapBrush objektu.  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>CD2DBitmapBrush::detach  
 Umožňuje odpojit prostředek rozhraní z objektu  
  
```  
ID2D1BitmapBrush* Detach();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel rozhraní odpojit prostředků.  
  
##  <a name="get"></a>CD2DBitmapBrush::Get  
 Vrátí ID2D1BitmapBrush rozhraní  
  
```  
ID2D1BitmapBrush* Get();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na rozhraní ID2D1BitmapBrush nebo hodnota NULL, pokud objekt dosud není inicializován.  
  
##  <a name="getbitmap"></a>CD2DBitmapBrush::GetBitmap  
 Získá zdroj rastrový obrázek, který používá tento štětce k vyplnění  
  
```  
CD2DBitmap* GetBitmap();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na objekt CD2DBitmap nebo hodnota NULL, pokud objekt dosud není inicializován.  
  
##  <a name="getextendmodex"></a>CD2DBitmapBrush::GetExtendModeX  
 Získá metodu, pomocí kterého stopy vodorovně dlaždice těchto oblastí, které rozšiřují po jeho rastrového obrázku  
  
```  
D2D1_EXTEND_MODE GetExtendModeX() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota, která určuje, jak stopy vodorovně dlaždice těchto oblastí, které rozšiřují po jeho rastrového obrázku  
  
##  <a name="getextendmodey"></a>CD2DBitmapBrush::GetExtendModeY  
 Získá metodu, pomocí kterého stopy svisle dlaždice těchto oblastí, které rozšiřují po jeho rastrového obrázku  
  
```  
D2D1_EXTEND_MODE GetExtendModeY() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota, která určuje, jak stopy svisle dlaždice těchto oblastí, které rozšiřují po jeho rastrového obrázku  
  
##  <a name="getinterpolationmode"></a>CD2DBitmapBrush::GetInterpolationMode  
 Získá metodu interpolace použít, když je škálovat nebo otáčet rastrový obrázek štětce  
  
```  
D2D1_BITMAP_INTERPOLATION_MODE GetInterpolationMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Metodu interpolace použít, když je škálovat nebo otáčet rastrový obrázek štětce  
  
##  <a name="m_pbitmap"></a>CD2DBitmapBrush::m_pBitmap  
 Ukládá ukazatel na objekt CD2DBitmap.  
  
```  
CD2DBitmap* m_pBitmap;  
```  
  
##  <a name="m_pbitmapbrush"></a>CD2DBitmapBrush::m_pBitmapBrush  
 Ukládá ukazatel na objekt ID2D1BitmapBrush.  
  
```  
ID2D1BitmapBrush* m_pBitmapBrush;  
```  
  
##  <a name="m_pbitmapbrushproperties"></a>CD2DBitmapBrush::m_pBitmapBrushProperties  
 Bitmap stopy vlastnosti.  
  
```  
D2D1_BITMAP_BRUSH_PROPERTIES* m_pBitmapBrushProperties;  
```  
  
##  <a name="operator_id2d1bitmapbrush_star"></a>CD2DBitmapBrush::Operator ID2D1BitmapBrush *  
 Vrátí ID2D1BitmapBrush rozhraní  
  
```  
operator ID2D1BitmapBrush*();
```   
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na rozhraní ID2D1BitmapBrush nebo hodnota NULL, pokud objekt dosud není inicializován.  
  
##  <a name="setbitmap"></a>CD2DBitmapBrush::SetBitmap  
 Určuje zdroj rastrový obrázek, který používá tento štětce k vyplnění  
  
```  
void SetBitmap(CD2DBitmap* pBitmap);
```  
  
### <a name="parameters"></a>Parametry  
 `pBitmap`  
 Zdroj bitové mapy používané štětce  
  
##  <a name="setextendmodex"></a>CD2DBitmapBrush::SetExtendModeX  
 Určuje, jak stopy vodorovně dlaždice těchto oblastí, které rozšiřují po jeho rastrového obrázku  
  
```  
void SetExtendModeX(D2D1_EXTEND_MODE extendModeX);
```  
  
### <a name="parameters"></a>Parametry  
 `extendModeX`  
 Hodnota, která určuje, jak stopy vodorovně dlaždice těchto oblastí, které rozšiřují po jeho rastrového obrázku  
  
##  <a name="setextendmodey"></a>CD2DBitmapBrush::SetExtendModeY  
 Určuje, jak stopy svisle dlaždice těchto oblastí, které rozšiřují po jeho rastrového obrázku  
  
```  
void SetExtendModeY(D2D1_EXTEND_MODE extendModeY);
```  
  
### <a name="parameters"></a>Parametry  
 `extendModeY`  
 Hodnota, která určuje, jak stopy svisle dlaždice těchto oblastí, které rozšiřují po jeho rastrového obrázku  
  
##  <a name="setinterpolationmode"></a>CD2DBitmapBrush::SetInterpolationMode  
 Určuje režim interpolace použít, když je škálovat nebo otáčet rastrový obrázek štětce  
  
```  
void SetInterpolationMode(D2D1_BITMAP_INTERPOLATION_MODE interpolationMode);
```  
  
### <a name="parameters"></a>Parametry  
 `interpolationMode`  
 Režim interpolace použít, když je škálovat nebo otáčet rastrový obrázek štětce  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
