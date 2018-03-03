---
title: "Třída CMFCRibbonColorButton | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonColorButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::CMFCRibbonColorButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::AddColorsGroup
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::EnableAutomaticButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::EnableOtherButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetAutomaticColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetColorBoxSize
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetColumns
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetHighlightedColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::RemoveAllColorGroups
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColorBoxSize
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColorName
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColumns
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetDocumentColors
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetPalette
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::UpdateColor
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonColorButton [MFC], CMFCRibbonColorButton
- CMFCRibbonColorButton [MFC], AddColorsGroup
- CMFCRibbonColorButton [MFC], EnableAutomaticButton
- CMFCRibbonColorButton [MFC], EnableOtherButton
- CMFCRibbonColorButton [MFC], GetAutomaticColor
- CMFCRibbonColorButton [MFC], GetColor
- CMFCRibbonColorButton [MFC], GetColorBoxSize
- CMFCRibbonColorButton [MFC], GetColumns
- CMFCRibbonColorButton [MFC], GetHighlightedColor
- CMFCRibbonColorButton [MFC], RemoveAllColorGroups
- CMFCRibbonColorButton [MFC], SetColor
- CMFCRibbonColorButton [MFC], SetColorBoxSize
- CMFCRibbonColorButton [MFC], SetColorName
- CMFCRibbonColorButton [MFC], SetColumns
- CMFCRibbonColorButton [MFC], SetDocumentColors
- CMFCRibbonColorButton [MFC], SetPalette
- CMFCRibbonColorButton [MFC], UpdateColor
ms.assetid: 6b4b4ee3-8cc0-41b4-a4eb-93e8847008e1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b8da5a7a05f1765fea840c579c91ddd9b3ef672b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcribboncolorbutton-class"></a>CMFCRibbonColorButton – třída
`CMFCRibbonColorButton` Třída implementuje tlačítko barev, které můžete přidat na pásu karet na řádek. Na pásu karet tlačítko barev zobrazí rozevírací nabídce, která obsahuje jeden nebo více palety barev.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonColorButton : public CMFCRibbonGallery  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCRibbonColorButton::CMFCRibbonColorButton](#cmfcribboncolorbutton)||  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCRibbonColorButton::AddColorsGroup](#addcolorsgroup)|Přidá skupinu barev do oblasti regulární barev.|  
|[CMFCRibbonColorButton::EnableAutomaticButton](#enableautomaticbutton)|Určuje, zda **automatické** tlačítko je k dispozici.|  
|[CMFCRibbonColorButton::EnableOtherButton](#enableotherbutton)|Umožňuje **jiných** tlačítko.|  
|[CMFCRibbonColorButton::GetAutomaticColor](#getautomaticcolor)||  
|[CMFCRibbonColorButton::GetColor](#getcolor)|Vrátí aktuálně vybrané barvy.|  
|[CMFCRibbonColorButton::GetColorBoxSize](#getcolorboxsize)|Vrátí velikost elementů barvu, která se zobrazují na pruhu barev.|  
|[CMFCRibbonColorButton::GetColumns](#getcolumns)||  
|[CMFCRibbonColorButton::GetHighlightedColor](#gethighlightedcolor)|Vrátí barvu aktuálně vybraného elementu v automaticky otevřeném okně paletu barev.|  
|[CMFCRibbonColorButton::RemoveAllColorGroups](#removeallcolorgroups)|Odebere všechny skupiny barvu z oblasti regulární barev.|  
|[CMFCRibbonColorButton::SetColor](#setcolor)|Vybere barvu, která z oblasti regulární barev.|  
|[CMFCRibbonColorButton::SetColorBoxSize](#setcolorboxsize)|Nastaví velikost všech elementů barev, které se zobrazují na pruhu barev.|  
|[CMFCRibbonColorButton::SetColorName](#setcolorname)||  
|[CMFCRibbonColorButton::SetColumns](#setcolumns)||  
|[CMFCRibbonColorButton::SetDocumentColors](#setdocumentcolors)|Určuje seznam hodnoty RGB zobrazíte v oblasti barva dokumentu.|  
|[CMFCRibbonColorButton::SetPalette](#setpalette)||  
|[CMFCRibbonColorButton::UpdateColor](#updatecolor)||  
  
## <a name="remarks"></a>Poznámky  
 Na pásu karet tlačítko barev zobrazí pruhu barev po stisknutí ho. Ve výchozím nastavení obsahuje tento pruhu barev názvem oblasti regulární barev palety barev výběr. Volitelně můžete zobrazit pruhu barev **automatické** tlačítko, která umožňuje uživateli vybrat výchozí barvu, a **jiných** tlačítko, které se zobrazí místní palety barev, který obsahuje další barvy.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pomocí různých metod v nástroji `CMFCRibbonColorButton` třídy. Tento příklad ukazuje, jak vytvořit `CMFCRibbonColorButton` objektu, nastavte velký obrázek, povolte **automatické** tlačítko, povolte **jiných** tlačítko, nastavit počet sloupců, nastavte velikost všech elementů barev které zobrazí na pruhu barev, přidejte skupinu barev do oblasti regulární barva a zadejte seznam hodnoty RGB zobrazíte v oblasti barva dokumentu. Tento fragment kódu je součástí [Ukázka kreslení klienta](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DrawClient#3](../../mfc/reference/codesnippet/cpp/cmfcribboncolorbutton-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)  
  
 [CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxribboncolorbutton.h  
  
##  <a name="addcolorsgroup"></a>CMFCRibbonColorButton::AddColorsGroup  
 Přidá skupinu barev do oblasti regulární barev.  
  
```  
void AddColorsGroup(
    LPCTSTR lpszName,  
    const CList<COLORREF,COLORREF>& lstColors,  
    BOOL bContiguousColumns=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszName`  
 Název skupiny.  
  
 [v]`lstColors`  
 Seznam barev.  
  
 [v]`bContiguousColumns`  
 Ovládací prvky zobrazení barvu položky ve skupině. Pokud `TRUE`, barvu položky jsou vykreslovány bez svislé mezery. Pokud `FALSE`, barvu položky jsou vykreslovány s svislé mezery.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce automaticky otevírané okno aby barvu použití zobrazí několik skupin barev. Můžete ovládat zobrazení barvy ve skupině.  
  
##  <a name="cmfcribboncolorbutton"></a>CMFCRibbonColorButton::CMFCRibbonColorButton  
 Vytvoří `CMFCRibbonColorButton` objektu.  
  
```  
CMFCRibbonColorButton();

 
CMFCRibbonColorButton(
    UINT nID,  
    LPCTSTR lpszText,  
    int nSmallImageIndex,  
    COLORREF color = RGB(0, 0, 0));

 
CMFCRibbonColorButton(
    UINT nID,  
    LPCTSTR lpszText,  
    BOOL bSimpleButtonLook,  
    int nSmallImageIndex,  
    int nLargeImageIndex,  
    COLORREF color = RGB(0, 0, 0));
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nID`  
 Určuje ID příkaz příkaz ke spuštění, když uživatel klikne na tlačítko.  
  
 [v]`lpszText`  
 Určuje text, který se zobrazí na tlačítko.  
  
 [v]`nSmallImageIndex`  
 Index počítaný od nuly malý obrázek na tlačítko zobrazit.  
  
 [v]`color`  
 Barva tlačítko (výchozí černé).  
  
 [v]`bSimpleButtonLook`  
 Pokud `TRUE`, tlačítko vykreslením jako jednoduchý obdélník.  
  
 [v]`nLargeImageIndex`  
 Index počítaný od nuly velký obrázek na tlačítko zobrazit.  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="enableautomaticbutton"></a>CMFCRibbonColorButton::EnableAutomaticButton  
 Určuje, zda **automatické** tlačítko je k dispozici.  
  
```  
void EnableAutomaticButton(
    LPCTSTR lpszLabel,  
    COLORREF colorAutomatic,  
    BOOL bEnable=TRUE,  
    LPCTSTR lpszToolTip=NULL,  
    BOOL bOnTop=TRUE,  
    BOOL bDrawBorder=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszLabel`  
 Popisek pro **automatické** tlačítko.  
  
 [v]`colorAutomatic`  
 Hodnotu RGB, která určuje **automatické** tlačítka výchozí barvu.  
  
 [v]`bEnable`  
 `TRUE`Pokud **automatické** tlačítko je dostupné; `FALSE` jestli není zakázaný.  
  
 [v]`lpszToolTip`  
 Popis **automatické** tlačítko.  
  
 [v]`bOnTop`  
 Určuje, zda **automatické** tlačítko je v horní části před paletu barev.  
  
 [v]`bDrawBorder`  
 `TRUE`Pokud aplikace nevykresluje na pásu karet tlačítko barvu ohraničení pruhu barev. Pruhu barev zobrazí aktuálně vybrané barvy. `FALSE`Pokud aplikace není vykreslení ohraničení  
  
##  <a name="enableotherbutton"></a>CMFCRibbonColorButton::EnableOtherButton  
 Umožňuje **jiných** tlačítko.  
  
```  
void EnableOtherButton(
    LPCTSTR lpszLabel,  
    LPCTSTR lpszToolTip=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszLabel`  
 Popisek tlačítka.  
  
 `lpszToolTip`  
 Text popisku pro **jiných** tlačítko.  
  
### <a name="remarks"></a>Poznámky  
 **Jiných** tlačítko je tlačítko, které se zobrazí pod skupinou barvy. Když uživatel klikne **jiných** tlačítko se zobrazí dialogové okno barvy.  
  
##  <a name="getautomaticcolor"></a>CMFCRibbonColorButton::GetAutomaticColor  
 Načte aktuální automatické – tlačítko barvy.  
  
```  
COLORREF GetAutomaticColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota Barva RGB představující aktuální automatické – tlačítko barvy.  
  
### <a name="remarks"></a>Poznámky  
 Barva automatické tlačítko je nastavena `colorAutomatic` byl předán parametr `CMFCRibbonColorButton::EnableAutomaticButton` metoda.  
  
##  <a name="getcolor"></a>CMFCRibbonColorButton::GetColor  
 Vrátí aktuálně vybrané barvy.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Barva vybraná kliknutím na tlačítko.  
  
##  <a name="getcolorboxsize"></a>CMFCRibbonColorButton::GetColorBoxSize  
 Vrátí velikost elementů barvu, která se zobrazují na pruhu barev.  
  
```  
CSize GetColorBoxSize() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Velikost tlačítka barev palety barev rozevíracího seznamu.  
  
##  <a name="getcolumns"></a>CMFCRibbonColorButton::GetColumns  
 Získá počet položek v řádku zobrazení galerie barva tlačítko pásu karet.  
  
```  
int GetColumns() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet ikony v jednotlivých řádcích.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="gethighlightedcolor"></a>CMFCRibbonColorButton::GetHighlightedColor  
 Vrátí barvu aktuálně vybraný element na paletě automaticky otevírané okno barev.  
  
```  
COLORREF GetHighlightedColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Barva aktuálně vybraný element na paletě automaticky otevírané okno barev.  
  
##  <a name="removeallcolorgroups"></a>CMFCRibbonColorButton::RemoveAllColorGroups  
 Odebere všechny skupiny barvu z oblasti regulární barev.  
  
```  
void RemoveAllColorGroups();
```  
  
##  <a name="setcolor"></a>CMFCRibbonColorButton::SetColor  
 Vybere barvu, která z oblasti regulární barev.  
  
```  
void SetColor(COLORREF color);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`color`  
 Barva nastavit.  
  
##  <a name="setcolorboxsize"></a>CMFCRibbonColorButton::SetColorBoxSize  
 Nastaví velikost všech elementů barev, které se zobrazují na pruhu barev.  
  
```  
void SetColorBoxSize(CSize sizeBox);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`sizeBox`  
 Novou velikost tlačítka barev palety barev.  
  
##  <a name="setcolorname"></a>CMFCRibbonColorButton::SetColorName  
 Nastaví nový název pro zadaná barva.  
  
```  
static void __stdcall SetColorName(
    COLORREF color,  
    const CString& strName);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`color`  
 Hodnota RGB barvy.  
  
 [v]`strName`  
 Nový název pro zadaná barva.  
  
### <a name="remarks"></a>Poznámky  
 Vzhledem k tomu, že zavolá `CMFCColorBar::SetColorName`, tato metoda mění název zadaná barva ve všech `CMFCColorBar` objekty ve vaší aplikaci.  
  
##  <a name="setcolumns"></a>CMFCRibbonColorButton::SetColumns  
 Nastaví počet sloupců, které jsou zobrazené v tabulce barev, které se zobrazí uživatelům během procesu výběru barva uživatele.  
  
```  
void SetColumns(int nColumns);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nColumns`  
 Počet barev ikony zobrazíte v jednotlivých řádcích.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setdocumentcolors"></a>CMFCRibbonColorButton::SetDocumentColors  
 Určuje seznam hodnoty RGB zobrazíte v oblasti barva dokumentu.  
  
```  
void SetDocumentColors(
    LPCTSTR lpszLabel,  
    CList<COLORREF,COLORREF>& lstColors);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszLabel`  
 Text, který se má zobrazit pomocí barev dokumentu.  
  
 [v]`lstColors`  
 Odkaz na seznam hodnoty RGB.  
  
##  <a name="setpalette"></a>CMFCRibbonColorButton::SetPalette  
 Určuje standardní barvy zobrazíte v tabulce barev, které zobrazí tlačítko barvy.  
  
```  
void SetPalette(CPalette* pPalette);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pPalette`  
 Ukazatel na paletu barev.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="updatecolor"></a>CMFCRibbonColorButton::UpdateColor  
 Voláno rámcem, když uživatel vybere barvu, která z tabulky barev zobrazí, když uživatel klikne na tlačítko barvy.  
  
```  
void UpdateColor(COLORREF color);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`color`  
 Barva vybraná uživatelem.  
  
### <a name="remarks"></a>Poznámky  
 `CMFCRibbonColorButton::UpdateColor` Metoda změní barvu aktuálně vybrané tlačítko a upozorní nadřazené odesláním `WM_COMMAND` zpráv s `BN_CLICKED` standardní oznámení. Použití [CMFCRibbonColorButton::GetColor](#getcolor) metoda pro načtení vybrané barvy.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonGallery – třída](../../mfc/reference/cmfcribbongallery-class.md)
