---
title: COleConvertDialog – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: ba57e756457fcffca806eeba7454ddf7bcf99d34
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504299"
---
# <a name="coleconvertdialog-class"></a>COleConvertDialog – třída

Další informace najdete v tématu struktura [OLEUICONVERT](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw) v Windows SDK.

## <a name="syntax"></a>Syntaxe

```
class COleConvertDialog : public COleDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[COleConvertDialog::COleConvertDialog](#coleconvertdialog)|`COleConvertDialog` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[COleConvertDialog::DoConvert](#doconvert)|Provede převod zadaný v dialogovém okně.|
|[COleConvertDialog::DoModal](#domodal)|Zobrazí dialogové okno změnit položku OLE.|
|[COleConvertDialog:: GetClassID](#getclassid)|Získá identifikátor CLSID přidružený k vybrané položce.|
|[COleConvertDialog::GetDrawAspect](#getdrawaspect)|Určuje, zda má být položka vykreslována jako ikona.|
|[COleConvertDialog::GetIconicMetafile](#geticonicmetafile)|Získá popisovač metasouboru přidruženého k ikonickým formuláři této položky.|
|[COleConvertDialog::GetSelectionType](#getselectiontype)|Získá zvolený typ výběru.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[COleConvertDialog::m_cv](#m_cv)|Struktura, která řídí chování dialogového okna.|

## <a name="remarks"></a>Poznámky

> [!NOTE]
>  Kód kontejneru generovaný průvodcem aplikací používá tuto třídu.

Další informace o dialogových oknech specifických pro OLE naleznete v dialogových oknech článku [v tématu OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleConvertDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxodlgs. h

##  <a name="coleconvertdialog"></a>COleConvertDialog::COleConvertDialog

Vytvoří pouze `COleConvertDialog` objekt.

```
explicit COleConvertDialog (
    COleClientItem* pItem,
    DWORD dwFlags = CF_SELECTCONVERTTO,
    CLSID* pClassID = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Odkazuje na položku, která má být převedena nebo aktivována.

*dwFlags*<br/>
Příznak vytvoření, který obsahuje libovolný počet následujících hodnot v kombinaci pomocí bitového operátoru OR:

- CF_SELECTCONVERTTO určuje, že tlačítko převést na přepínač bude zpočátku zaškrtnuto při volání dialogového okna. Toto nastavení je výchozí.

- CF_SELECTACTIVATEAS určuje, že přepínač aktivovat jako bude při prvním volání dialogového okna vybrán.

- CF_SETCONVERTDEFAULT určuje, že třída, jejíž identifikátor CLSID je určena `clsidConvertDefault` členem `m_cv` struktury, se použije jako výchozí výběr v poli se seznamem tříd, pokud je vybrán přepínač převést na přepínač.

- CF_SETACTIVATEDEFAULT určuje, že třída, jejíž identifikátor CLSID je určena `clsidActivateDefault` členem `m_cv` struktury, se použije jako výchozí výběr v poli se seznamem tříd při výběru přepínače aktivovat jako.

- CF_SHOWHELPBUTTON určuje, že se při volání dialogového okna zobrazí tlačítko Help.

*pClassID*<br/>
Odkazuje na CLSID položky, která má být převedena nebo aktivována. Pokud je NULL, použije se CLSID přidružené k *pItem* .

*pParentWnd*<br/>
Odkazuje na objekt okna nadřazeného objektu nebo vlastníka (typu `CWnd`), do kterého objekt dialogového okna patří. Pokud má hodnotu NULL, nadřazené okno dialogového okna je nastaveno na hlavní okno aplikace.

### <a name="remarks"></a>Poznámky

Chcete-li zobrazit dialogové okno, zavolejte funkci [DoModal](#domodal) .

Další informace najdete v tématu [klíč CLSID](/windows/win32/com/clsid-key-hklm) a struktura [OLEUICONVERT](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw) .

##  <a name="doconvert"></a>COleConvertDialog::D oConvert

Voláním této funkce, po úspěšném vrácení z [DoModal](#domodal), buď pro převod, nebo pro aktivaci objektu typu [COleClientItem](../../mfc/reference/coleclientitem-class.md).

```
BOOL DoConvert(COleClientItem* pItem);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Odkazuje na položku, která má být převedena nebo aktivována. Nemůže mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Položka je převedena nebo aktivována v závislosti na informacích vybraných uživatelem v dialogovém okně převést.

##  <a name="domodal"></a>COleConvertDialog::D oModal

Voláním této funkce zobrazíte dialogové okno převést OLE.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

Stav dokončení dialogového okna Jedna z následujících hodnot:

- IDOK, pokud se dialogové okno úspěšně zobrazilo.

- IDCANCEL, pokud uživatel zrušil dialogové okno.

- IDABORT, pokud došlo k chybě. Je-li vrácen IDABORT, zavolejte členskou funkci [COleDialog:: GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) , kde získáte další informace o typu chyby, ke které došlo. Seznam možných chyb naleznete v Windows SDK funkci [OLEUICONVERT](/windows/win32/api/oledlg/nf-oledlg-oleuiconvertw) .

### <a name="remarks"></a>Poznámky

Pokud chcete inicializovat různé ovládací prvky dialogového okna nastavením členů struktury [m_cv](#m_cv) , měli byste to provést před voláním `DoModal`, ale po sestavení objektu dialogového okna.

Pokud `DoModal` vrátí IDOK, můžete zavolat jiné členské funkce a načíst tak nastavení nebo informace, které uživatel zadal, do dialogového okna.

##  <a name="getclassid"></a>COleConvertDialog:: GetClassID

Voláním této funkce získáte identifikátor CLSID přidružený k položce, kterou uživatel vybral v dialogovém okně převést.

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>Návratová hodnota

Identifikátor CLSID přidružený k položce, která byla vybrána v dialogovém okně převést.

### <a name="remarks"></a>Poznámky

Tuto funkci volejte až po [DoModal](#domodal) vrátí IDOK.

Další informace najdete v tématu [klíč CLSID](/windows/win32/com/clsid-key-hklm) v Windows SDK.

##  <a name="getdrawaspect"></a>COleConvertDialog::GetDrawAspect

Voláním této funkce určíte, zda se uživatel rozhodl Zobrazit vybranou položku jako ikonu.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>Návratová hodnota

Metoda potřebná pro vykreslení objektu.

- DVASPECT_CONTENT vrátí, pokud není zaškrtnuto zaškrtávací políčko Zobrazit jako ikonu.

- DVASPECT_ICON vráceny, pokud bylo zaškrtnuto políčko Zobrazit jako ikonu.

### <a name="remarks"></a>Poznámky

Tuto funkci volejte až po [DoModal](#domodal) vrátí IDOK.

Další informace o aspektech kreslení najdete v tématu Struktura dat [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) v Windows SDK.

##  <a name="geticonicmetafile"></a>COleConvertDialog::GetIconicMetafile

Voláním této funkce získáte popisovač metasouboru, který obsahuje aspekt ikonickým vybrané položky.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač metasouboru obsahujícího aspekt ikonickým pro vybranou položku, pokud bylo zaškrtnuto políčko Zobrazit jako ikonu, když bylo dialogové okno zavřeno, kliknutím na tlačítko OK; jinak NULL.

##  <a name="getselectiontype"></a>COleConvertDialog::GetSelectionType

Voláním této funkce určíte typ převodu vybraný v dialogovém okně převést.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Návratová hodnota

Typ provedeného výběru.

### <a name="remarks"></a>Poznámky

Hodnoty návratového typu jsou určeny `Selection` výčtovým typem deklarovaným `COleConvertDialog` ve třídě.

```
enum Selection {
    noConversion,
    convertItem,
    activateAs
    };
```

Stručný popis těchto hodnot je následující:

- `COleConvertDialog::noConversion`Vrátí se, pokud buď bylo dialogové okno zrušeno, nebo uživatel nevybrali žádný převod. Pokud `COleConvertDialog::DoModal` se vrátí IDOK, je možné, že uživatel vybral jinou ikonu než ta, kterou jste dříve vybrali.

- `COleConvertDialog::convertItem`Vráceno, pokud bylo zaškrtnuto tlačítko převést na přepínač, uživatel vybral jinou položku pro převod na a `DoModal` vrátil IDOK.

- `COleConvertDialog::activateAs`Vrátí se, pokud jste zaškrtnuli tlačítko aktivovat jako, uživatel vybral jinou položku k aktivaci a `DoModal` vrátil IDOK.

##  <a name="m_cv"></a>COleConvertDialog::m_cv

Struktura typu OLEUICONVERT slouží k řízení chování dialogového okna převést.

```
OLEUICONVERT m_cv;
```

### <a name="remarks"></a>Poznámky

Členy této struktury lze upravovat buď přímo, nebo prostřednictvím členských funkcí.

Další informace najdete v tématu struktura [OLEUICONVERT](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw) v Windows SDK.

## <a name="see-also"></a>Viz také:

[COleDialog – třída](../../mfc/reference/coledialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleDialog – třída](../../mfc/reference/coledialog-class.md)
