---
title: 'TN021: Směrování příkazů a zpráv'
ms.date: 06/28/2018
f1_keywords:
- vc.routing
helpviewer_keywords:
- TN021
- command routing [MFC], technical note TN021
- Windows messages [MFC], routing
ms.assetid: b5952c8b-123e-406c-a36d-a6ac7c6df307
ms.openlocfilehash: bdd405bda5c0af9e04a50eee4ef5738f3a53259e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370412"
---
# <a name="tn021-command-and-message-routing"></a>TN021: Směrování příkazů a zpráv

> [!NOTE]
> Následující technická poznámka nebyla aktualizována od doby, kdy byla poprvé zahrnuta do online dokumentace. V důsledku toho mohou být některé postupy a témata zastaralé nebo nesprávné. Chcete-li získat nejnovější informace, doporučujeme vyhledat téma zájmu v online indexu dokumentace.

Tato poznámka popisuje architekturu směrování a odeslání příkazů a také pokročilá témata v obecném směrování zpráv okna.

Obecné podrobnosti o zde popsaných architekturách, zejména o rozdílu mezi zprávami systému Windows, oznámeními ovládacího prvku a příkazy, naleznete v jazyce Visual C++. Tato poznámka předpokládá, že jste velmi dobře obeznámeni s problémy popsanými v tištěné dokumentaci a řeší pouze velmi pokročilá témata.

## <a name="command-routing-and-dispatch-mfc-10-functionality-evolves-to-mfc-20-architecture"></a>Funkce směrování a odeslání knihovny MFC 1.0 se vyvíjí na architekturu knihovny MFC 2.0

Systém Windows má WM_COMMAND zprávu, která je přetížena poskytovat oznámení příkazů nabídky, klíče akcelerátoru a dialog-ovládací upozornění.

MFC 1.0 postaven na tom trochu tím, že příkaz obslužné `CWnd` rutiny (například "OnFileNew") v odvozené třídě získat volání v reakci na konkrétní WM_COMMAND. To je slepená spolu s datovou strukturu s názvem mapa zpráv a výsledkem je velmi prostorově efektivní příkazový mechanismus.

Knihovna MFC 1.0 také poskytla další funkce pro oddělení řídicích oznámení od zpráv příkazů. Příkazy jsou reprezentovány 16bitovým ID, někdy označované jako ID příkazu. Příkazy obvykle začínají `CFrameWnd` od (tj. výběr nabídky nebo přeloženého akcelerátoru) a jsou směrovány do různých jiných oken.

Knihovna MFC 1.0 používá směrování příkazů v omezeném smyslu pro implementaci rozhraní MDI (Multiple Document Interface). (Příkazy delegáta okna rámce MDI do aktivního podřízeného okna MDI.)

Tato funkce byla zobecněna a rozšířena v knihovně MFC 2.0, aby příkazy mohly být zpracovány širším rozsahem objektů (nejen objekty okna). Poskytuje více formální a rozšiřitelné architektury pro směrování zpráv a opakovaně používá směrování cíle příkazu nejen pro zpracování příkazů, ale také pro aktualizaci objektů rozhraní (jako položky nabídky a tlačítka panelu nástrojů) tak, aby odrážely aktuální dostupnost příkazu.

## <a name="command-ids"></a>Identifikátory příkazů

Vysvětlení procesu směrování a vazby příkazů naleznete v tématu Visual C++ . [Technická poznámka 20](../mfc/tn020-id-naming-and-numbering-conventions.md) obsahuje informace o pojmenování ID.

Pro ID příkazů používáme obecnou předponu "ID_". ID příkazů jsou >= 0x8000. Řádek zprávy nebo stavový řádek zobrazí řetězec popisu příkazu, pokud existuje stringtable prostředek se stejnými ID jako ID příkazu.

Ve zdrojích aplikace se id příkazu může zobrazit na několika místech:

- V jednom stringtable prostředek, který má stejné ID jako výzva řádku zprávy.

