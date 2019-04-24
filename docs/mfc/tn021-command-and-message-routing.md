---
title: 'TN021: Příkaz a směrování zpráv'
ms.date: 06/28/2018
f1_keywords:
- vc.routing
helpviewer_keywords:
- TN021
- command routing [MFC], technical note TN021
- Windows messages [MFC], routing
ms.assetid: b5952c8b-123e-406c-a36d-a6ac7c6df307
ms.openlocfilehash: ce8aa2013c8f2f351ca1028f0d6103135ba5ecd8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306178"
---
# <a name="tn021-command-and-message-routing"></a>TN021: Příkaz a směrování zpráv

> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována, protože byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata mohou být nesprávné nebo zastaralé. Nejnovější informace se doporučuje vyhledat téma zájmu v dokumentaci online index.

Tato poznámka popisuje architekturu směrování a odeslání příkazu, stejně jako pokročilá témata týkající se Obecné okno směrování zpráv.

Najdete Visual C++ pro obecné informace o architekturách tu popsané, zejména rozdíl mezi Windows zprávy oznámení ovládacích prvků a příkazů. Tato poznámka předpokládá, že velmi obeznámeni s problémy popsané v dokumentaci tištěné a pouze adresy velmi Pokročilá témata.

## <a name="command-routing-and-dispatch-mfc-10-functionality-evolves-to-mfc-20-architecture"></a>Směrování příkazů a odeslání MFC 1.0 funkcí se vyvíjí s knihovnou MFC 2.0 architektury

Windows má wm_command – zprávy, která je přetížena pro poskytují oznámení příkazy nabídky, klávesové zkratky a oznámení ovládacího prvku dialogu.

1.0 s MFC integrovaným zabývat trochu tím, že obslužná rutina příkazu (například "OnFileNew") `CWnd` odvozené třídy zavolána v reakci na konkrétní wm_command –. Rozděleno spolu s strukturu dat s názvem mapu zpráv a má za následek velmi efektivní pro místo příkazu mechanismus.

MFC 1.0 poskytujeme také další funkce pro oddělení oznámení ovládacích prvků ze zprávy příkazů. Příkazy jsou reprezentovány ID 16bitové, někdy označovanou jako ID příkazu. Příkazy obvykle začínají `CFrameWnd` (to znamená nabídky vyberte možnost nebo přeložené akcelerátoru) a směrované do celé řady dalších oknech.

1.0 knihovny MFC používá směrování příkazů v omezené smysl pro implementaci rozhraní více dokumentů (MDI). (Okna rámce MDI delegovat příkazy, které její aktivní podřízené okno MDI).

Tato funkce byla generalizovaný a rozšířit v MFC 2.0, aby bylo možné příkazy zpracovávat širší rozsah objektů (nikoli pouze objekty oken). Poskytuje další formální a rozšiřitelná architektura pro směrování zpráv a opětovně používá příkaz cíl směrování pro nejen zpracování příkazů, ale také pro aktualizace objektů uživatelského rozhraní (např. položky nabídky nebo tlačítka na panelu nástrojů) tak, aby odrážela aktuální dostupnost příkazu .

## <a name="command-ids"></a>Identifikátory příkazů

Vysvětlení směrování a proces vytvoření vazby příkazu naleznete v tématu Visual C++. [Technická poznámka 20](../mfc/tn020-id-naming-and-numbering-conventions.md) obsahuje informace o pojmenování ID.

Obecný předponu "ID_" používáme pro ID příkazů. ID příkazu je > = 0x8000. Zpráva řádku nebo stavového řádku. Zobrazí řetězce popisu příkazu, pokud je STRINGTABLE prostředek se stejným ID jako identifikátor příkazu

V prostředcích aplikace se zobrazí příkaz, který může ID na několika místech:

- V jedné STRINGTABLE prostředku, který má stejný Identifikátor jako zpráva řádku.

- Může být mnoho nabídce prostředky, které jsou připojeny k položkám, které vyvolají ten samý příkaz.

- (Rozšířené) v dialogovém okně tlačítko GOSUB příkazu.

Ve zdrojovém kódu vaší aplikace zobrazí se příkaz, který může ID na několika místech:

- V prostředku. H (nebo jiné hlavičkový soubor symbolů hlavní) k definování ID příkazů specifických pro aplikaci.

- NAPŘÍKLAD v poli ID použité k vytvoření panelu nástrojů.

- V makru ON_COMMAND.

- TŘEBA v ON_UPDATE_COMMAND_UI – makro.

V současné době pouze implementace v prostředí MFC, která vyžaduje ID příkazů být > = 0x8000 je implementace GOSUB dialogová okna a příkazy.

