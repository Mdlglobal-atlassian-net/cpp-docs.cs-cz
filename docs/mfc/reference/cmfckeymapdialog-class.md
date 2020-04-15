---
title: Třída CMFCKeyMapDialog
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
ms.openlocfilehash: 22aa006ce214ca720192bb761e2ff2b35a64fce3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374405"
---
# <a name="cmfckeymapdialog-class"></a>Třída CMFCKeyMapDialog

Třída `CMFCKeyMapDialog` podporuje ovládací prvek, který mapuje příkazy na klávesy na klávesnici.

## <a name="syntax"></a>Syntaxe

```
class CMFCKeyMapDialog : public CDialogEx
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCKeyMapDialog::CMFCKeyMapDialog](#cmfckeymapdialog)|Vytvoří `CMFCKeyMapDialog` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCKeyMapDialog::DoModální](#domodal)|Zobrazí dialogové okno mapování klávesnice.|

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCKeyMapDialog::FormatItem](#formatitem)|Volat rámci k vytvoření řetězce, který popisuje mapování klíčů. Ve výchozím nastavení řetězec obsahuje název příkazu, použité klávesové zkratky a popis klávesové zkratky.|
|[CMFCKeyMapDialog::GetCommandKeys](#getcommandkeys)|Načte řetězec, který obsahuje seznam klávesových zkratek přidružených k zadanému příkazu.|
|[CMFCKeyMapDialog::Položka OnInsertItem](#oninsertitem)|Volat rámci před vložením nové položky do ovládacího prvku vnitřní seznam, který podporuje ovládací prvek mapování klávesnice.|
|[CMFCKeyMapDialog::OnPrintHeader](#onprintheader)|Volat rámci vytisknout záhlaví pro mapu klávesnice na nové stránce.|
|[CMFCKeyMapDialog::OnPrintItem](#onprintitem)|Volat rámci vytisknout položku mapování klávesnice.|
|[CMFCKeyMapDialog::onsetcolumns](#onsetcolumns)|Volat rámci nastavit titulky pro sloupce v ovládacím prvku vnitřní seznam, který podporuje ovládací prvek mapování klávesnice.|
|[CMFCKeyMapDialog::PrintKeyMap](#printkeymap)|Volat rámci, když uživatel klepne na tlačítko **Tisk.**|
|[CMFCKeyMapDialog::SetColumnsWidth](#setcolumnswidth)|Volat rámci nastavit šířku sloupců v ovládacím prvku vnitřní seznam, který podporuje ovládací prvek mapování klávesnice.|

## <a name="remarks"></a>Poznámky

Pomocí `CMFCKeyMapDialog` třídy implementujte dialogové okno mapování klávesnice s nastavitelnou velikostí. Dialogové okno používá ovládací prvek zobrazení seznamu k zobrazení klávesových zkratek a jejich přidružených příkazů.

Chcete-li `CMFCKeyMapDialog` použít třídu v aplikaci, předaďte ukazatel do `CMFCKeyMapDialog` okna hlavního rámce jako parametr konstruktoru. Potom volání `DoModal` metody spustit modální dialogové okno.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCKeyMapDialog](../../mfc/reference/cmfckeymapdialog-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxkeymapdialog.h

## <a name="cmfckeymapdialogcmfckeymapdialog"></a><a name="cmfckeymapdialog"></a>CMFCKeyMapDialog::CMFCKeyMapDialog

Vytvoří `CMFCKeyMapDialog` objekt.

```
CMFCKeyMapDialog(
    CFrameWnd* pWndParentFrame,
    BOOL bEnablePrint=FALSE);
