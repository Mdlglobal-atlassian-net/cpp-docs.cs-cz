---
title: 'TN028: Podpora kontextové nápovědy'
ms.date: 11/04/2016
f1_keywords:
- vc.help
helpviewer_keywords:
- context-sensitive Help [MFC], MFC applications
- TN028
- resource identifiers, context-sensitive Help
ms.assetid: 884f1c55-fa27-4d4c-984f-30907d477484
ms.openlocfilehash: db20cb087d70284103cd02dcfa34b2089ae09821
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50533416"
---
# <a name="tn028-context-sensitive-help-support"></a>TN028: Podpora kontextové nápovědy

Tato poznámka popisuje pravidla pro přiřazování ID kontextů nápovědy a další problémy nápovědy v knihovně MFC. Podpora kontextové nápovědy vyžaduje kompilátor nápovědy, která je k dispozici v jazyce Visual C++.

> [!NOTE]
>  Kromě provádění WinHelp pomocí kontextové nápovědy, MFC také podporuje přes nabídku Nápověda jazyka HTML. Další informace o tuto podporu a programování s nápovědou HTML naleznete v tématu [HTML Help: Context-Sensitive Help for Your Programs](../mfc/html-help-context-sensitive-help-for-your-programs.md).

## <a name="types-of-help-supported"></a>Typy podporované nápovědy

Existují dva druhy kontextové nápovědy, které jsou implementované v aplikacích Windows. První, označuje jako "Nápověda F1" zahrnuje spuštění WinHelp s odpovídající kontext založen na aktuálně aktivní objekt. Druhým je režim "Shift + F1". V tomto režimu se ukazatel změní na kurzor nápovědy a uživatel pokračuje na objekt. V tomto okamžiku WinHelp spuštění a poskytnout pomoc pro objekt, který uživatel kliknul na.

Microsoft Foundation Classes implementovat oba z těchto forem nápovědy. Kromě toho rozhraní framework podporuje dva příkazy jednoduché nápovědy, Index nápovědy a pomoci.

## <a name="help-files"></a>Soubory nápovědy

Microsoft Foundation classes předpokládají jednoho souboru nápovědy. Tento soubor nápovědy musí mít stejný název a cestu jako aplikace. Například pokud je spustitelný soubor C:\MyApplication\MyHelp.exe musí být v souboru nápovědy C:\MyApplication\MyHelp.hlp. Nastavte cestu prostřednictvím *m_pszHelpFilePath* členské proměnné [CWinApp – třída](../mfc/reference/cwinapp-class.md).

## <a name="help-context-ranges"></a>Rozsahy kontextové nápovědy

Výchozí implementace MFC vyžaduje programu použít některá pravidla přiřazení kontextové nápovědy ID. Tato pravidla jsou určitý rozsah ID přidělené k určité ovládací prvky. Tato pravidla můžete přepsat tím, že poskytuje různé implementace různých souvisejících s nápovědou členských funkcí.

```
0x00000000 - 0x0000FFFF : user defined
0x00010000 - 0x0001FFFF : commands (menus/command buttons)
0x00010000 + ID_
(note: 0x18000-> 0x1FFFF is the practical range since command IDs are>=0x8000)
0x00020000 - 0x0002FFFF : windows and dialogs
0x00020000 + IDR_
(note: 0x20000-> 0x27FFF is the practical range since IDRs are <= 0x7FFF)
0x00030000 - 0x0003FFFF : error messages (based on error string ID)
0x00030000 + IDP_
0x00040000 - 0x0004FFFF : special purpose (non-client areas)
0x00040000 + HitTest area
0x00050000 - 0x0005FFFF : controls (those that are not commands)
0x00040000 + IDW_
```

## <a name="simple-help-commands"></a>Příkazy jednoduché "Help"

Existují dvou jednoduchých příkazů nápovědy, které jsou implementovány v rámci tříd Microsoft Foundation:

