---
title: Třída CFindReplaceDialog
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
ms.openlocfilehash: 7a12d0520d070d74afd9fa91e828970d14c82700
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373867"
---
# <a name="cfindreplacedialog-class"></a>Třída CFindReplaceDialog

Umožňuje implementovat standardní řetězec Najít a nahradit dialogová okna ve vaší aplikaci.

## <a name="syntax"></a>Syntaxe

```
class CFindReplaceDialog : public CCommonDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog)|Volání této funkce `CFindReplaceDialog` k vytvoření objektu.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CFindReplaceDialog::Vytvořit](#create)|Vytvoří a `CFindReplaceDialog` zobrazí dialogové okno.|
|[CFindReplaceDialog::FindNext](#findnext)|Volání této funkce k určení, zda uživatel chce najít další výskyt řetězce hledání.|
|[CFindReplaceDialog::GetFindString](#getfindstring)|Volání této funkce načíst aktuální řetězec hledání.|
|[CFindReplaceDialog::GetNotifier](#getnotifier)|Volání této funkce `FINDREPLACE` načíst strukturu v obslužné rutině registrované zprávy.|
|[CFindReplaceDialog::GetReplaceString](#getreplacestring)|Volání této funkce načíst aktuální nahradit řetězec.|
|[CFindReplaceDialog::IsTerminating](#isterminating)|Volání této funkce k určení, zda dialogové okno je ukončení.|
|[CFindReplaceDialog::MatchCase](#matchcase)|Volání této funkce k určení, zda uživatel chce přesně odpovídat případu řetězce hledání.|
|[CFindReplaceDialog::MatchWholeWord](#matchwholeword)|Volání této funkce k určení, zda uživatel chce odpovídat pouze celá slova.|
|[CFindReplaceDialog::Replaceall](#replaceall)|Volání této funkce k určení, zda uživatel chce nahradit všechny výskyty řetězce.|
|[CFindReplaceDialog::ReplaceCurrent](#replacecurrent)|Volání této funkce k určení, zda uživatel chce nahradit aktuální slovo.|
|[CFindReplaceDialog::SearchDown](#searchdown)|Volání této funkce k určení, zda uživatel chce hledání pokračovat směrem dolů.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CFindReplaceDialog::m_fr](#m_fr)|Struktura slouží k `CFindReplaceDialog` přizpůsobení objektu.|

## <a name="remarks"></a>Poznámky

Na rozdíl od ostatních `CFindReplaceDialog` běžných dialogových oken systému Windows jsou objekty nemodální, což uživatelům umožňuje interakci s jinými okny, když jsou na obrazovce. Existují dva druhy `CFindReplaceDialog` objektů: Hledat dialogová okna a Hledat a nahradit dialogová okna. Přestože dialogová okna umožňují uživateli zadávat řetězce vyhledávání a vyhledávání a nahrazování, neprovádějí žádnou funkci vyhledávání nebo nahrazování. Je nutné je přidat do aplikace.

Chcete-li `CFindReplaceDialog` vytvořit objekt, použijte zadaný konstruktor (který nemá žádné argumenty). Vzhledem k tomu, že se jedná o nemodální dialogové okno, přidělte objekt na haldě pomocí **nového** operátoru, nikoli v zásobníku.

Jakmile `CFindReplaceDialog` je objekt vytvořen, musíte volat [členovou](#create) funkci Vytvořit a vytvořit a zobrazit dialogové okno.

Pomocí [m_fr](#m_fr) struktury můžete před voláním `Create`dialogového okna inicializovat . Struktura `m_fr` je typu [FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew). Další informace o této struktuře naleznete v souboru Windows SDK.

Aby bylo nadřazené okno upozorňováno na požadavky na hledání a nahrazení, musíte použít funkci Windows [RegisterWindowMessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew) a použít [makro ON_REGISTERED_MESSAGE](message-map-macros-mfc.md#on_registered_message) mapy zpráv v okně rámce, které zpracovává tuto registrovanou zprávu.

Můžete určit, zda se uživatel rozhodl ukončit `IsTerminating` dialogové okno pomocí členské funkce.

`CFindReplaceDialog`spoléhá na COMMDLG. Soubor DLL, který je dodáván se systémem Windows verze 3.1 a novější.

Chcete-li dialogové okno přizpůsobit, `CFindReplaceDialog`odvoděte třídu z aplikace , zadejte vlastní šablonu dialogového okna a přidejte mapu zpráv pro zpracování zpráv s oznámením z rozšířených ovládacích prvků. Všechny nezpracované zprávy by měly být předány základní třídě.

Přizpůsobení funkce háku není nutné.

Další informace o `CFindReplaceDialog`použití naleznete v [tématu Common Dialog Classes](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CFindReplaceDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdlgs.h

## <a name="cfindreplacedialogcfindreplacedialog"></a><a name="cfindreplacedialog"></a>CFindReplaceDialog::CFindReplaceDialog

Vytvoří `CFindReplaceDialog` objekt.

```
CFindReplaceDialog();
```

### <a name="remarks"></a>Poznámky

Vzhledem `CFindReplaceDialog` k tomu, že objekt je nemodální dialogové okno, je nutné jej vytvořit na haldě pomocí **nového** operátoru.

Během zničení rozhraní se pokusí provést **odstranění na** ukazatel na dialogové okno. Pokud jste vytvořili dialogové okno v zásobníku, **tento** ukazatel neexistuje a nedefinované chování může způsobit.

Další informace o konstrukci `CFindReplaceDialog` objektů naleznete v přehledu [CFindReplaceDialog.](../../mfc/reference/cfindreplacedialog-class.md) Dialogové okno se zobrazí pomocí [dialogového okna CFindReplaceDialog::Create](#create) member function.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#170](../../mfc/codesnippet/cpp/cfindreplacedialog-class_1.cpp)]

## <a name="cfindreplacedialogcreate"></a><a name="create"></a>CFindReplaceDialog::Vytvořit

Vytvoří a zobrazí objekt dialogového okna Najít nebo Najít `bFindDialogOnly`nebo Nahradit v závislosti na hodnotě aplikace .

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
Nastavte tento parametr na HODNOTU TRUE, aby se zobrazilo dialogové okno **Najít.** Nastavte ji na HODNOTU NEPRAVDA, aby se zobrazilo dialogové okno **Najít a nahradit.**

*lpszNajítCo*<br/>
Když se zobrazí dialogové okno, ukazatel na výchozí hledaný řetězec. Pokud null, dialogové okno neobsahuje výchozí hledaný řetězec.

*lpszNahradit*<br/>
Když se zobrazí dialogové okno, ukazatel na výchozí náhradní řetězec. Pokud null, dialogové okno neobsahuje výchozí náhradní řetězec.

*dwFlags*<br/>
Jeden nebo více příznaků, které můžete použít k přizpůsobení nastavení dialogového okna, kombinované pomocí bitového operátoru OR. Výchozí hodnota je FR_DOWN, která určuje, že hledání má pokračovat směrem dolů. Další informace o těchto příznaky naleznete ve struktuře [FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew) v sadě Windows SDK.

*pParentWnd*<br/>
Ukazatel na nadřazené nebo vlastníjméno okna dialogového okna. Toto je okno, které obdrží zvláštní zprávu označující, že je požadována akce hledání nebo nahrazení. Pokud null, hlavní okno aplikace se používá.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byl objekt dialogového okna úspěšně vytvořen; jinak 0.

### <a name="remarks"></a>Poznámky

Aby bylo nadřazené okno upozorněno na požadavky na hledání a nahrazení, musíte použít funkci Windows [RegisterWindowMessage,](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew) jejíž vrácená hodnota je číslo zprávy jedinečné pro instanci aplikace. Okno rámce by mělo mít položku mapy zpráv, `OnFindReplace` která deklaruje funkci zpětného volání (v následujícím příkladu), která zpracovává tuto registrovanou zprávu. Následující fragment kódu je příkladem toho, jak to udělat `CMyRichEditView`pro třídu okna rámce s názvem :

[!code-cpp[NVC_MFCDocView#171](../../mfc/codesnippet/cpp/cfindreplacedialog-class_2.h)]

[!code-cpp[NVC_MFCDocView#172](../../mfc/codesnippet/cpp/cfindreplacedialog-class_3.cpp)]

[!code-cpp[NVC_MFCDocView#173](../../mfc/codesnippet/cpp/cfindreplacedialog-class_4.cpp)]

V `OnFindReplace` rámci funkce interpretovat záměry uživatele pomocí [CFindReplaceDialog::FindNext](#findnext) a [CFindReplaceDialog::IsTerminating](#isterminating) metody a vytvořit kód pro operace hledání a nahrazení.

### <a name="example"></a>Příklad

  Viz příklad [cfindreplacedialog::CFindReplaceDialog](#cfindreplacedialog).

## <a name="cfindreplacedialogfindnext"></a><a name="findnext"></a>CFindReplaceDialog::FindNext

Volání této funkce z funkce zpětného volání k určení, zda uživatel chce najít další výskyt hledaného řetězce.

```
BOOL FindNext() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud chce uživatel najít další výskyt hledaného řetězce; jinak 0.

