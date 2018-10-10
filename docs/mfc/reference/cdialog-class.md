---
title: CDialog – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDialog
- AFXWIN/CDialog
- AFXWIN/CDialog::CDialog
- AFXWIN/CDialog::Create
- AFXWIN/CDialog::CreateIndirect
- AFXWIN/CDialog::DoModal
- AFXWIN/CDialog::EndDialog
- AFXWIN/CDialog::GetDefID
- AFXWIN/CDialog::GotoDlgCtrl
- AFXWIN/CDialog::InitModalIndirect
- AFXWIN/CDialog::MapDialogRect
- AFXWIN/CDialog::NextDlgCtrl
- AFXWIN/CDialog::OnInitDialog
- AFXWIN/CDialog::OnSetFont
- AFXWIN/CDialog::PrevDlgCtrl
- AFXWIN/CDialog::SetDefID
- AFXWIN/CDialog::SetHelpID
- AFXWIN/CDialog::OnCancel
- AFXWIN/CDialog::OnOK
dev_langs:
- C++
helpviewer_keywords:
- CDialog [MFC], CDialog
- CDialog [MFC], Create
- CDialog [MFC], CreateIndirect
- CDialog [MFC], DoModal
- CDialog [MFC], EndDialog
- CDialog [MFC], GetDefID
- CDialog [MFC], GotoDlgCtrl
- CDialog [MFC], InitModalIndirect
- CDialog [MFC], MapDialogRect
- CDialog [MFC], NextDlgCtrl
- CDialog [MFC], OnInitDialog
- CDialog [MFC], OnSetFont
- CDialog [MFC], PrevDlgCtrl
- CDialog [MFC], SetDefID
- CDialog [MFC], SetHelpID
- CDialog [MFC], OnCancel
- CDialog [MFC], OnOK
ms.assetid: ca64b77e-2cd2-47e3-8eff-c2645ad578f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fdbbda6956e3265e7b17aa63ea26ac760b1fda5a
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2018
ms.locfileid: "48890618"
---
# <a name="cdialog-class"></a>CDialog – třída

Základní třída použitá pro zobrazování dialogových oken na obrazovce.

## <a name="syntax"></a>Syntaxe