- V možném počtu zdrojů NABÍDKY, které jsou připojeny k položkám nabídky, které vyvolávají stejný příkaz.

- (ADVANCED) v dialogovém okně pro příkaz GOSUB.

Ve zdrojovém kódu aplikace se id příkazu může zobrazit na několika místech:

- Ve vašem zdroji. H (nebo jiný hlavní soubor záhlaví symbolu) k definování ID příkazů specifických pro aplikaci.

- MOŽNÁ V poli ID slouží k vytvoření panelu nástrojů.

- V ON_COMMAND makru.

- Možná v ON_UPDATE_COMMAND_UI makro.

V současné době je jedinou implementací v knihovně MFC, která vyžaduje ID příkazů >= 0x8000, implementace dialogů/příkazů GOSUB.

## <a name="gosub-commands-using-command-architecture-in-dialogs"></a>Příkazy GOSUB, použití architektury příkazů v dialogových oknech

Architektura příkazů směrování a povolení příkazů funguje dobře s okny rámců, položkami nabídek, tlačítky panelu nástrojů, tlačítky dialogových panelů, dalšími ovládacími panely a dalšími prvky uživatelského rozhraní určenými k aktualizaci příkazů na vyžádání a směrování příkazů nebo řídicích ID na hlavní cíl příkazu (obvykle okno hlavního rámce). Tento cíl hlavního příkazu může podle potřeby směrovat oznámení o příkazu nebo řízení do jiných cílových objektů příkazu.

Dialogové okno (modální nebo nemodální) může využívat některé funkce architektury příkazu, pokud přiřadíte ID ovládacího prvku ovládacího prvku příslušnému ID příkazu. Podpora dialogových oken není automatická, takže možná budete muset napsat nějaký další kód.

Všimněte si, že pro všechny tyto funkce pracovat správně, id příkazu by měla být >= 0x8000. Vzhledem k tomu, že mnoho dialogových oken může být směrováno do stejného rámce, sdílené příkazy by měly být >= 0x8000, zatímco nesdílené IDC v určitém dialogu by měly být <= 0x7FFF.

Normální tlačítko můžete umístit do normálního modálního dialogu s IDC tlačítka nastaveným na příslušné ID příkazu. Když uživatel vybere tlačítko, vlastník dialogového okna (obvykle okno hlavního rámce) získá příkaz stejně jako jakýkoli jiný příkaz. Tento příkaz se nazývá příkaz GOSUB, protože se obvykle používá k zobrazení jiného dialogu (GOSUB prvního dialogu).

Můžete také volat `CWnd::UpdateDialogControls` funkci v dialogu a předat jí adresu hlavního okna rámce. Tato funkce povolí nebo zakáže ovládací prvky dialogového okna na základě toho, zda mají v rámečku obslužné rutiny příkazů. Tato funkce je volána automaticky pro ovládací panely v nečinnosti smyčky aplikace, ale musíte volat přímo pro normální dialogy, které chcete mít tuto funkci.

## <a name="when-on_update_command_ui-is-called"></a>Když se ON_UPDATE_COMMAND_UI nazývá

Udržování povoleného/kontrolovaného stavu všech položek nabídky programu po celou dobu může být výpočtově nákladný problém. Běžnou technikou je povolit nebo zkontrolovat položky nabídky pouze v případě, že uživatel vybere soubor POPUP. MFC 2.0 implementace `CFrameWnd` zpracovává WM_INITMENUPOPUP zprávy a používá architekturu směrování příkazů k určení stavů nabídek prostřednictvím obslužných rutin ON_UPDATE_COMMAND_UI.

`CFrameWnd`také zpracovává zprávu WM_ENTERIDLE popisující aktuální položku nabídky vybranou na stavovém řádku (označovanou také jako řádek zprávy).