## <a name="cfindreplacedialoggetfindstring"></a><a name="getfindstring"></a>CFindReplaceDialog::GetFindString

Volání této funkce z funkce zpětného volání načíst výchozí řetězec najít.

```
CString GetFindString() const;
```

### <a name="return-value"></a>Návratová hodnota

Výchozí řetězec najít.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

## <a name="cfindreplacedialoggetnotifier"></a><a name="getnotifier"></a>CFindReplaceDialog::GetNotifier

Voláním této funkce načtěte ukazatel na aktuální dialogové okno Najít nahradit.

```
static CFindReplaceDialog* PASCAL GetNotifier(LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*Lparam*<br/>
Hodnota *lparam* předána `OnFindReplace` členské funkce okna rámce.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktuální dialogové okno.

### <a name="remarks"></a>Poznámky

Měl by být použit v rámci funkce zpětného volání pro přístup k `m_fr` aktuálnímu dialogovému oknu, volání jeho členských funkcí a přístup ke struktuře.

### <a name="example"></a>Příklad

Viz [CFindReplaceDialog::Create](#create) pro příklad, jak zaregistrovat obslužnou rutinu OnFindReplace pro příjem oznámení z dialogového okna Najít nahradit.

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

## <a name="cfindreplacedialoggetreplacestring"></a><a name="getreplacestring"></a>CFindReplaceDialog::GetReplaceString

Volání této funkce načíst aktuální nahradit řetězec.

```
CString GetReplaceString() const;
```

### <a name="return-value"></a>Návratová hodnota

Výchozí řetězec, který má nahradit nalezené řetězce.

### <a name="example"></a>Příklad

  Viz příklad [cfindreplacedialog::GetFindString](#getfindstring).

## <a name="cfindreplacedialogisterminating"></a><a name="isterminating"></a>CFindReplaceDialog::IsTerminating

Volání této funkce v rámci funkce zpětného volání k určení, zda se uživatel rozhodl ukončit dialogové okno.

```
BOOL IsTerminating() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud se uživatel rozhodl ukončit dialogové okno; jinak 0.

