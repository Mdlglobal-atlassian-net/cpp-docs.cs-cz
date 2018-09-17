---
title: Cmfcribboncolorbutton – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 968dc2103f4abfeab2001394ae91044f0f67ff7a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45719690"
---
# <a name="cmfcribboncolorbutton-class"></a>Cmfcribboncolorbutton – třída
`CMFCRibbonColorButton` Třída implementuje barevné tlačítko, které můžete přidat na panel pásu karet. Tlačítko Barva pásu karet zobrazí rozevírací nabídku, která obsahuje jeden nebo více palet barev.  
  
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
|[CMFCRibbonColorButton::AddColorsGroup](#addcolorsgroup)|Přidá do oblasti regulární barva skupinu barev.|  
|[CMFCRibbonColorButton::EnableAutomaticButton](#enableautomaticbutton)|Určuje, zda **automatické** tlačítko je povolené.|  
|[CMFCRibbonColorButton::EnableOtherButton](#enableotherbutton)|Umožňuje **jiných** tlačítko.|  
|[CMFCRibbonColorButton::GetAutomaticColor](#getautomaticcolor)||  
|[CMFCRibbonColorButton::GetColor](#getcolor)|Vrátí aktuálně vybraný barvu.|  
|[CMFCRibbonColorButton::GetColorBoxSize](#getcolorboxsize)|Vrátí velikost prvků barev, které se zobrazují na pruhu barev.|  
|[CMFCRibbonColorButton::GetColumns](#getcolumns)||  
|[CMFCRibbonColorButton::GetHighlightedColor](#gethighlightedcolor)|Vrátí barvu aktuálně vybraný element na paletu barev automaticky otevíraného okna.|  
|[CMFCRibbonColorButton::RemoveAllColorGroups](#removeallcolorgroups)|Odebere všechny skupiny barev z oblasti regulární barvu.|  
|[CMFCRibbonColorButton::SetColor](#setcolor)|Vybere barvu z oblasti regulární barvu.|  
|[CMFCRibbonColorButton::SetColorBoxSize](#setcolorboxsize)|Nastaví velikost všech prvků barev, které se zobrazují na pruhu barev.|  
|[CMFCRibbonColorButton::SetColorName](#setcolorname)||  
|[CMFCRibbonColorButton::SetColumns](#setcolumns)||  
|[CMFCRibbonColorButton::SetDocumentColors](#setdocumentcolors)|Určuje seznam hodnoty RGB zobrazíte v oblasti barev dokumentu.|  
|[CMFCRibbonColorButton::SetPalette](#setpalette)||  
|[CMFCRibbonColorButton::UpdateColor](#updatecolor)||  
  
## <a name="remarks"></a>Poznámky  
 Tlačítko Barva pásu karet zobrazí pruhu barev, když uživatel stiskne ho. Ve výchozím nastavení obsahuje tento pruhu barev volá oblast regulární barev palety barev výběru. Volitelně můžete zobrazit pruhu barev **automatické** tlačítka, která umožňuje uživateli vybrat výchozí barva, a **jiných** tlačítko, které se zobrazí automaticky otevírané okno paletu barev, která obsahuje další barvy.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít různé metody v `CMFCRibbonColorButton` třídy. Tento příklad ukazuje, jak vytvořit `CMFCRibbonColorButton` objektu, nastavte velký obrázek, povolte **automatické** tlačítko, povolte **jiných** tlačítko, nastavte počet sloupců, nastavit velikost všech prvků Barva který se zobrazí na panelu barev., přidejte skupinu barev do oblasti regulární barva a zadat seznam hodnoty RGB zobrazíte v oblasti barev dokumentu. Tento fragment kódu je součástí [nakreslit Client sample](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DrawClient#3](../../mfc/reference/codesnippet/cpp/cmfcribboncolorbutton-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [Cmfcribbonbaseelement –](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [Cmfcribbonbutton –](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [Cmfcribbongallery –](../../mfc/reference/cmfcribbongallery-class.md)  
  
 [Cmfcribboncolorbutton –](../../mfc/reference/cmfcribboncolorbutton-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxribboncolorbutton.h  
  
##  <a name="addcolorsgroup"></a>  CMFCRibbonColorButton::AddColorsGroup  
 Přidá do oblasti regulární barva skupinu barev.  
  
```  
void AddColorsGroup(
    LPCTSTR lpszName,  
    const CList<COLORREF,COLORREF>& lstColors,  
    BOOL bContiguousColumns=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
*lpszName*<br/>
[in] Název skupiny.  
  
*lstColors*<br/>
[in] Seznam barev.  
  
*bContiguousColumns*<br/>
[in] Určuje způsob zobrazení Barva položek ve skupině. Pokud je hodnota TRUE, jsou vykreslovány vedle položek barev bez svislé mezery. Pokud má hodnotu FALSE, barva položky vykreslí ve svislé mezery.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce nastavit barvu místní použití zobrazit několik skupin barev. Můžete řídit, jak barvy zobrazují ve skupině.  
  
##  <a name="cmfcribboncolorbutton"></a>  CMFCRibbonColorButton::CMFCRibbonColorButton  
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
*nID*<br/>
[in] Určuje Identifikátor příkazu příkazu ke spuštění, když uživatel klikne na tlačítko.  
  
*lpszText*<br/>
[in] Určuje text, který se zobrazí na tlačítku.  
  
*nSmallImageIndex*<br/>
[in] Index založený na nule malý obrázek, který se zobrazí na tlačítku.  
  
*Barva*<br/>
[in] Barva tlačítka (výchozí hodnota je černá).  
  
*bSimpleButtonLook*<br/>
[in] Při hodnotě TRUE se tlačítko vykreslí jako jednoduchý obdélník.  
  
*nLargeImageIndex*<br/>
[in] Index založený na nule velký obrázek, který se zobrazí na tlačítku.  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="enableautomaticbutton"></a>  CMFCRibbonColorButton::EnableAutomaticButton  
 Určuje, zda **automatické** tlačítko je povolené.  
  
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
*lpszLabel*<br/>
[in] Popisek **automatické** tlačítko.  
  
*barvaAutomatická*<br/>
[in] Hodnota RGB, která určuje, **automatické** výchozí barvy tlačítka.  
  
*bEnable*<br/>
[in] Hodnota TRUE, pokud **automatické** tlačítko je dostupné; FALSE, pokud je zakázaná.  
  
*lpszToolTip*<br/>
[in] Text nápovědy **automatické** tlačítko.  
  
*bOnTop*<br/>
[in] Určuje, zda **automatické** je tlačítko v horní části před palety barev.  
  
*bDrawBorder*<br/>
[in] TRUE, pokud aplikace vykreslí ohraničení pruhu barev na tlačítko Barva pásu karet. Pruhu barev zobrazí aktuálně vybranou barvu. FALSE, pokud aplikace není nakreslí rámeček  
  
##  <a name="enableotherbutton"></a>  CMFCRibbonColorButton::EnableOtherButton  
 Umožňuje **jiných** tlačítko.  
  
```  
void EnableOtherButton(
    LPCTSTR lpszLabel,  
    LPCTSTR lpszToolTip=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszLabel*  
 Popisek tlačítka.  
  
 *lpszToolTip*  
 Text popisku pro **jiných** tlačítko.  
  
### <a name="remarks"></a>Poznámky  
 **Jiných** tlačítko je tlačítko, které se zobrazí pod skupinu barev. Pokud uživatel klikne **jiných** tlačítko, zobrazí dialogové okno barev.  
  
##  <a name="getautomaticcolor"></a>  CMFCRibbonColorButton::GetAutomaticColor  
 Načte aktuální barvu automatického tlačítka.  
  
```  
COLORREF GetAutomaticColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota barvy RGB, který představuje aktuální barvu automatického tlačítka.  
  
### <a name="remarks"></a>Poznámky  
 Nastavuje barvu automatického tlačítka `colorAutomatic` byl předán parametr `CMFCRibbonColorButton::EnableAutomaticButton` metody.  
  
##  <a name="getcolor"></a>  CMFCRibbonColorButton::GetColor  
 Vrátí aktuálně vybraný barvu.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Barva, vybrali kliknutím na tlačítko.  
  
##  <a name="getcolorboxsize"></a>  CMFCRibbonColorButton::GetColorBoxSize  
 Vrátí velikost prvků barev, které se zobrazují na pruhu barev.  
  
```  
CSize GetColorBoxSize() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Velikost tlačítka barvy palety barev rozevíracího seznamu.  
  
##  <a name="getcolumns"></a>  CMFCRibbonColorButton::GetColumns  
 Získá počet položek v řádku galerie zobrazit tlačítko Barva pásu karet.  
  
```  
int GetColumns() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet ikon v jednotlivých řádcích.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="gethighlightedcolor"></a>  CMFCRibbonColorButton::GetHighlightedColor  
 Vrátí barvu aktuálně vybraný element na palety barev.  
  
```  
COLORREF GetHighlightedColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Barva aktuálně vybraný element na palety barev.  
  
##  <a name="removeallcolorgroups"></a>  CMFCRibbonColorButton::RemoveAllColorGroups  
 Odebere všechny skupiny barev z oblasti regulární barvu.  
  
```  
void RemoveAllColorGroups();
```  
  
##  <a name="setcolor"></a>  CMFCRibbonColorButton::SetColor  
 Vybere barvu z oblasti regulární barvu.  
  
```  
void SetColor(COLORREF color);
```  
  
### <a name="parameters"></a>Parametry  
*Barva*<br/>
[in] Barvu, kterou chcete nastavit.  
  
##  <a name="setcolorboxsize"></a>  CMFCRibbonColorButton::SetColorBoxSize  
 Nastaví velikost všech prvků barev, které se zobrazují na pruhu barev.  
  
```  
void SetColorBoxSize(CSize sizeBox);
```  
  
### <a name="parameters"></a>Parametry  
*sizeBox*<br/>
[in] Nová velikost tlačítka barvy v barevné palety.  
  
##  <a name="setcolorname"></a>  CMFCRibbonColorButton::SetColorName  
 Nastaví nový název pro zadanou barvu.  
  
```  
static void __stdcall SetColorName(
    COLORREF color,  
    const CString& strName);
```  
  
### <a name="parameters"></a>Parametry  
*Barva*<br/>
[in] Hodnota RGB barvu.  
  
*%{strName/*<br/>
[in] Nový název pro zadanou barvu.  
  
### <a name="remarks"></a>Poznámky  
 Jelikož volá `CMFCColorBar::SetColorName`, tato metoda se změní název zadané barvy ve všech `CMFCColorBar` objekty ve vaší aplikaci.  
  
##  <a name="setcolumns"></a>  CMFCRibbonColorButton::SetColumns  
 Nastaví počet sloupců v tabulce barev, která se zobrazí uživateli při výběru barvy uživatele.  
  
```  
void SetColumns(int nColumns);
```  
  
### <a name="parameters"></a>Parametry  
*nColumns*<br/>
[in] Počet barevných ikon pro zobrazení v jednotlivých řádcích.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setdocumentcolors"></a>  CMFCRibbonColorButton::SetDocumentColors  
 Určuje seznam hodnoty RGB zobrazíte v oblasti barev dokumentu.  
  
```  
void SetDocumentColors(
    LPCTSTR lpszLabel,  
    CList<COLORREF,COLORREF>& lstColors);
```  
  
### <a name="parameters"></a>Parametry  
*lpszLabel*<br/>
[in] Text, který zobrazuje barvy dokumentu.  
  
*lstColors*<br/>
[in] Odkaz na seznam hodnoty RGB.  
  
##  <a name="setpalette"></a>  CMFCRibbonColorButton::SetPalette  
 Určuje standardní barvy pro zobrazení v tabulce barev, která bude tlačítko barev zobrazí.  
  
```  
void SetPalette(CPalette* pPalette);
```  
  
### <a name="parameters"></a>Parametry  
*pPalette*<br/>
[in] Ukazatel na paletu barev.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="updatecolor"></a>  CMFCRibbonColorButton::UpdateColor  
 Volá se rozhraním, když uživatel vybere barvu z tabulky barev zobrazí, když uživatel klikne na tlačítko barvy.  
  
```  
void UpdateColor(COLORREF color);
```  
  
### <a name="parameters"></a>Parametry  
*Barva*<br/>
[in] Barva vybraná uživatelem.  
  
### <a name="remarks"></a>Poznámky  
 `CMFCRibbonColorButton::UpdateColor` Metoda změní barvu vybraného tlačítka a upozorní nadřazené odesláním wm_command – zprávy s oznámením BN_CLICKED standard. Použití [CMFCRibbonColorButton::GetColor](#getcolor) metodu pro načtení vybraných barev.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonGallery – třída](../../mfc/reference/cmfcribbongallery-class.md)
