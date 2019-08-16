---
title: COleInsertDialog – třída
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
ms.openlocfilehash: a884f946b60be0567f39477f434db8efe041e393
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503934"
---
# <a name="coleinsertdialog-class"></a>COleInsertDialog – třída

Používá se pro dialogové okno Vložit objekt OLE.

## <a name="syntax"></a>Syntaxe

```
class COleInsertDialog : public COleDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[COleInsertDialog::COleInsertDialog](#coleinsertdialog)|`COleInsertDialog` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[COleInsertDialog::CreateItem](#createitem)|Vytvoří položku vybranou v dialogovém okně.|
|[COleInsertDialog::DoModal](#domodal)|Zobrazí dialogové okno Vložit objekt OLE.|
|[COleInsertDialog:: GetClassID](#getclassid)|Získá identifikátor CLSID přidružený k vybrané položce.|
|[COleInsertDialog::GetDrawAspect](#getdrawaspect)|Určuje, zda má být položka vykreslována jako ikona.|
|[COleInsertDialog::GetIconicMetafile](#geticonicmetafile)|Získá popisovač metasouboru přidruženého k ikonickým formuláři této položky.|
|[COleInsertDialog:: getcesta](#getpathname)|Získá úplnou cestu k souboru zvolenému v dialogovém okně.|
|[COleInsertDialog::GetSelectionType](#getselectiontype)|Získá typ vybraného objektu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[COleInsertDialog::m_io](#m_io)|Struktura typu OLEUIINSERTOBJECT, která řídí chování dialogového okna.|

## <a name="remarks"></a>Poznámky

Vytvořte objekt třídy `COleInsertDialog` , pokud chcete zavolat toto dialogové okno. Po vytvoření `COleInsertDialog` objektu lze pomocí struktury [m_io](#m_io) inicializovat hodnoty nebo stavy ovládacích prvků v dialogovém okně. `m_io` Struktura je typu OLEUIINSERTOBJECT. Další informace o použití této třídy dialogového okna naleznete v tématu členská funkce [DoModal](#domodal) .

> [!NOTE]
>  Kód kontejneru generovaný průvodcem aplikací používá tuto třídu.

Další informace najdete v tématu struktura [OLEUIINSERTOBJECT](/windows/win32/api/oledlg/ns-oledlg-oleuiinsertobjectw) v Windows SDK.

Další informace o dialogových oknech specifických pro OLE naleznete v dialogových oknech článku [v tématu OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleInsertDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxodlgs. h

##  <a name="coleinsertdialog"></a>COleInsertDialog::COleInsertDialog

Tato funkce vytvoří pouze `COleInsertDialog` objekt.

```
COleInsertDialog (
    DWORD dwFlags = IOF_SELECTCREATENEW,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*dwFlags*<br/>
Příznak vytvoření, který obsahuje libovolný počet následujících hodnot, které mají být kombinovány pomocí bitového operátoru OR:

- IOF_SHOWHELP určuje, že se při volání dialogového okna zobrazí tlačítko Help.

- IOF_SELECTCREATENEW určuje, zda bude při volání dialogového okna zaškrtnuto políčko vytvořit nový přepínač. Toto je výchozí nastavení a nedá se použít s IOF_SELECTCREATEFROMFILE.

- IOF_SELECTCREATEFROMFILE určuje, že přepínač Vytvořit ze souboru bude při prvním volání dialogového okna vybrán. Nelze použít s IOF_SELECTCREATENEW.

- IOF_CHECKLINK určuje, že zaškrtávací políčko odkaz bude při prvním volání dialogového okna kontrolován.

- IOF_DISABLELINK určuje, že při volání dialogového okna bude políčko odkaz neaktivní.

- IOF_CHECKDISPLAYASICON Určuje, že se při prvním zaškrtnutí políčka Zobrazit jako ikona bude zobrazovat aktuální ikona a tlačítko změnit ikonu bude povoleno při volání dialogového okna.

- IOF_VERIFYSERVERSEXIST určuje, že dialogové okno by mělo ověřit třídy, které přidá do seznamu, tím, že zajistí, aby servery zadané v registrační databázi existovaly před tím, než se zobrazí dialogové okno. Nastavením tohoto příznaku může výrazně zhoršit výkon.

*pParentWnd*<br/>
Odkazuje na objekt okna nadřazeného objektu nebo vlastníka (typu `CWnd`), do kterého objekt dialogového okna patří. Pokud je hodnota NULL, nadřazené okno objektu dialogového okna je nastaveno na hlavní okno aplikace.

### <a name="remarks"></a>Poznámky

Chcete-li zobrazit dialogové okno, zavolejte funkci [DoModal](#domodal) .

##  <a name="createitem"></a>COleInsertDialog:: CreateItem –

Voláním této funkce vytvoříte objekt typu [COleClientItem](../../mfc/reference/coleclientitem-class.md) pouze v případě, že [DoModal](#domodal) vrátí IDOK.

```
BOOL CreateItem(COleClientItem* pItem);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Odkazuje na položku, která má být vytvořena.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla položka vytvořena; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Před voláním této `COleClientItem` funkce je nutné objekt přidělit.

##  <a name="domodal"></a>COleInsertDialog::D oModal

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

`COleInsertDialog::DocObjectsOnly`Vloží pouze DocObjects.

`COleInsertDialog::ControlsOnly`Vloží pouze ovládací prvky ActiveX.

Nula nevkládá ani DocObject ani ovládací prvek ActiveX. Tato hodnota má za následek stejnou implementaci jako první prototyp uvedený výše.

### <a name="return-value"></a>Návratová hodnota

Stav dokončení dialogového okna Jedna z následujících hodnot:

- IDOK, pokud se dialogové okno úspěšně zobrazilo.

- IDCANCEL, pokud uživatel zrušil dialogové okno.

- IDABORT, pokud došlo k chybě. Je-li vrácen IDABORT, zavolejte členskou funkci [COleDialog:: GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) , kde získáte další informace o typu chyby, ke které došlo. Seznam možných chyb naleznete v Windows SDK funkci [OLEUIINSERTOBJECT](/windows/win32/api/oledlg/nf-oledlg-oleuiinsertobjectw) .

### <a name="remarks"></a>Poznámky

Pokud chcete inicializovat různé ovládací prvky dialogového okna nastavením členů struktury [m_io](#m_io) , měli byste to provést před voláním `DoModal`, ale po sestavení objektu dialogového okna.

Pokud `DoModal` vrátí IDOK, můžete zavolat jiné členské funkce pro načtení nastavení nebo zadání informací do dialogového okna uživatelem.

##  <a name="getclassid"></a>COleInsertDialog:: GetClassID

Voláním této funkce získáte identifikátor CLSID přidružené k vybrané položce pouze v případě, že funkce [DoModal](#domodal) vrátí IDOK a typ `COleInsertDialog::createNewItem`výběru je.

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí CLSID přidružené k vybrané položce.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [klíč CLSID](/windows/win32/com/clsid-key-hklm) v Windows SDK.

##  <a name="getdrawaspect"></a>COleInsertDialog::GetDrawAspect

Voláním této funkce určíte, zda se uživatel rozhodl Zobrazit vybranou položku jako ikonu.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>Návratová hodnota

Metoda potřebná pro vykreslení objektu.

- DVASPECT_CONTENT vrátí, pokud není zaškrtnuto zaškrtávací políčko Zobrazit jako ikonu.

- DVASPECT_ICON vráceny, pokud bylo zaškrtnuto políčko Zobrazit jako ikonu.

### <a name="remarks"></a>Poznámky

Tuto funkci volejte pouze v případě, že [DoModal](#domodal) vrátí IDOK.

Další informace o aspektech kreslení naleznete v tématu [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) data structure in Windows SDK.

##  <a name="geticonicmetafile"></a>COleInsertDialog::GetIconicMetafile

Voláním této funkce získáte popisovač metasouboru, který obsahuje aspekt ikonickým vybrané položky.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač metasouboru obsahujícího aspekt ikonickým pro vybranou položku, pokud bylo zaškrtnuto políčko Zobrazit jako ikonu, když bylo dialogové okno zavřeno, kliknutím na **tlačítko OK**; jinak NULL.

##  <a name="getpathname"></a>COleInsertDialog:: getcesta

Voláním této funkce získáte úplnou cestu k vybranému souboru pouze v případě, že [DoModal](#domodal) vrátí IDOK a typ `COleInsertDialog::createNewItem`výběru není.

```
CString GetPathName() const;
```

### <a name="return-value"></a>Návratová hodnota

Úplná cesta k souboru vybranému v dialogovém okně. Pokud je `createNewItem`typ výběru, tato funkce vrátí `CString` v režimu vydání nevýznamný nebo vyvolá kontrolní výraz v režimu ladění.

##  <a name="getselectiontype"></a>COleInsertDialog::GetSelectionType

Voláním této funkce získáte typ výběru vybraný v případě, že dialogové okno Vložit objekt bylo zavřeno kliknutím na **tlačítko OK**.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Návratová hodnota

Typ provedeného výběru.

### <a name="remarks"></a>Poznámky

Hodnoty návratového typu jsou určeny `Selection` výčtovým typem deklarovaným `COleInsertDialog` ve třídě.

```
enum Selection {
    createNewItem,
    insertFromFile,
    linkToFile
    };
```

Stručný popis těchto hodnot je následující:

- `COleInsertDialog::createNewItem`Byl vybrán přepínač Vytvořit nový.

- `COleInsertDialog::insertFromFile`Přepínač Vytvořit ze souboru byl vybrán a políčko odkaz nebylo zaškrtnuto.

- `COleInsertDialog::linkToFile`Přepínač Vytvořit ze souboru byl vybrán a zaškrtávací políčko odkaz bylo zaškrtnuto.

##  <a name="m_io"></a>  COleInsertDialog::m_io

Struktura typu OLEUIINSERTOBJECT slouží k řízení chování dialogového okna Vložit objekt.

```
OLEUIINSERTOBJECT m_io;
```

### <a name="remarks"></a>Poznámky

Členy této struktury lze upravovat buď přímo, nebo prostřednictvím členských funkcí.

Další informace najdete v tématu struktura [OLEUIINSERTOBJECT](/windows/win32/api/oledlg/ns-oledlg-oleuiinsertobjectw) v Windows SDK.

## <a name="see-also"></a>Viz také:

[OCLIENT Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[COleDialog – třída](../../mfc/reference/coledialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleDialog – třída](../../mfc/reference/coledialog-class.md)
