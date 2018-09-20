---
title: Coleconvertdialog – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleConvertDialog
- AFXODLGS/COleConvertDialog
- AFXODLGS/COleConvertDialog::COleConvertDialog
- AFXODLGS/COleConvertDialog::DoConvert
- AFXODLGS/COleConvertDialog::DoModal
- AFXODLGS/COleConvertDialog::GetClassID
- AFXODLGS/COleConvertDialog::GetDrawAspect
- AFXODLGS/COleConvertDialog::GetIconicMetafile
- AFXODLGS/COleConvertDialog::GetSelectionType
- AFXODLGS/COleConvertDialog::m_cv
dev_langs:
- C++
helpviewer_keywords:
- COleConvertDialog [MFC], COleConvertDialog
- COleConvertDialog [MFC], DoConvert
- COleConvertDialog [MFC], DoModal
- COleConvertDialog [MFC], GetClassID
- COleConvertDialog [MFC], GetDrawAspect
- COleConvertDialog [MFC], GetIconicMetafile
- COleConvertDialog [MFC], GetSelectionType
- COleConvertDialog [MFC], m_cv
ms.assetid: a7c57714-31e8-4b78-834d-8ddd1b856a1c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b1ff8047e6d7291fe55619d8b0a3eabb877b728a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436536"
---
# <a name="coleconvertdialog-class"></a>Coleconvertdialog – třída

Další informace najdete v tématu [OLEUICONVERT](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiconverta) struktura v sadě Windows SDK.

## <a name="syntax"></a>Syntaxe

```
class COleConvertDialog : public COleDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[COleConvertDialog::COleConvertDialog](#coleconvertdialog)|Vytvoří `COleConvertDialog` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[COleConvertDialog::DoConvert](#doconvert)|Provádí převod zadané v dialogovém okně.|
|[COleConvertDialog::DoModal](#domodal)|Zobrazí dialogové okno OLE změnu položky.|
|[COleConvertDialog::GetClassID](#getclassid)|Získá identifikátor CLSID přidružené k vybrané položce.|
|[COleConvertDialog::GetDrawAspect](#getdrawaspect)|Určuje, jestli se má kreslit položky jako ikona.|
|[COleConvertDialog::GetIconicMetafile](#geticonicmetafile)|Získá popisovač pro tento metasoubor spojené s formuláři ikonickým této položky.|
|[COleConvertDialog::GetSelectionType](#getselectiontype)|Získá typ výběru zvolili.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[COleConvertDialog::m_cv](#m_cv)|Struktura, která řídí chování dialogového okna.|

## <a name="remarks"></a>Poznámky

> [!NOTE]
>  Generované průvodcem kontejneru kódu aplikace používá tuto třídu.

Další informace o dialogových oknech OLE konkrétní, najdete v článku [dialogová okna v prostředí OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[Ccommondialog –](../../mfc/reference/ccommondialog-class.md)

[Coledialog –](../../mfc/reference/coledialog-class.md)

`COleConvertDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxodlgs.h

##  <a name="coleconvertdialog"></a>  COleConvertDialog::COleConvertDialog

Vytvoří pouze `COleConvertDialog` objektu.

```
explicit COleConvertDialog (
    COleClientItem* pItem,
    DWORD dwFlags = CF_SELECTCONVERTTO,
    CLSID* pClassID = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Odkazuje na položky, která má být převeden nebo aktivovat.

*dwFlags*<br/>
Vytvoření příznak, který bude obsahovat libovolný počet následující hodnoty kombinované pomocí bitového – operátor or:

- CF_SELECTCONVERTTO Určuje, které se bude přepínač převést na vybrané zpočátku když je volána dialogových oken. Toto nastavení je výchozí.

- CF_SELECTACTIVATEAS Určuje, které se bude přepínač aktivovat jako vybraná zpočátku když je volána dialogových oken.

- CF_SETCONVERTDEFAULT Určuje, že třídy, jejíž identifikátor CLSID určený pomocí `clsidConvertDefault` člena `m_cv` struktura se použije jako výchozí výběr v seznamu tříd, pokud je vybrána přepínač převést na.

- CF_SETACTIVATEDEFAULT Určuje, že třídy, jejíž identifikátor CLSID určený pomocí `clsidActivateDefault` člena `m_cv` struktura se použije jako výchozí výběr v seznamu tříd, pokud je vybrána přepínací tlačítko Aktivovat jako.

- CF_SHOWHELPBUTTON Určuje, že na tlačítko Nápověda se zobrazí, když je volána dialogových oken.

*pClassID má*<br/>
Odkazuje na identifikátor CLSID položka, která má být převeden nebo aktivovat. Pokud má hodnotu NULL, identifikátor CLSID přidružené *pItem* se použije.

*pParentWnd*<br/>
Odkazuje na objekt okna nadřazené nebo vlastník (typu `CWnd`), ke které patří objektu dialogového okna. Pokud je hodnota NULL, nadřazené okno dialogového okna je nastaveno na hlavního okna aplikace.

### <a name="remarks"></a>Poznámky

Chcete-li zobrazit dialogové okno, zavolejte [DoModal](#domodal) funkce.

Další informace najdete v tématu [klíč CLSID](/windows/desktop/com/clsid-key-hklm) a [OLEUICONVERT](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiconverta) struktury.

##  <a name="doconvert"></a>  COleConvertDialog::DoConvert

Tato funkce se volá po vrácení úspěšně z [DoModal](#domodal)– buď k převodu nebo aktivovat objekt typu [COleClientItem](../../mfc/reference/coleclientitem-class.md).

```
BOOL DoConvert(COleClientItem* pItem);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Odkazuje na položky, která má být převeden nebo aktivovat. Nemůže mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Položka je převeden nebo aktivovanou podle vybrané uživatelem v dialogovém okně Převést informace.

