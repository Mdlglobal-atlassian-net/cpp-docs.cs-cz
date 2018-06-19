---
title: 'TN022: Standardní příkazy implementace | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.commands
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dea42f4bd33281e65696791677bdd81a921a59e6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385522"
---
# <a name="tn022-standard-commands-implementation"></a>TN022: Implementace standardních příkazů
> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována vzhledem k tomu, že byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata může být zastaralý nebo není správný. Nejnovější informace se doporučuje, vyhledejte téma týkající se v indexu online dokumentaci.  
  
 Tato poznámka popisuje implementace standardních příkazů poskytované MFC 2.0. Čtení [Technická poznámka 21](../mfc/tn021-command-and-message-routing.md) první protože popisují mechanismy použít k implementaci řadu standardní příkazy.  
  
 Tento popis předpokládá znalost architektury MFC, rozhraní API a běžnou praxí při programování. Zdokumentovaných, jakož i nedokumentovanými "implementace pouze" rozhraní API jsou popsány. Toto není místo pro začátek učení o funkce nebo jak v prostředí MFC programu. Visual C++ najdete další obecné informace a podrobnosti o zdokumentovaných rozhraní API.  
  
## <a name="the-problem"></a>Problém  
 MFC definuje mnoho identifikátory standardních příkazů v záhlaví souboru AFXRES. H. Podpora Framework pro tyto příkazy se liší. Pochopení, kdy a jak framework třídy zpracování těchto příkazů nebude pouze ukážeme, jak interně pracuje rozhraní framework, ale bude poskytují užitečné informace o tom, jak přizpůsobit standardní implementace a naučit můžete několik techniky pro implementaci vlastní obslužné rutiny příkazů.  
  
## <a name="contents-of-this-technical-note"></a>Obsah této technické poznámky  
 Každý ID příkazu je podrobněji popsaná dvě části:  
  
-   Název: symbolického názvu ID příkazu (například **id_file_save –**) a potom podle účelu příkazu (například "uloží aktuální dokument") oddělené dvojtečkou.  
  
-   Jeden nebo více odstavců popisující, které třídy implementaci příkazu a jaké jsou výchozí implementace  
  
 Většina výchozí implementace příkazu jsou prewired v rozhraní framework mapy zpráv základní třídy. Existují některé příkaz implementace, které vyžadují explicitní kabeláž v odvozené třídě. Tyto možnosti jsou popsány v části "Note". Pokud jste vybrali správné možnosti v objekty AppWizard, se připojí tyto výchozí obslužné rutiny pro vás v generované kostru aplikace.  
  
## <a name="naming-convention"></a>Konvence vytváření názvů  
 Standardní příkazy podle jednoduché zásady vytváření názvů, který doporučujeme vám, že používáte-li to možné. Většina standardní příkazy jsou umístěné standardní místech v řádku nabídek aplikace. Symbolický název příkazu začíná "ID_", za nímž následuje název standardní místní nabídky, za nímž následuje název položky nabídky. Symbolický název je velkými písmeny s podtržítka-rozložení slov. Pro příkazy, které nemají názvy položek standardní nabídky, je název logického příkazu definována počínaje "ID_" (například **id_next_pane –**).  
  
 Používáme předponu "ID_" udávajících příkazy, které mají být vázána na položky nabídky, tlačítek panelu nástrojů nebo jiné objekty uživatelského rozhraní příkazu. Zpracování příkazů "ID_" obslužné rutiny příkazů by měl používat `ON_COMMAND` a `ON_UPDATE_COMMAND_UI` mechanismy MFC příkaz architektura.  
  
 Doporučujeme, aby že pro položky nabídky, které není použijte příkaz architektura a kódu pro konkrétní nabídky povolení a zakázání je třeba používáte standardní předponou "IDM_". Počet určité příkazy nabídky samozřejmě by měl být malé vzhledem k tomu následující příkaz architektury MFC pouze díky výkonnější obslužné rutiny příkazů (vzhledem k tomu, že bude fungovat s panely nástrojů), ale umožňuje opakovaně použitelný kód obslužná rutina příkazu.  
  
## <a name="id-ranges"></a>ID rozsahů  
 Naleznete [Technická poznámka 20](../mfc/tn020-id-naming-and-numbering-conventions.md) další podrobnosti o použití rozsahů ID v prostředí MFC.  
  
 Standardní příkazy MFC spadat do rozsahu 0xE000 k 0xEFFF. Prosím nespoléhejte na konkrétní hodnoty těchto identifikátorů vzhledem k tomu, že se může v budoucích verzích knihovny měnit.  
  
 Vaše aplikace měli definovat jeho příkazy v rozsahu 0x8000 k 0xDFFF.  
  
## <a name="standard-command-ids"></a>Identifikátory standardních příkazů  
 Pro každý ID příkazu je výzva řetězec standardní zprávy řádek, který naleznete v souboru pokynů. RC. Řetězec ID této nabídky výzvy musí být stejné jako pro ID příkazu.  
  
