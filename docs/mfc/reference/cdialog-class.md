---
title: CDialog – třída
ms.date: 09/07/2019
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
ms.openlocfilehash: cad762f426012d9d1931b96d54d8a53c9bab465d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375650"
---
# <a name="cdialog-class"></a>CDialog – třída

Základní třída používaná pro zobrazení dialogových oken na obrazovce.

## <a name="syntax"></a>Syntaxe

```
class CDialog : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CDialog::CDialog](#cdialog)|Vytvoří `CDialog` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CDialog::Vytvořit](#create)|Inicializuje `CDialog` objekt. Vytvoří nemodální dialogové okno a `CDialog` připojí ho k objektu.|
|[CDialog::Vytvořitnepřímá](#createindirect)|Vytvoří nemodální dialogové okno ze šablony dialogového okna v paměti (nikoli na základě prostředků).|
|[CDialog::DoModální](#domodal)|Zavolá modální dialogové okno a vrátí po dokončení.|
|[CDialog::EndDialog](#enddialog)|Zavře modální dialogové okno.|
|[CDialog::GetDefID](#getdefid)|Získá ID výchozí hotlačítka ovládacího prvku pro dialogové okno.|
|[CDialog::GotoDlgCtrl](#gotodlgctrl)|Přesune fokus na zadaný ovládací prvek dialogového okna v dialogovém okně.|
|[CDialog::InitModalIndirect](#initmodalindirect)|Vytvoří modální dialogové okno ze šablony dialogového okna v paměti (nikoli na základě prostředků). Parametry jsou uloženy, `DoModal` dokud není volána funkce.|
|[CDialog::MapDialogRect](#mapdialogrect)|Převede jednotky dialogového okna obdélníku na jednotky obrazovky.|
|[CDialog::NextDlgCtrl](#nextdlgctrl)|Přesune fokus na další ovládací prvek dialogového okna v dialogovém okně.|
|[CDialog::OnInitDialog](#oninitdialog)|Přepsání pro rozšíření inicializace dialogového okna.|
|[CDialog::OnSetFont](#onsetfont)|Přepsáním určete písmo, které má ovládací prvek dialogového okna použít při natahování textu.|
|[CDialog::PrevDlgCtrl](#prevdlgctrl)|Přesune fokus na předchozí ovládací prvek dialogového okna v dialogovém okně.|
|[CDialog::SetDefID](#setdefid)|Změní výchozí ovládací prvek tlačítka pro dialogové okno na zadané tlačítko.|
|[CDialog::SetHelpID](#sethelpid)|Nastaví kontextové ID nápovědy pro dialogové okno.|

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CDialog::OnCancel](#oncancel)|Přepsáním provedete akci tlačítka Storno nebo klávesy ESC. Výchozí nastavení zavře dialogové `DoModal` okno a vrátí hodnotu IDCANCEL.|
|[CDialog::OnOK](#onok)|Přepsáním provedete akci tlačítka OK v modálním dialogovém okně. Výchozí nastavení zavře dialogové `DoModal` okno a vrátí Hodnotu IDOK.|

## <a name="remarks"></a>Poznámky

Dialogová okna jsou dvou typů: modální a nemodální. Před pokračováním aplikace musí uživatel zavřít modální dialogové okno. Nemodální dialogové okno umožňuje uživateli zobrazit dialogové okno a vrátit se k jiné úloze bez zrušení nebo odebrání dialogového okna.

Objekt `CDialog` je kombinací šablony dialogu a `CDialog`odvozené třídy. Pomocí editoru dialogů vytvořte šablonu dialogu a uložte ji do prostředku a `CDialog`potom pomocí Průvodce přidáním třídy vytvořte třídu odvozenou z aplikace .

Dialogové okno, stejně jako jakékoli jiné okno, přijímá zprávy ze systému Windows. V dialogovém okně se obzvláště zajímáte o zpracování oznámení z ovládacích prvků dialogového okna, protože tak uživatel pracuje s vaším dialogovým oknem. Pomocí [Průvodce třídou](mfc-class-wizard.md) vyberte, které zprávy chcete zpracovat, a přidá příslušné položky mapy zpráv a členské funkce obslužné rutiny zpráv do třídy za vás. Potřebujete pouze napsat kód specifický pro aplikaci v členských funkcích obslužné rutiny.

Pokud chcete, můžete vždy psát položky mapy zpráv a členské funkce ručně.

Ve všech, kromě nejbanálnějšího dialogového okna, přidáte členské proměnné do odvozené třídy dialogů, abyste ukládali data zadaná uživatelem do ovládacích prvků dialogového okna nebo aby uživatel i zobrazili data. Průvodce přidáním proměnných můžete použít k vytvoření členských proměnných a jejich přidružení k ovládacím prvkům. Současně zvolíte typ proměnné a přípustný rozsah hodnot pro každou proměnnou. Průvodce kódem přidá členské proměnné do odvozené třídy dialogů.

Mapování dat je generováno pro automatické zpracování výměny dat mezi členskými proměnnými a ovládacími prvky dialogového okna. Mapování dat poskytuje funkce, které inicializují ovládací prvky v dialogovém okně se správnými hodnotami, načítají data a ověřují data.

Chcete-li vytvořit modální dialogové okno, vytvořte objekt v zásobníku pomocí `DoModal` konstruktoru pro odvozenou třídu dialogů a pak volejte k vytvoření dialogového okna a jeho ovládacích prvků. Pokud chcete vytvořit nemodální `Create` dialog, volání v konstruktoru dialogového okna třídy.

Můžete také vytvořit šablonu v paměti pomocí datové struktury [DLGTEMPLATE,](/windows/win32/api/winuser/ns-winuser-dlgtemplate) jak je popsáno v sadě Windows SDK. Po vytvoření `CDialog` objektu volejte [CreateIndirect](#createindirect) k vytvoření nemodálního dialogového okna nebo volání [InitModalIndirect](#initmodalindirect) a [DoModal](#domodal) k vytvoření modálního dialogového okna.

Mapování dat pro výměnu a ověření je `CWnd::DoDataExchange` zapsáno v přepsání, které je přidáno do nové třídy dialogu. Další informace o funkci `CWnd` výměny a ověřování naleznete v členské funkci [DoDataExchange.](../../mfc/reference/cwnd-class.md#dodataexchange)

Programátor a rozhraní volání `DoDataExchange` nepřímo prostřednictvím volání [CWnd::UpdateData](../../mfc/reference/cwnd-class.md#updatedata).

Rozhraní framework `UpdateData` volá, když uživatel klepne na tlačítko OK zavřít modální dialogové okno. (Data se nenačtou, pokud klepnete na tlačítko Storno.) Výchozí implementace [OnInitDialog](#oninitdialog) také `UpdateData` volá nastavit počáteční hodnoty ovládacích prvků. Obvykle přepsat `OnInitDialog` další inicializaci ovládacích prvků. `OnInitDialog`je volána po vytvoření všech dialogových ovládacích prvků a těsně před zobrazením dialogového okna.

Můžete volat `CWnd::UpdateData` kdykoli během provádění modálního nebo nemodálního dialogového okna.

Pokud vyvinete dialogové okno ručně, přidáte potřebné členské proměnné do odvozené třídy dialogového okna sami a přidáte členské funkce pro nastavení nebo získání těchto hodnot.

Modální dialogové okno se automaticky zavře, když uživatel stiskne `EndDialog` tlačítka OK nebo Storno nebo když váš kód volá členská funkce.

Při implementaci nemodální dialogové okno, `OnCancel` vždy přepsat `DestroyWindow` členské funkce a volání z něj. Nevolejte základní třídu `CDialog::OnCancel`, protože `EndDialog`volá , což způsobí, že dialogové okno bude neviditelné, ale nezničí ho. Měli byste také `PostNcDestroy` přepsat pro nemodální dialogová okna, abyste **je**odstranili , protože nemodální dialogová okna jsou obvykle přidělena **novými**. Modální dialogová okna jsou obvykle konstruovány na snímku a nepotřebují `PostNcDestroy` vyčištění.

Další informace `CDialog`naleznete v [tématu Dialogová okna](../../mfc/dialog-boxes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="cdialogcdialog"></a><a name="cdialog"></a>CDialog::CDialog

Chcete-li vytvořit modální dialogové okno založené na prostředku, volejte buď veřejnou formu konstruktoru.

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
Obsahuje řetězec s nulovým ukončením, který je názvem prostředku šablony dialogového okna.

*nIDŠablona*<br/>
Obsahuje id číslo prostředku šablony dialogového okna.

*pParentWnd*<br/>
Odkazuje na nadřazený objekt okna nebo objekt vlastníka (typu [CWnd),](../../mfc/reference/cwnd-class.md)ke kterému patří objekt dialogového okna. Pokud je null, nadřazené okno objektu dialogu je nastaveno na hlavní okno aplikace.

### <a name="remarks"></a>Poznámky

Jedna forma konstruktoru poskytuje přístup k prostředku dialogu podle názvu šablony. Druhý konstruktor poskytuje přístup podle čísla ID šablony, obvykle s **předponou IDD_** (například IDD_DIALOG1).

Chcete-li vytvořit modální dialogové okno ze šablony v paměti, nejprve vyvolat bezparametrický, chráněný konstruktor a pak volat `InitModalIndirect`.

Po vytvoření modálního dialogového okna s `DoModal`jednou z výše uvedených metod volejte .

Chcete-li vytvořit nemodální dialogové okno, použijte chráněnou formu konstruktoru. `CDialog` Konstruktor je chráněn, protože je nutné odvodit vlastní třídu dialogového okna k implementaci nemodální dialogové okno. Konstrukce nemodálnídialogového okna je dvoustupňový proces. Nejprve volání konstruktoru; potom volání `Create` členské funkce k vytvoření dialogového okna `CreateIndirect` založeného na prostředcích nebo volání k vytvoření dialogového okna ze šablony v paměti.

## <a name="cdialogcreate"></a><a name="create"></a>CDialog::Vytvořit

Volání `Create` k vytvoření nemodální dialogové okno pomocí dialogového okna šablony z prostředku.

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
Obsahuje řetězec s nulovým ukončením, který je názvem prostředku šablony dialogového okna.

*pParentWnd*<br/>
Odkazuje na nadřazený objekt okna (typu [CWnd),](../../mfc/reference/cwnd-class.md)ke kterému patří objekt dialogového okna. Pokud je null, nadřazené okno objektu dialogu je nastaveno na hlavní okno aplikace.

*nIDŠablona*<br/>
Obsahuje id číslo prostředku šablony dialogového okna.

### <a name="return-value"></a>Návratová hodnota

Oba formuláře vrátí nenulovou, pokud bylo vytvoření dialogového okna a inicializace dialogového okna úspěšné. jinak 0.

### <a name="remarks"></a>Poznámky

Můžete umístit volání `Create` uvnitř konstruktoru nebo volat po vyvolání konstruktoru.

Pro přístup `Create` k prostředku šablony dialogového okna buď název šablony nebo id číslo šablony (například IDD_DIALOG1).

Pro oba formuláře předavěte ukazatel nadřazeného objektu okna. Pokud *pParentWnd* je NULL, dialogové okno bude vytvořen s jeho nadřazené nebo vlastníkovi okna nastavena na hlavní okno aplikace.

Členská `Create` funkce se vrátí ihned po jeho otevření dialogového okna.

Pokud se dialogové okno objeví při vytvoření nadřazeného okna, použijte styl WS_VISIBLE v šabloně dialogového okna. V opačném případě `ShowWindow`je nutné volat . Další styly dialogových oken a jejich aplikace naleznete v části Struktura [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) v sadě Windows SDK a [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) v *referenční příručce knihovny MFC*.

Pomocí `CWnd::DestroyWindow` této funkce můžete zničit dialogové `Create` okno vytvořené funkcí.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCControlLadenDialog#62](../../mfc/codesnippet/cpp/cdialog-class_1.cpp)]

## <a name="cdialogcreateindirect"></a><a name="createindirect"></a>CDialog::Vytvořitnepřímá

Voláním této členské funkce vytvořte nemodální dialogové okno ze šablony dialogového okna v paměti.

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
Odkazuje na paměť, která obsahuje šablonu dialogového okna použitou k vytvoření dialogového okna. Tato šablona je ve formě struktury [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) a informace o řízení, jak je popsáno v sadě Windows SDK.

*pParentWnd*<br/>
Odkazuje na nadřazený objekt okna objektu dialogového okna (typu [CWnd).](../../mfc/reference/cwnd-class.md) Pokud je null, nadřazené okno objektu dialogu je nastaveno na hlavní okno aplikace.

*lpDialogInit*<br/>
Odkazuje na prostředek DLGINIT.

*hDialogTemplate*<br/>
Obsahuje popisovač globální paměti obsahující šablonu dialogového okna. Tato šablona je ve `DLGTEMPLATE` formě struktury a dat pro každý ovládací prvek v dialogovém okně.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud bylo dialogové okno úspěšně vytvořeno a inicializováno; jinak 0.

### <a name="remarks"></a>Poznámky

Členská `CreateIndirect` funkce se vrátí ihned po jeho otevření dialogového okna.

Pokud se dialogové okno objeví při vytvoření nadřazeného okna, použijte styl WS_VISIBLE v šabloně dialogového okna. V opačném případě `ShowWindow` je nutné volat, aby se zobrazila. Další informace o tom, jak můžete určit další styly dialogových oken v šabloně, naleznete v části Struktura [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) v sadě Windows SDK.

Pomocí `CWnd::DestroyWindow` této funkce můžete zničit dialogové `CreateIndirect` okno vytvořené funkcí.

Dialogová okna, která obsahují ovládací prvky ActiveX, vyžadují další informace poskytované v prostředku DLGINIT.

## <a name="cdialogdomodal"></a><a name="domodal"></a>CDialog::DoModální

Volání této členské funkce vyvolat modální dialogové okno a vrátit výsledek dialogového okna po dokončení.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota **int,** která určuje hodnotu parametru *nResult,* který byl předán členské funkci [CDialog::EndDialog,](#enddialog) která slouží k zavření dialogového okna. Vrácená hodnota je -1, pokud funkce nemohla vytvořit dialogové okno, nebo IDABORT, pokud došlo k jiné chybě, v takovém případě bude výstupní okno obsahovat informace o chybě z [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Poznámky

Tato členská funkce zpracovává veškerou interakci s uživatelem, když je dialogové okno aktivní. To je to, co dělá dialogové okno modální; to znamená, že uživatel nemůže pracovat s jinými okny, dokud není dialogové okno uzavřeno.

Pokud uživatel klepne na jedno z tlačítek v dialogovém okně, například OK nebo Cancel, je volána členská funkce obslužné rutiny zprávy, [například OnOK](#onok) nebo [OnCancel](#oncancel), k pokusu o zavření dialogového okna. Výchozí `OnOK` členská funkce ověří a aktualizuje data dialogového okna a zavře dialogové `OnCancel` okno s výsledkem IDOK a výchozí členská funkce zavře dialogové okno s výsledkem IDCANCEL bez ověření nebo aktualizace dat dialogového okna. Můžete přepsat tyto funkce obslužné rutiny zpráv změnit jejich chování.

> [!NOTE]
> `PreTranslateMessage`nyní volána pro zpracování modální dialogové okno zprávy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCControlLadenDialog#63](../../mfc/codesnippet/cpp/cdialog-class_2.cpp)]

## <a name="cdialogenddialog"></a><a name="enddialog"></a>CDialog::EndDialog

Volání této členské funkce k ukončení modální dialogové okno.

```
void EndDialog(int nResult);
```

### <a name="parameters"></a>Parametry

*nVýsledek*<br/>
Obsahuje hodnotu, která má být vrácena `DoModal`z dialogového okna volajícímu aplikace .

### <a name="remarks"></a>Poznámky

Tato členská funkce vrátí *hodnotu nResult* jako vrácenou hodnotu aplikace `DoModal`. `EndDialog` Tuto funkci je nutné použít k dokončení zpracování při každém vytvoření modálního dialogového okna.

Můžete volat `EndDialog` kdykoli, a to i v [OnInitDialog](#oninitdialog), v takovém případě byste měli zavřít dialogové okno před jeho zobrazením nebo před nastavením zaostření vstupu.

`EndDialog`nezavře dialogové okno okamžitě. Místo toho nastaví příznak, který přesměruje dialogové okno zavřít, jakmile aktuální obslužná rutina zprávy vrátí.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCControlLadenDialog#64](../../mfc/codesnippet/cpp/cdialog-class_3.cpp)]

[!code-cpp[NVC_MFCControlLadenDialog#65](../../mfc/codesnippet/cpp/cdialog-class_4.cpp)]

## <a name="cdialoggetdefid"></a><a name="getdefid"></a>CDialog::GetDefID

Volání `GetDefID` majestátně získat ID výchozího ovládacího prvku tlačítka pro dialogové okno.

```
DWORD GetDefID() const;
```

### <a name="return-value"></a>Návratová hodnota

32bitová hodnota `DWORD`( ). Pokud má výchozí tlačítko hodnotu ID, slovo vyššího řádu obsahuje DC_HASDEFID a slovo nižšího řádu obsahuje hodnotu ID. Pokud výchozí tlačítko nemá hodnotu ID, vrácená hodnota je 0.

### <a name="remarks"></a>Poznámky

Obvykle se jedná o tlačítko OK.

## <a name="cdialoggotodlgctrl"></a><a name="gotodlgctrl"></a>CDialog::GotoDlgCtrl

Přesune fokus na zadaný ovládací prvek v dialogovém okně.

```
void GotoDlgCtrl(CWnd* pWndCtrl);
```

### <a name="parameters"></a>Parametry

*pWndCtrl*<br/>
Identifikuje okno (ovládací prvek), které má být fokusováno.

### <a name="remarks"></a>Poznámky

Chcete-li získat ukazatel na ovládací prvek (podřízené okno) `CWnd::GetDlgItem` předat jako *pWndCtrl*, volání členské funkce, která vrátí ukazatel na [cWnd](../../mfc/reference/cwnd-class.md) objektu.

### <a name="example"></a>Příklad

  Viz příklad pro [CWnd::GetDlgItem](../../mfc/reference/cwnd-class.md#getdlgitem).

## <a name="cdialoginitmodalindirect"></a><a name="initmodalindirect"></a>CDialog::InitModalIndirect

Volání této členské funkce k inicializaci objektu modálního dialogu pomocí šablony dialogového okna, kterou vytvoříte v paměti.

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
Odkazuje na paměť, která obsahuje šablonu dialogového okna použitou k vytvoření dialogového okna. Tato šablona je ve formě struktury [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) a informace o řízení, jak je popsáno v sadě Windows SDK.

*hDialogTemplate*<br/>
Obsahuje popisovač globální paměti obsahující šablonu dialogového okna. Tato šablona je ve `DLGTEMPLATE` formě struktury a dat pro každý ovládací prvek v dialogovém okně.

*pParentWnd*<br/>
Odkazuje na nadřazený objekt okna nebo objekt vlastníka (typu [CWnd),](../../mfc/reference/cwnd-class.md)ke kterému patří objekt dialogového okna. Pokud je null, nadřazené okno objektu dialogu je nastaveno na hlavní okno aplikace.

*lpDialogInit*<br/>
Odkazuje na prostředek DLGINIT.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byl objekt dialogového okna úspěšně vytvořen a inicializován; jinak 0.

### <a name="remarks"></a>Poznámky

Chcete-li vytvořit modální dialogové okno nepřímo, nejprve přidělte globální blok paměti a vyplňte jej šablonou dialogového okna. Potom volání `CDialog` prázdné konstruktoru k vytvoření dialogového okna objektu. Dále volání `InitModalIndirect` pro uložení popisovače do šablony dialogového okna v paměti. Dialogové okno systému Windows je vytvořeno a zobrazeno později při volání členské funkce [DoModal.](#domodal)

Dialogová okna, která obsahují ovládací prvky ActiveX, vyžadují další informace poskytované v prostředku DLGINIT.

## <a name="cdialogmapdialogrect"></a><a name="mapdialogrect"></a>CDialog::MapDialogRect

Volání převést dialogové okno jednotky obdélníku na obrazovku jednotky.

```
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Odkazuje na [rect](/windows/win32/api/windef/ns-windef-rect) strukturu nebo [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt, který obsahuje dialogové okno souřadnice, které mají být převedeny.

### <a name="remarks"></a>Poznámky

Jednotky dialogového okna jsou uvedeny jako aktuální základní jednotka dialogového okna odvozená od průměrné šířky a výšky znaků v písmu použitém pro text dialogového okna. Jedna vodorovná jednotka je jedna čtvrtina jednotky základní šířky dialogového okna a jedna svislá jednotka je jedna osmina základní výškové jednotky dialogového okna.

Funkce `GetDialogBaseUnits` systému Windows vrátí informace o velikosti systémového písma, ale pokud použijete styl DS_SETFONT v souboru definice prostředku, můžete pro každé dialogové okno určit jiné písmo. Funkce `MapDialogRect` systému Windows používá příslušné písmo pro toto dialogové okno.

Členská `MapDialogRect` funkce nahradí jednotky dialogového okna v *lpRect* jednotkami obrazovky (pixely), takže obdélník lze použít k vytvoření dialogového okna nebo umístění ovládacího prvku v poli.

## <a name="cdialognextdlgctrl"></a><a name="nextdlgctrl"></a>CDialog::NextDlgCtrl

Přesune fokus na další ovládací prvek v dialogovém okně.

```
void NextDlgCtrl() const;
```

### <a name="remarks"></a>Poznámky

Pokud je fokus na posledním ovládacím prvku v dialogovém okně, přesune se na první ovládací prvek.

## <a name="cdialogoncancel"></a><a name="oncancel"></a>CDialog::OnCancel

Framework volá tuto metodu, když uživatel klepne na **tlačítko Cancel** nebo stiskne klávesu ESC v modálním nebo nemodálním dialogovém okně.

```
virtual void OnCancel();
```

### <a name="remarks"></a>Poznámky

Přepište tuto metodu k provedení akcí (například obnovení starých dat), když uživatel zavře dialogové okno klepnutím na **tlačítko Storno** nebo stisknutím klávesy ESC. Výchozí zavře modální dialogové okno voláním [EndDialog](#enddialog) a způsobuje [DoModal](#domodal) vrátit IDCANCEL.

Pokud implementujete **tlačítko Storno** v nemodálním dialogovém okně, musíte přepsat metodu `OnCancel` a volat [DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) uvnitř. Nevolejte metodu základní třídy, `EndDialog`protože volá , což způsobí, že dialogové okno bude neviditelné, ale nezničí ho.

> [!NOTE]
> Tuto metodu nelze přepsat, `CFileDialog` pokud použijete objekt v programu, který je kompilován v systému Windows XP. Další informace `CFileDialog`naleznete v [tématu CFileDialog Class](../../mfc/reference/cfiledialog-class.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCControlLadenDialog#66](../../mfc/codesnippet/cpp/cdialog-class_5.cpp)]

## <a name="cdialogoninitdialog"></a><a name="oninitdialog"></a>CDialog::OnInitDialog

Tato metoda je volána `WM_INITDIALOG` jako odpověď na zprávu.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Návratová hodnota

Určuje, zda aplikace nastavila vstupní fokus na jeden z ovládacích prvků v dialogovém okně. Pokud `OnInitDialog` vrátí nenulovou hodnotu, systém Windows nastaví vstupní fokus na výchozí umístění, což je první ovládací prvek v dialogovém okně. Aplikace může vrátit 0 pouze v případě, že explicitně nastavila vstupní fokus na jeden z ovládacích prvků v dialogovém okně.

### <a name="remarks"></a>Poznámky

Systém Windows `WM_INITDIALOG` odešle zprávu do dialogového okna během volání [Vytvořit](#create), [Vytvořitnepřímý](#createindirect)nebo [DoModal,](#domodal) ke kterým dojde bezprostředně před zobrazením dialogového okna.

Přepište tuto metodu, pokud chcete provést speciální zpracování při inicializace dialogového okna. V potlačené verzi nejprve `OnInitDialog` volat základní třídy, ale ignorovat jeho vrácená hodnota. Obvykle se vrátíte `TRUE` z přepsané metody.

Systém Windows `OnInitDialog` volá funkci pomocí standardního globálního dialogového okna, který je společný pro všechna dialogová okna knihovny tříd aplikace Microsoft Foundation. Nevolá tuto funkci prostřednictvím mapy zpráv, a proto nepotřebujete položku mapy zpráv pro tuto metodu.

> [!NOTE]
> Tuto metodu `CFileDialog` nelze přepsat, pokud používáte objekt v programu, který je kompilován v operačních systémech Windows Vista nebo novějších. Další informace o `CFileDialog` změnách v systému Windows Vista a novějších naleznete v [tématu CFileDialog Class](../../mfc/reference/cfiledialog-class.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCControlLadenDialog#67](../../mfc/codesnippet/cpp/cdialog-class_6.cpp)]

## <a name="cdialogonok"></a><a name="onok"></a>CDialog::OnOK

Volána, když uživatel klikne na tlačítko **OK** (tlačítko s ID IDOK).

```
virtual void OnOK();
```

### <a name="remarks"></a>Poznámky

Přepište tuto metodu a proveďte akce při aktivaci tlačítka **OK.** Pokud dialogové okno obsahuje automatické ověření dat a výměnu, výchozí implementace této metody ověří data dialogového okna a aktualizuje příslušné proměnné v aplikaci.

Pokud implementujete tlačítko **OK** v nemodálním `OnOK` dialogovém okně, musíte přepsat metodu a volat [DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) uvnitř. Nevolejte metodu základní třídy, protože volá [EndDialog,](#enddialog) který umožňuje dialogové okno neviditelné, ale nezničí jej.

> [!NOTE]
> Tuto metodu nelze přepsat, `CFileDialog` pokud použijete objekt v programu, který je kompilován v systému Windows XP. Další informace `CFileDialog`naleznete v [tématu CFileDialog Class](../../mfc/reference/cfiledialog-class.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCControlLadenDialog#68](../../mfc/codesnippet/cpp/cdialog-class_7.cpp)]

## <a name="cdialogonsetfont"></a><a name="onsetfont"></a>CDialog::OnSetFont

Určuje písmo, které bude ovládací prvek dialogového okna používat při kreslení textu.

```
Virtual void OnSetFont(CFont* pFont);
```

### <a name="parameters"></a>Parametry

*písmo*<br/>
[v] Určuje ukazatel na písmo, které bude použito jako výchozí písmo pro všechny ovládací prvky v tomto dialogovém okně.

### <a name="remarks"></a>Poznámky

Dialogové okno použije zadané písmo jako výchozí pro všechny ovládací prvky.

Editor dialogů obvykle nastaví písmo dialogového okna jako součást prostředku šablony dialogového okna.

> [!NOTE]
> Tuto metodu `CFileDialog` nelze přepsat, pokud používáte objekt v programu, který je kompilován v operačních systémech Windows Vista nebo novějších. Další informace o `CFileDialog` změnách v systému Windows Vista a novějších naleznete v [tématu CFileDialog Class](../../mfc/reference/cfiledialog-class.md).

## <a name="cdialogprevdlgctrl"></a><a name="prevdlgctrl"></a>CDialog::PrevDlgCtrl

Nastaví fokus na předchozí ovládací prvek v dialogovém okně.

```
void PrevDlgCtrl() const;
```

### <a name="remarks"></a>Poznámky

Pokud je fokus na prvním ovládacím prvku v dialogovém okně, přesune se na poslední ovládací prvek v poli.

## <a name="cdialogsetdefid"></a><a name="setdefid"></a>CDialog::SetDefID

Změní výchozí ovládací prvek tlačítka pro dialogové okno.

```
void SetDefID(UINT nID);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
Určuje ID ovládacího prvku tlačítka, který se stane výchozím.

## <a name="cdialogsethelpid"></a><a name="sethelpid"></a>CDialog::SetHelpID

Nastaví kontextové ID nápovědy pro dialogové okno.

```
void SetHelpID(UINT nIDR);
```

### <a name="parameters"></a>Parametry

*nIDR*<br/>
Určuje id nápovědy pro kontext.

## <a name="see-also"></a>Viz také

[Ukázka knihovny MFC DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[Ukázka knihovny MFC DLGTEMPL](../../overview/visual-cpp-samples.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