Struktura nabídky aplikace, upravená visual c++, se používá k reprezentaci potenciální příkazy k dispozici v WM_INITMENUPOPUP době. ON_UPDATE_COMMAND_UI obslužné rutiny můžete upravit stav nebo text nabídky nebo pro pokročilé použití (například seznam OBJEKT MRU souboru nebo nabídky ole slovesa), ve skutečnosti upravit strukturu nabídky před vykreslením nabídky.

Stejný druh zpracování ON_UPDATE_COMMAND_UI se provádí pro panely nástrojů (a další ovládací panely) při vstupu aplikace do smyčky nečinnosti. Další informace o ovládacích panelech naleznete v *příručce třídní knihovny* a [technické poznámce 31.](../mfc/tn031-control-bars.md)

## <a name="nested-pop-up-menus"></a>Vnořené rozbalovací nabídky

Pokud používáte vnořenou strukturu nabídky, zjistíte, že obslužná rutina ON_UPDATE_COMMAND_UI pro první položku nabídky v rozbalovací nabídce je volána ve dvou různých případech.

Nejprve se nazývá samotné rozbalovací menu. To je nezbytné, protože rozbalovací nabídky nemají ID a používáme ID první položky nabídky rozbalovací nabídky odkazovat na celou rozbalovací nabídku. V takovém případě bude *proměnná m_pSubMenu* člena objektu `CCmdUI` nenulá a bude ukazovat na rozbalovací nabídku.

Za druhé, je volána těsně před položky nabídky v rozbalovací nabídce mají být vypracovány. V tomto případě ID odkazuje pouze na první *m_pSubMenu* položku nabídky `CCmdUI` a m_pSubMenu členské proměnné objektu bude NULL.

To umožňuje povolit rozbalovací nabídku odlišnou od položek nabídky, ale vyžaduje, abyste napsali nějaký kód podporující nabídku. Například v vnořené nabídce s následující strukturou:

```Output
File>
    New>
    Sheet (ID_NEW_SHEET)
    Chart (ID_NEW_CHART)
```

Příkazy ID_NEW_SHEET a ID_NEW_CHART lze nezávisle povolit nebo zakázat. **Nová** rozbalovací nabídka by měla být povolena, pokud je povolena některá z těchto dvou.

Obslužná rutina příkazu pro ID_NEW_SHEET (první příkaz v automaticky otevíraném zobrazení) bude vypadat nějak takto:

```cpp
void CMyApp::OnUpdateNewSheet(CCmdUI* pCmdUI)
{
    if (pCmdUI->m_pSubMenu != NULL)
    {
        // enable entire pop-up for "New" sheet and chart
        BOOL bEnable = m_bCanCreateSheet || m_bCanCreateChart;
        // CCmdUI::Enable is a no-op for this case, so we
        // must do what it would have done.
        pCmdUI->m_pMenu->EnableMenuItem(pCmdUI->m_nIndex,
            MF_BYPOSITION |
            (bEnable  MF_ENABLED : (MF_DISABLED | MF_GRAYED)));

        return;
    }
    // otherwise just the New Sheet command
    pCmdUI->Enable(m_bCanCreateSheet);
}
```

Obslužná rutina příkazu pro ID_NEW_CHART by byla normální obslužná rutina příkazu aktualizace a vypadala by podobně:

```cpp
void CMyApp::OnUpdateNewChart(CCmdUI* pCmdUI)
{
    pCmdUI->Enable(m_bCanCreateChart);
}
```

## <a name="on_command-and-on_bn_clicked"></a>ON_COMMAND a ON_BN_CLICKED

Makra mapy zpráv pro **ON_COMMAND** a **ON_BN_CLICKED** jsou stejná. Mechanismus směrování příkazů a řízení řízení knihovny MFC používá pouze ID příkazu k rozhodnutí, kam se má směrovat. Řídicí oznámení s kódem oznámení ovládacího prvku nula (**BN_CLICKED**) jsou interpretována jako příkazy.

