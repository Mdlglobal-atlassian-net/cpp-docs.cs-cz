---
title: 'TN022: Implementace standardních příkazů'
ms.date: 11/04/2016
f1_keywords:
- vc.commands
helpviewer_keywords:
- ID_PREV_PANE command [MFC]
- ID_APP_EXIT command [MFC]
- ID_NEXT_PANE command [MFC]
- ID_INDICATOR_REC command [MFC]
- ID_WINDOW_SPLIT command [MFC]
- ID_FILE_PRINT_PREVIEW command [MFC]
- ID_WINDOW_CASCADE command [MFC]
- ID_FILE_CLOSE command [MFC]
- ID_FILE_SAVE_COPY_AS command [MFC]
- ID_WINDOW_ARRANGE command [MFC]
- ID_EDIT_FIND command [MFC]
- ID_FILE_OPEN command [MFC]
- ID_FILE_PAGE_SETUP command [MFC]
- ID_OLE_VERB_FIRST command [MFC]
- ID_EDIT_UNDO command [MFC]
- ID_EDIT_CLEAR command [MFC]
- ID_INDICATOR_CAPS command [MFC]
- ID_HELP_INDEX command [MFC]
- commands [MFC], standard
- ID_FILE_PRINT_SETUP command [MFC]
- ID_DEFAULT_HELP command [MFC]
- ID_INDICATOR_SCRL command [MFC]
- ID_FILE_PRINT command [MFC]
- ID_INDICATOR_OVR command [MFC]
- ID_INDICATOR_KANA command [MFC]
- ID_EDIT_COPY command [MFC]
- ID_EDIT_REDO command [MFC]
- ID_EDIT_PASTE command [MFC]
- ID_OLE_INSERT_NEW command [MFC]
- ID_OLE_EDIT_LINKS command [MFC]
- ID_EDIT_PASTE_SPECIAL command [MFC]
- ID_INDICATOR_EXT command [MFC]
- ID_HELP_USING command [MFC]
- standard commands
- ID_VIEW_STATUS_BAR command [MFC]
- ID_FILE_SAVE_AS command [MFC]
- ID_EDIT_CLEAR_ALL command [MFC]
- ID_WINDOW_NEW command [MFC]
- ID_CONTEXT_HELP command [MFC]
- ID_EDIT_REPLACE command [MFC]
- ID_WINDOW_TILE_HORZ command [MFC]
- ID_APP_ABOUT command [MFC]
- TN022
- ID_VIEW_TOOLBAR command [MFC]
- ID_HELP command [MFC]
- ID_WINDOW_TILE_VERT command [MFC]
- ID_EDIT_CUT command [MFC]
- ID_FILE_UPDATE command [MFC]
- ID_EDIT_REPEAT command [MFC]
- ID_FILE_SAVE command [MFC]
- ID_EDIT_PASTE_LINK command [MFC]
- ID_EDIT_SELECT_ALL command [MFC]
- ID_FILE_NEW command [MFC]
- ID_INDICATOR_NUM command
ms.assetid: a7883b46-23f7-4870-ac3a-804aed9258b5
ms.openlocfilehash: 0f79aaaf59f12e226220e51681f64d0bf1131303
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50504335"
---
# <a name="tn022-standard-commands-implementation"></a>TN022: Implementace standardních příkazů

> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována, protože byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata mohou být nesprávné nebo zastaralé. Nejnovější informace se doporučuje vyhledat téma zájmu v dokumentaci online index.

Tato poznámka popisuje implementace standardních příkazů poskytované MFC 2.0. Čtení [Technická poznámka 21](../mfc/tn021-command-and-message-routing.md) první protože popisuje mechanismus používaný k implementaci mnoho standardních příkazů.

Tento popis se předpokládá znalost architektury MFC, rozhraní API a postup pro běžné programování. Zdokumentovaných, jakož i nedokumentované "implementace pouze" rozhraní API jsou popsány. Toto není místo, kde můžete začít seznamování se se funkce nebo jak programovat v knihovně MFC. Visual C++ naleznete další obecné informace a podrobnosti o zdokumentovaných rozhraní API.

## <a name="the-problem"></a>Problém

MFC definuje v souboru hlaviček AFXRES mnoho identifikátory standardních příkazů. H. Podpora rozhraní pro tyto příkazy se liší. Principy, kde a jak tříd rozhraní framework zpracovat tyto příkazy nebude pouze ukazují, jak interně pracuje rozhraní framework, ale bude obsahovat užitečné informace o postupu při přizpůsobení standardní implementace a představuje několik technik implementace vlastní obslužné rutiny příkazů.

## <a name="contents-of-this-technical-note"></a>Obsah této technické poznámky

Každé ID příkazu je popsána ve dvou částech:

- Název: symbolický název ID příkazu (například id_file_save –), za nímž následuje účel příkazu (například "uloží aktuální dokument") oddělených středníkem.

- Jeden nebo více odstavců popisující, které třídy implementace příkazu a co dělá výchozí implementace

