---
title: 'TN021: Příkazů a zpráv směrování | Microsoft Docs'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.routing
dev_langs:
- C++
helpviewer_keywords:
- TN021
- command routing [MFC], technical note TN021
- Windows messages [MFC], routing
ms.assetid: b5952c8b-123e-406c-a36d-a6ac7c6df307
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e31a35878564fc09fa6c045566811a3ff9e4b0ef
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122014"
---
# <a name="tn021-command-and-message-routing"></a>TN021: Směrování příkazů a zpráv

> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována vzhledem k tomu, že byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata může být zastaralý nebo není správný. Nejnovější informace se doporučuje, vyhledejte téma týkající se v indexu online dokumentaci.

Tato poznámka popisuje architekturu příkaz Směrování a odesílání, jakož i Pokročilá témata v obecné okno směrování zpráv.

Naleznete Visual C++ pro obecné informace o architektury tu popsané, zejména rozdíl mezi zprávy, oznámení ovládacího prvku a příkazy Windows. Tato poznámka se předpokládá velmi obeznámeni s problémy popsané v dokumentaci tištěných a pouze adresy velmi Pokročilá témata.

## <a name="command-routing-and-dispatch-mfc-10-functionality-evolves-to-mfc-20-architecture"></a>Směrování příkazů a odesílání MFC 1.0 funkce zpracovaní s knihovnou MFC 2.0 architektura

Systém Windows má wm_command – zprávu, která je přetížena zajistit oznámení příkazy nabídky, klávesy akcelerátoru a oznámení o dialogovém okně ovládacího prvku.

MFC 1.0 součástí na který trochu tím, že se obslužná rutina příkazu (například "OnFileNew") `CWnd` odvozené třídy k zavolána v reakci na konkrétní wm_command –. Rozděleno společně s strukturu dat s názvem mapy zpráv a výsledkem mechanismus velmi efektivní pro místo příkazu.

MFC 1.0 k dispozici také další funkce pro oddělení oznámení ovládacího prvku z příkazu zprávy. Příkazy jsou reprezentované pomocí ID 16bitové, někdy označovanou jako ID příkazu. Příkazy obvykle začínají `CFrameWnd` (to znamená, nabídky vyberte možnost nebo akcelerátor přeložený) a získat směrována na celou řadu dalších windows.

MFC 1.0 používá směrování příkazů v omezené smysl pro implementaci rozhraní více dokumentů (MDI). (Rámce okna MDI delegovat příkazy k jeho aktivní okno podřízeného MDI).

Tato funkce je zobecněn a rozšířený ve MFC 2.0 umožňuje příkazy zpracovávat širší rozsah objektů (nikoli pouze objekty oken). Poskytuje další formální a rozšiřitelnou architekturu pro směrování zpráv a opětovně používá příkaz cíl směrování pro nejen zpracování příkazů, ale také pro aktualizace objektů uživatelského rozhraní (například položek nabídky a tlačítka panelu nástrojů) tak, aby odrážela aktuální dostupnost příkazu .

## <a name="command-ids"></a>Identifikátory příkazů

Vysvětlení příkazu směrování a proces vázání naleznete v tématu Visual C++. [Technická poznámka 20](../mfc/tn020-id-naming-and-numbering-conventions.md) obsahuje informace o pojmenování ID.

Obecné předponu "ID_" používáme pro ID příkazů. Identifikátory příkazů jsou > = 0x8000. Panel zpráv řádek nebo stav zobrazí řetězec popisu příkazu, pokud je prostředkem STRINGTABLE stejné ID jako ID příkazu.

V prostředcích vaší aplikace zobrazí se příkaz může ID na několika místech:

-   V jedné STRINGTABLE prostředku, který má stejné ID jako řádku řádek zprávy.

-   V které by mohly mít mnoho nabídky prostředky, které jsou připojené k položky nabídky, které vyvolají stejný příkaz.

-   (Rozšířené) v dialogovém okně tlačítko pro příkaz GOSUB.

Ve zdrojovém kódu aplikace zobrazí se příkaz může ID na několika místech:

-   V prostředku. H (nebo další hlavní symbol hlavičkový soubor) k definování identifikátory příkazů specifické pro aplikaci.

-   TŘEBA v pole ID použít k vytvoření panelu nástrojů.

-   V on_command – makro.

-   MOŽNÁ v on_update_command_ui – makro.

V současné době pouze implementace v MFC, která vyžaduje ID příkazů být > = 0x8000 je implementace GOSUB dialogová okna nebo příkazy.

## <a name="gosub-commands-using-command-architecture-in-dialogs"></a>GOSUB příkazy, pomocí příkazu architektury v dialogových oknech

