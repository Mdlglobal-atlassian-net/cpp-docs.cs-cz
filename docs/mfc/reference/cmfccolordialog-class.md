---
title: "Třída CMFCColorDialog | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
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
caps.latest.revision: "30"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0f607d6145d08617151a64845bc23a58f2849dbf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cmfccolordialog-class"></a>CMFCColorDialog – třída
`CMFCColorDialog` Třída reprezentuje dialogové okno Výběr barev.  
  
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
|[CMFCColorDialog::GetColor](#getcolor)|Vrátí aktuální vybrané barvy.|  
|[CMFCColorDialog::GetPalette](#getpalette)|Vrátí barvy palety.|  
|`CMFCColorDialog::PreTranslateMessage`|Přeloží zprávy oken, než jsou odeslány do [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) a [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funkce systému Windows. Syntaxe a další informace najdete v tématu [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Přepisuje `CDialogEx::PreTranslateMessage`.)|  
|[CMFCColorDialog::RebuildPalette](#rebuildpalette)|Paleta odvozená z palety systému.|  
|[CMFCColorDialog::SetCurrentColor](#setcurrentcolor)|Nastaví aktuální vybrané barvy.|  
|[CMFCColorDialog::SetNewColor](#setnewcolor)|Nastaví barvu nejvíc odpovídá zadané hodnoty RGB.|  
|[CMFCColorDialog::SetPageOne](#setpageone)|Vybere hodnotu RGB pro první stránku vlastností.|  
|[CMFCColorDialog::SetPageTwo](#setpagetwo)|Vybere hodnotu RGB pro druhou stránku vlastností.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|`m_bIsMyPalette`|`TRUE`Pokud dialogové okno pro výběr barev používá svou vlastní paletu barev nebo `FALSE` Pokud dialogové okno používá paletu, která je zadána v `CMFCColorDialog` konstruktor.|  
|`m_bPickerMode`|`TRUE`Když uživatel je výběr barvy z dialogového okna Výběr; v opačném `FALSE`.|  
|`m_btnColorSelect`|Tlačítko barev, které uživatel vybral.|  
|`m_CurrentColor`|Aktuálně vybrané barvy.|  
|`m_hcurPicker`|Kurzor, který se používá k vybrat barvu.|  
|`m_NewColor`|Potenciální vybrané barvy, která může trvale vybrána nebo vrátit zpět na původní barvy.|  
|`m_pColourSheetOne`|Ukazatel na první stránku vlastnosti seznamu vlastností pro výběr barev.|  
|`m_pColourSheetTwo`|Ukazatel na druhé stránce vlastnost seznamu vlastností pro výběr barev.|  
|`m_pPalette`|Aktuální logické palety.|  
|`m_pPropSheet`|Ukazatel na seznamu vlastností pro dialogové okno pro výběr barev.|  
|`m_wndColors`|Objekt ovládacího prvku pro výběr barev.|  
|`m_wndStaticPlaceHolder`|Statické ovládací prvek, který je zástupný symbol pro seznam vlastností pro výběr barev.|  
  
## <a name="remarks"></a>Poznámky  
 Dialogové okno pro výběr barev se zobrazí jako seznam vlastností se dvěma stránkami. Na první stránce vyberte standardní barvu z palety systému; na druhé stránce vyberte vlastních barev.  
  
 Můžete vytvořit `CMFCColorDialog` objektu v zásobníku a pak zavolají `DoModal`, předávání počáteční barvu jako parametr, který se `CMFCColorDialog` konstruktor. Dialogové okno pro výběr barev poté vytvoří několik [CMFCColorPickerCtrl třída](../../mfc/reference/cmfccolorpickerctrl-class.md) objekty pro zpracování každé paletu barev.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
 [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nakonfigurovat pomocí různých metod v dialogové okno barvy `CMFCColorDialog` třídy. Příklad ukazuje, jak nastavit aktuální a nové barvy dialogového okna a jak nastavit červené, zelené a modré součástí vybrané barvy na stránkách dvou vlastností barev dialogového okna. Tato ukázka je součástí [nové ovládací prvky ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#3](../../mfc/reference/codesnippet/cpp/cmfccolordialog-class_1.cpp)]  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcolordialog.h  
  
##  <a name="cmfccolordialog"></a>CMFCColorDialog::CMFCColorDialog  
 Vytvoří `CMFCColorDialog` objektu.  
  
```  
CMFCColorDialog(
    COLORREF clrInit=0,  
    DWORD dwFlags=0,  
    CWnd* pParentWnd=NULL,  
    HPALETTE hPal=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`clrInit`  
 Výchozí výběr barev. Pokud není zadaná žádná hodnota, výchozí hodnota je RGB(0,0,0) (černé).  
  
 [v]`dwFlags`  
 (Vyhrazené).  
  
 [v]`pParentWnd`  
 Ukazatele v dialogovém okně nadřazené nebo vlastníka.  
  
 [v]`hPal`  
 Popisovač pro palety barev.  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getcolor"></a>CMFCColorDialog::GetColor  
 Načte barvu, která si uživatel vybere ze dialogové okno barvy.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) hodnotu, která obsahuje informace o RGB barvy vybraných v dialogovém okně barvy.  
  
### <a name="remarks"></a>Poznámky  
 Po zavolání metody volání této funkce `DoModal` metoda.  
  
##  <a name="getpalette"></a>CMFCColorDialog::GetPalette  
 Načte paletu barev, která je k dispozici v dialogovém okně aktuální barev.  
  
```  
CPalette* GetPalette() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `CPalette` objektu, která byla zadaná v `CMFCColorDialog` konstruktor.  
  
### <a name="remarks"></a>Poznámky  
 Určuje barevnou paletu barev, které uživatel může vybrat.  
  
##  <a name="rebuildpalette"></a>CMFCColorDialog::RebuildPalette  
 Paleta odvozená z palety systému.  
  
```  
void RebuildPalette();
```  
  
##  <a name="setcurrentcolor"></a>CMFCColorDialog::SetCurrentColor  
 Nastaví barvu aktuální dialogového okna.  
  
```  
void SetCurrentColor(COLORREF rgb);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`rgb`  
 Hodnotu barva RGB  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setnewcolor"></a>CMFCColorDialog::SetNewColor  
 Nastaví barvu aktuální barvu v aktuální paletu, která se nejvíce podobá.  
  
```  
void SetNewColor(COLORREF rgb);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`rgb`  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) určující barva RGB.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setpageone"></a>CMFCColorDialog::SetPageOne  
 Určuje explicitně červené, zelené a modré součástí vybrané barvy na první stránce vlastnost dialogového okna barvy.  
  
```  
void SetPageOne(
    BYTE R,  
    BYTE G,  
    BYTE B);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`R`  
 Určuje komponentu red hodnoty RGB.  
  
 [v]`G`  
 Určuje komponentu zelená hodnoty RGB.  
  
 [v]`B`  
 Určuje komponentu blue hodnoty RGB.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setpagetwo"></a>CMFCColorDialog::SetPageTwo  
 Na druhé stránce vlastnost dialogového okna barvy explicitně určuje červené, zelené a modré součástí vybrané barvy.  
  
```  
void SetPageTwo(
    BYTE R,  
    BYTE G,  
    BYTE B);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`R`  
 Určuje komponentu red hodnoty RGB  
  
 [v]`G`  
 Určuje komponentu zelená hodnoty RGB  
  
 [v]`B`  
 Určuje komponentu blue hodnoty RGB  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCColorPickerCtrl – třída](../../mfc/reference/cmfccolorpickerctrl-class.md)