Většina implementací výchozí příkaz se prewired v mapování zprávy základní třídy v rámci. Existují některé příkaz implementace, které vyžadují explicitní propojení v odvozené třídě. Tyto možnosti jsou popsány v části "Poznámky". Pokud zvolíte správné možnosti v AppWizard, se připojí těchto výchozích obslužných rutin pro vás v generované kostru aplikace.

## <a name="naming-convention"></a>Konvence vytváření názvů

Standardní příkazy dodržují jednoduché zásady vytváření názvů, který doporučujeme, abyste že je použít, pokud je to možné. Většina standardních příkazy jsou umístěny ve standardní umístění v řádku nabídek aplikace. Symbolický název příkazu začíná řetězcem "ID_", za nímž následuje název standardní místní nabídka, za nímž následuje název položky nabídky. Symbolický název se s podtržítkem slov velká písmena. Příkazy, které nemají názvy položek standardní nabídky Název logické příkaz je definován počínaje "ID_" (například id_next_pane –).

K označení příkazy, které mají být vázaný na položky nabídky, tlačítek panelu nástrojů nebo jiných objektů uživatelského rozhraní příkazového používáme předponu "ID_". Zpracování příkazů "ID_" obslužné rutiny příkazů by měl použít mechanismy ON_COMMAND a ON_UPDATE_COMMAND_UI příkaz architektury MFC.

Doporučujeme že používat standardní předponu "IDM_" pro položky nabídky, které nemají použijte příkaz architektury a kód specifický pro nabídky můžete povolit nebo zakázat, je nutné. Počet konkrétní příkazy nabídky samozřejmě by měl být malé, protože následující příkaz architektury MFC nejen umožňuje výkonnější obslužné rutiny příkazů (vzhledem k tomu, že bude fungovat s panely nástrojů), ale díky opakovaně použitelný kód obslužné rutiny příkazu.

## <a name="id-ranges"></a>ID oblasti

Najdete [Technická poznámka 20](../mfc/tn020-id-naming-and-numbering-conventions.md) podrobné informace o použití rozsahů ID v knihovně MFC.

Standardní příkazy knihovny MFC spadat do rozsahu 0xE000 k 0xEFFF. Prosím nespoléhejte na konkrétní hodnoty těchto identifikátorů vzhledem k tomu, že se může změnit v budoucích verzích knihovny.

Vaše aplikace by měla definovat jeho příkazů v rozsahu 0x8000 – 0xDFFF.

## <a name="standard-command-ids"></a>Identifikátory standardních příkazů

Pro každé ID příkazu je standardní zprávy řádku výzvy řetězec, který se nachází v souboru pokynů. RC. ID řetězce pro tuto nabídku řádku musí být stejný jako u ID příkazu.

- Id_file_new – vytvoří dokument nový nebo je prázdný.

    > [!NOTE]
    >  Je nutné připojit k vaší `CWinApp`-odvozené třídy mapy zpráv pro tuto funkci povolit.

   `CWinApp::OnFileNew` Tento příkaz odlišně v závislosti na počtu šablony dokumentů implementuje v aplikaci. Pokud existuje pouze jeden `CDocTemplate`, `CWinApp::OnFileNew` vytvoří nový dokument typu, jakož i správnou třídu rámce a zobrazení.

   Pokud existuje více než jeden `CDocTemplate`, `CWinApp::OnFileNew` vyzve uživatele, se dialogové okno (AFX_IDD_NEWTYPEDLG) aby select, který typ použít dokumentu. Vybrané `CDocTemplate` slouží k vytvoření dokumentu.

   Jednou z běžných přizpůsobení id_file_new – je poskytnout jiný a další grafické řadu typů dokumentů. V tomto případě můžete implementovat vlastní `CMyApp::OnFileNew` a umístěte ho do mapy zpráv místo `CWinApp::OnFileNew`. Není nutné volat implementaci základní třídy.

   Další běžné přizpůsobení id_file_new – je samostatný příkaz pro vytvoření dokumentu každého typu. V tomto případě byste měli definovat nový příkaz ID, například ID_FILE_NEW_CHART a ID_FILE_NEW_SHEET.

- Id_file_open – otevře existující dokument.

    > [!NOTE]
    >  Je nutné připojit k vaší `CWinApp`-odvozené třídy mapy zpráv pro tuto funkci povolit.

   `CWinApp::OnFileOpen` je velmi jednoduché provedení volání `CWinApp::DoPromptFileName` následovaný `CWinApp::OpenDocumentFile` s názvem souboru nebo cesta k souboru, který se otevře. `CWinApp` Implementace rutiny `DoPromptFileName` zobrazí standardní dialogové okno FileOpen a vyplní přípony souborů získané z aktuální šablony dokumentů.

   Jeden společný přizpůsobení id_file_open – je FileOpen dialogové okno Upravit nebo přidat další filtry souborů. Je doporučeným způsobem, jak přizpůsobit tak, nahraďte vlastním FileOpen dialogových oken a volání výchozí implementace `CWinApp::OpenDocumentFile` pomocí názvu souboru nebo cesta k dokumentu. Není nutné volat základní třídy.

