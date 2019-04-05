---
title: Colepastespecialdialog – třída
ms.date: 11/04/2016
f1_keywords:
- COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog::COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog::AddFormat
- AFXODLGS/COlePasteSpecialDialog::AddLinkEntry
- AFXODLGS/COlePasteSpecialDialog::AddStandardFormats
- AFXODLGS/COlePasteSpecialDialog::CreateItem
- AFXODLGS/COlePasteSpecialDialog::DoModal
- AFXODLGS/COlePasteSpecialDialog::GetDrawAspect
- AFXODLGS/COlePasteSpecialDialog::GetIconicMetafile
- AFXODLGS/COlePasteSpecialDialog::GetPasteIndex
- AFXODLGS/COlePasteSpecialDialog::GetSelectionType
- AFXODLGS/COlePasteSpecialDialog::m_ps
helpviewer_keywords:
- COlePasteSpecialDialog [MFC], COlePasteSpecialDialog
- COlePasteSpecialDialog [MFC], AddFormat
- COlePasteSpecialDialog [MFC], AddLinkEntry
- COlePasteSpecialDialog [MFC], AddStandardFormats
- COlePasteSpecialDialog [MFC], CreateItem
- COlePasteSpecialDialog [MFC], DoModal
- COlePasteSpecialDialog [MFC], GetDrawAspect
- COlePasteSpecialDialog [MFC], GetIconicMetafile
- COlePasteSpecialDialog [MFC], GetPasteIndex
- COlePasteSpecialDialog [MFC], GetSelectionType
- COlePasteSpecialDialog [MFC], m_ps
ms.assetid: 0e82ef9a-9bbe-457e-8240-42c86a0534f7
ms.openlocfilehash: 9c31ed6f82f4280206bf233999fac74981636db3
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "58776905"
---
# <a name="colepastespecialdialog-class"></a>Colepastespecialdialog – třída

Používá se pro dialogové okno zvláštní vložení OLE.

## <a name="syntax"></a>Syntaxe

```
class COlePasteSpecialDialog : public COleDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[COlePasteSpecialDialog::COlePasteSpecialDialog](#colepastespecialdialog)|Vytvoří `COlePasteSpecialDialog` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[COlePasteSpecialDialog::AddFormat](#addformat)|Přidá do seznamu formátů, které vaše aplikace můžete vložit vlastní formáty.|
|[COlePasteSpecialDialog::AddLinkEntry](#addlinkentry)|Přidá novou položku do seznamu podporovaných formátů schránky.|
|[COlePasteSpecialDialog::AddStandardFormats](#addstandardformats)|Přidá CF_BITMAP CF_DIB, CF_METAFILEPICT a volitelně můžete vložit vaše aplikace CF_LINKSOURCE do seznamu formátů.|
|[COlePasteSpecialDialog::CreateItem](#createitem)|Vytvoří položku v kontejneru dokumentu pomocí určeného formátu.|
|[COlePasteSpecialDialog::DoModal](#domodal)|Zobrazí dialogové okno zvláštní vložení OLE.|
|[COlePasteSpecialDialog::GetDrawAspect](#getdrawaspect)|Určuje, jestli se má kreslit položky jako ikony nebo ne.|
|[COlePasteSpecialDialog::GetIconicMetafile](#geticonicmetafile)|Získá popisovač pro tento metasoubor spojené s formuláři ikonickým této položky.|
|[COlePasteSpecialDialog::GetPasteIndex](#getpasteindex)|Získá index možnosti dostupné vložení, který byl vybrán uživatelem.|
|[COlePasteSpecialDialog::GetSelectionType](#getselectiontype)|Získá typ výběru zvolili.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[COlePasteSpecialDialog::m_ps](#m_ps)|Struktura typu OLEUIPASTESPECIAL, které řídí funkce dialogového okna.|

## <a name="remarks"></a>Poznámky

Vytvoření objektu třídy `COlePasteSpecialDialog` kdy chcete volat dialogovému oknu. Po `COlePasteSpecialDialog` objekt byl vytvořen, můžete použít [AddFormat](#addformat) a [AddStandardFormats](#addstandardformats) členské funkce přidejte formátů schránky do dialogového okna. Můžete také použít [m_ps](#m_ps) struktury k inicializaci hodnoty nebo stavy ovládacích prvků v dialogovém okně. `m_ps` Struktury je typu OLEUIPASTESPECIAL.

Další informace najdete v tématu [OLEUIPASTESPECIAL](/windows/desktop/api/oledlg/ns-oledlg-tagoleuipastespeciala) struktura v sadě Windows SDK.

Další informace o dialogových oken OLE konkrétní, najdete v článku [dialogová okna v prostředí OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget –](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COlePasteSpecialDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxodlgs.h

##  <a name="addformat"></a>  COlePasteSpecialDialog::AddFormat

Voláním této funkce pro přidání nové formáty do seznamu formátů, které vaše aplikace může podporovat v operaci Vložit jinak.

```
void AddFormat(
    const FORMATETC& formatEtc,
    LPTSTR lpszFormat,
    LPTSTR lpszResult,
    DWORD flags);

