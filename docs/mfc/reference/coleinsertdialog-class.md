---
title: Coleinsertdialog – třída
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
ms.openlocfilehash: 27bf98ea4fe6951624873c1463d50f37558c9234
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "58781481"
---
# <a name="coleinsertdialog-class"></a>Coleinsertdialog – třída

Používá se pro dialogové okno vložení objektu OLE.

## <a name="syntax"></a>Syntaxe

```
class COleInsertDialog : public COleDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[COleInsertDialog::COleInsertDialog](#coleinsertdialog)|Vytvoří `COleInsertDialog` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[COleInsertDialog::CreateItem](#createitem)|Vytvoří položky vybrané v dialogovém okně.|
|[COleInsertDialog::DoModal](#domodal)|Zobrazí dialogové okno vložení objektu OLE.|
|[COleInsertDialog::GetClassID](#getclassid)|Získá identifikátor CLSID přidružené k vybrané položce.|
|[COleInsertDialog::GetDrawAspect](#getdrawaspect)|Určuje, jestli se má kreslit položky jako ikona.|
|[COleInsertDialog::GetIconicMetafile](#geticonicmetafile)|Získá popisovač pro tento metasoubor spojené s formuláři ikonickým této položky.|
|[COleInsertDialog::GetPathName](#getpathname)|Získá úplnou cestu k souboru vybrána v dialogovém okně.|
|[COleInsertDialog::GetSelectionType](#getselectiontype)|Získá typ vybraného objektu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[COleInsertDialog::m_io](#m_io)|Struktura typu OLEUIINSERTOBJECT, které ovládá chování dialogového okna.|

## <a name="remarks"></a>Poznámky

Vytvoření objektu třídy `COleInsertDialog` kdy chcete volat dialogovému oknu. Po `COleInsertDialog` objekt byl vytvořen, můžete použít [m_io](#m_io) struktury k inicializaci hodnoty nebo stavy ovládacích prvků v dialogovém okně. `m_io` Struktury je typu OLEUIINSERTOBJECT. Další informace o použití této třídy dialogového okna, najdete v článku [DoModal](#domodal) členskou funkci.

> [!NOTE]
>  Generované průvodcem kontejneru kódu aplikace používá tuto třídu.

Další informace najdete v tématu [OLEUIINSERTOBJECT](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiinsertobjecta) struktura v sadě Windows SDK.

Další informace o dialogových oken OLE konkrétní, najdete v článku [dialogová okna v prostředí OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget –](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleInsertDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxodlgs.h

##  <a name="coleinsertdialog"></a>  COleInsertDialog::COleInsertDialog

Tato funkce vytvoří pouze `COleInsertDialog` objektu.

```
COleInsertDialog (
    DWORD dwFlags = IOF_SELECTCREATENEW,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*dwFlags*<br/>
Vytvoření příznak, který obsahuje libovolný počet následující hodnoty a nelze jej zkombinovat pomocí operátoru bitového operátoru OR:

- IOF_SHOWHELP Určuje, že na tlačítko Nápověda se zobrazí, když je volána dialogových oken.

- IOF_SELECTCREATENEW Určuje, že bude možné vytvořit nový přepínač vybrán zpočátku když je volána dialogových oken. Toto je výchozí a nelze použít s IOF_SELECTCREATEFROMFILE.

- IOF_SELECTCREATEFROMFILE Určuje, které se bude přepínač Vytvořit ze souboru vybrat zpočátku když je volána dialogových oken. Nelze použít s IOF_SELECTCREATENEW.

- IOF_CHECKLINK Určuje, zda bude odkaz zaškrtávací políčko zaškrtnuto zpočátku když je volána dialogových oken.

- IOF_DISABLELINK určuje políčko propojení se deaktivuje při volání dialogových oken.

- IOF_CHECKDISPLAYASICON Určuje, zda zaškrtávací políčko Zobrazit jako ikonu budou zpočátku kontrolovat, aktuální ikony se zobrazí a změnit ikonu tlačítka se aktivuje, když je zavolána dialogových oken.

- IOF_VERIFYSERVERSEXIST Určuje, zda dialogové okno by měl ověřit třídám, které se přidá do seznamu tím, že zajišťuje, že servery zadané v registrační databázi existovat předtím, než se zobrazí dialogové okno. Nastavení tohoto příznaku může výrazně snížit výkon.

*pParentWnd*<br/>
Odkazuje na objekt okna nadřazené nebo vlastník (typu `CWnd`), ke které patří objektu dialogového okna. Pokud je hodnota NULL, nadřazené okno z objektu dialogového okna je nastaveno na hlavního okna aplikace.

### <a name="remarks"></a>Poznámky

Chcete-li zobrazit dialogové okno, zavolejte [DoModal](#domodal) funkce.

##  <a name="createitem"></a>  COleInsertDialog::CreateItem

Voláním této funkce pro vytvoření objektu typu [COleClientItem](../../mfc/reference/coleclientitem-class.md) pouze tehdy, pokud [DoModal](#domodal) vrátí IDOK.

```
BOOL CreateItem(COleClientItem* pItem);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Odkazuje na položku, kterou chcete vytvořit.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla vytvořena položka; jinak 0.

### <a name="remarks"></a>Poznámky

Je třeba přiřadit `COleClientItem` objektů, než bude možné volat tuto funkci.

##  <a name="domodal"></a>  COleInsertDialog::DoModal

Voláním této funkce Zobrazit dialogové okno vložení objektu OLE.

```
virtual INT_PTR
    DoModal();

INT_PTR
    DoModal(DWORD  dwFlags);
```

### <a name="parameters"></a>Parametry

*dwFlags*<br/>
Jeden z následujících hodnot:

`COleInsertDialog::DocObjectsOnly` Vloží pouze DocObjects.

`COleInsertDialog::ControlsOnly` Vloží pouze ovládací prvky ActiveX.

Nula vloží DocObject ani ovládacího prvku ActiveX. Výsledkem hodnota stejné implementaci jako první prototypu uvedené výše.

### <a name="return-value"></a>Návratová hodnota

Stav dokončení pro dialogové okno. Jeden z následujících hodnot:

- IDOK, pokud úspěšně zobrazí dialogové okno.

- IDCANCEL, pokud uživatel zrušil dialogové okno.

- IDABORT, pokud došlo k chybě. Pokud je vrácena IDABORT, zavolejte [COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) členská funkce, chcete-li získat další informace o typu chyby, ke které došlo. Seznam možných chyb, najdete v článku [OleUIInsertObject](/windows/desktop/api/oledlg/nf-oledlg-oleuiinsertobjecta) funkce v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Pokud chcete inicializovat různé ovládací prvky dialogového okna pole tak, že nastavíte členy [m_io](#m_io) strukturu, je potřeba to udělat před voláním `DoModal`, ale po vytvoření objektu dialogového okna.

Pokud `DoModal` vrátí IDOK, můžete volat další členské funkce k načtení nastavení nebo informace o vstup do dialogového okna uživatelem.

##  <a name="getclassid"></a>  COleInsertDialog::GetClassID

Voláním této funkce získáte CLSID asociované s vybrané položky pouze tehdy, pokud [DoModal](#domodal) vrátí IDOK a typ výběru je `COleInsertDialog::createNewItem`.

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí CLSID asociované s vybranou položkou.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [klíč CLSID](/windows/desktop/com/clsid-key-hklm) v sadě Windows SDK.

##  <a name="getdrawaspect"></a>  COleInsertDialog::GetDrawAspect

Voláním této funkce k určení, pokud se uživatel rozhodl zobrazení vybrané položky jako ikona.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>Návratová hodnota

Metoda potřebné k vykreslení objektu.

- DVASPECT_CONTENT vrácena, pokud není zaškrtnuto zaškrtávací políčko Zobrazit jako ikonu.

- DVASPECT_ICON vrácena, pokud je zaškrtnuto zaškrtávací políčko Zobrazit jako ikonu.

### <a name="remarks"></a>Poznámky

Volání této funkce pouze tehdy, pokud [DoModal](#domodal) vrátí IDOK.

Další informace o aspekt kreslení, naleznete v tématu [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) datové struktury v sadě Windows SDK.

##  <a name="geticonicmetafile"></a>  COleInsertDialog::GetIconicMetafile

Voláním této funkce se získat popisovač pro tento metasoubor obsahující ikonickým aspekt vybranou položku.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač metasoubor obsahující ikonickým aspekt vybranou položku, pokud se zaškrtávací políčko Zobrazit jako ikonu zaškrtnutí, když zavřel dialogové okno výběrem **OK**; jinak hodnota NULL.

##  <a name="getpathname"></a>  COleInsertDialog::GetPathName

Voláním této funkce získat úplnou cestu, pouze pokud vybraný soubor [DoModal](#domodal) vrátí IDOK a typ výběru není `COleInsertDialog::createNewItem`.

```
CString GetPathName() const;
```

### <a name="return-value"></a>Návratová hodnota

Úplná cesta k souboru vybraného v dialogovém okně. Pokud je typ výběru `createNewItem`, tato funkce vrací nemá význam `CString` v režimu vydání nebo způsobí, že kontrolní výraz v režimu ladění.

##  <a name="getselectiontype"></a>  COleInsertDialog::GetSelectionType

Voláním této funkce se získat typ výběru zvolit pokud dialogové okno Vložit objekt nedošlo výběrem **OK**.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Návratová hodnota

Typ výběru.

### <a name="remarks"></a>Poznámky

Typ vrácené hodnoty jsou určeny `Selection` typ výčtu deklarovaný v `COleInsertDialog` třídy.

```
enum Selection {
    createNewItem,
    insertFromFile,
    linkToFile
    };
```

Postupujte podle stručný popis těchto hodnot:

- `COleInsertDialog::createNewItem` Vytvořit nový přepínač byl vybrán.

- `COleInsertDialog::insertFromFile` Byl vybrán přepínač Vytvořit ze souboru a není zaškrtnuto zaškrtávací políčko odkaz.

- `COleInsertDialog::linkToFile` Byl vybrán přepínač Vytvořit ze souboru a odkaz zaškrtávací políčko došlo k zaškrtnutí.

##  <a name="m_io"></a>  COleInsertDialog::m_io

Struktura typu OLEUIINSERTOBJECT používat k ovládání chování dialogové okno Vložit objekt.

```
OLEUIINSERTOBJECT m_io;
```

### <a name="remarks"></a>Poznámky

Přímo nebo prostřednictvím členské funkce, lze upravit členy této struktury.

Další informace najdete v tématu [OLEUIINSERTOBJECT](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiinsertobjecta) struktura v sadě Windows SDK.

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[Coledialog – třída](../../mfc/reference/coledialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Coledialog – třída](../../mfc/reference/coledialog-class.md)