-   Id_file_new – vytvoří dokument nové nebo je prázdný.  
  
    > [!NOTE]
    >  Musíte se připojit k vaší `CWinApp`-odvozené třídy a mapy zpráv pro povolení této funkce.  
  
     `CWinApp::OnFileNew` implementuje tento příkaz odlišně v závislosti na počtu šablony dokumentů v aplikaci. Pokud existuje pouze jeden `CDocTemplate`, `CWinApp::OnFileNew` vytvoří nový dokument typu, jakož i správnou třídu rámec a zobrazení.  
  
     Pokud je více než jedna `CDocTemplate`, `CWinApp::OnFileNew` vyzve uživatele, se dialogové okno (**AFX_IDD_NEWTYPEDLG**) aby vyberte typů dokumentů, které se mají použít. Vybraný `CDocTemplate` se používá k vytvoření dokumentu.  
  
     Jeden běžné přizpůsobení `ID_FILE_NEW` je poskytovat jiné a další grafické výběr typů dokumentů. V takovém případě můžete implementovat vlastní **CMyApp::OnFileNew** a umístěte ji na mapě zpráva místo `CWinApp::OnFileNew`. Není nutné volat implementaci základní třídy.  
  
     Další běžné přizpůsobení `ID_FILE_NEW` je poskytnout samostatný příkaz pro vytvoření dokumentu každého typu. V takovém případě byste měli definovat nový příkaz ID, například ID_FILE_NEW_CHART a ID_FILE_NEW_SHEET.  
  
-   Id_file_open – otevře existující dokument.  
  
    > [!NOTE]
    >  Musíte se připojit k vaší `CWinApp`-odvozené třídy a mapy zpráv pro povolení této funkce.  
  
     `CWinApp::OnFileOpen` je velmi jednoduchá implementace volání **CWinApp::DoPromptFileName** následuje `CWinApp::OpenDocumentFile` s názvem souboru nebo cesta k otevření souboru. `CWinApp` Implementace rutiny **DoPromptFileName** přináší standardní FileOpen – dialogové okno a doplní s příponami souborů získali z aktuální šablony dokumentů.  
  
     Jeden běžné přizpůsobení `ID_FILE_OPEN` je FileOpen – dialogové okno Upravit a přidat další filtry souborů. Doporučeným způsobem, jak přizpůsobit toto je výchozí implementace nahraďte vlastní FileOpen – dialogové okno a volání `CWinApp::OpenDocumentFile` s názvem souboru nebo cesta k dokumentu. Není nutné volat základní třídy.  
  
-   Id_file_close – zavře otevřený dokument.  
  
     **CDocument::OnFileClose** volání `CDocument::SaveModified` pro vyzvání uživatele k uložení dokumentu, pokud byla změněna a pak zavolá `OnCloseDocument`. Všechny ukončovací logiku, včetně zničení dokumentu, se provádí v `OnCloseDocument` rutiny.  
  
    > [!NOTE]
    >  **Id_file_close –** funguje jinak z `WM_CLOSE` zpráva nebo **SC_CLOSE** příkaz systému odeslána do okna s rámečkem dokumenty. Zavřením okna bude dokument zavřít, pouze v případě poslední rámce okna s dokumentu. Zavírání dokumentů s **id_file_close –** nebude pouze zavřete dokument, ale bude zavřít všechna okna s rámečkem zobrazující dokumentu.  
  
-   Id_file_save – uloží aktuální dokument.  
  
     Implementace používá pomocnou rutinou **CDocument::DoSave** sloužící pro obě **OnFileSave** a **OnFileSaveAs**. Pokud uložíte dokument, který ještě nebyl uložen před (to znamená, nemá název cesty, jako v případě funkci FileNew) nebo z jen pro čtení dokumentu, který byl načten **OnFileSave** logiku bude fungovat stejně jako **id_file_save_as –** příkazů a požádat uživatele o zadejte nový název souboru. Vlastní proces otevření souboru a díky ukládání se provádí prostřednictvím virtuální funkce `OnSaveDocument`.  
  
     Existují dvě běžné příčiny, chcete-li přizpůsobit **id_file_save –**. Pro dokumenty, které neukládejte, stačí odstranit **id_file_save –** položek nabídky a tlačítka panelu nástrojů z uživatelského rozhraní. Také se ujistěte, nikdy nesprávné dokumentu (to znamená, nikdy volat `CDocument::SetModifiedFlag`) a rozhraní nikdy způsobí uložit dokument. Pro dokumenty, které musí být zhruba uložit do jiného než soubor na disku definujte nový příkaz pro tuto operaci.  
  
     U `COleServerDoc`, **id_file_save –** se používá pro uložení souboru (pro běžné dokumenty) i aktualizaci souboru (pro embedded dokumentů).  
  
     Pokud dokument data se ukládají v jednotlivých disků soubory, ale nechcete použít výchozí **CDocument** serializovat implementace, by měly přepsat `CDocument::OnSaveDocument` místo **OnFileSave**.  
  
