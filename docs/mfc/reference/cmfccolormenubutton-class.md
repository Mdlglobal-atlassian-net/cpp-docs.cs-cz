---
title: Třída CMFCColorMenuButton | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableAutomaticButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableDocumentColors
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableOtherButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableTearOff
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetAutomaticColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetColorByCmdID
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnChangeParentWnd
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OpenColorDialog
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColorByCmdID
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColorName
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColumnsNumber
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CopyFrom
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CreatePopupMenu
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::IsEmptyMenuAllowed
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnDraw
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnDrawOnCustomizeList
dev_langs:
- C++
helpviewer_keywords:
- CMFCColorMenuButton [MFC], CMFCColorMenuButton
- CMFCColorMenuButton [MFC], EnableAutomaticButton
- CMFCColorMenuButton [MFC], EnableDocumentColors
- CMFCColorMenuButton [MFC], EnableOtherButton
- CMFCColorMenuButton [MFC], EnableTearOff
- CMFCColorMenuButton [MFC], GetAutomaticColor
- CMFCColorMenuButton [MFC], GetColor
- CMFCColorMenuButton [MFC], GetColorByCmdID
- CMFCColorMenuButton [MFC], OnChangeParentWnd
- CMFCColorMenuButton [MFC], OpenColorDialog
- CMFCColorMenuButton [MFC], SetColor
- CMFCColorMenuButton [MFC], SetColorByCmdID
- CMFCColorMenuButton [MFC], SetColorName
- CMFCColorMenuButton [MFC], SetColumnsNumber
- CMFCColorMenuButton [MFC], CopyFrom
- CMFCColorMenuButton [MFC], CreatePopupMenu
- CMFCColorMenuButton [MFC], IsEmptyMenuAllowed
- CMFCColorMenuButton [MFC], OnDraw
- CMFCColorMenuButton [MFC], OnDrawOnCustomizeList
ms.assetid: 42685704-e994-4f7b-9553-62283c27b754
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ea9fddef1b032d1e17ea46229a992c23ca960822
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37039021"
---
# <a name="cmfccolormenubutton-class"></a>CMFCColorMenuButton – třída
`CMFCColorMenuButton` Třída podporuje příkazu nabídky nebo tlačítka panelu nástrojů, který začíná dialogové okno pro výběr barev.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCColorMenuButton : public CMFCToolBarMenuButton  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCColorMenuButton::CMFCColorMenuButton](#cmfccolormenubutton)|Vytvoří `CMFCColorMenuButton` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCColorMenuButton::EnableAutomaticButton](#enableautomaticbutton)|Povolí nebo zakáže "automatické" tlačítko, které je umístěné výše regulární barva tlačítek. (Automatické tlačítko standardní systému jmenuje **automatické**.)|  
|[CMFCColorMenuButton::EnableDocumentColors](#enabledocumentcolors)|Umožňuje zobrazení barvy specifické pro dokument místo barvy systému.|  
|[CMFCColorMenuButton::EnableOtherButton](#enableotherbutton)|Povolí nebo zakáže "ostatní" tlačítko, které je umístěné pod regulární barva tlačítek. (Standardní systém "ostatní" tlačítko jmenuje **Další barvy**.)|  
|[CMFCColorMenuButton::EnableTearOff](#enabletearoff)|Umožňuje možnost oddělení podokně barev.|  
|[CMFCColorMenuButton::GetAutomaticColor](#getautomaticcolor)|Načte aktuální automatické barvu.|  
|[CMFCColorMenuButton::GetColor](#getcolor)|Načte aktuální tlačítko barvy.|  
|[CMFCColorMenuButton::GetColorByCmdID](#getcolorbycmdid)|Načte barvu, která odpovídá ID zadaného příkazu.|  
|[CMFCColorMenuButton::OnChangeParentWnd](#onchangeparentwnd)|Voláno rámcem, když se změní nadřazeného okna.|  
|[CMFCColorMenuButton::OpenColorDialog](#opencolordialog)|Otevře dialogové okno Výběr barev.|  
|[CMFCColorMenuButton::SetColor](#setcolor)|Nastaví barvu aktuální barva tlačítko.|  
|[CMFCColorMenuButton::SetColorByCmdID](#setcolorbycmdid)|Nastaví barvu zadaná barva tlačítka nabídky.|  
|[CMFCColorMenuButton::SetColorName](#setcolorname)|Nastaví nový název pro zadaná barva.|  
|[CMFCColorMenuButton::SetColumnsNumber](#setcolumnsnumber)|Nastaví počet sloupců, které jsou zobrazeny `CMFCColorBar` objektu.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCColorMenuButton::CopyFrom](#copyfrom)|Zkopíruje jiné tlačítka panelu nástrojů na tlačítko aktuální.|  
|[CMFCColorMenuButton::CreatePopupMenu](#createpopupmenu)|Vytvoří dialogové okno pro výběr barev.|  
|[CMFCColorMenuButton::IsEmptyMenuAllowed](#isemptymenuallowed)|Určuje, zda jsou podporovány prázdný nabídky.|  
|[CMFCColorMenuButton::OnDraw](#ondraw)|Voláno rámcem zobrazíte obrázek na tlačítko.|  
|[CMFCColorMenuButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|Voláno rámcem před `CMFCColorMenuButton` objektu se zobrazí v seznamu dialogového okna přizpůsobení panelu nástrojů.|  
  
## <a name="remarks"></a>Poznámky  
 Nahradit původní příkaz nebo na panelu nástrojů tlačítko nabídky s `CMFCColorMenuButton` objektu, vytvořte `CMFCColorMenuButton` objekt, nastavte všechny příslušné [CMFCColorBar třída](../../mfc/reference/cmfccolorbar-class.md) styly a pak volání `ReplaceButton` metoda [CMFCToolBar třída](../../mfc/reference/cmfctoolbar-class.md) třídy. Pokud můžete přizpůsobit panel nástrojů, zavolejte [CMFCToolBarsCustomizeDialog::ReplaceButton](../../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) metoda.  
  
 Dialogové okno pro výběr barev se vytvoří během zpracování [CMFCColorMenuButton::CreatePopupMenu](#createpopupmenu) obslužné rutiny události. Obslužné rutiny události upozorní nadřazeného rámce s `WM_COMMAND` zprávy. `CMFCColorMenuButton` Objekt odešle ID ovládacího prvku, který je přiřazen k původní příkaz nebo na panelu nástrojů tlačítko nabídky.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit a nakonfigurovat pomocí různých metod v tlačítka s nabídkou barev `CMFCColorMenuButton` třídy. V příkladu `CPalette` objektu je prvním vytvoření a pak se použije k vytvoření objektu `CMFCColorMenuButton` třídy. `CMFCColorMenuButton` Objektu je nakonfigurovaný tak, že povolení jeho automatické a ostatní tlačítka a nastavení jeho barvy a počet sloupců. Tento kód je součástí [ukázkové aplikace Word Pad](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_WordPad#5](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_1.h)]  
[!code-cpp[NVC_MFC_WordPad#6](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)  
  
 [CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcolormenubutton.h  
  
##  <a name="cmfccolormenubutton"></a>  CMFCColorMenuButton::CMFCColorMenuButton  
 Vytvoří `CMFCColorMenuButton` objektu.  
  
```  
CMFCColorMenuButton();

 
CMFCColorMenuButton(
    UINT uiCmdID,  
    LPCTSTR lpszText,  
    CPalette* pPalette=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *uiCmdID*  
 ID příkazu tlačítko.  
  
 [v] *lpszText*  
 Text tlačítka.  
  
 [v] *pPalette*  
 Ukazatel na paletu barev na tlačítko.  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
 První konstruktor je výchozí konstruktor. Aktuální barva objektu a Automatická barva inicializovány na černé (RGB (0, 0, 0)).  
  
 Druhý konstruktor inicializuje tlačítko pro barvu, která odpovídá ID zadaný příkaz.  
  
##  <a name="copyfrom"></a>  CMFCColorMenuButton::CopyFrom  
 Zkopíruje jeden [CMFCToolBarMenuButton třída](../../mfc/reference/cmfctoolbarmenubutton-class.md)-odvozené objekt do jiné.  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *src*  
 Tlačítko zdroj pro kopírování.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu pro kopírování objektů, které jsou odvozeny od `CMFCColorMenuButton` objektu.  
  
##  <a name="createpopupmenu"></a>  CMFCColorMenuButton::CreatePopupMenu  
 Vytvoří dialogové okno pro výběr barev.  
  
```  
virtual CMFCPopupMenu* CreatePopupMenu();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Objekt, který reprezentuje dialogové okno pro výběr barev.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána rámcem po stisknutí tlačítka s nabídkou barev.  
  
##  <a name="enableautomaticbutton"></a>  CMFCColorMenuButton::EnableAutomaticButton  
 Povolí nebo zakáže "automatické" tlačítko, které je umístěné výše regulární barva tlačítek. (Automatické tlačítko standardní systému jmenuje **automatické**.)  
  
```  
void EnableAutomaticButton(
    LPCTSTR lpszLabel,  
    COLORREF colorAutomatic,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *lpszLabel*  
 Určuje text tlačítka, který se zobrazí, když na tlačítko Automatická.  
  
 [v] *barvaAutomatická*  
 Určuje barvu automatické nové.  
  
 [v] *bEnable*  
 Určuje, jestli je tlačítko Automatické nebo ne.  
  
### <a name="remarks"></a>Poznámky  
 Automatické tlačítko použije aktuální výchozí barvu.  
  
##  <a name="enabledocumentcolors"></a>  CMFCColorMenuButton::EnableDocumentColors  
 Umožňuje zobrazení barvy specifické pro dokument místo barvy systému.  
  
```  
void EnableDocumentColors(
    LPCTSTR lpszLabel,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *lpszLabel*  
 Určuje text tlačítka.  
  
 [v] *bEnable*  
 `TRUE` k zobrazení barvy specifické pro dokument nebo `FALSE` zobrazíte barvy systému.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte k zobrazení aktuální barvy dokumentu nebo barvy palety systému, když uživatel klikne na tlačítko nabídky barvu.  
  
##  <a name="enableotherbutton"></a>  CMFCColorMenuButton::EnableOtherButton  
 Povolí nebo zakáže "ostatní" tlačítko, které je umístěné pod regulární barva tlačítek. (Standardní systém "ostatní" tlačítko jmenuje **Další barvy**.)  
  
```  
void EnableOtherButton(
    LPCTSTR lpszLabel,  
    BOOL bAltColorDlg=TRUE,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *lpszLabel*  
 Určuje text tlačítka.  
  
 [v] *bAltColorDlg*  
 Zadejte `TRUE` zobrazíte `CMFCColorDialog` dialogové okno, nebo `FALSE` zobrazíte dialogové okno barvy standardní systém.  
  
 [v] *bEnable*  
 Zadejte `TRUE` se zobrazí tlačítko "ostatní"; jinak hodnota `FALSE`. Výchozí hodnota je `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="enabletearoff"></a>  CMFCColorMenuButton::EnableTearOff  
 Umožňuje možnost oddělení podokně barev.  
  
```  
void EnableTearOff(
    UINT uiID,  
    int nVertDockColumns=-1,  
    int nHorzDockRows=-1);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *uiID*  
 Určuje ID pro podokně úplné vypnutí.  
  
 [v] *nVertDockColumns*  
 Určuje počet sloupců v podokně svisle ukotveného barev v úplné vypnutí stavu.  
  
 [v] *nHorzDockRows*  
 Určuje počet řádků v podokně vodorovně ukotvené barev v úplné vypnutí stavu.  
  
### <a name="remarks"></a>Poznámky  
 Volat tuto metodu za účelem povolení této funkce "úplné vypnuto" pro podokně barvu, která se objeví při `CMFCColorMenuButton` stisknutí tlačítka.  
  
##  <a name="getautomaticcolor"></a>  CMFCColorMenuButton::GetAutomaticColor  
 Načte aktuální automatické barvu.  
  
```  
COLORREF GetAutomaticColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota Barva RGB představující aktuální automatické barvu.  
  
### <a name="remarks"></a>Poznámky  
 Volat tuto metodu za účelem získání automatické barvu, která se nastavuje pomocí [CMFCColorMenuButton::EnableAutomaticButton](#enableautomaticbutton).  
  
##  <a name="getcolor"></a>  CMFCColorMenuButton::GetColor  
 Načte aktuální tlačítko barvy.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Barva tlačítko.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getcolorbycmdid"></a>  CMFCColorMenuButton::GetColorByCmdID  
 Načte barvu, která odpovídá ID zadaného příkazu.  
  
```  
static COLORREF GetColorByCmdID(UINT uiCmdID);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *uiCmdID*  
 ID příkazu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Barvu, která odpovídá ID zadaný příkaz.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte, pokud máte několik barva tlačítek v aplikaci. Když uživatel klikne na tlačítko barvy, tlačítko odešle jeho ID příkazu wm_command – zprávy ke své nadřazené úloze. `GetColorByCmdID` Metoda načíst barvu odpovídající pomocí ID příkazu.  
  
##  <a name="isemptymenuallowed"></a>  CMFCColorMenuButton::IsEmptyMenuAllowed  
 Určuje, zda jsou podporovány prázdný nabídky.  
  
```  
virtual BOOL IsEmptyMenuAllowed() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Jsou povoleny nabídky nenulové hodnoty, pokud je prázdný. jinak hodnota nula.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení jsou podporovány prázdný nabídky. Potlačí tuto metodu v odvozené třídě toto chování změnit.  
  
##  <a name="onchangeparentwnd"></a>  CMFCColorMenuButton::OnChangeParentWnd  
 Voláno rámcem, když se změní nadřazeného okna.  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *pWndParent*  
 Ukazatel do nového nadřazeného okna.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ondraw"></a>  CMFCColorMenuButton::OnDraw  
 Voláno rámcem zobrazíte obrázek na tlačítko.  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rect,  
    CMFCToolBarImages* pImages,  
    BOOL bHorz=TRUE,  
    BOOL bCustomizeMode=FALSE,  
    BOOL bHighlight=FALSE,  
    BOOL bDrawBorder=TRUE,  
    BOOL bGrayDisabledButtons=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *primárního řadiče domény*  
 Ukazatel na kontextu zařízení.  
  
 [v] *Rect –*  
 Obdélníku, která bounds oblasti překreslit.  
  
 [v] *pImages*  
 Body v seznamu obrázků panelu nástrojů.  
  
 [v] *bHorz*  
 `TRUE` k určení, že je panelu nástrojů v vodorovné ukotvený stavu; v opačném `FALSE`. Výchozí hodnota je `TRUE`.  
  
 [v] *bCustomizeMode*  
 `TRUE` Chcete-li určit, že aplikace je v režimu přizpůsobení; v opačném `FALSE`. Výchozí hodnota je `FALSE`.  
  
 [v] *bHighlight*  
 `TRUE` Chcete-li určit, že bude zvýrazněný tlačítko. v opačném `FALSE`. Výchozí hodnota je `FALSE`.  
  
 [v] *bDrawBorder*  
 `TRUE` Chcete-li určit, že se zobrazí na tlačítko ohraničení; v opačném `FALSE`. Výchozí hodnota je `TRUE`.  
  
 [v] *bGrayDisabledButtons*  
 `TRUE` Chcete-li určit, který zakázáno tlačítka jsou šedý (neaktivní) v opačném `FALSE`. Výchozí hodnota je `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ondrawoncustomizelist"></a>  CMFCColorMenuButton::OnDrawOnCustomizeList  
 Voláno rámcem před `CMFCColorMenuButton` objektu se zobrazí v seznamu dialogového okna přizpůsobení panelu nástrojů.  
  
```  
virtual int OnDrawOnCustomizeList(
    CDC* pDC,  
    const CRect& rect,  
    BOOL bSelected);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *primárního řadiče domény*  
 Ukazatel na kontextu zařízení.  
  
 [v] *Rect –*  
 Obdélníku, která bounds tlačítko, které se mají vykreslovat.  
  
 [v] *bSelected*  
 `TRUE` Určuje, že je tlačítko ve vybraném stavu; v opačném `FALSE`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Šířka tlačítko.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána rámcem při `CMFCColorMenuButton` objektu se zobrazí v seznamu během procesu přizpůsobení panelu nástrojů.  
  
##  <a name="opencolordialog"></a>  CMFCColorMenuButton::OpenColorDialog  
 Otevře dialogové okno Výběr barev.  
  
```  
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,  
    COLORREF& colorRes);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *colorDefault*  
 Výchozí barvu, který je vybraný v dialogovém okně barvy.  
  
 [out] *colorRes*  
 Vrátí barvu, která si uživatel vybere ze dialogové okno barev.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud uživatel vybere nový barvy; jinak hodnota nula.  
  
### <a name="remarks"></a>Poznámky  
 Při kliknutí na tlačítko nabídky volejte tuto metodu za účelem otevřete dialogové okno barvy. Pokud je vrácená hodnota nenulové, barvu, která si uživatel vybere je uložen v *colorRes* parametr. Použití [CMFCColorMenuButton::EnableOtherButton](#enableotherbutton) metoda přepínat mezi dialogové okno Standardní barev a [CMFCColorDialog třída](../../mfc/reference/cmfccolordialog-class.md) dialogové okno.  
  
##  <a name="setcolor"></a>  CMFCColorMenuButton::SetColor  
 Nastaví barvu aktuální barva tlačítko.  
  
```  
virtual void SetColor(
    COLORREF clr,  
    BOOL bNotify=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *clr*  
 Hodnotu barva RGB.  
  
 [v] *bNotify*  
 `TRUE` Chcete-li použít *clr* parametr barvy, která má všechny související nabídky nebo tlačítko panelu nástrojů; jinak hodnota `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Voláním této metody lze změnit barvu aktuální barva tlačítko. Pokud *bNotify* parametr je nenulové hodnoty, barva na odpovídající tlačítko na všechny přidružené místní nabídky nebo nástrojů se změní na barvu určeného *clr* parametr.  
  
##  <a name="setcolorbycmdid"></a>  CMFCColorMenuButton::SetColorByCmdID  
 Nastaví barvu zadaná barva tlačítka nabídky.  
  
```  
static void SetColorByCmdID(
    UINT uiCmdID,  
    COLORREF color);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *uiCmdID*  
 ID prostředku tlačítka s nabídkou barev.  
  
 [v] *barev*  
 Hodnotu barva RGB.  
  
##  <a name="setcolorname"></a>  CMFCColorMenuButton::SetColorName  
 Nastaví nový název pro zadaná barva.  
  
```  
static void SetColorName(
    COLORREF color,  
    const CString& strName);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *barev*  
 Hodnota RGB barvu, jejíž název změní.  
  
 [v] *%{strName/*  
 Nový název barvy.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setcolumnsnumber"></a>  CMFCColorMenuButton::SetColumnsNumber  
 Nastaví počet sloupců do zobrazení v ovládacím prvku pro výběr barev ( [CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) objekt).  
  
```  
void SetColumnsNumber(int nColumns);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *nColumns*  
 Číslo sloupce k zobrazení.  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCColorBar – třída](../../mfc/reference/cmfccolorbar-class.md)   
 [CMFCToolBar – třída](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarsCustomizeDialog – třída](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)   
 [CMFCColorButton – třída](../../mfc/reference/cmfccolorbutton-class.md)