void AddFormat(
    UINT cf,
    DWORD tymed,
    UINT nFormatID,
    BOOL bEnableIcon,
    BOOL bLink);
```

### <a name="parameters"></a>Parametry

*fmt*<br/>
Odkaz na datový typ, který chcete přidat.

*lpszFormat*<br/>
Řetězec, který popisuje formát pro uživatele.

*lpszResult*<br/>
Řetězec, který popisuje výsledek, pokud tento formát je vybrána v dialogovém okně.

*příznaky*<br/>
Různé propojování a vkládání možnosti dostupné pro tento formát. Tento příznak je bitová kombinace hodnot jednoho nebo více různých hodnot v OLEUIPASTEFLAG výčtového typu.

*cf*<br/>
Formát schránky pro přidání.

*objekt tymed*<br/>
Typy médií, které jsou k dispozici v tomto formátu. Toto je bitová kombinace hodnot jednoho nebo více hodnot v objekt TYMED výčtového typu.

*nFormatID*<br/>
ID řetězce, který identifikuje tento formát. Formát tohoto řetězce je dvou samostatných řetězců oddělených znakem '\n'. První řetězec, který je stejný, který by se předal v *lpstrFormat* parametr a druhý je stejné jako *lpstrResult* parametru.

*bEnableIcon*<br/>
Příznak, který určuje, zda zaškrtávací políčko Zobrazit jako ikonu je povoleno, když tento formát je vybrán v seznamu.

*bLink*<br/>
Příznak, který určuje, zda je povoleno přepínací tlačítko Vložit odkaz, když tento formát je vybrán v seznamu.

### <a name="remarks"></a>Poznámky

Voláním této funkce můžete přidat buď standardní formáty, jako je například CF_TEXT nebo CF_TIFF nebo vlastní formáty, které vaše aplikace má registrovaný v systému. Další informace o vkládání dat objektů do vaší aplikace, najdete v článku [datové objekty a zdroje dat: Manipulace s](../../mfc/data-objects-and-data-sources-manipulation.md).

Další informace najdete v tématu [objekt TYMED](/windows/desktop/api/objidl/ne-objidl-tagtymed) typ výčtu a [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktura v sadě Windows SDK.

Další informace najdete v tématu [OLEUIPASTEFLAG](/windows/desktop/api/oledlg/ne-oledlg-tagoleuipasteflag) Výčtový typ v sadě Windows SDK.

##  <a name="addlinkentry"></a>  COlePasteSpecialDialog::AddLinkEntry

Přidá novou položku do seznamu podporovaných formátů schránky.

```
OLEUIPASTEFLAG AddLinkEntry(UINT cf);
```

### <a name="parameters"></a>Parametry

*cf*<br/>
Formát schránky pro přidání.

### <a name="return-value"></a>Návratová hodnota

[OLEUIPASTEFLAG](/windows/desktop/api/oledlg/ne-oledlg-tagoleuipasteflag) struktura obsahující informace o nových odkazů.

##  <a name="addstandardformats"></a>  COlePasteSpecialDialog::AddStandardFormats

Voláním této funkce přidání následujících formátů schránky do seznamu formátů, které vaše aplikace může podporovat v rámci Vložit jinak operace:

```
void AddStandardFormats(BOOL bEnableLink = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnableLink*<br/>
Příznak, který určuje, jestli se má přidat do seznamu formátů CF_LINKSOURCE vaší aplikace můžete vložit.

### <a name="remarks"></a>Poznámky

- CF_BITMAP

- CF_DIB

- CF_METAFILEPICT

- **"Vloženého objektu"**

- (volitelně) **"Spojí zdrojová"**

Tyto formáty slouží k podpoře vložení a propojení.

##  <a name="colepastespecialdialog"></a>  COlePasteSpecialDialog::COlePasteSpecialDialog

Vytvoří `COlePasteSpecialDialog` objektu.

```
COlePasteSpecialDialog(
    DWORD dwFlags = PSF_SELECTPASTE,
    COleDataObject* pDataObject = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*dwFlags*<br/>
Vytvoření příznak obsahuje libovolný počet následující příznaky kombinované pomocí bitového operátoru OR – operátor:

- PSF_SELECTPASTE Určuje, které se bude přepínač Vložit kontroluje zpočátku když je volána dialogových oken. Nelze použít v kombinaci s PSF_SELECTPASTELINK. Toto nastavení je výchozí.

- PSF_SELECTPASTELINK Určuje, že přepínač Vložit odkaz bude zaškrtnuté políčko zpočátku když je volána dialogových oken. Nelze použít v kombinaci s PSF_SELECTPASTE.

- PSF_CHECKDISPLAYASICON Určuje, které se bude zaškrtávací políčko Zobrazit jako ikonu zaškrtnutí zpočátku když je volána dialogových oken.

- PSF_SHOWHELP Určuje, že na tlačítko Nápověda se zobrazí, když je volána dialogových oken.

*pDataObject*<br/>
Odkazuje [coledataobject –](../../mfc/reference/coledataobject-class.md) pro vložení. Pokud je tato hodnota NULL, načte `COleDataObject` ze schránky.

*pParentWnd*<br/>
Odkazuje na objekt okna nadřazené nebo vlastník (typu `CWnd`), ke které patří objektu dialogového okna. Pokud je hodnota NULL, nadřazené okno dialogového okna je nastaveno na hlavního okna aplikace.

### <a name="remarks"></a>Poznámky

Tato funkce vytvoří pouze `COlePasteSpecialDialog` objektu. Chcete-li zobrazit dialogové okno, zavolejte [DoModal](#domodal) funkce.

Další informace najdete v tématu [OLEUIPASTEFLAG](/windows/desktop/api/oledlg/ne-oledlg-tagoleuipasteflag) Výčtový typ v sadě Windows SDK.

##  <a name="createitem"></a>  COlePasteSpecialDialog::CreateItem

Vytvoří novou položku, která byla vybrána v dialogovém okně Vložit jinak.

```
BOOL CreateItem(COleClientItem* pNewItem);
```

### <a name="parameters"></a>Parametry

*pNewItem*<br/>
Odkazuje `COleClientItem` instance. Nemůže mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla tato položka vytvořena úspěšně; jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce by měla být volána pouze po [DoModal](#domodal) vrátí IDOK.

##  <a name="domodal"></a>  COlePasteSpecialDialog::DoModal

Zobrazí dialogové okno zvláštní vložení OLE.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

Stav dokončení pro dialogové okno. Jeden z následujících hodnot:

- IDOK, pokud úspěšně zobrazí dialogové okno.

- IDCANCEL, pokud uživatel zrušil dialogové okno.

- IDABORT, pokud došlo k chybě. Pokud je vrácena IDABORT, zavolejte `COleDialog::GetLastError` členská funkce, chcete-li získat další informace o typu chyby, ke které došlo. Seznam možných chyb, najdete v článku [OleUIPasteSpecial](/windows/desktop/api/oledlg/nf-oledlg-oleuipastespeciala) funkce v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Pokud chcete inicializovat různé ovládací prvky dialogového okna pole tak, že nastavíte členy [m_ps](#m_ps) strukturu, je potřeba to udělat před voláním `DoModal`, ale po vytvoření objektu dialogového okna.

Pokud `DoModal` vrátí IDOK, můžete volat ostatní členské funkce k načtení nastavení nebo informace o vstup uživatelem do dialogových oken.

##  <a name="getdrawaspect"></a>  COlePasteSpecialDialog::GetDrawAspect

Určuje, pokud se uživatel rozhodl zobrazení vybrané položky jako ikona.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>Návratová hodnota

Metoda potřebné k vykreslení objektu.

- DVASPECT_CONTENT vrácena, pokud se zaškrtávací políčko Zobrazit jako ikonu zaškrtnutí, když se zavře dialogové okno.

- DVASPECT_ICON vrácena, pokud došlo k zaškrtnutí zaškrtávacího políčka Zobrazit jako ikonu při dialogové okno se zavře.

### <a name="remarks"></a>Poznámky

Pouze voláním této funkce po [DoModal](#domodal) vrátí IDOK.

Další informace o aspekt kreslení, najdete v článku [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktura v sadě Windows SDK.

##  <a name="geticonicmetafile"></a>  COlePasteSpecialDialog::GetIconicMetafile

Získá metasoubor přidružený k položce vybrané uživatelem.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač na metasoubor obsahující ikonickým aspekt vybrané položky, je-li zaškrtnutí políčka Zobrazit jako ikonu byla vybrána, když dialogové okno se zavře výběrem **OK**; jinak hodnota NULL.

##  <a name="getpasteindex"></a>  COlePasteSpecialDialog::GetPasteIndex

Získá hodnotu indexu přidružený k položce uživatel vybral.

```
int GetPasteIndex() const;
```

### <a name="return-value"></a>Návratová hodnota

Index v poli `OLEUIPASTEENTRY` struktury vybrané uživatelem. Formát, který odpovídá vybraného indexu by měla sloužit při provádění operace vložení.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [OLEUIPASTEENTRY](/windows/desktop/api/oledlg/ns-oledlg-tagoleuipasteentrya) struktura v sadě Windows SDK.

##  <a name="getselectiontype"></a>  COlePasteSpecialDialog::GetSelectionType

Určuje typ výběru uživatele.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí typ výběru.

### <a name="remarks"></a>Poznámky

Typ vrácené hodnoty jsou určeny `Selection` typ výčtu deklarovaný v `COlePasteSpecialDialog` třídy.

```
enum Selection {
    pasteLink,
    pasteNormal,
    pasteOther,
    pasteStatic
    };
```

Postupujte podle stručný desccriptions z těchto hodnot:

- `COlePasteSpecialDialog::pasteLink` Došlo k zaškrtnutí přepínač Vložit odkaz a zvolený formát je standardní formát OLE.

- `COlePasteSpecialDialog::pasteNormal` Došlo k zaškrtnutí přepínač vložení a zvolený formát je standardní formát OLE.

- `COlePasteSpecialDialog::pasteOther` Vybraný formát není standardní formát OLE.

- `COlePasteSpecialDialog::pasteStatic` Zvolený formát je metasouboru.

##  <a name="m_ps"></a>  COlePasteSpecialDialog::m_ps

Struktura typu OLEUIPASTESPECIAL používat k ovládání chování dialogové okno zvláštní vložení.

```
OLEUIPASTESPECIAL m_ps;
```

### <a name="remarks"></a>Poznámky

Přímo nebo prostřednictvím členské funkce, lze upravit členy této struktury.

Další informace najdete v tématu [OLEUIPASTESPECIAL](/windows/desktop/api/oledlg/ns-oledlg-tagoleuipastespeciala) struktura v sadě Windows SDK.

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[Coledialog – třída](../../mfc/reference/coledialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Coledialog – třída](../../mfc/reference/coledialog-class.md)
