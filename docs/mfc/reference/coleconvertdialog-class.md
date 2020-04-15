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
ms.openlocfilehash: 6d6690b8d06df29ce9fcd323eb8724009ee3cca9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366163"
---
# <a name="coleconvertdialog-class"></a>COleConvertDialog – třída

Další informace naleznete v [oleuiconvert](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw) struktury v sadě Windows SDK.

## <a name="syntax"></a>Syntaxe

```
class COleConvertDialog : public COleDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[COleConvertDialog::COleConvertDialog](#coleconvertdialog)|Vytvoří `COleConvertDialog` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[COleConvertDialog::DoConvert](#doconvert)|Provede převod zadaný v dialogovém okně.|
|[COleConvertDialog::DoModální](#domodal)|Zobrazí dialogové okno Změnit položku OLE.|
|[coleconvertdialog::GetClassID](#getclassid)|Získá CLSID přidružené k vybrané položce.|
|[COleConvertDialog::GetDrawAspect](#getdrawaspect)|Určuje, zda se má nakreslit položka jako ikona.|
|[COleConvertDialog::GetIconicMetafile](#geticonicmetafile)|Získá popisovač metasouboru přidruženého k kultovní podobě této položky.|
|[COleConvertDialog::GetSelectionType](#getselectiontype)|Získá typ výběru vybrán.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[COleConvertDialog::m_cv](#m_cv)|Struktura, která řídí chování dialogového okna.|

## <a name="remarks"></a>Poznámky

> [!NOTE]
> Kód kontejneru generovaný průvodcem aplikace používá tuto třídu.

Další informace o dialogových oknech specifických pro OLE naleznete v článku [Dialogová okna v ole](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleConvertDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxodlgs.h

## <a name="coleconvertdialogcoleconvertdialog"></a><a name="coleconvertdialog"></a>COleConvertDialog::COleConvertDialog

Vytvoří pouze `COleConvertDialog` objekt.

```
explicit COleConvertDialog (
    COleClientItem* pItem,
    DWORD dwFlags = CF_SELECTCONVERTTO,
    CLSID* pClassID = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*pPoložka*<br/>
Odkazuje na položku, která má být převedena nebo aktivována.

*dwFlags*<br/>
Vytvoření příznak, který obsahuje libovolný počet následujících hodnot v kombinaci s bitové nebo operátor:

- CF_SELECTCONVERTTO Určuje, že přepínací tlačítko Převést na bude vybráno zpočátku při volání dialogového okna. Toto nastavení je výchozí.

- CF_SELECTACTIVATEAS Určuje, že přepínací tlačítko Aktivovat jako bude vybráno zpočátku při volání dialogového okna.

- CF_SETCONVERTDEFAULT Určuje, že třída, jejíž kód `clsidConvertDefault` CLSID je určen členem `m_cv` struktury, bude použita jako výchozí výběr v seznamu tříd, když je vybráno přepínací tlačítko Převést na.

- CF_SETACTIVATEDEFAULT Určuje, že třída, jejíž kód `clsidActivateDefault` CLSID je určen členem `m_cv` struktury, bude použita jako výchozí výběr v seznamu tříd, když je vybráno přepínací tlačítko Aktivovat jako.

- CF_SHOWHELPBUTTON Určuje, že se při volání dialogového okna zobrazí tlačítko Nápověda.

*id třídy p*<br/>
Odkazuje na CLSID položky, která má být převedena nebo aktivována. Pokud null, CLSID přidružené *pItem* bude použit.

*pParentWnd*<br/>
Odkazuje na nadřazený objekt `CWnd`okna nebo objekt vlastníka (typu), ke kterému patří objekt dialogového okna. Pokud je null, nadřazené okno dialogového okna je nastavena na hlavní okno aplikace.

### <a name="remarks"></a>Poznámky

Chcete-li zobrazit dialogové okno, zavolejte funkci [DoModal.](#domodal)

Další informace naleznete v tématu [CLSID Key](/windows/win32/com/clsid-key-hklm) a [OLEUICONVERT](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw) struktury.

## <a name="coleconvertdialogdoconvert"></a><a name="doconvert"></a>COleConvertDialog::DoConvert

Volání této funkce po úspěšném návratu z [DoModal](#domodal), buď převést nebo aktivovat objekt typu [COleClientItem](../../mfc/reference/coleclientitem-class.md).

```
BOOL DoConvert(COleClientItem* pItem);
```

### <a name="parameters"></a>Parametry

*pPoložka*<br/>
Odkazuje na položku, která má být převedena nebo aktivována. Nemůže být null.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Položka se převede nebo aktivuje podle informací vybraných uživatelem v dialogovém okně Převést.

## <a name="coleconvertdialogdomodal"></a><a name="domodal"></a>COleConvertDialog::DoModální

Voláním této funkce zobrazíte dialogové okno Ole Convert.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

Stav dokončení dialogového okna. Jedna z následujících hodnot:

- IDOK, pokud bylo dialogové okno úspěšně zobrazeno.

- IDCANCEL, pokud uživatel zrušil dialogové okno.

- IDABORT, pokud došlo k chybě. Pokud je vrácena IDABORT, volejte [cOleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) členské funkce získat další informace o typu chyby, ke které došlo. Seznam možných chyb naleznete v tématu [OleUIConvert](/windows/win32/api/oledlg/nf-oledlg-oleuiconvertw) funkce v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Pokud chcete inicializovat různé ovládací prvky dialogového okna nastavením členů `DoModal` [m_cv](#m_cv) struktury, měli byste to provést před voláním , ale po vytvoření objektu dialogového okna.

Pokud `DoModal` vrátí Hodnotu IDOK, můžete volat další členské funkce a načíst nastavení nebo informace, které uživatel zadal do dialogového okna.

## <a name="coleconvertdialoggetclassid"></a><a name="getclassid"></a>coleconvertdialog::GetClassID

Voláním této funkce získáte přidružení k položce, kterou uživatel vybral v dialogovém okně Převést.

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>Návratová hodnota

ClsiD přidružený k položce, která byla vybrána v dialogovém okně Převést.

### <a name="remarks"></a>Poznámky

Volání této funkce pouze po [DoModal](#domodal) vrátí IDOK.

Další informace naleznete v tématu [KLÍČ CLSID](/windows/win32/com/clsid-key-hklm) v sadě Windows SDK.

## <a name="coleconvertdialoggetdrawaspect"></a><a name="getdrawaspect"></a>COleConvertDialog::GetDrawAspect

Volání této funkce k určení, zda se uživatel rozhodl zobrazit vybranou položku jako ikonu.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>Návratová hodnota

Metoda potřebná k vykreslení objektu.

- DVASPECT_CONTENT vrácena, pokud políčko Zobrazit jako ikona nebylo zaškrtnuto.

- DVASPECT_ICON Vráceno, pokud bylo zaškrtnuto políčko Zobrazit jako ikona.

### <a name="remarks"></a>Poznámky

Volání této funkce pouze po [DoModal](#domodal) vrátí IDOK.

Další informace o aspektu kreslení naleznete v datové struktuře [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) v sadě Windows SDK.

## <a name="coleconvertdialoggeticonicmetafile"></a><a name="geticonicmetafile"></a>COleConvertDialog::GetIconicMetafile

Volání této funkce získat popisovač metasouboru, který obsahuje kultovní aspekt vybrané položky.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač metasouboru obsahující kultovní aspekt vybrané položky, pokud bylo zaškrtnuto políčko Zobrazit jako ikona, když byl dialog odmítnut výběrem OK; jinak NULL.

## <a name="coleconvertdialoggetselectiontype"></a><a name="getselectiontype"></a>COleConvertDialog::GetSelectionType

Voláním této funkce určete typ převodu vybraný v dialogovém okně Převést.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Návratová hodnota

Typ výběru.

### <a name="remarks"></a>Poznámky

Hodnoty vráceného typu `Selection` jsou určeny typem `COleConvertDialog` výčtu deklarovaným ve třídě.

```
enum Selection {
    noConversion,
    convertItem,
    activateAs
    };
```

Stručný popis těchto hodnot je následující:

- `COleConvertDialog::noConversion`Vráceno, pokud bylo dialogové okno zrušeno nebo uživatel nevybral žádný převod. Pokud `COleConvertDialog::DoModal` je vrácena IDOK, je možné, že uživatel vybral jinou ikonu než dříve vybranou.

- `COleConvertDialog::convertItem`Vráceno, pokud bylo zaškrtnuto přepínací tlačítko Převést na, uživatel vybral jinou položku, na kterou se má převést, a `DoModal` vrátil iDOK.

- `COleConvertDialog::activateAs`Pokud bylo zaškrtnuto přepínací tlačítko Aktivovat jako, uživatel `DoModal` vybral jinou položku k aktivaci a vrátil iDOK.

## <a name="coleconvertdialogm_cv"></a><a name="m_cv"></a>COleConvertDialog::m_cv

Struktura typu OLEUICONVERT slouží k řízení chování dialogového okna Převést.

```
OLEUICONVERT m_cv;
```

### <a name="remarks"></a>Poznámky

Členy této struktury lze upravit přímo nebo prostřednictvím členských funkcí.

Další informace naleznete v [oleuiconvert](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw) struktury v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[COleDialog – třída](../../mfc/reference/coledialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleDialog – třída](../../mfc/reference/coledialog-class.md)