- Id_help_index –, který je implementován [CWinApp::OnHelpIndex](../mfc/reference/cwinapp-class.md#onhelpindex)

- Id_help_using –, který je implementován [CWinApp::OnHelpUsing](../mfc/reference/cwinapp-class.md#onhelpusing)

První příkaz zobrazí index nápovědy pro aplikaci. Druhé se zobrazí uživatelské nápovědy pomocí programu WinHelp.

## <a name="context-sensitive-help-f1-help"></a>Kontextové nápovědy (Nápověda F1)

Klávesy F1 je obvykle přeložit do příkazu se ID sady id_help – za akcelerátoru umístí do tabulky akcelerátorů hlavního okna. Id_help – příkaz může být také generován tlačítko s ID id_help – v hlavním okně nebo dialogovém okně pole.

Bez ohledu na to, jak je generován id_help – příkaz přesměruje ho jako normální příkaz dokud nedosáhne obslužná rutina příkazu. Další informace o architektuře MFC směrování příkazů [Technická poznámka 21](../mfc/tn021-command-and-message-routing.md). Pokud má aplikace Help povolena, id_help – příkaz bude zpracován adresou [CWinApp::OnHelp](../mfc/reference/cwinapp-class.md#onhelp). Objekt aplikace přijme zprávu nápovědy a přesměruje příkaz odpovídajícím způsobem. To je nezbytné, protože výchozí směrování příkazů není vhodný pro určení nejspecifičtější kontextu.

`CWinApp::OnHelp` pokusy o spuštění WinHelp v následujícím pořadí:

1. Kontroluje aktivní `AfxMessageBox` volání s pomáhají ID. Pokud je aktuálně aktivní okno se zprávou, WinHelp se spustí s kontextem vhodné tuto okno se zprávou.

1. Odešle zprávu WM_COMMANDHELP do aktivního okna. Pokud toto okno spuštěním WinHelp neodpoví, stejnou zprávu odeslaný na předchůdce tohoto okna dokud zpracování zprávy nebo aktuální okno je okno nejvyšší úrovně.

1. Id_default_help – příkaz odešle do hlavního okna. Tím se spustí výchozí nápovědy. Tento příkaz se obvykle mapuje na `CWinApp::OnHelpIndex`.

Globálně přepsat výchozí ID základní hodnoty (například 0x10000 pro příkazy a 0x20000 pro prostředky, například dialogová okna), aplikace by měly přepsat [CWinApp::WinHelp](../mfc/reference/cwinapp-class.md#winhelp).

Pokud chcete přepsat tuto funkci a tak, že je určena kontextové nápovědy, zpracovávejte WM_COMMANDHELP zprávy. Můžete chtít poskytnout konkrétnější nápovědy směrování než poskytuje rozhraní, protože pouze přejde hluboké aktuální podřízené okno MDI. Také můžete chtít poskytnout další nápovědu pro konkrétní okno nebo dialogového okna, například podle aktuální vnitřní stav tohoto objektu nebo aktivní ovládací prvek v rámci dialogového okna.

## <a name="wmcommandhelp"></a>WM_COMMANDHELP

```

afx_msg LRESULT CWnd::OnCommandHelp(WPARAM wParam, LPARAM lParam)

```

WM_COMMANDHELP je soukromých zpráv knihovny MFC Windows, které se získaly podle aktivního okna, pokud se požaduje nápovědy. Když v okně obdrží tuto zprávu, může volat `CWinApp::WinHelp` s kontextem, který odpovídá vnitřní stav okna.

*lParam*<br/>
Obsahuje aktuálně k dispozici kontextové nápovědy. *lParam* je nula, pokud byly určeny žádné kontextové nápovědy. Implementace `OnCommandHelp` můžete použít ID kontextu v *lParam* k určení jiného kontextu nebo právě jej lze předat do `CWinApp::WinHelp`.

*wParam*<br/>
Se nepoužívá a bude nula.

Pokud `OnCommandHelp` volání funkce `CWinApp::WinHelp`, měla by vrátit **TRUE**. Vrací **TRUE** zastaví směrování tento příkaz k jiné třídy a dalších oknech.

## <a name="help-mode-shiftf1-help"></a>Režim nápovědy (Nápověda Shift + F1)

Toto je tedy o druhou podobu kontextové nápovědy. Obecně platí tento režim je zadání stisknutím klávesy SHIFT + F1 nebo prostřednictvím nabídky panelu nástrojů. Je implementován jako příkaz (id_context_help –). Zavěšení filtru zprávy se nepoužívá pro převod tento příkaz při modální dialogové okno nebo nabídka je aktivní, proto tento příkaz je k dispozici pouze uživateli, pokud aplikace provádí pumpu zpráv hlavní (`CWinApp::Run`).

Po zadání tohoto režimu, se zobrazí kurzor myši nápovědy přes všechny oblasti aplikace, i v případě, že aplikace obvykle zobrazí jeho vlastní kurzoru pro tuto oblast (např. velikosti ohraničení kolem okno). Uživatel je možné vybrat příkaz pomocí myši nebo klávesnice. Namísto provádění příkazu se zobrazí nápovědu k tento příkaz. Také uživatel může kliknout na objekt viditelný na obrazovce, jako je například tlačítko na panelu nástrojů a zobrazí nápovědu pro daný objekt. Tento režim Nápověda je poskytována `CWinApp::OnContextHelp`.

Během provádění této smyčky, všechny vstup klávesnice je neaktivní, s výjimkou klíče, které přistupují k nabídce. Navíc se příkaz překlad stále provádí prostřednictvím `PreTranslateMessage` aby uživatel mohl klávesy akcelerátoru a zobrazit nápovědu k tento příkaz.

Pokud existují konkrétní překlady nebo akce trvá umístit `PreTranslateMessage` funkce, která by neměl probíhat během režimu nápovědy klávesy SHIFT + F1, měli byste zkontrolovat *m_bHelpMode* člen `CWinApp` než se pustíte do těch operace. `CDialog` Provádění `PreTranslateMessage` zkontroluje to před voláním `IsDialogMessage`, např. Zakáže "dialogové okno navigační" klávesy na nemodální dialogová okna v režimu SHIFT + F1. Kromě toho `CWinApp::OnIdle` je stále volána v průběhu této smyčky.

Pokud uživatel vybere příkaz v nabídce, zpracuje se jako nápovědu k tomuto příkazu (prostřednictvím WM_COMMANDHELP, viz níže). Pokud uživatel klikne viditelná oblast okna aplikace, rozhodne, zda je myši v neklientské oblasti klikněte nebo klepněte na klienta. `OnContextHelp` mapování obslužné rutiny myši v neklientské oblasti klikne na kliknutí na klienta automaticky. Pokud je klient kliknutí, pak se odešle WM_HELPHITTEST okna, ke které došlo ke kliknutí na. Pokud toto okno vrátí nenulovou hodnotu, tato hodnota slouží jako kontext nápovědu. Pokud hodnotu nula, `OnContextHelp` pokusí nadřazené okno (a které se svou nadřazenou třídou a tak dále). Pokud kontextové nápovědy nelze určit, ve výchozím nastavení je odeslat do hlavního okna, která se pak (obvykle) mapuje na id_default_help – příkaz `CWinApp::OnHelpIndex`.

## <a name="wmhelphittest"></a>WM_HELPHITTEST

```

afx_msg LRESULT CWnd::OnHelpHitTest(
WPARAM, LPARAM lParam)
```

WM_HELPHITTEST je zpráva MFC privátní windows, který přijme aktivní okno kliknutí na režimu nápovědy klávesy SHIFT + F1. V okně obdrží tuto zprávu, vrátí **DWORD** ID nápovědy pro použití u WinHelp.

LOWORD(lParam) obsahuje souřadnice zařízení osy x, ve kterém bylo kliknuto myši vzhledem ke klientské oblasti okna.

HIWORD(lParam) obsahuje souřadnice y.

*wParam*<br/>
Se nepoužívá a bude nula. Pokud vrácená hodnota je nenulový, se nazývá WinHelp pomocí daného kontextu. Pokud vrácená hodnota je nula, je dotazován nadřazené okno o pomoc.

V mnoha případech můžete využít kód spuštění testu, které už můžete mít. Zobrazit provádění `CToolBar::OnHelpHitTest` příklad zpracování zprávy WM_HELPHITTEST (kód využívá spuštění testu kód použitý pro tlačítka a popisky v `CControlBar`).

## <a name="mfc-application-wizard-support-and-makehm"></a>Podpora průvodce aplikací knihovny MFC a makehm –

Průvodce aplikací MFC vytvoří soubory potřebné k sestavení souboru nápovědy (.cnt a HPJ soubory). Zahrnuje také řadu předem připravených .rtf soubory, které je akceptuje kompilátor nápovědy společnosti Microsoft. Řada z nich jsou dokončeny, ale některé možná muset upravit pro konkrétní aplikaci.

Makehm – nástroj podporuje automatické vytvoření souboru "Nápověda mapování". Makehm – nástroj jsou dobře převeditelné prostředků aplikace. H soubor k mapování souboru nápovědy. Příklad:

```
#define IDD_MY_DIALOG   2000
#define ID_MY_COMMAND   150
```

bude přeloženo na:

```
HIDD_MY_DIALOG    0x207d0
HID_MY_COMMAND    0x10096
```

Tento formát je kompatibilní se zařízením kompilátor nápovědy, který mapuje identifikátory kontextu (čísla na pravé straně) s názvy témat (symboly na levé straně).

Zdrojový kód pro makehm – je dostupný v ukázce MFC programovací nástroje [makehm –](../visual-cpp-samples.md).

## <a name="adding-help-support-after-running-the-mfc-application-wizard"></a>Přidání podpory nápovědy po spuštění Průvodce aplikací MFC

Nejlepší způsob, jak přidat zobrazíte nápovědu, jak vaše aplikace je zaškrtněte možnost "Context-sensitive Help" na stránce Pokročilé funkce, Průvodce aplikací knihovny MFC před vytvořením aplikace. Tímto způsobem Průvodce aplikací MFC automaticky přidá položky mapování nezbytné zprávu do vašeho `CWinApp`-odvozené třídy pro podporu nápovědy.

## <a name="help-on-message-boxes"></a>Nápověda k okna se zprávou

Nápovědu k okna se zprávou (říká se jim upozornění) je podporované prostřednictvím `AfxMessageBox` funkce, obálku pro `MessageBox` rozhraní Windows API.

Existují dvě verze `AfxMessageBox`, jeden pro použití s ID řetězce a druhou pro použití s ukazatelem na řetězec (`LPCSTR`):

```
int AFXAPI AfxMessageBox(LPCSTR lpszText,
    UINT nType,
    UINT nIDHelp);

int AFXAPI AfxMessageBox(UINT nIDPrompt,
    UINT nType,
    UINT nIDHelp);
```

V obou případech je volitelná Nápověda ID.

V prvním případě výchozí hodnota pro nIDHelp je 0, což označuje není žádná nápověda pro toto okno se zprávou. Pokud uživatel stiskne klávesu F1, jako je například zpráva pole je aktivní, uživatel nebude přijímat nápovědy (i v případě, že aplikace podporuje nápovědy). Pokud to není žádoucí, pro nIDHelp musí být zadána a ID nápovědy.

V druhém případě je výchozí hodnota pro nIDHelp -1, což znamená, že ID nápovědy je stejný jako nIDPrompt. Pomoc bude fungovat pouze v případě, že aplikace je povoleno nápovědy, samozřejmě). Pro nIDHelp byste měli použít 0, pokud chcete, okno se zprávou nemají žádnou pomoc podporu. Se má zpráva nápovědy povolené, ale výkonný ID nápovědy jiný než nIDPrompt, stačí zadat kladnou hodnotu pro nIDHelp liší od nIDPrompt.

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