-   Id_file_save_as – uloží aktuální dokument pod jiným názvem souboru.  
  
     **CDocument::OnFileSaveAs** implementace používá stejný **CDocument::DoSave** pomocnou rutinou jako **OnFileSave**. **OnFileSaveAs** příkaz se zpracovává stejně jako **id_file_save –** kdyby měl žádný název souboru před uložení dokumentů. **COleServerDoc::OnFileSaveAs** implementuje logiku uložit soubor dat normální dokumentu nebo uložte dokument serveru představující objekt OLE vložených v nějaké jiné aplikaci jako samostatný soubor.  
  
     Pokud upravíte logiku **id_file_save –**, budete pravděpodobně chtít přizpůsobit **id_file_save_as –** v podobně nebo se operace "Uložit jako" nemusí vztahovat k dokumentu. Položky nabídky můžete odebrat z nabídky panelu, pokud není nutné.  
  
-   Id_file_save_copy_as – ukládá kopie aktuální dokument pod novým názvem.  
  
     **COleServerDoc::OnFileSaveCopyAs** implementace je velmi podobné **CDocument::OnFileSaveAs**kromě toho, že objekt dokument není "připojené" k základní souboru po uložení. To znamená pokud v paměti "změny dokumentu" před uložení, ji je stále "upravit". Kromě toho tento příkaz nemá žádný vliv na cestu nebo název uložené v dokumentu.  
  
-   Id_file_update – upozorní kontejner pro uložení vložený dokument.  
  
     `COleServerDoc::OnUpdateDocument` Implementace jednoduše notifiies kontejner, který má být uložen vložení. Kontejner pak zavolá příslušné OLE rozhraní API a uložte vložený objekt.  
  
-   Id_file_page_setup – vyvolá dialogovým instalační program nebo rozložení stránky specifické pro aplikaci.  
  
     Aktuálně neexistuje žádná standard pro toto dialogové okno a rozhraní nemá žádnou výchozí implementaci tohoto příkazu.  
  
     Pokud zvolíte možnost implementovat tento příkaz, doporučujeme že použít toto ID příkazu.  
  
-   Id_file_print_setup – vyvolání standardního dialogového okna Nastavení tisku.  
  
    > [!NOTE]
    >  Musíte se připojit k vaší `CWinApp`-odvozené třídy a mapy zpráv pro povolení této funkce.  
  
     Tento příkaz vyvolá standardní instalaci tiskových dialog, který umožňuje uživateli upravit tiskárny a tisku nastavení pro alespoň tento dokument nebo maximálně všechny dokumenty v této aplikaci. Chcete-li změnit výchozí nastavení tiskárny pro celý systém musí používat ovládací panely.  
  
     `CWinApp::OnFilePrintSetup` je velmi jednoduchá implementace vytváření `CPrintDialog` objekt a volání **CWinApp::DoPrintDialog** implementace funkce. Nastaví tato výchozí nastavení tiskárny aplikace.  
  
     Běžné potřebu přizpůsobení tento příkaz je umožnit pro každý dokument nastavení tiskárny, které by měly být uložené s dokumentem, když se uloží. Uděláte to tak měli byste přidat obslužnou rutinu map zpráv ve vaší **CDocument** třídu, která vytvoří `CPrintDialog` objektu, inicializuje s atributy odpovídající tiskárny (obvykle **hDevMode** a **hDevNames je**), volání **CPrintDialog::DoModal,** a uložte nastavení změněné tiskárny. Pro implementaci robustní, by měla vypadat v provádění **CWinApp::DoPrintDialog** pro zjišťování chyb a **CWinApp::UpdatePrinterSelection** pro práci s rozumný výchozí hodnoty a sledování změn systémové tiskárny.  
  
-   Id_file_print – standardní tisk aktuálního dokumentu  
  
    > [!NOTE]
    >  Musíte se připojit k vaší `CView`-odvozené třídy a mapy zpráv pro povolení této funkce.  
  
     Tento příkaz vytiskne aktuálním dokumentu nebo více správně spustí tisk procesu, který zahrnuje vyvolání dialogovém okně Standardní tisku a spouštění modul tisku.  
  
     **CView::OnFilePrint** implementuje tento příkaz a hlavní tiskové smyčky. Volá virtuální `CView::OnPreparePrinting` výzvu uživateli s dialogovém okně tisku. Potom ho připraví výstup řadič domény, který se do tiskárny, otevře dialogové okno tisku průběhu (**AFX_IDD_PRINTDLG**) a odešle `StartDoc` řídicí na tiskárnu. **CView::OnFilePrint** také obsahuje hlavní stránkové tiskové smyčky. Pro jednotlivé stránky, volá virtuální `CView::OnPrepareDC` následuje `StartPage` řídicí a volání virtuální `CView::OnPrint` pro tuto stránku. Až budete hotoví, virtuální `CView::OnEndPrinting` je volána, a Tisk dialogové okno průběhu je uzavřený.  
  
     Architektura pro tisk MFC slouží k připojení mnoha různými způsoby pro tisku a přehled tisku. Za normálních okolností najdete různé `CView` přepisovatelné funkce pro všechny stránkové tiskové úlohy. Pouze v případě aplikace, která používá tiskárny pro jiné stránky orientovaných na výstupu by měl zjistit potřeba nahradit **id_file_print –** implementace.  
  