```
class CDialog : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CDialog::CDialog](#cdialog)|Vytvoří `CDialog` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDialog::Create](#create)|Inicializuje `CDialog` objektu. Vytvoří nemodální dialogové okno a připojí ho k `CDialog` objektu.|
|[CDialog::CreateIndirect](#createindirect)|Vytvoří nemodální dialogové okno z šablony dialog-box v paměti (ne založené na prostředcích).|
|[CDialog::DoModal](#domodal)|Vyvolá modální dialogové okno a vrátí po dokončení.|
|[CDialog::EndDialog](#enddialog)|Modální dialogové okno se zavře.|
|[CDialog::GetDefID](#getdefid)|Získá ID stisknutelných výchozí ovládací prvek pro dialogové okno.|
|[CDialog::GotoDlgCtrl](#gotodlgctrl)|Přesune fokus na zadané dialogového okna ovládacího prvku v dialogovém okně.|
|[CDialog::InitModalIndirect](#initmodalindirect)|Vytvoří modální dialogové okno z šablony dialog-box v paměti (ne založené na prostředcích). Parametry jsou uloženy do funkce `DoModal` je volána.|
|[CDialog::MapDialogRect](#mapdialogrect)|Převede jednotkách dialogového okna obdélník na obrazovce jednotky.|
|[CDialog::NextDlgCtrl](#nextdlgctrl)|Přesune fokus na další ovládací prvek dialogového okna v dialogovém okně.|
|[CDialog::OnInitDialog](#oninitdialog)|Přepsání pro rozšíření Inicializace dialogového okna.|
|[CDialog::OnSetFont](#onsetfont)|Přepsání nastavení za účelem určení písma, která se má použít při kreslení textu je ovládací prvek dialogového okna.|
|[CDialog::PrevDlgCtrl](#prevdlgctrl)|Přesune fokus na předchozí ovládací prvek dialogového okna v dialogovém okně.|
|[CDialog::SetDefID](#setdefid)|Výchozí ovládací prvek stisknutelných pro dialogové okno se změní na zadaný pushbutton.|
|[CDialog::SetHelpID](#sethelpid)|Nastaví ID kontextové nápovědy pro dialogové okno.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CDialog::OnCancel](#oncancel)|Přepsání nastavení za účelem provedení tlačítko Storno nebo reakce na stisknutí klávesy ESC. Výchozí hodnota zavře dialogové okno a `DoModal` vrátí IDCANCEL.|
|[CDialog::OnOK](#onok)|Přepsání nastavení za účelem provedení akce tlačítko OK v modální dialogové okno. Výchozí hodnota zavře dialogové okno a `DoModal` vrátí IDOK.|

## <a name="remarks"></a>Poznámky

Dialogová okna jsou dvou typů: modální a nemodální. Modální dialogové okno musejí být uzavřené tímto uživatelem, předtím, než bude aplikace dále. Nemodální dialogové okno umožňuje uživateli zobrazit dialogové okno a vraťte se do jiné úlohy bez zrušení nebo odebrání dialogových oken.

A `CDialog` objektu je kombinací šablony dialogového okna a `CDialog`-odvozené třídy. Použití editoru dialogového okna můžete vytvořit šablony dialogového okna a uložit do zdroje a pak pomocí průvodce Přidat třídu vytvořte třídu odvozenou z `CDialog`.

Dialogovému oknu, stejně jako jakékoli jiné okno přijímá zprávy z Windows. V dialogovém okně vás zajímají hlavně zpracování zpráv s oznámením v ovládacích prvcích v dialogovém okně, protože to je, jak uživatel pracuje s dialogovým oknem. Použijte okno Vlastnosti a vyberte si přejete zpráv pro zpracování a přidá položky odpovídající mapu zpráv a členské funkce obslužná rutina zprávy do třídy za vás. Stačí napsat kód specifický pro aplikaci v členské funkce obslužné rutiny.

Pokud dáváte přednost, můžete vždy napsat položky mapování zpráv a členské funkce ručně.

Ve všech ale nejvíce triviální dialogových oken Přidat členské proměnné vlastní třídy odvozené dialogového okna pro ukládání dat zadané v ovládacích prvcích v dialogovém okně uživatelem nebo chcete zobrazit data pro uživatele. Přidat proměnnou průvodce můžete vytvořit členské proměnné a spojit je s ovládacími prvky. Ve stejnou dobu můžete zvolit typ proměnné a přípustný rozsah hodnot pro každou proměnnou. Kód průvodce přidá členské proměnné do vlastní třídy odvozené dialogového okna.

Mapování dat se vygeneruje automaticky zpracování výměna dat mezi ovládacími prvky v dialogovém okně a členské proměnné. Mapování dat poskytuje funkce, které inicializovat ovládací prvky v dialogovém okně nahraďte odpovídajícími hodnotami, načtěte data a ověřit data.

K vytvoření modálního dialogového okna, sestavte objekt v zásobníku pomocí konstruktoru pro vlastní třídy odvozené dialogového okna a poté zavolejte `DoModal` vytvoření dialogového okna a jeho ovládací prvky. Pokud chcete vytvořit nemodální dialogové okno, zavolejte `Create` v konstruktoru vlastní třídy dialogového okna.

Můžete také vytvořit šablonu v paměti pomocí [DLGTEMPLATE](/windows/desktop/api/winuser/ns-winuser-dlgtemplate) datové struktury, jak je popsáno v sadě Windows SDK. Poté, co vytvoříte `CDialog` objektu, volejte [CreateIndirect](#createindirect) k vytvoření nemodální dialogové okno nebo volání [InitModalIndirect](#initmodalindirect) a [DoModal](#domodal) vytvoření modální Dialogové okno.

Mapování výměna a ověřování dat je napsána v přepsání `CWnd::DoDataExchange` , který se přidá do vaší nové třídy dialogového okna. Zobrazit [DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange) členské funkce v `CWnd` pro další informace o funkci výměna a ověřování.

Programátor a volání rozhraní framework `DoDataExchange` nepřímo prostřednictvím volání [CWnd::UpdateData](../../mfc/reference/cwnd-class.md#updatedata).

Rámec volá `UpdateData` když uživatel klepne na tlačítko OK zavřete dialogové okno modální okno. (Není načítání dat po kliknutí na tlačítko Storno.) Výchozí implementace [OnInitDialog](#oninitdialog) nevolá `UpdateData` nastavit počáteční hodnoty z ovládacích prvků. Obvykle přepsat `OnInitDialog` další inicializovat ovládací prvky. `OnInitDialog` je volána poté, co jsou vytvořeny všechny ovládací prvky dialogového okna a těsně před dialogového okna se zobrazí pole.

Můžete volat `CWnd::UpdateData` kdykoli během provádění modální a nemodální dialogové okno.

Pokud vyvíjíte dialogového okna ručně, nezbytné členské proměnné přidejte do třídy odvozené dialogového okna sami a přidejte členské funkce pro nastavení nebo získání těchto hodnot.

Modální dialogové okno se automaticky zavře po stisknutí tlačítka OK nebo zrušení nebo když kód volá `EndDialog` členskou funkci.

Při implementaci nemodální dialogové okno vždy přepíší `OnCancel` členské funkce a volání `DestroyWindow` z ní. Nevolejte základní třídu `CDialog::OnCancel`, protože volá `EndDialog`, které se vytvořit dialogové okno, ale nebude zničit. Měli byste také přepsat `PostNcDestroy` pro nemodální dialogová okna, chcete-li odstranit **to**, protože nemodální dialogová okna jsou obvykle přiděleny pomocí **nové**. Modální dialogová okna jsou obvykle vytvořeny v rámci a není nutné `PostNcDestroy` vyčištění.

Další informace o `CDialog`, naleznete v tématu [dialogových oknech](../../mfc/dialog-boxes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

##  <a name="cdialog"></a>  CDialog::CDialog

K sestavení kompletních založené na prostředcích modální dialogové okno, volání obou tvarech veřejného konstruktoru.

```
explicit CDialog(
    LPCTSTR lpszTemplateName,
    CWnd* pParentWnd = NULL);