Příkaz architekturu směrování a povolení příkazy pracuje s okna s rámečkem, položky nabídky, tlačítka panelu nástrojů, tlačítek na panelu dialogové okno, ostatní ovládací pruhy a další prvky uživatelského rozhraní, které jsou navržené tak, aby aktualizace na vyžádání a směrování příkazů nebo řízení ID do hlavního příkaz target (obvykle hlavního okna rámce). Tento příkaz hlavní cíl může příkaz nebo ovládací prvek oznámení směrovat další příkaz cílové objekty podle potřeby.

Zobrazí se dialogové okno (modální nebo nemodální) mohou těžit z výhod některé funkce architektury příkaz-li přiřadit ID ovládacího prvku v dialogovém okně ID příslušný příkaz. Podpora pro dialogová okna není automatická, takže možná budete muset napsat další kód.

Pro všechny tyto funkce správně fungovat, vaše ID příkazů by mělo být > = 0x8000. Vzhledem k tomu, že mnoho dialogová okna může získat směruje na stejné rámečku, sdílené příkazy by měla být > = 0x8000, zatímco sdíleném IDCs v konkrétní dialogu by měla být < = 0x7FFF.

Normální tlačítko můžete umístit v normálním modální dialogové okno s IDC tlačítka nastavené ID příslušný příkaz. Když uživatel vybere tlačítko, vlastník dialogového okna (obvykle hlavního okna rámce) načte příkaz, stejně jako ostatní příkaz. Tomu se říká GOSUB příkaz, protože obvykle se používá k zprovoznit další dialog (GOSUB první dialogového okna).

Můžete také zavolat funkci `CWnd::UpdateDialogControls` na vaše dialogové okno možností a předejte ji adresu hlavního rámce okna. Tato funkce bude povolit nebo zakázat podle toho, jestli se mají obslužné rutiny příkazů v rámci vaší ovládací prvky dialogového okna. Tato funkce je volána automaticky za vás pro ovládací pruhy v nečinné smyčky vaší aplikace, ale je třeba volat přímo pro normální dialogová okna, které chcete tuto funkci.

## <a name="when-onupdatecommandui-is-called"></a>Když je volána on_update_command_ui –

Uchování stavu povoleno zaškrtnutí položky nabídky všechny programu vždy může být náročné problém. Běžný postup je k povolení nebo zkontrolujte položky nabídky jenom v případě, že uživatel vybere automaticky otevřeném OKNĚ. Implementace MFC 2.0 `CFrameWnd` zpracovává zprávy WM_INITMENUPOPUP a používá směrování architektura příkaz k určení stavy nabídky prostřednictvím on_update_command_ui – obslužné rutiny.

`CFrameWnd` také obstará WM_ENTERIDLE zpráva k popisu aktuální nabídce položky vybrané na stavovém řádku (také označované jako řádek zprávy).

Struktura nabídky aplikace, upravovat pomocí Visual C++, se používá k reprezentování potenciální příkazy, které jsou k dispozici v době WM_INITMENUPOPUP. On_update_command_ui – obslužné rutiny můžete upravit text nabídky nebo stav, nebo pro pokročilé používá (například seznam naposledy použitých souborů nebo v místní nabídce příkazy OLE), ve skutečnosti změna nabídky struktury před vykreslením v nabídce.

Panely nástrojů (a další ovládací pruhy) se provádí stejný řazení on_update_command_ui – zpracování vstupu aplikace v jeho nečinné smyčky. Najdete v článku *knihovny tříd* a [Technická poznámka 31](../mfc/tn031-control-bars.md) Další informace o ovládací pruhy.

## <a name="nested-pop-up-menus"></a>Vnořené místní nabídky

Pokud používáte struktury vnořené nabídky, si všimnete, že ve dvou různých případech se nazývá on_update_command_ui – obslužná rutina pro první položku v místní nabídce.

Nejprve je volána pro místní nabídky, sám sebe. To je nezbytné, protože místní nabídky nemají ID a používáme ID první položku z místní nabídky k odkazování na celý místní nabídky. V takovém případě *m_pSubMenu* členské proměnné `CCmdUI` objekt bude obsahovat hodnotu NULL a bude odkazovat na místní nabídky.

Druhý je vyvolána před položek nabídky v rozbalovací nabídce mají vykreslovat. V takovém případě Identifikátor odkazuje jenom na první položku a *m_pSubMenu* členské proměnné `CCmdUI` objektu bude mít hodnotu NULL.

To umožňuje povolit místní nabídky, které se liší od jeho položky nabídky, ale vyžaduje, že můžete napsat kód vědět nabídky. Například v nabídce vnořené s následující strukturou:

```Output
File>
    New>
    Sheet (ID_NEW_SHEET)
    Chart (ID_NEW_CHART)
```

Příkazy ID_NEW_SHEET a ID_NEW_CHART můžete nezávisle povolit nebo zakázat. **Nový** místní nabídky by měla být povolená, pokud je povoleno buď dva.

Obslužná rutina pro ID_NEW_SHEET (první příkaz v místní nabídce) by vypadat podobně jako:

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

Obslužná rutina pro ID_NEW_CHART by obslužná rutina příkazu normální aktualizace a podívejte se na něco jako:

```cpp
void CMyApp::OnUpdateNewChart(CCmdUI* pCmdUI)
{
    pCmdUI->Enable(m_bCanCreateChart);
}
```

## <a name="oncommand-and-onbnclicked"></a>On_command – a ON_BN_CLICKED

Makra map zpráv pro **on_command –** a **ON_BN_CLICKED** jsou stejné. ID příkazu, který používá MFC příkazy a ovládání oznámení mechanismus směrování jenom rozhoduje, kam chcete směrovat. Řízení oznámení s kód oznámení ovládacího prvku nula (**BN_CLICKED**) se interpretují jako příkazy.

> [!NOTE]
> Všechny zprávy oznámení ovládacího prvku ve skutečnosti projít řetězu obslužná rutina příkazu. Například když je technicky možné psaní obslužná rutina ovládacího prvku oznámení pro **EN_CHANGE** ve třídě dokumentů. To se obecně nedoporučuje protože praktická použití této funkce jsou několik, tato funkce není podporována ClassWizard a použití funkce může mít za následek křehké kódu.

## <a name="disabling-the-automatic-disabling-of-button-controls"></a>Zakázání automatické zakázání ovládacích prvků

Pokud umístění ovládacího prvku tlačítka na panel dialogového okna, nebo v dialogu pomocí kde jsou volání **CWnd::UpdateDialogControls** vlastními, si všimnete, že tlačítka, které nemají **on_command –** nebo **On_update_command_ui –** obslužné rutiny se automaticky zakáže pro vás rámcem. V některých případech nebudete muset obslužná rutina, ale budete chtít na tlačítko zůstat zapnuté. Nejjednodušší způsob, jak dosáhnout je přidání obslužná rutina příkazu fiktivní (jde udělat ClassWizard) a se nic nestane.

## <a name="window-message-routing"></a>Směrování zpráv oken

Následující část popisuje některé pokročilejší témata na třídy knihovny MFC a jak je ovlivnit směrování zpráv systému Windows a další témata. Informace v tomto poli je pouze stručně popsány. Odkazovat *knihovny tříd* podrobnosti o veřejné rozhraní API. Naleznete ke zdrojovému kódu knihovny MFC Další informace o podrobnosti implementace.

Naleznete [technická Poznámka 17](../mfc/tn017-destroying-window-objects.md) pro informace o čištění okno, velmi důležité téma pro všechny **CWnd**-odvozených třídách.

## <a name="cwnd-issues"></a>Problémy CWnd

Členská funkce implementace **CWnd::OnChildNotify** poskytuje výkonný a rozšiřitelný architekturu pro podřízená okna (také označované jako ovládací prvky) připojit nebo jinak informováni o zprávy, příkazy a řízení oznámení, které jsou určeny pro jejich nadřazené (nebo "vlastník"). Pokud podřízeného okna (/ řídit) je jazyka C++ **CWnd** objektu samostatně, virtuální funkce **OnChildNotify** je nejdříve volána s parametry z původní zprávy (to znamená, **MSG**struktura). Podřízeného okna můžete ponecháte zprávy, eat je nebo upravit zprávu pro nadřazený prvek (stane se výjimečně).

Výchozí hodnota **CWnd** implementace zpracovává následující zprávy a používá **OnChildNotify** háku systému windows (ovládací prvky) prvním přístupu na zprávu povoleno podřízené:

- **WM_MEASUREITEM** a **WM_DRAWITEM** (pro samoobslužné kreslení)

- **WM_COMPAREITEM** a **WM_DELETEITEM** (pro samoobslužné kreslení)

- **WM_HSCROLL** a **WM_VSCROLL**

- **WM_CTLCOLOR –**

- **WM_PARENTNOTIFY**

Všimnete si **OnChildNotify** háku slouží ke změně vykreslování vlastníka zprávy do samoobslužné kreslení zpráv.

Kromě **OnChildNotify** háku, posuňte zprávy mají další směrování chování. Níže naleznete další podrobnosti o posuvníky a zdroje **WM_HSCROLL** a **WM_VSCROLL** zprávy.