-   Id_file_print_preview – zadejte režim náhledu pro aktuální dokument.  
  
    > [!NOTE]
    >  Musíte se připojit k vaší `CView`-odvozené třídy a mapy zpráv pro povolení této funkce.  
  
     **CView::OnFilePrintPreview** spustí režimu náhledu tisku voláním zdokumentovaných pomocné funkce **CView::DoPrintPreview**. **CView::DoPrintPreview** je modul hlavní smyčky náhledu tisku, stejně jako **OnFilePrint** je hlavní modul pro tisk smyčky.  
  
     Operaci náhledu tisku lze přizpůsobit mnoha různými způsoby pomocí jiné parametry k předání **DoPrintPreview**. Naleznete [Technická poznámka 30](../mfc/tn030-customizing-printing-and-print-preview.md), která popisuje některé podrobnosti náhledu tisku a jak přizpůsobit.  
  
-   **ID_FILE_MRU_FILE1**... **FILE16** rozsah ID příkazu pro naposledy použitých souborů `list`.  
  
     **CWinApp::OnUpdateRecentFileMenu** je příkaz uživatelského rozhraní obslužnou rutinu aktualizace, je jedním z dalších pokročilých použití `ON_UPDATE_COMMAND_UI` mechanismus. V nabídce prostředku, je nutné definovat pouze jednu položku s ID **ID_FILE_MRU_FILE1**. Daná položka nabídky původně vypnutý.  
  
     Seznam roste, další nabídky, které položky budou přidány do seznamu položek jako naposledy použitých. Standardní `CWinApp` výchozí implementace standardní limitu čtyři naposledy použitých souborů. Můžete změnit výchozí voláním `CWinApp::LoadStdProfileSettings` s hodnotou větší nebo menší. Seznam naposledy použitých je uložen do aplikace. Soubor INI. V seznamu je načten do vaší aplikace `InitInstance` funkce při volání `LoadStdProfileSettings`a je uložen při ukončení aplikace. Obslužná rutina naposledy použitých aktualizace příkaz uživatelského rozhraní se převést i absolutní cesty relativní cesty pro zobrazení v nabídce Soubor.  
  
     **CWinApp::OnOpenRecentFile** je `ON_COMMAND` obslužná rutina, která provede příkaz skutečný. Jednoduše získá název souboru ze seznamu naposledy použitých a volání `CWinApp::OpenDocumentFile`, na které se všechny práci při otevření souboru a aktualizuje seznam naposledy použitých.  
  
     Přizpůsobení Tato obslužná rutina příkazu se nedoporučuje.  
  
-   Id_edit_clear – vymaže aktuální výběr  
  
     Aktuálně neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat pro každou `CView`-odvozené třídy.  
  
     `CEditView` poskytuje implementaci pro tento příkaz pomocí `CEdit::Clear`. Příkaz vypnutá, pokud není aktuální výběr.  
  
     Pokud zvolíte možnost implementovat tento příkaz, doporučujeme že použít toto ID příkazu.  
  
-   Id_edit_clear_all – Vymaže celý dokument.  
  
     Aktuálně neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat pro každou `CView`-odvozené třídy.  
  
     Pokud zvolíte možnost implementovat tento příkaz, doporučujeme že použít toto ID příkazu. Viz ukázka MFC kurzu [KLIKYHÁKY](../visual-cpp-samples.md) příklad implementace.  
  
-   Id_edit_copy – zkopíruje aktuální výběr do schránky.  
  
     Aktuálně neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat pro každou `CView`-odvozené třídy.  
  
     `CEditView` poskytuje implementaci pro tento příkaz, který zkopíruje aktuálně vybraný text do schránky jako CF_TEXT pomocí `CEdit::Copy`. Příkaz vypnutá, pokud není aktuální výběr.  
  
     Pokud zvolíte možnost implementovat tento příkaz, doporučujeme že použít toto ID příkazu.  
  
-   Id_edit_cut – vyjme aktuální výběr do schránky.  
  
     Aktuálně neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat pro každou `CView`-odvozené třídy.  
  
     `CEditView` poskytuje implementaci pro tento příkaz, který ořízne aktuálně vybraný text do schránky jako CF_TEXT pomocí `CEdit::Cut`. Příkaz vypnutá, pokud není aktuální výběr.  
  
     Pokud zvolíte možnost implementovat tento příkaz, doporučujeme že použít toto ID příkazu.  
  
