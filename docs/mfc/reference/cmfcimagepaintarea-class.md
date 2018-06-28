---
title: Třída CMFCImagePaintArea | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::GetMode
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetBitmap
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetColor
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetMode
dev_langs:
- C++
helpviewer_keywords:
- CMFCImagePaintArea [MFC], CMFCImagePaintArea
- CMFCImagePaintArea [MFC], GetMode
- CMFCImagePaintArea [MFC], SetBitmap
- CMFCImagePaintArea [MFC], SetColor
- CMFCImagePaintArea [MFC], SetMode
ms.assetid: c59eec22-f15a-4e58-8c4d-4a18a41f4452
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dea815ef86b16ad472303fd53da5c51e333b13a3
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37037369"
---
# <a name="cmfcimagepaintarea-class"></a>CMFCImagePaintArea – třída
Poskytuje oblast obrázku, který používáte k úpravě bitovou kopii v dialogovém okně editor bitové kopie.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCImagePaintArea : public CButton  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|||  
|-|-|  
|Název|Popis|  
|[CMFCImagePaintArea::CMFCImagePaintArea](#cmfcimagepaintarea)|Vytvoří `CMFCImagePaintArea` objektu.|  
|`CMFCImagePaintArea::~CMFCImagePaintArea`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|||  
|-|-|  
|Název|Popis|  
|[CMFCImagePaintArea::GetMode](#getmode)|Načte aktuální režim kreslení.|  
|[CMFCImagePaintArea::SetBitmap](#setbitmap)|Nastaví rastrový obrázek oblasti obrázku.|  
|[CMFCImagePaintArea::SetColor](#setcolor)|Nastaví barvu aktuální kreslení.|  
|[CMFCImagePaintArea::SetMode](#setmode)|Nastaví aktuální režim kreslení.|  
  
### <a name="remarks"></a>Poznámky  
 Tato třída není určena pro použití přímo z vašeho kódu.  
  
 Rozhraní používá tuto třídu pro zobrazení oblasti obrázku v dialogovém okně editor bitové kopie. Další informace o dialogovém okně editor bitové kopie najdete v tématu [CMFCImageEditorDialog třída](../../mfc/reference/cmfcimageeditordialog-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit objekt `CMFCImagePaintArea` třídy, nastavte aktuální kreslení barvu, nastavit aktuální režim kreslení a rastrový obrázek oblasti obrázku.  
  
 [!code-cpp[NVC_MFC_RibbonApp#37](../../mfc/reference/codesnippet/cpp/cmfcimagepaintarea-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCImagePaintArea](../../mfc/reference/cmfcimagepaintarea-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afximagepaintarea.h  
  
##  <a name="cmfcimagepaintarea"></a>  CMFCImagePaintArea::CMFCImagePaintArea  
 Vytvoří `CMFCImagePaintArea` objektu.  
  
```  
CMFCImagePaintArea(CMFCImageEditorDialog* pParentDlg);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v] *pParentDlg*|Ukazatel na okno, které je nadřazená image editoru.|  
  
##  <a name="getmode"></a>  CMFCImagePaintArea::GetMode  
 Načte aktuální režim kreslení.  
  
```  
IMAGE_EDIT_MODE GetMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 [IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md) hodnotu, která určuje aktuální režim kreslení.  
  
##  <a name="setbitmap"></a>  CMFCImagePaintArea::SetBitmap  
 Nastaví rastrový obrázek oblasti obrázku.  
  
```  
void SetBitmap(CBitmap* pBitmap);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v] *pBitmap*|Nový rastrový obrázek pro zobrazení.|  
  
### <a name="remarks"></a>Poznámky  
 Pokud *pBitmap* je `NULL`, tato metoda nastaví velikost oblasti upravitelnými Malování na nulu. Nastaví, jinak hodnota velikosti oblasti upravitelnými Malování velikost zadaná rastrového obrázku.  
  
##  <a name="setcolor"></a>  CMFCImagePaintArea::SetColor  
 Nastaví barvu aktuální kreslení.  
  
```  
void SetColor(COLORREF color);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v] *barev*|Nové kreslení barva.|  
  
### <a name="remarks"></a>Poznámky  
 Když vyberte barvu z panelu image editor palety nebo volby barev, rozhraní volá tuto metodu za účelem aktualizace aktuální kreslení barvu. Černá je počáteční barvu kreslení ( `COLORREF` hodnota 0).  
  
 Kreslení barvu používá dialogové okno editor bitové kopie pro všechny režimy kreslení s výjimkou `IMAGE_EDIT_MODE_COLOR`. Další informace o kreslení režimy najdete v tématu [CMFCImagePaintArea::IMAGE_EDIT_MODE – výčet](cmfcimagepaintarea-image-edit-mode-enumeration.md).  
  
##  <a name="setmode"></a>  CMFCImagePaintArea::SetMode  
 Nastaví aktuální režim kreslení.  
  
```  
void SetMode(IMAGE_EDIT_MODE mode);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v] *režimu*|[IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md) hodnotu, která určuje aktuální režim kreslení.|  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCImageEditorDialog – třída](../../mfc/reference/cmfcimageeditordialog-class.md)