```

### <a name="parameters"></a>Parametry

*pWndParentFrame*<br/>
[v] Ukazatel na nadřazené okno objektu. `CMFCKeyMapDialog`

*povolittisk*<br/>
[v] TRUE, pokud lze vytisknout seznam kláves akcelerátoru; jinak NEPRAVDA. Výchozí hodnota je FALSE.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCKeyMapDialog` třídy. Tento příklad je součástí [ukázky visual studia](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#21](../../mfc/codesnippet/cpp/cmfckeymapdialog-class_1.cpp)]

## <a name="cmfckeymapdialogdomodal"></a><a name="domodal"></a>CMFCKeyMapDialog::DoModální

Zobrazí dialogové okno mapování klávesnice.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

Celé číslo podepsané, například IDOK nebo IDCANCEL, které je předáno metodě [CDialog::EndDialog.](../../mfc/reference/cdialog-class.md#enddialog) Metoda zase zavře dialogové okno. Další informace naleznete v [tématu CDialog::DoModal](../../mfc/reference/cdialog-class.md#domodal).

### <a name="remarks"></a>Poznámky

Dialogové okno mapování klávesnice umožňuje vybrat a přiřadit klávesy akcelerátoru různým kategoriím příkazů. Kromě toho můžete zkopírovat vybrané klávesy akcelerátoru a jejich popis do schránky.

## <a name="cmfckeymapdialogformatitem"></a><a name="formatitem"></a>CMFCKeyMapDialog::FormatItem

Volat rámci k vytvoření řetězce, který popisuje mapování klíčů. Ve výchozím nastavení řetězec obsahuje název příkazu, použité klávesové zkratky a popis klávesové zkratky.

```
virtual CString FormatItem(int nItem) const;
```

### <a name="parameters"></a>Parametry

*nPoložka*<br/>
[v] Nulový index položky v interním seznamu mapování klíčů.

### <a name="return-value"></a>Návratová hodnota

Objekt, `CString` který obsahuje formátovaný text položky.

### <a name="remarks"></a>Poznámky

## <a name="cmfckeymapdialoggetcommandkeys"></a><a name="getcommandkeys"></a>CMFCKeyMapDialog::GetCommandKeys

Načte hodnotu řetězce. Řetězec obsahuje seznam klávesových zkratek, které jsou přidruženy k zadanému příkazu.

```
virtual CString GetCommandKeys(UINT uiCmdID) const;
```

### <a name="parameters"></a>Parametry

*uiCmdID*<br/>
[v] ID příkazu.

### <a name="return-value"></a>Návratová hodnota

Seznam klávesových zkratek oddělených středníkem (';') je přidružen k zadanému příkazu.

### <a name="remarks"></a>Poznámky

## <a name="cmfckeymapdialogoninsertitem"></a><a name="oninsertitem"></a>CMFCKeyMapDialog::Položka OnInsertItem

Volat rámci před vložením nové položky do ovládacího prvku vnitřní seznam, který podporuje ovládací prvek mapování klávesnice.

```
virtual void OnInsertItem(
    CMFCToolBarButton* pButton,
    int nItem);
```

### <a name="parameters"></a>Parametry

*pTlačítko*<br/>
[v] Ukazatel na tlačítko panelu nástrojů, které slouží k mapování kombinace kláves klávesnice na název příkazu a popis. Položka mapy klíče je uložena v ovládacím prvku vnitřního seznamu.

*nPoložka*<br/>
[v] Index založený na nule, který určuje, kam vložit novou položku mapy klíčů do ovládacího prvku vnitřního seznamu.

### <a name="remarks"></a>Poznámky

## <a name="cmfckeymapdialogonprintheader"></a><a name="onprintheader"></a>CMFCKeyMapDialog::OnPrintHeader

Volat rámci vytisknout záhlaví pro mapu klávesnice na nové stránce.

```
virtual int OnPrintHeader(
    CDC& dc,
    int nPage,
    int cx) const;
```

### <a name="parameters"></a>Parametry

*Dc*<br/>
[v] Kontext zařízení pro tiskárnu.

*nStránka*<br/>
[v] Číslo stránky, které chcete vytisknout.

*Cx*<br/>
[v] Vodorovné odsazení záhlaví v obrazových bodech.

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu výška tištěného textu. Další informace naleznete v části Vrácená hodnota [cdc::DrawText](../../mfc/reference/cdc-class.md#drawtext).

### <a name="remarks"></a>Poznámky

Rozhraní Framework používá tuto metodu k tisku mapy klávesnice. Ve výchozím nastavení tato metoda vytiskne číslo stránky, název aplikace a název dialogového okna.

## <a name="cmfckeymapdialogonprintitem"></a><a name="onprintitem"></a>CMFCKeyMapDialog::OnPrintItem

Volat rámci vytisknout položku mapování klávesnice.

```
virtual int OnPrintItem(
    CDC& dc,
    int nItem,
    int y,
    int cx,
    BOOL bCalcHeight) const;
```

### <a name="parameters"></a>Parametry

*Dc*<br/>
[v] Kontext zařízení tiskárny.

*nPoložka*<br/>
[v] Index na základě nuly položky k tisku.

*Y*<br/>
[v] Svislé odsazení mezi horní části stránky a umístění položky.

*Cx*<br/>
[v] Vodorovné odsazení mezi levým levým bodem stránky a umístěním položky.

*bCalcHeight*<br/>
[v] TRUE pro výpočet nejlepší výšky pro tiskovou položku; NEPRAVDA zkrátit položku tisku tak, aby odpovídala výchozí mezery.

### <a name="return-value"></a>Návratová hodnota

Výška tištěné položky.

### <a name="remarks"></a>Poznámky

Framework volá tuto metodu k tisku položky dialogového okna mapy klíčů. Ve výchozím nastavení tato metoda vytiskne název příkazu položky, klávesové zkratky a popis příkazu.

## <a name="cmfckeymapdialogonsetcolumns"></a><a name="onsetcolumns"></a>CMFCKeyMapDialog::onsetcolumns

Volat rámci nastavit titulky pro sloupce v ovládacím prvku vnitřní seznam, který podporuje ovládací prvek mapování klávesnice.

```
virtual void OnSetColumns();
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato metoda získá titulky pro sloupce ze tří prostředků. Titulek příkazového sloupce je z IDS_AFXBARRES_COMMAND, titulek klíčového sloupce je z IDS_AFXBARRES_KEYS a popisek sloupce popisek je od IDS_AFXBARRES_DESCRIPTION.

## <a name="cmfckeymapdialogprintkeymap"></a><a name="printkeymap"></a>CMFCKeyMapDialog::PrintKeyMap

Volat rámci, když uživatel klepne na tlačítko **Tisk.**

```
virtual void PrintKeyMap();
```

### <a name="remarks"></a>Poznámky

Metoda `PrintKeyMap` vytiskne mapu klíčů. Zahájí novou tiskovou úlohu a poté opakovaně zavolá metody [CMFCKeyMapDialog::OnPrintHeader](#onprintheader) a [CMFCKeyMapDialog::OnPrintItem,](#onprintitem) dokud nebudou vytištěna všechna mapování klíčů.

## <a name="cmfckeymapdialogsetcolumnswidth"></a><a name="setcolumnswidth"></a>CMFCKeyMapDialog::SetColumnsWidth

Volat rámci nastavit šířku sloupců v ovládacím prvku vnitřní seznam, který podporuje ovládací prvek mapování klávesnice.

```
virtual void SetColumnsWidth();
```

### <a name="remarks"></a>Poznámky

Tato metoda nastaví sloupce ovládacího prvku interního seznamu na výchozí šířky. Nejprve se vypočítá šířka sloupce klávesových zkratek. Pak jedna třetina zbývající šířky je přidělena příkazu sloupce a zbývající dvě třetiny je přidělena do sloupce popisu.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CKeyboardManager – třída](../../mfc/reference/ckeyboardmanager-class.md)