## <a name="cframewnd-issues"></a>CFrameWnd problémy

**CFrameWnd** třída poskytuje většina směrování příkazů a uživatelského rozhraní aktualizace implementace. Používá se především pro okno rámce aplikace (**CWinApp::m_pMainWnd**), ale platí pro všechna okna s rámečkem.

Hlavní okno rámce je v okně na panelu nabídek a je nadřazená stavového řádku nebo zprávy řádku. Najdete výše diskuzi na směrování příkazů a **WM_INITMENUPOPUP.**

**CFrameWnd** třída poskytuje správu aktivního zobrazení. Následující zprávy jsou směrovány prostřednictvím active zobrazení:

- Všechny zprávy příkazu (první přístup k nim získá aktivní zobrazení).

- **WM_HSCROLL** a **WM_VSCROLL** zprávy ze stejné úrovni posuvníky (viz níže).

- **WM_ACTIVATE** (a **WM_MDIACTIVATE** pro rozhraní MDI) získat převedena na volání virtuální funkce **CView::OnActivateView**.

## <a name="cmdiframewndcmdichildwnd-issues"></a>CMDIFrameWnd/CMDIChildWnd problémy

Třídy oken s rámečkem obou MDI odvozena od **CFrameWnd** a proto jsou obě povolené pro stejný druh směrování příkazů a uživatelského rozhraní aktualizace součástí **CFrameWnd**. V typické aplikaci MDI pouze hlavní okno rámce (tedy **CMDIFrameWnd** objektu) obsahuje panelu nabídek a na stavovém řádku a proto je hlavní zdroj směrování implementace příkazu.

Schéma obecné směrování je, že aktivní podřízeného okna MDI získá první přístup k příkazům. Výchozí hodnota **PreTranslateMessage –** funkce zpracování tabulky akcelerátoru pro obě podřízených oken MDI (první) a rámečku MDI (druhý) a také standardní akcelerátorů příkaz systému MDI normálně zpracovávat  **TranslateMDISysAccel** (poslední).

## <a name="scroll-bar-issues"></a>Posuvník problémy

Při zpracování zprávy scroll (**WM_HSCROLL**/**OnHScroll** nebo **WM_VSCROLL**/**OnVScroll**), že byste měli zkusit napsat kód obslužné rutiny, takže nespoléhá se na odkud pochází zprávu řádku přejděte. Nejedná se pouze o obecné Windows problém, protože scroll zprávy mohou pocházet z true posuvníku panelu Ovládací prvky nebo z **ws_hscroll –**/**ws_vscroll –** posuvníky, které nejsou ovládací prvky panelu přejděte.

MFC rozšiřuje, který povoluje ovládací prvky panelu přejděte na podřízené nebo okna se přešli na stejné úrovni (ve skutečnosti vztah nadřazený podřízený mezi posuvníku a okno se přesunut oblasti může být nic). To je obzvláště důležité pro sdílené posuvníky s rozdělovače oken. Naleznete [Technická poznámka 29](../mfc/tn029-splitter-windows.md) podrobnosti o provádění **CSplitterWnd** včetně Další informace o sdílených posuvníku panelu problémy.

Na poznámky na okraj jsou uvedeny dvě **CWnd** odvozené třídy, kde doba pro vytvoření stylů panelu přejděte na jsou do pasti a nebyl předán do systému Windows. Když předána běžný postup vytvoření **ws_hscroll –** a **ws_vscroll –** lze nezávisle nastavit, ale po vytvoření nedá změnit. By měl samozřejmě není přímo testů nebo nastavit službu bits WS_SCROLL styl okna, které budou vytvořeny.

Pro **CMDIFrameWnd** styly posuvníku panelu můžete předat **vytvořit** nebo **loadframe –** slouží k vytváření MDICLIENT. Pokud chcete mít posouvatelného MDICLIENT oblasti (jako správce systému Windows Program) pro nastavte oba posuvníku styly (**ws_hscroll –** &#124; **ws_vscroll –**) pro styl použitý k vytvoření **CMDIFrameWnd**.

Pro **CSplitterWnd** styly posuvníku panelu, na které se týkají posuvníků speciální sdílené přesunout pro rozdělovače oblasti. Pro statické rozdělovače oken bude obvykle není nastavit buď styl panelu přejděte. Dynamické rozdělovače oken, bude obvykle mají posuvník styl nastavte směr bude rozdělíte, který je **ws_hscroll –** rozdělit řádky, **ws_vscroll –** rozdělit sloupce.

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)  
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)  