> [!NOTE]
> Ve skutečnosti všechny zprávy o oznámení ovládacího prvku projít řetězce obslužné rutiny příkazu. Například je technicky možné pro zápis obslužné rutiny oznámení ovládacího prvku pro **EN_CHANGE** ve vaší třídě dokumentu. To není obecně vhodné, protože praktické aplikace této funkce jsou málo, funkce není podporovánclassWizard a použití funkce může mít za následek křehký kód.

## <a name="disabling-the-automatic-disabling-of-button-controls"></a>Zakázání automatického zakázání ovládacích prvků tlačítek

Pokud umístíte ovládací prvek tlačítka na dialogové míchací panel nebo v dialogovém okně pomocí, kde voláte **CWnd::UpdateDialogControls** na vlastní pěst, zjistíte, že tlačítka, která nemají **ON_COMMAND** nebo **ON_UPDATE_COMMAND_UI** obslužné rutiny budou automaticky zakázány pro vás rámci. V některých případech nebudete muset mít obslužnou rutinu, ale budete chtít, aby tlačítko zůstalo povolené. Nejjednodušší způsob, jak toho dosáhnout, je přidat fiktivní obslužnou rutinu příkazu (snadné provádět s ClassWizard) a nedělat nic v něm.

## <a name="window-message-routing"></a>Směrování zpráv okna

Následující popisuje některé pokročilejší témata na třídy knihovny MFC a jak směrování zpráv systému Windows a další témata ovlivňují. Informace zde jsou popsány pouze stručně. Podrobnosti o veřejných apich naleznete v *odkazu na knihovnu tříd.* Další informace o podrobnostech implementace naleznete ve zdrojovém kódu knihovny knihovny knihovny knihovny knihovny knihovny knihovny knihovny Knihovny MFC.

Podrobnosti o vyčištění okna, což je velmi důležité téma pro všechny třídy **odvozené od CWnd,** naleznete v [technické poznámce 17.](../mfc/tn017-destroying-window-objects.md)

## <a name="cwnd-issues"></a>CWnd problémy

Funkce člen implementace **CWnd::OnChildNotify** poskytuje výkonnou a rozšiřitelnou architekturu pro podřízená okna (označovaná také jako ovládací prvky) pro zavěšení nebo jiné informace o zprávách, příkazech a oznámeních ovládacích prvků, které přejdou na jejich nadřazené (nebo "vlastník"). Pokud podřízené okno (/control) je c++ **CWnd** objekt sám, virtuální funkce **OnChildNotify** je volána jako první s parametry z původní zprávy (to znamená, **msg** struktury). Podřízené okno může nechat zprávu samostatně, jíst nebo upravit zprávu pro nadřazené (rare).

Výchozí **implementace CWnd** zpracovává následující zprávy a používá **onChildNotify** hák povolit podřízené okna (ovládací prvky) pro první přístup ke zprávě:

- **WM_MEASUREITEM** a **WM_DRAWITEM** (pro sebelosování)

- **WM_COMPAREITEM** a **WM_DELETEITEM** (pro sebelosování)

- **WM_HSCROLL** a **WM_VSCROLL**

- **WM_CTLCOLOR**

- **WM_PARENTNOTIFY**

Všimněte **si, že hák OnChildNotify** se používá pro změnu zpráv kreslení vlastníka do zpráv s vlastním kreslením.

Kromě **onChildNotify** háček, scroll zprávy mají další směrování chování. Další podrobnosti o posuvnících a zdrojích **WM_HSCROLL** a **WM_VSCROLL** zpráv naleznete níže.

## <a name="cframewnd-issues"></a>CFrameWnd problémy

Třída **CFrameWnd** poskytuje většinu směrování příkazů a implementaci aktualizace uživatelského rozhraní. Používá se především pro okno hlavního rámce aplikace (**CWinApp::m_pMainWnd),** ale platí pro všechna okna rámce.

Okno hlavního rámce je okno s panelem nabídek a je nadřazeným stavovým řádkem nebo řádkem zprávy. Viz výše uvedená diskuse o směrování příkazů a **WM_INITMENUPOPUP.**

