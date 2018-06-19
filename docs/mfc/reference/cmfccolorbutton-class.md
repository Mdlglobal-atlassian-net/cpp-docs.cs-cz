---
title: Třída CMFCColorButton | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton::CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton::EnableAutomaticButton
- AFXCOLORBUTTON/CMFCColorButton::EnableOtherButton
- AFXCOLORBUTTON/CMFCColorButton::GetAutomaticColor
- AFXCOLORBUTTON/CMFCColorButton::GetColor
- AFXCOLORBUTTON/CMFCColorButton::SetColor
- AFXCOLORBUTTON/CMFCColorButton::SetColorName
- AFXCOLORBUTTON/CMFCColorButton::SetColumnsNumber
- AFXCOLORBUTTON/CMFCColorButton::SetDocumentColors
- AFXCOLORBUTTON/CMFCColorButton::SetPalette
- AFXCOLORBUTTON/CMFCColorButton::SizeToContent
- AFXCOLORBUTTON/CMFCColorButton::IsDrawXPTheme
- AFXCOLORBUTTON/CMFCColorButton::OnDraw
- AFXCOLORBUTTON/CMFCColorButton::OnDrawBorder
- AFXCOLORBUTTON/CMFCColorButton::OnDrawFocusRect
- AFXCOLORBUTTON/CMFCColorButton::OnShowColorPopup
- AFXCOLORBUTTON/CMFCColorButton::RebuildPalette
- AFXCOLORBUTTON/CMFCColorButton::UpdateColor
- AFXCOLORBUTTON/CMFCColorButton::m_bEnabledInCustomizeMode
dev_langs:
- C++
helpviewer_keywords:
- CMFCColorButton [MFC], CMFCColorButton
- CMFCColorButton [MFC], EnableAutomaticButton
- CMFCColorButton [MFC], EnableOtherButton
- CMFCColorButton [MFC], GetAutomaticColor
- CMFCColorButton [MFC], GetColor
- CMFCColorButton [MFC], SetColor
- CMFCColorButton [MFC], SetColorName
- CMFCColorButton [MFC], SetColumnsNumber
- CMFCColorButton [MFC], SetDocumentColors
- CMFCColorButton [MFC], SetPalette
- CMFCColorButton [MFC], SizeToContent
- CMFCColorButton [MFC], IsDrawXPTheme
- CMFCColorButton [MFC], OnDraw
- CMFCColorButton [MFC], OnDrawBorder
- CMFCColorButton [MFC], OnDrawFocusRect
- CMFCColorButton [MFC], OnShowColorPopup
- CMFCColorButton [MFC], RebuildPalette
- CMFCColorButton [MFC], UpdateColor
- CMFCColorButton [MFC], m_bEnabledInCustomizeMode
ms.assetid: 9fdf34ae-4cc5-4c5e-9d89-1c50e8a73699
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cea6fc2a543a528a0838479b2c47bea99f21cf96
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33371110"
---
# <a name="cmfccolorbutton-class"></a>CMFCColorButton – třída
`CMFCColorButton` a [CMFCColorBar třída](../../mfc/reference/cmfccolorbar-class.md) třídy se společně používají k implementaci ovládacího prvku pro výběr barev.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCColorButton : public CMFCButton  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCColorButton::CMFCColorButton](#cmfccolorbutton)|Vytvoří nový `CMFCColorButton` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton)|Povolí nebo zakáže "automatické" tlačítko, které je umístěné výše regulární barva tlačítek. (Automatické tlačítko standardní systému jmenuje **automatické**.)|  
|[CMFCColorButton::EnableOtherButton](#enableotherbutton)|Povolí nebo zakáže "ostatní" tlačítko, které je umístěné pod regulární barva tlačítek. (Standardní systém "ostatní" tlačítko jmenuje **Další barvy**.)|  
|[CMFCColorButton::GetAutomaticColor](#getautomaticcolor)|Načte aktuální automatické barvu.|  
|[CMFCColorButton::GetColor](#getcolor)|Načte tlačítko barvy.|  
|[CMFCColorButton::SetColor](#setcolor)|Nastaví barvu tlačítko.|  
|[CMFCColorButton::SetColorName](#setcolorname)|Nastaví název barvy.|  
|[CMFCColorButton::SetColumnsNumber](#setcolumnsnumber)|Nastaví počet sloupců v dialogovém okně pro výběr barev.|  
|[CMFCColorButton::SetDocumentColors](#setdocumentcolors)|Určuje seznam specifické pro dokument barev, které se zobrazují v dialogovém okně pro výběr barev.|  
|[CMFCColorButton::SetPalette](#setpalette)|Určuje paletu barev standardní zobrazení.|  
|[CMFCColorButton::SizeToContent](#sizetocontent)|Změní velikost ovládacího prvku tlačítko, v závislosti na velikosti jeho textových a obrázkových.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCColorButton::IsDrawXPTheme](#isdrawxptheme)|Označuje, zda aktuální barva tlačítko se zobrazí v vizuální styl systému Windows XP.|  
|[CMFCColorButton::OnDraw](#ondraw)|Voláno rámcem obrázek na tlačítko zobrazit.|  
|[CMFCColorButton::OnDrawBorder](#ondrawborder)|Voláno rámcem zobrazíte na tlačítko ohraničení.|  
|[CMFCColorButton::OnDrawFocusRect](#ondrawfocusrect)|Voláno rámcem zobrazíte rámečku fokusu, když je důraz na tlačítko.|  
|[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)|Voláno rámcem, o který se má zobrazit při dialogové okno pro výběr barev.|  
|[CMFCColorButton::RebuildPalette](#rebuildpalette)|Inicializuje `m_pPalette` chráněné zadaný palety nebo výchozí systémové palety – datový člen.|  
|[CMFCColorButton::UpdateColor](#updatecolor)|Voláno rámcem, když uživatel vybere barvu z palety dialogové okno pro výběr barev.|  
  
### <a name="data-members"></a>Datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|`m_bAltColorDlg`|Logická hodnota. Pokud `TRUE`, zobrazí rozhraní [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) barva dialogu při *jiné* po kliknutí na tlačítko, nebo, pokud `FALSE`, dialogové okno barev systému. Výchozí hodnota je `TRUE`. Další informace najdete v tématu [CMFCColorButton::EnableOtherButton](#enableotherbutton).|  
|`m_bAutoSetFocus`|Logická hodnota. Pokud `TRUE`, když se zobrazí v nabídce, nebo pokud rozhraní nastaví fokus v nabídce Barva `FALSE`, nezmění fokus. Výchozí hodnota je `TRUE`.|  
|[CMFCColorButton::m_bEnabledInCustomizeMode](#m_benabledincustomizemode)|Určuje, jestli je povolený režim přizpůsobení pro tlačítko barvy.|  
|`m_Color`|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) hodnotu. Obsahuje aktuálně vybrané barvy.|  
|`m_ColorAutomatic`|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) hodnotu. Obsahuje aktuálně vybrané výchozí barvu.|  
|`m_Colors`|A [carray –](../../mfc/reference/carray-class.md) z [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) hodnoty. Obsahuje aktuálně k dispozici barvy.|  
|`m_lstDocColors`|A [CList](../../mfc/reference/clist-class.md) z [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) hodnoty. Obsahuje aktuální barvy dokumentu.|  
|`m_nColumns`|Celé číslo. Obsahuje počet sloupců do zobrazení v mřížce barvy v nabídce Výběr barev.|  
|`m_pPalette`|Ukazatel [CPalette](../../mfc/reference/cpalette-class.md). Obsahuje barev, které jsou k dispozici v nabídce aktuální výběr barev.|  
|`m_pPopup`|Ukazatel [CMFCColorPopupMenu třída](../../mfc/reference/cmfccolorpopupmenu-class.md) objektu. V nabídce Výběr barvy, která se zobrazí po kliknutí na tlačítko barvy.|  
|`m_strAutoColorText`|Řetězec. Popisek tlačítka "automatické" v nabídce Výběr barev.|  
|`m_strDocColorsText`|Řetězec. Popisek tlačítka v nabídce Výběr barvy, která zobrazuje barvy dokumentu.|  
|`m_strOtherText`|Řetězec. Popisek tlačítko "ostatní" v nabídce Výběr barev.|  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení `CMFCColorButton` třída chová jako nabízené tlačítka, které se otevře dialogové okno pro výběr barev. Dialogové okno pro výběr barev obsahuje pole malé barva tlačítek a "ostatní" tlačítka zobrazující výběr vlastních barev. (Standardní systém "ostatní" tlačítko jmenuje **Další barvy**.) Když uživatel vybere novou barvu, `CMFCColorButton` objekt změna se projeví a zobrazí vybrané barvy.  
  
 Vytvoření ovládacího prvku tlačítko barvy, buď přímo v kódu, nebo pomocí **ClassWizard** nástroje a šablony pole dialogového okna. Pokud vytvoříte ovládací prvek tlačítko barvy přímo, přidejte `CMFCColorButton` proměnnou vaší aplikace a pak volání konstruktoru a `Create` metody `CMFCColorButton` objektu. Pokud použijete **ClassWizard**, přidejte `CButton` proměnné k vaší aplikaci a poté změňte typ proměnné z `CButton` k `CMFCColorButton`.  
  
 Dialogové okno pro výběr barev ( [CMFCColorBar třída](../../mfc/reference/cmfccolorbar-class.md)) se zobrazí [CMFCColorButton::OnShowColorPopup](#onshowcolorpopup) metoda při volání rozhraní `OnLButtonDown` obslužné rutiny události. [CMFCColorButton::OnShowColorPopup](#onshowcolorpopup) metoda může být potlačena za účelem podpory výběr vlastních barev.  
  
 `CMFCColorButton` Objekt upozorní nadřazené barvu, která mění odesláním `WM_COMMAND | BN_CLICKED` oznámení. Nadřazený používá [CMFCColorButton::GetColor](#getcolor) metoda pro načtení platnou barvu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nakonfigurovat barva tlačítko pomocí různých metod v `CMFCColorButton` třídy. Metody nastavení barvy tlačítko barvy a jeho počet sloupců a povolit automatického a další tlačítka. Tato ukázka je součástí [stav panelu Demo-ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_StatusBarDemo#10](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_1.h)]  
[!code-cpp[NVC_MFC_StatusBarDemo#11](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_2.cpp)]  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcolorbutton.h  
  
##  <a name="cmfccolorbutton"></a>  CMFCColorButton::CMFCColorButton  
 Vytvoří nový `CMFCColorButton` objektu.  
  
```  
CMFCColorButton();
```  
  
##  <a name="enableautomaticbutton"></a>  CMFCColorButton::EnableAutomaticButton  
 Povolit nebo zakázat tlačítko "automatické" v ovládacím prvku pro výběr barev a nastavte barvu automaticky (výchozí).  
  
```  
void EnableAutomaticButton(
    LPCTSTR lpszLabel,  
    COLORREF colorAutomatic,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `lpszLabel`  
 Určuje text automatické tlačítka.  
  
 [v] `colorAutomatic`  
 Hodnota RGB, která určuje výchozí barvu automatické tlačítko.  
  
 [v] `bEnable`  
 Určuje, zda je povoleno automatické tlačítko.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="enableotherbutton"></a>  CMFCColorButton::EnableOtherButton  
 Povolit nebo zakázat "ostatní" tlačítko, které se zobrazí pod regulární barva tlačítek.  
  
```  
void EnableOtherButton(
    LPCTSTR lpszLabel,  
    BOOL bAltColorDlg=TRUE,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `lpszLabel`  
 Určuje text, na tlačítko.  
  
 [v] `bAltColorDlg`  
 Určuje, zda [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) otevřít dialogové okno nebo dialogové okno barvy systém když uživatel klikne na tlačítko.  
  
 [v] `bEnable`  
 Určuje, zda je povoleno tlačítko "ostatní".  
  
### <a name="remarks"></a>Poznámky  
 Klikněte na tlačítko "ostatní" zobrazíte dialogové okno barvy. Pokud *bAltColorDlg* parametr `TRUE`, [CMFCColorDialog třída](../../mfc/reference/cmfccolordialog-class.md) se zobrazí; jinak se zobrazí dialogové okno barev systému.  
  
##  <a name="getautomaticcolor"></a>  CMFCColorButton::GetAutomaticColor  
 Načte aktuální barvu automaticky (výchozí).  
  
```  
COLORREF GetAutomaticColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnotu RGB představující aktuální automatické barvu.  
  
### <a name="remarks"></a>Poznámky  
 Aktuální automatické barva nastavena [CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton) metoda.  
  
##  <a name="getcolor"></a>  CMFCColorButton::GetColor  
 Načte aktuálně vybrané barvy.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnotu RGB.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="isdrawxptheme"></a>  CMFCColorButton::IsDrawXPTheme  
 Označuje, zda aktuální barva tlačítko se zobrazí v vizuální styl systému Windows XP.  
  
```  
BOOL IsDrawXPTheme() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud jsou podporovány vizuální styly a aktuální barva tlačítko se zobrazí v vizuální styl Windows XP. v opačném `FALSE`.  
  
##  <a name="m_benabledincustomizemode"></a>  CMFCColorButton::m_bEnabledInCustomizeMode  
 Barva tlačítko nastaví do režimu přizpůsobení.  
  
```  
BOOL m_bEnabledInCustomizeMode;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud potřebujete přidat tlačítko barvy na stránku přizpůsobení dialog (nebo uživateli umožní vybrat jinou možnost Barva během přizpůsobování), povolte tlačítko nastavením `m_bEnabledInCustomizeMode` člena `TRUE`. Ve výchozím nastavení je tento člen nastavena na `FALSE`.  
  
##  <a name="ondraw"></a>  CMFCColorButton::OnDraw  
 Voláno rámcem Vykreslit obrázek na tlačítko.  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rect,  
    UINT uiState);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pDC`  
 Body do kontextu zařízení, která se použije k vykreslení bitové kopie na tlačítko.  
  
 [v] `rect`  
 Obdélníku, která bounds tlačítko.  
  
 [v] `uiState`  
 Určuje vizuální stav zobrazí tlačítko.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu za účelem přizpůsobení proces vykreslování.  
  
##  <a name="ondrawborder"></a>  CMFCColorButton::OnDrawBorder  
 Voláno rámcem zobrazíte ohraničení tlačítko.  
  
```  
virtual void OnDrawBorder(
    CDC* pDC,  
    CRect& rectClient,  
    UINT uiState);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pDC`  
 Body do kontextu zařízení použít k vykreslení ohraničení.  
  
 [v] `rectClient`  
 Obdélníku v kontextu zařízení, která je zadána `pDC` parametr, který definuje hranice tlačítka, které se mají vykreslovat.  
  
 [v] `uiState`  
 Určuje vizuální stav zobrazí tlačítko.  
  
### <a name="remarks"></a>Poznámky  
 Přepsání této funkci můžete přizpůsobit vzhled tlačítka Barva ohraničení.  
  
##  <a name="ondrawfocusrect"></a>  CMFCColorButton::OnDrawFocusRect  
 Voláno rámcem zobrazíte rámečku fokusu, když má právě fokus, tlačítko.  
  
```  
virtual void OnDrawFocusRect(
    CDC* pDC,  
    const CRect& rectClient);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pDC`  
 Body použitý k vykreslení rámečku fokusu v kontextu zařízení.  
  
 [v] `rectClient`  
 Obdélníku v kontextu zařízení určeného `pDC` parametr, který definuje hranice tlačítko.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu za účelem přizpůsobení vzhledu rámečku fokusu.  
  
##  <a name="onshowcolorpopup"></a>  CMFCColorButton::OnShowColorPopup  
 Voláno před provedením pruhu barev v automaticky otevřeném okně se zobrazí.  
  
```  
virtual void OnShowColorPopup();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="rebuildpalette"></a>  CMFCColorButton::RebuildPalette  
 Inicializuje `m_pPalette` chráněné zadaný palety nebo výchozí systémové palety – datový člen.  
  
```  
void RebuildPalette(CPalette* pPal);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v] `pPal`|Ukazatel na logické palety nebo `NULL`. Pokud `NULL`, je použit výchozí systémové palety.|  
  
##  <a name="setcolor"></a>  CMFCColorButton::SetColor  
 Určuje barvu tlačítka.  
  
```  
void SetColor(COLORREF color);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `color`  
 Hodnotu RGB.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setcolorname"></a>  CMFCColorButton::SetColorName  
 Určuje název barvy.  
  
```  
static void SetColorName(
    COLORREF color,  
    const CString& strName);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `color`  
 Hodnoty RGB barvy.  
  
 [v] `strName`  
 Názvu barvy.  
  
### <a name="remarks"></a>Poznámky  
 Seznam názvů barva je globální na aplikaci. V důsledku toho tato metoda přenáší jeho parametry [CMFCColorBar::SetColorName](../../mfc/reference/cmfccolorbar-class.md#setcolorname).  
  
##  <a name="setcolumnsnumber"></a>  CMFCColorButton::SetColumnsNumber  
 Definuje počet sloupců, které se zobrazují v tabulce barev, které se zobrazí uživatelům během procesu výběru barva uživatele.  
  
```  
void SetColumnsNumber(int nColumns);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nColumns`  
 Určuje počet sloupců.  
  
### <a name="remarks"></a>Poznámky  
 Uživatel může vybrat barvu z pruhu barev místní nabídka, která zobrazuje tabulku předdefinované barvy. Tuto metodu použijte k definování počet sloupců v tabulce.  
  
##  <a name="setdocumentcolors"></a>  CMFCColorButton::SetDocumentColors  
 Určuje sadu barev a název sady pro. Se zobrazí sada barvy, použití [CMFCColorBar třída](../../mfc/reference/cmfccolorbar-class.md) objektu.  
  
```  
void SetDocumentColors(
    LPCTSTR lpszLabel,  
    CList<COLORREF,COLORREF>& lstColors);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `lpszLabel`  
 Určuje popisek, který se má zobrazit sadou barvy dokumentu.  
  
 [v] `lstColors`  
 Odkaz na seznam hodnoty RGB.  
  
### <a name="remarks"></a>Poznámky  
 A `CMFCColorButton` objekt udržuje seznam hodnoty RGB, které se přenáší do [CMFCColorBar třída](../../mfc/reference/cmfccolorbar-class.md) objektu. Když se zobrazí pruhu barev, tyto barvy se zobrazují v speciální části, jejichž popisek je zadána `lpszLabel` parametr.  
  
##  <a name="setpalette"></a>  CMFCColorButton::SetPalette  
 Určuje standardní barvy zobrazíte na pruhu barev v automaticky otevřeném okně.  
  
```  
void SetPalette(CPalette* pPalette);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pPalette`  
 Ukazatel na paletu barev.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="sizetocontent"></a>  CMFCColorButton::SizeToContent  
 Změní velikost ovládacího prvku tlačítko podle jeho textových a obrázkových.  
  
```  
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bCalcOnly`  
 Pokud nenulové hodnoty, se vypočítává nové velikosti ovládacího prvku tlačítko však skutečná velikost se nezmění.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CSize` objekt, který určuje novou velikost ovládacího prvku tlačítko.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="updatecolor"></a>  CMFCColorButton::UpdateColor  
 Voláno rámcem, když uživatel vybere barvu, která z pruhu barev, které se zobrazí, když uživatel klikne na tlačítko barvy.  
  
```  
virtual void UpdateColor(COLORREF color);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `color`  
 Barva vybraná uživatelem.  
  
### <a name="remarks"></a>Poznámky  
 `UpdateColor` Funkce se změní na aktuálně vybrané tlačítko barvy a upozorní nadřazené odesláním `WM_COMMAND` zpráv s `BN_CLICKED` standardní oznámení. Použití [CMFCColorButton::GetColor](#getcolor) metoda pro načtení vybrané barvy.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCButton – třída](../../mfc/reference/cmfcbutton-class.md)   
 [CMFCColorBar – třída](../../mfc/reference/cmfccolorbar-class.md)   
 [CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)   
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)   
 [CPalette – třída](../../mfc/reference/cpalette-class.md)   
 [Carray – třída](../../mfc/reference/carray-class.md)   
 [CList – třída](../../mfc/reference/clist-class.md)   
 [CString](../../atl-mfc-shared/reference/cstringt-class.md)