##  <a name="domodal"></a>  COleConvertDialog::DoModal

Voláním této funkce zobrazíte dialogové okno Převést OLE.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

Stav dokončení pro dialogové okno. Jeden z následujících hodnot:

- IDOK, pokud úspěšně zobrazí dialogové okno.

- IDCANCEL, pokud uživatel zrušil dialogové okno.

- IDABORT, pokud došlo k chybě. Pokud je vrácena IDABORT, zavolejte [COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) členská funkce, chcete-li získat další informace o typu chyby, ke které došlo. Seznam možných chyb, najdete v článku [OleUIConvert](/windows/desktop/api/oledlg/nf-oledlg-oleuiconverta) funkce v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Pokud chcete inicializovat různé ovládací prvky dialogového okna pole tak, že nastavíte členy [m_cv](#m_cv) strukturu, je potřeba to udělat před voláním `DoModal`, ale po vytvoření objektu dialogového okna.

Pokud `DoModal` vrátí IDOK, můžete volat ostatní členské funkce k načtení nastavení nebo informace, které se vstup uživatelem do dialogových oken.

##  <a name="getclassid"></a>  COleConvertDialog::GetClassID

Volání této funkce získáte identifikátor CLSID přidružené k položce vybrané v dialogovém okně Převést uživatele.

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>Návratová hodnota

Identifikátor CLSID přidružené k položce, která byla vybrána v dialogovém okně Convert.

### <a name="remarks"></a>Poznámky

Tato funkce až po volání [DoModal](#domodal) vrátí IDOK.

Další informace najdete v tématu [klíč CLSID](/windows/desktop/com/clsid-key-hklm) v sadě Windows SDK.

##  <a name="getdrawaspect"></a>  COleConvertDialog::GetDrawAspect

Voláním této funkce určete, jestli se uživatel rozhodl zobrazení vybrané položky jako ikona.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>Návratová hodnota

Metoda potřebné k vykreslení objektu.

- DVASPECT_CONTENT vrácena, pokud není zaškrtnuto zaškrtávací políčko Zobrazit jako ikonu.

- DVASPECT_ICON vrácena, pokud je zaškrtnuto zaškrtávací políčko Zobrazit jako ikonu.

### <a name="remarks"></a>Poznámky

Tato funkce až po volání [DoModal](#domodal) vrátí IDOK.

Další informace o aspekt kreslení, najdete v článku [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) datové struktury v sadě Windows SDK.

##  <a name="geticonicmetafile"></a>  COleConvertDialog::GetIconicMetafile

Voláním této funkce se získat popisovač pro tento metasoubor obsahující ikonickým aspekt vybranou položku.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač pro tento metasoubor obsahující ikonickým aspekt vybranou položku, pokud se zaškrtávací políčko Zobrazit jako ikonu zaškrtnutí, když výběrem OK; zavřel dialogové okno v opačném případě hodnota NULL.

##  <a name="getselectiontype"></a>  COleConvertDialog::GetSelectionType

Voláním této funkce určit typ převodu vybrané v dialogovém okně Convert.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Návratová hodnota

Typ výběru.

### <a name="remarks"></a>Poznámky

Typ vrácené hodnoty jsou určeny `Selection` typ výčtu deklarovaný v `COleConvertDialog` třídy.

```
enum Selection {
    noConversion,
    convertItem,
    activateAs
    };
```

Postupujte podle stručný popis těchto hodnot:

- `COleConvertDialog::noConversion` Vrátí Pokud dialogové okno byla zrušena nebo uživatel vybral žádný převod. Pokud `COleConvertDialog::DoModal` vrátil IDOK, je možné, že uživatel vybral jinou ikonu než dříve vybraný.

- `COleConvertDialog::convertItem` Vrátí, pokud došlo k zaškrtnutí přepínač převést na, uživatel vybral jiná položka převést, a `DoModal` vrátil IDOK.

- `COleConvertDialog::activateAs` Vrátí, pokud došlo k zaškrtnutí přepínač aktivovat jako uživatel vybral jinou položku, pokud chcete aktivovat, a `DoModal` vrátil IDOK.

##  <a name="m_cv"></a>  COleConvertDialog::m_cv

Struktura typu OLEUICONVERT používat k ovládání chování dialogové okno Převést.

```
OLEUICONVERT m_cv;
```

### <a name="remarks"></a>Poznámky

Přímo nebo prostřednictvím členské funkce, lze upravit členy této struktury.

Další informace najdete v tématu [OLEUICONVERT](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiconverta) struktura v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[COleDialog – třída](../../mfc/reference/coledialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleDialog – třída](../../mfc/reference/coledialog-class.md)