## <a name="gosub-commands-using-command-architecture-in-dialogs"></a>Příkazy GOSUB, pomocí příkazu architektury v dialogových oknech

Příkaz architektury, směrování a příkazy pracuje s oken s rámečkem, položek nabídky, tlačítka na panelu nástrojů, tlačítek dialogového okna, jiné ovládací pruhy a další prvky uživatelského rozhraní navržené tak, aby aktualizace na vyžádání a směrování příkazů nebo hlavní ovládací prvek ID cíl příkazu (obvykle hlavní okno rámce). Využívajících hlavního příkazu může směrovat další příkaz cílové objektů podle potřeby oznámení příkaz nebo ovládací prvek.

Dialogové okno (modálním nebo nemodálním) mohou těžit z některé funkce architektury příkazu, pokud přiřadíte ID ovládacího prvku dialogu ID příslušný příkaz. Podporu pro dialogová okna není automatická, takže možná budete muset napsat další kód.

Všimněte si, že všechny tyto funkce fungovalo správně, vaše ID příkazů by měl být > = 0x8000. Protože mnoho dialogových oknech může směrované na rámec stejné, sdílené příkazy by měl být > = 0x8000, zatímco nesdílené IDCs v konkrétní dialogového okna by měl být < = 0x7FFF.

Normální tlačítko můžete umístit v normální modální dialogové okno s IDC tlačítka nastavte na ID příslušný příkaz. Když uživatel vybere tlačítko, vlastník dialogového okna (obvykle hlavní okno rámce) načte příkaz, stejně jako všechny příkazy. Příkaz GOSUB tomu se říká, protože ho se zobrazí další dialog (GOSUB prvního dialogového okna) se obvykle používá.

Můžete také volat funkci `CWnd::UpdateDialogControls` na dialogové okno a předejte jí adresu okna hlavního rámce. Tato funkce se povolí nebo zakáže závislosti na tom, zda mají obslužné rutiny příkazů v rámci vaší ovládací prvky dialogového okna. Tato funkce je volána automaticky za vás pro ovládací pruhy v nečinné smyčky vaší aplikace, ale lze zavolat přímo pro normální dialogová okna, které chcete nechat tuto funkci.

## <a name="when-onupdatecommandui-is-called"></a>Když je volána ON_UPDATE_COMMAND_UI

Udržování stavu povolený/checked položek nabídky všechny programu celou dobu může být problém výpočetně náročné. Běžná technika je povolení/vrácení položek nabídky se pouze v případě, že uživatel vybere automaticky otevírané okno. Implementace MFC 2.0 `CFrameWnd` zpracovává zprávu WM_INITMENUPOPUP a používá k určení stavů nabídky prostřednictvím obslužné rutiny ON_UPDATE_COMMAND_UI architekturu směrování příkazu.

`CFrameWnd` také zpracovává zprávy WM_ENTERIDLE pro popis aktuální nabídce položky vybrané na stavovém řádku (také označované jako řádek zprávy).

Struktura nabídky aplikace, upravovat Visual C++, se používá k reprezentování potenciální příkazy, které jsou k dispozici v době WM_INITMENUPOPUP. ON_UPDATE_COMMAND_UI obslužné rutiny můžete změnit text nabídky nebo stav nebo pro rozšířené použití (např. do seznamu naposledy použitých souborů nebo v rozbalovací nabídce příkazy OLE), ve skutečnosti upravit struktura nabídky před vykreslením nabídky.

Panely nástrojů (a další ovládací pruhy) se provádí stejný druh ON_UPDATE_COMMAND_UI zpracování při aplikaci zadá jeho nečinné smyčky. Najdete v článku *knihovny tříd* a [Technická poznámka 31](../mfc/tn031-control-bars.md) Další informace o ovládacích panelů.

## <a name="nested-pop-up-menus"></a>Vnořené místní nabídky

Pokud používáte struktura vnořené nabídky, můžete si všimnout, že je volána obslužnou rutinu ON_UPDATE_COMMAND_UI pro první položku v rozbalovací nabídce ve dvou různých případech.

Nejprve je volána pro rozbalovací nabídce, samotného. To je nezbytné, protože nabídek nejsou dostupné žádné identifikátory a používáme ID první položky nabídky v rozbalovací nabídce k odkazování na celý rozbalovací nabídky. V takovém případě *m_pSubMenu* členské proměnné `CCmdUI` objektu bude mít hodnotu NULL a bude odkazovat na místní nabídky.

Za druhé je volána těsně před plánovaným položek nabídky v rozbalovací nabídce je potřeba vykreslit. V takovém případě Identifikátor odkazuje pouze na první položky nabídky a *m_pSubMenu* členské proměnné `CCmdUI` objektu bude mít hodnotu NULL.