explicit CDialog(
    UINT nIDTemplate,
    CWnd* pParentWnd = NULL);

CDialog();
```

### <a name="parameters"></a>Parametry

*lpszTemplateName*<br/>
Obsahuje řetězec zakončený hodnotou null, který je název prostředku šablony dialogového okna.

*nIDTemplate*<br/>
Obsahuje identifikační číslo prostředku šablony dialogového okna.

*pParentWnd*<br/>
Odkazuje na objekt okna nadřazené nebo vlastník (typu [CWnd](../../mfc/reference/cwnd-class.md)), ke které patří objektu dialogového okna. Pokud je hodnota NULL, objektu dialogového okna nadřazené okno bude nastaveno na hlavní okno aplikace.

### <a name="remarks"></a>Poznámky

Jednu formu konstruktor poskytuje přístup k prostředku dialogového okna podle názvu šablony. Konstruktoru poskytuje přístup podle čísla ID šablony, obvykle s **IDD_** předpona (například IDD_DIALOG1).

K sestavení kompletních modální dialogové okno z šablony v paměti, nejprve vyvolat konstruktor bez parametrů, chráněné a následně zavolat `InitModalIndirect`.

Poté, co vytvoříte modální dialogové okno s některou z výše uvedených metod, volání `DoModal`.

Vytvoření nemodálního dialogového okna, chráněné forma se používá `CDialog` konstruktoru. Konstruktor je chráněna, protože musíte odvodit vlastní třídu dialogového okna pro implementaci nemodální dialogové okno. Vytvoření nemodálního dialogového okna je dvoustupňový proces. První volání konstruktoru; Zavolejte `Create` členskou funkci pro vytvoření založené na prostředcích dialogového okna, nebo se telefonicky `CreateIndirect` vytvořit dialogové okno z šablony v paměti.

##  <a name="create"></a>  CDialog::Create

Volání `Create` Vytvoření nemodálního dialogového okna pomocí šablony dialog-box z prostředku.

```
virtual BOOL Create(
    LPCTSTR lpszTemplateName,
    CWnd* pParentWnd = NULL);


