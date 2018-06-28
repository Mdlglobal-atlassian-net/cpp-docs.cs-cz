---
title: Třída CMFCCaptionBar | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCCaptionBar
- AFXCAPTIONBAR/CMFCCaptionBar
- AFXCAPTIONBAR/CMFCCaptionBar::Create
- AFXCAPTIONBAR/CMFCCaptionBar::DoesAllowDynInsertBefore
- AFXCAPTIONBAR/CMFCCaptionBar::EnableButton
- AFXCAPTIONBAR/CMFCCaptionBar::GetAlignment
- AFXCAPTIONBAR/CMFCCaptionBar::GetBorderSize
- AFXCAPTIONBAR/CMFCCaptionBar::GetButtonRect
- AFXCAPTIONBAR/CMFCCaptionBar::GetMargin
- AFXCAPTIONBAR/CMFCCaptionBar::IsMessageBarMode
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveBitmap
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveButton
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveIcon
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveText
- AFXCAPTIONBAR/CMFCCaptionBar::SetBitmap
- AFXCAPTIONBAR/CMFCCaptionBar::SetBorderSize
- AFXCAPTIONBAR/CMFCCaptionBar::SetButton
- AFXCAPTIONBAR/CMFCCaptionBar::SetButtonPressed
- AFXCAPTIONBAR/CMFCCaptionBar::SetButtonToolTip
- AFXCAPTIONBAR/CMFCCaptionBar::SetFlatBorder
- AFXCAPTIONBAR/CMFCCaptionBar::SetIcon
- AFXCAPTIONBAR/CMFCCaptionBar::SetImageToolTip
- AFXCAPTIONBAR/CMFCCaptionBar::SetMargin
- AFXCAPTIONBAR/CMFCCaptionBar::SetText
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawBackground
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawBorder
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawButton
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawImage
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawText
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarBackground
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarBorder
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarText
dev_langs:
- C++
helpviewer_keywords:
- CMFCCaptionBar [MFC], Create
- CMFCCaptionBar [MFC], DoesAllowDynInsertBefore
- CMFCCaptionBar [MFC], EnableButton
- CMFCCaptionBar [MFC], GetAlignment
- CMFCCaptionBar [MFC], GetBorderSize
- CMFCCaptionBar [MFC], GetButtonRect
- CMFCCaptionBar [MFC], GetMargin
- CMFCCaptionBar [MFC], IsMessageBarMode
- CMFCCaptionBar [MFC], RemoveBitmap
- CMFCCaptionBar [MFC], RemoveButton
- CMFCCaptionBar [MFC], RemoveIcon
- CMFCCaptionBar [MFC], RemoveText
- CMFCCaptionBar [MFC], SetBitmap
- CMFCCaptionBar [MFC], SetBorderSize
- CMFCCaptionBar [MFC], SetButton
- CMFCCaptionBar [MFC], SetButtonPressed
- CMFCCaptionBar [MFC], SetButtonToolTip
- CMFCCaptionBar [MFC], SetFlatBorder
- CMFCCaptionBar [MFC], SetIcon
- CMFCCaptionBar [MFC], SetImageToolTip
- CMFCCaptionBar [MFC], SetMargin
- CMFCCaptionBar [MFC], SetText
- CMFCCaptionBar [MFC], OnDrawBackground
- CMFCCaptionBar [MFC], OnDrawBorder
- CMFCCaptionBar [MFC], OnDrawButton
- CMFCCaptionBar [MFC], OnDrawImage
- CMFCCaptionBar [MFC], OnDrawText
- CMFCCaptionBar [MFC], m_clrBarBackground
- CMFCCaptionBar [MFC], m_clrBarBorder
- CMFCCaptionBar [MFC], m_clrBarText
ms.assetid: acb54d5f-14ff-4c96-aeb3-7717cf566d9a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5f655d8bd6fbfd19182bbaeed21eaa95739ff33d
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37038969"
---
# <a name="cmfccaptionbar-class"></a>CMFCCaptionBar – třída
A `CMFCCaptionBar` objekt je ovládací prvek panel, který může zobrazit tři prvky: tlačítko, štítek text a rastrový obrázek. Současně se může zobrazit pouze jeden element každého typu. Každý prvek levé nebo pravé hrany ovládací prvek nebo k centru můžete zarovnat. Styl ploché nebo 3D může platit taky pro horní a dolní ohraničení panelu titulek.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCCaptionBar : public CPane  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCCaptionBar::Create](#create)|Ovládací prvek popisek panelu vytvoří a připojí jej k `CMFCCaptionBar` objektu.|  
|[CMFCCaptionBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|Určuje, zda jiný podokně můžete dynamicky vložen mezi panelu popisek a jeho nadřazené rámečku. (Přepisuje [CBasePane::DoesAllowDynInsertBefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|  
|[CMFCCaptionBar::EnableButton](#enablebutton)|Povolí nebo zakáže tlačítka na panelu titulek.|  
|[CMFCCaptionBar::GetAlignment](#getalignment)|Vrátí zadaný element zarovnání.|  
|[CMFCCaptionBar::GetBorderSize](#getbordersize)|Vrátí velikost ohraničení panelu titulek.|  
|[CMFCCaptionBar::GetButtonRect](#getbuttonrect)|Načte ohraničující obdélník tlačítka na panelu titulek.|  
|[CMFCCaptionBar::GetMargin](#getmargin)|Vrací vzdálenost mezi okrajem panelu elementů popisek a okraji ovládacího panelu titulek.|  
|[CMFCCaptionBar::IsMessageBarMode](#ismessagebarmode)|Určuje, jestli na titulek panelu je v režimu panelu zpráv.|  
|[CMFCCaptionBar::RemoveBitmap](#removebitmap)|Odebere rastrového obrázku panelu titulek.|  
|[CMFCCaptionBar::RemoveButton](#removebutton)|Odebere tlačítko panelu titulek.|  
|[CMFCCaptionBar::RemoveIcon](#removeicon)|Odebere ikonu z panelu titulek.|  
|[CMFCCaptionBar::RemoveText](#removetext)|Textový popisek, odeberete z panelu titulek.|  
|[CMFCCaptionBar::SetBitmap](#setbitmap)|Nastaví pro bitovou kopii rastrového obrázku panelu titulek.|  
|[CMFCCaptionBar::SetBorderSize](#setbordersize)|Nastaví velikost ohraničení panelu titulek.|  
|[CMFCCaptionBar::SetButton](#setbutton)|Nastaví na tlačítko panelu titulek.|  
|[CMFCCaptionBar::SetButtonPressed](#setbuttonpressed)|Určuje, zda zůstává tlačítko při stisknutí tlačítka.|  
|[CMFCCaptionBar::SetButtonToolTip](#setbuttontooltip)|Nastaví popis tlačítka pro tlačítko.|  
|[CMFCCaptionBar::SetFlatBorder](#setflatborder)|Nastaví styl ohraničení panelu titulek.|  
|[CMFCCaptionBar::SetIcon](#seticon)|Nastaví na ikonu pro záhlaví.|  
|[CMFCCaptionBar::SetImageToolTip](#setimagetooltip)|Nastaví popisek pro bitovou kopii pro panelu titulek.|  
|[CMFCCaptionBar::SetMargin](#setmargin)|Nastaví vzdálenost mezi hrany panelu element caption a okraji ovládacího panelu titulek.|  
|[CMFCCaptionBar::SetText](#settext)|Nastaví textový popisek pro panelu titulek.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCCaptionBar::OnDrawBackground](#ondrawbackground)|Voláno rámcem k vyplnění pozadí panelu titulek.|  
|[CMFCCaptionBar::OnDrawBorder](#ondrawborder)|Voláno rámcem k vykreslení ohraničení panelu titulek.|  
|[CMFCCaptionBar::OnDrawButton](#ondrawbutton)|Voláno rámcem k vykreslení tlačítko panelu titulek.|  
|[CMFCCaptionBar::OnDrawImage](#ondrawimage)|Voláno rámcem kreslení obrázku panelu titulek.|  
|[CMFCCaptionBar::OnDrawText](#ondrawtext)|Voláno rámcem k vykreslení panelu text titulku.|  
  
### <a name="data-members"></a>Datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCCaptionBar::m_clrBarBackground](#m_clrbarbackground)|Barva pozadí panelu titulek.|  
|[CMFCCaptionBar::m_clrBarBorder](#m_clrbarborder)|Barva ohraničení panelu titulek.|  
|[CMFCCaptionBar::m_clrBarText](#m_clrbartext)|Barva řádku text titulku.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud chcete vytvořit záhlaví, postupujte takto:  
  
1.  Vytvořit `CMFCCaptionBar` objektu. Obvykle přidejte panelu popisek třídy oken s rámečkem.  
  
2.  Volání [CMFCCaptionBar::Create](#create) metodu pro vytvoření ovládacího prvku popisek panelu a připojte ji k `CMFCCaptionBar` objektu.  
  
3.  Volání [CMFCCaptionBar::SetButton](#setbutton), [CMFCCaptionBar::SetText](#settext), [CMFCCaptionBar::SetIcon](#seticon), a [CMFCCaptionBar::SetBitmap](#setbitmap)nastavit elementy panelu titulek.  
  
 Když nastavíte button element, je nutné přiřadit ID příkazu pro tlačítko. Když uživatel klikne na tlačítko, trasy panelu popisek `WM_COMMAND` zprávy, které mají toto ID do nadřazeného rámce okna.  
  
 Na panelu titulek může spolupracovat taky v režimu panelu zpráv, které emuluje panelu zpráv, který se zobrazí v aplikacích Microsoft Office 2007. V režimu panelu zpráv na titulek panelu zobrazí rastrový obrázek, zprávu a tlačítko (což obvykle otevře dialogové okno.) Popisek lze přiřadit bitové mapy.  
  
 Chcete-li povolit režim panelu zprávy, volejte [CMFCCaptionBar::Create](#create) a nastavte čtvrtého parametru (bIsMessageBarMode) na `TRUE`.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pomocí různých metod v nástroji `CMFCCaptionBar` třídy. Příklad ukazuje postup vytvoření ovládacího prvku popisek panelu, nastavit 3D ohraničení panelu titulku, nastavena vzdálenost v pixelech, mezi hrany titulek panelu elementy a okraji ovládacího panelu titulku, nastavte na tlačítko panelu popisek , nastavit popis tlačítka pro tlačítko, nastavit textový popisek pro panelu titulku, nastavit rastrový obrázek pro panelu popisek a nastavit popis tlačítka pro bitovou kopii na panelu titulek. Tento fragment kódu je součástí [MS Office 2007 Demo-ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#1](../../mfc/reference/codesnippet/cpp/cmfccaptionbar-class_1.h)]  
[!code-cpp[NVC_MFC_MSOffice2007Demo#2](../../mfc/reference/codesnippet/cpp/cmfccaptionbar-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCCaptionBar](../../mfc/reference/cmfccaptionbar-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcaptionbar.h  
  
##  <a name="create"></a>  CMFCCaptionBar::Create  
 Ovládací prvek popisek panelu vytvoří a připojí jej k `CMFCCaptionBar` objektu.  
  
```  
BOOL Create(
    DWORD dwStyle,  
    CWnd* pParentWnd,  
    UINT uID,  
    int nHeight=-1,  
    BOOL bIsMessageBarMode=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 *dwStyle*  
 Logické nebo kombinace styly řádku titulku.  
  
 *pParentWnd*  
 Nadřazené okno ovládacího panelu titulek.  
  
 *uID*  
 ID ovládacího panelu titulek.  
  
 *nHeight*  
 Výška v pixelech ovládacího prvku popisek panelu. Pokud je -1, výška se vypočítává podle výšky na ikonu, text a tlačítko, které tento ovládací prvek popisek panelu zobrazí.  
  
 *bIsMessageBarMode*  
 `TRUE` Pokud je panel titulek v režimu panelu zpráv; `FALSE` jinak.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud ovládací prvek popisek panelu je vytvořen úspěšně; `FALSE` jinak.  
  
### <a name="remarks"></a>Poznámky  
 Můžete vytvořit `CMFCCaptionBar` objektu ve dvou krocích. Nejprve budete volat konstruktor, a poté zavoláte `Create` metoda, která vytvoří ovládacího prvku Windows a připojí jej k `CMFCCaptionBar` objektu.  
  
##  <a name="doesallowdyninsertbefore"></a>  CMFCCaptionBar::DoesAllowDynInsertBefore  
 Určuje, zda jiný podokně můžete dynamicky vložen mezi panelu popisek a jeho nadřazené rámečku.  
  
```  
virtual BOOL DoesAllowDynInsertBefore() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `FALSE` přepsána.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="enablebutton"></a>  CMFCCaptionBar::EnableButton  
 Povolí nebo zakáže tlačítka na panelu titulek.  
  
```  
void EnableButton(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *bEnable*  
 `TRUE` Chcete-li na tlačítko Povolit `FALSE` na tlačítko zakázat.  
  
##  <a name="getalignment"></a>  CMFCCaptionBar::GetAlignment  
 Vrátí zadaný element zarovnání.  
  
```  
BarElementAlignment GetAlignment(BarElement elem);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *elem*  
 Element caption panelu pro které chcete načíst zarovnání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Zarovnání elementu, jako je tlačítko rastrový obrázek, text nebo ikonu.  
  
### <a name="remarks"></a>Poznámky  
 Zarovnání element může být jedna z následujících hodnot:  
  
-   ALIGN_INVALID  
  
-   ALIGN_LEFT  
  
-   ALIGN_RIGHT  
  
-   ALIGN_CENTER  
  
##  <a name="getbordersize"></a>  CMFCCaptionBar::GetBorderSize  
 Vrátí velikost ohraničení panelu titulek.  
  
```  
int GetBorderSize() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Velikost v pixelech, ohraničení.  
  
##  <a name="getbuttonrect"></a>  CMFCCaptionBar::GetButtonRect  
 Načte ohraničující obdélník tlačítka na panelu titulek.  
  
```  
CRect GetButtonRect() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CRect` objekt, který obsahuje souřadnice ohraničující obdélník tlačítka na panelu titulek.  
  
##  <a name="getmargin"></a>  CMFCCaptionBar::GetMargin  
 Vrací vzdálenost mezi okrajem panelu elementů popisek a okraji ovládacího panelu titulek.  
  
```  
int GetMargin() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vzdálenost v pixelech, mezi okraj řádku elementů popisek a okraji ovládacího panelu titulek.  
  
##  <a name="ismessagebarmode"></a>  CMFCCaptionBar::IsMessageBarMode  
 Určuje, jestli na titulek panelu je v režimu panelu zpráv.  
  
```  
BOOL IsMessageBarMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud je panel titulek v režimu panelu zpráv; `FALSE` jinak.  
  
### <a name="remarks"></a>Poznámky  
 V režimu panelu zpráv na titulek panelu zobrazí obrázek s popisek, text zprávy a tlačítko.  
  
##  <a name="m_clrbarbackground"></a>  CMFCCaptionBar::m_clrBarBackground  
 Barva pozadí panelu titulek.  
  
```  
COLORREF m_clrBarBackground  
```  
  
##  <a name="m_clrbarborder"></a>  CMFCCaptionBar::m_clrBarBorder  
 Barva ohraničení panelu titulek.  
  
```  
COLORREF m_clrBarBorder  
```  
  
##  <a name="m_clrbartext"></a>  CMFCCaptionBar::m_clrBarText  
 Barva řádku text titulku.  
  
```  
COLORREF m_clrBarText  
```  
  
##  <a name="ondrawbackground"></a>  CMFCCaptionBar::OnDrawBackground  
 Voláno rámcem k vyplnění pozadí panelu titulek.  
  
```  
virtual void OnDrawBackground(
    CDC* pDC,  
    CRect rect);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *primárního řadiče domény*  
 Ukazatel na zařízení kontextu panelu titulek.  
  
 [v] *Rect –*  
 Ohraničující obdélník k vyplnění.  
  
### <a name="remarks"></a>Poznámky  
 `OnDrawBackground` Metoda je volána, když na pozadí panelu popisek má být vyplněna. Výchozí implementace doplní na pozadí pomocí [CMFCCaptionBar::m_clrBarBackground](#m_clrbarbackground) barev.  
  
 Potlačí tuto metodu v `CMFCCaptionBar` odvozené třídy k přizpůsobení vzhledu ovládacího panelu titulek.  
  
##  <a name="ondrawborder"></a>  CMFCCaptionBar::OnDrawBorder  
 Voláno rámcem k vykreslení ohraničení panelu titulek.  
  
```  
virtual void OnDrawBorder(
    CDC* pDC,  
    CRect rect);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *primárního řadiče domény*  
 Kontext zařízení, která se používá k zobrazení ohraničení.  
  
 [v] *Rect –*  
 Ohraničující obdélník.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení mají ohraničení ploché styl.  
  
 Potlačí tuto metodu v `CMFCCaptionBar` odvozené třídy k přizpůsobení vzhledu ohraničení panelu titulek.  
  
##  <a name="ondrawbutton"></a>  CMFCCaptionBar::OnDrawButton  
 Voláno rámcem k vykreslení tlačítko panelu titulek.  
  
```  
virtual void OnDrawButton(
    CDC* pDC,  
    CRect rect,  
    const CString& strButton,  
    BOOL bEnabled);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *primárního řadiče domény*  
 Ukazatel na kontextu zařízení, která se používá k zobrazení tlačítka.  
  
 [v] *Rect –*  
 Ohraničující obdélník tlačítko.  
  
 [v] *strButton*  
 Text popisku tlačítka.  
  
 [v] *bEnabled*  
 `TRUE` Pokud je povoleno tlačítko; `FALSE` jinak.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu v `CMFCCaptionBar` odvozené třídy přizpůsobit vzhled tlačítka panelu titulek.  
  
##  <a name="ondrawimage"></a>  CMFCCaptionBar::OnDrawImage  
 Voláno rámcem kreslení obrázku panelu titulek.  
  
```  
virtual void OnDrawImage(
    CDC* pDC,  
    CRect rect);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *primárního řadiče domény*  
 Ukazatel na kontextu zařízení, která se používá k zobrazení bitovou kopii.  
  
 [v] *Rect –*  
 Určuje ohraničující obdélník bitovou kopii.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu v `CMFCCaptionBar` odvozené třídy přizpůsobit vzhled obrázku.  
  
##  <a name="ondrawtext"></a>  CMFCCaptionBar::OnDrawText  
 Voláno rámcem k vykreslení panelu text titulku.  
  
```  
virtual void OnDrawText(
    CDC* pDC,  
    CRect rect,  
    const CString& strText);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *primárního řadiče domény*  
 Ukazatel na kontextu zařízení, která se používá k zobrazení tlačítka.  
  
 [v] *Rect –*  
 Ohraničující obdélník text.  
  
 [v] *strText*  
 Textový řetězec k zobrazení.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace zobrazí text s použitím `CDC::DrawText` a [CMFCCaptionBar::m_clrBarText](#m_clrbartext) barev.  
  
 Potlačí tuto metodu v `CMFCCaptionBar` odvozené třídy přizpůsobit vzhled panelu titulek textu.  
  
##  <a name="removebitmap"></a>  CMFCCaptionBar::RemoveBitmap  
 Odebere rastrového obrázku panelu titulek.  
  
```  
void RemoveBitmap();
```  
  
##  <a name="removebutton"></a>  CMFCCaptionBar::RemoveButton  
 Odebere tlačítko panelu titulek.  
  
```  
void RemoveButton();
```  
  
### <a name="remarks"></a>Poznámky  
 Rozložení panelu prvků titulek jsou automaticky upraví.  
  
##  <a name="removeicon"></a>  CMFCCaptionBar::RemoveIcon  
 Odebere ikonu z panelu titulek.  
  
```  
void RemoveIcon();
```  
  
##  <a name="removetext"></a>  CMFCCaptionBar::RemoveText  
 Textový popisek, odeberete z panelu titulek.  
  
```  
void RemoveText();
```  
  
##  <a name="setbitmap"></a>  CMFCCaptionBar::SetBitmap  
 Nastaví pro bitovou kopii rastrového obrázku panelu titulek.  
  
```  
void SetBitmap(
    HBITMAP hBitmap,  
    COLORREF clrTransparent,  
    BOOL bStretch=FALSE,  
    BarElementAlignment bmpAlignment=ALIGN_RIGHT);

 
void SetBitmap(
    UINT uiBmpResID,  
    COLORREF clrTransparent,  
    BOOL bStretch=FALSE,  
    BarElementAlignment bmpAlignment=ALIGN_RIGHT);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *hBitmap*  
 Popisovač rastrového obrázku nastavit.  
  
 [v] *clrTransparent*  
 Hodnota RGB, který určuje průhlednou barvu bitmapy.  
  
 [v] *bStretch*  
 Pokud `TRUE`, rastrový obrázek je roztažen tak, pokud nevejde do bitové kopie ohraničujícího rámečku. Jinak není roztažená bitové mapy.  
  
 [v] *bmpAlignment*  
 Zarovnání bitové mapy.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte k nastavení rastrový obrázek v řádku záhlaví.  
  
 Předchozí rastrový obrázek automaticky zničena. Pokud panelu titulek zobrazí ikonu, protože jste volali metodu [CMFCCaptionBar::SetIcon](#seticon) metody bitmapy se nezobrazí, pokud odeberete ikonu voláním [CMFCCaptionBar::RemoveIcon](#removeicon).  
  
 Bitmapy je zarovnán podle *bmpAlignment* parametr.  Tento parametr může být jeden z následujících `BarElementAlignment` hodnoty:  
  
-   ALIGN_INVALID  
  
-   ALIGN_LEFT  
  
-   ALIGN_RIGHT  
  
-   ALIGN_CENTER  
  
##  <a name="setbordersize"></a>  CMFCCaptionBar::SetBorderSize  
 Nastaví velikost ohraničení panelu titulek.  
  
```  
void SetBorderSize(int nSize);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *nSize*  
 Novou velikost v pixelech, ohraničení panelu titulek.  
  
##  <a name="setbutton"></a>  CMFCCaptionBar::SetButton  
 Nastaví na tlačítko panelu titulek.  
  
```  
void SetButton(
    LPCTSTR lpszLabel,  
    UINT uiCmdUI,  
    BarElementAlignment btnAlignmnet=ALIGN_LEFT,  
    BOOL bHasDropDownArrow=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszLabel*  
 Popisek příkazového tlačítka.  
  
 *uiCmdUI*  
 ID příkazu pro tlačítka.  
  
 *btnAlignmnet*  
 Zarovnání na tlačítko.  
  
 *bHasDropDownArrow*  
 `TRUE` je-li na tlačítko zobrazí rozevírací šipku, `FALSE` jinak.  
  
##  <a name="setbuttonpressed"></a>  CMFCCaptionBar::SetButtonPressed  
 Určuje, zda zůstává tlačítko při stisknutí tlačítka.  
  
```  
void SetButtonPressed(BOOL bPresed=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *bPresed*  
 `TRUE` Pokud tlačítko udržuje stav při stisknutí tlačítka `FALSE` jinak.  
  
##  <a name="setbuttontooltip"></a>  CMFCCaptionBar::SetButtonToolTip  
 Nastaví popis tlačítka pro tlačítko.  
  
```  
void SetButtonToolTip(
    LPCTSTR lpszToolTip,  
    LPCTSTR lpszDescription=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *lpszToolTip*  
 Popisek popisek.  
  
 [v] *lpszDescription*  
 Popis popisku.  
  
##  <a name="setflatborder"></a>  CMFCCaptionBar::SetFlatBorder  
 Nastaví styl ohraničení panelu titulek.  
  
```  
void SetFlatBorder(BOOL bFlat=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *bFlat*  
 `TRUE` Pokud je plochý ohraničení indikátoru titulek. `FALSE` Pokud není 3D.  
  
##  <a name="seticon"></a>  CMFCCaptionBar::SetIcon  
 Nastaví na ikonu pro záhlaví.  
  
```  
void SetIcon(
    HICON hIcon,  
    BarElementAlignment iconAlignment=ALIGN_RIGHT);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *hIcon*  
 Popisovač na ikonu nastavení.  
  
 [v] *iconAlignment*  
 Zarovnání ikonu.  
  
### <a name="remarks"></a>Poznámky  
 Popisek řádky můžete zobrazit ikony nebo bitmapy. V tématu [CMFCCaptionBar::SetBitmap](#setbitmap) a zjistěte, jak zobrazit rastrový obrázek. Pokud jste nastavili ikony i bitmapy, se vždy zobrazuje ikonu. Volání [CMFCCaptionBar::RemoveIcon](#removeicon) odebrání ikonu na panelu titulek.  
  
 Ikona je zarovnán podle požadavků *iconAlignment* parametr. Může být jeden z následujících `BarElementAlignment` hodnoty:  
  
-   ALIGN_INVALID  
  
-   ALIGN_LEFT  
  
-   ALIGN_RIGHT  
  
-   ALIGN_CENTER  
  
##  <a name="setimagetooltip"></a>  CMFCCaptionBar::SetImageToolTip  
 Nastaví popisek pro bitovou kopii na panelu titulek.  
  
```  
void SetImageToolTip(
    LPCTSTR lpszToolTip,  
    LPCTSTR lpszDescription=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *lpszToolTip*  
 Text popisu tlačítka.  
  
 [v] *lpszDescription*  
 Popis popisku.  
  
##  <a name="setmargin"></a>  CMFCCaptionBar::SetMargin  
 Nastaví vzdálenost mezi hrany panelu element caption a okraji ovládacího panelu titulek.  
  
```  
void SetMargin(int nMargin);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *nMargin*  
 Vzdálenost v pixelech, mezi okraj řádku elementů popisek a okraji ovládacího panelu titulek.  
  
##  <a name="settext"></a>  CMFCCaptionBar::SetText  
 Nastaví textový popisek pro panelu titulek.  
  
```  
void SetText(
    const CString& strText,  
    BarElementAlignment textAlignment=ALIGN_RIGHT);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *strText*  
 Textový řetězec, který chcete nastavit.  
  
 [v] *textAlignment*  
 Zarovnání textu.  
  
### <a name="remarks"></a>Poznámky  
 Textový popisek je zarovnán podle *textAlignment* parametr. Může být jeden z následujících `BarElementAlignment` hodnoty:  
  
-   ALIGN_INVALID  
  
-   ALIGN_LEFT  
  
-   ALIGN_RIGHT  
  
-   ALIGN_CENTER  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)