- Id_file_close – ukončí aktuálně otevřeného dokumentu.

   `CDocument::OnFileClose` volání `CDocument::SaveModified` vyzvat uživatele k uložení dokumentu, pokud byla změněna a pak zavolá `OnCloseDocument`. Všechny uzavírací logiku, včetně zničení dokumentu, se provádí v `OnCloseDocument` rutiny.

    > [!NOTE]
    >  Id_file_close – funguje jinak než zprávu WM_CLOSE nebo příkaz SC_CLOSE systému, pošle se oknu rámce dokumenty. Zavřením okna se zavřít dokument pouze v případě poslední okno rámce zobrazují dokument. Zavírání dokumentů s id_file_close – nebude pouze zavřít dokument ale se zavřít všechna okna rámce zobrazují dokument.

- Id_file_save – uloží aktuální dokument.

   Implementace používá pomocnou rutinou `CDocument::DoSave` sloužící pro obě `OnFileSave` a `OnFileSaveAs`. Pokud ukládáte dokument, který nebyl uložen před (tedy nemá název cesty, třeba v případě funkci FileNew) nebo, který byl načten z dokumentu aplikace jen pro čtení `OnFileSave` logiky bude fungovat jako id_file_save_as – příkaz a požádat uživatele, aby zadejte nový název souboru . Vlastní proces, že soubor a způsobem ukládání se provádí prostřednictvím virtuální funkce `OnSaveDocument`.

   Existují dva běžné důvody pro přizpůsobení id_file_save –. Pro dokumenty, které neukládejte jednoduše odeberte položky nabídky id_file_save – a tlačítka panelu nástrojů z uživatelského rozhraní. Také se ujistěte, nikdy nesprávné dokumentu (to znamená, nikdy neměl volat `CDocument::SetModifiedFlag`) a rozhraní nikdy nezpůsobí dokumentu, který má být uložen. Pro dokumenty, které ukládají jistě než souboru na disku, definovat nový příkaz pro danou operaci.

   V případě třídy `COleServerDoc`, id_file_save – se používá pro uložení souboru (pro normální dokumenty) a aktualizaci souboru (pro embedded dokumenty).

   Pokud data vašeho dokumentu jsou uloženy v souborech jednotlivých disků, ale nechcete použít výchozí `CDocument` serializovat implementaci, kterou byste měli přepsat `CDocument::OnSaveDocument` místo `OnFileSave`.

- Id_file_save_as – uloží aktuální dokument pod jiným názvem souboru.

   `CDocument::OnFileSaveAs` Implementace používá stejný `CDocument::DoSave` pomocné rutiny jako `OnFileSave`. `OnFileSaveAs` Příkaz probíhá stejně jako id_file_save – Pokud žádný název souboru před uložit dokumenty. `COleServerDoc::OnFileSaveAs` implementuje logiku datový soubor normální dokument uložit nebo uložit dokument na serveru představující objekt OLE vložená v jiné aplikaci jako samostatný soubor.

   Pokud upravíte logiky id_file_save –, budete pravděpodobně chtít přizpůsobit id_file_save_as – podobným způsobem nebo operace "Uložit jako" se nemusí vztahovat na váš dokument. Pokud není potřeba, můžete odebrat položky nabídky v panelu nabídky.

- Id_file_save_copy_as – uloží kopii aktuální dokument pod novým názvem.

   `COleServerDoc::OnFileSaveCopyAs` Implementace se velmi podobá `CDocument::OnFileSaveAs`, s tím rozdílem, že objekt dokumentu není "připojené" do základního souboru po uložení. To znamená pokud dokument v paměti "změnil" před uložit, to je stále "upravit". Kromě toho tento příkaz nemá žádný vliv na cestu nebo název uložená v dokumentu.

- Id_file_update – upozorní kontejner pro vložený dokument uložit.

   `COleServerDoc::OnUpdateDocument` Implementace jednoduše notifiies kontejneru, který má být uložen vkládání. Kontejner pak zavolá odpovídající OLE rozhraní API za účelem uložení vloženého objektu.

- Id_file_page_setup – vyvolá dialogové okno nastavení a rozložení stránky specifické pro aplikaci.

   V současné době neexistuje žádný standardní pro tento dialog a rozhraní nemá žádnou výchozí implementaci tohoto příkazu.

   Pokud se rozhodnete implementovat tento příkaz, doporučujeme že použít toto ID příkazu.

- Id_file_print_setup – vyvolat standardní dialogové okno Nastavení tisku.

    > [!NOTE]
    >  Je nutné připojit k vaší `CWinApp`-odvozené třídy mapy zpráv pro tuto funkci povolit.

   Tento příkaz spustí standardní nastavení tisku dialog, který umožňuje uživateli upravit tiskárny a tisku nastavení pro alespoň tento dokument nebo maximálně všechny dokumenty v této aplikaci. Chcete-li změnit výchozí nastavení tiskárny pro celý systém musí pomocí ovládacího panelu.

   `CWinApp::OnFilePrintSetup` je velmi jednoduchá implementace vytváření `CPrintDialog` objektu a volání `CWinApp::DoPrintDialog` implementaci funkce. Tím se nastaví výchozí nastavení tiskárny aplikace.

   Běžné potřeby přizpůsobení tento příkaz je umožnit pro každý dokument nastavení tiskárny, které by měla být uložena s dokumentem při uložení. Provedete to tak, měli byste přidat obslužnou rutinu mapování zpráv ve vaší `CDocument` třídu, která vytvoří `CPrintDialog` objektu, inicializuje ji s atributy odpovídající tiskárny (obvykle *hDevMode* a *hDevNames je*), zavolejte `CPrintDialog::DoModal`a uložte nastavení změněné tiskárny. Robustní implementaci byste se podívat na provádění `CWinApp::DoPrintDialog` pro zjišťování chyb a `CWinApp::UpdatePrinterSelection` pro práci s rozumné výchozí hodnoty a sledování změn systémová tiskárny.

