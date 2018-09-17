---
title: Cmfccolordialog – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog::CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog::GetColor
- AFXCOLORDIALOG/CMFCColorDialog::GetPalette
- AFXCOLORDIALOG/CMFCColorDialog::RebuildPalette
- AFXCOLORDIALOG/CMFCColorDialog::SetCurrentColor
- AFXCOLORDIALOG/CMFCColorDialog::SetNewColor
- AFXCOLORDIALOG/CMFCColorDialog::SetPageOne
- AFXCOLORDIALOG/CMFCColorDialog::SetPageTwo
dev_langs:
- C++
helpviewer_keywords:
- CMFCColorDialog [MFC], CMFCColorDialog
- CMFCColorDialog [MFC], GetColor
- CMFCColorDialog [MFC], GetPalette
- CMFCColorDialog [MFC], RebuildPalette
- CMFCColorDialog [MFC], SetCurrentColor
- CMFCColorDialog [MFC], SetNewColor
- CMFCColorDialog [MFC], SetPageOne
- CMFCColorDialog [MFC], SetPageTwo
ms.assetid: 235bbbbc-a3b1-46e0-801b-fb55093ec579
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3cf85ec6de81ca18f32b8cd6bea015341f78287c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715355"
---
# <a name="cmfccolordialog-class"></a>Cmfccolordialog – třída
`CMFCColorDialog` Třída představuje dialogové okno Výběr barvy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCColorDialog : public CDialogEx  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCColorDialog::CMFCColorDialog](#cmfccolordialog)|Vytvoří `CMFCColorDialog` objektu.|  
|`CMFCColorDialog::~CMFCColorDialog`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCColorDialog::GetColor](#getcolor)|Vrátí aktuální vybraná barva.|  
|[CMFCColorDialog::GetPalette](#getpalette)|Vrátí hodnotu barvy palety.|  
|`CMFCColorDialog::PreTranslateMessage`|Přeloží okno zprávy před odesláním do [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) funkce Windows. Syntaxe a další informace najdete v tématu [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Přepíše `CDialogEx::PreTranslateMessage`.)|  
|[CMFCColorDialog::RebuildPalette](#rebuildpalette)|Z palety systému je odvozena barevnou paletu.|  
|[CMFCColorDialog::SetCurrentColor](#setcurrentcolor)|Nastaví aktuální vybraná barva.|  
|[CMFCColorDialog::SetNewColor](#setnewcolor)|Nastavuje barvu nejvíce odpovídá zadané hodnoty RGB.|  
|[CMFCColorDialog::SetPageOne](#setpageone)|Vybere hodnota RGB pro první stránku vlastností.|  
|[CMFCColorDialog::SetPageTwo](#setpagetwo)|Vybere hodnota RGB pro druhou stránku vlastností.|  
  
### <a name="protected-data-members"></a>Chránění členové dat  
  
|Název|Popis|  
|----------|-----------------|  
|`m_bIsMyPalette`|Hodnota TRUE, pokud dialogové okno Výběr barvy používá vlastní paletu barev, nebo hodnotu FALSE, pokud používá paletu, která je zadána v dialogovém okně `CMFCColorDialog` konstruktoru.|  
|`m_bPickerMode`|Hodnota TRUE, když uživatel je výběr barvy z dialogového okna Výběr; v opačném případě hodnota FALSE.|  
|`m_btnColorSelect`|Barva tlačítka, které uživatel vybral.|  
|`m_CurrentColor`|Aktuálně vybraná barva.|  
|`m_hcurPicker`|Kurzor, který se používá pro výběr barvy.|  
|`m_NewColor`|Potenciální vybranou barvu, která může trvale vybrána nebo vrátit zpět na původní barvy.|  
|`m_pColourSheetOne`|Ukazatel na první stránku vlastností seznamu vlastností pro výběr barvy.|  
|`m_pColourSheetTwo`|Ukazatel na druhé stránce vlastnost seznamu vlastností pro výběr barvy.|  
|`m_pPalette`|Aktuální logickou paletu.|  
|`m_pPropSheet`|Ukazatel na seznam vlastností pro dialogové okno Výběr barvy.|  
|`m_wndColors`|Objekt ovládacího prvku pro výběr barvy.|  
|`m_wndStaticPlaceHolder`|Statický ovládací prvek, který je zástupný symbol pro seznam vlastností pro výběr barvy.|  
  
## <a name="remarks"></a>Poznámky  
 Zobrazí se dialogové okno Výběr barvy jako seznam vlastností se dvěma stránkami. Na stránce první vyberte standardní barvu z palety systému; na druhé stránce můžete vybrat vlastní barvu.  
  
 Můžete vytvořit `CMFCColorDialog` objektu do zásobníku a následně zavolat `DoModal`, předá jako parametr do počáteční barvu `CMFCColorDialog` konstruktor. Dialogové okno Výběr barvy potom vytvoří několik [CMFCColorPickerCtrl – třída](../../mfc/reference/cmfccolorpickerctrl-class.md) objekty pro zpracování každé palety barev.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [Cdialogex –](../../mfc/reference/cdialogex-class.md)  
  
 [Cmfccolordialog –](../../mfc/reference/cmfccolordialog-class.md)  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nakonfigurovat pomocí různých metod v dialogovém okně barev `CMFCColorDialog` třídy. Příklad ukazuje, jak nastavit aktuální a nové barev dialogového okna a jak nastavit komponenty červené, zelené a modré vybraná barva na stránkách dvou vlastností barev dialogového okna. V tomto příkladu je součástí [nové ovládací prvky ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#3](../../mfc/reference/codesnippet/cpp/cmfccolordialog-class_1.cpp)]  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcolordialog.h  
  
##  <a name="cmfccolordialog"></a>  CMFCColorDialog::CMFCColorDialog  
 Vytvoří `CMFCColorDialog` objektu.  
  
```  
CMFCColorDialog(
    COLORREF clrInit=0,  
    DWORD dwFlags=0,  
    CWnd* pParentWnd=NULL,  
    HPALETTE hPal=NULL);
```  
  
### <a name="parameters"></a>Parametry  
*clrInit*<br/>
[in] Výchozí výběr barvy. Pokud není zadána žádná hodnota, výchozí hodnota je RGB(0,0,0) (černá).  
  
*dwFlags*<br/>
[in] Vyhrazená.
  
*pParentWnd*<br/>
[in] Ukazatel na okno nadřazené nebo vlastník dialogových oken.  
  
*hPal*<br/>
[in] Popisovač palety barev.  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getcolor"></a>  CMFCColorDialog::GetColor  
 Zjišťuje barvu, kterou uživatel vybere v dialogovém okně barev.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A [COLORREF](/windows/desktop/gdi/colorref) hodnotu, která obsahuje informace o RGB barva vybraná v dialogovém okně barev.  
  
### <a name="remarks"></a>Poznámky  
 Voláním této funkce po volání `DoModal` metody.  
  
##  <a name="getpalette"></a>  CMFCColorDialog::GetPalette  
 Načte paletu barev, která je k dispozici v aktuálním dialogovém okně barev.  
  
```  
CPalette* GetPalette() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `CPalette` objekt, který byl zadán v `CMFCColorDialog` konstruktoru.  
  
### <a name="remarks"></a>Poznámky  
 Palety barev určuje barvy, které uživatel může zvolit.  
  
##  <a name="rebuildpalette"></a>  CMFCColorDialog::RebuildPalette  
 Z palety systému je odvozena barevnou paletu.  
  
```  
void RebuildPalette();
```  
  
##  <a name="setcurrentcolor"></a>  CMFCColorDialog::SetCurrentColor  
 Nastaví aktuální barvu dialogového okna.  
  
```  
void SetCurrentColor(COLORREF rgb);
```  
  
### <a name="parameters"></a>Parametry  
*RGB*<br/>
[in] Hodnota barvy RGB  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setnewcolor"></a>  CMFCColorDialog::SetNewColor  
 Nastaví aktuální barvu na barvu, která se nejvíce podobá aktuální palety.  
  
```  
void SetNewColor(COLORREF rgb);
```  
  
### <a name="parameters"></a>Parametry  
*RGB*<br/>
[in] A [COLORREF](/windows/desktop/gdi/colorref) , který určuje barva RGB.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setpageone"></a>  CMFCColorDialog::SetPageOne  
 Explicitně určuje červené, zelené a modré složky vybraná barva na první stránce vlastností barev dialogového okna.  
  
```  
void SetPageOne(
    BYTE R,  
    BYTE G,  
    BYTE B);
```  
  
### <a name="parameters"></a>Parametry  
*R*<br/>
[in] Určuje hodnota červené hodnoty RGB.  
  
*G*<br/>
[in] Určuje hodnota zelené hodnoty RGB.  
  
*B*<br/>
[in] Určuje modrou složku hodnoty RGB.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setpagetwo"></a>  CMFCColorDialog::SetPageTwo  
 Explicitně určuje červené, zelené a modré složky vybraná barva na druhé stránce vlastností barev dialogového okna.  
  
```  
void SetPageTwo(
    BYTE R,  
    BYTE G,  
    BYTE B);
```  
  
### <a name="parameters"></a>Parametry  
*R*<br/>
[in] Určuje komponentu red hodnoty RGB  
  
*G*<br/>
[in] Určuje komponentu zelené hodnoty RGB  
  
*B*<br/>
[in] Určuje komponentu modré hodnoty RGB  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCColorPickerCtrl – třída](../../mfc/reference/cmfccolorpickerctrl-class.md)
