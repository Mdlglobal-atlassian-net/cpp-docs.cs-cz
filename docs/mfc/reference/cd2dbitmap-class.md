---
title: "Třída CD2DBitmap | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DBitmap
- AFXRENDERTARGET/CD2DBitmap
- AFXRENDERTARGET/CD2DBitmap::CD2DBitmap
- AFXRENDERTARGET/CD2DBitmap::Attach
- AFXRENDERTARGET/CD2DBitmap::CopyFromBitmap
- AFXRENDERTARGET/CD2DBitmap::CopyFromMemory
- AFXRENDERTARGET/CD2DBitmap::CopyFromRenderTarget
- AFXRENDERTARGET/CD2DBitmap::Create
- AFXRENDERTARGET/CD2DBitmap::Destroy
- AFXRENDERTARGET/CD2DBitmap::Detach
- AFXRENDERTARGET/CD2DBitmap::Get
- AFXRENDERTARGET/CD2DBitmap::GetDPI
- AFXRENDERTARGET/CD2DBitmap::GetPixelFormat
- AFXRENDERTARGET/CD2DBitmap::GetPixelSize
- AFXRENDERTARGET/CD2DBitmap::GetSize
- AFXRENDERTARGET/CD2DBitmap::IsValid
- AFXRENDERTARGET/CD2DBitmap::CommonInit
- AFXRENDERTARGET/CD2DBitmap::m_bAutoDestroyHBMP
- AFXRENDERTARGET/CD2DBitmap::m_hBmpSrc
- AFXRENDERTARGET/CD2DBitmap::m_lpszType
- AFXRENDERTARGET/CD2DBitmap::m_pBitmap
- AFXRENDERTARGET/CD2DBitmap::m_sizeDest
- AFXRENDERTARGET/CD2DBitmap::m_strPath
- AFXRENDERTARGET/CD2DBitmap::m_uiResID
dev_langs:
- C++
helpviewer_keywords:
- CD2DBitmap [MFC], CD2DBitmap
- CD2DBitmap [MFC], CD2DBitmap
- CD2DBitmap [MFC], Attach
- CD2DBitmap [MFC], CopyFromBitmap
- CD2DBitmap [MFC], CopyFromMemory
- CD2DBitmap [MFC], CopyFromRenderTarget
- CD2DBitmap [MFC], Create
- CD2DBitmap [MFC], Destroy
- CD2DBitmap [MFC], Detach
- CD2DBitmap [MFC], Get
- CD2DBitmap [MFC], GetDPI
- CD2DBitmap [MFC], GetPixelFormat
- CD2DBitmap [MFC], GetPixelSize
- CD2DBitmap [MFC], GetSize
- CD2DBitmap [MFC], IsValid
- CD2DBitmap [MFC], CommonInit
- CD2DBitmap [MFC], m_bAutoDestroyHBMP
- CD2DBitmap [MFC], m_hBmpSrc
- CD2DBitmap [MFC], m_lpszType
- CD2DBitmap [MFC], m_pBitmap
- CD2DBitmap [MFC], m_sizeDest
- CD2DBitmap [MFC], m_strPath
- CD2DBitmap [MFC], m_uiResID
ms.assetid: 2b3686f1-812c-462b-b449-9f0cb6949bf6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 967bad02cf92b0078d789e5c0b6b55f9644bb17b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cd2dbitmap-class"></a>CD2DBitmap – třída
Obálka pro ID2D1Bitmap.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CD2DBitmap : public CD2DResource;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DBitmap::CD2DBitmap](#cd2dbitmap)|Přetíženo. Vytvoří objekt CD2DBitmap z HBITMAP.|  
|[CD2DBitmap:: ~ CD2DBitmap](#_dtorcd2dbitmap)|Destruktor. Voláno, když je zničen objektu D2D rastrového obrázku.|  
  
### <a name="protected-constructors"></a>Chráněné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DBitmap::CD2DBitmap](#cd2dbitmap)|Přetíženo. Vytvoří objekt CD2DBitmap.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DBitmap::Attach](#attach)|Připojí existující prostředek rozhraní k objektu|  
|[CD2DBitmap::CopyFromBitmap](#copyfrombitmap)|Zkopíruje zadané oblasti ze zadaného bitové mapy do aktuální rastrového obrázku|  
|[CD2DBitmap::CopyFromMemory](#copyfrommemory)|Zkopíruje zadané oblasti z paměti do aktuální rastrového obrázku|  
|[CD2DBitmap::CopyFromRenderTarget](#copyfromrendertarget)|Kopie zadané oblasti ze zadaného vykreslení cíl do aktuální rastrového obrázku|  
|[CD2DBitmap::Create](#create)|Vytvoří CD2DBitmap. (Přepisuje [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|  
|[CD2DBitmap::Destroy](#destroy)|Zničí CD2DBitmap objektu. (Přepisuje [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|  
|[CD2DBitmap::detach](#detach)|Umožňuje odpojit prostředek rozhraní z objektu|  
|[CD2DBitmap::Get](#get)|Vrátí ID2D1Bitmap rozhraní|  
|[CD2DBitmap::GetDPI](#getdpi)|Vrátí bodů na palec (DPI) bitmapy|  
|[CD2DBitmap::GetPixelFormat](#getpixelformat)|Načte pixelů formátu a alpha režimu bitové mapy|  
|[CD2DBitmap::GetPixelSize](#getpixelsize)|Vrátí velikost v jednotky závislé na zařízení (v pixelech), bitmapy|  
|[CD2DBitmap::GetSize](#getsize)|Vrátí velikost v pixelech nezávislé na zařízení (vyhrazené), bitmapy|  
|[CD2DBitmap::IsValid](#isvalid)|Ověří platnost prostředku (přepíše [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DBitmap::CommonInit](#commoninit)|Inicializuje objekt|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DBitmap::Operator ID2D1Bitmap *](#operator_id2d1bitmap_star)|Vrátí ID2D1Bitmap rozhraní|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DBitmap::m_bAutoDestroyHBMP](#m_bautodestroyhbmp)|Hodnota TRUE, pokud by měl být zničený, m_hBmpSrc; jinak hodnota FALSE.|  
|[CD2DBitmap::m_hBmpSrc](#m_hbmpsrc)|Popisovač zdroje rastrového obrázku.|  
|[CD2DBitmap::m_lpszType](#m_lpsztype)|Typ prostředku.|  
|[CD2DBitmap::m_pBitmap](#m_pbitmap)|Ukládá ukazatel na objekt ID2D1Bitmap.|  
|[CD2DBitmap::m_sizeDest](#m_sizedest)|Bitmap – velikost cílového.|  
|[CD2DBitmap::m_strPath](#m_strpath)|Cesta k souboru Botmap.|  
|[CD2DBitmap::m_uiResID](#m_uiresid)|Bitmap – ID prostředku.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 `CD2DBitmap`
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxrendertarget.h  
  
##  <a name="_dtorcd2dbitmap"></a>CD2DBitmap:: ~ CD2DBitmap  
 Destruktor. Voláno, když je zničen objektu D2D rastrového obrázku.  
  
```  
virtual ~CD2DBitmap();
```  
  
##  <a name="attach"></a>CD2DBitmap::Attach  
 Připojí existující prostředek rozhraní k objektu  
  
```  
void Attach(ID2D1Bitmap* pResource);
```  
  
### <a name="parameters"></a>Parametry  
 `pResource`  
 Existující rozhraní prostředků. Nemůže mít hodnotu NULL  
  
##  <a name="cd2dbitmap"></a>CD2DBitmap::CD2DBitmap  
 Vytvoří objekt CD2DBitmap z prostředku.  
  
```  
CD2DBitmap(
    CRenderTarget* pParentTarget,  
    UINT uiResID,  
    LPCTSTR lpszType = NULL,  
    CD2DSizeU sizeDest = CD2DSizeU(0, 0), 
    BOOL bAutoDestroy = TRUE);

 
CD2DBitmap(
    CRenderTarget* pParentTarget,  
    LPCTSTR lpszPath,  
    CD2DSizeU sizeDest = CD2DSizeU(0, 0), 
    BOOL bAutoDestroy = TRUE);

 
CD2DBitmap(
    CRenderTarget* pParentTarget,  
    HBITMAP hbmpSrc,  
    CD2DSizeU sizeDest = CD2DSizeU(0, 0), 
    BOOL bAutoDestroy = TRUE);

 
CD2DBitmap(
    CRenderTarget* pParentTarget,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentTarget`  
 Ukazatel na cíl vykreslení.  
  
 `uiResID`  
 Číslo ID prostředku prostředku.  
  
 `lpszType`  
 Ukazatel na řetězec ukončené hodnotou null, který obsahuje typ prostředku.  
  
 `sizeDest`  
 Velikost cílového bitmapy.  
  
 `bAutoDestroy`  
 Označuje, že bude objekt zničí vlastník (pParentTarget).  
  
 `lpszPath`  
 Ukazatel na řetězec ukončené hodnotou null, který obsahuje název souboru.  
  
 `hbmpSrc`  
 Popisovač bitové mapy.  
  
##  <a name="commoninit"></a>CD2DBitmap::CommonInit  
 Inicializuje objekt  
  
```  
void CommonInit();
```  
  
##  <a name="copyfrombitmap"></a>CD2DBitmap::CopyFromBitmap  
 Zkopíruje zadané oblasti ze zadaného bitové mapy do aktuální rastrového obrázku  
  
```  
HRESULT CopyFromBitmap(
    const CD2DBitmap* pBitmap,  
    const CD2DPointU* destPoint = NULL,  
    const CD2DRectU* srcRect = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pBitmap`  
 Rastrový obrázek pro kopírování z  
  
 `destPoint`  
 V aktuální rastrového obrázku levém horním rohu oblasti, ke které oblasti určeného srcRect zkopírován  
  
 `srcRect`  
 Oblasti rastrový obrázek ke zkopírování  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí S_OK. Funkce HRESULT chybový kód.  
  
##  <a name="copyfrommemory"></a>CD2DBitmap::CopyFromMemory  
 Zkopíruje zadané oblasti z paměti do aktuální rastrového obrázku  
  
```  
HRESULT CopyFromMemory(
    const void* srcData,  
    UINT32 pitch,  
    const CD2DRectU* destRect = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `srcData`  
 Data ke zkopírování  
  
 `pitch`  
 Stride nebo výška, uložené v srcData bitmapy zdroje. Stride je počet bajtů řádkového rozkladu (jeden řádek pixelů v paměti). Stride můžete vypočítaný z tohoto vzorce: šířka v pixelech * bajtů za pixelů + paměti odsazení  
  
 `destRect`  
 V aktuální rastrového obrázku levém horním rohu oblasti, ke které oblasti určeného srcRect zkopírován  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí S_OK. Funkce HRESULT chybový kód.  
  
##  <a name="copyfromrendertarget"></a>CD2DBitmap::CopyFromRenderTarget  
 Kopie zadané oblasti ze zadaného vykreslení cíl do aktuální rastrového obrázku  
  
```  
HRESULT CopyFromRenderTarget(
    const CRenderTarget* pRenderTarget,  
    const CD2DPointU* destPoint = NULL,  
    const CD2DRectU* srcRect = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pRenderTarget`  
 Vykreslení cíl, který obsahuje oblast pro kopírování  
  
 `destPoint`  
 V aktuální rastrového obrázku levém horním rohu oblasti, ke které oblasti určeného srcRect zkopírován  
  
 `srcRect`  
 Oblasti RenderTarget ke kopírování.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí S_OK. Funkce HRESULT chybový kód.  
  
##  <a name="create"></a>CD2DBitmap::Create  
 Vytvoří CD2DBitmap.  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `pRenderTarget`  
 Ukazatel na cíl vykreslení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí S_OK. Funkce HRESULT chybový kód.  
  
##  <a name="destroy"></a>CD2DBitmap::Destroy  
 Zničí CD2DBitmap objektu.  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>CD2DBitmap::detach  
 Umožňuje odpojit prostředek rozhraní z objektu  
  
```  
ID2D1Bitmap* Detach();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel rozhraní odpojit prostředků.  
  
##  <a name="get"></a>CD2DBitmap::Get  
 Vrátí ID2D1Bitmap rozhraní  
  
```  
ID2D1Bitmap* Get();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na rozhraní ID2D1Bitmap nebo hodnota NULL, pokud objekt dosud není inicializován.  
  
##  <a name="getdpi"></a>CD2DBitmap::GetDPI  
 Vrátí bodů na palec (DPI) bitmapy  
  
```  
CD2DSizeF GetDPI() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vodorovného a svislého DPI bitové mapy.  
  
##  <a name="getpixelformat"></a>CD2DBitmap::GetPixelFormat  
 Načte pixelů formátu a alpha režimu bitové mapy  
  
```  
D2D1_PIXEL_FORMAT GetPixelFormat() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pixelů formátu a alpha režim bitmapy.  
  
##  <a name="getpixelsize"></a>CD2DBitmap::GetPixelSize  
 Vrátí velikost v jednotky závislé na zařízení (v pixelech), bitmapy  
  
```  
CD2DSizeU GetPixelSize() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Velikost v pixelech bitovou mapu...  
  
##  <a name="getsize"></a>CD2DBitmap::GetSize  
 Vrátí velikost v pixelech nezávislé na zařízení (vyhrazené), bitmapy  
  
```  
CD2DSizeF GetSize() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Velikost v vyhrazené IP adresy, bitmapy.  
  
##  <a name="isvalid"></a>CD2DBitmap::IsValid  
 Kontrola platnosti prostředků  
  
```  
virtual BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud prostředek je platná. jinak hodnota FALSE.  
  
##  <a name="m_bautodestroyhbmp"></a>CD2DBitmap::m_bAutoDestroyHBMP  
 Hodnota TRUE, pokud by měl být zničený, m_hBmpSrc; jinak hodnota FALSE.  
  
```  
BOOL m_bAutoDestroyHBMP;  
```  
  
##  <a name="m_hbmpsrc"></a>CD2DBitmap::m_hBmpSrc  
 Popisovač zdroje rastrového obrázku.  
  
```  
HBITMAP m_hBmpSrc;  
```  
  
##  <a name="m_lpsztype"></a>CD2DBitmap::m_lpszType  
 Typ prostředku.  
  
```  
LPCTSTR m_lpszType;  
```  
  
##  <a name="m_pbitmap"></a>CD2DBitmap::m_pBitmap  
 Ukládá ukazatel na objekt ID2D1Bitmap.  
  
```  
ID2D1Bitmap* m_pBitmap;  
```  
  
##  <a name="m_sizedest"></a>CD2DBitmap::m_sizeDest  
 Bitmap – velikost cílového.  
  
```  
CD2DSizeU m_sizeDest;  
```  
  
##  <a name="m_strpath"></a>CD2DBitmap::m_strPath  
 Cesta k souboru Botmap.  
  
```  
CString m_strPath;  
```  
  
##  <a name="m_uiresid"></a>CD2DBitmap::m_uiResID  
 Bitmap – ID prostředku.  
  
```  
UINT m_uiResID;  
```  
  
##  <a name="operator_id2d1bitmap_star"></a>CD2DBitmap::Operator ID2D1Bitmap *  
 Vrátí ID2D1Bitmap rozhraní  
  
```  
operator ID2D1Bitmap*();
```   
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na rozhraní ID2D1Bitmap nebo hodnota NULL, pokud objekt dosud není inicializován.  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