-   Id_edit_find – zahájení operace hledání zobrazíte dialog nemodální najít.  
  
     Aktuálně neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat pro každou `CView`-odvozené třídy.  
  
     `CEditView` poskytuje implementaci pro tento příkaz, který volá pomocné funkce implementace **OnEditFindReplace** můžete použít a uložit do proměnné privátní implementace předchozí nastavení vyhledání a nahrazení. `CFindReplaceDialog` Třída se používá ke správě dialogového okna bez režimu pro výzvy pro uživatele.  
  
     Pokud zvolíte možnost implementovat tento příkaz, doporučujeme že použít toto ID příkazu.  
  
-   Id_edit_paste – vloží aktuální obsah schránky.  
  
     Aktuálně neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat pro každou `CView`-odvozené třídy.  
  
     `CEditView` poskytuje implementaci pro tento příkaz, který zkopíruje aktuální data ze schránky, nahraďte vybraný text použití `CEdit::Paste`. Příkaz vypnutá, pokud neexistuje žádné **CF_TEXT** do schránky.  
  
     **COleClientDoc** právě poskytuje obslužná rutina příkazu uživatelského rozhraní aktualizace pro tento příkaz. Pokud schránka neobsahuje li položky OLE nebo objekt, bude příkaz zakázána. Jste zodpovědní za zápis obslužné rutiny pro příkaz skutečné provedete skutečné vkládání. Pokud aplikaci OLE můžete také vložit dalších formátů, měli byste jim poskytnout vlastní aktualizace uživatelského rozhraní obslužná rutina příkazu v zobrazení nebo dokumentu (tedy někde před **COleClientDoc** v cílové směrování příkazů).  
  
     Pokud zvolíte možnost implementovat tento příkaz, doporučujeme že použít toto ID příkazu.  
  
     Nahrazuje standardní implementace OLE, použijte `COleClientItem::CanPaste`.  
  
-   Id_edit_paste_link – vloží odkaz z aktuální obsah schránky.  
  
     Aktuálně neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat pro každou `CView`-odvozené třídy.  
  
     `COleDocument` právě poskytuje obslužná rutina příkazu uživatelského rozhraní aktualizace pro tento příkaz. Pokud schránka neobsahuje korelovat OLE položky nebo objekt, bude příkaz zakázána. Jste zodpovědní za zápis obslužné rutiny pro příkaz skutečné provedete skutečné vkládání. Pokud aplikaci OLE můžete také vložit dalších formátů, měli byste jim poskytnout vlastní aktualizace uživatelského rozhraní obslužná rutina příkazu v zobrazení nebo dokumentu (tedy někde před `COleDocument` v cílové směrování příkazů).  
  
     Pokud zvolíte možnost implementovat tento příkaz, doporučujeme že použít toto ID příkazu.  
  
     Nahrazuje standardní implementace OLE, použijte `COleClientItem::CanPasteLink`.  
  
-   Id_edit_paste_special – vloží aktuální obsah schránky s možnostmi.  
  
     Aktuálně neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat pro každou `CView`-odvozené třídy. MFC neposkytuje toto dialogové okno.  
  
     Pokud zvolíte možnost implementovat tento příkaz, doporučujeme že použít toto ID příkazu.  
  
-   Id_edit_repeat – Zopakuje poslední akci.  
  
     Aktuálně neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat pro každou `CView`-odvozené třídy.  
  
     `CEditView` poskytuje implementaci tohoto příkazu se zopakovat poslední akci najít. Proměnné privátní implementace poslední hledání se používají. Příkaz vypnutá, pokud nelze k pokusu o hledání.  
  
     Pokud zvolíte možnost implementovat tento příkaz, doporučujeme že použít toto ID příkazu.  
  
-   Id_edit_replace – zahájí operaci nahrazení zobrazíte dialog nemodální nahradit.  
  
     Aktuálně neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat pro každou `CView`-odvozené třídy.  
  
     `CEditView` poskytuje implementaci pro tento příkaz, který volá pomocné funkce implementace **OnEditFindReplace** můžete použít a uložit do proměnné privátní implementace předchozí nastavení vyhledání a nahrazení. `CFindReplaceDialog` Třída se používá ke správě dialogového okna bez režimu, který zobrazí výzvu.  
  
     Pokud zvolíte možnost implementovat tento příkaz, doporučujeme že použít toto ID příkazu.  
  
-   Id_edit_select_all – vybere celý dokument.  
  
     Aktuálně neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat pro každou `CView`-odvozené třídy.  
  
     `CEditView` poskytuje implementaci pro tento příkaz, který vybere veškerý text v dokumentu. Příkaz vypnutá, pokud neexistuje žádný text k výběru.  
  
     Pokud zvolíte možnost implementovat tento příkaz, doporučujeme že použít toto ID příkazu.  
  
-   Id_edit_undo – vrátí zpět poslední akci.  
  
     Aktuálně neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat pro každou `CView`-odvozené třídy.  
  
     `CEditView` poskytuje implementaci tohoto příkazu, pomocí `CEdit::Undo`. Příkaz vypnutá, pokud `CEdit::CanUndo` vrátí hodnotu FALSE.  
  
     Pokud zvolíte možnost implementovat tento příkaz, doporučujeme že použít toto ID příkazu.  
  
