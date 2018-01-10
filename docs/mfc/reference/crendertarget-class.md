---
title: "Třída CRenderTarget | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRenderTarget
- AFXRENDERTARGET/CRenderTarget
- AFXRENDERTARGET/CRenderTarget::CRenderTarget
- AFXRENDERTARGET/CRenderTarget::Attach
- AFXRENDERTARGET/CRenderTarget::BeginDraw
- AFXRENDERTARGET/CRenderTarget::Clear
- AFXRENDERTARGET/CRenderTarget::COLORREF_TO_D2DCOLOR
- AFXRENDERTARGET/CRenderTarget::CreateCompatibleRenderTarget
- AFXRENDERTARGET/CRenderTarget::Destroy
- AFXRENDERTARGET/CRenderTarget::Detach
- AFXRENDERTARGET/CRenderTarget::DrawBitmap
- AFXRENDERTARGET/CRenderTarget::DrawEllipse
- AFXRENDERTARGET/CRenderTarget::DrawGeometry
- AFXRENDERTARGET/CRenderTarget::DrawGlyphRun
- AFXRENDERTARGET/CRenderTarget::DrawLine
- AFXRENDERTARGET/CRenderTarget::DrawRectangle
- AFXRENDERTARGET/CRenderTarget::DrawRoundedRectangle
- AFXRENDERTARGET/CRenderTarget::DrawText
- AFXRENDERTARGET/CRenderTarget::DrawTextLayout
- AFXRENDERTARGET/CRenderTarget::EndDraw
- AFXRENDERTARGET/CRenderTarget::FillEllipse
- AFXRENDERTARGET/CRenderTarget::FillGeometry
- AFXRENDERTARGET/CRenderTarget::FillMesh
- AFXRENDERTARGET/CRenderTarget::FillOpacityMask
- AFXRENDERTARGET/CRenderTarget::FillRectangle
- AFXRENDERTARGET/CRenderTarget::FillRoundedRectangle
- AFXRENDERTARGET/CRenderTarget::Flush
- AFXRENDERTARGET/CRenderTarget::GetAntialiasMode
- AFXRENDERTARGET/CRenderTarget::GetDpi
- AFXRENDERTARGET/CRenderTarget::GetMaximumBitmapSize
- AFXRENDERTARGET/CRenderTarget::GetPixelFormat
- AFXRENDERTARGET/CRenderTarget::GetPixelSize
- AFXRENDERTARGET/CRenderTarget::GetRenderTarget
- AFXRENDERTARGET/CRenderTarget::GetSize
- AFXRENDERTARGET/CRenderTarget::GetTags
- AFXRENDERTARGET/CRenderTarget::GetTextAntialiasMode
- AFXRENDERTARGET/CRenderTarget::GetTextRenderingParams
- AFXRENDERTARGET/CRenderTarget::GetTransform
- AFXRENDERTARGET/CRenderTarget::IsSupported
- AFXRENDERTARGET/CRenderTarget::IsValid
- AFXRENDERTARGET/CRenderTarget::PopAxisAlignedClip
- AFXRENDERTARGET/CRenderTarget::PopLayer
- AFXRENDERTARGET/CRenderTarget::PushAxisAlignedClip
- AFXRENDERTARGET/CRenderTarget::PushLayer
- AFXRENDERTARGET/CRenderTarget::RestoreDrawingState
- AFXRENDERTARGET/CRenderTarget::SaveDrawingState
- AFXRENDERTARGET/CRenderTarget::SetAntialiasMode
- AFXRENDERTARGET/CRenderTarget::SetDpi
- AFXRENDERTARGET/CRenderTarget::SetTags
- AFXRENDERTARGET/CRenderTarget::SetTextAntialiasMode
- AFXRENDERTARGET/CRenderTarget::SetTextRenderingParams
- AFXRENDERTARGET/CRenderTarget::SetTransform
- AFXRENDERTARGET/CRenderTarget::VerifyResource
- AFXRENDERTARGET/CRenderTarget::m_lstResources
- AFXRENDERTARGET/CRenderTarget::m_pRenderTarget
- AFXRENDERTARGET/CRenderTarget::m_pTextFormatDefault
dev_langs: C++
helpviewer_keywords:
- CRenderTarget [MFC], CRenderTarget
- CRenderTarget [MFC], Attach
- CRenderTarget [MFC], BeginDraw
- CRenderTarget [MFC], Clear
- CRenderTarget [MFC], COLORREF_TO_D2DCOLOR
- CRenderTarget [MFC], CreateCompatibleRenderTarget
- CRenderTarget [MFC], Destroy
- CRenderTarget [MFC], Detach
- CRenderTarget [MFC], DrawBitmap
- CRenderTarget [MFC], DrawEllipse
- CRenderTarget [MFC], DrawGeometry
- CRenderTarget [MFC], DrawGlyphRun
- CRenderTarget [MFC], DrawLine
- CRenderTarget [MFC], DrawRectangle
- CRenderTarget [MFC], DrawRoundedRectangle
- CRenderTarget [MFC], DrawText
- CRenderTarget [MFC], DrawTextLayout
- CRenderTarget [MFC], EndDraw
- CRenderTarget [MFC], FillEllipse
- CRenderTarget [MFC], FillGeometry
- CRenderTarget [MFC], FillMesh
- CRenderTarget [MFC], FillOpacityMask
- CRenderTarget [MFC], FillRectangle
- CRenderTarget [MFC], FillRoundedRectangle
- CRenderTarget [MFC], Flush
- CRenderTarget [MFC], GetAntialiasMode
- CRenderTarget [MFC], GetDpi
- CRenderTarget [MFC], GetMaximumBitmapSize
- CRenderTarget [MFC], GetPixelFormat
- CRenderTarget [MFC], GetPixelSize
- CRenderTarget [MFC], GetRenderTarget
- CRenderTarget [MFC], GetSize
- CRenderTarget [MFC], GetTags
- CRenderTarget [MFC], GetTextAntialiasMode
- CRenderTarget [MFC], GetTextRenderingParams
- CRenderTarget [MFC], GetTransform
- CRenderTarget [MFC], IsSupported
- CRenderTarget [MFC], IsValid
- CRenderTarget [MFC], PopAxisAlignedClip
- CRenderTarget [MFC], PopLayer
- CRenderTarget [MFC], PushAxisAlignedClip
- CRenderTarget [MFC], PushLayer
- CRenderTarget [MFC], RestoreDrawingState
- CRenderTarget [MFC], SaveDrawingState
- CRenderTarget [MFC], SetAntialiasMode
- CRenderTarget [MFC], SetDpi
- CRenderTarget [MFC], SetTags
- CRenderTarget [MFC], SetTextAntialiasMode
- CRenderTarget [MFC], SetTextRenderingParams
- CRenderTarget [MFC], SetTransform
- CRenderTarget [MFC], VerifyResource
- CRenderTarget [MFC], m_lstResources
- CRenderTarget [MFC], m_pRenderTarget
- CRenderTarget [MFC], m_pTextFormatDefault
ms.assetid: 30d1607d-68d3-4d14-ac36-fdbd0ef903a1
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a52a2add3306aaf684f9a48a06d1add229205233
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="crendertarget-class"></a>CRenderTarget – třída
Obálka pro ID2D1RenderTarget.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CRenderTarget : public CObject;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CRenderTarget::CRenderTarget](#crendertarget)|Vytvoří objekt CRenderTarget.|  
|[CRenderTarget:: ~ CRenderTarget](#crendertarget__~crendertarget)|Destruktor. Voláno, když je zničen cílový objekt vykreslení.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CRenderTarget::Attach](#attach)|Připojí existující vykreslení cílové rozhraní k objektu|  
|[CRenderTarget::BeginDraw](#begindraw)|Inicializuje kreslení na tento cíl vykreslení.|  
|[CRenderTarget::Clear](#clear)|Vymaže oblasti výkresu zadaná barva.|  
|[CRenderTarget::COLORREF_TO_D2DCOLOR](#colorref_to_d2dcolor)|Převede objekt D2D1_COLOR_F GDI barvy a alfa hodnot.|  
|[CRenderTarget::CreateCompatibleRenderTarget](#createcompatiblerendertarget)|Vytvoří nový cíl vykreslení rastrový obrázek pro použití při kreslení zprostředkující mimo obrazovku, který je kompatibilní s aktuální cíl vykreslení.|  
|[CRenderTarget::Destroy](#destroy)|Odstraní jeden nebo více prostředků|  
|[CRenderTarget::Detach](#detach)|Umožňuje odpojit vykreslení cílové rozhraní z objektu|  
|[CRenderTarget::DrawBitmap](#drawbitmap)|Formátovaný text popsaného zadaný objekt IDWriteTextLayout nevykresluje.|  
|[CRenderTarget::DrawEllipse](#drawellipse)|Nakreslí obrys zadaný elipsy pomocí styl zadaný tahu.|  
|[CRenderTarget::DrawGeometry](#drawgeometry)|Nakreslí obrys zadaná geometrie pomocí styl zadaný tahu.|  
|[CRenderTarget::DrawGlyphRun](#drawglyphrun)|Vykreslí zadaný glyfů.|  
|[CRenderTarget::DrawLine](#drawline)|Nakreslí mezi uvedených bodů pomocí styl zadaný tahu.|  
|[CRenderTarget::DrawRectangle](#drawrectangle)|Nakreslí obrys rámečku, který má zadaný dimenzí a styl tahu.|  
|[CRenderTarget::DrawRoundedRectangle](#drawroundedrectangle)|Nakreslí obrys zadaný zaoblený obdélník pomocí styl zadaný tahu.|  
|[CRenderTarget::DrawText](#drawtext)|Vykreslí zadaný text použití formátu informací uvedených v objektu IDWriteTextFormat.|  
|[CRenderTarget::DrawTextLayout](#drawtextlayout)|Formátovaný text popsaného zadaný objekt IDWriteTextLayout nevykresluje.|  
|[CRenderTarget::EndDraw](#enddraw)|Ukončí kreslení operací na cíli vykreslování a označuje aktuální stav chyby a přidružených značek.|  
|[CRenderTarget::FillEllipse](#fillellipse)|Vybarví vnitřek zadaný třemi tečkami.|  
|[CRenderTarget::FillGeometry](#fillgeometry)|Vybarví vnitřek zadaná geometrie.|  
|[CRenderTarget::FillMesh](#fillmesh)|Vybarví vnitřek zadaný OK.|  
|[CRenderTarget::FillOpacityMask](#fillopacitymask)|Platí maska krytí popsaného Zadaný rastrový obrázek na štětce a používá tento štětce k vyplnění oblast vykreslování cíle.|  
|[CRenderTarget::FillRectangle](#fillrectangle)|Vybarví vnitřek zadaný rámeček.|  
|[CRenderTarget::FillRoundedRectangle](#fillroundedrectangle)|Vybarví vnitřek zadaný zaoblený obdélník.|  
|[CRenderTarget::Flush](#flush)|Spouští všechny čekající příkazy kreslení.|  
|[CRenderTarget::GetAntialiasMode](#getantialiasmode)|Načte aktuální vyhlazení režim pro vykreslování operace netextových.|  
|[CRenderTarget::GetDpi](#getdpi)|Vrátí vykreslení cíle bodů na palec (DPI)|  
|[CRenderTarget::GetMaximumBitmapSize](#getmaximumbitmapsize)|Získá maximální velikost v jednotkách závislé na zařízení (v pixelech), všechny dimenze jeden rastrový obrázek nepodporuje cíl vykreslení|  
|[CRenderTarget::GetPixelFormat](#getpixelformat)|Načte pixelů formátu a alpha režimu vykreslování cíle|  
|[CRenderTarget::GetPixelSize](#getpixelsize)|Vrátí velikost cíle vykreslení v pixelech zařízení|  
|[CRenderTarget::GetRenderTarget](#getrendertarget)|Vrátí ID2D1RenderTarget rozhraní|  
|[CRenderTarget::GetSize](#getsize)|Vrátí velikost cíle vykreslení v pixelech nezávislé na zařízení|  
|[CRenderTarget::GetTags](#gettags)|Získá popisek pro následné kreslení operace.|  
|[CRenderTarget::GetTextAntialiasMode](#gettextantialiasmode)|Získá aktuální režim antialiasingu textu a glyfy kreslení operations.|  
|[CRenderTarget::GetTextRenderingParams](#gettextrenderingparams)|Načte cíl vykreslení aktuální možnosti vykreslování textu.|  
|[CRenderTarget::GetTransform](#gettransform)|Zadaná transformace se vztahuje na cíl vykreslování, nahraďte existující transformace. Všechny následné kreslení operace dojít v transformovaných prostoru.|  
|[CRenderTarget::IsSupported](#issupported)|Určuje, zda cílový vykreslení podporuje zadané vlastnosti|  
|[CRenderTarget::IsValid](#isvalid)|Kontrola platnosti prostředků|  
|[CRenderTarget::PopAxisAlignedClip](#popaxisalignedclip)|Odebere poslední klip zarovnaný osy z vykreslení cíle. Po tato metoda je volána, klip platí pro další kreslení operacích.|  
|[CRenderTarget::PopLayer](#poplayer)|Zastaví přesměrování kreslení operations do vrstvy, která je zadána poslední PushLayer volání.|  
|[CRenderTarget::PushAxisAlignedClip](#pushaxisalignedclip)|Odebere poslední klip zarovnaný osy z vykreslení cíle. Po tato metoda je volána, klip platí pro další kreslení operacích.|  
|[CRenderTarget::PushLayer](#pushlayer)|Přidá zadané vrstvě k vykreslení cíli tak, aby obdržel všechny následné kreslení operace, dokud se nazývá PopLayer.|  
|[CRenderTarget::RestoreDrawingState](#restoredrawingstate)|Nastaví cíl vykreslení kreslení stavu u zadaného ID2D1DrawingStateBlock.|  
|[CRenderTarget::SaveDrawingState](#savedrawingstate)|Uloží aktuální stav kreslení do zadané ID2D1DrawingStateBlock.|  
|[CRenderTarget::SetAntialiasMode](#setantialiasmode)|Nastaví režim antialiasingu vykreslení cíle. Režim vyhlazování se vztahuje na všechny následné kreslení operace s výjimkou text a glyfy kreslení operace.|  
|[CRenderTarget::SetDpi](#setdpi)|Nastaví bodů na palec (DPI) cíle vykreslení.|  
|[CRenderTarget::SetTags](#settags)|Určuje popisek pro následné kreslení operace.|  
|[CRenderTarget::SetTextAntialiasMode](#settextantialiasmode)|Určuje režim vyhlazování použít pro následující text a kreslení operace glyfů.|  
|[CRenderTarget::SetTextRenderingParams](#settextrenderingparams)|Určuje možnosti vykreslování textu má být použita pro všechny následující text a glyfy kreslení operace.|  
|[CRenderTarget::SetTransform](#settransform)|Přetíženo. Zadaná transformace se vztahuje na cíl vykreslování, nahraďte existující transformace. Všechny následné kreslení operace dojít v transformovaných prostoru.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CRenderTarget::VerifyResource](#verifyresource)|Ověří platnost objekt CD2DResource; Pokud ho ještě neexistuje, vytvoří se objekt.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CRenderTarget::operator ID2D1RenderTarget *](#operator_id2d1rendertarget_star)|Vrátí ID2D1RenderTarget rozhraní|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CRenderTarget::m_lstResources](#m_lstresources)|Seznam ukazatelé na objekty CD2DResource.|  
|[CRenderTarget::m_pRenderTarget](#m_prendertarget)|Ukazatel na objekt ID2D1RenderTarget.|  
|[CRenderTarget::m_pTextFormatDefault](#m_ptextformatdefault)|Ukazatel na CD2DTextFormat objekt, který obsahuje výchozí formát textu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CRenderTarget](../../mfc/reference/crendertarget-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxrendertarget.h  
  
##  <a name="_dtorcrendertarget"></a>CRenderTarget:: ~ CRenderTarget  
 Destruktor. Voláno, když je zničen cílový objekt vykreslení.  
  
```  
virtual ~CRenderTarget();
```  
  
##  <a name="attach"></a>CRenderTarget::Attach  
 Připojí existující vykreslení cílové rozhraní k objektu  
  
```  
void Attach(ID2D1RenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `pRenderTarget`  
 Existující vykreslení cílové rozhraní. Nemůže mít hodnotu NULL  
  
##  <a name="begindraw"></a>CRenderTarget::BeginDraw  
 Inicializuje kreslení na tento cíl vykreslení.  
  
```  
void BeginDraw();
```  
  
##  <a name="clear"></a>CRenderTarget::Clear  
 Vymaže oblasti výkresu zadaná barva.  
  
```  
void Clear(D2D1_COLOR_F color);
```  
  
### <a name="parameters"></a>Parametry  
 `color`  
 Barva, ke kterému je oblasti výkresu vymazán.  
  
##  <a name="colorref_to_d2dcolor"></a>CRenderTarget::COLORREF_TO_D2DCOLOR  
 Převede objekt D2D1_COLOR_F GDI barvy a alfa hodnot.  
  
```  
static D2D1_COLOR_F COLORREF_TO_D2DCOLOR(
    COLORREF color,  
    int nAlpha = 255);
```  
  
### <a name="parameters"></a>Parametry  
 `color`  
 RGB hodnota.  
  
 `nAlpha`  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota D2D1_COLOR_F.  
  
##  <a name="createcompatiblerendertarget"></a>CRenderTarget::CreateCompatibleRenderTarget  
 Vytvoří nový cíl vykreslení rastrový obrázek pro použití při kreslení zprostředkující mimo obrazovku, který je kompatibilní s aktuální cíl vykreslení.  
  
```  
BOOL CreateCompatibleRenderTarget(
    CBitmapRenderTarget& bitmapTarget,  
    CD2DSizeF sizeDesired = CD2DSizeF(0., 0.), 
    CD2DSizeU sizePixelDesired = CD2DSizeU(0, 0), 
    D2D1_PIXEL_FORMAT* desiredFormat = NULL,  
    D2D1_COMPATIBLE_RENDER_TARGET_OPTIONS options = D2D1_COMPATIBLE_RENDER_TARGET_OPTIONS_NONE);
```  
  
### <a name="parameters"></a>Parametry  
 `bitmapTarget`  
 Po návratu tato metoda obsahuje adresu ukazatel na nový cílový vykreslení rastrového obrázku. Tento parametr je předán bez inicializace.  
  
 `sizeDesired`  
 Požadovaná velikost nová cílová vykreslení v pixelech nezávislé na zařízení, pokud má být liší od originálu vykreslení cíl, nebo hodnotu NULL. Další informace najdete v části poznámky.  
  
 `sizePixelDesired`  
 Požadovaná velikost nová cílová vykreslení v pixelech, pokud má být liší od originálu vykreslení cíl, nebo hodnotu NULL. Další informace najdete v části poznámky.  
  
 `desiredFormat`  
 Požadované Pixelový formát a alfa režim nový vykreslení cíl, nebo hodnotu NULL. Pokud Pixelový formát je nastavený na DXGI_FORMAT_UNKNOWN nebo pokud tento parametr hodnotu null, nová cílová vykreslení používá stejný formát pixelů jako původní vykreslení cíl. Pokud alfa režim je D2D1_ALPHA_MODE_UNKNOWN nebo tento parametr hodnotu NULL, alfa režimu nová cílová vykreslení výchozí D2D1_ALPHA_MODE_PREMULTIPLIED. Informace o podporovaných pixelů formátech najdete v tématu podporované formáty pixelů a Alpha režimy.  
  
 `options`  
 Hodnota, která určuje, zda musí být kompatibilní s GDI nová cílová vykreslení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu FALSE.  
  
##  <a name="crendertarget"></a>CRenderTarget::CRenderTarget  
 Vytvoří objekt CRenderTarget.  
  
```  
CRenderTarget();
```  
  
##  <a name="destroy"></a>CRenderTarget::Destroy  
 Odstraní jeden nebo více prostředků  
  
```  
BOOL Destroy(BOOL bDeleteResources = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bDeleteResources`  
 Pokud bDeleteResources hodnotu PRAVDA, všechny prostředky, které jsou umístěné v m_lstResources budou automaticky zničena.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí hodnotu TRUE. Jinak vrátí hodnotu FALSE  
  
##  <a name="detach"></a>CRenderTarget::Detach  
 Umožňuje odpojit vykreslení cílové rozhraní z objektu  
  
```  
ID2D1RenderTarget* Detach ();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na odpojit vykreslit cílové rozhraní.  
  
##  <a name="drawbitmap"></a>CRenderTarget::DrawBitmap  
 Formátovaný text popsaného zadaný objekt IDWriteTextLayout nevykresluje.  
  
```  
void DrawBitmap(
    CD2DBitmap* pBitmap,  
    const CD2DRectF& rectDest,  
    float fOpacity = 1.0,  
    D2D1_BITMAP_INTERPOLATION_MODE interpolationMode = D2D1_BITMAP_INTERPOLATION_MODE_LINEAR,  
    const CD2DRectF* pRectSrc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pBitmap`  
 Rastrový obrázek pro vykreslení.  
  
 `rectDest`  
 Velikost a umístění v pixelech nezávislé na zařízení v prostoru souřadnic cíl vykreslení oblasti, ke kterému se nevykreslí bitové mapy. Rámeček není dobře seřazený, nic se nevykreslí, ale cíl vykreslení nevstupuje do chybového stavu.  
  
 `fOpacity`  
 Hodnota mezi 0,0 f a 1,0 f (včetně), která určuje hodnotu krytí platí pro bitovou mapu; Tato hodnota se násobí proti hodnoty alfa obsahu rastrového obrázku.  
  
 `interpolationMode`  
 Režim interpolace použijte, pokud je bitmapy škálovat nebo otáčet o kreslení operaci.  
  
 `pRectSrc`  
 Velikost a umístění v pixelech nezávislé na zařízení v souřadnicového prostoru rastrového obrázku na oblasti v rámci bitové mapy k vykreslení.  
  
##  <a name="drawellipse"></a>CRenderTarget::DrawEllipse  
 Nakreslí obrys zadaný elipsy pomocí styl zadaný tahu.  
  
```  
void DrawEllipse(
    const CD2DEllipse& ellipse,  
    CD2DBrush* pBrush,  
    FLOAT fStrokeWidth = 1.0,  
    ID2D1StrokeStyle* strokeStyle = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `ellipse`  
 Pozice a radius se třemi tečkami k vykreslení v pixelech nezávislé na zařízení.  
  
 `pBrush`  
 Štětce použita k vyplnění outline se třemi tečkami.  
  
 `fStrokeWidth`  
 Tloušťka tahu se třemi tečkami. Tahu se jedná o outline se třemi tečkami.  
  
 `strokeStyle`  
 Styl tahu aplikovat na obrys se třemi tečkami nebo hodnota NULL pro malování plnou tahu.  
  
##  <a name="drawgeometry"></a>CRenderTarget::DrawGeometry  
 Nakreslí obrys zadaná geometrie pomocí styl zadaný tahu.  
  
```  
void DrawGeometry(
    CD2DGeometry* pGeometry,  
    CD2DBrush* pBrush,  
    FLOAT fStrokeWidth = 1.0,  
    ID2D1StrokeStyle* strokeStyle = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pGeometry`  
 Geometrie k vykreslení.  
  
 `pBrush`  
 Štětce použita k vyplnění geometrické tahu.  
  
 `fStrokeWidth`  
 Tloušťka geometrické tahu. Tahu se jedná o geometrie outline.  
  
 `strokeStyle`  
 Styl tahu pro použití geometrické outline nebo hodnota NULL pro malování plnou tahu.  
  
##  <a name="drawglyphrun"></a>CRenderTarget::DrawGlyphRun  
 Vykreslí zadaný glyfů.  
  
```  
void DrawGlyphRun(
    const CD2DPointF& ptBaseLineOrigin,  
    const DWRITE_GLYPH_RUN& glyphRun,  
    CD2DBrush* pForegroundBrush,  
    DWRITE_MEASURING_MODE measuringMode = DWRITE_MEASURING_MODE_NATURAL);
```  
  
### <a name="parameters"></a>Parametry  
 `ptBaseLineOrigin`  
 Původ v pixelech nezávislé na zařízení, glyfů standardních hodnot.  
  
 `glyphRun`  
 Glyfů pro vykreslení.  
  
 `pForegroundBrush`  
 Štětce použita k vyplnění zadaný glyfů.  
  
 `measuringMode`  
 Hodnota, která určuje, jak jsou glyfy metriky používá k měření text při formátování. Výchozí hodnota je DWRITE_MEASURING_MODE_NATURAL.  
  
##  <a name="drawline"></a>CRenderTarget::DrawLine  
 Nakreslí mezi uvedených bodů pomocí styl zadaný tahu.  
  
```  
void DrawLine(
    const CD2DPointF& ptFrom,  
    const CD2DPointF& ptTo,  
    CD2DBrush* pBrush,  
    FLOAT fStrokeWidth = 1.0,  
    ID2D1StrokeStyle* strokeStyle = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `ptFrom`  
 Počáteční bod čáry v pixelech nezávislé na zařízení.  
  
 `ptTo`  
 Koncový bod řádku v pixelech nezávislé na zařízení.  
  
 `pBrush`  
 Štětce použita k vyplnění tahu na řádku.  
  
 `fStrokeWidth`  
 Hodnota větší než nebo rovna hodnotě 0,0 f, která určuje šířku tahu. Pokud není tento parametr zadán, bude výchozí 1.0f. Tahu je umístěn na střed v řádku.  
  
 `strokeStyle`  
 Styl tahu Malování, nebo hodnotu NULL pro malování na souvislou čáru.  
  
##  <a name="drawrectangle"></a>CRenderTarget::DrawRectangle  
 Nakreslí obrys rámečku, který má zadaný dimenzí a styl tahu.  
  
```  
void DrawRectangle(
    const CD2DRectF& rect,  
    CD2DBrush* pBrush,  
    FLOAT fStrokeWidth = 1.0,  
    ID2D1StrokeStyle* strokeStyle = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `rect`  
 Dimenze rámeček k vykreslení v pixelech nezávislé na zařízení  
  
 `pBrush`  
 Štětce použita k vyplnění tahu obdélníku  
  
 `fStrokeWidth`  
 Hodnota větší než nebo rovno 0, která určuje šířku tahu obdélníku 0f. Tahu se jedná o obdélníku outline.  
  
 `strokeStyle`  
 Styl tahu Malování, nebo hodnotu NULL pro malování plnou tahu.  
  
##  <a name="drawroundedrectangle"></a>CRenderTarget::DrawRoundedRectangle  
 Nakreslí obrys zadaný zaoblený obdélník pomocí styl zadaný tahu.  
  
```  
void DrawRoundedRectangle(
    const CD2DRoundedRect& rectRounded,  
    CD2DBrush* pBrush,  
    FLOAT fStrokeWidth = 1.0,  
    ID2D1StrokeStyle* strokeStyle = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `rectRounded`  
 Dimenze zaoblený obdélník k vykreslení v pixelech nezávislé na zařízení.  
  
 `pBrush`  
 Štětce použita k vyplnění zaoblený obdélník outline.  
  
 `fStrokeWidth`  
 Šířku tahu zaoblený obdélník. Tahu se jedná o zaoblený obdélník outline. Výchozí hodnota je 1.0f.  
  
 `strokeStyle`  
 Styl tahu zaoblený obdélník nebo hodnota NULL pro malování plnou tahu. Výchozí hodnota je NULL.  
  
##  <a name="drawtext"></a>CRenderTarget::DrawText  
 Vykreslí zadaný text použití formátu informací uvedených v objektu IDWriteTextFormat.  
  
```  
void DrawText(
    const CString& strText,  
    const CD2DRectF& rect,  
    CD2DBrush* pForegroundBrush,  
    CD2DTextFormat* textFormat = NULL,  
    D2D1_DRAW_TEXT_OPTIONS options = D2D1_DRAW_TEXT_OPTIONS_NONE,  
    DWRITE_MEASURING_MODE measuringMode = DWRITE_MEASURING_MODE_NATURAL);
```  
  
### <a name="parameters"></a>Parametry  
 `strText`  
 Ukazatel na pole znaků Unicode k vykreslení.  
  
 `rect`  
 Velikost a umístění oblasti, ve kterém se nevykreslí text.  
  
 `pForegroundBrush`  
 Štětce použita k vyplnění text.  
  
 `textFormat`  
 Objekt, který popisuje formátování podrobnosti text k vykreslení, jako jsou například písmo, velikost písma a směr toku.  
  
 `options`  
 Hodnota, která určuje, zda text by měl být přichyceno k hranice pixelů a jestli text by měl být oříznuto rámeček rozložení. Výchozí hodnota je D2D1_DRAW_TEXT_OPTIONS_NONE, která označuje, že text by měl být přichyceno k hranice pixelů a nesmí být oříznut na obdélník rozložení.  
  
 `measuringMode`  
 Hodnota, která určuje, jak jsou glyfy metriky používá k měření text při formátování. Výchozí hodnota je DWRITE_MEASURING_MODE_NATURAL.  
  
##  <a name="drawtextlayout"></a>CRenderTarget::DrawTextLayout  
 Formátovaný text popsaného zadaný objekt IDWriteTextLayout nevykresluje.  
  
```  
void DrawTextLayout(
    const CD2DPointF& ptOrigin,  
    CD2DTextLayout* textLayout,  
    CD2DBrush* pBrushForeground,  
    D2D1_DRAW_TEXT_OPTIONS options = D2D1_DRAW_TEXT_OPTIONS_NONE);
```  
  
### <a name="parameters"></a>Parametry  
 `ptOrigin`  
 Bod popsané v pixelech nezávislé na zařízení, na kterých se vykresluje levém horním rohu popsaného textLayout textu.  
  
 `textLayout`  
 Formátovaný text k vykreslení. Kreslení důsledky, které nedědí z ID2D1Resource se ignorují. Pokud existují kreslení účinky, které dědí od ID2D1Resource které nejsou štětce, tato metoda selže a cíl vykreslení zprovozněn v chybovém stavu.  
  
 `pBrushForeground`  
 Štětce použita k vyplnění jakýkoli text v textLayout, který ještě nemá štětce přidružené jako kreslení vliv (zadaný metodou IDWriteTextLayout::SetDrawingEffect).  
  
 `options`  
 Hodnota, která určuje, zda text by měl být přichyceno k hranice pixelů a jestli text by měl být oříznuto rámeček rozložení. Výchozí hodnota je D2D1_DRAW_TEXT_OPTIONS_NONE, která označuje, že text by měl být přichyceno k hranice pixelů a nesmí být oříznut na obdélník rozložení.  
  
##  <a name="enddraw"></a>CRenderTarget::EndDraw  
 Ukončí kreslení operací na cíli vykreslování a označuje aktuální stav chyby a přidružených značek.  
  
```  
HRESULT EndDraw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí S_OK. Funkce HRESULT chybový kód.  
  
##  <a name="fillellipse"></a>CRenderTarget::FillEllipse  
 Vybarví vnitřek zadaný třemi tečkami.  
  
```  
void FillEllipse(
    const CD2DEllipse& ellipse,  
    CD2DBrush* pBrush);
```  
  
### <a name="parameters"></a>Parametry  
 `ellipse`  
 Pozice a protokolu radius v pixelech nezávislé na zařízení se třemi tečkami k vyplnění.  
  
 `pBrush`  
 Štětec k vyplnění vnitřku se třemi tečkami.  
  
##  <a name="fillgeometry"></a>CRenderTarget::FillGeometry  
 Vybarví vnitřek zadaná geometrie.  
  
```  
void FillGeometry(
    CD2DGeometry* pGeometry,  
    CD2DBrush* pBrush,  
    CD2DBrush* pOpacityBrush = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pGeometry`  
 Geometrie k vyplnění.  
  
 `pBrush`  
 Štětce použita k vyplnění geometrie je vnitřní.  
  
 `pOpacityBrush`  
 Maska krytí použít geometrie; Hodnota NULL pro žádné krytí masku. Pokud je zadán masky krytí (parametr opacityBrush), musí být štětce ID2D1BitmapBrush, který má režimech rozšířit x a y nastavena na D2D1_EXTEND_MODE_CLAMP. Další informace najdete v části poznámky.  
  
##  <a name="fillmesh"></a>CRenderTarget::FillMesh  
 Vybarví vnitřek zadaný OK.  
  
```  
void FillMesh(
    CD2DMesh* pMesh,  
    CD2DBrush* pBrush);
```  
  
### <a name="parameters"></a>Parametry  
 `pMesh`  
 OK k vyplnění.  
  
 `pBrush`  
 Štětce použita k vyplnění OK.  
  
##  <a name="fillopacitymask"></a>CRenderTarget::FillOpacityMask  
 Platí maska krytí popsaného Zadaný rastrový obrázek na štětce a používá tento štětce k vyplnění oblast vykreslování cíle.  
  
```  
void FillOpacityMask(
    CD2DBitmap* pOpacityMask,  
    CD2DBrush* pBrush,  
    D2D1_OPACITY_MASK_CONTENT content,  
    const CD2DRectF& rectDest,  
    const CD2DRectF& rectSrc);
```  
  
### <a name="parameters"></a>Parametry  
 `pOpacityMask`  
 Pozice a protokolu radius v pixelech nezávislé na zařízení se třemi tečkami k vyplnění.  
  
 `pBrush`  
 Štětce použita k vyplnění oblast vykreslování cíle určeného destinationRectangle.  
  
 `content`  
 Typ obsahu, který obsahuje maska krytí. Hodnota se používá k určení barevný prostor, ve kterém je maska krytí smíšení.  
  
 `rectDest`  
 Oblast vykreslování cíl pro malování v pixelech nezávislé na zařízení.  
  
 `rectSrc`  
 Oblast rastrový obrázek, který chcete použít jako masku krytí v pixelech nezávislé na zařízení.  
  
##  <a name="fillrectangle"></a>CRenderTarget::FillRectangle  
 Vybarví vnitřek zadaný rámeček.  
  
```  
void FillRectangle(
    const CD2DRectF& rect,  
    CD2DBrush* pBrush);
```  
  
### <a name="parameters"></a>Parametry  
 `rect`  
 Dimenze rámeček pro malování v pixelech nezávislé na zařízení.  
  
 `pBrush`  
 Štětce použita k vyplnění rámeček je vnitřní.  
  
##  <a name="fillroundedrectangle"></a>CRenderTarget::FillRoundedRectangle  
 Vybarví vnitřek zadaný zaoblený obdélník.  
  
```  
void FillRoundedRectangle(
    const CD2DRoundedRect& rectRounded,  
    CD2DBrush* pBrush);
```  
  
### <a name="parameters"></a>Parametry  
 `rectRounded`  
 Dimenze zaoblený obdélník k vyplnění v nezávislých pixelů zařízení.  
  
 `pBrush`  
 Štětec k vyplnění vnitřku zaoblený obdélník.  
  
##  <a name="flush"></a>CRenderTarget::Flush  
 Spouští všechny čekající příkazy kreslení.  
  
```  
void Flush(
    D2D1_TAG* tag1 = NULL,  
    D2D1_TAG* tag2 = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `tag1`  
 Obsahuje značky pro kreslení operace, které způsobit chyby, nebo 0, pokud nedošlo k chybám. Tento parametr je předán bez inicializace.  
  
 `tag2`  
 Obsahuje značky pro kreslení operace, které způsobit chyby, nebo 0, pokud nedošlo k chybám. Tento parametr je předán bez inicializace.  
  
##  <a name="getantialiasmode"></a>CRenderTarget::GetAntialiasMode  
 Načte aktuální vyhlazení režim pro vykreslování operace netextových.  
  
```  
D2D1_ANTIALIAS_MODE GetAntialiasMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální režim antialiasingu pro netextových kreslení operace.  
  
##  <a name="getdpi"></a>CRenderTarget::GetDpi  
 Vrátí vykreslení cíle bodů na palec (DPI)  
  
```  
CD2DSizeF GetDpi() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Cíl vykreslení bodů na palec (DPI).  
  
##  <a name="getmaximumbitmapsize"></a>CRenderTarget::GetMaximumBitmapSize  
 Získá maximální velikost v jednotkách závislé na zařízení (v pixelech), všechny dimenze jeden rastrový obrázek nepodporuje cíl vykreslení  
  
```  
UINT32 GetMaximumBitmapSize() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Maximální velikost v pixelech všechny dimenze jeden rastrový obrázek nepodporuje cíl vykreslení  
  
##  <a name="getpixelformat"></a>CRenderTarget::GetPixelFormat  
 Načte pixelů formátu a alpha režimu vykreslování cíle  
  
```  
D2D1_PIXEL_FORMAT GetPixelFormat() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pixelů formátu a alpha režimu vykreslování cíle  
  
##  <a name="getpixelsize"></a>CRenderTarget::GetPixelSize  
 Vrátí velikost cíle vykreslení v pixelech zařízení  
  
```  
CD2DSizeU GetPixelSize() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Velikost cíle vykreslení v pixelech zařízení  
  
##  <a name="getrendertarget"></a>CRenderTarget::GetRenderTarget  
 Vrátí ID2D1RenderTarget rozhraní  
  
```  
ID2D1RenderTarget* GetRenderTarget();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na rozhraní ID2D1RenderTarget nebo hodnota NULL, pokud objekt dosud není inicializován.  
  
##  <a name="getsize"></a>CRenderTarget::GetSize  
 Vrátí velikost cíle vykreslení v pixelech nezávislé na zařízení  
  
```  
CD2DSizeF GetSize() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální velikost cíle vykreslení v pixelech nezávislé na zařízení  
  
##  <a name="gettags"></a>CRenderTarget::GetTags  
 Získá popisek pro následné kreslení operace.  
  
```  
void GetTags(
    D2D1_TAG* tag1 = NULL,  
    D2D1_TAG* tag2 = NULL) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `tag1`  
 Obsahuje první popisek pro další kreslení operacích. Tento parametr je předán bez inicializace. Pokud je zadána hodnota NULL, je načíst žádnou hodnotu tohoto parametru.  
  
 `tag2`  
 Obsahuje druhý popisek pro další kreslení operacích. Tento parametr je předán bez inicializace. Pokud je zadána hodnota NULL, je načíst žádnou hodnotu tohoto parametru.  
  
##  <a name="gettextantialiasmode"></a>CRenderTarget::GetTextAntialiasMode  
 Získá aktuální režim antialiasingu textu a glyfy kreslení operations.  
  
```  
D2D1_TEXT_ANTIALIAS_MODE GetTextAntialiasMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální režim antialiasingu pro text a glyfy kreslení operace.  
  
##  <a name="gettextrenderingparams"></a>CRenderTarget::GetTextRenderingParams  
 Načte cíl vykreslení aktuální možnosti vykreslování textu.  
  
```  
void GetTextRenderingParams(IDWriteRenderingParams** textRenderingParams);
```  
  
### <a name="parameters"></a>Parametry  
 `textRenderingParams`  
 Po návratu tato metoda je textRenderingParamscontains adresu ukazatel na cíl vykreslení aktuální možnosti vykreslování textu.  
  
##  <a name="gettransform"></a>CRenderTarget::GetTransform  
 Zadaná transformace se vztahuje na cíl vykreslování, nahraďte existující transformace. Všechny následné kreslení operace dojít v transformovaných prostoru.  
  
```  
void GetTransform(D2D1_MATRIX_3X2_F* transform);
```  
  
### <a name="parameters"></a>Parametry  
 `transform`  
 Transformace použít k vykreslení cíli.  
  
##  <a name="issupported"></a>CRenderTarget::IsSupported  
 Určuje, zda cílový vykreslení podporuje zadané vlastnosti  
  
```  
BOOL IsSupported(const D2D1_RENDER_TARGET_PROPERTIES& renderTargetProperties) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `renderTargetProperties`  
 Vykreslení vlastnosti cíle pro testování  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud zadaný vykreslení vlastnosti cíle podporuje tento cíl vykreslení; jinak hodnota FALSE  
  
##  <a name="isvalid"></a>CRenderTarget::IsValid  
 Kontrola platnosti prostředků  
  
```  
BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud prostředek je platná. jinak hodnota FALSE.  
  
##  <a name="m_lstresources"></a>CRenderTarget::m_lstResources  
 Seznam ukazatelé na objekty CD2DResource.  
  
```  
CObList m_lstResources;  
```  
  
##  <a name="m_prendertarget"></a>CRenderTarget::m_pRenderTarget  
 Ukazatel na objekt ID2D1RenderTarget.  
  
```  
ID2D1RenderTarget* m_pRenderTarget;  
```  
  
##  <a name="m_ptextformatdefault"></a>CRenderTarget::m_pTextFormatDefault  
 Ukazatel na CD2DTextFormat objekt, který obsahuje výchozí formát textu.  
  
```  
CD2DTextFormat* m_pTextFormatDefault;  
```  
  
##  <a name="operator_id2d1rendertarget_star"></a>CRenderTarget::operator ID2D1RenderTarget *  
 Vrátí ID2D1RenderTarget rozhraní  
  
```  
operator ID2D1RenderTarget*();
```   
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na rozhraní ID2D1RenderTarget nebo hodnota NULL, pokud objekt dosud není inicializován.  
  
##  <a name="popaxisalignedclip"></a>CRenderTarget::PopAxisAlignedClip  
 Odebere poslední klip zarovnaný osy z vykreslení cíle. Po tato metoda je volána, klip platí pro další kreslení operacích.  
  
```  
void PopAxisAlignedClip();
```  
  
##  <a name="poplayer"></a>CRenderTarget::PopLayer  
 Zastaví přesměrování kreslení operations do vrstvy, která je zadána poslední PushLayer volání.  
  
```  
void PopLayer();
```  
  
##  <a name="pushaxisalignedclip"></a>CRenderTarget::PushAxisAlignedClip  
 Odebere poslední klip zarovnaný osy z vykreslení cíle. Po tato metoda je volána, klip platí pro další kreslení operacích.  
  
```  
void PushAxisAlignedClip(
    const CD2DRectF& rectClip,  
    D2D1_ANTIALIAS_MODE mode = D2D1_ANTIALIAS_MODE_PER_PRIMITIVE);
```  
  
### <a name="parameters"></a>Parametry  
 `rectClip`  
 Velikost a umístění oblasti výstřižek v pixelech nezávislé na zařízení.  
  
 `mode`  
 Vyhlazení režim, který slouží k vykreslení okrajů klip rects, které mají subpixel hranice a a přizpůsobte klip se scény obsahem. Prolnutí se provádí po při PopAxisAlignedClip metoda je volána a doporučení se netýká každý primitivní ve vrstvě.  
  
##  <a name="pushlayer"></a>CRenderTarget::PushLayer  
 Přidá zadané vrstvě k vykreslení cíli tak, aby obdržel všechny následné kreslení operace, dokud se nazývá PopLayer.  
  
```  
void PushLayer(
    const D2D1_LAYER_PARAMETERS& layerParameters,  
    CD2DLayer& layer);
```  
  
### <a name="parameters"></a>Parametry  
 `layerParameters`  
 Obsahu hranice, geometrickou maska, krytí, masku krytí a možnosti vyhlazení vrstvy.  
  
 `layer`  
 Vrstva, která přijímá následných kreslení operací.  
  
##  <a name="restoredrawingstate"></a>CRenderTarget::RestoreDrawingState  
 Nastaví cíl vykreslení kreslení stavu u zadaného ID2D1DrawingStateBlock.  
  
```  
void RestoreDrawingState(ID2D1DrawingStateBlock& drawingStateBlock);
```  
  
### <a name="parameters"></a>Parametry  
 `drawingStateBlock`  
 Nový stav kreslení vykreslení cíle.  
  
##  <a name="savedrawingstate"></a>CRenderTarget::SaveDrawingState  
 Uloží aktuální stav kreslení do zadané ID2D1DrawingStateBlock.  
  
```  
void SaveDrawingState(ID2D1DrawingStateBlock& drawingStateBlock) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `drawingStateBlock`  
 Po návratu tato metoda obsahuje aktuální stav kreslení vykreslení cíle. Tento parametr se musí inicializovat před předáním k metodě.  
  
##  <a name="setantialiasmode"></a>CRenderTarget::SetAntialiasMode  
 Nastaví režim antialiasingu vykreslení cíle. Režim vyhlazování se vztahuje na všechny následné kreslení operace s výjimkou text a glyfy kreslení operace.  
  
```  
void SetAntialiasMode(D2D1_ANTIALIAS_MODE antialiasMode);
```  
  
### <a name="parameters"></a>Parametry  
 `antialiasMode`  
 Režim antialiasingu pro budoucí kreslení operace.  
  
##  <a name="setdpi"></a>CRenderTarget::SetDpi  
 Nastaví bodů na palec (DPI) cíle vykreslení.  
  
```  
void SetDpi(const CD2DSizeF& sizeDPI);
```  
  
### <a name="parameters"></a>Parametry  
 `sizeDPI`  
 Hodnota větší než nebo rovna nule, který určuje vodorovný/verticalDPI vykreslení cíle.  
  
##  <a name="settags"></a>CRenderTarget::SetTags  
 Určuje popisek pro následné kreslení operace.  
  
```  
void SetTags(
    D2D1_TAG tag1,  
    D2D1_TAG tag2);
```  
  
### <a name="parameters"></a>Parametry  
 `tag1`  
 Štítek pro použití na další kreslení operacích.  
  
 `tag2`  
 Štítek pro použití na další kreslení operacích.  
  
##  <a name="settextantialiasmode"></a>CRenderTarget::SetTextAntialiasMode  
 Určuje režim vyhlazování použít pro následující text a kreslení operace glyfů.  
  
```  
void SetTextAntialiasMode(D2D1_TEXT_ANTIALIAS_MODE textAntialiasMode);
```  
  
### <a name="parameters"></a>Parametry  
 `textAntialiasMode`  
 Vyhlazení režim pro použití pro následující text a glyfy kreslení operace.  
  
##  <a name="settextrenderingparams"></a>CRenderTarget::SetTextRenderingParams  
 Určuje možnosti vykreslování textu má být použita pro všechny následující text a glyfy kreslení operace.  
  
```  
void SetTextRenderingParams(IDWriteRenderingParams* textRenderingParams = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `textRenderingParams`  
 Možnosti vykreslování textu má být použita pro všechny následující text a glyfy kreslení operace; Hodnota NULL, zrušte aktuální možnosti vykreslování textu.  
  
##  <a name="settransform"></a>CRenderTarget::SetTransform  
 Zadaná transformace se vztahuje na cíl vykreslování, nahraďte existující transformace. Všechny následné kreslení operace dojít v transformovaných prostoru.  
  
```  
void SetTransform(const D2D1_MATRIX_3X2_F* transform);  
void SetTransform(const D2D1_MATRIX_3X2_F& transform);
```  
  
### <a name="parameters"></a>Parametry  
 `transform`  
 Transformace použít k vykreslení cíli.  
  
##  <a name="verifyresource"></a>CRenderTarget::VerifyResource  
 Ověří platnost objekt CD2DResource; Pokud ho ještě neexistuje, vytvoří se objekt.  
  
```  
BOOL VerifyResource(CD2DResource* pResource);
```  
  
### <a name="parameters"></a>Parametry  
 `pResource`  
 Ukazatel na CD2DResource objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, je objekt, pokud je to platná; jinak hodnota FALSE.  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
