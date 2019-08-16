---
title: COlePasteSpecialDialog – třída
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
ms.openlocfilehash: f4174369620f14f2d1ac410aa5d756c75097ad0f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503768"
---
# <a name="colepastespecialdialog-class"></a>COlePasteSpecialDialog – třída

Slouží k zadání speciálního dialogového okna pro vložení OLE.

## <a name="syntax"></a>Syntaxe

```
class COlePasteSpecialDialog : public COleDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[COlePasteSpecialDialog::COlePasteSpecialDialog](#colepastespecialdialog)|`COlePasteSpecialDialog` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[COlePasteSpecialDialog::AddFormat](#addformat)|Přidá vlastní formáty do seznamu formátů, které může vaše aplikace vložit.|
|[COlePasteSpecialDialog::AddLinkEntry](#addlinkentry)|Přidá novou položku do seznamu podporovaných formátů schránky.|
|[COlePasteSpecialDialog::AddStandardFormats](#addstandardformats)|Přidá CF_BITMAP, CF_DIB, CF_METAFILEPICT a volitelně CF_LINKSOURCE na seznam formátů, které může vaše aplikace vložit.|
|[COlePasteSpecialDialog::CreateItem](#createitem)|Vytvoří položku v dokumentu kontejneru pomocí zadaného formátu.|
|[COlePasteSpecialDialog::DoModal](#domodal)|Zobrazí dialogové okno vložení speciálního objektu OLE.|
|[COlePasteSpecialDialog::GetDrawAspect](#getdrawaspect)|Určuje, zda má být položka vykreslována jako ikona.|
|[COlePasteSpecialDialog::GetIconicMetafile](#geticonicmetafile)|Získá popisovač metasouboru přidruženého k ikonickým formuláři této položky.|
|[COlePasteSpecialDialog::GetPasteIndex](#getpasteindex)|Získá index dostupných možností vložení, které byly zvoleny uživatelem.|
|[COlePasteSpecialDialog::GetSelectionType](#getselectiontype)|Získá zvolený typ výběru.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[COlePasteSpecialDialog::m_ps](#m_ps)|Struktura typu OLEUIPASTESPECIAL, která řídí funkci dialogového okna.|

## <a name="remarks"></a>Poznámky

Vytvořte objekt třídy `COlePasteSpecialDialog` , pokud chcete zavolat toto dialogové okno. Po vytvoření `COlePasteSpecialDialog` objektu lze pomocí členských funkcí [AddFormat](#addformat) a [AddStandardFormats](#addstandardformats) přidat do dialogového okna formáty schránky. Můžete také použít strukturu [m_ps](#m_ps) k inicializaci hodnot nebo stavů ovládacích prvků v dialogovém okně. `m_ps` Struktura je typu OleUIPasteSpecial.

Další informace najdete v tématu struktura [OleUIPasteSpecial](/windows/win32/api/oledlg/ns-oledlg-oleuipastespecialw) v Windows SDK.

Další informace o dialogových oknech specifických pro OLE naleznete v dialogových oknech článku [v tématu OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COlePasteSpecialDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxodlgs. h

##  <a name="addformat"></a>COlePasteSpecialDialog::AddFormat

Voláním této funkce přidáte nové formáty do seznamu formátů, které vaše aplikace může podporovat ve speciální operaci vložení.

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
Odkaz na datový typ, který se má přidat

*lpszFormat*<br/>
Řetězec, který popisuje formát pro uživatele.

*lpszResult*<br/>
Řetězec, který popisuje výsledek, pokud je v dialogovém okně zvolen tento formát.

*Flag*<br/>
K dispozici jsou různé možnosti propojování a vkládání pro tento formát. Tento příznak je bitovou kombinací jedné nebo více různých hodnot v typu výčtu OLEUIPASTEFLAG.

*cf*<br/>
Formát schránky, který má být přidán.

*tymed*<br/>
Typy médií, které jsou k dispozici v tomto formátu. Toto je bitová kombinace jedné nebo více hodnot v typu výčtu TYMED.

*nFormatID*<br/>
ID řetězce, který identifikuje tento formát. Formát tohoto řetězce je dva samostatné řetězce oddělené znakem "\n". První řetězec je stejný, který by byl předán do parametru *lpstrFormat* a druhý je stejný jako parametr *lpstrResult* .

*bEnableIcon*<br/>
Příznak, který určuje, zda je zaškrtnuto políčko Zobrazit jako, pokud je v seznamu zvolen tento formát.

*Blikají*<br/>
Příznak, který určuje, zda je povoleno přepínač Vložit odkaz, pokud je v seznamu vybrán tento formát.

### <a name="remarks"></a>Poznámky

Pomocí této funkce lze přidat standardní formáty jako CF_TEXT nebo CF_TIFF nebo vlastní formáty, které vaše aplikace zaregistrovala v systému. Další informace o vkládání datových objektů do aplikace naleznete v článku [datové objekty a zdroje dat: Manipulace](../../mfc/data-objects-and-data-sources-manipulation.md).

Další informace naleznete v části typ výčtu [TYMED](/windows/win32/api/objidl/ne-objidl-tymed) a struktura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) v Windows SDK.

Další informace naleznete v části [OLEUIPASTEFLAG](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag) typ výčtu v Windows SDK.

##  <a name="addlinkentry"></a>COlePasteSpecialDialog::AddLinkEntry

Přidá novou položku do seznamu podporovaných formátů schránky.

```
OLEUIPASTEFLAG AddLinkEntry(UINT cf);
```

### <a name="parameters"></a>Parametry

*cf*<br/>
Formát schránky, který má být přidán.

### <a name="return-value"></a>Návratová hodnota

Struktura [OLEUIPASTEFLAG](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag) obsahující informace pro novou položku odkazu.

##  <a name="addstandardformats"></a>COlePasteSpecialDialog::AddStandardFormats

Voláním této funkce přidáte následující formáty schránky do seznamu formátů, které vaše aplikace může podporovat ve speciální operaci vložení:

```
void AddStandardFormats(BOOL bEnableLink = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnableLink*<br/>
Příznak, který určuje, jestli se má přidat CF_LINKSOURCE do seznamu formátů, které může vaše aplikace vložit.

### <a name="remarks"></a>Poznámky

- CF_BITMAP

- CF_DIB

- CF_METAFILEPICT

- **"Vložený objekt"**

- Volitelně **"Zdroj propojení"**

Tyto formáty slouží k podpoře vkládání a propojení.

##  <a name="colepastespecialdialog"></a>COlePasteSpecialDialog::COlePasteSpecialDialog

`COlePasteSpecialDialog` Vytvoří objekt.

```
COlePasteSpecialDialog(
    DWORD dwFlags = PSF_SELECTPASTE,
    COleDataObject* pDataObject = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*dwFlags*<br/>
Příznak vytvoření obsahuje libovolný počet následujících příznaků kombinovaných pomocí bitového operátoru OR:

- PSF_SELECTPASTE určuje, že přepínač vložení bude při volání dialogového okna kontrolován. Nelze použít v kombinaci s PSF_SELECTPASTELINK. Toto nastavení je výchozí.

- PSF_SELECTPASTELINK určuje, zda bude při volání dialogového okna zaškrtnuto políčko vložit přepínač odkazu. Nelze použít v kombinaci s PSF_SELECTPASTE.

- PSF_CHECKDISPLAYASICON určuje, že zaškrtávací políčko Zobrazit jako ikonu bude při prvním volání dialogového okna kontrolováno.

- PSF_SHOWHELP určuje, že se při volání dialogového okna zobrazí tlačítko Help.

*pDataObject*<br/>
Odkazuje na [COleDataObject](../../mfc/reference/coledataobject-class.md) pro vložení. Pokud je tato hodnota null, získá `COleDataObject` ze schránky.

*pParentWnd*<br/>
Odkazuje na objekt okna nadřazeného objektu nebo vlastníka (typu `CWnd`), do kterého objekt dialogového okna patří. Pokud má hodnotu NULL, nadřazené okno dialogového okna je nastaveno na hlavní okno aplikace.

### <a name="remarks"></a>Poznámky

Tato funkce vytvoří `COlePasteSpecialDialog` pouze objekt. Chcete-li zobrazit dialogové okno, zavolejte funkci [DoModal](#domodal) .

Další informace naleznete v části [OLEUIPASTEFLAG](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag) typ výčtu v Windows SDK.

##  <a name="createitem"></a>COlePasteSpecialDialog:: CreateItem –

Vytvoří novou položku, která byla vybrána v dialogovém okně Vložit jinak.

```
BOOL CreateItem(COleClientItem* pNewItem);
```

### <a name="parameters"></a>Parametry

*pNewItem*<br/>
Odkazuje na `COleClientItem` instanci. Nemůže mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud se položka úspěšně vytvořila; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato funkce by měla být volána pouze po [DoModal](#domodal) vrátí IDOK.

##  <a name="domodal"></a>COlePasteSpecialDialog::D oModal

Zobrazí dialogové okno vložení speciálního objektu OLE.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

Stav dokončení dialogového okna Jedna z následujících hodnot:

- IDOK, pokud se dialogové okno úspěšně zobrazilo.

- IDCANCEL, pokud uživatel zrušil dialogové okno.

- IDABORT, pokud došlo k chybě. Je-li vrácen IDABORT, zavolejte `COleDialog::GetLastError` členskou funkci pro získání dalších informací o typu chyby, ke které došlo. Seznam možných chyb naleznete v Windows SDK funkci [OleUIPasteSpecial](/windows/win32/api/oledlg/nf-oledlg-oleuipastespecialw) .

### <a name="remarks"></a>Poznámky

Pokud chcete inicializovat různé ovládací prvky dialogového okna nastavením členů struktury [m_ps](#m_ps) , měli byste to provést před voláním `DoModal`, ale po sestavení objektu dialogového okna.

Pokud `DoModal` vrátí IDOK, můžete zavolat jiné členské funkce pro načtení nastavení nebo zadání informací uživatelem do dialogového okna.

##  <a name="getdrawaspect"></a>COlePasteSpecialDialog::GetDrawAspect

Určuje, zda se uživatel rozhodl Zobrazit vybranou položku jako ikonu.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>Návratová hodnota

Metoda potřebná pro vykreslení objektu.

- DVASPECT_CONTENT vrátilo, pokud nebylo zaškrtnuto políčko Zobrazit jako ikonu, když bylo dialogové okno zavřeno.

- DVASPECT_ICON vrátilo, pokud bylo zaškrtnuto políčko Zobrazit jako ikonu, když bylo dialogové okno zavřeno.

### <a name="remarks"></a>Poznámky

Tuto funkci volejte jenom po [DoModal](#domodal) vrátí IDOK.

Další informace o aspektech kreslení najdete v tématu struktura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) v Windows SDK.

##  <a name="geticonicmetafile"></a>COlePasteSpecialDialog::GetIconicMetafile

Získá metasoubor přidružený k položce vybrané uživatelem.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač metasouboru obsahujícího aspekt ikonickým pro vybranou položku, pokud bylo zaškrtnuto políčko Zobrazit jako ikonu, když bylo dialogové okno zavřeno, kliknutím na **tlačítko OK**; jinak NULL.

##  <a name="getpasteindex"></a>COlePasteSpecialDialog::GetPasteIndex

Získá hodnotu indexu přidruženou k položce vybrané uživatelem.

```
int GetPasteIndex() const;
```

### <a name="return-value"></a>Návratová hodnota

Index do pole `OLEUIPASTEENTRY` struktury, které uživatel vybral. Při provádění operace vložení by měl být použit formát, který odpovídá vybranému indexu.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu struktura [OLEUIPASTEENTRY](/windows/win32/api/oledlg/ns-oledlg-oleuipasteentryw) v Windows SDK.

##  <a name="getselectiontype"></a>COlePasteSpecialDialog::GetSelectionType

Určuje typ výběru, který uživatel provedl.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí typ provedeného výběru.

### <a name="remarks"></a>Poznámky

Hodnoty návratového typu jsou určeny `Selection` výčtovým typem deklarovaným `COlePasteSpecialDialog` ve třídě.

```
enum Selection {
    pasteLink,
    pasteNormal,
    pasteOther,
    pasteStatic
    };
```

Stručný desccriptions těchto hodnot je následující:

- `COlePasteSpecialDialog::pasteLink`Přepínač vložení odkazu byl zkontrolován a vybraný formát byl standardní formát OLE.

- `COlePasteSpecialDialog::pasteNormal`Přepínač vložení byl zkontrolován a vybraný formát byl standardní formát OLE.

- `COlePasteSpecialDialog::pasteOther`Vybraný formát není standardní formát OLE.

- `COlePasteSpecialDialog::pasteStatic`Zvolený formát byl metasoubor.

##  <a name="m_ps"></a>  COlePasteSpecialDialog::m_ps

Struktura typu OLEUIPASTESPECIAL slouží k řízení chování dialogového okna Vložit speciální.

```
OLEUIPASTESPECIAL m_ps;
```

### <a name="remarks"></a>Poznámky

Členy této struktury lze upravovat přímo nebo prostřednictvím členských funkcí.

Další informace najdete v tématu struktura [OleUIPasteSpecial](/windows/win32/api/oledlg/ns-oledlg-oleuipastespecialw) v Windows SDK.

## <a name="see-also"></a>Viz také:

[OCLIENT Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[COleDialog – třída](../../mfc/reference/coledialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleDialog – třída](../../mfc/reference/coledialog-class.md)