- Id_file_print – standardní tisk aktuálního dokumentu

    > [!NOTE]
    >  Je nutné připojit k vaší `CView`-odvozené třídy mapy zpráv pro tuto funkci povolit.

   Tento příkaz vypíše aktuální dokument nebo přesněji, spustí proces tisku, který zahrnuje volání standardní dialogové okno Tisk a spuštěný modul tisku.

   `CView::OnFilePrint` implementuje tento příkaz a hlavní smyčka tisku. Volání virtuální `CView::OnPreparePrinting` na příkazový řádek uživatele pomocí dialogového okna Tisk. Potom připraví výstup řadič domény do tiskárny, zobrazí dialogové okno Tisk průběhu (AFX_IDD_PRINTDLG) a odešle `StartDoc` řídicí do tiskárny. `CView::OnFilePrint` také obsahuje hlavní smyčka tisku orientované na stránce. Pro každou stránku volá virtuální `CView::OnPrepareDC` následovaný `StartPage` řídicí a volání virtuální `CView::OnPrint` pro danou stránku. Po dokončení, virtuální `CView::OnEndPrinting` je zavolána, a zavření dialogového okna Tisk průběhu.

   Architektura pro tisk MFC slouží k propojení mnoha různými způsoby pro náhled tisku a tisk. Obvykle zjistíte různých `CView` přepisovatelné funkce vhodný pro všechny stránky objektově orientovaný tiskové úlohy. Pouze v případě aplikace, která používá tiskárny pro výstup orientovaný jiné stránky by pro vás potřeba nahradit id_file_print – implementace.

- Id_file_print_preview – zadejte režim náhledu pro aktuální dokument.

    > [!NOTE]
    >  Je nutné připojit k vaší `CView`-odvozené třídy mapy zpráv pro tuto funkci povolit.

   `CView::OnFilePrintPreview` spuštění režimu náhledu tisku voláním zdokumentovaných pomocnou funkci `CView::DoPrintPreview`. `CView::DoPrintPreview` je hlavní modul pro náhled tisku smyčky, stejně jako `OnFilePrint` je hlavní modul pro tisk smyčky.

   Náhled tisku operace lze přizpůsobit mnoha různými způsoby předáním různými parametry pro `DoPrintPreview`. Najdete [Technická poznámka 30](../mfc/tn030-customizing-printing-and-print-preview.md)níž se probírá některé podrobnosti náhledu tisku a jak ji přizpůsobit.

- ID_FILE_MRU_FILE1... FILE16 Rozsah ID příkazu pro naposledy použitých souborů **seznamu**.

   `CWinApp::OnUpdateRecentFileMenu` aktualizace uživatelského rozhraní obslužná rutina příkazu, který je jedním z pokročilejší použití mechanismu ON_UPDATE_COMMAND_UI je. V nabídce prostředku třeba s ID ID_FILE_MRU_FILE1 definovat pouze jednu položku. Tuto položku nabídky zpočátku zakázáno.

   Seznam rozrůstá, další nabídky, které položky jsou přidány do seznamu položek jako seznamu naposledy použitých položek. Standardní `CWinApp` implementace výchozí hodnota je standardní limit čtyř naposledy použitých souborů. Můžete změnit výchozí voláním `CWinApp::LoadStdProfileSettings` s hodnotou větší nebo menší. Seznam naposledy použitých je uložen v vaší aplikace. Soubor INI. Načíst seznam ve vaší aplikaci `InitInstance` fungovat, pokud zavoláte `LoadStdProfileSettings`a je uložen při ukončení aplikace. Obslužná rutina naposledy použitých aktualizací příkazu uživatelského rozhraní se převést i absolutní cesty relativní cesty pro zobrazení v nabídce Soubor.

   `CWinApp::OnOpenRecentFile` je ON_COMMAND obslužná rutina, která provádí skutečný příkaz. Jednoduše získá název souboru ze seznamu naposledy použitých a volání `CWinApp::OpenDocumentFile`, která vykonává všechnu práci otevření souboru a aktualizuje se seznam naposledy použitých.

   Přizpůsobení Tato obslužná rutina příkazu se nedoporučuje.

- Id_edit_clear – vymaže aktuální výběr

   Aktuálně neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat pro každou `CView`-odvozené třídy.

   `CEditView` poskytuje implementaci pro tento příkaz pomocí `CEdit::Clear`. Příkaz je zakázaná, pokud nebyla vybrána žádná aktuální položka.

   Pokud se rozhodnete implementovat tento příkaz, doporučujeme že použít toto ID příkazu.