-   Id_edit_redo – znovu provede poslední akci.  
  
     Aktuálně neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat pro každou `CView`-odvozené třídy.  
  
     Pokud zvolíte možnost implementovat tento příkaz, doporučujeme že použít toto ID příkazu.  
  
-   Id_window_new – Otevře další okno v aktivním dokumentu.  
  
     **CMDIFrameWnd::OnWindowNew** implementuje Tato výkonná funkce pomocí šablony dokumentu aktuálního dokumentu vytvořit jiný rámec obsahující jiného zobrazení aktuálního dokumentu.  
  
     Jako většina více dokumentů (MDI) rozhraní příkazy nabídky okna příkaz vypnutá, pokud neexistuje žádné aktivní podřízeného okna MDI.  
  
     Přizpůsobení Tato obslužná rutina příkazu se nedoporučuje. Pokud chcete zadat příkaz, který vytvoří další zobrazení nebo okna s rámečkem, pravděpodobně bude lepší inventing vlastní příkaz. Může klonovat kód z **CMDIFrameWnd::OnWindowNew** a upravit tak, aby určité rámec a zobrazení třídy libovolně.  
  
-   Id_window_arrange – Uspořádá ikony v dolní části okna MDI  
  
     `CMDIFrameWnd` implementuje tento standardní příkaz MDI v implementaci pomocné funkci **OnMDIWindowCmd**. Tato pomocná mapuje identifikátory příkazů na zprávy oken MDI a proto můžete sdílet velké množství kódu.  
  
     Jako většina příkazy nabídky okna MDI příkaz vypnutá, pokud neexistuje žádné aktivní podřízeného okna MDI.  
  
     Přizpůsobení Tato obslužná rutina příkazu se nedoporučuje.  
  
-   Id_window_cascade – Cascades windows, aby se překrývala.  
  
     `CMDIFrameWnd` implementuje tento standardní příkaz MDI v implementaci pomocné funkci **OnMDIWindowCmd**. Tato pomocná mapuje identifikátory příkazů na zprávy oken MDI a proto můžete sdílet velké množství kódu.  
  
     Jako většina příkazy nabídky okna MDI příkaz vypnutá, pokud neexistuje žádné aktivní podřízeného okna MDI.  
  
     Přizpůsobení Tato obslužná rutina příkazu se nedoporučuje.  
  
-   Id_window_tile_horz – dlaždice windows vodorovně.  
  
     Tento příkaz je implementována ve `CMDIFrameWnd` stejně jako **id_window_cascade –**, s výjimkou různé zprávy oken MDI se používá pro operaci.  
  
     Měli byste vybrat výchozí orientaci dlaždice pro vaši aplikaci. To provedete tak, že změníte Identifikátor pro položku nabídky "Dlaždici" okno buď **id_window_tile_horz –** nebo **id_window_tile_vert –**.  
  
-   Id_window_tile_vert – dlaždice windows svisle.  
  
     Tento příkaz je implementována ve `CMDIFrameWnd` stejně jako **id_window_cascade –**, s výjimkou různé zprávy oken MDI se používá pro operaci.  
  
     Měli byste vybrat výchozí orientaci dlaždice pro vaši aplikaci. To provedete tak, že změníte Identifikátor pro položku nabídky "Dlaždici" okno buď **id_window_tile_horz –** nebo **id_window_tile_vert –**.  
  
-   Id_window_split – klávesnice rozhraní rozdělovače.  
  
     `CView` Tento příkaz pro zpracovává `CSplitterWnd` implementace. Pokud zobrazení je součástí rozděleném okně, bude tento příkaz delegovat na funkci implementace `CSplitterWnd::DoKeyboardSplit`. To umístí rozdělovače v režimu, který vám umožní uživatelům klávesnice rozdělení nebo zrušit rozdělení rozděleném okně.  
  
     Tento příkaz je zakázán, pokud není v rozdělovač zobrazení.  
  
     Přizpůsobení Tato obslužná rutina příkazu se nedoporučuje.  
  
-   Id_app_about – vyvolá dialogové okno o.  
  
     Neexistuje žádná standardní implementace pro aplikace o pole. Výchozí objekty AppWizard vytvořené aplikace bude vytvoření třídy dialogového okna vlastní pro vaši aplikaci a používat jako vaše o pole. Objekty AppWizard bude také zapisovat trivial obslužná rutina, která zpracovává tento příkaz a vyvolá dialogové okno.  
  
     Téměř vždy implementujete tento příkaz.  
  
-   Id_app_exit – ukončit aplikaci.  
  
     **CWinApp::OnAppExit** zpracovává tento příkaz odesláním `WM_CLOSE` zprávu, která se hlavní okno aplikace. Standardní vypínání aplikace (výzvy k potvrzení změny souborů a tak dále) jsou zpracována `CFrameWnd` implementace.  
  
     Přizpůsobení Tato obslužná rutina příkazu se nedoporučuje. Přepsání `CWinApp::SaveAllModified` nebo `CFrameWnd` zavření logiku se doporučuje.  
  
     Pokud zvolíte možnost implementovat tento příkaz, doporučujeme že použít toto ID příkazu.  
  