### <a name="remarks"></a>Poznámky

Pokud tato funkce vrátí nenulovou `DestroyWindow` hodnotu, měli byste zavolat členní funkci aktuálního dialogového okna a nastavit libovolnou proměnnou ukazatele dialogového okna na hodnotu NULL. Volitelně můžete také uložit naposledy zadaný text hledání/nahrazení a použít jej k inicializaci dalšího dialogového okna hledání a nahrazení.

### <a name="example"></a>Příklad

  Viz příklad [cfindreplacedialog::GetFindString](#getfindstring).

## <a name="cfindreplacedialogm_fr"></a><a name="m_fr"></a>CFindReplaceDialog::m_fr

Slouží k `CFindReplaceDialog` přizpůsobení objektu.

```
FINDREPLACE m_fr;
```

### <a name="remarks"></a>Poznámky

`m_fr`je struktura typu [FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew). Jeho členové ukládají charakteristiky objektu dialogového okna. Po vytvoření `CFindReplaceDialog` objektu můžete `m_fr` použít k úpravě různých hodnot v dialogovém okně.

Další informace o této struktuře naleznete v `FINDREPLACE` části Windows SDK.

### <a name="example"></a>Příklad

  Viz příklad [cfindreplacedialog::CFindReplaceDialog](#cfindreplacedialog).

## <a name="cfindreplacedialogmatchcase"></a><a name="matchcase"></a>CFindReplaceDialog::MatchCase

Volání této funkce k určení, zda uživatel chce přesně odpovídat případu řetězce hledání.

```
BOOL MatchCase() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud chce uživatel najít výskyty hledaného řetězce, které přesně odpovídají případu hledaného řetězce; jinak 0.

## <a name="cfindreplacedialogmatchwholeword"></a><a name="matchwholeword"></a>CFindReplaceDialog::MatchWholeWord

Volání této funkce k určení, zda uživatel chce odpovídat pouze celá slova.

```
BOOL MatchWholeWord() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud chce uživatel porovnat pouze celá slova hledaného řetězce; jinak 0.

## <a name="cfindreplacedialogreplaceall"></a><a name="replaceall"></a>CFindReplaceDialog::Replaceall

Volání této funkce k určení, zda uživatel chce nahradit všechny výskyty řetězce.

```
BOOL ReplaceAll() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud uživatel požádal, aby byly nahrazeny všechny řetězce odpovídající řetězci nahrazení; jinak 0.

## <a name="cfindreplacedialogreplacecurrent"></a><a name="replacecurrent"></a>CFindReplaceDialog::ReplaceCurrent

Volání této funkce k určení, zda uživatel chce nahradit aktuální slovo.

```
BOOL ReplaceCurrent() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud uživatel požádal, aby byl aktuálně vybraný řetězec nahrazen řetězcem nahrazení; jinak 0.

## <a name="cfindreplacedialogsearchdown"></a><a name="searchdown"></a>CFindReplaceDialog::SearchDown

Volání této funkce k určení, zda uživatel chce hledání pokračovat směrem dolů.

```
BOOL SearchDown() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud uživatel chce, aby hledání pokračovalo směrem dolů; 0, pokud uživatel chce, aby hledání pokračovalo směrem nahoru.

## <a name="see-also"></a>Viz také

[CCommonDialog – třída](../../mfc/reference/ccommondialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
