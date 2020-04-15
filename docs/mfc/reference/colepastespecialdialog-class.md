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
ms.openlocfilehash: 5e67a81f48b8cdf0dae6dc90fc2ded8dc44a73ab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376988"
---
# <a name="colepastespecialdialog-class"></a>COlePasteSpecialDialog – třída

Používá se pro dialogové okno OLE Vložit jinak.

## <a name="syntax"></a>Syntaxe

```
class COlePasteSpecialDialog : public COleDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[ColePasteSpecialDialog::ColePasteSpecialDialog](#colepastespecialdialog)|Vytvoří `COlePasteSpecialDialog` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[ColePasteSpecialDialog::AddFormat](#addformat)|Přidá vlastní formáty do seznamu formátů, které může aplikace vložit.|
|[ColePasteSpecialDialog::AddLinkEntry](#addlinkentry)|Přidá novou položku do seznamu podporovaných formátů schránky.|
|[COlePasteSpecialDialog::AddStandardFormats](#addstandardformats)|Přidá CF_BITMAP, CF_DIB, CF_METAFILEPICT a volitelně CF_LINKSOURCE do seznamu formátů, které může aplikace vložit.|
|[COlePasteSpecialDialog::CreateItem](#createitem)|Vytvoří položku v dokumentu kontejneru pomocí zadaného formátu.|
|[COlePasteSpecialDialog::DoModal](#domodal)|Zobrazí dialogové okno OLE Vložit jinak.|
|[COlePasteSpecialDialog::GetDrawAspect](#getdrawaspect)|Určuje, zda má být položka nakreslete jako ikonu nebo ne.|
|[COlePasteSpecialDialog::GetIconicMetafile](#geticonicmetafile)|Získá popisovač metasouboru přidruženého k kultovní podobě této položky.|
|[COlePasteSpecialDialog::GetPasteIndex](#getpasteindex)|Získá index dostupné možnosti vložení, který byl vybrán uživatelem.|
|[ColePasteSpecialDialog::GetSelectionType](#getselectiontype)|Získá typ výběru vybrán.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[COlePasteSpecialDialog::m_ps](#m_ps)|Struktura typu OLEUIPASTESPECIAL, která řídí funkci dialogového okna.|

## <a name="remarks"></a>Poznámky

Chcete-li volat `COlePasteSpecialDialog` toto dialogové okno, vytvořte objekt třídy. Po `COlePasteSpecialDialog` vytvoření objektu můžete pomocí členských funkcí [AddFormat](#addformat) a [AddStandardFormats](#addstandardformats) přidat do dialogového okna formáty schránky. Strukturu [m_ps](#m_ps) můžete také použít k inicializaci hodnot nebo stavů ovládacích prvků v dialogovém okně. Struktura `m_ps` je typu OLEUIPASTESPECIAL.

Další informace naleznete [v oleuiPASTESPECIAL](/windows/win32/api/oledlg/ns-oledlg-oleuipastespecialw) struktury v sadě Windows SDK.

Další informace týkající se dialogových oken specifických pro OLE naleznete v článku [Dialogová okna v ole](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COlePasteSpecialDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxodlgs.h

## <a name="colepastespecialdialogaddformat"></a><a name="addformat"></a>ColePasteSpecialDialog::AddFormat

Voláním této funkce přidáte nové formáty do seznamu formátů, které může aplikace podporovat v operaci Vložit jinak.

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

*Fmt*<br/>
Odkaz na datový typ, který chcete přidat.

*lpszFormat*<br/>
Řetězec, který popisuje formát pro uživatele.

*lpszVýsledek*<br/>
Řetězec, který popisuje výsledek, pokud je tento formát vybrán v dialogovém okně.

*příznaky*<br/>
Různé možnosti propojení a vkládání, které jsou k dispozici pro tento formát. Tento příznak je bitová kombinace jedné nebo více různých hodnot ve výčtu OLEUIPASTEFLAG typu.

*Viz*<br/>
Formát schránky, který chcete přidat.

*tymed*<br/>
Typy médií, které jsou k dispozici v tomto formátu. Toto je bitová kombinace jedné nebo více hodnot ve výčtovém typu TYMED.

*nID formátu*<br/>
ID řetězce, který identifikuje tento formát. Formát tohoto řetězce je dva samostatné řetězce oddělené znakem \n. První řetězec je stejný, který by byl předán v parametru *lpstrFormat* a druhý je stejný jako parametr *lpstrResult.*

*bEnableIcon*<br/>
Příznak, který určuje, zda je zaškrtnuto políčko Zobrazit jako ikona, pokud je tento formát vybrán v seznamu.

*Blikat*<br/>
Příznak, který určuje, zda je přepínač Vložit odkaz povolen, pokud je tento formát vybrán v seznamu.

### <a name="remarks"></a>Poznámky

Tuto funkci lze volat přidat standardní formáty, například CF_TEXT nebo CF_TIFF nebo vlastní formáty, které vaše aplikace zaregistrovala v systému. Další informace o vkládání datových objektů do aplikace naleznete v článku [Datové objekty a zdroje dat: Manipulace](../../mfc/data-objects-and-data-sources-manipulation.md).

Další informace naleznete v textu typu výčtu [TYMED](/windows/win32/api/objidl/ne-objidl-tymed) a struktury [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) v sadě Windows SDK.

Další informace naleznete v [oleuiPASTEFLAG](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag) ve výčtu typu v sadě Windows SDK.

## <a name="colepastespecialdialogaddlinkentry"></a><a name="addlinkentry"></a>ColePasteSpecialDialog::AddLinkEntry

Přidá novou položku do seznamu podporovaných formátů schránky.

```
OLEUIPASTEFLAG AddLinkEntry(UINT cf);
```

### <a name="parameters"></a>Parametry

*Viz*<br/>
Formát schránky, který chcete přidat.

### <a name="return-value"></a>Návratová hodnota

Struktura [OLEUIPASTEFLAG](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag) obsahující informace pro novou položku propojení.

## <a name="colepastespecialdialogaddstandardformats"></a><a name="addstandardformats"></a>COlePasteSpecialDialog::AddStandardFormats

Voláním této funkce přidáte následující formáty schránky do seznamu formátů, které může aplikace podporovat v operaci Vložit jinak:

```
void AddStandardFormats(BOOL bEnableLink = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnableLink*<br/>
Příznak, který určuje, zda chcete přidat CF_LINKSOURCE do seznamu formátů, které může aplikace vložit.

### <a name="remarks"></a>Poznámky

- CF_BITMAP

- CF_DIB

- CF_METAFILEPICT

- **"Vložený objekt"**

- (volitelně) **"Zdroj propojení"**

Tyto formáty se používají k podpoře vkládání a propojení.

## <a name="colepastespecialdialogcolepastespecialdialog"></a><a name="colepastespecialdialog"></a>ColePasteSpecialDialog::ColePasteSpecialDialog

Vytvoří `COlePasteSpecialDialog` objekt.

```
COlePasteSpecialDialog(
    DWORD dwFlags = PSF_SELECTPASTE,
    COleDataObject* pDataObject = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*dwFlags*<br/>
Vytvoření příznak, obsahuje libovolný počet následujících příznaků v kombinaci pomocí bitového operátoru OR:

- PSF_SELECTPASTE Určuje, že přepínací tlačítko Vložit bude zpočátku zaškrtnuto při volání dialogového okna. Nelze použít v kombinaci s PSF_SELECTPASTELINK. Toto nastavení je výchozí.

- PSF_SELECTPASTELINK Určuje, že přepínací tlačítko Vložit odkaz bude zpočátku zaškrtnuto při volání dialogového okna. Nelze použít v kombinaci s PSF_SELECTPASTE.

- PSF_CHECKDISPLAYASICON Určuje, že zaškrtávací políčko Zobrazit jako ikona bude zpočátku zaškrtnuto při volání dialogového okna.

- PSF_SHOWHELP Určuje, že se při volání dialogového okna zobrazí tlačítko Nápověda.

*objekt pDataObject*<br/>
Odkazuje na [COleDataObject](../../mfc/reference/coledataobject-class.md) pro vkládání. Pokud je tato hodnota null, získá `COleDataObject` ze schránky.

*pParentWnd*<br/>
Odkazuje na nadřazený objekt `CWnd`okna nebo objekt vlastníka (typu), ke kterému patří objekt dialogového okna. Pokud je null, nadřazené okno dialogového okna je nastavena na hlavní okno aplikace.

### <a name="remarks"></a>Poznámky

Tato funkce pouze `COlePasteSpecialDialog` vytvoří objekt. Chcete-li zobrazit dialogové okno, zavolejte funkci [DoModal.](#domodal)

Další informace naleznete v [oleuiPASTEFLAG](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag) ve výčtu typu v sadě Windows SDK.

## <a name="colepastespecialdialogcreateitem"></a><a name="createitem"></a>COlePasteSpecialDialog::CreateItem

Vytvoří novou položku, která byla vybrána v dialogovém okně Vložit jinak.

```
BOOL CreateItem(COleClientItem* pNewItem);
```

### <a name="parameters"></a>Parametry

*pNewItem*<br/>
Odkazuje na `COleClientItem` instanci. Nemůže být null.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla položka úspěšně vytvořena; jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce by měla být volána pouze po [DoModal](#domodal) vrátí IDOK.

## <a name="colepastespecialdialogdomodal"></a><a name="domodal"></a>COlePasteSpecialDialog::DoModal

Zobrazí dialogové okno OLE Vložit jinak.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

Stav dokončení dialogového okna. Jedna z následujících hodnot:

- IDOK, pokud bylo dialogové okno úspěšně zobrazeno.

- IDCANCEL, pokud uživatel zrušil dialogové okno.

- IDABORT, pokud došlo k chybě. Pokud je vrácena IDABORT, volání `COleDialog::GetLastError` členské funkce získat další informace o typu chyby, ke které došlo. Seznam možných chyb naleznete v části [OleUIPasteSpecial](/windows/win32/api/oledlg/nf-oledlg-oleuipastespecialw) v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Pokud chcete inicializovat různé ovládací prvky dialogového okna nastavením členů `DoModal` [m_ps](#m_ps) struktury, měli byste to provést před voláním , ale po vytvoření objektu dialogového okna.

Pokud `DoModal` vrátí hodnotu IDOK, můžete volat další členské funkce a načíst nastavení nebo informace vstupující uživatelem do dialogového okna.

## <a name="colepastespecialdialoggetdrawaspect"></a><a name="getdrawaspect"></a>COlePasteSpecialDialog::GetDrawAspect

Určuje, zda se uživatel rozhodl zobrazit vybranou položku jako ikonu.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>Návratová hodnota

Metoda potřebná k vykreslení objektu.

- DVASPECT_CONTENT Vráceno, pokud při zavření dialogového okna nebylo zaškrtnuto políčko Zobrazit jako ikona.

- DVASPECT_ICON Vráceno, pokud bylo při zavření dialogového okna zaškrtnuto políčko Zobrazit jako ikona.

### <a name="remarks"></a>Poznámky

Volání této funkce pouze po [DoModal](#domodal) vrátí IDOK.

Další informace o aspektu kreslení naleznete v tématu [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) struktura v sadě Windows SDK.

## <a name="colepastespecialdialoggeticonicmetafile"></a><a name="geticonicmetafile"></a>COlePasteSpecialDialog::GetIconicMetafile

Získá metasoubor přidružený k položce vybrané uživatelem.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač metasouboru obsahující hotmana, který obsahuje ikonický aspekt vybrané položky, pokud bylo při zavření dialogového okna zaškrtnuto políčko Zobrazit jako ikona, když bylo dialogové okno odmítnuto volbou **OK**; jinak NULL.

## <a name="colepastespecialdialoggetpasteindex"></a><a name="getpasteindex"></a>COlePasteSpecialDialog::GetPasteIndex

Získá hodnotu indexu přidruženou k položce, kterou uživatel vybral.

```
int GetPasteIndex() const;
```

### <a name="return-value"></a>Návratová hodnota

Index do pole `OLEUIPASTEENTRY` struktur, které byly vybrány uživatelem. Formát, který odpovídá vybranému indexu, by měl být použit při provádění operace vložení.

### <a name="remarks"></a>Poznámky

Další informace naleznete v [oleuipasteentry](/windows/win32/api/oledlg/ns-oledlg-oleuipasteentryw) struktury v sadě Windows SDK.

## <a name="colepastespecialdialoggetselectiontype"></a><a name="getselectiontype"></a>ColePasteSpecialDialog::GetSelectionType

Určuje typ výběru, který uživatel provedl.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí typ provedeného výběru.

### <a name="remarks"></a>Poznámky

Hodnoty vráceného typu `Selection` jsou určeny typem `COlePasteSpecialDialog` výčtu deklarovaným ve třídě.

```
enum Selection {
    pasteLink,
    pasteNormal,
    pasteOther,
    pasteStatic
    };
```

Následují stručné hodnoty těchto hodnot:

- `COlePasteSpecialDialog::pasteLink`Bylo zkontrolováno přepínací tlačítko Vložit odkaz a zvolený formát byl standardní formát OLE.

- `COlePasteSpecialDialog::pasteNormal`Bylo zkontrolováno přepínací tlačítko Vložit a zvolený formát byl standardní formát OLE.

- `COlePasteSpecialDialog::pasteOther`Vybraný formát není standardní formát OLE.

- `COlePasteSpecialDialog::pasteStatic`Zvolený formát byl metasoubor.

## <a name="colepastespecialdialogm_ps"></a><a name="m_ps"></a>COlePasteSpecialDialog::m_ps

Struktura typu OLEUIPASTESPECIAL používaná k řízení chování dialogového okna Vložit jinak.

```
OLEUIPASTESPECIAL m_ps;
```

### <a name="remarks"></a>Poznámky

Členy této struktury lze upravovat přímo nebo prostřednictvím členských funkcí.

Další informace naleznete [v oleuiPASTESPECIAL](/windows/win32/api/oledlg/ns-oledlg-oleuipastespecialw) struktury v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[OKLIENT ukázkový příklad knihovny MFC](../../overview/visual-cpp-samples.md)<br/>
[COleDialog – třída](../../mfc/reference/coledialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleDialog – třída](../../mfc/reference/coledialog-class.md)
