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
ms.openlocfilehash: 502edc837d7886dd60ab5107fb194c1490a76928
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370332"
---
# <a name="tn028-context-sensitive-help-support"></a>TN028: Podpora kontextové nápovědy

Tato poznámka popisuje pravidla pro přiřazování ID kontextů nápovědy a další problémy nápovědy v knihovně MFC. Kontextová podpora nápovědy vyžaduje kompilátor nápovědy, který je k dispozici ve visual c++.

> [!NOTE]
> Kromě implementace kontextové nápovědy pomocí nápovědy WinHelp podporuje knihovna MFC také použití nápovědy HTML. Další informace o této podpoře a programování pomocí nápovědy HTML naleznete v [nápovědě html: kontextová nápověda pro programy](../mfc/html-help-context-sensitive-help-for-your-programs.md).

## <a name="types-of-help-supported"></a>Podporované typy nápovědy

Existují dva typy kontextové nápovědy implementované v aplikacích systému Windows. První, označované jako "Nápověda F1" zahrnuje spuštění WinHelp s příslušným kontextem na základě aktuálně aktivního objektu. Druhým je režim "Shift+ F1". V tomto režimu se kurzor myši změní na kurzor nápovědy a uživatel pokračuje kliknutím na objekt. V tomto okamžiku je spuštěna akce WinHelp, která poskytuje nápovědu k objektu, na který uživatel klikl.

Třídy Microsoft Foundation implementovat obě tyto formy nápovědy. Kromě toho rozhraní framework podporuje dva jednoduché příkazy nápovědy, index nápovědy a použití nápovědy.

## <a name="help-files"></a>Soubory nápovědy

Třídy Microsoft Foundation předpokládají jeden soubor nápovědy. Tento soubor nápovědy musí mít stejný název a cestu jako aplikace. Pokud je například spustitelný soubor C:\MyApplication\MyHelp.exe, musí být soubor nápovědy C:\MyApplication\MyHelp.hlp. Cestu nastavíte proměnnou *m_pszHelpFilePath* člena [třídy CWinApp](../mfc/reference/cwinapp-class.md).

## <a name="help-context-ranges"></a>Kontextové rozsahy nápovědy

Výchozí implementace knihovny MFC vyžaduje, aby program dodržoval některá pravidla týkající se přiřazení ID kontextu nápovědy. Tato pravidla jsou rozsah ID přidělené konkrétní ovládací prvky. Tato pravidla můžete přepsat poskytnutím různých implementací různých členských funkcí souvisejících s nápovědou.

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

## <a name="simple-help-commands"></a>Jednoduché příkazy "Nápověda"

Existují dva jednoduché příkazy nápovědy, které jsou implementovány třídy Microsoft Foundation:

- ID_HELP_INDEX, který je implementován [CWinApp::OnHelpIndex](../mfc/reference/cwinapp-class.md#onhelpindex)

- ID_HELP_USING který je implementován [CWinApp::OnHelpUsing](../mfc/reference/cwinapp-class.md#onhelpusing)

První příkaz zobrazí index nápovědy pro aplikaci. Druhý zobrazuje uživatelskou nápovědu k používání programu WinHelp.

## <a name="context-sensitive-help-f1-help"></a>Kontextová nápověda (Nápověda F1)

Klávesa F1 je obvykle přeložena do příkazu s ID ID_HELP akcelerátorem umístěným do tabulky akcelerátoru hlavního okna. Příkaz ID_HELP může být také generován tlačítkem s ID ID_HELP v hlavním okně nebo dialogovém okně.

Bez ohledu na to, jak je příkaz ID_HELP generován, je směrován jako normální příkaz, dokud nedosáhne obslužné rutiny příkazu. Další informace o architektuře směrování příkazů knihovny MFC naleznete v [technické poznámce 21](../mfc/tn021-command-and-message-routing.md). Pokud je v aplikaci povolena nápověda, příkaz ID_HELP bude zpracován [pomocí příkazu CWinApp::OnHelp](../mfc/reference/cwinapp-class.md#onhelp). Aplikační objekt obdrží zprávu nápovědy a potom odpovídajícím způsobem směruje příkaz. To je nezbytné, protože výchozí směrování příkazů není vhodné pro určení nejkonkrétnější ho kontextu.

`CWinApp::OnHelp`pokusí se spustit nápovědu WinHelp v následujícím pořadí:

1. Zkontroluje aktivní `AfxMessageBox` hovor s ID nápovědy. Pokud je aktuálně aktivní okno se zprávou, je spuštěna nápověda WinHelp s kontextem odpovídajícím tomuto poli zprávy.

1. Odešle zprávu WM_COMMANDHELP do aktivního okna. Pokud toto okno nereaguje spuštěním winhelp, stejná zpráva je pak odeslána předkům tohoto okna, dokud zpráva je zpracována nebo aktuální okno je okno nejvyšší úrovně.

1. Odešle příkaz ID_DEFAULT_HELP do hlavního okna. Tím se vyvolá výchozí nápověda. Tento příkaz je obecně `CWinApp::OnHelpIndex`mapován na .

Chcete-li globálně přepsat výchozí základní hodnoty ID (např. 0x10000 pro příkazy a 0x20000 pro prostředky, jako jsou dialogová okna), aplikace by měla přepsat [CWinApp::WinHelp](../mfc/reference/cwinapp-class.md#winhelp).

Chcete-li přepsat tuto funkci a způsob, jakým je určen kontext nápovědy, měli byste zpracovat zprávu WM_COMMANDHELP. Můžete chtít poskytnout konkrétnější směrování nápovědy, než poskytuje rozhraní framework, protože jde pouze tak hluboko jako aktuální podřízené okno MDI. Můžete také poskytnout konkrétnější nápovědu pro určité okno nebo dialogové okno, například na základě aktuálního vnitřního stavu daného objektu nebo aktivního ovládacího prvku v dialogovém okně.

## <a name="wm_commandhelp"></a>WM_COMMANDHELP

```

afx_msg LRESULT CWnd::OnCommandHelp(WPARAM wParam, LPARAM lParam)
```

WM_COMMANDHELP je soukromá zpráva knihovny Windows MFC, která je přijata aktivním oknem při požadavku na nápovědu. Když okno obdrží tuto zprávu, `CWinApp::WinHelp` může volat s kontextem, který odpovídá vnitřnístav okna.

*Lparam*<br/>
Obsahuje kontext aktuálně dostupné nápovědy. *LParam* je nula, pokud nebyl určen žádný kontext nápovědy. Implementace `OnCommandHelp` můžete použít ID kontextu v *lParam* k určení jiného `CWinApp::WinHelp`kontextu nebo můžete jen předat .

*wParam*<br/>
Nepoužívá se a bude nula.

Pokud `OnCommandHelp` funkce `CWinApp::WinHelp`volá , měla by vrátit **hodnotu TRUE**. Vrácení **funkce TRUE** zastaví směrování tohoto příkazu do jiných tříd a do jiných oken.

## <a name="help-mode-shiftf1-help"></a>Režim nápovědy (nápověda Shift+F1)

Toto je druhá forma kontextové nápovědy. Obecně platí, že tento režim se zadává stisknutím kláves SHIFT+F1 nebo přes nabídku/panel nástrojů. Je implementován jako příkaz (ID_CONTEXT_HELP). Háček filtru zpráv se nepoužívá k překladu tohoto příkazu, když je aktivní modální dialogové okno nebo nabídka,`CWinApp::Run`proto je tento příkaz k dispozici pouze uživateli, když aplikace provádí čerpadlo hlavní zprávy ( ).

Po vstupu do tohoto režimu se kurzor myši nápovědy zobrazí ve všech oblastech aplikace, i když by aplikace normálně zobrazovala vlastní kurzor pro tuto oblast (například ohraničení velikosti kolem okna). Uživatel je schopen použít myš nebo klávesnici k výběru příkazu. Místo spuštění příkazu se zobrazí nápověda k tomuto příkazu. Uživatel může také klepnout na viditelný objekt na obrazovce, například na tlačítko na panelu nástrojů, a zobrazí se nápověda pro tento objekt. Tento režim nápovědy poskytuje `CWinApp::OnContextHelp`společnost .

Během provádění této smyčky je veškerý vstup z klávesnice neaktivní, s výjimkou kláves, které přistupují k nabídce. Překlad příkazů se také `PreTranslateMessage` provádí prostřednictvím, aby uživatel mohl stisknout klávesu akcelerátoru a získat nápovědu k tomuto příkazu.

Pokud jsou ve `PreTranslateMessage` funkci, která by se neměla uskutečňovat v režimu nápovědy SHIFT+F1, probíhá určité překlady nebo akce, měli byste `CWinApp` před provedením těchto operací zkontrolovat *m_bHelpMode* člen. Provádění `CDialog` kontroly `PreTranslateMessage` to `IsDialogMessage`před voláním , například. Tím se zakáží tlačítka "dialog navigace" na nemodálnídialogovběhem režimu SHIFT + F1. Kromě toho `CWinApp::OnIdle` je stále volána během této smyčky.

Pokud uživatel vybere příkaz z nabídky, je zpracován jako nápověda na tento příkaz (prostřednictvím WM_COMMANDHELP, viz níže). Pokud uživatel klepne na viditelnou oblast okna aplikace, je provedeno určení, zda se jedná o neklientské kliknutí nebo kliknutí klienta. `OnContextHelp`zvládá mapování neklientských kliknutí na kliknutí klienta automaticky. Pokud se jedná o kliknutí klienta, odešle WM_HELPHITTEST do okna, na které bylo kliknuto. Pokud toto okno vrátí nenulovou hodnotu, tato hodnota se použije jako kontext pro nápovědu. Pokud vrátí nulu, `OnContextHelp` pokusí se nadřazené okno (a není-li to, jeho nadřazené a tak dále). Pokud nelze určit kontext nápovědy, je ve výchozím nastavení odeslání příkazu ID_DEFAULT_HELP do hlavního okna, které je pak (obvykle) mapováno na `CWinApp::OnHelpIndex`.

## <a name="wm_helphittest"></a>WM_HELPHITTEST

```

afx_msg LRESULT CWnd::OnHelpHitTest(
WPARAM, LPARAM lParam)
```

WM_HELPHITTEST je soukromá zpráva knihovny MFC, která je přijata aktivním oknem, na které klepnulo během režimu nápovědy SHIFT+F1. Když okno obdrží tuto zprávu, vrátí ID nápovědy **DWORD** pro použití WinHelp.

LOWORD(lParam) obsahuje souřadnici zařízení osy X, kde bylo klepnutí myši vzhledem ke klientské oblasti okna.

HIWORD(lParam) obsahuje souřadnici osy Y.

*wParam*<br/>
se nepoužívá a bude nula. Pokud je vrácená hodnota nenulová, je s tímto kontextem volána nápověda WinHelp. Pokud je vrácená hodnota nulová, nadřazené okno je dotazován o pomoc.

V mnoha případech můžete využít kód testování přístupů, který již máte. Podívejte se `CToolBar::OnHelpHitTest` na implementaci pro příklad zpracování zprávy WM_HELPHITTEST (kód využívá hit-test kód `CControlBar`používaný na tlačítka a popisky v ).

## <a name="mfc-application-wizard-support-and-makehm"></a>Podpora průvodce aplikací knihovny MFC a makehm

Průvodce aplikací knihovny MFC vytvoří potřebné soubory k vytvoření souboru nápovědy (soubory HPT a HPJ). Obsahuje také řadu předem vytvořených souborů RTF, které jsou přijímány kompilátorem nápovědy společnosti Microsoft. Mnoho témat je dokončeno, ale některé z nich může být nutné upravit pro konkrétní aplikaci.

Automatické vytvoření souboru "mapování nápovědy" je podporováno nástrojem s názvem MAKEHM. Nástroj MAKEHM může přeložit prostředek aplikace. H do souboru mapování nápovědy. Příklad:

```
#define IDD_MY_DIALOG   2000
#define ID_MY_COMMAND   150
```

budou přeloženy do:

```
HIDD_MY_DIALOG    0x207d0
HID_MY_COMMAND    0x10096
```

Tento formát je kompatibilní se zařízením kompilátoru nápovědy, které mapuje ID kontextu (čísla na pravé straně) s názvy témat (symboly na levé straně).

Zdrojový kód pro MAKEHM je k dispozici ve vzorku mfc programovací nástroje [MAKEHM](../overview/visual-cpp-samples.md).

## <a name="adding-help-support-after-running-the-mfc-application-wizard"></a>Přidání podpory nápovědy po spuštění Průvodce aplikací knihovny MFC

Nejlepší způsob, jak přidat nápovědu do aplikace, je před vytvořením aplikace zkontrolovat možnost Kontextová nápověda na stránce Rozšířené funkce Průvodce aplikací knihovny MFC. Tímto způsobem Průvodce aplikací knihovny MFC automaticky `CWinApp`přidá potřebné položky mapy zpráv do vaší odvozené třídy pro podporu nápovědy.

## <a name="help-on-message-boxes"></a>Nápověda k polím zpráv

Nápověda k oknům se zprávami `AfxMessageBox` (někdy nazývané výstrahy) je podporována prostřednictvím funkce, obálky rozhraní API systému `MessageBox` Windows.

Existují dvě verze `AfxMessageBox`, jedna pro použití s ID řetězce a druhá`LPCSTR`pro použití s ukazatelem na řetězec ( ):

```
int AFXAPI AfxMessageBox(LPCSTR lpszText,
    UINT nType,
    UINT nIDHelp);

int AFXAPI AfxMessageBox(UINT nIDPrompt,
    UINT nType,
    UINT nIDHelp);
```

V obou případech existuje volitelné ID nápovědy.

V prvním případě je výchozí hodnota pro nIDHelp 0, což znamená, že pro toto okno se zprávou není nápověda. Pokud uživatel stiskne klávesu F1, zatímco například okno se zprávou je aktivní, uživatel neobdrží nápovědu (i v případě, že aplikace podporuje nápovědu). Pokud to není žádoucí, id nápovědy by měla být k dispozici pro nIDHelp.

V druhém případě je výchozí hodnota pro nIDHelp -1, což znamená, že ID nápovědy je stejné jako nIDPrompt. Nápověda bude fungovat pouze v případě, že aplikace je help-enabled, samozřejmě). Měli byste poskytnout 0 pro nIDHelp, pokud si přejete, aby okno se zprávou nemají žádnou podporu nápovědy. Pokud chcete, aby zpráva byla povolena nápověda, ale touha jiné ID pomoci než nIDPrompt, jednoduše poskytnout kladnou hodnotu pro nIDHelp liší od nIDPrompt.

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