-   Id_help_index – uvádí Nápověda témata z. HLP soubor.  
  
    > [!NOTE]
    >  Musíte se připojit k vaší `CWinApp`-odvozené třídy a mapy zpráv pro povolení této funkce.  
  
     `CWinApp::OnHelpIndex` Tento příkaz zpracovává trivially voláním `CWinApp::WinHelp`.  
  
     Přizpůsobení Tato obslužná rutina příkazu se nedoporučuje.  
  
-   Id_help_using – zobrazí nápovědu k použití nápovědy.  
  
    > [!NOTE]
    >  Musíte se připojit k vaší `CWinApp`-odvozené třídy a mapy zpráv pro povolení této funkce.  
  
     `CWinApp::OnHelpUsing` Tento příkaz zpracovává trivially voláním `CWinApp::WinHelp`.  
  
     Přizpůsobení Tato obslužná rutina příkazu se nedoporučuje.  
  
-   Id_context_help – zadá SHIFT + F1 režimu nápovědy.  
  
    > [!NOTE]
    >  Musíte se připojit k vaší `CWinApp`-odvozené třídy a mapy zpráv pro povolení této funkce.  
  
     `CWinApp::OnContextHelp` nastavení režimu kurzor nápovědy, zadáním modální smyčky a čekání uživateli vybrat a údržbu za účelem získání nápovědy zpracovává tento příkaz. Naleznete [Technická poznámka 28](../mfc/tn028-context-sensitive-help-support.md) další podrobnosti o implementace MFC pomoct.  
  
     Přizpůsobení Tato obslužná rutina příkazu se nedoporučuje.  
  
-   Id_help – poskytuje nápovědu pro aktuální kontext  
  
    > [!NOTE]
    >  Musíte se připojit k vaší `CWinApp`-odvozené třídy a mapy zpráv pro povolení této funkce.  
  
     `CWinApp::OnHelp` Tento příkaz zpracovává získáním kontext správnou nápovědu pro aktuální kontext aplikace. Zpracovává jednoduché F1 – Nápověda, nápovědy na okna zpráv a tak dále. Naleznete [Technická poznámka 28](../mfc/tn028-context-sensitive-help-support.md) pro další podrobnosti o knihovny MFC pomoct implementace.  
  
     Přizpůsobení Tato obslužná rutina příkazu se nedoporučuje.  
  
-   Id_default_help – zobrazí výchozí nápovědy pro kontext  
  
    > [!NOTE]
    >  Musíte se připojit k vaší `CWinApp`-odvozené třídy a mapy zpráv pro povolení této funkce.  
  
     Tento příkaz je obvykle namapována na `CWinApp::OnHelpIndex`.  
  
     Obslužná rutina různých příkazu lze zadat, pokud se požaduje nerozlišuje mezi výchozího nápovědy a indexu nápovědy.  
  
-   Id_next_pane – přejde na další podokno  
  
     `CView` Tento příkaz pro zpracovává `CSplitterWnd` implementace. Pokud zobrazení je součástí rozděleném okně, bude tento příkaz delegovat na funkci implementace **CSplitterWnd::OnNextPaneCmd**. Tím se posunou aktivní zobrazení do dalšího podokna v rozdělovače.  
  
     Tento příkaz je zakázán, pokud toto zobrazení není rozdělovač nebo je k dispozici žádné další podokno přejít na.  
  
     Přizpůsobení Tato obslužná rutina příkazu se nedoporučuje.  
  
-   Id_prev_pane – přejde na předchozí podokno  
  
     `CView` Tento příkaz pro zpracovává `CSplitterWnd` implementace. Pokud zobrazení je součástí rozděleném okně, bude tento příkaz delegovat na funkci implementace **CSplitterWnd::OnNextPaneCmd**. Tím se posunou aktivní zobrazení v rozdělovače do předchozího podokna.  
  
     Tento příkaz je zakázán, pokud toto zobrazení není rozdělovač nebo je k dispozici žádné předchozí podokno přejít na.  
  
     Přizpůsobení Tato obslužná rutina příkazu se nedoporučuje.  
  
-   Id_ole_insert_new – vloží nový objekt OLE  
  
     Aktuálně neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat pro vaši `CView`-odvozené třídy vložit novou položku OLE nebo objekt v aktuálním výběru.  
  
     Všechny klientské aplikace OLE by měla implementovat tento příkaz. Objekty AppWizard, s parametrem OLE vytvoří "kostra" provádění **OnInsertObject** ve třídě zobrazení, která bude mít k dokončení.  
  
     Viz ukázka MFC OLE [OCLIENT](../visual-cpp-samples.md) příklad pro úplnou implementaci tohoto příkazu.  
  