virtual BOOL Create(
    UINT nIDTemplate,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*lpszTemplateName*<br/>
Obsahuje řetězec zakončený hodnotou null, který je název prostředku šablony dialogového okna.

*pParentWnd*<br/>
Odkazuje na nadřazený objekt okna (typu [CWnd](../../mfc/reference/cwnd-class.md)), ke které patří objektu dialogového okna. Pokud je hodnota NULL, objektu dialogového okna nadřazené okno bude nastaveno na hlavní okno aplikace.

*nIDTemplate*<br/>
Obsahuje identifikační číslo prostředku šablony dialogového okna.

### <a name="return-value"></a>Návratová hodnota

Obě formy vrátí nenulovou hodnotu, pokud dialogového okna vytváření a inicializace byla úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Můžete vložit volání `Create` uvnitř konstruktoru nebo volání po konstruktoru je vyvolána.

Dvě formy `Create` členské funkce jsou k dispozici pro přístup k prostředku šablony dialogového okna podle názvu šablony nebo šablony identifikační číslo (například IDD_DIALOG1).

U obou tvarech předejte ukazatel na nadřazený objekt okna. Pokud *pParentWnd* má hodnotu NULL, vytvoří se dialogové okno s její nadřazené nebo vlastník okno nastavení hlavního okna aplikace.

`Create` Členská funkce vrátí okamžitě po vytvoření dialogových oken.

WS_VISIBLE styl šablony dialogového okna použijte, pokud při vytváření nadřazeného okna by se zobrazit dialogové okno. V opačném případě je nutné volat `ShowWindow`. Další styly dialogového okna a jejich použití naleznete v tématu [DLGTEMPLATE](/windows/desktop/api/winuser/ns-winuser-dlgtemplate) struktura v sadě Windows SDK a [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) v *odkaz knihovny MFC*.

Použití `CWnd::DestroyWindow` funkce zničit dialogové okno vytvořené `Create` funkce.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCControlLadenDialog#62](../../mfc/codesnippet/cpp/cdialog-class_1.cpp)]

##  <a name="createindirect"></a>  CDialog::CreateIndirect

Voláním této členské funkce pro nemodální dialogové okno vytvořit z šablony dialog-box v paměti.

```
virtual BOOL CreateIndirect(
    LPCDLGTEMPLATE lpDialogTemplate,
    CWnd* pParentWnd = NULL,
    void* lpDialogInit = NULL);


virtual BOOL CreateIndirect(
    HGLOBAL hDialogTemplate,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*lpDialogTemplate*<br/>
Odkazuje na paměti, která obsahuje šablony dialog-box umožňuje vytvořit dialogové okno. Tato šablona je ve formě [DLGTEMPLATE](/windows/desktop/api/winuser/ns-winuser-dlgtemplate) struktury a ovládací prvek informace, jak je popsáno v sadě Windows SDK.

*pParentWnd*<br/>
Odkazuje na objekt okna nadřazeného objektu dialogového okna (typu [CWnd](../../mfc/reference/cwnd-class.md)). Pokud je hodnota NULL, objektu dialogového okna nadřazené okno bude nastaveno na hlavní okno aplikace.

*lpDialogInit*<br/>
Odkazuje na prostředek DLGINIT.

*hDialogTemplate*<br/>
Obsahuje popisovač do globální paměti, který obsahuje šablony dialog-box. Tato šablona je ve formě `DLGTEMPLATE` strukturu a data pro každý ovládací prvek v dialogovém okně.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byl vytvořen a inicializován úspěšně; dialogových oken jinak 0.

### <a name="remarks"></a>Poznámky

`CreateIndirect` Členská funkce vrátí okamžitě po vytvoření dialogových oken.

WS_VISIBLE styl šablony dialogového okna použijte, pokud při vytváření nadřazeného okna by se zobrazit dialogové okno. V opačném případě je nutné volat `ShowWindow` způsobit má objevit. Další informace o tom, jak můžete zadat další styly dialogového okna v šabloně, najdete v článku [DLGTEMPLATE](/windows/desktop/api/winuser/ns-winuser-dlgtemplate) struktura v sadě Windows SDK.

Použití `CWnd::DestroyWindow` funkce zničit dialogové okno vytvořené `CreateIndirect` funkce.

Dialogová okna, které obsahují ovládací prvky ActiveX vyžadují další informace, které jsou součástí DLGINIT prostředků.

##  <a name="domodal"></a>  CDialog::DoModal

Voláním této členské funkce k vyvolání modálních dialogových oken a vrácení výsledku dialogového okna, až budete hotovi.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

**Int** hodnotu, která určuje hodnotu *Nvýsledek* parametr, který byl předán [CDialog::EndDialog](#enddialog) členská funkce, který slouží k zavření dialogového okna. Vrácená hodnota je -1, pokud funkci nelze vytvořit dialogové okno nebo IDABORT, pokud došlo k nějaké chybě, v takovém případě v okně Výstup bude obsahovat informace o chybě z [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360).

### <a name="remarks"></a>Poznámky

Tato členská funkce zpracovává všechny interakce s uživatelem, dialogové okno je aktivní. Toto je kvůli tomu dialogové okno modální; To znamená uživatel nemohou komunikovat s ostatní okna, dokud není zavřena dialogových oken.

Pokud uživatel klikne jeden z tlačítek v dialogovém okně, jako je OK nebo zrušit, obslužná rutina zprávy členské funkce, jako například [onok –](#onok) nebo [OnCancel](#oncancel), volá se, že pokus o dialogové okno zavřete. Výchozí hodnota `OnOK` členská funkce se ověřit a aktualizace dat dialogového okna a zavřete dialogové okno s výsledkem IDOK a ve výchozím nastavení `OnCancel` členská funkce se zavřete dialogové okno s výsledkem IDCANCEL bez ověřování nebo aktualizaci data dialogového okna. Tyto funkce popisovač zpráv, změnit jejich chování můžete přepsat.

> [!NOTE]
> `PreTranslateMessage` se teď nazývá pro zpracování zpráv modální dialogové okno pole.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCControlLadenDialog#63](../../mfc/codesnippet/cpp/cdialog-class_2.cpp)]

##  <a name="enddialog"></a>  CDialog::EndDialog

Voláním této členské funkce k ukončení modální dialogové okno.

```
void EndDialog(int nResult);
```

### <a name="parameters"></a>Parametry

*Nvýsledek*<br/>
Obsahuje hodnotu, která má být vrácena z dialogových oken volajícímu `DoModal`.

### <a name="remarks"></a>Poznámky

Tato členská funkce vrátí *Nvýsledek* jako návratovou hodnotu `DoModal`. Je nutné použít `EndDialog` funkce, která se dokončí zpracování pokaždé, když se vytvoří modální dialogové okno.

Můžete volat `EndDialog` kdykoli, dokonce i v [OnInitDialog](#oninitdialog), v takovém případě by měl zavřete dialogové okno dříve, než se zobrazí nebo předtím, než je nastaven vstupní fokus.

`EndDialog` nemůžete ho zavřít dialogové okno okamžitě. Místo toho nastaví příznak, který přesměruje dialogové okno zavřete ihned poté, co vrátí aktuální obslužná rutina zprávy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCControlLadenDialog#64](../../mfc/codesnippet/cpp/cdialog-class_3.cpp)]

[!code-cpp[NVC_MFCControlLadenDialog#65](../../mfc/codesnippet/cpp/cdialog-class_4.cpp)]

##  <a name="getdefid"></a>  CDialog::GetDefID

Volání `GetDefID` členskou funkci k získání ID ovládacího prvku výchozí stisknutelných pro dialogové okno.

```
DWORD GetDefID() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota 32-bit ( `DWORD`). Pokud výchozí pushbutton má hodnotu ID, vyšší řád slova obsahuje DC_HASDEFID a nižší řád slova obsahuje hodnotu ID. Pokud výchozí pushbutton nemá hodnotu ID, vrácená hodnota je 0.

### <a name="remarks"></a>Poznámky

Obvykle se jedná tlačítko OK.

##  <a name="gotodlgctrl"></a>  CDialog::GotoDlgCtrl

Přesune fokus na prvku zadané v dialogovém okně.

```
void GotoDlgCtrl(CWnd* pWndCtrl);
```

### <a name="parameters"></a>Parametry

*pWndCtrl*<br/>
Identifikuje okna (ovládací prvek), které se má získat fokus.

### <a name="remarks"></a>Poznámky

Chcete-li získat ukazatel na ovládací prvek (podřízené okno) k předání jako *pWndCtrl*, volání `CWnd::GetDlgItem` členská funkce, které vrací ukazatel na [CWnd](../../mfc/reference/cwnd-class.md) objektu.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CWnd::GetDlgItem](../../mfc/reference/cwnd-class.md#getdlgitem).

##  <a name="initmodalindirect"></a>  CDialog::InitModalIndirect

Voláním této členské funkce pro inicializaci objektu modálního dialogového okna pomocí šablony dialogového okna, který vytvoříte v paměti.

```
BOOL InitModalIndirect(
    LPCDLGTEMPLATE lpDialogTemplate,
    CWnd* pParentWnd = NULL,
    void* lpDialogInit = NULL);


    BOOL InitModalIndirect(
    HGLOBAL hDialogTemplate,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*lpDialogTemplate*<br/>
Odkazuje na paměti, která obsahuje šablony dialog-box umožňuje vytvořit dialogové okno. Tato šablona je ve formě [DLGTEMPLATE](/windows/desktop/api/winuser/ns-winuser-dlgtemplate) struktury a ovládací prvek informace, jak je popsáno v sadě Windows SDK.

*hDialogTemplate*<br/>
Obsahuje popisovač do globální paměti, který obsahuje šablony dialog-box. Tato šablona je ve formě `DLGTEMPLATE` strukturu a data pro každý ovládací prvek v dialogovém okně.

*pParentWnd*<br/>
Odkazuje na objekt okna nadřazené nebo vlastník (typu [CWnd](../../mfc/reference/cwnd-class.md)), ke které patří objektu dialogového okna. Pokud je hodnota NULL, objektu dialogového okna nadřazené okno bude nastaveno na hlavní okno aplikace.

*lpDialogInit*<br/>
Odkazuje na prostředek DLGINIT.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byl vytvořen a inicializován úspěšně; objektu dialogového okna jinak 0.

### <a name="remarks"></a>Poznámky

K vytvoření modálního dialogového okna nepřímo, nejprve přidělit globální blok paměti a vyplnit šablony dialogového okna. Poté zavolejte prázdné `CDialog` konstruktor k vytvoření objektu dialogového okna. Pak zavolejte `InitModalIndirect` pro ukládání vašich popisovač do šablony dialogového okna v paměti. Dialogové okno Windows se vytvoří a zobrazí později, když [DoModal](#domodal) členská funkce je volána.

Dialogová okna, které obsahují ovládací prvky ActiveX vyžadují další informace, které jsou součástí DLGINIT prostředků.

##  <a name="mapdialogrect"></a>  CDialog::MapDialogRect

Volání za účelem převést jednotkách dialogového okna obdélník na obrazovce jednotky.

```
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*lprect –*<br/>
Odkazuje na [RECT](../../mfc/reference/rect-structure1.md) struktury nebo [crect –](../../atl-mfc-shared/reference/crect-class.md) objekt, který obsahuje – dialogové okno koordinuje má být převeden.

### <a name="remarks"></a>Poznámky

Jsou dialogového okna jednotky vyjádřený jako aktuální základní jednotku dialogového okna odvozený od průměrné šířku a výšku znaků v písmo použité pro text dialogového okna. Jedna jednotka na vodorovné čtvrtinu jednotku base šířky dialogového okna a jedna jednotka na svislé je 28 jedné jednotky základní výška dialogového okna.

`GetDialogBaseUnits` Vrátí informace o velikosti písma systému Windows, můžete ale zadat pro každou dialogové okno písmo při použití stylu DS_SETFONT v souboru definice prostředků. `MapDialogRect` Funkce Windows používá odpovídající písmo pro toto dialogové okno.

`MapDialogRect` Členskou funkci nahrazuje jednotky dialogového okna v *lprect –* s obrazovky jednotek (v pixelech) tak, že obdélník lze použít k vytvoření dialogového nebo umístit ovládací prvek v poli.

##  <a name="nextdlgctrl"></a>  CDialog::NextDlgCtrl

Přesune fokus na další ovládací prvek v dialogovém okně.

```
void NextDlgCtrl() const;
```

### <a name="remarks"></a>Poznámky

Pokud je fokus na poslední ovládací prvek v dialogovém okně, přesune se do první ovládací prvek.

##  <a name="oncancel"></a>  CDialog::OnCancel

Rozhraní volá tuto metodu, když uživatel klikne **zrušit** nebo stiskne klávesu ESC v modálním nebo nemodálním dialogovém okně.

```
virtual void OnCancel();
```

### <a name="remarks"></a>Poznámky

Potlačí tuto metodu k provádění akcí (například obnovení stará data) když uživatel zavře dialogové okno kliknutím **zrušit** nebo že jich dosáhli klávesu ESC. Výchozí hodnota ukončí modální dialogové okno voláním [EndDialog](#enddialog) a způsobí [DoModal](#domodal) vrátit IDCANCEL.

Pokud se rozhodnete implementovat **zrušit** tlačítko nemodálního dialogového okna, je nutné přepsat `OnCancel` metoda a volání [destroywindow –](../../mfc/reference/cwnd-class.md#destroywindow) dovnitř. Nevolejte metodu základní třídy, jelikož volá `EndDialog`, které bude skrytí dialogových oken, ale ne zničit.

> [!NOTE]
>  Nejde přepsat tuto metodu při použití `CFileDialog` v programu, který je zkompilován pod Windows XP. Další informace o `CFileDialog`, naleznete v tématu [cfiledialog – třída](../../mfc/reference/cfiledialog-class.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCControlLadenDialog#66](../../mfc/codesnippet/cpp/cdialog-class_5.cpp)]

##  <a name="oninitdialog"></a>  CDialog::OnInitDialog

Tato metoda je volána v reakci `WM_INITDIALOG` zprávy.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Návratová hodnota

Určuje, zda v aplikaci je nastaven vstupní fokus na některý ovládací prvky v dialogovém okně. Pokud `OnInitDialog` vrátí nenulovou hodnotu, Windows nastaví zaměření pro vstup do výchozího umístění první ovládací prvek v dialogovém okně. Aplikace může vrátit 0 pouze v případě, že je explicitně nastaveno zaměření pro vstup na některý ovládací prvky v dialogovém okně.

### <a name="remarks"></a>Poznámky

Windows odešle `WM_INITDIALOG` zprávy do dialogového okna průběhu [vytvořit](#create), [CreateIndirect](#createindirect), nebo [DoModal](#domodal) volání, ke kterým dochází, bezprostředně před dialogových oken Zobrazí se.

Potlačí tuto metodu, pokud chcete provést zvláštní zpracování při inicializaci dialogových oken. Přepsané verze nejprve volat základní třídy `OnInitDialog` ale ignorovat jeho návratovou hodnotu. Obvykle bude vracet `TRUE` z přepsané metody.

Volání Windows `OnInitDialog` funkce pomocí běžných postupu standardní globální – dialogové okno pro všechna dialogová okna knihovny Microsoft Foundation Class. Nevolá této funkce přes mapu zpráv, a proto není nutné položku mapování zpráv pro tuto metodu.

> [!NOTE]
> Nejde přepsat tuto metodu při použití `CFileDialog` v programu, který je kompilován v rámci Windows Vista nebo novější operační systémy. Další informace o změnách `CFileDialog` naleznete v části Windows Vista a novějších verzích [cfiledialog – třída](../../mfc/reference/cfiledialog-class.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCControlLadenDialog#67](../../mfc/codesnippet/cpp/cdialog-class_6.cpp)]

##  <a name="onok"></a>  CDialog::OnOK

Volá se, když uživatel klikne **OK** (tlačítko s ID IDOK).

```
virtual void OnOK();
```

### <a name="remarks"></a>Poznámky

Přepsáním této metody můžete provádět akce, když **OK** se aktivuje tlačítko. Pokud dialogové okno obsahuje ověřování automatické dat a serveru exchange, výchozí implementace této metody ověří dat dialogového okna a aktualizuje odpovídající proměnné ve vaší aplikaci.

Pokud se rozhodnete implementovat **OK** tlačítko nemodálního dialogového okna, je nutné přepsat `OnOK` metoda a volání [destroywindow –](../../mfc/reference/cwnd-class.md#destroywindow) dovnitř. Nevolejte metodu základní třídy, jelikož volá [EndDialog](#enddialog) které vytvoří dialogové okno neviditelné, ale nezničí ho.

> [!NOTE]
>  Nejde přepsat tuto metodu při použití `CFileDialog` v programu, který je zkompilován pod Windows XP. Další informace o `CFileDialog`, naleznete v tématu [cfiledialog – třída](../../mfc/reference/cfiledialog-class.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCControlLadenDialog#68](../../mfc/codesnippet/cpp/cdialog-class_7.cpp)]

##  <a name="onsetfont"></a>  CDialog::OnSetFont

Určuje písmo, které ovládací prvek dialogového okna bude používat při kreslení textu.

```
Virtual void OnSetFont(CFont* pFont);
```

### <a name="parameters"></a>Parametry

*pFont*<br/>
[in] Určuje ukazatel na písma, která se použije jako výchozí písmo pro všechny ovládací prvky v tomto dialogu.

### <a name="remarks"></a>Poznámky

Dialogové okno bude používat určené písmo jako výchozí pro všechny své ovládací prvky.

Editor dialogového okna obvykle nastaví písmo dialogového okna jako součást prostředku šablony dialogového okna.

> [!NOTE]
> Nejde přepsat tuto metodu při použití `CFileDialog` v programu, který je kompilován v rámci Windows Vista nebo novější operační systémy. Další informace o změnách `CFileDialog` naleznete v části Windows Vista a novějších verzích [cfiledialog – třída](../../mfc/reference/cfiledialog-class.md).

##  <a name="prevdlgctrl"></a>  CDialog::PrevDlgCtrl

Nastaví fokus na předchozí ovládací prvek v dialogovém okně.

```
void PrevDlgCtrl() const;
```

### <a name="remarks"></a>Poznámky

Pokud je fokus na první prvek v dialogovém okně, jeho přejde na poslední ovládací prvek v poli.

##  <a name="setdefid"></a>  CDialog::SetDefID

Změní výchozí ovládací prvek stisknutelných pro dialogové okno.

```
void SetDefID(UINT nID);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Určuje ID stisknutelných ovládacího prvku, který se stane výchozí.

##  <a name="sethelpid"></a>  CDialog::SetHelpID

Nastaví ID kontextové nápovědy pro dialogové okno.

```
void SetHelpID(UINT nIDR);
```

### <a name="parameters"></a>Parametry

*nIDR*<br/>
Určuje ID kontextové nápovědy.

## <a name="see-also"></a>Viz také

[Ukázka DLGCBR32 knihovny MFC](../../visual-cpp-samples.md)<br/>
[Ukázky knihovny MFC DLGTEMPL](../../visual-cpp-samples.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)

