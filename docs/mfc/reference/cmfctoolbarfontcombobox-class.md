---
title: "Třída CMFCToolBarFontComboBox | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::GetFontDesc
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::SetFont
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarFontComboBox [MFC], CMFCToolBarFontComboBox
- CMFCToolBarFontComboBox [MFC], GetFontDesc
- CMFCToolBarFontComboBox [MFC], SetFont
ms.assetid: 25f8e08c-aadd-4cb5-9581-a99d49d444b1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5f499c5593460b10957c7d09e01c0f458529df0d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmfctoolbarfontcombobox-class"></a>CMFCToolBarFontComboBox – třída
Tlačítka panelu nástrojů, který obsahuje prvek pole se seznamem, který umožňuje uživateli vybrat písmo ze seznamu písem systému.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCToolBarFontComboBox : public CMFCToolBarComboBoxButton  
```  
  
## <a name="members"></a>Členové  
  
### <a name="protected-constructors"></a>Chráněné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCToolBarFontComboBox::CMFCToolBarFontComboBox](#cmfctoolbarfontcombobox)|Vytvoří `CMFCToolBarFontComboBox` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc)|Vrátí ukazatel `CMFCFontInfo` objekt pro zadaný index v poli se seznamem.|  
|[CMFCToolBarFontComboBox::SetFont](#setfont)|Vybere písmo v poli se seznamem písmo podle buď v názvu písma, nebo předponu a znaková sada písma.|  
  
### <a name="data-members"></a>Datové členy  
 [CMFCToolBarFontComboBox::m_nFontHeight](#m_nfontheight)  
 Výška znaků do pole se seznamem písma.  
  
## <a name="remarks"></a>Poznámky  
 Pokud chcete přidat do panelu nástrojů tlačítko pole se seznamem písma, postupujte takto:  
  
1.  Zarezervujte si pro tlačítko zástupný identifikátor ID prostředku v nadřazeném prostředku panelu nástrojů.  
  
2.  Vytvořit `CMFCToolBarFontComboBox` objektu.  
  
3.  V popisovač zpráv, který zpracovává `AFX_WM_RESETTOOLBAR` zprávy, nahradit původní tlačítko tlačítka Nová pole se seznamem pomocí [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).  
  
4.  Synchronizovat písma, který je vybraný v pole se seznamem s písma v dokumentu s použitím [CMFCToolBarFontComboBox::SetFont](#setfont) metoda.  
  
 Chcete-li synchronizovat dokumentu písma s písma vybraného v seznamu, použijte [CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc) metodu za účelem načtení atributů vybrané písma a použít tyto atributy pro vytvoření [ CFont – třída](../../mfc/reference/cfont-class.md) objektu.  
  
 Tlačítko pole se seznamem písmo volá funkci Win32 [EnumFontFamiliesEx](http://msdn.microsoft.com/library/windows/desktop/dd162620) k určení písma obrazovky a tiskárny, které jsou k dispozici v systému.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)  
  
 [CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxtoolbarfontcombobox.h  
  
##  <a name="cmfctoolbarfontcombobox"></a>CMFCToolBarFontComboBox::CMFCToolBarFontComboBox  
 Vytvoří [CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md) objektu.  
  
```  
public:  
CMFCToolBarFontComboBox(
    UINT uiID,  
    int iImage,  
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,  
    BYTE nCharSet = DEFAULT_CHARSET,  
    DWORD dwStyle = CBS_DROPDOWN,  
    int iWidth = 0,  
    BYTE nPitchAndFamily = DEFAULT_PITCH);

 
protected:  
CMFCToolBarFontComboBox(
    CObList* pLstFontsExternal,  
    int nFontType,  
    BYTE nCharSet,  
    BYTE nPitchAndFamily);  
  
