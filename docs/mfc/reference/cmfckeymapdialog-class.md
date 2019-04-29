---
title: CMFCKeyMapDialog Class
ms.date: 11/04/2016
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
ms.openlocfilehash: 65aa5ab0f24999ee23a97f383577b69584825502
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388498"
---
# <a name="cmfckeymapdialog-class"></a>CMFCKeyMapDialog Class

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
|[CMFCKeyMapDialog::FormatItem](#formatitem)|Volá se rozhraním sestavit řetězec, který popisuje mapování klíčů. Ve výchozím nastavení řetězec obsahuje název příkazu, klávesové zkratky používá a Popis klíče zástupce.|
|[CMFCKeyMapDialog::GetCommandKeys](#getcommandkeys)|Načte řetězec, který obsahuje seznam klávesových zkratek, které jsou přidružené k zadaný příkaz.|
|[CMFCKeyMapDialog::OnInsertItem](#oninsertitem)|Volá se rozhraním, než se nová položka je vložen do ovládacího prvku vnitřní seznam, který podporuje ovládací prvek mapování klávesnice.|
|[CMFCKeyMapDialog::OnPrintHeader](#onprintheader)|Volá se rozhraním pro tisk na novou stránku záhlaví pro mapování klávesnice.|
|[CMFCKeyMapDialog::OnPrintItem](#onprintitem)|Volá se rozhraním pro tisk položku mapování klávesnice.|
|[CMFCKeyMapDialog::OnSetColumns](#onsetcolumns)|Volá se rozhraním, chcete-li nastavit popisky sloupců v ovládacím prvku vnitřní seznam, který podporuje ovládací prvek mapování klávesnice.|
|[CMFCKeyMapDialog::PrintKeyMap](#printkeymap)|Volá se rozhraním, když uživatel klikne **tisk** tlačítko.|
|[CMFCKeyMapDialog::SetColumnsWidth](#setcolumnswidth)|Volá se rozhraním, aby nastavte šířku sloupců v ovládacím prvku vnitřní seznam, který podporuje ovládací prvek mapování klávesnice.|

## <a name="remarks"></a>Poznámky

Použití `CMFCKeyMapDialog` třídu pro implementaci dialogové okno mapování klávesnice umožňující změnu velikosti. Dialogové okno používá ovládací prvek zobrazení seznamu zobrazíte klávesové zkratky a jejich přidružené příkazy.

Použít `CMFCKeyMapDialog` třídy v aplikaci, předat ukazatel do okna hlavního rámce jako parametr `CMFCKeyMapDialog` konstruktoru. Zavolejte `DoModal` metoda spuštění modální dialogové okno.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCKeyMapDialog](../../mfc/reference/cmfckeymapdialog-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxkeymapdialog.h

##  <a name="cmfckeymapdialog"></a>  CMFCKeyMapDialog::CMFCKeyMapDialog

Vytvoří `CMFCKeyMapDialog` objektu.

```
CMFCKeyMapDialog(
    CFrameWnd* pWndParentFrame,
    BOOL bEnablePrint=FALSE);
```

### <a name="parameters"></a>Parametry

*pWndParentFrame*<br/>
[in] Ukazatel do nadřazeného okna `CMFCKeyMapDialog` objektu.

*bEnablePrint*<br/>
[in] Hodnota TRUE, pokud lze vytisknout seznam klávesové zkratky; v opačném případě hodnota FALSE. Výchozí hodnota je FALSE.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCKeyMapDialog` třídy. V tomto příkladu je součástí [Visual Studio demonstrační ukázka](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#21](../../mfc/codesnippet/cpp/cmfckeymapdialog-class_1.cpp)]

##  <a name="domodal"></a>  CMFCKeyMapDialog::DoModal

Zobrazí dialogové okno mapování klávesnice.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

Celé číslo se znaménkem, jako je například IDOK nebo IDCANCEL, který je předán [CDialog::EndDialog](../../mfc/reference/cdialog-class.md#enddialog) metody. Metoda, pak zavřete dialogové okno. Další informace najdete v tématu [CDialog::DoModal](../../mfc/reference/cdialog-class.md#domodal).

### <a name="remarks"></a>Poznámky

Dialogové okno mapování klávesnice umožňuje vybrat a přiřadit různé kategorie příkazy kláves akcelerátoru. Kromě toho můžete zkopírovat vybrané přístupové klávesy a jejich popis do schránky.

##  <a name="formatitem"></a>  CMFCKeyMapDialog::FormatItem

Volá se rozhraním sestavit řetězec, který popisuje mapování klíčů. Ve výchozím nastavení řetězec obsahuje název příkazu, klávesové zkratky používá a Popis klíče zástupce.

```
virtual CString FormatItem(int nItem) const;
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
[in] Index založený na nule položka ve vnitřním seznamu mapování klíčů.

### <a name="return-value"></a>Návratová hodnota

A `CString` objekt, který obsahuje text formátovaný položky.

### <a name="remarks"></a>Poznámky

##  <a name="getcommandkeys"></a>  CMFCKeyMapDialog::GetCommandKeys

Načte hodnotu řetězce. Řetězec obsahuje seznam klávesových zkratek, které jsou spojeny s zadaný příkaz.

```
virtual CString GetCommandKeys(UINT uiCmdID) const;
```

### <a name="parameters"></a>Parametry

*uiCmdID*<br/>
[in] ID příkazu.

### <a name="return-value"></a>Návratová hodnota

Oddělený středníkem (;) seznam klávesových zkratek, které souvisí s zadaný příkaz.

### <a name="remarks"></a>Poznámky

##  <a name="oninsertitem"></a>  CMFCKeyMapDialog::OnInsertItem

Volá se rozhraním, než se nová položka je vložen do ovládacího prvku vnitřní seznam, který podporuje ovládací prvek mapování klávesnice.

```
virtual void OnInsertItem(
    CMFCToolBarButton* pButton,
    int nItem);
```

### <a name="parameters"></a>Parametry

*pButton*<br/>
[in] Ukazatel, který se používá k mapování kombinaci kláves klávesnice k příkazu název a popis tlačítka panelu nástrojů. Položka mapování klíčů je uložena v ovládacím prvku vnitřní seznam.

*nItem*<br/>
[in] Index založený na nule, který určuje, kam chcete vložit novou položku mapování klíčů v ovládacím prvku vnitřní seznam.

### <a name="remarks"></a>Poznámky

##  <a name="onprintheader"></a>  CMFCKeyMapDialog::OnPrintHeader

Volá se rozhraním pro tisk na novou stránku záhlaví pro mapování klávesnice.

```
virtual int OnPrintHeader(
    CDC& dc,
    int nPage,
    int cx) const;
```

### <a name="parameters"></a>Parametry

*dc*<br/>
[in] Kontext zařízení pro tiskárny.

*nPage*<br/>
[in] Číslo stránky k tisku.

*cx*<br/>
[in] Vodorovný posun záhlaví v pixelech.

### <a name="return-value"></a>Návratová hodnota

V případě úspěšného ověření výšku tištěných textu. Další informace najdete v části vrátit hodnotu z [CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext).

### <a name="remarks"></a>Poznámky

Rozhraní používá tuto metodu pro tisk mapování klávesnice. Ve výchozím nastavení tato metoda vytiskne číslo stránky, název aplikace a název pole dialogového okna.

##  <a name="onprintitem"></a>  CMFCKeyMapDialog::OnPrintItem

Volá se rozhraním pro tisk položku mapování klávesnice.

```
virtual int OnPrintItem(
    CDC& dc,
    int nItem,
    int y,
    int cx,
    BOOL bCalcHeight) const;
```

### <a name="parameters"></a>Parametry

*dc*<br/>
[in] Kontext zařízení tiskárny.

*nItem*<br/>
[in] Index založený na nule položky k vytištění.

*y*<br/>
[in] Svislý posun mezi horní části stránky a pozici položky.

*cx*<br/>
[in] Vodorovný posun mezi levé části stránky a pozici položky.

*bCalcHeight*<br/>
[in] TRUE, pokud chcete vypočítat nejlepší výška tisku položky; Došlo ke zkrácení tisku položky tak, aby místo výchozí hodnotu FALSE.

### <a name="return-value"></a>Návratová hodnota

Výšku tištěných položky.

### <a name="remarks"></a>Poznámky

Rozhraní volá tuto metodu pro tisk položky dialogového okna mapování klíčů. Ve výchozím nastavení tato metoda vytiskne název příkazu, klávesové zkratky a příkaz popis položky.

##  <a name="onsetcolumns"></a>  CMFCKeyMapDialog::OnSetColumns

Volá se rozhraním, chcete-li nastavit popisky sloupců v ovládacím prvku vnitřní seznam, který podporuje ovládací prvek mapování klávesnice.

```
virtual void OnSetColumns();
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato metoda získává popisky sloupců z tři zdroje. Titulek příkazový sloupec je z IDS_AFXBARRES_COMMAND titulek klíčový sloupec je z IDS_AFXBARRES_KEYS a titulek popis sloupce je z IDS_AFXBARRES_DESCRIPTION.

##  <a name="printkeymap"></a>  CMFCKeyMapDialog::PrintKeyMap

Volá se rozhraním, když uživatel klikne **tisk** tlačítko.

```
virtual void PrintKeyMap();
```

### <a name="remarks"></a>Poznámky

`PrintKeyMap` Metoda vytiskne mapování klíčů. Inicializuje nové tiskové úlohy a pak zavolá opakovaně [CMFCKeyMapDialog::OnPrintHeader](#onprintheader) a [CMFCKeyMapDialog::OnPrintItem](#onprintitem) metody, dokud jsou zobrazeny všechny mapování klíčů.

##  <a name="setcolumnswidth"></a>  CMFCKeyMapDialog::SetColumnsWidth

Volá se rozhraním, aby nastavte šířku sloupců v ovládacím prvku vnitřní seznam, který podporuje ovládací prvek mapování klávesnice.

```
virtual void SetColumnsWidth();
```

### <a name="remarks"></a>Poznámky

Tato metoda nastaví vnitřní seznam sloupců ovládacího prvku na výchozí šířky. Nejprve se vypočítá šířku sloupce klíče zástupce. Pak jednu třetinu zbývající šířky je přidělená k příkazový sloupec a zbývající dvě třetiny je přidělená k sloupci Popis.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CKeyboardManager – třída](../../mfc/reference/ckeyboardmanager-class.md)
