---
title: Dialogové CFindReplaceDialog – Třída
ms.date: 11/04/2016
f1_keywords:
- CFindReplaceDialog
- AFXDLGS/CFindReplaceDialog
- AFXDLGS/CFindReplaceDialog::CFindReplaceDialog
- AFXDLGS/CFindReplaceDialog::Create
- AFXDLGS/CFindReplaceDialog::FindNext
- AFXDLGS/CFindReplaceDialog::GetFindString
- AFXDLGS/CFindReplaceDialog::GetNotifier
- AFXDLGS/CFindReplaceDialog::GetReplaceString
- AFXDLGS/CFindReplaceDialog::IsTerminating
- AFXDLGS/CFindReplaceDialog::MatchCase
- AFXDLGS/CFindReplaceDialog::MatchWholeWord
- AFXDLGS/CFindReplaceDialog::ReplaceAll
- AFXDLGS/CFindReplaceDialog::ReplaceCurrent
- AFXDLGS/CFindReplaceDialog::SearchDown
- AFXDLGS/CFindReplaceDialog::m_fr
helpviewer_keywords:
- CFindReplaceDialog [MFC], CFindReplaceDialog
- CFindReplaceDialog [MFC], Create
- CFindReplaceDialog [MFC], FindNext
- CFindReplaceDialog [MFC], GetFindString
- CFindReplaceDialog [MFC], GetNotifier
- CFindReplaceDialog [MFC], GetReplaceString
- CFindReplaceDialog [MFC], IsTerminating
- CFindReplaceDialog [MFC], MatchCase
- CFindReplaceDialog [MFC], MatchWholeWord
- CFindReplaceDialog [MFC], ReplaceAll
- CFindReplaceDialog [MFC], ReplaceCurrent
- CFindReplaceDialog [MFC], SearchDown
- CFindReplaceDialog [MFC], m_fr
ms.assetid: 610f0b5d-b398-4ef6-8c05-e9d6641e50a8
ms.openlocfilehash: 71234adec214bcbf5d42090edb582a7e5dd552b0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506531"
---
# <a name="cfindreplacedialog-class"></a>Dialogové CFindReplaceDialog – Třída

Umožňuje v aplikaci implementovat standardní dialogová okna pro hledání a nahrazování řetězců.

## <a name="syntax"></a>Syntaxe

