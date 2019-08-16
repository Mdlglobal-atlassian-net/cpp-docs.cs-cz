---
title: CDialog – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: d9969b7dd41dc7a67e21bb2735b1d716bd988d07
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506878"
---
# <a name="cdialog-class"></a>CDialog – třída

Základní třída používaná k zobrazení dialogových oken na obrazovce.

## <a name="syntax"></a>Syntaxe

```
class CDialog : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CDialog::CDialog](#cdialog)|`CDialog` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CDialog:: Create](#create)|`CDialog` Inicializuje objekt. Vytvoří nemodální dialogové okno a připojí ho k `CDialog` objektu.|
|[CDialog::CreateIndirect](#createindirect)|Vytvoří nemodální dialogové okno ze šablony dialogového okna v paměti (ne založené na prostředku).|
|[CDialog::DoModal](#domodal)|Vyvolá modální dialogové okno a vrátí hodnotu po dokončení.|
|[CDialog:: EndDialog](#enddialog)|Zavře modální dialogové okno.|
|[CDialog:: GetDefID](#getdefid)|Získá ID výchozího ovládacího prvku (pushbutton) pro dialogové okno.|
|[CDialog::GotoDlgCtrl](#gotodlgctrl)|Přesune fokus na určený ovládací prvek dialogového okna v dialogovém okně.|
|[CDialog::InitModalIndirect](#initmodalindirect)|Vytvoří modální dialogové okno ze šablony dialogového okna v paměti (ne založené na prostředku). Parametry jsou uloženy, dokud není volána `DoModal` funkce.|
|[CDialog::MapDialogRect](#mapdialogrect)|Převede jednotky dialogového okna obdélníku na jednotky obrazovky.|
|[CDialog::NextDlgCtrl](#nextdlgctrl)|Přesune fokus na další ovládací prvek dialogového okna v dialogovém okně.|
|[CDialog::OnInitDialog](#oninitdialog)|Přepište pro rozšíření Inicializace dialogového okna.|
|[CDialog::OnSetFont](#onsetfont)|Přepsáním můžete určit písmo, které ovládací prvek dialogového okna použije při kreslení textu.|
|[CDialog::PrevDlgCtrl](#prevdlgctrl)|Přesune fokus na předchozí ovládací prvek dialogového okna v dialogovém okně.|
|[CDialog:: SetDefID](#setdefid)|Změní výchozí ovládací prvek (pushbutton) pro dialogové okno na zadaný (pushbutton).|
|[CDialog:: SetHelpID](#sethelpid)|Nastaví kontextově závislé ID kontextové Nápověda pro dialog.|

### <a name="protected-methods"></a>Chráněné metody

|Name|Popis|
|----------|-----------------|
|[CDialog::OnCancel](#oncancel)|Přepsáním provedete akci tlačítka Storno nebo klávesy ESC. Výchozí nastavení zavře dialogové okno a `DoModal` vrátí IDCANCEL.|
|[CDialog::OnOK](#onok)|Přepište k provedení akce tlačítko OK v modálním dialogovém okně. Výchozí nastavení zavře dialogové okno a `DoModal` vrátí IDOK.|

## <a name="remarks"></a>Poznámky

Dialogová okna jsou dvou typů: modální a nemodální. Modální dialogové okno musí být před pokračováním aplikace zavřeno uživatelem. Nemodální dialogové okno umožňuje uživateli zobrazit dialogové okno a vrátit se k jiné úloze bez zrušení nebo odebrání dialogového okna.

Objekt je kombinací šablony dialogového okna `CDialog`a třídy odvozené od třídy. `CDialog` Pomocí editoru dialogových oken vytvořte šablonu dialogového okna a uložte ji do prostředku, pak pomocí Průvodce přidáním třídy vytvořte třídu odvozenou z `CDialog`.

Dialogové okno, podobně jako jakékoli jiné okno, přijímá zprávy ze systému Windows. V dialogovém okně máte zejména zájem o zpracování oznamovacích zpráv z ovládacích prvků v dialogovém okně, protože to je způsob, jakým uživatel komunikuje s vaším dialogovým oknem. Pomocí okno Vlastnosti vyberte, které zprávy chcete zpracovat, a přidejte příslušné položky mapy zpráv a členské funkce obslužné rutiny zpráv do třídy za vás. Stačí pouze psát kód specifický pro aplikaci ve funkcích členů obslužné rutiny.

Pokud dáváte přednost, můžete vždy napsat položky a členské funkce mapy zpráv ručně.

Ve všech, ale nejvíce triviálních dialogových oknech můžete přidat členské proměnné do odvozené třídy dialogu pro ukládání dat zadaných v ovládacích prvcích dialogového okna uživatelem nebo pro zobrazení dat pro uživatele. Průvodce přidáním proměnné lze použít k vytvoření proměnných členů a jejich přidružení k ovládacím prvkům. Ve stejnou chvíli zvolíte typ proměnné a přípustný rozsah hodnot pro každou proměnnou. Průvodce kódem přidá proměnné členů do odvozené třídy dialogu.

Je generována mapa dat pro automatické zpracování výměny dat mezi proměnnými členů a ovládacími prvky dialogového okna. Mapa dat poskytuje funkce, které inicializují ovládací prvky v dialogovém okně se správnými hodnotami, načítají data a ověřují data.

Chcete-li vytvořit modální dialogové okno, Sestavte objekt v zásobníku pomocí konstruktoru pro odvozenou třídu dialogového okna a potom `DoModal` zavolejte k vytvoření dialogového okna a jeho ovládacích prvků. Pokud chcete vytvořit nemodální dialogové okno, zavolejte `Create` v konstruktoru vaší třídy dialogu.

Můžete také vytvořit šablonu v paměti pomocí datové struktury [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) , jak je popsáno v Windows SDK. Po vytvoření [](#domodal) [](#initmodalindirect) [](#createindirect) objektu zavolejte CreateIndirect k vytvoření nemodálního dialogového okna nebo zavolejte InitModalIndirect a DoModal pro vytvoření modálního dialogového okna. `CDialog`

Mapování dat Exchange a ověření je napsáno v přepsání `CWnd::DoDataExchange` , které je přidáno do nové třídy dialogového okna. Další informace [](../../mfc/reference/cwnd-class.md#dodataexchange) o funkci Exchange a `CWnd` ověřování najdete v části členské funkce DoDataExchange v tématu.

Programátor i rozhraní volají `DoDataExchange` nepřímo prostřednictvím volání [CWnd:: UpdateData](../../mfc/reference/cwnd-class.md#updatedata).

Rozhraní volá `UpdateData` , když uživatel klikne na tlačítko OK, aby zavřel modální dialogové okno. (Po kliknutí na tlačítko Storno nejsou data načtena.) Výchozí implementace [OnInitDialog](#oninitdialog) také volá `UpdateData` k nastavení počátečních hodnot ovládacích prvků. Obvykle přepíšete `OnInitDialog` pro další inicializaci ovládacích prvků. `OnInitDialog`je volána po vytvoření všech ovládacích prvků dialogového okna a těsně před zobrazením dialogového okna.

Můžete zavolat `CWnd::UpdateData` kdykoli během provádění modálního nebo nemodálního dialogového okna.

Pokud vytvoříte dialogové okno ručně, přidáte potřebné členské proměnné do odvozené třídy dialogového okna sami a přidáte členské funkce pro nastavení nebo získání těchto hodnot.

Modální dialogové okno se automaticky zavře, když uživatel stiskne tlačítka OK nebo Storno nebo když váš kód volá `EndDialog` členskou funkci.

Při implementaci nemodálního dialogového okna vždy přepište `OnCancel` členskou funkci a zavolejte `DestroyWindow` v ní. Nevolejte základní třídu `CDialog::OnCancel`, protože volá `EndDialog`, což způsobí, že dialogové okno nebude viditelné, ale neodstraní ho. Měli byste také přepsat `PostNcDestroy` pro nemodální dialogová okna, abybylo možné je odstranit, protože nemodální dialogová okna se obvykle přiřazují s **novými**. Modální dialogová okna jsou obvykle vytvořena na snímku a nepotřebují `PostNcDestroy` vyčištění.

Další informace o `CDialog`naleznete v [dialogových oknech](../../mfc/dialog-boxes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

##  <a name="cdialog"></a>CDialog:: CDialog

Pro vytvoření modálního dialogového okna založeného na prostředku zavolejte buď veřejnou formu konstruktoru.

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
Obsahuje řetězec zakončený znakem null, který je názvem prostředku šablony dialogového okna.

*nIDTemplate*<br/>
Obsahuje číslo ID prostředku šablony dialogového okna.

*pParentWnd*<br/>
Odkazuje na objekt okna nadřazeného objektu nebo vlastníka (typu [CWnd](../../mfc/reference/cwnd-class.md)), do kterého objekt dialogového okna patří. Pokud má hodnotu NULL, je nadřazené okno objektu dialogového okna nastaveno na hlavní okno aplikace.

### <a name="remarks"></a>Poznámky

Jedna forma konstruktoru poskytuje přístup k prostředku dialogového okna podle názvu šablony. Druhý konstruktor poskytuje přístup podle ID šablony, obvykle s předponou **IDD_** (například IDD_DIALOG1).

Chcete-li vytvořit modální dialogové okno ze šablony v paměti, nejprve vyvolejte bezparametrový, chráněný konstruktor a potom `InitModalIndirect`zavolejte.

Po vytvoření modálního dialogového okna jedním z výše uvedených metod zavolejte `DoModal`.

Chcete-li vytvořit nemodální dialogové okno, použijte chráněnou formu `CDialog` konstruktoru. Konstruktor je chráněný, protože musíte odvodit vlastní třídu dialogových oken pro implementaci nemodálního dialogového okna. Vytváření nemodálních dialogových oken je proces se dvěma kroky. Nejdřív zavolejte konstruktor; pak zavolejte `Create` členskou funkci pro vytvoření dialogového okna založeného na prostředku nebo zavolejte `CreateIndirect` k vytvoření dialogového okna ze šablony v paměti.

##  <a name="create"></a>CDialog:: Create

Voláním `Create` pro vytvoření nemodálního dialogového okna pomocí šablony dialogového okna z prostředku.

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
Obsahuje řetězec zakončený znakem null, který je názvem prostředku šablony dialogového okna.

*pParentWnd*<br/>
Odkazuje na objekt nadřazeného okna (typu [CWnd](../../mfc/reference/cwnd-class.md)), do kterého objekt dialogového okna patří. Pokud má hodnotu NULL, je nadřazené okno objektu dialogového okna nastaveno na hlavní okno aplikace.

*nIDTemplate*<br/>
Obsahuje číslo ID prostředku šablony dialogového okna.

### <a name="return-value"></a>Návratová hodnota

Při úspěšném vytvoření a inicializaci dialogového okna vrátí oba formuláře nenulovou hodnotu; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Volání do `Create` konstruktoru lze vyvolat nebo volat po vyvolání konstruktoru.

Pro přístup k prostředku `Create` šablony dialogového okna pomocí názvu šablony nebo ID šablony (například IDD_DIALOG1) jsou k dispozici dvě formy členské funkce.

Pro obě formuláře předejte ukazatel na nadřazený objekt okna. Pokud má *pParentWnd* hodnotu null, dialogové okno se vytvoří s jeho nadřazeným nebo vlastnickým oknem nastaveným na hlavní okno aplikace.

Členská funkce se `Create` vrátí hned po vytvoření dialogového okna.

V šabloně dialogového okna použijte styl WS_VISIBLE, pokud se dialogové okno zobrazí při vytvoření nadřazeného okna. V opačném případě je `ShowWindow`nutné zavolat. Další styly dialogového okna a jejich aplikace naleznete v části struktura [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) v tématu [styly](../../mfc/reference/styles-used-by-mfc.md#window-styles) Windows SDK a okna v *Referenci knihovny MFC*.

Použijte funkci k zničení dialogového okna vytvořeného `Create` funkcí. `CWnd::DestroyWindow`

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCControlLadenDialog#62](../../mfc/codesnippet/cpp/cdialog-class_1.cpp)]

##  <a name="createindirect"></a>CDialog:: CreateIndirect

Zavolejte tuto členskou funkci pro vytvoření nemodálního dialogového okna ze šablony dialogového okna v paměti.

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
Odkazuje na paměť obsahující šablonu dialogového okna sloužící k vytvoření dialogového okna. Tato šablona je ve formě struktury [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) a informace o řízení, jak je popsáno v Windows SDK.

*pParentWnd*<br/>
Odkazuje na objekt nadřazeného okna objektu dialogového okna (typu [CWnd](../../mfc/reference/cwnd-class.md)). Pokud má hodnotu NULL, je nadřazené okno objektu dialogového okna nastaveno na hlavní okno aplikace.

*lpDialogInit*<br/>
Odkazuje na prostředek DLGINIT.

*hDialogTemplate*<br/>
Obsahuje popisovač globální paměti obsahující šablonu dialogového okna. Tato šablona je ve formě `DLGTEMPLATE` struktury a dat pro každý ovládací prvek v dialogovém okně.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo dialogové okno vytvořeno a inicializováno úspěšně; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Členská funkce se `CreateIndirect` vrátí hned po vytvoření dialogového okna.

V šabloně dialogového okna použijte styl WS_VISIBLE, pokud se dialogové okno zobrazí při vytvoření nadřazeného okna. V opačném případě je `ShowWindow` nutné zavolat, aby se zobrazila. Další informace o tom, jak lze určit další styly dialogových oken v šabloně, naleznete v tématu struktura [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) v Windows SDK.

Použijte funkci k zničení dialogového okna vytvořeného `CreateIndirect` funkcí. `CWnd::DestroyWindow`

Dialogová okna obsahující ovládací prvky ActiveX vyžadují další informace, které jsou k dispozici v prostředku DLGINIT.

##  <a name="domodal"></a>CDialog::D oModal

Zavolejte tuto členskou funkci pro vyvolání modálního dialogového okna a po dokončení vrátí výsledek pro dialogové okno.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota typu **int** , která určuje hodnotu parametru *nvýsledek* , která byla předána členské funkci [CDialog:: EndDialog](#enddialog) , která slouží k zavření dialogového okna. Návratová hodnota je-1, pokud funkce nemohla vytvořit dialogové okno, nebo IDABORT, pokud došlo k nějaké jiné chybě, v takovém případě bude okno výstup obsahovat informace o chybě z [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Poznámky

Tato členská funkce zpracovává veškerou interakci s uživatelem, když je dialogové okno aktivní. Toto je dialogové okno modální. To znamená, že uživatel nemůže pracovat s ostatními okny, dokud nebude dialogové okno zavřeno.

Pokud uživatel klikne na jednu z pushbuttons v dialogovém okně, jako je například OK nebo zrušit, je volána členská funkce obslužné rutiny zprávy, například [OnOK –](#onok) nebo- [Cancel](#oncancel), k pokusu o zavření dialogového okna. Výchozí `OnOK` členská funkce ověří a aktualizuje data dialogového okna a zavře dialogové okno s výsledkem IDOK a výchozí `OnCancel` členská funkce zavře dialogové okno s výsledky IDCANCEL bez ověřování a aktualizace dialogová okna data. Můžete přepsat tyto funkce obslužných rutin zpráv a změnit jejich chování.

> [!NOTE]
> `PreTranslateMessage`je nyní volána pro modální zpracování zpráv dialogového okna.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCControlLadenDialog#63](../../mfc/codesnippet/cpp/cdialog-class_2.cpp)]

##  <a name="enddialog"></a>CDialog:: EndDialog

Zavolejte tuto členskou funkci pro ukončení modálního dialogového okna.

```
void EndDialog(int nResult);
```

### <a name="parameters"></a>Parametry

*Nvýsledek*<br/>
Obsahuje hodnotu, která má být vrácena z dialogového okna volajícímu `DoModal`.

### <a name="remarks"></a>Poznámky

Tato členská funkce vrací *nvýsledek* jako návratovou hodnotu `DoModal`. `EndDialog` Funkci musíte použít k dokončení zpracování při každém vytvoření modálního dialogového okna.

Můžete zavolat `EndDialog` kdykoli, dokonce i v [OnInitDialog](#oninitdialog), v takovém případě byste měli dialogové okno zavřít před zobrazením nebo před nastavením fokusu vstupu.

`EndDialog`okamžitě nezavře dialogové okno. Místo toho nastaví příznak, který přesměruje dialogové okno tak, aby se zavřelo, jakmile se vrátí aktuální obslužná rutina zprávy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCControlLadenDialog#64](../../mfc/codesnippet/cpp/cdialog-class_3.cpp)]

[!code-cpp[NVC_MFCControlLadenDialog#65](../../mfc/codesnippet/cpp/cdialog-class_4.cpp)]

##  <a name="getdefid"></a>CDialog:: GetDefID

Chcete-li získat ID výchozího ovládacího prvku (pushbutton) pro dialogové okno, zavolejte členskoufunkci.`GetDefID`

```
DWORD GetDefID() const;
```

### <a name="return-value"></a>Návratová hodnota

32 hodnota bitu ( `DWORD`). Pokud má výchozí (pushbutton) hodnotu ID, slovo s vyšším pořadím obsahuje DC_HASDEFID a slovo s nižším pořadím obsahuje hodnotu ID. Pokud výchozí (pushbutton) nemá hodnotu ID, vrácená hodnota je 0.

### <a name="remarks"></a>Poznámky

Obvykle se jedná o tlačítko OK.

##  <a name="gotodlgctrl"></a>  CDialog::GotoDlgCtrl

Přesune fokus na určený ovládací prvek v dialogovém okně.

```
void GotoDlgCtrl(CWnd* pWndCtrl);
```

### <a name="parameters"></a>Parametry

*pWndCtrl*<br/>
Identifikuje okno (ovládací prvek), které se má získat fokus.

### <a name="remarks"></a>Poznámky

Chcete-li získat ukazatel na ovládací prvek (podřízené okno) pro předání jako *pWndCtrl*, zavolejte `CWnd::GetDlgItem` členskou funkci, která vrací ukazatel na objekt [CWnd](../../mfc/reference/cwnd-class.md) .

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CWnd:: GetDlgItem](../../mfc/reference/cwnd-class.md#getdlgitem).

##  <a name="initmodalindirect"></a>CDialog:: InitModalIndirect

Zavolejte tuto členskou funkci pro inicializaci modálního objektu dialogového okna pomocí šablony dialogového okna, kterou vytvoříte v paměti.

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
Odkazuje na paměť obsahující šablonu dialogového okna sloužící k vytvoření dialogového okna. Tato šablona je ve formě struktury [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) a informace o řízení, jak je popsáno v Windows SDK.

*hDialogTemplate*<br/>
Obsahuje popisovač globální paměti obsahující šablonu dialogového okna. Tato šablona je ve formě `DLGTEMPLATE` struktury a dat pro každý ovládací prvek v dialogovém okně.

*pParentWnd*<br/>
Odkazuje na objekt okna nadřazeného objektu nebo vlastníka (typu [CWnd](../../mfc/reference/cwnd-class.md)), do kterého objekt dialogového okna patří. Pokud má hodnotu NULL, je nadřazené okno objektu dialogového okna nastaveno na hlavní okno aplikace.

*lpDialogInit*<br/>
Odkazuje na prostředek DLGINIT.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byl objekt dialogového okna vytvořen a inicializován úspěšně; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Chcete-li vytvořit modální dialogové okno nepřímo, nejprve přidělte globální blok paměti a vyplňte ho šablonou dialogového okna. Pak zavolejte prázdný `CDialog` konstruktor pro vytvoření objektu dialogového okna. Potom zavolejte `InitModalIndirect` na Uložit popisovač do šablony dialogového okna v paměti. Dialogové okno Windows se vytvoří a zobrazí se později při volání členské funkce [DoModal](#domodal) .

Dialogová okna obsahující ovládací prvky ActiveX vyžadují další informace, které jsou k dispozici v prostředku DLGINIT.

##  <a name="mapdialogrect"></a>CDialog:: MapDialogRect

Volá se, aby se na jednotky obrazovky převedly jednotky dialogového okna v rámečku.

```
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Odkazuje na strukturu [Rect](/windows/win32/api/windef/ns-windef-rect) nebo objekt [CRect](../../atl-mfc-shared/reference/crect-class.md) , který obsahuje souřadnice dialogových oken, které mají být převedeny.