- Id_edit_clear_all – Vymaže celý dokument.

   Aktuálně neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat pro každou `CView`-odvozené třídy.

   Pokud se rozhodnete implementovat tento příkaz, doporučujeme že použít toto ID příkazu. Najdete v ukázce MFC kurzu [SCRIBBLE](../visual-cpp-samples.md) příklad implementace.

- Id_edit_copy – zkopíruje aktuální výběr do schránky.

   Aktuálně neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat pro každou `CView`-odvozené třídy.

   `CEditView` poskytuje implementaci tohoto příkazu, který zkopíruje aktuálně vybraného textu do schránky jako použití CF_TEXT `CEdit::Copy`. Příkaz je zakázaná, pokud nebyla vybrána žádná aktuální položka.

   Pokud se rozhodnete implementovat tento příkaz, doporučujeme že použít toto ID příkazu.

- Id_edit_cut – vyjme aktuální výběr do schránky.

   Aktuálně neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat pro každou `CView`-odvozené třídy.

   `CEditView` poskytuje implementaci tohoto příkazu, která Vyjme aktuálně vybraného textu do schránky jako použití CF_TEXT `CEdit::Cut`. Příkaz je zakázaná, pokud nebyla vybrána žádná aktuální položka.

   Pokud se rozhodnete implementovat tento příkaz, doporučujeme že použít toto ID příkazu.

- Id_edit_find – začíná operace hledání zobrazí dialogové okno nemodální hledání.

   Aktuálně neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat pro každou `CView`-odvozené třídy.

   `CEditView` poskytuje implementaci tohoto příkazu, která volá funkci pomocné rutiny implementace `OnEditFindReplace` použít a uložit předchozí nastavení najít/nahradit v privátní implementace proměnné. `CFindReplaceDialog` Třída se používá ke správě nemodální dialogové okno pro výzvu uživateli.

   Pokud se rozhodnete implementovat tento příkaz, doporučujeme že použít toto ID příkazu.

- Id_edit_paste – vloží aktuální obsah schránky.

   Aktuálně neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat pro každou `CView`-odvozené třídy.

   `CEditView` poskytuje implementaci tohoto příkazu, která kopíruje data aktuálního schránky nahrazení vybraný text pomocí `CEdit::Paste`. Příkaz je zakázaná, pokud neexistuje žádný **CF_TEXT** ve schránce.

   `COleClientDoc` poskytuje obslužná rutina příkazu uživatelského rozhraní aktualizace pro tento příkaz. Jestliže schránky neobsahuje Vložitelný položky OLE/objektu, příkaz se deaktivuje. Zodpovídáte za zápis obslužné rutiny pro skutečný příkaz provedete skutečné vložení. Pokud aplikaci OLE lze rovněž vložit dalších formátů, byste měli poskytnout vlastní aktualizace uživatelského rozhraní obslužná rutina příkazu v zobrazení nebo dokumentu (to znamená, někde před `COleClientDoc` v cíl směrování příkazů).

   Pokud se rozhodnete implementovat tento příkaz, doporučujeme že použít toto ID příkazu.

   Pro nahrazení standardní implementace technologie OLE, použijte `COleClientItem::CanPaste`.

- Id_edit_paste_link – vloží odkaz na aktuální obsah schránky.

   Aktuálně neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat pro každou `CView`-odvozené třídy.

   `COleDocument` poskytuje obslužná rutina příkazu uživatelského rozhraní aktualizace pro tento příkaz. Jestliže schránky neobsahuje propojovací položky/objekt OLE, příkaz se deaktivuje. Zodpovídáte za zápis obslužné rutiny pro skutečný příkaz provedete skutečné vložení. Pokud aplikaci OLE lze rovněž vložit dalších formátů, byste měli poskytnout vlastní aktualizace uživatelského rozhraní obslužná rutina příkazu v zobrazení nebo dokumentu (to znamená, někde před `COleDocument` v cíl směrování příkazů).

   Pokud se rozhodnete implementovat tento příkaz, doporučujeme že použít toto ID příkazu.

   Pro nahrazení standardní implementace technologie OLE, použijte `COleClientItem::CanPasteLink`.

- Id_edit_paste_special – vloží aktuální obsah schránky s možnostmi.

   Aktuálně neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat pro každou `CView`-odvozené třídy. MFC neposkytuje toto dialogové okno.

   Pokud se rozhodnete implementovat tento příkaz, doporučujeme že použít toto ID příkazu.

- Id_edit_repeat – Zopakuje poslední operaci.

   Aktuálně neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat pro každou `CView`-odvozené třídy.

   `CEditView` poskytuje implementaci pro tento příkaz zopakovat poslední akci najít. Soukromá implementace proměnné pro poslední hledání se používají. Příkaz je zakázaná, pokud nelze najít k pokusu o.

   Pokud se rozhodnete implementovat tento příkaz, doporučujeme že použít toto ID příkazu.

