---
title: Třída CMFCToolBarFontSizeComboBox | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::GetTwipSize
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::RebuildFontSizes
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::SetTwipSize
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarFontSizeComboBox [MFC], CMFCToolBarFontSizeComboBox
- CMFCToolBarFontSizeComboBox [MFC], GetTwipSize
- CMFCToolBarFontSizeComboBox [MFC], RebuildFontSizes
- CMFCToolBarFontSizeComboBox [MFC], SetTwipSize
ms.assetid: 72e0c44c-6a0e-4194-a71f-ab64e3afb9b5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4b2c5734618bf1bedc72fe78dbeaada8c437391f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cmfctoolbarfontsizecombobox-class"></a>CMFCToolBarFontSizeComboBox – třída
Tlačítka panelu nástrojů, který obsahuje prvek pole se seznamem, který umožňuje uživateli vybrat velikost písma.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCToolBarFontSizeComboBox : public CMFCToolBarComboBoxButton  
```  
  
## <a name="members"></a>Členové  
  
### <a name="protected-constructors"></a>Chráněné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox](#cmfctoolbarfontsizecombobox)|Vytvoří `CMFCToolBarFontSizeComboBox` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize)|Vrátí velikost vybraných písma v twipech.|  
|[CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes)|Vyplní seznamu pole se seznamem všech velikostí podporované písma pro zadaný písmo.|  
|[CMFCToolBarFontSizeComboBox::SetTwipSize](#settwipsize)|Nastaví velikost písma v twipech.|  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít `CMFCToolBarFontSizeComboBox` objektu společně s [CMFCToolBarFontComboBox třída](../../mfc/reference/cmfctoolbarfontcombobox-class.md) objekt, který chcete povolit uživatelům výběr písma a velikost písma.  
  
 Tlačítko pole se seznamem velikost písma můžete přidat na panel nástrojů stejně, jako je přidání tlačítka pole se seznamem písma. Další informace najdete v tématu [CMFCToolBarFontComboBox třída](../../mfc/reference/cmfctoolbarfontcombobox-class.md).  
  
 Když uživatel vybere nový písma v `CMFCToolBarFontComboBox` objekt, můžete vyplnit pole se seznamem velikost písma s podporovaných velikostí pro toto písmo pomocí [CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes) metoda.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pomocí různých metod v nástroji `CMFCToolBarFontSizeComboBox` třída ke konfiguraci `CMFCToolBarFontSizeComboBox` objektu. Příklad ukazuje, jak načíst velikost písma v twipech, v textovém poli, vyplnit pole se seznamem velikost písma se všechny platné velikost daného písma a zadejte velikost písma v twipech. Tento fragment kódu je součástí [ukázkové aplikace Word Pad](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_WordPad#8](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontsizecombobox-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)  
  
 [CMFCToolBarFontSizeComboBox](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxtoolbarfontcombobox.h  
  
##  <a name="cmfctoolbarfontsizecombobox"></a>  CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox  
 Vytvoří `CMFCToolBarFontSizeComboBox` objektu.  
  
```  
CMFCToolBarFontSizeComboBox();
```  
  
##  <a name="gettwipsize"></a>  CMFCToolBarFontSizeComboBox::GetTwipSize  
 Velikost písma v twipech, načte z textového pole se seznamem velikost písma.  
  
```  
int GetTwipSize() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud je kladné návratovou hodnotu, je velikost písma v twipech. Je -1, pokud textového pole pole se seznamem je prázdný. Je -2, pokud dojde k chybě.  
  
##  <a name="rebuildfontsizes"></a>  CMFCToolBarFontSizeComboBox::RebuildFontSizes  
 Vyplní pole se seznamem velikost písma všechny platné velikost daného písma.  
  
```  
void RebuildFontSizes(const CString& strFontName);
```  
  
### <a name="parameters"></a>Parametry  
 `[in] strFontName`  
 Určuje název písma.  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete synchronizovat mezi výběru v poli se seznamem písma a pole se seznamem velikost písma, jako například volání této funkce [CMFCToolBarFontComboBox třída](../../mfc/reference/cmfctoolbarfontcombobox-class.md).  
  
##  <a name="settwipsize"></a>  CMFCToolBarFontSizeComboBox::SetTwipSize  
 Zaokrouhlí číslo zadaný velikost (v twipech) na nejbližší hodnotu v body a poté nastaví velikost vybraného v seznamu můžete tuto hodnotu.  
  
```  
void SetTwipSize(int nSize);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nSize`  
 Určuje velikost písma (v twipech) k nastavení.  
  
### <a name="remarks"></a>Poznámky  
 Předchozí platnou velikost písma lze načíst později voláním [CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize) metoda.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar – třída](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarButton – třída](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CMFCToolBarComboBoxButton – třída](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)   
 [CMFCFontInfo – třída](../../mfc/reference/cmfcfontinfo-class.md)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [Návod: Umístění ovládacích prvků na panely nástrojů](../../mfc/walkthrough-putting-controls-on-toolbars.md)