CMFCToolBarFontComboBox();
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiID`  
 ID příkazu pole se seznamem.  
  
 [v]`iImage`  
 Index založený na nule obrázku panelu nástrojů. Bitovou kopii se nachází v [CMFCToolBarImages třída](../../mfc/reference/cmfctoolbarimages-class.md) objektu, který [CMFCToolBar třída](../../mfc/reference/cmfctoolbar-class.md) udržuje – třída.  
  
 [v]`nFontType`  
 Typy písem, která obsahuje pole se seznamem. Tento parametr může být kombinaci (nebo logická hodnota) z následujících hodnot:  
  
 DEVICE_FONTTYPE  
  
 RASTER_FONTTYPE  
  
 TRUETYPE_FONTTYPE  
  
 [v]`nCharSet`  
 Pokud nastaven na DEFAULT_CHARSET, pole se seznamem obsahuje všechny jednoznačně názvem písem v všechny znakových sad. (Pokud existují dvě písma se stejným názvem, pole se seznamem obsahuje jeden z nich). Pokud je nastaven na hodnotu sady platný znak pole se seznamem obsahuje pouze písma v sadě zadaný znak. V tématu [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) seznam možných znak nastaví.  
  
 [v]`dwStyle`  
 Styl pole se seznamem. (viz [pole se seznamem styly](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles))  
  
 [v]`iWidth`  
 Šířku v pixelech ovládacích prvků pro úpravy.  
  
 [v]`nPitchAndFamily`  
 Pokud je nastaven na DEFAULT_PITCH, pole se seznamem obsahuje písma, bez ohledu na výšku. Pokud nastavíte hodnotu FIXED_PITCH nebo VARIABLE_PITCH, pole se seznamem obsahuje pouze písma s daným typem výšku. Filtrování podle rodinu písem není aktuálně podporován.  
  
 [out]`pLstFontsExternal`  
 Ukazatel na [CObList třída](../../mfc/reference/coblist-class.md) objekt, který ukládá dostupná písma.  
  
### <a name="remarks"></a>Poznámky  
 Obvykle `CMFCToolBarFontComboBox` objekty uložit seznam dostupných písem v jedné sdílené `CObList` objektu. Pokud použijete druhý přetížení konstruktoru a zadejte platný ukazatel na `pLstFontsExternal`, že `CMFCToolBarFontComboBox` objektu bude místo toho zadejte `CObList` , `pLstFontsExternal` body k dispozici písmy.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit `CMFCToolBarFontComboBox` objektu. Tento fragment kódu je součástí [ukázkové aplikace Word Pad](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_WordPad#7](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontcombobox-class_1.cpp)]  
  
##  <a name="getfontdesc"></a>CMFCToolBarFontComboBox::GetFontDesc  
 Vrátí ukazatel `CMFCFontInfo` objekt pro zadaný index v poli se seznamem.  
  
```  
const CMFCFontInfo* GetFontDesc(int iIndex=-1) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v]`iIndex`  
 Určuje index položky pole se seznamem založený na nule.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na `CMFCFontInfo` objektu. Pokud `iIndex` neurčuje platnou položku index, je vrácenou hodnotou `NULL`.  
  
##  <a name="m_nfontheight"></a>CMFCToolBarFontComboBox::m_nFontHeight  
 Určuje výšku v pixelech znaků v pole se seznamem písma, pokud má pole se seznamem styl kreslení vlastníka.  
  
```  
static int m_nFontHeight  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud `m_nFontHeight` proměnné je 0, výška se vypočítá automaticky podle výchozí písmo pole se seznamem. Výška zahrnuje jak výstup znaků nad účaří a klesání znaků pod směrného plánu.  
  
##  <a name="setfont"></a>CMFCToolBarFontComboBox::SetFont  
 Vybere písmo v poli se seznamem písmo podle název písma a znak nastavit, které jsou určené v parametrech.  
  
```  
BOOL SetFont(
    LPCTSTR lpszName,  
    BYTE nCharSet=DEFAULT_CHARSET,  
    BOOL bExact=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszName`  
 Určuje název písma nebo předponu.  
  
 [v]`nCharSet`  
 Určuje znakovou sadu.  
  
 [v]`bExact`  
 Určuje, zda `lpszName` obsahuje název písma nebo předponu písma.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud písmo jste vybrali úspěšně; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `bExact` je `TRUE`, tato metoda vybere písmo, který přesně odpovídá názvu, který jste zadali jako `lpszName`. Pokud `bExact` je `FALSE`, tato metoda vybere písmo, který začíná textem určeným jako `lpszName` a používající znaková sada, která jste zadali jako `nCharSet`. Pokud `nCharSet` je nastaven na DEFAULT_CHARSET, budou znaková sada ignorováno a pouze `lpszName` se použije k výběru písmo.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar – třída](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarButton – třída](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CMFCToolBarComboBoxButton – třída](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)   
 [CMFCFontInfo – třída](../../mfc/reference/cmfcfontinfo-class.md)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [Návod: Umístění ovládacích prvků na panely nástrojů](../../mfc/walkthrough-putting-controls-on-toolbars.md)