- Id_edit_replace – zahájí operaci nahrazení zobrazí dialogové okno nemodální nahradit.

   Aktuálně neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat pro každou `CView`-odvozené třídy.

   `CEditView` poskytuje implementaci tohoto příkazu, která volá funkci pomocné rutiny implementace `OnEditFindReplace` použít a uložit předchozí nastavení najít/nahradit v privátní implementace proměnné. `CFindReplaceDialog` Třída se používá ke správě nemodální dialogové okno, které se zobrazí výzva.

   Pokud se rozhodnete implementovat tento příkaz, doporučujeme že použít toto ID příkazu.

- Id_edit_select_all – vybere celý dokument.

   Aktuálně neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat pro každou `CView`-odvozené třídy.

   `CEditView` poskytuje implementaci tohoto příkazu, který vybere celý text v dokumentu. Příkaz je zakázaná, pokud neexistuje žádný text k výběru.

   Pokud se rozhodnete implementovat tento příkaz, doporučujeme že použít toto ID příkazu.

- Id_edit_undo – vrátí zpět poslední operaci.

   Aktuálně neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat pro každou `CView`-odvozené třídy.

   `CEditView` poskytuje implementaci tohoto příkazu, `CEdit::Undo`. Příkaz je zakázaná, pokud `CEdit::CanUndo` vrátí hodnotu FALSE.

   Pokud se rozhodnete implementovat tento příkaz, doporučujeme že použít toto ID příkazu.

- Id_edit_redo – provede znovu poslední operaci.

   Aktuálně neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat pro každou `CView`-odvozené třídy.

   Pokud se rozhodnete implementovat tento příkaz, doporučujeme že použít toto ID příkazu.

- Id_window_new – Otevře další okno pro aktivní dokument.

   `CMDIFrameWnd::OnWindowNew` implementuje této výkonné funkce s použitím šablony dokumentu aktuálního dokumentu vytvořit jiný rámec obsahující jiného zobrazení aktuálního dokumentu.

   Jako většina více dokumentů (MDI) interface příkazy nabídky okna příkaz je zakázán, pokud neexistuje žádná aktivní podřízené okno MDI.

   Přizpůsobení Tato obslužná rutina příkazu se nedoporučuje. Pokud chcete zadat příkaz, který vytvoří další zobrazení nebo okna s rámečkem, pravděpodobně bude lepší vzorec inventing vlastní příkaz. Můžete naklonovat kód z `CMDIFrameWnd::OnWindowNew` a upravte je tak konkrétní rámce a zobrazení třídy podle vašich představ.

- Id_window_arrange – Uspořádá ikony v dolní části okna MDI.

   `CMDIFrameWnd` implementuje standardní příkaz MDI v implementaci pomocné funkci `OnMDIWindowCmd`. Této pomocné rutiny mapuje identifikátory příkazů zpráv Windows MDI a může proto podělím o spoustu toho kód.

   Stejně jako většinu příkazy nabídky okna MDI příkaz zakázaná, pokud neexistuje žádná aktivní podřízené okno MDI.

   Přizpůsobení Tato obslužná rutina příkazu se nedoporučuje.

- Id_window_cascade – Cascades windows tak, aby se.

   `CMDIFrameWnd` implementuje standardní příkaz MDI v implementaci pomocné funkci `OnMDIWindowCmd`. Této pomocné rutiny mapuje identifikátory příkazů zpráv Windows MDI a může proto podělím o spoustu toho kód.

   Stejně jako většinu příkazy nabídky okna MDI příkaz zakázaná, pokud neexistuje žádná aktivní podřízené okno MDI.

   Přizpůsobení Tato obslužná rutina příkazu se nedoporučuje.

- Id_window_tile_horz – dlaždice windows vodorovně.

   Tento příkaz je implementována v `CMDIFrameWnd` stejně jako id_window_cascade –, s výjimkou jiná zpráva Windows MDI se používá pro operaci.

   Měli byste vybrat výchozí orientace dlaždici pro vaši aplikaci. Můžete to provést tak, že změníte ID pro položku nabídky "Tile" okno id_window_tile_horz – nebo id_window_tile_vert –.

- Windows id_window_tile_vert – dlaždice svisle.

   Tento příkaz je implementována v `CMDIFrameWnd` stejně jako id_window_cascade –, s výjimkou jiná zpráva Windows MDI se používá pro operaci.

   Měli byste vybrat výchozí orientace dlaždici pro vaši aplikaci. Můžete to provést tak, že změníte ID pro položku nabídky "Tile" okno id_window_tile_horz – nebo id_window_tile_vert –.

- Id_window_split – klávesnice rozhraní rozdělovač.

   `CView` zpracování tohoto příkazu `CSplitterWnd` implementace. Součást okno s rozdělovačem. při zobrazení tohoto příkazu bude delegovat na funkci implementace `CSplitterWnd::DoKeyboardSplit`. To umístí příčky v režimu, který vám umožní uživatelům klávesnice a rozdělit nebo zrušit rozdělení okno s rozdělovačem.

   Tento příkaz je zakázán, pokud zobrazení není rozdělovač.

   Přizpůsobení Tato obslužná rutina příkazu se nedoporučuje.