-   Id_ole_edit_links – upraví OLE odkazy  
  
     `COleDocument` Tento příkaz zpracovává pomocí zadané MFC implementace standardní dialog odkazy OLE. Implementace toto dialogové okno, které je přístupné přes `COleLinksDialog` třídy. Pokud aktuální dokument neobsahuje žádné odkazy, příkaz je zakázané.  
  
     Přizpůsobení Tato obslužná rutina příkazu se nedoporučuje.  
  
-   ID_OLE_VERB_FIRST –... Poslední rozsah ID pro příkazy OLE  
  
     `COleDocument` používá tento rozsah ID příkazu pro příkazy nepodporuje aktuálně vybrané položky nebo objekt OLE. Toto musí být rozsahu vzhledem k tomu, že daný typ položky nebo objektu OLE může podporovat nula nebo více vlastních příkazů. V nabídce aplikace, musí mít jednu položku nabídky s ID **id_ole_verb_first –**. Při spuštění programu v nabídce bude aktualizována popis příkaz příslušné nabídky (nebo místní nabídky s mnoha příkazů). Správu nabídce OLE se zpracovává souborem `AfxOleSetEditMenu`, done v obslužná rutina příkazu uživatelského rozhraní aktualizace pro tento příkaz.  
  
     Neexistují žádné explicitní příkaz obslužné rutiny pro zpracování každé ID příkazu, který v tomto rozsahu. **COleDocument::OnCmdMsg** přepsána depeše všechny identifikátory příkazů v tomto rozsahu, je převádět na nule příkaz čísla a server pro tento příkaz spusťte (pomocí `COleClientItem::DoVerb`).  
  
     Přizpůsobení nebo jiných použijte tento příkaz rozsah ID se nedoporučuje.  
  
-   Id_view_toolbar – přepíná panelu nástrojů zapnout a vypnout  
  
     `CFrameWnd` zpracuje tento příkaz a aktualizace obslužná rutina uživatelského rozhraní pro přepnutí viditelné stavu panelu nástrojů. Panelu nástrojů musí být podřízeného okna rámce s ID podřízené okno `AFX_IDW_TOOLBAR`. Obslužná rutina ve skutečnosti přepíná viditelnost panelu nástrojů okna. `CFrameWnd::RecalcLayout` slouží k ho překreslit okno rámečku panelu nástrojů v jeho nového stavu. Aktualizace obslužná rutina uživatelského rozhraní kontroluje položky nabídky, pokud je zobrazen panel nástrojů.  
  
     Přizpůsobení Tato obslužná rutina příkazu se nedoporučuje. Pokud chcete přidat další panely nástrojů, budete chtít klonovat a úpravám obslužná rutina příkazu a aktualizace obslužná rutina uživatelského rozhraní pro tento příkaz.  
  
-   Id_view_status_bar – přepíná na stavovém řádku zapnout a vypnout  
  
     Tento příkaz je implementována ve `CFrameWnd` stejně jako **id_view_toolbar –**, s výjimkou a jiné podřízené okno ID (**AFX_IDW_STATUS_BAR**) se používá.  
  
## <a name="update-only-command-handlers"></a>Obslužné rutiny aktualizace příkazů  
 Několik identifikátory standardních příkazů slouží jako indikátory ve stavovém řádku. Tyto použijte stejný příkaz aktualizace uživatelského rozhraní mechanismu pro zpracování pro zobrazení jejich aktuální stav visual během doby nečinnosti aplikace. Vzhledem k tomu, že je není možné vybrat uživatelem (nelze tedy push panelu podokno stavu), pak nemá smysl mít `ON_COMMAND` obslužné rutiny pro tyto identifikátory příkazů.  
  
-   **Id_indicator_caps –** : Indikátor uzamčení Zakončení.  
  
-   **Id_indicator_num –** : NUM zámku indikátoru.  
  
-   **Id_indicator_scrl –** : SCRL zámku indikátoru.  
  
-   **Id_indicator_kana –** : znaky abeced KANA zámku ukazatele (platí pouze pro japonské systémy).  
  
 Všechny tyto tři jsou implementované v **CFrameWnd::OnUpdateKeyIndicator**, implementace pomocné rutiny, která používá ID příkazu k mapování na příslušný virtuální klíč. Běžná implementace povolí nebo zakáže (podokna stav Zakázáno = žádný text) `CCmdUI` objekt v závislosti na tom, zda je příslušný virtuální klíč aktuálně uzamčena.  
  
 Přizpůsobení Tato obslužná rutina příkazu se nedoporučuje.  
  
-   **Id_indicator_ext –: EXT**zakončeno vyberte indikátoru.  
  
-   **Id_indicator_ovr –: OV**e**R**vytvořit indikátoru.  
  
-   **Id_indicator_rec –: REC**ording indikátoru.  
  
 Aktuálně neexistuje žádná standardní implementace pro tyto ukazatele.  
  
 Pokud zvolíte možnost implementovat tyto ukazatele, doporučujeme, abyste používali tyto ukazatele ID a údržbu, řazení indikátory ve stavovém řádku (který je v tomto pořadí: EXT, Zakončení, NUM, SCRL, indikátor přes, dop.).  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