### <a name="remarks"></a>Poznámky

Jednotky dialogového okna jsou uvedeny ve smyslu aktuální základní jednotky dialogového okna odvozené od průměrné šířky a výšky znaků v písmu použitém pro text dialogového okna. Jedna vodorovná jednotka je jednou ze čtvrté jednotky základní šířky dialogového okna a jedna svislá jednotka je o jednu osmina jednotky základní výšky dialogového okna.

Funkce `GetDialogBaseUnits` Windows vrátí informace o velikosti pro písmo systému, ale pro každé dialogové okno můžete zadat jiné písmo, pokud použijete styl DS_SETFONT v souboru definice prostředků. Funkce `MapDialogRect` Windows používá vhodná písma pro toto dialogové okno.

Členská funkce nahradí jednotky dialogového okna v lpRect s jednotkami obrazovky (pixely) tak, aby obdélník mohl být použit k vytvoření dialogového okna nebo umístění ovládacího prvku v rámci pole. `MapDialogRect`

##  <a name="nextdlgctrl"></a>  CDialog::NextDlgCtrl

Přesune fokus na další ovládací prvek v dialogovém okně.

```
void NextDlgCtrl() const;
```

### <a name="remarks"></a>Poznámky

Pokud je fokus na posledním ovládacím prvku v dialogovém okně, přesune se do prvního ovládacího prvku.