- Id_app_about – vyvolá dialogové okno o.

   Neexistuje žádný standardní implementace pro pole o aplikace. Výchozí aplikace vytvořená Průvodcem AppWizard vytvoříte dialogové okno vlastní třídu pro vaši aplikaci a použijte ho jako o pole. AppWizard také zapíše triviální příkaz obslužná rutina, která zpracovává tento příkaz a vyvolá dialogové okno.

   Tento příkaz se téměř vždy implementovat.

- Id_app_exit – ukončete aplikaci.

   `CWinApp::OnAppExit` zpracuje tento příkaz odešle zprávu WM_CLOSE hlavního okna aplikace. Standardní ukončování aplikace (vás vyzve k zadání změny souborů a tak dále) je zpracována `CFrameWnd` implementace.

   Přizpůsobení Tato obslužná rutina příkazu se nedoporučuje. Přepsání `CWinApp::SaveAllModified` nebo `CFrameWnd` zavření logiky se doporučuje.

   Pokud se rozhodnete implementovat tento příkaz, doporučujeme že použít toto ID příkazu.

- Témata id_help_index – obsahuje seznam nápovědy z. HLP souboru.

    > [!NOTE]
    >  Je nutné připojit k vaší `CWinApp`-odvozené třídy mapy zpráv pro tuto funkci povolit.

   `CWinApp::OnHelpIndex` Tento příkaz zpracovává triviálně voláním `CWinApp::WinHelp`.

   Přizpůsobení Tato obslužná rutina příkazu se nedoporučuje.

- Id_help_using – zobrazí nápovědu o tom, jak použít nápovědu.

    > [!NOTE]
    >  Je nutné připojit k vaší `CWinApp`-odvozené třídy mapy zpráv pro tuto funkci povolit.

   `CWinApp::OnHelpUsing` Tento příkaz zpracovává triviálně voláním `CWinApp::WinHelp`.

   Přizpůsobení Tato obslužná rutina příkazu se nedoporučuje.

- Režim nápovědy id_context_help – vloží SHIFT + F1.

    > [!NOTE]
    >  Je nutné připojit k vaší `CWinApp`-odvozené třídy mapy zpráv pro tuto funkci povolit.

   `CWinApp::OnContextHelp` Tento příkaz se stará nastavení režimu kurzor nápovědy, zadáním modální smyčky a čekání na uživatele vyberte okno můžete zobrazit nápovědu pro. Najdete [Technická poznámka 28](../mfc/tn028-context-sensitive-help-support.md) podrobné informace o implementaci MFC nápovědy.

   Přizpůsobení Tato obslužná rutina příkazu se nedoporučuje.

- Id_help – poskytuje nápovědu pro aktuální kontext

    > [!NOTE]
    >  Je nutné připojit k vaší `CWinApp`-odvozené třídy mapy zpráv pro tuto funkci povolit.

   `CWinApp::OnHelp` Tento příkaz zpracovává tím, že získáme kontextu odbornou pomoc pro aktuální kontext aplikace. To řeší jednoduché nápovědy klávesy F1, nápovědu pro okna se zprávou a tak dále. Najdete [Technická poznámka 28](../mfc/tn028-context-sensitive-help-support.md) pro další podrobnosti o MFC implementace.

   Přizpůsobení Tato obslužná rutina příkazu se nedoporučuje.

- Id_default_help – zobrazuje výchozí nápovědu pro kontext

    > [!NOTE]
    >  Je nutné připojit k vaší `CWinApp`-odvozené třídy mapy zpráv pro tuto funkci povolit.

   Tento příkaz se obvykle mapuje na `CWinApp::OnHelpIndex`.

   Obslužná rutina různých příkazu lze zadat v případě potřeby rozdíl mezi výchozími nápovědy a index nápovědy.

- Id_next_pane – přejde na další podokno

   `CView` zpracování tohoto příkazu `CSplitterWnd` implementace. Součást okno s rozdělovačem. při zobrazení tohoto příkazu bude delegovat na funkci implementace `CSplitterWnd::OnNextPaneCmd`. Aktivnímu zobrazení. to se přesune na další podokno v příčky.

   Tento příkaz je zakázán, pokud zobrazení není rozdělovač nebo je k dispozici žádné další podokno přejdete na.

   Přizpůsobení Tato obslužná rutina příkazu se nedoporučuje.

- Id_prev_pane – přejde na předchozí podokno

   `CView` zpracování tohoto příkazu `CSplitterWnd` implementace. Součást okno s rozdělovačem. při zobrazení tohoto příkazu bude delegovat na funkci implementace `CSplitterWnd::OnNextPaneCmd`. Tímto přesunete aktivní zobrazení na předchozí podokno v příčky.

   Tento příkaz je zakázán, pokud zobrazení není rozdělovač nebo je k dispozici žádné předchozí podokno. Chcete-li přejít k.

   Přizpůsobení Tato obslužná rutina příkazu se nedoporučuje.

- Id_ole_insert_new – vloží nový objekt OLE

   Aktuálně neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat pro vaši `CView`-odvozené třídy nové položky OLE/objekt vložit na aktuální výběr.

   Tento příkaz by měly implementovat všechny klientské aplikace OLE. AppWizard, s možností OLE vytvoří kostru provádění `OnInsertObject` ve třídě zobrazení, který bude mít k dokončení.

   Najdete v ukázce MFC OLE [OCLIENT](../visual-cpp-samples.md) příklad pro úplnou implementaci tohoto příkazu.

