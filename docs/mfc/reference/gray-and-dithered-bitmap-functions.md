---
title: "Funkce gray a Dithered pro bitové mapy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AFXWIN/AfxDrawGrayBitmap
- AFXWIN/AfxGetGrayBitmap
- AFXWIN/AfxDrawDitheredBitmap
- AFXWIN/AfxGetDitheredBitmap
dev_langs: C++
helpviewer_keywords: gray and dithered bitmap functions [MFC]
ms.assetid: cb139a77-b85e-4504-9d93-24156ad77a41
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 372fd343bbca8bfac4ec31a34b3920cf29d35957
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="gray-and-dithered-bitmap-functions"></a>Funkce Gray a Dithered pro bitové mapy
**Funkce Gray bitové mapy**  
  
 MFC poskytuje dvě funkce pro poskytnutí rastrový obrázek vzhledu ovládacího prvku zakázané.  
  
 ![Porovnání ikona šedé a původní verze](../../mfc/reference/media/vcgraybitmap.gif "vcgraybitmap")  
  
|||  
|-|-|  
|[Afxdrawgraybitmap –](#afxdrawgraybitmap)|Nakreslí šedé verzi rastrový obrázek.|  
|[Afxgetgraybitmap –](#afxgetgraybitmap)|Zkopíruje šedé verzi rastrový obrázek.|  
  
 **Funkce dithered pro bitové mapy**  
  
 MFC také poskytuje dvě funkce pro nahrazení rastrový obrázek pozadí tónovaná vzor.  
  
 ![Porovnání ikona tónovaná a původní verze](../../mfc/reference/media/vcditheredbitmap.gif "vcditheredbitmap")  
  
|||  
|-|-|  
|[Afxdrawditheredbitmap –](#afxdrawditheredbitmap)|Nakreslí bitmap s tónovaná pozadí.|  
|[Afxgetditheredbitmap –](#afxgetditheredbitmap)|Zkopíruje bitmap s tónovaná pozadí.|  
  
##  <a name="afxdrawgraybitmap"></a>Afxdrawgraybitmap –  
 Nakreslí šedé verzi rastrový obrázek.  
  
```   
void AFXAPI AfxDrawGrayBitmap(
    CDC* pDC,  
    int x,  
    int y,  
    const CBitmap& rSrc,  
    COLORREF crBackground); 
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Odkazuje na cílový řadič domény.  
  
 *x*  
 Cílový souřadnici x.  
  
 *y*  
 Cílový souřadnici y.  
  
 `rSrc`  
 Zdroj bitové mapy.  
  
 `crBackground`  
 Nové barvu pozadí (obvykle zašedlé, jako je například COLOR_MENU).  
  
### <a name="remarks"></a>Poznámky  
 Rastrový obrázek vykreslené s `AfxDrawGrayBitmap` bude mít vzhledu ovládacího prvku zakázané.  
  
 ![Porovnání ikona šedé a původní verze](../../mfc/reference/media/vcgraybitmap.gif "vcgraybitmap")  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#191](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_1.cpp)]  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  

##  <a name="afxgetgraybitmap"></a>Afxgetgraybitmap –  
 Zkopíruje šedé verzi rastrový obrázek.  
  
```   
void AFXAPI AfxGetGrayBitmap(
    const CBitmap& rSrc,  
    CBitmap* pDest,  
    COLORREF crBackground); 
```  
  
### <a name="parameters"></a>Parametry  
 `rSrc`  
 Zdroj bitové mapy.  
  
 `pDest`  
 Určení bitové mapy.  
  
 `crBackground`  
 Nové barvu pozadí (obvykle zašedlé, jako je například COLOR_MENU).  
  
### <a name="remarks"></a>Poznámky  
 Rastrový obrázek zkopírován s `AfxGetGrayBitmap` bude mít vzhledu ovládacího prvku zakázané.  
  
 ![Porovnání ikona šedé a původní verze](../../mfc/reference/media/vcgraybitmap.gif "vcgraybitmap")  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#193](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_2.cpp)]  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="afxdrawditheredbitmap"></a>Afxdrawditheredbitmap –  
 Nakreslí rastrového obrázku, nahraďte jeho pozadí vzor tónovaná (kontrola).  
  
```   
void AFXAPI AfxDrawDitheredBitmap(
    CDC* pDC,  
    int x,  
    int y,  
    const CBitmap& rSrc,  
    COLORREF cr1  ,  
    COLORREF cr2); 
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Odkazuje na cílový řadič domény.  
  
 *x*  
 Cílový souřadnici x.  
  
 *y*  
 Cílový souřadnici y.  
  
 `rSrc`  
 Zdroj bitové mapy.  
  
 `cr1`  
 Mezi dvěma rozklad barvy, obvykle bílá.  
  
 `cr2`  
 Další rozklad barva, obvykle světle šedé (COLOR_MENU).  
  
### <a name="remarks"></a>Poznámky  
 Zdroj rastrový obrázek se vykresluje v cílovém umístění řadiče domény s dvěma barvami ( `cr1` a `cr2`) šachovnicová mřížka vzor výměna rastrový obrázek na pozadí. Na pozadí rastrový obrázek zdroj je definován jako jeho bílé pixelů a všechny pixelů odpovídající barvu pixelů v levém horním rohu bitmapy.  
  
 ![Porovnání ikona tónovaná a původní verze](../../mfc/reference/media/vcditheredbitmap.gif "vcditheredbitmap")  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#190](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_3.cpp)]  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  


##  <a name="afxgetditheredbitmap"></a>Afxgetditheredbitmap –  
 Zkopíruje bitové mapy, nahraďte jeho pozadí vzor tónovaná (kontrola).  
  
```   
void AFXAPI AfxGetDitheredBitmap(
    const CBitmap& rSrc,  
    CBitmap* pDest,  
    COLORREF cr1  ,  
    COLORREF cr2); 
```  
  
### <a name="parameters"></a>Parametry  
 `rSrc`  
 Zdroj bitové mapy.  
  
 `pDest`  
 Určení bitové mapy.  
  
 `cr1`  
 Mezi dvěma rozklad barvy, obvykle bílá.  
  
 `cr2`  
 Další rozklad barva, obvykle světle šedé (COLOR_MENU).  
  
### <a name="remarks"></a>Poznámky  
 Rastrový obrázek zdroje se zkopíruje na cílový bitmap s dvěma barvami ( `cr1` a `cr2`) šachovnicová mřížka vzor nahrazení zdroj rastrového obrázku pozadí. Na pozadí rastrový obrázek zdroj je definován jako jeho bílé pixelů a všechny pixelů odpovídající barvu pixelů v levém horním rohu bitmapy.  
  
 ![Porovnání ikona tónovaná a původní verze](../../mfc/reference/media/vcditheredbitmap.gif "vcditheredbitmap")  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#192](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_4.cpp)]  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
## <a name="see-also"></a>Viz také  
 [Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