##  <a name="oncancel"></a>CDialog::-Cancel

Rozhraní volá tuto metodu, když uživatel klikne na **Zrušit** nebo stiskne klávesu ESC v modálním nebo nemodálním dialogovém okně.

```
virtual void OnCancel();
```

### <a name="remarks"></a>Poznámky

Tuto metodu přepište, pokud chcete provádět akce (například obnovení starých dat), když uživatel zavře dialogové okno, kliknutím na **Zrušit** nebo když zasáhne klávesu ESC. Výchozí zavře modální dialogové okno voláním [EndDialog](#enddialog) a způsobil [DOMODAL](#domodal) pro návrat IDCANCEL.

Pokud implementujete tlačítko **Zrušit** v nemodálním dialogovém okně, je nutné přepsat `OnCancel` metodu a volat [DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) uvnitř ní. Nevolejte metodu základní třídy, protože volá `EndDialog`, což způsobí, že dialogové okno nebude viditelné, ale nezničí ho.

> [!NOTE]
>  Tuto metodu nelze přepsat, pokud používáte `CFileDialog` objekt v programu, který je zkompilován v systému Windows XP. Další informace o `CFileDialog`naleznete v tématu [Třída CFileDialog](../../mfc/reference/cfiledialog-class.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCControlLadenDialog#66](../../mfc/codesnippet/cpp/cdialog-class_5.cpp)]

##  <a name="oninitdialog"></a>CDialog:: OnInitDialog

Tato metoda je volána jako odpověď na `WM_INITDIALOG` zprávu.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Návratová hodnota

Určuje, zda aplikace nastavila vstupní fokus na jeden z ovládacích prvků v dialogovém okně. Pokud `OnInitDialog` vrátí nenulovou hodnotu, systém Windows nastaví fokus vstupu na výchozí umístění, první ovládací prvek v dialogovém okně. Aplikace může vrátit 0 pouze v případě, že explicitně nastaví fokus vstupu na jeden z ovládacích prvků v dialogovém okně.

### <a name="remarks"></a>Poznámky

`WM_INITDIALOG` Systém Windows pošle zprávu do dialogového okna během volání [Create](#create), [CreateIndirect](#createindirect)nebo [DoModal](#domodal) , která se objeví bezprostředně před zobrazením dialogového okna.

Tuto metodu přepište, pokud chcete provést speciální zpracování při inicializaci dialogového okna. V přepsané verzi nejdříve zavolejte základní třídu `OnInitDialog` , ale ignorujte její návratovou hodnotu. Obvykle se vrátíte `TRUE` z přepsané metody.

Systém Windows volá `OnInitDialog` funkci pomocí obecného obecného postupu pro všechna knihovna Microsoft Foundation Class dialogová okna. Nevolá tuto funkci přes mapu zpráv, takže pro tuto metodu nepotřebujete položku mapování zpráv.

> [!NOTE]
> Tuto metodu nelze přepsat, pokud používáte `CFileDialog` objekt v programu, který je zkompilován v systému Windows Vista nebo novějších operačních systémech. Další informace o změnách `CFileDialog` v rámci systému Windows Vista a novějších naleznete v tématu [Třída CFileDialog](../../mfc/reference/cfiledialog-class.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCControlLadenDialog#67](../../mfc/codesnippet/cpp/cdialog-class_6.cpp)]

##  <a name="onok"></a>CDialog:: OnOK –

Volá se, když uživatel klikne na tlačítko **OK** (tlačítko s ID IDOK).

```
virtual void OnOK();
```

### <a name="remarks"></a>Poznámky

Tuto metodu přepište, pokud chcete provádět akce, když se aktivuje tlačítko **OK** . Pokud dialogové okno obsahuje automatické ověřování dat a Exchange, výchozí implementace této metody ověří data dialogového okna a aktualizuje příslušné proměnné ve vaší aplikaci.

Pokud implementujete tlačítko **OK** v nemodálním dialogovém okně, je nutné přepsat `OnOK` metodu a volat [DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) uvnitř ní. Nevolejte metodu základní třídy, protože volá [EndDialog](#enddialog) , což způsobí, že dialogové okno nebude viditelné, ale nezničí ho.

> [!NOTE]
>  Tuto metodu nelze přepsat, pokud používáte `CFileDialog` objekt v programu, který je zkompilován v systému Windows XP. Další informace o `CFileDialog`naleznete v tématu [Třída CFileDialog](../../mfc/reference/cfiledialog-class.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCControlLadenDialog#68](../../mfc/codesnippet/cpp/cdialog-class_7.cpp)]

##  <a name="onsetfont"></a>CDialog:: OnSetFont

Určuje písmo, které bude ovládací prvek dialogového okna používat při vykreslování textu.

```
Virtual void OnSetFont(CFont* pFont);
```

### <a name="parameters"></a>Parametry

*pFont*<br/>
pro Určuje ukazatel na písmo, které bude použito jako výchozí písmo pro všechny ovládací prvky v tomto dialogovém okně.

### <a name="remarks"></a>Poznámky

Dialogové okno použije zadané písmo jako výchozí pro všechny jeho ovládací prvky.

Editor dialogového okna obvykle nastavuje písmo dialogového okna jako součást prostředku šablony dialogového okna.

> [!NOTE]
> Tuto metodu nelze přepsat, pokud používáte `CFileDialog` objekt v programu, který je zkompilován v systému Windows Vista nebo novějších operačních systémech. Další informace o změnách `CFileDialog` v rámci systému Windows Vista a novějších naleznete v tématu [Třída CFileDialog](../../mfc/reference/cfiledialog-class.md).

##  <a name="prevdlgctrl"></a>  CDialog::PrevDlgCtrl

Nastaví fokus na předchozí ovládací prvek v dialogovém okně.

```
void PrevDlgCtrl() const;
```

### <a name="remarks"></a>Poznámky

Pokud je fokus prvním ovládacím prvkem v dialogovém okně, přesune se na poslední ovládací prvek v poli.

##  <a name="setdefid"></a>CDialog:: SetDefID

Změní výchozí ovládací prvek (pushbutton) pro dialogové okno.

```
void SetDefID(UINT nID);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Určuje ID ovládacího prvku (pushbutton), který se stane výchozím nastavením.

##  <a name="sethelpid"></a>CDialog:: SetHelpID

Nastaví kontextově závislé ID kontextové Nápověda pro dialog.

```
void SetHelpID(UINT nIDR);
```

### <a name="parameters"></a>Parametry

*nIDR*<br/>
Určuje kontextové ID kontextové Nápověda.

## <a name="see-also"></a>Viz také:

[DLGCBR32 Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[DLGTEMPL Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
