---
title: "Třída CMFCRibbonGalleryMenuButton | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonGalleryMenuButton
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::CMFCRibbonGalleryMenuButton
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::CopyFrom
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::CreatePopupMenu
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::GetPalette
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::HasButton
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::IsEmptyMenuAllowed
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonGalleryMenuButton [MFC], CMFCRibbonGalleryMenuButton
- CMFCRibbonGalleryMenuButton [MFC], CopyFrom
- CMFCRibbonGalleryMenuButton [MFC], CreatePopupMenu
- CMFCRibbonGalleryMenuButton [MFC], GetPalette
- CMFCRibbonGalleryMenuButton [MFC], HasButton
- CMFCRibbonGalleryMenuButton [MFC], IsEmptyMenuAllowed
ms.assetid: 4d459d9b-8b1a-4371-92f6-dc4ce6cc42c8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4a50dd19b15e9510bd5d1ca504209caecaf195fc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcribbongallerymenubutton-class"></a>CMFCRibbonGalleryMenuButton – třída
Implementuje tlačítko nabídky pásu karet, které obsahuje Galerie pásu karet.  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
   
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonGalleryMenuButton : public CMFCToolBarMenuButton  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCRibbonGalleryMenuButton::CMFCRibbonGalleryMenuButton](#cmfcribbongallerymenubutton)|Vytvoří a inicializuje `CMFCRibbonGalleryMenuButton` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCRibbonGalleryMenuButton::CopyFrom](#copyfrom)|(Přepisuje [CMFCToolBarMenuButton::CopyFrom](../../mfc/reference/cmfctoolbarmenubutton-class.md#copyfrom).)|  
|[CMFCRibbonGalleryMenuButton::CreatePopupMenu](#createpopupmenu)|(Přepisuje [CMFCToolBarMenuButton::CreatePopupMenu](../../mfc/reference/cmfctoolbarmenubutton-class.md#createpopupmenu).)|  
|[CMFCRibbonGalleryMenuButton::GetPalette](#getpalette)||  
|[CMFCRibbonGalleryMenuButton::HasButton](#hasbutton)|(Přepisuje `CMFCToolBarMenuButton::HasButton`.)|  
|[CMFCRibbonGalleryMenuButton::IsEmptyMenuAllowed](#isemptymenuallowed)|(Přepisuje [CMFCToolBarMenuButton::IsEmptyMenuAllowed](../../mfc/reference/cmfctoolbarmenubutton-class.md#isemptymenuallowed).)|  
  
### <a name="remarks"></a>Poznámky  
 Tlačítko nabídky Galerie se zobrazí jako místní nabídky se šipkou. Po kliknutí na toto tlačítko, zobrazí se Galerie obrázků. Když vytvoříte tlačítka s nabídkou galerie, musíte zadat seznamu obrázků obsahující tyto bitové kopie.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zobrazit galerie odrážek v tlačítka s nabídkou:  
  
```  
BOOL CMainFrame::OnShowPopupMenu (CMFCPopupMenu* pMenuPopup)  
{  
    int nBulletIndex = pMenuBar->CommandToIndex (ID_PARA_BULLETS);

    if (nBulletIndex>= 0)  
 {  
    CMFCToolBarButton* pExButton = 
    pMenuBar->GetButton(nBulletIndex);
ASSERT_VALID (pExButton);

    CMFCRibbonGalleryMenuButton paletteBullet (
    pExButton->m_nID, 
    pExButton->GetImage (),  
    pExButton->m_strText);

 InitBulletPalette (&paletteBullet.GetPalette ());

    pMenuBar->ReplaceButton (ID_PARA_BULLETS,
    paletteBullet);

 }  
}  
```  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md) [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) [CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md) [CMFCRibbonGalleryMenuButton](../../mfc/reference/cmfcribbongallerymenubutton-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxRibbonPaletteGallery.h  
  
##  <a name="copyfrom"></a>CMFCRibbonGalleryMenuButton::CopyFrom  

  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`src`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="cmfcribbongallerymenubutton"></a>CMFCRibbonGalleryMenuButton::CMFCRibbonGalleryMenuButton  
 Vytvoří a inicializuje [CMFCRibbonGalleryMenuButton](../../mfc/reference/cmfcribbongallerymenubutton-class.md) objektu.  
  
```  
CMFCRibbonGalleryMenuButton(
    UINT uiID,  
    int iImage,  
    LPCTSTR lpszText,  
    CMFCToolBarImages& imagesPalette);

 
CMFCRibbonGalleryMenuButton(
    UINT uiID,  
    int iImage,  
    LPCTSTR lpszText,  
    UINT uiImagesPaletteResID = 0,  
    int cxPaletteImage = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `uiID`  
 ID příkazu tlačítka. Toto je hodnota odeslaných za **wm_command –** zprávy po kliknutí na toto tlačítko.  
  
 `iImage`  
 Index bitové kopie zobrazíte pomocí tlačítka nabídky galerie. Bitové kopie jsou uloženy v `imagesPalette` parametr.  
  
 `lpszText`  
 Text pro zobrazení na tlačítko nabídky.  
  
 `imagesPalette`  
 Obsahuje seznam obrázků pro zobrazení v galerii.  
  
 `uiImagesPaletteResID`  
 ID prostředku seznam obrázků pro obrázky, které chcete zobrazit v galerii.  
  
 `cxPaletteImage`  
 Určuje šířku v pixelech bitovou kopii k zobrazení v galerii.  
  
### <a name="remarks"></a>Poznámky  
 Místní nabídky, která má šipka se zobrazí tlačítko nabídky galerie. Po kliknutí na toto tlačítko, zobrazí se Galerie obrázků.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pomocí konstruktoru `CMFCRibbonGalleryMenuButton` třídy. Tento fragment kódu je součástí [MS Office 2007 Demo-ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#8](../../mfc/reference/codesnippet/cpp/cmfcribbongallerymenubutton-class_1.cpp)]  
  
##  <a name="createpopupmenu"></a>CMFCRibbonGalleryMenuButton::CreatePopupMenu  

  
```  
virtual CMFCPopupMenu* CreatePopupMenu();
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getpalette"></a>CMFCRibbonGalleryMenuButton::GetPalette  

  
```  
CMFCRibbonGallery& GetPalette();
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="hasbutton"></a>CMFCRibbonGalleryMenuButton::HasButton  

  
```  
virtual BOOL HasButton() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="isemptymenuallowed"></a>CMFCRibbonGalleryMenuButton::IsEmptyMenuAllowed  

  
```  
virtual BOOL IsEmptyMenuAllowed() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarMenuButton – třída](../../mfc/reference/cmfctoolbarmenubutton-class.md)   
 [CMFCRibbonGallery – třída](../../mfc/reference/cmfcribbongallery-class.md)
