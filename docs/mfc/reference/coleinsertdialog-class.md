---
title: Třída COleInsertDialog
ms.date: 11/04/2016
f1_keywords:
- COleInsertDialog
- AFXODLGS/COleInsertDialog
- AFXODLGS/COleInsertDialog::COleInsertDialog
- AFXODLGS/COleInsertDialog::CreateItem
- AFXODLGS/COleInsertDialog::DoModal
- AFXODLGS/COleInsertDialog::GetClassID
- AFXODLGS/COleInsertDialog::GetDrawAspect
- AFXODLGS/COleInsertDialog::GetIconicMetafile
- AFXODLGS/COleInsertDialog::GetPathName
- AFXODLGS/COleInsertDialog::GetSelectionType
- AFXODLGS/COleInsertDialog::m_io
helpviewer_keywords:
- COleInsertDialog [MFC], COleInsertDialog
- COleInsertDialog [MFC], CreateItem
- COleInsertDialog [MFC], DoModal
- COleInsertDialog [MFC], GetClassID
- COleInsertDialog [MFC], GetDrawAspect
- COleInsertDialog [MFC], GetIconicMetafile
- COleInsertDialog [MFC], GetPathName
- COleInsertDialog [MFC], GetSelectionType
- COleInsertDialog [MFC], m_io
ms.assetid: a9ec610b-abde-431e-bd01-c40159a66dbb
ms.openlocfilehash: b5de4ff5daa80e1d8727444a4cfd275597e18c08
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374974"
---
# <a name="coleinsertdialog-class"></a>Třída COleInsertDialog

Používá se pro dialogové okno Vložit objekt OLE.

## <a name="syntax"></a>Syntaxe