```
class CFindReplaceDialog : public CCommonDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[Dialogové CFindReplaceDialog:: dialogové CFindReplaceDialog](#cfindreplacedialog)|Voláním této funkce vytvoříte `CFindReplaceDialog` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[Dialogové CFindReplaceDialog:: Create](#create)|Vytvoří a zobrazí `CFindReplaceDialog` dialogové okno.|
|[Dialogové CFindReplaceDialog:: NajítDalší](#findnext)|Voláním této funkce určíte, zda uživatel chce najít další výskyt řetězce Find.|
|[Dialogové CFindReplaceDialog:: GetFindString](#getfindstring)|Voláním této funkce načtete aktuální řetězec hledání.|
|[Dialogové CFindReplaceDialog:: inoznamovatel](#getnotifier)|Voláním této funkce načtete `FINDREPLACE` strukturu v zaregistrované obslužné rutině zprávy.|
|[Dialogové CFindReplaceDialog:: GetReplaceString](#getreplacestring)|Voláním této funkce načtete aktuální řetězec nahrazení.|
|[Dialogové CFindReplaceDialog:: IsTerminating](#isterminating)|Voláním této funkce určíte, zda je dialogové okno ukončeno.|
|[CFindReplaceDialog::MatchCase](#matchcase)|Voláním této funkce určíte, zda chce uživatel přesně vyhledat velikost písmen hledaného řetězce.|
|[CFindReplaceDialog::MatchWholeWord](#matchwholeword)|Voláním této funkce určíte, zda chce uživatel vyhledat pouze celá slova.|
|[Dialogové CFindReplaceDialog:: nahradit všechno](#replaceall)|Voláním této funkce určíte, zda chce uživatel nahradit všechny výskyty řetězce.|
|[Dialogové CFindReplaceDialog:: ReplaceCurrent](#replacecurrent)|Voláním této funkce určíte, zda uživatel chce nahradit aktuální slovo.|
|[CFindReplaceDialog::SearchDown](#searchdown)|Voláním této funkce určíte, zda bude uživatel chtít, aby hledání pokračovalo směrem dolů.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CFindReplaceDialog::m_fr](#m_fr)|Struktura používaná k přizpůsobení `CFindReplaceDialog` objektu.|

## <a name="remarks"></a>Poznámky

Na rozdíl od ostatních společných `CFindReplaceDialog` dialogových oken Windows jsou objekty nemodální a umožňují uživatelům interakci s ostatními okny, když jsou na obrazovce. Existují dva druhy `CFindReplaceDialog` objektů: Hledání dialogových oken a dialogových oken najít/nahradit. I když dialogová okna umožňují uživateli zadávat vyhledávání a hledat/nahrazovat řetězce, neprovádí žádné funkce vyhledávání a nahrazování. Je nutné je přidat do aplikace.

Chcete-li `CFindReplaceDialog` vytvořit objekt, použijte poskytnutý konstruktor (který neobsahuje žádné argumenty). Vzhledem k tomu, že se jedná o nemodální dialogové okno, přidělte objekt na haldě pomocí operátoru **New** , nikoli v zásobníku.

Jakmile je objekt vytvořen, je nutné zavolat funkci vytvořit členskou funkci pro vytvoření a zobrazení dialogového okna. [](#create) `CFindReplaceDialog`

Použijte strukturu [m_fr](#m_fr) k inicializaci dialogového okna před voláním `Create`. Struktura je typu FINDREPLACE. [](/windows/win32/api/commdlg/ns-commdlg-findreplacew) `m_fr` Další informace o této struktuře naleznete v Windows SDK.

Aby bylo nadřazené okno upozorněno na žádosti o nalezení/nahrazení, je nutné použít funkci Windows [RegisterWindowMessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew) a v okně rámce použít makro [ON_REGISTERED_MESSAGE](message-map-macros-mfc.md#on_registered_message) – mapování zpráv, které tuto registrovanou zprávu zpracuje.

Můžete určit, zda se uživatel rozhodl ukončit dialogové okno pomocí `IsTerminating` členské funkce.

`CFindReplaceDialog`spoléhá na COMMDLG. Soubor DLL dodávaný se systémem Windows verze 3,1 nebo novějším.

Chcete-li přizpůsobit dialogové okno, odvodit třídu `CFindReplaceDialog`z, zadat vlastní šablonu dialogového okna a přidat mapu zpráv pro zpracování zpráv s oznámením z rozšířených ovládacích prvků. Všechny nezpracované zprávy by měly být předány základní třídě.

Přizpůsobení funkce zavěšení není vyžadováno.

Další informace o použití `CFindReplaceDialog`naleznete v tématu [Common dialoging Class](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CFindReplaceDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdlgs. h

##  <a name="cfindreplacedialog"></a>Dialogové CFindReplaceDialog:: dialogové CFindReplaceDialog

`CFindReplaceDialog` Vytvoří objekt.

```
CFindReplaceDialog();
```

### <a name="remarks"></a>Poznámky

Vzhledem k tomu, že objektjenemodálnídialogovéokno,jenutnéjejsestavitnahalděpomocíoperátoru`CFindReplaceDialog` New.

Během zničení se systém pokusí **tuto operaci odstranit** na ukazateli do dialogového okna. Pokud jste v zásobníku vytvořili dialogové okno, tento ukazatel neexistuje a může **to** mít nedefinované chování.

Další informace o konstrukci `CFindReplaceDialog` objektů naleznete v tématu [dialogové CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md) Overview. K zobrazení dialogového okna použijte funkci [dialogové CFindReplaceDialog:: Create](#create) member.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#170](../../mfc/codesnippet/cpp/cfindreplacedialog-class_1.cpp)]

##  <a name="create"></a>Dialogové CFindReplaceDialog:: Create

Vytvoří a zobrazí objekt dialogového okna Najít nebo najít/nahradit v závislosti na hodnotě `bFindDialogOnly`.

```
virtual BOOL Create(
    BOOL bFindDialogOnly,
    LPCTSTR lpszFindWhat,
    LPCTSTR lpszReplaceWith = NULL,
    DWORD dwFlags = FR_DOWN,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*bFindDialogOnly*<br/>
Nastavte tento parametr na hodnotu TRUE, chcete-li zobrazit dialogové okno **Najít** . Nastavte na hodnotu FALSE, chcete-li zobrazit dialogové okno **Najít/nahradit** .

*lpszFindWhat*<br/>
Když se zobrazí dialogové okno, ukazatel na výchozí hledaný řetězec. Pokud je hodnota NULL, dialogové okno neobsahuje výchozí hledaný řetězec.

*lpszReplaceWith*<br/>
Když se zobrazí dialogové okno, ukazatel na výchozí řetězec pro nahrazení. Pokud je hodnota NULL, dialogové okno neobsahuje výchozí řetězec pro nahrazení.

*dwFlags*<br/>
Jeden nebo více příznaků, které lze použít k přizpůsobení nastavení dialogového okna v kombinaci s použitím bitového operátoru OR. Výchozí hodnota je FR_DOWN, která určuje, zda bude hledání pokračovat směrem dolů. Další informace o těchto příznacích najdete v [FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew) struktuře v Windows SDK.

*pParentWnd*<br/>
Ukazatel na nadřazené nebo vlastní okno dialogového okna. Toto je okno, které obdrží speciální zprávu oznamující, že je požadována akce najít/nahradit. Pokud má hodnotu NULL, použije se hlavní okno aplikace.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byl objekt dialogového okna úspěšně vytvořen; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Aby bylo nadřazené okno upozorňováno na požadavky Find/Replace, je nutné použít funkci Windows [RegisterWindowMessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew) , jejíž návratová hodnota je číslo zprávy jedinečné na instanci aplikace. Okno rámce by mělo mít položku mapování zprávy, která deklaruje funkci zpětného volání ( `OnFindReplace` v následujícím příkladu), která zpracovává tuto registrovanou zprávu. Následující fragment kódu je příkladem toho, jak to provést pro třídu okna rámce s názvem `CMyRichEditView`:

[!code-cpp[NVC_MFCDocView#171](../../mfc/codesnippet/cpp/cfindreplacedialog-class_2.h)]

[!code-cpp[NVC_MFCDocView#172](../../mfc/codesnippet/cpp/cfindreplacedialog-class_3.cpp)]

[!code-cpp[NVC_MFCDocView#173](../../mfc/codesnippet/cpp/cfindreplacedialog-class_4.cpp)]

V rámci `OnFindReplace` vaší funkce interpretujte záměry uživatele pomocí metod [dialogové CFindReplaceDialog:: NajítDalší](#findnext) a [dialogové CFindReplaceDialog:: IsTerminating](#isterminating) a vytvoříte kód pro operace Find/Replace.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [dialogové CFindReplaceDialog:: dialogové CFindReplaceDialog](#cfindreplacedialog).

##  <a name="findnext"></a>Dialogové CFindReplaceDialog:: NajítDalší

Voláním této funkce z funkce zpětného volání určíte, zda uživatel chce najít další výskyt hledaného řetězce.

```
BOOL FindNext() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud chce uživatel najít další výskyt hledaného řetězce; v opačném případě 0.

##  <a name="getfindstring"></a>Dialogové CFindReplaceDialog:: GetFindString

Voláním této funkce z funkce zpětného volání načtete výchozí řetězec, který chcete najít.

```
CString GetFindString() const;
```

### <a name="return-value"></a>Návratová hodnota

Výchozí řetězec, který se má najít

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

##  <a name="getnotifier"></a>Dialogové CFindReplaceDialog:: inoznamovatel

Voláním této funkce načtete ukazatel na aktuální dialogové okno Najít nahrazení.

```
static CFindReplaceDialog* PASCAL GetNotifier(LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*lParam*<br/>
Hodnota *lParam* předaná `OnFindReplace` členské funkci okna rámce.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktuální dialogové okno.

### <a name="remarks"></a>Poznámky

Měla by být použita v rámci vaší funkce zpětného volání pro přístup k aktuálnímu dialogovému oknu, zavolat jeho členské `m_fr` funkce a přistupovat ke struktuře.

### <a name="example"></a>Příklad

Příklad registrace obslužné rutiny OnFindReplace pro příjem oznámení z dialogového okna Najít nahrazení naleznete v tématu [dialogové CFindReplaceDialog:: Create](#create) .

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

##  <a name="getreplacestring"></a>Dialogové CFindReplaceDialog:: GetReplaceString

Voláním této funkce načtete aktuální řetězec nahrazení.

```
CString GetReplaceString() const;
```

### <a name="return-value"></a>Návratová hodnota

Výchozí řetězec, pomocí kterého mají být nahrazeny nalezené řetězce.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [dialogové CFindReplaceDialog::](#getfindstring)GetFindString.

##  <a name="isterminating"></a>Dialogové CFindReplaceDialog:: IsTerminating

Voláním této funkce v rámci funkce zpětného volání určíte, zda se uživatel rozhodl ukončit dialogové okno.

```
BOOL IsTerminating() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud se uživatel rozhodl ukončit dialogové okno; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Pokud tato funkce vrátí nenulovou hodnotu, měli byste zavolat `DestroyWindow` členskou funkci aktuálního dialogového okna a nastavit jakoukoli proměnnou v poli ukazatel na hodnotu null. Volitelně můžete také uložit text najít/nahradit a použít ho k inicializaci dalšího dialogového okna Najít/nahradit.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [dialogové CFindReplaceDialog::](#getfindstring)GetFindString.

##  <a name="m_fr"></a>Dialogové CFindReplaceDialog:: m_fr

Slouží k přizpůsobení `CFindReplaceDialog` objektu.

```
FINDREPLACE m_fr;
```

### <a name="remarks"></a>Poznámky

`m_fr`je struktura typu [FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew). Její členové ukládají charakteristiky objektu dialogového okna. Po sestavení `CFindReplaceDialog` objektu lze použít `m_fr` k úpravě různých hodnot v dialogovém okně.

Další informace o této struktuře naleznete v tématu `FINDREPLACE` struktura v Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [dialogové CFindReplaceDialog:: dialogové CFindReplaceDialog](#cfindreplacedialog).

##  <a name="matchcase"></a>Dialogové CFindReplaceDialog:: MatchCase

Voláním této funkce určíte, zda chce uživatel přesně vyhledat velikost písmen hledaného řetězce.

```
BOOL MatchCase() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud chce uživatel najít výskyty hledaného řetězce, který přesně odpovídá případu hledaného řetězce; v opačném případě 0.

##  <a name="matchwholeword"></a>Dialogové CFindReplaceDialog:: MatchWholeWord

Voláním této funkce určíte, zda chce uživatel vyhledat pouze celá slova.

```
BOOL MatchWholeWord() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud chce uživatel vyhledat pouze celá slova vyhledávaného řetězce; v opačném případě 0.

##  <a name="replaceall"></a>Dialogové CFindReplaceDialog:: nahradit všechno

Voláním této funkce určíte, zda chce uživatel nahradit všechny výskyty řetězce.

```
BOOL ReplaceAll() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud uživatel požádal o nahrazení všech řetězců, které odpovídají řetězci Replace; v opačném případě 0.

##  <a name="replacecurrent"></a>Dialogové CFindReplaceDialog:: ReplaceCurrent

Voláním této funkce určíte, zda uživatel chce nahradit aktuální slovo.

```
BOOL ReplaceCurrent() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud uživatel požadoval, aby byl aktuálně vybraný řetězec nahrazen řetězcem Replace; v opačném případě 0.

##  <a name="searchdown"></a>Dialogové CFindReplaceDialog:: SearchDown

Voláním této funkce určíte, zda bude uživatel chtít, aby hledání pokračovalo směrem dolů.

```
BOOL SearchDown() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud uživatel chce, aby hledání pokračovalo směrem dolů; 0, pokud uživatel chce, aby hledání pokračovalo směrem nahoru.

## <a name="see-also"></a>Viz také:

[CCommonDialog – třída](../../mfc/reference/ccommondialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
