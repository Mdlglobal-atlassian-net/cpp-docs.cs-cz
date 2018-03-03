---
title: "Třída CDrawingManager | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDrawingManager
- AFXDRAWMANAGER/CDrawingManager
- AFXDRAWMANAGER/CDrawingManager::CDrawingManager
- AFXDRAWMANAGER/CDrawingManager::CreateBitmap_32
- AFXDRAWMANAGER/CDrawingManager::DrawAlpha
- AFXDRAWMANAGER/CDrawingManager::DrawRotated
- AFXDRAWMANAGER/CDrawingManager::DrawEllipse
- AFXDRAWMANAGER/CDrawingManager::DrawGradientRing
- AFXDRAWMANAGER/CDrawingManager::DrawRect
- AFXDRAWMANAGER/CDrawingManager::DrawShadow
- AFXDRAWMANAGER/CDrawingManager::Fill4ColorsGradient
- AFXDRAWMANAGER/CDrawingManager::FillGradient
- AFXDRAWMANAGER/CDrawingManager::FillGradient2
- AFXDRAWMANAGER/CDrawingManager::GrayRect
- AFXDRAWMANAGER/CDrawingManager::HighlightRect
- AFXDRAWMANAGER/CDrawingManager::HLStoRGB_ONE
- AFXDRAWMANAGER/CDrawingManager::HLStoRGB_TWO
- AFXDRAWMANAGER/CDrawingManager::HSVtoRGB
- AFXDRAWMANAGER/CDrawingManager::HuetoRGB
- AFXDRAWMANAGER/CDrawingManager::MirrorRect
- AFXDRAWMANAGER/CDrawingManager::PixelAlpha
- AFXDRAWMANAGER/CDrawingManager::PrepareShadowMask
- AFXDRAWMANAGER/CDrawingManager::RGBtoHSL
- AFXDRAWMANAGER/CDrawingManager::RGBtoHSV
- AFXDRAWMANAGER/CDrawingManager::SetAlphaPixel
- AFXDRAWMANAGER/CDrawingManager::SetPixel
- AFXDRAWMANAGER/CDrawingManager::SmartMixColors
dev_langs:
- C++
helpviewer_keywords:
- CDrawingManager [MFC], CDrawingManager
- CDrawingManager [MFC], CreateBitmap_32
- CDrawingManager [MFC], DrawAlpha
- CDrawingManager [MFC], DrawRotated
- CDrawingManager [MFC], DrawEllipse
- CDrawingManager [MFC], DrawGradientRing
- CDrawingManager [MFC], DrawRect
- CDrawingManager [MFC], DrawShadow
- CDrawingManager [MFC], Fill4ColorsGradient
- CDrawingManager [MFC], FillGradient
- CDrawingManager [MFC], FillGradient2
- CDrawingManager [MFC], GrayRect
- CDrawingManager [MFC], HighlightRect
- CDrawingManager [MFC], HLStoRGB_ONE
- CDrawingManager [MFC], HLStoRGB_TWO
- CDrawingManager [MFC], HSVtoRGB
- CDrawingManager [MFC], HuetoRGB
- CDrawingManager [MFC], MirrorRect
- CDrawingManager [MFC], PixelAlpha
- CDrawingManager [MFC], PrepareShadowMask
- CDrawingManager [MFC], RGBtoHSL
- CDrawingManager [MFC], RGBtoHSV
- CDrawingManager [MFC], SetAlphaPixel
- CDrawingManager [MFC], SetPixel
- CDrawingManager [MFC], SmartMixColors
ms.assetid: 9e4775ca-101b-4aa9-a85a-4d047c701215
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 689d538c03a35175040663aedb7bd6130aae10fd
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2018
---
# <a name="cdrawingmanager-class"></a>CDrawingManager – třída
`CDrawingManager` Třída implementuje složité algoritmy kreslení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDrawingManager : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CDrawingManager::CDrawingManager](#cdrawingmanager)|Vytvoří `CDrawingManager` objektu.|  
|`CDrawingManager::~CDrawingManager`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDrawingManager::CreateBitmap_32](#createbitmap_32)|Vytvoří 32-bit device independent bitmap (DIB), aplikace může zapisovat přímo do.|  
|[CDrawingManager::DrawAlpha](#drawalpha)|Zobrazí rastrové obrázky, které mají průhledných nebo poloprůhledných pixelů.|  
|[CDrawingManager::DrawRotated](#drawrotated)|Otočí zdroj obsahu řadiče domény v dané obdélníku podle +/-90 stupňů|  
|[CDrawingManager::DrawEllipse](#drawellipse)|Nakreslí elipsy s zadaný barvy výplně a ohraničení.|  
|[CDrawingManager::DrawGradientRing](#drawgradientring)|Nakreslí jako kruh a doplní barevně.|  
|[CDrawingManager::DrawLine CDrawingManager::DrawLineA](#drawline_cdrawingmanager__drawlinea)|Nakreslí čáru.|  
|[CDrawingManager::DrawRect](#drawrect)|Kreslení obdélníku s zadaný barvy výplně a ohraničení.|  
|[CDrawingManager::DrawShadow](#drawshadow)|Nakreslí stínové pro obdélníkovou oblast.|  
|[CDrawingManager::Fill4ColorsGradient](#fill4colorsgradient)|Dva barevné přechody vyplní obdélníkovou oblast.|  
|[CDrawingManager::FillGradient](#fillgradient)|Zadaná barva přechodu vyplní obdélníkovou oblast.|  
|[CDrawingManager::FillGradient2](#fillgradient2)|Zadaná barva přechodu vyplní obdélníkovou oblast. Rovněž je zadán směr Změna barvy přechodu.|  
|[CDrawingManager::GrayRect](#grayrect)|Vyplní obdélníku zadaný šedou barvu.|  
|[CDrawingManager::HighlightRect](#highlightrect)|Označuje obdélníkovou oblast.|  
|[CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)|Převede barvu, která z reprezentace HLS znázornění RGB.|  
|[CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)|Převede barvu, která z reprezentace HLS znázornění RGB.|  
|[CDrawingManager::HSVtoRGB](#hsvtorgb)|Převede barvu, která z reprezentace HSV znázornění RGB.|  
|[CDrawingManager::HuetoRGB](#huetorgb)|Pomocná metoda, která převede hodnotu hue na červené, zelené nebo modré součásti.|  
|[CDrawingManager::MirrorRect](#mirrorrect)|Převrátí obdélníkovou oblast.|  
|[CDrawingManager::PixelAlpha](#pixelalpha)|Pomocná metoda, která určuje poslední barvu poloprůhledných pixelů.|  
|[CDrawingManager::PrepareShadowMask](#prepareshadowmask)|Vytvoří rastrového obrázku, který lze použít jako stínu.|  
|[CDrawingManager::RGBtoHSL](#rgbtohsl)|Převede barvu, která z reprezentace RGB na znázornění HSL.|  
|[CDrawingManager::RGBtoHSV](#rgbtohsv)|Převede barvu, která z reprezentace RGB na znázornění HSV.|  
|[CDrawingManager::SetAlphaPixel](#setalphapixel)|Pomocná metoda, která barvy částečně transparentní pixelů v rastrový obrázek.|  
|[CDrawingManager::SetPixel](#setpixel)|Pomocná metoda, která změny jedinému pixelu rastrový obrázek zadaná barva.|  
|[CDrawingManager::SmartMixColors](#smartmixcolors)|Kombinuje dvě barvy na základě vyvážené poměru.|  
  
## <a name="remarks"></a>Poznámky  
 `CDrawingManager` Třída poskytuje funkce pro vykreslování stínů, barevné přechody a zvýrazněná obdélníky. Provádí taky prolnutí alfa. Tuto třídu můžete použít přímo změnit uživatelského rozhraní aplikace.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
 `CDrawingManager`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdrawmanager.h  
  
##  <a name="cdrawingmanager"></a>CDrawingManager::CDrawingManager  
 Vytvoří [CDrawingManager](../../mfc/reference/cdrawingmanager-class.md) objektu.  
  
```  
CDrawingManager(CDC& dc);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`dc`  
 Odkaz na kontextu zařízení. `CDrawingManager` Používá tento kontext pro vykreslování.  
  
##  <a name="createbitmap_32"></a>CDrawingManager::CreateBitmap_32  
 Vytvoří 32-bit device independent bitmap (DIB), aplikace může zapisovat přímo do.  
  
```  
static HBITMAP __stdcall CreateBitmap_32(
    const CSize& size,  
    void** pBits);
 
static HBITMAP __stdcall CreateBitmap_32(
    HBITMAP bitmap,  
    COLORREF clrTransparent = -1);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v]`size`|A [CSize](../../atl-mfc-shared/reference/csize-class.md) parametr, který určuje velikost bitové mapy.|  
|[out]`pBits`|Ukazatel na ukazatel data, která přijímá umístění DIB bit hodnoty.|  
|`bitmap`|Popisovač pro původní bitové mapy|  
|`clrTransparent`|Hodnotu RGB zadání průhledná barva původní bitmapy.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro nově vytvořený obrázek ve formátu DIB, pokud tato metoda je úspěšná. v opačném případě `NULL`.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o tom, jak vytvořit obrázek ve formátu DIB najdete v tématu [CreateDIBSection](http://msdn.microsoft.com/library/windows/desktop/dd183491).  
  
##  <a name="drawalpha"></a>CDrawingManager::DrawAlpha  
 Zobrazí rastrové obrázky, které mají průhledných nebo poloprůhledných pixelů.  
  
```  
void DrawAlpha(
    CDC* pDstDC,  
    const CRect& rectDst,  
    CDC* pSrcDC,  
    const CRect& rectSrc);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDstDC`  
 Ukazatel na kontext zařízení pro cíl.  
  
 [v]`rectDst`  
 Cílový rámeček.  
  
 [v]`pSrcDC`  
 Ukazatel na kontext zařízení pro zdroj.  
  
 [v]`rectSrc`  
 Rámeček zdroje.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda provádí prolnutí alfa pro dvě bitové mapy. Další informace o prolnutí alfa najdete v tématu [AlphaBlend](http://msdn.microsoft.com/library/windows/desktop/dd183351) ve Windows SDK.  
  
##  <a name="drawellipse"></a>CDrawingManager::DrawEllipse  
 Nakreslí elipsy s zadaný barvy výplně a ohraničení.  
  
```  
void DrawEllipse(
    const CRect& rect,  
    COLORREF clrFill,  
    COLORREF clrLine);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`rect`  
 Ohraničující obdélník pro se třemi tečkami.  
  
 [v]`clrFill`  
 Barva, kterou tato metoda používá k vyplnění se třemi tečkami.  
  
 [v]`clrLine`  
 Barva tato metoda používá jako ohraničení se třemi tečkami.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vrátí bez kreslení elipsy, pokud je buď barva nastavena na hodnotu -1. Také vrátí hodnotu bez kreslení elipsy, pokud je buď dimenze ohraničující obdélník 0.  
  
##  <a name="drawgradientring"></a>CDrawingManager::DrawGradientRing  
 Nakreslí jako kruh a doplní barevně.  
  
```  
BOOL DrawGradientRing(
    CRect rect,  
    COLORREF colorStart,  
    COLORREF colorFinish,  
    COLORREF colorBorder,  
    int nAngle,  
    int nWidth,  
    COLORREF clrFace = (COLORREF)-1);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`rect`  
 A [CRect](../../atl-mfc-shared/reference/crect-class.md) parametr, který určuje hranicí pro přechodu prstenec.  
  
 [v]`colorStart`  
 První barva přechodu.  
  
 [v]`colorFinish`  
 Poslední barva přechodu.  
  
 [v]`colorBorder`  
 Barva ohraničení.  
  
 [v]`nAngle`  
 Parametr, který určuje počáteční úhel přechodu kreslení. Tato hodnota by měla být v rozmezí od 0 do 360.  
  
 [v]`nWidth`  
 Šířka ohraničení pro kruh.  
  
 [v]`clrFace`  
 Barva vnitřního prstence.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Rámeček definované `rect` musí být alespoň 5 pixelů široké a 5 pixelů.  
  
##  <a name="drawline_cdrawingmanager__drawlinea"></a>CDrawingManager::DrawLine CDrawingManager::DrawLineA  
 Nakreslí čáru.  
  
```  
void DrawLine(
    int x1,  
    int y1,  
    int x2,  
    int y2,  
    COLORREF clrLine);
 
void DrawLineA(
    double x1,  
    double y1,  
    double x2,  
    double y2,  
    COLORREF clrLine);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v]`x1`|Souřadnice x, kde začíná na řádku.|  
|[v]`y1`|Souřadnice y, kde začíná na řádku.|  
|[v]`x2`|Souřadnice x, které končí na řádku.|  
|[v]`y2`|Souřadnice y, které končí na řádku.|  
|[v]`clrLine`|Barva čáry.|  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda selže, pokud `clrLine` rovná -1.  
  
##  <a name="drawrect"></a>CDrawingManager::DrawRect  
 Kreslení obdélníku s zadaný barvy výplně a ohraničení.  
  
```  
void DrawRect(
    const CRect& rect,  
    COLORREF clrFill,  
    COLORREF clrLine);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`rect`  
 Hranice pro rámeček.  
  
 [v]`clrFill`  
 Barva, kterou tato metoda používá k vyplnění rámeček.  
  
 [v]`clrLine`  
 Barva tato metoda se používá pro ohraničení rámečku.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vrátí bez kreslení obdélníků, pokud je buď barva nastavena na hodnotu -1. Také se vrátí, pokud buď dimenze rámeček je 0.  
  
##  <a name="drawshadow"></a>CDrawingManager::DrawShadow  
 Nakreslí stínové pro obdélníkovou oblast.  
  
```  
BOOL DrawShadow(
    CRect rect,  
    int nDepth,  
    int iMinBrightness = 100,  
    int iMaxBrightness = 50,  
    CBitmap* pBmpSaveBottom = NULL,  
    CBitmap* pBmpSaveRight = NULL,  
    COLORREF clrBase = (COLORREF)-1,  
    BOOL bRightShadow = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`rect`  
 Obdélníkovou oblast v aplikaci. Kreslení manager bude zakreslit stín pod této oblasti.  
  
 [v]`nDepth`  
 Šířka a výška stínové kopie.  
  
 [v]`iMinBrightness`  
 Minimální také průraznost stínu.  
  
 [v]`iMaxBrightness`  
 Maximální také průraznost stínu.  
  
 [v]`pBmpSaveBottom`  
 Ukazatel rastrového obrázku, který obsahuje bitovou kopii pro dolní část stínové kopie.  
  
 [v]`pBmpSaveRight`  
 Ukazatel rastrového obrázku, který obsahuje bitovou kopii pro stínu, který je vykreslen na pravé straně rámečku.  
  
 [v]`clrBase`  
 Barvu stínu.  
  
 [v]`bRightShadow`  
 Parametr typu Boolean, která určuje, jak se bude stín vykreslen. Pokud `bRightShadow` je `TRUE`, `DrawShadow` nevykresluje stín na pravé straně rámečku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí parametrů můžete zadat dvě platný bitmap pro dolní a pravé stínů `pBmpSaveBottom` a `pBmpSaveRight`. Pokud tyto [CBitmap](../../mfc/reference/cbitmap-class.md) objekty mají objekt připojené GDI `DrawShadow` použije tyto bitmap jako stínů. Pokud `CBitmap` parametry nemají objekt připojené GDI `DrawShadow` nevykresluje stín a připojí rastrových obrázků na parametry. V budoucích volání `DrawShadow`, můžete zadat tyto bitmap pro urychlení proces vykreslování. Další informace o `CBitmap` třídy a objektů GDI, najdete v části [grafické objekty](../../mfc/graphic-objects.md).  
  
 Pokud některá z těchto parametrů `NULL`, `DrawShadow` bude automaticky kreslení stínové kopie.  
  
 Pokud nastavíte `bRightShadow` k `FALSE`, stín vykreslovat pod a nalevo od obdélníkovou oblast.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `DrawShadow` metodu `CDrawingManager` třídy. Tento fragment kódu je součástí [Prop list Demo-ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_PropSheetDemo#1](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_1.cpp)]  
  
##  <a name="fill4colorsgradient"></a>CDrawingManager::Fill4ColorsGradient  
 Dva barevné přechody vyplní obdélníkovou oblast.  
  
```  
void Fill4ColorsGradient(
    CRect rect,  
    COLORREF colorStart1,  
    COLORREF colorFinish1,  
    COLORREF colorStart2,  
    COLORREF colorFinish2,  
    BOOL bHorz = TRUE,  
    int nPercentage = 50);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`rect`  
 Rámeček k vyplnění.  
  
 [v]`colorStart1`  
 Počáteční barvu pro první přechod barev.  
  
 [v]`colorFinish1`  
 Poslední barvu pro první přechod barev.  
  
 [v]`colorStart2`  
 Počáteční barvu pro druhý přechod barev.  
  
 [v]`colorFinish2`  
 Poslední barvu pro druhý přechod barev.  
  
 [v]`bHorz`  
 Parametr typu Boolean, která určuje, zda `Fill4ColorsGradient` barvy přechodu vodorovně nebo svisle. `TRUE`Určuje vodorovný přechod.  
  
 [v]`nPercentage`  
 Celé číslo od 0 – 100. Tato hodnota informuje o procentu rámeček vyplníte první přechod barev.  
  
### <a name="remarks"></a>Poznámky  
 Když obdélníku, naplní se dvěma barevné přechody, jsou umístěné výše navzájem nebo další mezi sebou, v závislosti na hodnotě `bHorz`. Každý přechod barev se počítá samostatně pomocí metody [CDrawingManager::FillGradient](#fillgradient).  
  
 Tato metoda generuje chybu assertion Pokud `nPercentage` je menší než 0 nebo více než 100.  
  
##  <a name="fillgradient"></a>CDrawingManager::FillGradient  
 Zadaná barva přechodu vyplní obdélníkovou oblast.  
  
```  
void FillGradient(
    CRect rect,  
    COLORREF colorStart,  
    COLORREF colorFinish,  
    BOOL bHorz = TRUE,  
    int nStartFlatPercentage = 0,  
    int nEndFlatPercentage = 0);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`rect`  
 Obdélníkovou oblast k vyplnění.  
  
 [v]`colorStart`  
 První barva přechodu.  
  
 [v]`colorFinish`  
 Poslední barva přechodu.  
  
 [v]`bHorz`  
 Logický parametr, který určuje, zda `FillGradient` vykreslován vodorovně nebo svisle přechodu.  
  
 [v]`nStartFlatPercentage`  
 Procento obdélníku, který `FillGradient` vyplní `colorStart` před spuštěním přechodu.  
  
 [v]`nEndFlatPercentage`  
 Procento obdélníku, která `FillGradient` vyplní `colorFinish` po jejím dokončení přechodu.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `FillGradient` metodu `CDrawingManager` třídy. Tento fragment kódu je součástí [MS Office 2007 Demo-ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#12](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_2.cpp)]  
  
##  <a name="fillgradient2"></a>CDrawingManager::FillGradient2  
 Zadaná barva přechodu vyplní obdélníkovou oblast.  
  
```  
void FillGradient2 (
    CRect rect,  
    COLORREF colorStart,  
    COLORREF colorFinish,  
    int nAngle = 0);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`rect`  
 Obdélníkovou oblast k vyplnění.  
  
 [v]`colorStart`  
 První barva barevného přechodu.  
  
 [v]`colorFinish`  
 Poslední barva barevného přechodu.  
  
 [v]`nAngle`  
 Celé číslo od 0 do 360. Tento parametr určuje směr přechod barev.  
  
### <a name="remarks"></a>Poznámky  
 Použití `nAngle` k určení směru přechodu barvy. Když zadáte směr přechod barev, také určit, kde začíná přechod barev. Hodnota 0 pro `nAngle` informuje začne má barevný přechod z horní části rámeček. Jako `nAngle` zvyšuje, výchozí umístění pro přechodu posouvá směrem k proti směru hodinových ručiček o úhel podle.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `FillGradient2` metodu `CDrawingManager` třídy. Tento fragment kódu je součástí [nové ovládací prvky ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#37](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_3.cpp)]  
  
##  <a name="grayrect"></a>CDrawingManager::GrayRect  
 Vyplní obdélníku zadaný šedou barvu.  
  
```  
BOOL GrayRect(
    CRect rect,  
    int nPercentage = -1,  
    COLORREF clrTransparent = (COLORREF)-1,  
    COLORREF clrDisabled = (COLORREF)-1);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`rect`  
 Obdélníkovou oblast k vyplnění.  
  
 [v]`nPercentage`  
 Procento šedé, které chcete v obdélníku.  
  
 [v]`clrTransparent`  
 Průhledná barva.  
  
 [v]`clrDisabled`  
 Barvu, která tato metoda používá pro deaktivace sytost Pokud `nPercentage` je nastaven na hodnotu -1.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud metoda byla úspěšná. v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Pro parametr `nPercentage`, nižší hodnota znamená tmavší barva.  
  
 Maximální hodnota `nPercentage` je 200. Hodnota, která je větší než 200 nezmění vzhled rámečku. Pokud je hodnota -1, tato metoda používá `clrDisabled` omezit sytost rámeček.  
  
##  <a name="highlightrect"></a>CDrawingManager::HighlightRect  
 Označuje obdélníkovou oblast.  
  
```  
BOOL HighlightRect(
    CRect rect,  
    int nPercentage = -1,  
    COLORREF clrTransparent = (COLORREF)-1,  
    int nTolerance = 0,  
    COLORREF clrBlend = (COLORREF)-1);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`rect`  
 Obdélníkovou oblast, abyste měli na očích.  
  
 [v]`nPercentage`  
 Procento, která určuje, jak transparentní by měla být zvýraznění.  
  
 [v]`clrTransparent`  
 Průhledná barva.  
  
 [v]`nTolerance`  
 Celé číslo mezi 0 a 255, která určuje barvu tolerance.  
  
 [v]`clrBlend`  
 Základní barva prolnutí.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud je metoda úspěšná. v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `nPercentage` je od 0 do 99, `HighlightRect` používá alfa míchání algoritmus. Další informace o alfa míchání najdete v tématu [alfa míchání čar a výplní](/dotnet/framework/winforms/advanced/alpha-blending-lines-and-fills). Pokud `nPercentage` -1, je tato metoda používá výchozí úroveň zvýraznění. Pokud `nPercentage` je 100, tato metoda neprovede žádnou akci a vrátí `TRUE`.  
  
 Metoda používá parametr `nTolerance` k určení, zda se mají zvýrazňovat obdélníkovou oblast. Abyste měli na očích rámeček rozdíl mezi barvu pozadí vaší aplikace a `clrTransparent` musí být menší než `nTolerance` v jednotlivých komponentách barvy (červená, zelená a modrá).  
  
##  <a name="hlstorgb_one"></a>CDrawingManager::HLStoRGB_ONE  
 Převede barvu, která z reprezentace HLS znázornění RGB.  
  
```  
static COLORREF __stdcall HLStoRGB_ONE(
    double H,  
    double L,  
    double S);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`H`  
 Číslo mezi 0 a 1, který představuje odstín barvy.  
  
 [v]`L`  
 Číslo mezi 0 a 1, která určuje Světelnost barvy.  
  
 [v]`S`  
 Číslo mezi 0 a 1 určující sytost barvy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Reprezentace RGB zadaná barva HLS.  
  
### <a name="remarks"></a>Poznámky  
 Barvu, která může být reprezentován jako HSV (hue, sytost a hodnota), HSL (hue, sytost a světlost) nebo RGB (červená, zelená a modrá). Další informace o různých reprezentace barva najdete v tématu [barva](http://go.microsoft.com/fwlink/p/?linkid=119126).  
  
 Tato metoda a `CDrawingManager::HLStoRGB_TWO` metoda provádět stejné operace, ale vyžadují různé hodnoty pro `H` parametr. Tato metoda `H` je procento kruhu. V `CDrawingManager::HLStoRGB_TWO` metody `H` je stupeň hodnotu od 0 do 360, které obě představují red. Například s `HLStoRGB_ONE`, hodnotu 0,25 pro `H` je ekvivalentní hodnotě 90 s `HLStoRGB_TWO`.  
  
##  <a name="hlstorgb_two"></a>CDrawingManager::HLStoRGB_TWO  
 Převede barvu, která z reprezentace HLS znázornění RGB.  
  
```  
static COLORREF __stdcall HLStoRGB_TWO(
    double H,  
    double L,  
    double S);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`H`  
 Číslo od 0 do 360, které představuje odstín barvy.  
  
 [v]`L`  
 Číslo mezi 0 a 1, která určuje Světelnost barvy.  
  
 [v]`S`  
 Číslo mezi 0 a 1 určující sytost barvy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Reprezentace RGB zadaná barva HLS.  
  
### <a name="remarks"></a>Poznámky  
 Barvu, která může být reprezentován jako HSV (hue, sytost a hodnota), HSL (hue, sytost a světlost) nebo RGB (červená, zelená a modrá). Další informace o různých reprezentace barva najdete v tématu [barva](http://go.microsoft.com/fwlink/p/?linkid=119126).  
  
 Tato metoda a [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one) metoda provádět stejné operace, ale vyžadují různé hodnoty pro `H` parametr. Tato metoda `H` je stupeň hodnotu od 0 do 360, které obě představují red. V [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one) metody `H` je procento kruhu. Například s `HLStoRGB_ONE`, hodnotu 0,25 pro `H` je ekvivalentní hodnotě 90 s `HLStoRGB_TWO`.  
  
##  <a name="hsvtorgb"></a>CDrawingManager::HSVtoRGB  
 Převede barvu, která z reprezentace HSV znázornění RGB.  
  
```  
static COLORREF __stdcall HSVtoRGB(
    double H,  
    double S,  
    double V);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v]`H`|Číslo od 0 do 360, která určuje odstín barvy.|  
|[v]`S`|Číslo mezi 0 a 1 určující sytost barvy.|  
|[v]`V`|Číslo mezi 0 a 1, který určuje hodnotu barvy.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Reprezentace RGB barvu HSV zadat.  
  
### <a name="remarks"></a>Poznámky  
 Barvu, která může být reprezentován jako HSV (hue, sytost a hodnota), HSL (hue, sytost a světlost) nebo RGB (červená, zelená a modrá). Další informace o různých reprezentace barva najdete v tématu [barva](http://go.microsoft.com/fwlink/p/?linkid=119126).  
  
##  <a name="huetorgb"></a>CDrawingManager::HuetoRGB  
 Převede hodnotu hue červené, zelené nebo modré součásti.  
  
```  
static double __stdcall HuetoRGB(
    double m1,  
    double m2,  
    double h);

 
static BYTE __stdcall HueToRGB(
    float rm1,  
    float rm2,  
    float rh);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`m1`  
 V části poznámky.  
  
 [v]`m2`  
 V části poznámky.  
  
 [v]`h`  
 V části poznámky.  
  
 [v]`rm1`  
 V části poznámky.  
  
 [v]`rm2`  
 V části poznámky.  
  
 [v]`rh`  
 V části poznámky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jednotlivé červené, zelené nebo modré komponentu pro zadaný hue.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je metoda helper, `CDrawingManager` třídy používá k výpočtu jednotlivých součástí červené, zelené a modré barvy v HSV nebo HSL reprezentace. Tato metoda není určena k volání přímo z programátorů. Vstupní parametry jsou hodnoty, které závisí na převod algoritmu.  
  
 Převést HSV nebo HSL barva RGB reprezentaci, volání jednoho z následujících metod:  
  
- [CDrawingManager::HSVtoRGB](#hsvtorgb)  
  
- [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)  
  
- [CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)  
  
##  <a name="mirrorrect"></a>CDrawingManager::MirrorRect  
 Převrátí obdélníkovou oblast.  
  
```  
void MirrorRect(
    CRect rect,  
    BOOL bHorz = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`rect`  
 Ohraničující obdélník oblasti k převrácení.  
  
 [v]`bHorz`  
 Parametr typu Boolean, která určuje, zda rámeček převrátí vodorovně nebo svisle.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu můžete překlopit všechny plochy kontextu zařízení ve vlastnictví `CDrawingManager` třídy. Pokud `bHorz` je nastaven na `TRUE`, tato metoda vodorovně převrátí oblasti. Jinak se Překlopí oblasti svisle.  
  
##  <a name="pixelalpha"></a>CDrawingManager::PixelAlpha  
 Vypočítá konečné barvu poloprůhledných pixelů.  
  
```  
static COLORREF __stdcall PixelAlpha(
    COLORREF srcPixel,  
    int percent);
 
static COLORREF __stdcall PixelAlpha(
    COLORREF srcPixel,  
    double percentR,  
    double percentG,  
    double percentB);

static COLORREF __stdcall PixelAlpha(
    COLORREF srcPixel,  
    COLORREF dstPixel,  
    int percent);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`srcPixel`  
 Počáteční barvu pixelech.  
  
 [v]`percent`  
 Číslo mezi 0 a 100, který představuje procento průhlednosti. Hodnota 100 označuje, že počáteční barvu je zcela transparentní.  
  
 [v]`percentR`  
 Číslo mezi 0 a 100, který představuje procento průhlednost pro komponentu red.  
  
 [v]`percentG`  
 Číslo mezi 0 a 100, který představuje procento průhlednost pro komponentu zelená.  
  
 [v]`percentB`  
 Číslo mezi 0 a 100, který představuje procento průhlednost pro komponentu blue.  
  
 [v]`dstPixel`  
 Základní barva pixelech.  
  
### <a name="return-value"></a>Návratová hodnota  
 Poslední barva poloprůhledných pixelů.  
  
### <a name="remarks"></a>Poznámky  
 Toto je pomocná třída pro zvýrazňování poloprůhledných rastrové obrázky a není určená k volání přímo z programátorů.  
  
 Pokud používáte verzi metody, která má `dstPixel`, konečnou barvu je kombinací `dstPixel` a `srcPixel`. `srcPixel` Barva je částečně průhledná barva nad základní barva `dstPixel`.  
  
##  <a name="prepareshadowmask"></a>CDrawingManager::PrepareShadowMask  
 Vytvoří rastrového obrázku, který lze použít jako stínu.  
  
```  
static HBITMAP __stdcall PrepareShadowMask (
    int nDepth,  
    COLORREF clrBase,  
    int iMinBrightness = 0,  
    int iMaxBrightness = 100);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nDepth`  
 Šířka a výška stínové kopie.  
  
 [v]`clrBase`  
 Barvu stínu.  
  
 [v]`iMinBrightness`  
 Minimální také průraznost stínu.  
  
 [v]`iMaxBrightness`  
 Maximální také průraznost stínu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro vytvoření rastrového obrázku, pokud tato metoda je úspěšné; v opačném případě `NULL`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `nDepth` je nastaven na 0, tato metoda ukončí a vrátí `NULL`. Pokud `nDepth` je menší než 3, šířku a výšku stínu jsou nastaveny na 3 pixelů.  
  
##  <a name="rgbtohsl"></a>CDrawingManager::RGBtoHSL  
 Převede barvu, která z reprezentace (RGB) červené, zelené a modré hue, sytost a reprezentace světlost (HSL –).  
  
```  
static void __stdcall RGBtoHSL(
    COLORREF rgb,  
    double* H,  
    double* S,  
    double* L);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v]`rgb`|Barva RGB hodnoty.|  
|[out]`H`|Ukazatel na dvojitou, kde Metoda ukládá odstín barvy.|  
|[out]`S`|Ukazatel na dvojitou, kde Metoda ukládá sytost barvy.|  
|[out]`L`|Ukazatel na dvojitou, kde Metoda ukládá světlost barvy.|  
  
### <a name="remarks"></a>Poznámky  
 Barvu, která může být reprezentován jako HSV (hue, sytost a hodnota), HSL (hue, sytost a světlost) nebo RGB (červená, zelená a modrá). Další informace o různých reprezentace barva najdete v tématu [barva](http://go.microsoft.com/fwlink/p/?linkid=119126).  
  
 Vrácená hodnota pro `H` je reprezentována jako desetinné číslo mezi 0 a 1, kde 0 a 1 představují red. Vrácené hodnoty `S` a `L` jsou čísla od 0 do 1.  
  
##  <a name="rgbtohsv"></a>CDrawingManager::RGBtoHSV  
 Převede barvu, která z reprezentace RGB na znázornění HSV.  
  
```  
static void __stdcall RGBtoHSV(
    COLORREF rgb,  
    double* H,  
    double* S,  
    double* V);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`rgb`  
 Barva převod reprezentace RGB.  
  
 [out]`H`  
 Ukazatel na dvojitou, kde tato metoda ukládá výsledné odstín barvy.  
  
 [out]`S`  
 Ukazatel na dvojitou, kde tato metoda ukládá výsledné sytost barvy.  
  
 [out]`V`  
 Ukazatel na dvojitou, kde tato metoda ukládá výslednou hodnotu pro tuto barvu.  
  
### <a name="remarks"></a>Poznámky  
 Barvu, která může být reprezentován jako HSV (hue, sytost a hodnota), HSL (hue, sytost a světlost) nebo RGB (červená, zelená a modrá). Další informace o různých reprezentace barva najdete v tématu [barva](http://go.microsoft.com/fwlink/p/?linkid=119126).  
  
 Vrácená hodnota pro `H` je číslo v rozsahu od 0 do 360, kde 0 až 360 znamenat red. Vrácení hodnoty pro `S` a `V` jsou čísla od 0 do 1.  
  
##  <a name="setalphapixel"></a>CDrawingManager::SetAlphaPixel  
 Barvy transparentní pixelů v rastrový obrázek.  
  
```  
static void __stdcall SetAlphaPixel(
    COLORREF* pBits,  
    CRect rect,  
    int x,  
    int y,  
    int percent,  
    int iShadowSize,  
    COLORREF clrBase = (COLORREF)-1,  
    BOOL bIsRight = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pBits`  
 Ukazatel na bitových hodnot pro bitovou mapu.  
  
 [v]`rect`  
 Obdélníkovou oblast v aplikaci. Kreslení manager nevykresluje stínové pod a napravo od této oblasti.  
  
 [v]`x`  
 Vodorovné souřadnice pixelů na barvu.  
  
 [v]`y`  
 Svislé souřadnice pixelů na barvu.  
  
 [v]`percent`  
 Procento průhlednost.  
  
 [v]`iShadowSize`  
 Šířka a výška stínové kopie.  
  
 [v]`clrBase`  
 Barvu stínu.  
  
 [v]`bIsRight`  
 Parametr typu Boolean, která určuje, které pixelů na barvu. Další informace naleznete v části Poznámky.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je pomocná metoda, která je používána [CDrawingManager::DrawShadow](#drawshadow) metoda. Doporučujeme, pokud chcete k vykreslení stín, volání `CDrawingManager::DrawShadow` místo.  
  
 Pokud `bIsRight` je nastaven na `TRUE`, se měří pixelů na barvu `x` pixelů z pravé hrany `rect`. Pokud je `FALSE`, se měří pixelů na barvu `x` pixelů od levého okraje `rect`.  
  
##  <a name="setpixel"></a>CDrawingManager::SetPixel  
 Zadaná barva změny jedinému pixelu rastrový obrázek.  
  
```  
static void __stdcall SetPixel(
    COLORREF* pBits,  
    int cx,  
    int cy,  
    int x,  
    int y,  
    COLORREF color);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v]`pBits`|Ukazatel na bitových hodnot bitmapy.|  
|[v]`cx`|Celková šířka rastrového obrázku.|  
|[v]`cy`|Celková výška bitové mapy.|  
|[v]`x`|Souřadnici x pixelů v souboru bitové mapy, chcete-li změnit.|  
|[v]`y`|Souřadnice y pixelů v souboru bitové mapy, chcete-li změnit.|  
|[v]`color`|Nové barva pixelů identifikovaný zadaný souřadnice.|  
  
##  <a name="smartmixcolors"></a>CDrawingManager::SmartMixColors  
 Kombinuje dvě barvy na základě vyvážené poměru.  
  
```  
static COLORREF __stdcall SmartMixColors(
    COLORREF color1,  
    COLORREF color2,  
    double dblLumRatio = 1.,  
    int k1 = 1,  
    int k2 = 1);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v]`color1`|První barvu, která kombinovat.|  
|[v]`color2`|Druhý barvu, která kombinovat.|  
|[v]`dblLumRatio`|Poměr pro světelnost nové barvy. `SmartMixColors`Vynásobí svítivost smíšený barvy tento poměr před určení konečné barvy.|  
|[v]`k1`|Vážený poměr pro první barvy.|  
|[v]`k2`|Vážený poměr druhý barvy.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Barvu, která představuje vyvážené směs zadaný barvy.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda selže s chybou, pokud má jedna `k1` nebo `k2` je menší než nula. Pokud jsou oba tyto parametry nastavit na hodnotu 0, vrátí metoda `RGB(0, 0, 0)`.  
  
 Vážený poměr se počítá pomocí tohoto vzorce: (barvou1 * k1 + barva2 \* k2) /(k1 + k2). Po vyvážené poměr je určený, vypočítá metodu světelnost smíšený barvy. Poté pracuje světelnost podle `dblLumRatio`. Pokud je hodnota větší než 1.0, metoda nastaví světelnost smíšený barvy na novou hodnotu. Světelnost, jinak hodnota nastavena na 1.0.  
  
##  <a name="drawrotated"></a>CDrawingManager::DrawRotated  
 Otočí zdroj obsahu řadiče domény v dané obdélníku o 90 stupňů.  
  
```  
void DrawRotated(
    CRect rectDest,  
    CDC& dcSrc,  
    BOOL bClockWise);
```  
  
### <a name="parameters"></a>Parametry  
 `rectDest`  
 Cílový obdélník.  
  
 `dcSrc`  
 Kontext zařízení zdroje.  
  
 `bClockWise`  
 `TRUE`Určuje otočení + 90 stupňů; `FALSE` označuje otáčení-90 stupňů.  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)