```
class COleInsertDialog : public COleDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[COleInsertDialog::COleInsertDialog](#coleinsertdialog)|Vytvoří `COleInsertDialog` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[COleInsertDialog::Vytvořitpoložku](#createitem)|Vytvoří položku vybranou v dialogovém okně.|
|[COleInsertDialog::DoModální](#domodal)|Zobrazí dialogové okno Vložit objekt OLE.|
|[coleinsertdialog::GetClassID](#getclassid)|Získá CLSID přidružené k vybrané položce.|
|[COleInsertDialog::GetDrawAspect](#getdrawaspect)|Určuje, zda má být položka nakresleta jako ikona.|
|[COleInsertDialog::GetIconicMetafile](#geticonicmetafile)|Získá popisovač metasouboru přidruženého k kultovní podobě této položky.|
|[COleInsertDialog::GetPathName](#getpathname)|Získá úplnou cestu k souboru vybranému v dialogovém okně.|
|[COleInsertDialog::GetSelectionType](#getselectiontype)|Získá typ objektu vybrané.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[COleInsertDialog::m_io](#m_io)|Struktura typu OLEUIINSERTOBJECT, která řídí chování dialogového okna.|

## <a name="remarks"></a>Poznámky

Chcete-li volat `COleInsertDialog` toto dialogové okno, vytvořte objekt třídy. Po `COleInsertDialog` vytvoření objektu můžete pomocí [m_io](#m_io) struktury inicializovat hodnoty nebo stavy ovládacích prvků v dialogovém okně. Struktura `m_io` je typu OLEUIINSERTOBJECT. Další informace o použití této třídy dialogů naleznete v členské funkci [DoModal.](#domodal)

> [!NOTE]
> Kód kontejneru generovaný průvodcem aplikace používá tuto třídu.

Další informace naleznete v [oleuiINSERTOBJECT](/windows/win32/api/oledlg/ns-oledlg-oleuiinsertobjectw) struktury v sadě Windows SDK.

Další informace týkající se dialogových oken specifických pro OLE naleznete v článku [Dialogová okna v ole](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleInsertDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxodlgs.h

## <a name="coleinsertdialogcoleinsertdialog"></a><a name="coleinsertdialog"></a>COleInsertDialog::COleInsertDialog

Tato funkce vytvoří `COleInsertDialog` pouze objekt.

```
COleInsertDialog (
    DWORD dwFlags = IOF_SELECTCREATENEW,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*dwFlags*<br/>
Vytvoření příznak, který obsahuje libovolný počet následujících hodnot, které mají být kombinovány pomocí bitového operátoru OR:

- IOF_SHOWHELP Určuje, že se při volání dialogového okna zobrazí tlačítko Nápověda.

- IOF_SELECTCREATENEW Určuje, že přepínací tlačítko Vytvořit nový bude vybráno zpočátku při volání dialogového okna. Toto je výchozí nastavení a nelze jej použít s IOF_SELECTCREATEFROMFILE.

- IOF_SELECTCREATEFROMFILE Určuje, že přepínací tlačítko Vytvořit ze souboru bude vybráno zpočátku při volání dialogového okna. Nelze použít s IOF_SELECTCREATENEW.

- IOF_CHECKLINK Určuje, že zaškrtávací políčko Odkaz bude zpočátku zaškrtnuto při volání dialogového okna.

- IOF_DISABLELINK Určuje, že zaškrtávací políčko Odkaz bude při volání dialogového okna zakázáno.

- IOF_CHECKDISPLAYASICON Určuje, že zaškrtávací políčko Zobrazit jako ikona bude zpočátku zaškrtnuto, zobrazí se aktuální ikona a při volání dialogového okna se aktivuje tlačítko Změnit ikonu.

- IOF_VERIFYSERVERSEXIST Určuje, že dialogové okno by mělo ověřit třídy, které přidá do seznamu, tím, že zajistí, aby servery zadané v registrační databázi existovaly před zobrazením dialogového okna. Nastavení tohoto příznaku může výrazně zhoršit výkon.

*pParentWnd*<br/>
Odkazuje na nadřazený objekt `CWnd`okna nebo objekt vlastníka (typu), ke kterému patří objekt dialogového okna. Pokud je null, nadřazené okno objektu dialogového okna je nastavena na hlavní okno aplikace.

### <a name="remarks"></a>Poznámky

Chcete-li zobrazit dialogové okno, zavolejte funkci [DoModal.](#domodal)

## <a name="coleinsertdialogcreateitem"></a><a name="createitem"></a>COleInsertDialog::Vytvořitpoložku

Volání této funkce k vytvoření objektu typu [COleClientItem](../../mfc/reference/coleclientitem-class.md) pouze v [případě, že DoModal](#domodal) vrátí IDOK.

```
BOOL CreateItem(COleClientItem* pItem);
```

### <a name="parameters"></a>Parametry

*pPoložka*<br/>
Odkazuje na položku, která má být vytvořena.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla položka vytvořena; jinak 0.

### <a name="remarks"></a>Poznámky

Před voláním `COleClientItem` této funkce je nutné objekt přidělit.

## <a name="coleinsertdialogdomodal"></a><a name="domodal"></a>COleInsertDialog::DoModální

Voláním této funkce zobrazíte dialogové okno Vložit objekt OLE.

```
virtual INT_PTR
    DoModal();

INT_PTR
    DoModal(DWORD  dwFlags);
```

### <a name="parameters"></a>Parametry

*dwFlags*<br/>
Jedna z následujících hodnot:

`COleInsertDialog::DocObjectsOnly`vloží pouze DocObjects.

`COleInsertDialog::ControlsOnly`vloží pouze ovládací prvky ActiveX.

Nula nevloží ani DocObject, ani ovládací prvek ActiveX. Výsledkem této hodnoty je stejná implementace jako první prototyp uvedený výše.

### <a name="return-value"></a>Návratová hodnota

Stav dokončení dialogového okna. Jedna z následujících hodnot:

- IDOK, pokud bylo dialogové okno úspěšně zobrazeno.

- IDCANCEL, pokud uživatel zrušil dialogové okno.

- IDABORT, pokud došlo k chybě. Pokud je vrácena IDABORT, volejte [cOleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) členské funkce získat další informace o typu chyby, ke které došlo. Seznam možných chyb naleznete v části [Funkce OleUIInsertObject](/windows/win32/api/oledlg/nf-oledlg-oleuiinsertobjectw) v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Pokud chcete inicializovat různé ovládací prvky dialogového okna nastavením členů `DoModal` [m_io](#m_io) struktury, měli byste to provést před voláním , ale po vytvoření objektu dialogového okna.

Pokud `DoModal` vrátí hodnotu IDOK, můžete volat další členské funkce a načíst nastavení nebo informace vstup do dialogového okna uživatelem.

## <a name="coleinsertdialoggetclassid"></a><a name="getclassid"></a>coleinsertdialog::GetClassID

Volání této funkce získat CLSID přidružené k vybrané položce pouze v [případě, že DoModal](#domodal) vrátí IDOK a typ výběru je `COleInsertDialog::createNewItem`.

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí kód CLSID přidružený k vybrané položce.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [KLÍČ CLSID](/windows/win32/com/clsid-key-hklm) v sadě Windows SDK.

## <a name="coleinsertdialoggetdrawaspect"></a><a name="getdrawaspect"></a>COleInsertDialog::GetDrawAspect

Volánítéto funkce k určení, zda se uživatel rozhodl zobrazit vybranou položku jako ikonu.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>Návratová hodnota

Metoda potřebná k vykreslení objektu.

- DVASPECT_CONTENT vrácena, pokud políčko Zobrazit jako ikona nebylo zaškrtnuto.

- DVASPECT_ICON Vráceno, pokud bylo zaškrtnuto políčko Zobrazit jako ikona.

### <a name="remarks"></a>Poznámky

Volání této funkce pouze v [případě, že DoModal](#domodal) vrátí IDOK.

Další informace o aspektu kreslení naleznete v tématu [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) datové struktury v sadě Windows SDK.

## <a name="coleinsertdialoggeticonicmetafile"></a><a name="geticonicmetafile"></a>COleInsertDialog::GetIconicMetafile

Volání této funkce získat popisovač metasouboru, který obsahuje kultovní aspekt vybrané položky.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač metasouboru obsahující hotmana, který obsahuje ikonický aspekt vybrané položky, pokud bylo zaškrtnuto políčko Zobrazit jako ikona, když byl dialog odmítnut výběrem **možnosti OK**; jinak NULL.

## <a name="coleinsertdialoggetpathname"></a><a name="getpathname"></a>COleInsertDialog::GetPathName

Volání této funkce získat úplnou cestu vybraného souboru pouze v [případě, že DoModal](#domodal) vrátí IDOK a typ výběru není `COleInsertDialog::createNewItem`.

```
CString GetPathName() const;
```

### <a name="return-value"></a>Návratová hodnota

Úplná cesta k souboru vybranému v dialogovém okně. Pokud je `createNewItem`typ výběru , tato `CString` funkce vrátí bezvýznamný v režimu vydání nebo způsobí kontrolní výraz v režimu ladění.

## <a name="coleinsertdialoggetselectiontype"></a><a name="getselectiontype"></a>COleInsertDialog::GetSelectionType

Voláním této funkce získáte výběr, když bylo dialogové okno Vložit objekt odmítnuto volbou **OK**.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Návratová hodnota

Typ výběru.

### <a name="remarks"></a>Poznámky

Hodnoty vráceného typu `Selection` jsou určeny typem `COleInsertDialog` výčtu deklarovaným ve třídě.

```
enum Selection {
    createNewItem,
    insertFromFile,
    linkToFile
    };
```

Stručný popis těchto hodnot je následující:

- `COleInsertDialog::createNewItem`Bylo vybráno přepínací tlačítko Vytvořit nový.

- `COleInsertDialog::insertFromFile`Bylo zaškrtnuto přepínací tlačítko Vytvořit ze souboru a políčko Odkaz nebylo zaškrtnuto.

- `COleInsertDialog::linkToFile`Bylo zaškrtnuto přepínací tlačítko Vytvořit ze souboru a bylo zaškrtnuto políčko Odkaz.

## <a name="coleinsertdialogm_io"></a><a name="m_io"></a>COleInsertDialog::m_io

Struktura typu OLEUIINSERTOBJECT používaná k řízení chování dialogového okna Vložit objekt.

```
OLEUIINSERTOBJECT m_io;
```

### <a name="remarks"></a>Poznámky

Členy této struktury lze upravit přímo nebo prostřednictvím členských funkcí.

Další informace naleznete v [oleuiINSERTOBJECT](/windows/win32/api/oledlg/ns-oledlg-oleuiinsertobjectw) struktury v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[OKLIENT ukázkový příklad knihovny MFC](../../overview/visual-cpp-samples.md)<br/>
[COleDialog – třída](../../mfc/reference/coledialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleDialog – třída](../../mfc/reference/coledialog-class.md)