To umožňuje povolit v rozbalovací nabídce liší od jeho položek nabídky, ale vyžaduje psaní kódu podle některé nabídky. Například ve vnořených nabídky s následující strukturou:

```Output
File>
    New>
    Sheet (ID_NEW_SHEET)
    Chart (ID_NEW_CHART)
```

Příkazy ID_NEW_SHEET a ID_NEW_CHART může být nezávisle na sobě povolena nebo zakázána. **Nový** rozbalovací nabídky by měla být povolená, pokud některý z nich je povolené.

Obslužná rutina příkazu pro ID_NEW_SHEET (první příkaz v místní nabídce) bude vypadat nějak takto:

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

Obslužná rutina příkazu pro ID_NEW_CHART by obslužná rutina příkazu normální aktualizace a podívejte se něco jako:

```cpp
void CMyApp::OnUpdateNewChart(CCmdUI* pCmdUI)
{
    pCmdUI->Enable(m_bCanCreateChart);
}
```

## <a name="oncommand-and-onbnclicked"></a>ON_COMMAND a ON_BN_CLICKED

Makra map zpráv pro **ON_COMMAND** a **ON_BN_CLICKED** jsou stejné. ID příkazu, který MFC příkazy a ovládání oznámení mechanismus směrování využívá jenom rozhodování, kam chcete směrovat. Ovládací prvek oznámení s kódem oznámení ovládacího prvku nula (**BN_CLICKED**) jsou interpretovány jako příkazy.

> [!NOTE]
> Ve skutečnosti všech zpráv s oznámením ovládacího prvku projít řetězu obslužná rutina příkazu. Například je technicky možné si můžete napsat obslužnou rutinu oznámení ovládacího prvku **EN_CHANGE** ve své třídě dokumentu. Nejedná obecně vhodné, protože praktické aplikace tato funkce se několik, tato funkce není podporována nástrojem ClassWizard a použití funkce může způsobit křehké kódu.

## <a name="disabling-the-automatic-disabling-of-button-controls"></a>Zakázat automatické vypnutí ovládací prvky tlačítek

Pokud umístit ovládací prvek tlačítko na panel dialogového okna, nebo v dialogovém okně použití voláte **CWnd::UpdateDialogControls** vlastními silami, všimnete si tohoto tlačítka, které nemají **ON_COMMAND** nebo **ON_UPDATE_COMMAND_UI** obslužné rutiny se automaticky deaktivuje pro vás rozhraní. V některých případech nemusíte mít obslužnou rutinu, ale můžete tlačítko zůstat zapnuté. Nejjednodušší způsob, jak toho dosáhnout, je přidání obslužná rutina příkazu fiktivní (jde udělat ClassWizard) a nedělat nic do něj.

## <a name="window-message-routing"></a>Směrování zpráv oken

Následující část popisuje některé pokročilejší témata na třídy knihovny MFC a jak je ovlivnit směrování zpráv Windows a další témata. Informace v tomto poli je pouze stručně popisuje. Odkazovat *knihovny tříd* podrobné informace o veřejných rozhraní API. Najdete zdrojový kód knihovny MFC pro další informace o podrobnosti implementace.

Najdete [technická Poznámka 17](../mfc/tn017-destroying-window-objects.md) pro podrobnosti o okně Vyčištění, velmi důležité tématu a vyhledat všechny **CWnd**-odvozené třídy.

## <a name="cwnd-issues"></a>CWnd – problémy

Členská funkce implementace **CWnd::OnChildNotify** poskytuje výkonnou a rozšiřitelnou architekturu pro podřízená okna (označované také jako ovládací prvky) k připojení nebo jinak informováni o zprávy, příkazy a ovládací prvek oznámení, které jejich nadřazené (nebo "vlastník"). Pokud podřízené okno (/ ovládací prvek) jazyka C++ je **CWnd** objektu samotného, virtuální funkce **OnChildNotify** je nejdříve volána s parametry z původní zprávy (to znamená, **MSG**struktura). Podřízené okno může opustit zprávu samostatně, jíst ho nebo upravit zprávu pro nadřazenou položku (vzácného).

Výchozí **CWnd** implementace zpracovává následující zprávy a používá **OnChildNotify** hook umožňující podřízené systému windows (ovládací prvky) k první přístupu na úrovni zprávy:

- **WM_MEASUREITEM** a **WM_DRAWITEM** (pro vlastní kreslení)

- **WM_COMPAREITEM** a **WM_DELETEITEM** (pro vlastní kreslení)

- **WM_HSCROLL** a **WM_VSCROLL**

- **WM_CTLCOLOR**

- **WM_PARENTNOTIFY**

Uvidíte **OnChildNotify** hook slouží ke změně vykreslené vlastníkem zprávy do samostatně nakreslit zpráv.

