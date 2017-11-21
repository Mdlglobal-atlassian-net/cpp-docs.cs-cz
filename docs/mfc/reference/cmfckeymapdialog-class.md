---
title: "Třída CMFCKeyMapDialog | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::DoModal
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::FormatItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::GetCommandKeys
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnInsertItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnPrintHeader
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnPrintItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnSetColumns
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::PrintKeyMap
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::SetColumnsWidth
dev_langs: C++
helpviewer_keywords:
- CMFCKeyMapDialog [MFC], CMFCKeyMapDialog
- CMFCKeyMapDialog [MFC], DoModal
- CMFCKeyMapDialog [MFC], FormatItem
- CMFCKeyMapDialog [MFC], GetCommandKeys
- CMFCKeyMapDialog [MFC], OnInsertItem
- CMFCKeyMapDialog [MFC], OnPrintHeader
- CMFCKeyMapDialog [MFC], OnPrintItem
- CMFCKeyMapDialog [MFC], OnSetColumns
- CMFCKeyMapDialog [MFC], PrintKeyMap
- CMFCKeyMapDialog [MFC], SetColumnsWidth
ms.assetid: 5feb4942-d636-462d-a162-0104dd320f4e
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 27278d64ab1aef17149a3b4c166cff9c302e29ca
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cmfckeymapdialog-class"></a>CMFCKeyMapDialog – třída
`CMFCKeyMapDialog` Třída podporuje ovládací prvek, který mapuje příkazy kláves na klávesnici.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCKeyMapDialog : public CDialogEx  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCKeyMapDialog::CMFCKeyMapDialog](#cmfckeymapdialog)|Vytvoří `CMFCKeyMapDialog` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCKeyMapDialog::DoModal](#domodal)|Zobrazí dialogové okno mapování klávesnice.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCKeyMapDialog::FormatItem](#formatitem)|Voláno rámcem vytvořit řetězec, který popisuje klíčové mapování. Ve výchozím nastavení řetězec obsahuje název příkazu, klávesové zkratky používá a Popis klíče zástupce.|  
|[CMFCKeyMapDialog::GetCommandKeys](#getcommandkeys)|Načte řetězec, který obsahuje seznam klávesové zkratky, které jsou přidružené k zadaný příkaz.|  
|[CMFCKeyMapDialog::OnInsertItem](#oninsertitem)|Voláno rámcem, než je vložit novou položku do interní seznamu ovládací prvek, který podporuje ovládací prvek mapování klávesnice.|  
|[CMFCKeyMapDialog::OnPrintHeader](#onprintheader)|Voláno rámcem tisknout hlavičku pro mapu klávesnice na novou stránku.|  
|[CMFCKeyMapDialog::OnPrintItem](#onprintitem)|Voláno rámcem tisknout položku mapování klávesnice.|  
|[CMFCKeyMapDialog::OnSetColumns](#onsetcolumns)|Voláno rámcem nastavit titulky pro sloupce v ovládacím prvku vnitřní seznam, který podporuje ovládací prvek mapování klávesnice.|  
|[CMFCKeyMapDialog::PrintKeyMap](#printkeymap)|Voláno rámcem, když uživatel klikne **tiskových** tlačítko.|  
|[CMFCKeyMapDialog::SetColumnsWidth](#setcolumnswidth)|Voláno rámcem nastavit šířku sloupců v ovládacím prvku vnitřní seznam, který podporuje ovládací prvek mapování klávesnice.|  
  
## <a name="remarks"></a>Poznámky  
 Použití `CMFCKeyMapDialog` třídu pro implementaci dialogové okno mapování klávesnice s možností změny velikosti. Dialogové okno používá ovládacího prvku zobrazení seznamu zobrazíte klávesové zkratky a jejich přidružené příkazy.  
  
 Použít `CMFCKeyMapDialog` třídy v aplikaci, předat ukazatel hlavního okna rámce jako parametr, který se `CMFCKeyMapDialog` konstruktor. Potom zavolejte `DoModal` metoda zahájíte modální dialogové okno.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
 [CMFCKeyMapDialog](../../mfc/reference/cmfckeymapdialog-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxkeymapdialog.h  
  
##  <a name="cmfckeymapdialog"></a>CMFCKeyMapDialog::CMFCKeyMapDialog  
 Vytvoří `CMFCKeyMapDialog` objektu.  
  
```  
CMFCKeyMapDialog(
    CFrameWnd* pWndParentFrame,  
    BOOL bEnablePrint=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pWndParentFrame`  
 Ukazatel na okno nadřazené `CMFCKeyMapDialog` objektu.  
  
 [v]`bEnablePrint`  
 `TRUE`Pokud je seznam klávesy akcelerátoru můžete vytisknout; v opačném `FALSE`. Výchozí hodnota je `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit objekt `CMFCKeyMapDialog` třídy. Tato ukázka je součástí [Visual Studio Demo-ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#21](../../mfc/codesnippet/cpp/cmfckeymapdialog-class_1.cpp)]  
  
##  <a name="domodal"></a>CMFCKeyMapDialog::DoModal  
 Zobrazí dialogové okno mapování klávesnice.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Podepsaná hodnota typu integer, například `IDOK` nebo `IDCANCEL`, která je předán [CDialog::EndDialog](../../mfc/reference/cdialog-class.md#enddialog) metoda. V případě metody zase zavře dialogové okno. Další informace najdete v tématu [CDialog::DoModal](../../mfc/reference/cdialog-class.md#domodal).  
  
### <a name="remarks"></a>Poznámky  
 Dialogové okno mapování klávesnice umožňuje vybrat a přiřadit různé kategorie příkazy klávesy akcelerátoru. Kromě toho můžete zkopírovat vybrané přístupové klávesy a jejich popis do schránky.  
  
##  <a name="formatitem"></a>CMFCKeyMapDialog::FormatItem  
 Voláno rámcem vytvořit řetězec, který popisuje klíčové mapování. Ve výchozím nastavení řetězec obsahuje název příkazu, klávesové zkratky používá a Popis klíče zástupce.  
  
```  
virtual CString FormatItem(int nItem) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nItem`  
 Index založený na nule položky v seznamu interní klíče mapování.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CString` objekt, který obsahuje text formátovaný položky.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getcommandkeys"></a>CMFCKeyMapDialog::GetCommandKeys  
 Načte hodnotu řetězce. Řetězec obsahuje seznam klávesové zkratky, které jsou přidruženy zadaný příkaz.  
  
```  
virtual CString GetCommandKeys(UINT uiCmdID) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiCmdID`  
 ID příkazu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Oddělený středníkem (;) seznamu klávesových zkratek, který je přidružen zadaný příkaz.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="oninsertitem"></a>CMFCKeyMapDialog::OnInsertItem  
 Voláno rámcem, než je vložit novou položku do prvku vnitřní seznam, který podporuje ovládací prvek mapování klávesnice.  
  
```  
virtual void OnInsertItem(
    CMFCToolBarButton* pButton,  
    int nItem);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pButton`  
 Ukazatel na tlačítka panelu nástrojů, který se používá k mapování kombinaci kláves klávesnice na příkaz název a popis. Položka klíče mapy je uložena v ovládacím prvku vnitřní seznam.  
  
 [v]`nItem`  
 Index počítaný od nuly, který určuje, kam chcete vložit novou položku klíče mapy v ovládacím prvku vnitřní seznam.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onprintheader"></a>CMFCKeyMapDialog::OnPrintHeader  
 Voláno rámcem tisknout hlavičku pro mapu klávesnice na novou stránku.  
  
```  
virtual int OnPrintHeader(
    CDC& dc,  
    int nPage,  
    int cx) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v]`dc`  
 Kontext zařízení pro tiskárny.  
  
 [v]`nPage`  
 Číslo stránky k vytištění.  
  
 [v]`cx`  
 Vodorovný posun záhlaví má v pixelech.  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě úspěšného výšku tištěných textu. Další informace najdete v části vrátit hodnotu z [CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext).  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní používá tato metoda tisknout mapy klávesnice. Ve výchozím nastavení vytiskne tato metoda číslo stránky, název aplikace a dialogové okno název.  
  
##  <a name="onprintitem"></a>CMFCKeyMapDialog::OnPrintItem  
 Voláno rámcem tisknout položku mapování klávesnice.  
  
```  
virtual int OnPrintItem(
    CDC& dc,  
    int nItem,  
    int y,  
    int cx,  
    BOOL bCalcHeight) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v]`dc`  
 Kontext zařízení tiskárny.  
  
 [v]`nItem`  
 Index založený na nule položky k vytištění.  
  
 [v]`y`  
 Svislý posun od pozice položky horní části stránky.  
  
 [v]`cx`  
 Vodorovný posun mezi levé části stránky a umístění položky.  
  
 [v]`bCalcHeight`  
 `TRUE`Chcete-li vypočítat nejlepší výšku pro položku tiskové; `FALSE` zkrátit tiskové položky tak, aby odpovídal výchozí místo.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výška tištěných položky.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework volá tuto metodu za účelem tisku položky dialogového okna klíče mapy. Ve výchozím nastavení vytiskne tato metoda název příkazu, klávesové zkratky a příkaz popis položky.  
  
##  <a name="onsetcolumns"></a>CMFCKeyMapDialog::OnSetColumns  
 Voláno rámcem nastavit titulky pro sloupce v ovládacím prvku vnitřní seznam, který podporuje ovládací prvek mapování klávesnice.  
  
```  
virtual void OnSetColumns();
```  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení tato metoda získá titulky pro sloupce z tři zdroje. Popisek sloupce příkaz je z IDS_AFXBARRES_COMMAND, titulek klíčový sloupec je z IDS_AFXBARRES_KEYS a titulek popis sloupce je z IDS_AFXBARRES_DESCRIPTION.  
  
##  <a name="printkeymap"></a>CMFCKeyMapDialog::PrintKeyMap  
 Voláno rámcem, když uživatel klikne **tiskových** tlačítko.  
  
```  
virtual void PrintKeyMap();
```  
  
### <a name="remarks"></a>Poznámky  
 `PrintKeyMap` Metoda vytiskne klíče mapy. Inicializuje nové tiskové úlohy a pak opakovaně zavolá [CMFCKeyMapDialog::OnPrintHeader](#onprintheader) a [CMFCKeyMapDialog::OnPrintItem](#onprintitem) metody, dokud se všechny klíče mapování jsou vytisknout.  
  
##  <a name="setcolumnswidth"></a>CMFCKeyMapDialog::SetColumnsWidth  
 Voláno rámcem nastavit šířku sloupců v ovládacím prvku vnitřní seznam, který podporuje ovládací prvek mapování klávesnice.  
  
```  
virtual void SetColumnsWidth();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda nastaví vnitřní seznam sloupců ovládacího prvku na výchozí šířky. Nejprve se počítá šířku sloupce klíče zástupce. Pak jednu třetinu zbývající šířky je přidělená k sloupci příkazu a zbývající dvoutřetinovou je přidělená k sloupci Popis.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CKeyboardManager – třída](../../mfc/reference/ckeyboardmanager-class.md)