- Id_ole_edit_links – úpravy odkazů OLE

   `COleDocument` zpracuje tento příkaz pomocí poskytované MFC provádění standardního dialogového okna odkazů OLE. Implementace tohoto dialogového okna je přístupný prostřednictvím `COleLinksDialog` třídy. Pokud aktuální dokument neobsahuje žádné odkazy, příkaz je zakázané.

   Přizpůsobení Tato obslužná rutina příkazu se nedoporučuje.

- ID_OLE_VERB_FIRST –... Poslední rozsah ID pro příkazy OLE

   `COleDocument` používá tento rozsah ID příkazu pro příkazy podporované v aktuálně vybrané položky nebo objektu OLE. Rozsah musí být od daného typu objekt nebo položky OLE může podporovat nula nebo více vlastních příkazů. V nabídce vaší aplikace měli byste mít jednu položku s ID id_ole_verb_first –. Při spuštění programu v nabídce bude aktualizována popis příkaz příslušné nabídky (nebo místní nabídky s mnoha příkazů). Správa nabídce OLE se zpracovává souborem `AfxOleSetEditMenu`, Hotovo v obslužná rutina příkazu uživatelského rozhraní aktualizace pro tento příkaz.

   Neexistují žádné explicitní příkaz obslužné rutiny pro zpracování každé ID příkazu, který v tomto rozsahu. `COleDocument::OnCmdMsg` přepsáno zachytávat všechny identifikátory příkazů v tomto rozsahu, proměnit založený na nule příkaz čísla a spustit server pro tuto operaci (pomocí `COleClientItem::DoVerb`).

   Přizpůsobení ani jiné užívání tohoto rozsahu ID příkazu se nedoporučuje.

- Id_view_toolbar – Přepíná panel nástrojů zapnutí a vypnutí

   `CFrameWnd` zpracuje tento příkaz a obslužná rutina příkazu pro aktualizaci uživatelského rozhraní, chcete-li přepnout viditelné stav panelu nástrojů. Panelu nástrojů musí být podřízené okno rámce s ID AFX_IDW_TOOLBAR podřízené okno. Obslužná rutina příkazu ve skutečnosti přepíná viditelnost okna nástrojů. `CFrameWnd::RecalcLayout` slouží k ho překreslit oknem rámce s panelem nástrojů ve stavu nový. Obslužná rutina příkazu pro aktualizaci uživatelského rozhraní ověří položky nabídky po viditelné panelu nástrojů.

   Přizpůsobení Tato obslužná rutina příkazu se nedoporučuje. Pokud chcete přidat další panely nástrojů, můžete klonovat a upravit obslužná rutina příkazu a obslužná rutina příkazu pro aktualizaci uživatelského rozhraní pro tento příkaz.

- Id_view_status_bar – přepíná stavový řádek zapnutí a vypnutí

   Tento příkaz je implementována v `CFrameWnd` stejně jako id_view_toolbar –, s výjimkou ID (AFX_IDW_STATUS_BAR) se používá jiné podřízené okno.

## <a name="update-only-command-handlers"></a>Obslužné rutiny aktualizace příkazů

Několik identifikátory standardních příkazů se používají jako ukazatele ve stavovém řádku. Tyto stejné příkazu pro aktualizaci uživatelského rozhraní mechanismu pro zpracování zobrazíte pomocí jejich aktuální vizuální stav během doby nečinnosti aplikace. Protože nemůže být vybrána uživatelem (to znamená, budete nelze odeslat panelu stavového řádku stav), pak nemá smysl mít obslužnou rutinu ON_COMMAND pro tyto identifikátory příkazů.

- Id_indicator_caps –: Limit zámku ukazatel.

- Id_indicator_num –: NUM lock ukazatel.

- Id_indicator_scrl –: SCRL zámek ukazatel.

- Id_indicator_kana –: KANA uzamknout ukazatel (platí jenom pro japonské systémy).

Všechny tyto tři jsou implementovány v `CFrameWnd::OnUpdateKeyIndicator`, implementace pomocné rutiny, který používá ID příkazu pro mapování na příslušné virtuální klávesy. Běžnou implementaci povolí nebo zakáže (podokna stavu zakázáno = žádný text) `CCmdUI` objekt v závislosti na tom, jestli je aktuálně uzamčená odpovídající virtuální klávesy.

Přizpůsobení Tato obslužná rutina příkazu se nedoporučuje.

- Id_indicator_ext –: Rozšířený výběr ukazatele.

- Id_indicator_ovr –: Indikátor přepisování.

- Id_indicator_rec –: Zaznamenávání indikátoru.

Aktuálně neexistuje žádná standardní implementace pro tyto ukazatele.

Pokud se rozhodnete implementovat tyto indikátory, doporučujeme, abyste používali tyto identifikátory ukazatele a zachování řazení ukazatelů ve stavovém řádku (to znamená, že v tomto pořadí: EXT, Zakončení, číslo, SCRL, přes, dop.).

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