Kromě **OnChildNotify** hook, posuňte zprávy mají další směrování chování. Níže jsou uvedené podrobné informace o posuvníky a zdroje **WM_HSCROLL** a **WM_VSCROLL** zprávy.

## <a name="cframewnd-issues"></a>CFrameWnd – problémy

**CFrameWnd** třída poskytuje většinu směrování příkazů a uživatelského rozhraní aktualizací implementace. Používá se především pro hlavní okno rámce aplikace (**CWinApp::m_pMainWnd**), ale platí pro všechna okna rámce.

Hlavní okno rámce je v okně na řádku nabídek a je nadřazené ve stavovém řádku nebo zpráva řádku. Podrobnosti najdete výše uvedené informace o směrování příkazů a **WM_INITMENUPOPUP.**

**CFrameWnd** třída poskytuje správu aktivního zobrazení. Následující zprávy se směrují prostřednictvím aktivní zobrazení:

- Všechny zprávy příkazu (aktivního zobrazení získá první přístup k nim).

- **WM_HSCROLL** a **WM_VSCROLL** zprávy z na stejné úrovni posuvníky (viz níže).

- **WM_ACTIVATE** (a **WM_MDIACTIVATE** pro MDI) získat převedena na volání virtuální funkce **CView::OnActivateView**.

## <a name="cmdiframewndcmdichildwnd-issues"></a>CMDIFrameWnd – / CMDIChildWnd – problémy

Obě třídy okna rámce MDI odvozovat **CFrameWnd** a proto jsou povoleny pro stejný druh směrování příkazů a aktualizace uživatelského rozhraní součástí **CFrameWnd**. V typické aplikaci MDI, pouze hlavní okno rámce (to znamená **CMDIFrameWnd** objekt) obsahuje řádek nabídek a stavovým řádkem a proto je hlavní příčiny směrování implementace příkazu.

Obecné směrování schéma je, že aktivní podřízené okno MDI získá první přístup k příkazům. Výchozí hodnota **PreTranslateMessage –** funkce zpracování tabulky akcelerátoru pro obě podřízených oken MDI (první) a rámce MDI (v sekundách) a také standardní akcelerátory systémový příkaz MDI obvykle zpracovává  **TranslateMDISysAccel** (poslední).

## <a name="scroll-bar-issues"></a>Posuvník problémy

Při zpracování zprávy posuvníku (**WM_HSCROLL**/**OnHScroll** a/nebo **WM_VSCROLL**/**OnVScroll**), snažte se tak nespoléhá na posuvníku panelu zprávy, odkud napsat kód pro obslužnou rutinu. To není jenom o obecné Windows problém, protože posuvníku zprávy můžou pocházet z true posuvníku panelu Ovládací prvky nebo z **WS_HSCROLL**/**WS_VSCROLL** posuvníky, které nejsou ovládací prvky stavového řádku posuvníku.

Rozšiřuje knihovny MFC, která umožňuje pro ovládací prvky stavového řádku posouvání podřízených nebo v okně se přešli na stejné úrovni (ve skutečnosti nadřazené a podřízené vztah mezi posuvník a okno se možnosti posouvat určitý objekt může být libovolná). To je obzvláště důležité pro sdílené posuvníky s rozdělovače oken. Najdete [Technická poznámka 29](../mfc/tn029-splitter-windows.md) podrobné informace o provádění **CSplitterWnd** včetně Další informace o sdílených posuvníku panelu problémy.

Na straně poznámku, existují dva **CWnd** odvozené třídy, kde styly panelu přejděte na vytvořit, když jsou zachycena a nebudou předány Windows. Když předána rutině vytváření, **WS_HSCROLL** a **WS_VSCROLL** lze nezávisle na sobě nastavit, ale po vytvoření nedá změnit. Samozřejmě by měl přímo testovat nebo nastavit bity WS_SCROLL styl okna, které si vytvořilo.

Pro **CMDIFrameWnd** styly posuvníku panelu předáním **vytvořit** nebo **loadframe –** se používají k vytváření MDICLIENT. Pokud chcete mít posuvné oblasti MDICLIENT (jako Windows programový manažer) nastavte oba posuvníku styly (**WS_HSCROLL** &#124; **WS_VSCROLL**) pro styl použitý k vytvoření **CMDIFrameWnd**.

Pro **CSplitterWnd** styly posuvníku panelu použít lze na speciální sdílené posuvníky v oblasti rozdělovač. Pro statické rozdělovače oken bude obvykle není nastavena buď styl panelu přejděte. Dynamické rozdělovače oken, obvykle využívá posuvník sadu stylů pro směr rozdělíte, tedy **WS_HSCROLL** rozdělit řádky, **WS_VSCROLL** rozdělit sloupce.

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