Třída **CFrameWnd** poskytuje správu aktivního zobrazení. Následující zprávy jsou směrovány prostřednictvím aktivního zobrazení:

- Všechny příkazzprávy (aktivní zobrazení získá první přístup k nim).

- **WM_HSCROLL** a **WM_VSCROLL** zprávy z posuvníků na sourozenecké úrovni (viz níže).

- **WM_ACTIVATE** (a **WM_MDIACTIVATE** pro MDI) se změní na volání virtuální funkce **CView::OnActivateView**.

## <a name="cmdiframewndcmdichildwnd-issues"></a>CMDIFrameWnd/CMDIChildWnd problémy

Obě třídy okna rámce MDI jsou odvozeny z **CFrameWnd** a proto jsou povoleny pro stejný druh směrování příkazů a aktualizace uživatelského rozhraní poskytované v **CFrameWnd**. V typické aplikaci MDI pouze hlavní okno rámce (to znamená **CMDIFrameWnd** objekt) obsahuje řádek nabídek a stavový řádek a proto je hlavním zdrojem implementace směrování příkazu.

Obecné schéma směrování je, že aktivní podřízené okno MDI získá první přístup k příkazům. Výchozí **funkce PreTranslateMessage** zpracovávají tabulky akcelerátorů pro podřízené okna MDI (první) a rámec MDI (druhý) a také standardní akcelerátory příkazů systému MDI obvykle zpracovány **TranslateMDISysAccel** (poslední).

## <a name="scroll-bar-issues"></a>Problémy s posuvníkem

Při zpracování scroll-message **(WM_HSCROLL**/**OnHScroll** a/nebo **WM_VSCROLL**/**OnVScroll**) byste se měli pokusit napsat kód obslužné rutiny, aby se nespoléhal na to, odkud zpráva posuvníku pochází. To není jen obecný problém systému Windows, protože rolovací zprávy mohou pocházet z ovládacích prvků true scroll bar nebo z **WS_HSCROLL**/**WS_VSCROLL** posuvníky, které nejsou ovládací prvky posuvníku.

Knihovna MFC rozšiřuje, že aby posuvník ovládací prvky buď potomek nebo na stejné úrovni okna posouvání (ve skutečnosti vztah nadřazený/podřízený mezi posuvník a okno posouvání může být cokoliv). To je důležité zejména pro sdílené posuvníky s rozdělovacími okny. Podrobnosti o implementaci **CSplitterWnd,** včetně dalších informací o sdílených problémech s posuvníkem, naleznete v [technické poznámce 29.](../mfc/tn029-splitter-windows.md)

Na straně poznámka, existují dvě **CWnd** odvozené třídy, kde posuvník styly zadané v době vytvoření jsou zachyceny a nejsou předány systému Windows. Při předání rutiny vytváření lze nezávisle nastavit **WS_HSCROLL** a **WS_VSCROLL,** ale po vytvoření nelze změnit. Samozřejmě byste neměli přímo testovat nebo nastavujte bity stylu WS_SCROLL okna, které vytvořili.

Pro **CMDIFrameWnd** se styly posuvníku, které předáte **do příkazu Vytvořit** nebo **LoadFrame,** použít k vytvoření mdiclientu. Pokud chcete mít rolovací oblast MDICLIENT (jako je Správce programů systému Windows), nezapomeňte nastavit oba styly posuvníku **(WS_HSCROLL** &#124; **WS_VSCROLL)** pro styl použitý k vytvoření **CMDIFrameWnd**.

Pro **CSplitterWnd** styly posuvníku platí pro speciální sdílené posuvníky pro oblasti rozdělovače. U statických štrůdkových oken obvykle nenastavíte ani styl posuvníku. Pro dynamická okna rozdělovače, budete mít obvykle posuvník styl nastavit pro směr, který rozdělíte, To znamená, **WS_HSCROLL** pokud můžete rozdělit řádky, **WS_VSCROLL,** pokud můžete rozdělit sloupce.

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
