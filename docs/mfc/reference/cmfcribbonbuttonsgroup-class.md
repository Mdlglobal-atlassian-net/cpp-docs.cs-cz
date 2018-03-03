---
title: "Třída CMFCRibbonButtonsGroup | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonButtonsGroup
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::AddButton
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::AddButtons
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetButton
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetCount
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetImageSize
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetRegularSize
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::HasImages
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::OnDrawImage
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::RemoveAll
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::SetImages
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::SetParentCategory
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonButtonsGroup [MFC], CMFCRibbonButtonsGroup
- CMFCRibbonButtonsGroup [MFC], AddButton
- CMFCRibbonButtonsGroup [MFC], AddButtons
- CMFCRibbonButtonsGroup [MFC], GetButton
- CMFCRibbonButtonsGroup [MFC], GetCount
- CMFCRibbonButtonsGroup [MFC], GetImageSize
- CMFCRibbonButtonsGroup [MFC], GetRegularSize
- CMFCRibbonButtonsGroup [MFC], HasImages
- CMFCRibbonButtonsGroup [MFC], OnDrawImage
- CMFCRibbonButtonsGroup [MFC], RemoveAll
- CMFCRibbonButtonsGroup [MFC], SetImages
- CMFCRibbonButtonsGroup [MFC], SetParentCategory
ms.assetid: b993d93e-fc1a-472f-a87f-1d7b7b499845
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 45851ea66e324f57cb7df3daaa99eb8a1b8b9311
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcribbonbuttonsgroup-class"></a>CMFCRibbonButtonsGroup – třída
`CMFCRibbonButtonsGroup` Třída umožňuje uspořádat sadu tlačítek pásu karet do skupiny. Všechny tlačítka ve skupině jsou přímo vedle sebe vodorovně a vložen do ohraničení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonButtonsGroup : public CMFCRibbonBaseElement  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup](#cmfcribbonbuttonsgroup)|Vytvoří `CMFCRibbonButtonsGroup` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCRibbonButtonsGroup::AddButton](#addbutton)|Přidá tlačítko do skupiny.|  
|[CMFCRibbonButtonsGroup::AddButtons](#addbuttons)|Seznam tlačítek, přidá do skupiny.|  
|[CMFCRibbonButtonsGroup::GetButton](#getbutton)|Vrátí ukazatel na tlačítko, který se nachází na zadaný index.|  
|[CMFCRibbonButtonsGroup::GetCount](#getcount)|Vrátí počet tlačítka ve skupině.|  
|[CMFCRibbonButtonsGroup::GetImageSize](#getimagesize)|Vrátí velikost bitové kopie normální bitové kopie ve skupině pásu karet (přepíše [CMFCRibbonBaseElement::GetImageSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getimagesize).)|  
|[CMFCRibbonButtonsGroup::GetRegularSize](#getregularsize)|Vrátí velikost regulární elementu pásu karet (přepíše [CMFCRibbonBaseElement::GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|  
|[CMFCRibbonButtonsGroup::HasImages](#hasimages)|Sestavy jestli `CMFCRibbonButtonsGroup` objekt obsahuje obrázků panelu nástrojů.|  
|[CMFCRibbonButtonsGroup::OnDrawImage](#ondrawimage)|Nakreslí obrázek odpovídající pro zadanou tlačítko, v závislosti na tom, zda je tlačítko Normální, zvýrazněné nebo zakázáno.|  
|[CMFCRibbonButtonsGroup::RemoveAll](#removeall)|Odebere všechny tlačítka z `CMFCRibbonButtonsGroup` objektu.|  
|[CMFCRibbonButtonsGroup::SetImages](#setimages)|Přiřadí bitové kopie do skupiny.|  
|[CMFCRibbonButtonsGroup::SetParentCategory](#setparentcategory)|Nastaví nadřazeného `CMFCRibbonCategory` z `CMFCRibbonButtonsGroup` objekt a všechny tlačítka v něm (přepíše [CMFCRibbonBaseElement::SetParentCategory](../../mfc/reference/cmfcribbonbaseelement-class.md#setparentcategory).)|  
  
## <a name="remarks"></a>Poznámky  
 Skupiny je odvozený od [CMFCBaseRibbonElement](../../mfc/reference/cmfcribbonbaseelement-class.md) a smí uživatel manipulovat jako jedna entita. Skupiny můžete umístit v jakékoli panelu nebo v místní nabídce.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pomocí různých metod v nástroji `CMFCRibbonButtonsGroup` třídy. Tento příklad ukazuje, jak vytvořit `CMFCRibbonButtonsGroup` objektu, přiřaďte bitové kopie do skupiny tlačítek pásu karet a přidání tlačítka do skupiny tlačítek pásu karet. Tento fragment kódu je součástí [Ukázka kreslení klienta](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DrawClient#2](../../mfc/reference/codesnippet/cpp/cmfcribbonbuttonsgroup-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButtonsGroup](../../mfc/reference/cmfcribbonbuttonsgroup-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxribbonbuttonsgroup.h  
  
##  <a name="addbutton"></a>CMFCRibbonButtonsGroup::AddButton  
 Přidá tlačítko do skupiny.  
  
```  
void AddButton(CMFCRibbonBaseElement* pButton);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pButton`  
 Ukazatel na tlačítko Přidat.  
  
##  <a name="addbuttons"></a>CMFCRibbonButtonsGroup::AddButtons  
 Seznam tlačítek, přidá do skupiny.  
  
```  
void AddButtons(
    const CList<CMFCRibbonBaseElement*,CMFCRibbonBaseElement*>& lstButtons);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lstButtons`  
 Seznam ukazatele na tlačítka, který chcete přidat.  
  
##  <a name="cmfcribbonbuttonsgroup"></a>CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup  
 Vytvoří `CMFCRibbonButtonsGroup` objektu.  
  
```  
CMFCRibbonButtonsGroup();
CMFCRibbonButtonsGroup(CMFCRibbonBaseElement* pButton);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pButton`  
 Určuje tlačítka pro přidání do nově vytvořený `CMFCRibbonButtonsGroup` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getbutton"></a>CMFCRibbonButtonsGroup::GetButton  
 Vrátí ukazatel na tlačítko, který se nachází na zadaný index.  
  
```  
CMFCRibbonBaseElement* GetButton(int i) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v]`i`  
 Index počítaný od nuly tlačítka vrátit.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na tlačítko, který se nachází v zadaném indexu. `NULL`Pokud zadaný index je mimo rozsah.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getcount"></a>CMFCRibbonButtonsGroup::GetCount  
 Vrátí počet tlačítka ve skupině.  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet tlačítka ve skupině.  
  
##  <a name="getimagesize"></a>CMFCRibbonButtonsGroup::GetImageSize  
 Získá zdroj velikost bitové kopie do chráněného `CMFCToolBarImages` člen `m_Images`.  
  
```  
const CSize GetImageSize() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí velikost obrázku zdroj obrázků na panelu nástrojů, pokud existuje, nebo `CSize` nula, pokud není.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getregularsize"></a>CMFCRibbonButtonsGroup::GetRegularSize  
 Načte maximální možná velikost skupinového elementu pásu karet.  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 Ukazatel na kontext zařízení skupiny pásu karet.  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="hasimages"></a>CMFCRibbonButtonsGroup::HasImages  
 Sestavy jestli `CMFCRibbonButtonsGroup` objekt obsahuje obrázků panelu nástrojů.  
  
```  
BOOL HasImages() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, pokud chráněný `CMFCToolBarImages` člen `m_Images` obsahuje všechny bitové kopie, nebo hodnotu NEPRAVDA, pokud není.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ondrawimage"></a>CMFCRibbonButtonsGroup::OnDrawImage  
 Nakreslí obrázek odpovídající pro zadanou tlačítko, v závislosti na tom, zda je tlačítko Normální, zvýrazněné nebo zakázáno.  
  
```  
virtual void OnDrawImage(
    CDC* pDC,  
    CRect rectImage,  
    CMFCRibbonBaseElement* pButton,  
    int nImageIndex);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 Ukazatel na kontextu zařízení `CMFCRibbonButtonsGroup` objektu.  
  
 [v]`rectImage`  
 Obdélníku, ve kterém k vykreslení bitovou kopii.  
  
 [v]`pButton`  
 Tlačítko pro které chcete kreslení obrázku.  
  
 [v]`nImageIndex`  
 Index bitové kopie k vykreslení na tlačítko (v jednom z polí tři image pro tlačítka Normální, zvýrazněné nebo zakázáno).  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="removeall"></a>CMFCRibbonButtonsGroup::RemoveAll  
 Odebere všechny tlačítka z `CMFCRibbonButtonsGroup` objektu.  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setimages"></a>CMFCRibbonButtonsGroup::SetImages  
 Přiřadí bitové kopie do skupiny tlačítek pásu karet.  
  
```  
void SetImages(
    CMFCToolBarImages* pImages,  
    CMFCToolBarImages* pHotImages,  
    CMFCToolBarImages* pDisabledImages);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pImages`  
 Regulární bitové kopie.  
  
 [v]`pHotImages`  
 Aktivní Image.  
  
 [v]`pDisabledImages`  
 Zakázané bitové kopie.  
  
### <a name="remarks"></a>Poznámky  
 Volání `SetImages` předtím, než přidáte tlačítka do skupiny. Počet bitových kopií musí být větší nebo rovna počtu tlačítka, který se má přidat do skupiny.  
  
> [!NOTE]
>  Aktivní Image jsou bitové kopie, které se zobrazují, když nastavení ukazatele myši na tlačítko. Zakázané Image jsou bitové kopie, které se zobrazí, když je zakázáno na tlačítko.  
  
##  <a name="setparentcategory"></a>CMFCRibbonButtonsGroup::SetParentCategory  
 Nastaví nadřazeného `CMFCRibbonCategory` z `CMFCRibbonButtonsGroup` objekt a všechny tlačítka v něm.  
  
```  
virtual void SetParentCategory(CMFCRibbonCategory* pCategory);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pCategory`  
 Ukazatel na nadřazené kategorii, kterou chcete nastavit (na kartách skupiny v ovládacích prvků pásu karet se nazývají kategorie).  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)
