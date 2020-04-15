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
ms.openlocfilehash: 5c7041f40c7e30592f642d29d9d02812a9596864
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370400"
---
# <a name="tn022-standard-commands-implementation"></a>TN022: Implementace standardních příkazů

> [!NOTE]
> Následující technická poznámka nebyla aktualizována od doby, kdy byla poprvé zahrnuta do online dokumentace. V důsledku toho mohou být některé postupy a témata zastaralé nebo nesprávné. Chcete-li získat nejnovější informace, doporučujeme vyhledat téma zájmu v online indexu dokumentace.

Tato poznámka popisuje implementace standardních příkazů poskytované knihovnou MFC 2.0. Nejprve si přečtěte [technickou poznámku 21,](../mfc/tn021-command-and-message-routing.md) protože popisuje mechanismy používané k implementaci mnoha standardních příkazů.

Tento popis předpokládá znalost architektury knihovny MFC, rozhraní API a běžné programovací praxe. Jsou popsána zdokumentovaná i nedokumentovaná pravidla API "pouze implementace". Toto není místo, kde začít učit o funkcích nebo jak programovat v knihovně MFC. Podrobnější informace o dokumentovaných souborech API naleznete v jazyce Visual C++.

## <a name="the-problem"></a>Problém

Knihovna MFC definuje mnoho standardních ID příkazů v souboru záhlaví AFXRES. H. Podpora rozhraní pro tyto příkazy se liší. Pochopení, kde a jak framework třídy zpracovávat tyto příkazy nejen ukázat, jak rozhraní funguje interně, ale poskytne užitečné informace o tom, jak přizpůsobit standardní implementace a naučí několik technik pro implementaci vlastní příkaz obslužné rutiny.

## <a name="contents-of-this-technical-note"></a>Obsah této technické poznámky

Každé ID příkazu je popsáno ve dvou částech:

- Název: symbolický název ID příkazu (například ID_FILE_SAVE) následovaný účelem příkazu (například "uloží aktuální dokument") odděleným dvojtečkou.

- Jeden nebo více odstavců popisujících, které třídy implementují příkaz a co výchozí implementace dělá

Většina výchozí příkaz implementace jsou předem zapojeny v mapování zpráv základní třídy rozhraní. Existují některé implementace příkazů, které vyžadují explicitní zapojení v odvozené třídě. Ty jsou popsány v části "Poznámka". Pokud jste v Průvodci aplikací zvolili správné možnosti, budou tyto výchozí obslužné rutiny připojeny v generované aplikaci kostry.

## <a name="naming-convention"></a>Konvence vytváření názvů

Standardní příkazy se řídí jednoduchou konvencí pojmenování, kterou doporučujeme použít, pokud je to možné. Většina standardních příkazů je umístěna na standardních místech v panelu nabídek aplikace. Symbolický název příkazu začíná "ID_" následovaný standardním názvem rozbalovací nabídky následovaným názvem položky nabídky. Symbolický název je velkými písmeny s podtržítkem konce slov. Pro příkazy, které nemají standardní názvy položek nabídky, je definován název logického příkazu začínající na "ID_" (například ID_NEXT_PANE).

Předponu "ID_" používáme k označení příkazů, které jsou navrženy tak, aby byly vázány na položky nabídky, tlačítka panelu nástrojů nebo jiné objekty uživatelského rozhraní příkazu. Obslužné rutiny příkazů zpracovávající příkazy "ID_" by měly používat ON_COMMAND a ON_UPDATE_COMMAND_UI mechanismy architektury příkazů knihovny MFC.

Doporučujeme použít standardní předponu "IDM_" pro položky nabídky, které nedodržují architekturu příkazů a potřebují kód specifický pro danou nabídku, aby je povolily a zakázaly. Samozřejmě počet příkazů specifických pro nabídku by měl být malý, protože po architektuře příkazů knihovny MFC nejen že je obslužná rutina příkazů výkonnější (protože budou pracovat s panely nástrojů), ale umožňuje opakované použití kódu obslužné rutiny příkazu.

## <a name="id-ranges"></a>Rozsahy ID

Další podrobnosti o použití rozsahů ID v knihovně MFC naleznete v [technické poznámce 20.](../mfc/tn020-id-naming-and-numbering-conventions.md)

Standardní příkazy MFC spadají do rozsahu 0xE000 až 0xEFFF. Nespoléhejte se na konkrétní hodnoty těchto ID, protože se mohou v budoucích verzích knihovny změnit.

Aplikace by měla definovat své příkazy v rozsahu 0x8000 až 0xDFFF.

## <a name="standard-command-ids"></a>Standardní ID příkazů

Pro každé ID příkazu je standardní řetězec řádku zprávy, který lze nalézt v souboru PROMPTS. Rc. ID řetězce pro tento řádek nabídky musí být stejné jako pro ID příkazu.

- ID_FILE_NEW Vytvoří nový/prázdný dokument.

    > [!NOTE]
    >  Chcete-li tuto `CWinApp`funkci povolit, musíte ji připojit k mapování zpráv odvozené třídy.

   `CWinApp::OnFileNew`implementuje tento příkaz odlišně v závislosti na počtu šablon dokumentů v aplikaci. Pokud existuje pouze `CDocTemplate` `CWinApp::OnFileNew` jeden , vytvoří nový dokument tohoto typu, stejně jako správný rámec a třídu zobrazení.

   Pokud existuje více `CDocTemplate`než `CWinApp::OnFileNew` jeden , vyzve uživatele dialog (AFX_IDD_NEWTYPEDLG) umožňuje vybrat typ dokumentu, který chcete použít. Vybraná `CDocTemplate` volba se použije k vytvoření dokumentu.

   Jedním z běžných přizpůsobení ID_FILE_NEW je poskytnout jiný a graficky jší výběr typů dokumentů. V takovém případě můžete `CMyApp::OnFileNew` implementovat vlastní a umístit `CWinApp::OnFileNew`jej do mapy zpráv namísto . Není nutné volat implementaci základní třídy.

   Dalším běžným přizpůsobením ID_FILE_NEW je poskytnout samostatný příkaz pro vytvoření dokumentu každého typu. V takovém případě byste měli definovat nová ID příkazů, například ID_FILE_NEW_CHART a ID_FILE_NEW_SHEET.

- ID_FILE_OPEN Otevře existující dokument.

    > [!NOTE]
    >  Chcete-li tuto `CWinApp`funkci povolit, musíte ji připojit k mapování zpráv odvozené třídy.

   `CWinApp::OnFileOpen`má velmi jednoduchou `CWinApp::DoPromptFileName` implementaci `CWinApp::OpenDocumentFile` volání následovanou názvem souboru nebo cesty souboru, který chcete otevřít. Implementace `CWinApp` rutina `DoPromptFileName` vyvolá standardní FileOpen dialog a vyplní jej přípony souborů získané z aktuálních šablon dokumentů.

   Jedním z běžných přizpůsobení ID_FILE_OPEN je přizpůsobení dialogového okna FileOpen nebo přidání dalších filtrů souborů. Doporučený způsob, jak to přizpůsobit, je nahradit výchozí implementaci vlastním `CWinApp::OpenDocumentFile` dialogovým oknem FileOpen a volat názvem souboru nebo cesty dokumentu. Není třeba volat základní třídy.

- ID_FILE_CLOSE Zavře aktuálně otevřený dokument.

   `CDocument::OnFileClose`volá, `CDocument::SaveModified` aby vyzval uživatele k uložení dokumentu, pokud `OnCloseDocument`byl změněn, a poté zavolá . Všechny logiky uzávěrky, včetně zničení dokumentu, se provádí v rutině. `OnCloseDocument`

    > [!NOTE]
    >  ID_FILE_CLOSE funguje jinak než zpráva WM_CLOSE nebo příkaz SC_CLOSE systému odeslaný do okna rámce dokumentů. Zavřením okna zavřete dokument pouze v případě, že se jedná o poslední okno rámce zobrazující dokument. Zavření dokumentu s ID_FILE_CLOSE nejen zavře dokument, ale zavře se všechna okna rámečku zobrazující dokument.

- ID_FILE_SAVE Uloží aktuální dokument.

   Implementace používá pomocnou `CDocument::DoSave` rutinu, která `OnFileSave` `OnFileSaveAs`se používá pro oba a . Pokud uložíte dokument, který nebyl uložen dříve (to znamená, že nemá název cesty, jako v případě FileNew) nebo `OnFileSave` který byl přečten z dokumentu jen pro čtení, logika bude fungovat jako příkaz ID_FILE_SAVE_AS a požádejte uživatele o zadání nového názvu souboru. Skutečný proces otevírání souboru a dělá ukládání se `OnSaveDocument`provádí prostřednictvím virtuální funkce .

   Existují dva běžné důvody pro přizpůsobení ID_FILE_SAVE. U dokumentů, které se neukládají, jednoduše odeberte z uživatelského rozhraní položky nabídky ID_FILE_SAVE a tlačítka panelu nástrojů. Také se ujistěte, že jste nikdy dirty `CDocument::SetModifiedFlag`dokumentu (to znamená, nikdy volat) a rozhraní nikdy způsobit dokument, který má být uložen. Pro dokumenty, které se ukládají do jiného místa než na disk, definujte pro tuto operaci nový příkaz.

   V případě `COleServerDoc`, ID_FILE_SAVE se používá jak pro ukládání souborů (pro normální dokumenty), tak pro aktualizaci souboru (pro vložené dokumenty).

   Pokud jsou data dokumentu uložena v jednotlivých souborech na `CDocument` disku, ale nechcete používat `CDocument::OnSaveDocument` výchozí `OnFileSave`serializovat implementaci, měli byste místo něj přepsat .

- ID_FILE_SAVE_AS Uloží aktuální dokument pod jiným názvem souboru.

   Implementace `CDocument::OnFileSaveAs` používá stejnou `CDocument::DoSave` pomocnou `OnFileSave`rutinu jako . Příkaz `OnFileSaveAs` je zpracován stejně ID_FILE_SAVE, pokud dokumenty před uložením neměly žádný název souboru. `COleServerDoc::OnFileSaveAs`implementuje logiku pro uložení normálního datového souboru dokumentu nebo pro uložení dokumentu serveru představujícího objekt OLE vložený do jiné aplikace jako samostatný soubor.

   Pokud přizpůsobíte logiku ID_FILE_SAVE, budete pravděpodobně chtít přizpůsobit ID_FILE_SAVE_AS podobným způsobem nebo se na dokument nemusí vztahovat operace Uložit jako. Pokud není potřeba, můžete položku nabídky odebrat z panelu nabídek.

- ID_FILE_SAVE_COPY_AS Uloží kopii aktuálního dokumentu pod novým názvem.

   Implementace `COleServerDoc::OnFileSaveCopyAs` je velmi `CDocument::OnFileSaveAs`podobná , s tím rozdílem, že objekt dokumentu není "připojen" k podkladovému souboru po uložení. To znamená, že pokud byl dokument v paměti "upraven" před uložením, je stále "změněn". Kromě toho tento příkaz nemá žádný vliv na název cesty nebo název uložený v dokumentu.

- ID_FILE_UPDATE Upozorní kontejner na uložení vloženého dokumentu.

   Implementace `COleServerDoc::OnUpdateDocument` jednoduše upozorní kontejner, který by měl být uložen vkládání. Kontejner pak volá příslušná řešení API OLE, aby uložil vložený objekt.

- ID_FILE_PAGE_SETUP Vyvolá dialogové okno nastavení a rozložení stránky specifické pro aplikaci.

   V současné době neexistuje žádný standard pro toto dialogové okno a rozhraní framework nemá žádnou výchozí implementaci tohoto příkazu.

   Pokud se rozhodnete implementovat tento příkaz, doporučujeme použít toto ID příkazu.

- ID_FILE_PRINT_SETUP Vyvolat standardní dialogové okno Nastavení tisku.

    > [!NOTE]
    >  Chcete-li tuto `CWinApp`funkci povolit, musíte ji připojit k mapování zpráv odvozené třídy.

   Tento příkaz vyvolá standardní dialogové okno nastavení tisku, které umožňuje uživateli přizpůsobit nastavení tiskárny a tisku alespoň pro tento dokument nebo maximálně všechny dokumenty v této aplikaci. Chcete-li změnit výchozí nastavení tiskárny pro celý systém, musíte pomocí Ovládacích panelů změnit.

   `CWinApp::OnFilePrintSetup`má velmi jednoduchou `CPrintDialog` implementaci, která `CWinApp::DoPrintDialog` vytváří objekt a volá implementační funkci. Tím nastavíte výchozí nastavení tiskárny aplikace.

   Běžnou potřebou přizpůsobení tohoto příkazu je umožnit nastavení tiskárny pro každý dokument, které by mělo být uloženo s dokumentem při uložení. Chcete-li to provést, měli byste `CDocument` přidat obslužnou rutinu mapy zpráv do třídy, která vytvoří `CPrintDialog` objekt, inicializuje jej s příslušnými atributy tiskárny (obvykle *hDevMode* a *hDevNames*), zavolejte `CPrintDialog::DoModal`a uložte změněné nastavení tiskárny. Pro robustní implementaci byste se měli `CWinApp::DoPrintDialog` podívat na `CWinApp::UpdatePrinterSelection` implementaci pro detekci chyb a pro řešení rozumných výchozích hodnot a sledování změn celé tiskárny systému.

- ID_FILE_PRINT Standardní tisk aktuálního dokumentu

    > [!NOTE]
    >  Chcete-li tuto `CView`funkci povolit, musíte ji připojit k mapování zpráv odvozené třídy.

   Tento příkaz vytiskne aktuální dokument nebo správněji spustí proces tisku, který zahrnuje vyvolání standardního tiskového dialogu a spuštění tiskového stroje.

   `CView::OnFilePrint`implementuje tento příkaz a hlavní tiskovou smyčku. Volá virtuální `CView::OnPreparePrinting` výzvu uživatele s tiskovým dialogem. Potom připraví výstup DC přejít na tiskárnu, vyvolá dialogové okno průběhu `StartDoc` tisku (AFX_IDD_PRINTDLG) a odešle escape do tiskárny. `CView::OnFilePrint`obsahuje také hlavní tiskovou smyčku orientovanou na stránku. Pro každou stránku volá `CView::OnPrepareDC` virtuální `StartPage` následuje escape a `CView::OnPrint` volání virtuální pro tuto stránku. Po dokončení je `CView::OnEndPrinting` volána virtuální a dialogové okno průběhu tisku je uzavřeno.

   Architektura tisku knihovny MFC je navržena tak, aby se při tisk a náhledu zavázala mnoha různými způsoby. Obvykle najdete různé `CView` overridable funkce vhodné pro všechny stránky-orientované tiskové úlohy. Pouze v případě aplikace, která používá tiskárnu pro výstup orientovaný na stránky, byste měli najít potřebu nahradit ID_FILE_PRINT implementaci.

- ID_FILE_PRINT_PREVIEW Vstup do režimu náhledu aktuálního dokumentu.

    > [!NOTE]
    >  Chcete-li tuto `CView`funkci povolit, musíte ji připojit k mapování zpráv odvozené třídy.

   `CView::OnFilePrintPreview`spustí režim náhledu voláním zdokumentované `CView::DoPrintPreview`pomocné funkce . `CView::DoPrintPreview`je hlavní modul pro smyčku `OnFilePrint` náhledu tisku, stejně jako hlavní modul pro tiskovou smyčku.

   Operaci náhledu tisku lze přizpůsobit různými způsoby předáním různých `DoPrintPreview`parametrů . Podívejte se prosím na [technickou poznámku 30](../mfc/tn030-customizing-printing-and-print-preview.md), která popisuje některé podrobnosti náhledu a jeho přizpůsobení.

- ID_FILE_MRU_FILE1... FILE16 Rozsah ID příkazů pro **seznam**souborů MRU .

   `CWinApp::OnUpdateRecentFileMenu`je obslužná rutina příkazu update, která je jedním z pokročilejších použití mechanismu ON_UPDATE_COMMAND_UI. V prostředku nabídky stačí definovat pouze jednu položku nabídky s ID ID_FILE_MRU_FILE1. Tato položka nabídky zůstane zpočátku zakázána.

   Jak seznam MRU roste, další položky nabídky jsou přidány do seznamu. Standardní `CWinApp` implementace výchozí standardní limit čtyř naposledy použitých souborů. Výchozí nastavení můžete změnit `CWinApp::LoadStdProfileSettings` voláním s větší nebo menší hodnotou. Seznam MRU je uložen v aplikaci . INI. Seznam je načten ve `InitInstance` funkci aplikace, `LoadStdProfileSettings`pokud voláte , a je uložen při ukončení aplikace. Obslužná rutina příkazu MRU update příkazu také převede absolutní cesty na relativní cesty pro zobrazení v nabídce souboru.

   `CWinApp::OnOpenRecentFile`je obslužná rutina ON_COMMAND, která provádí skutečný příkaz. Jednoduše získá název souboru ze seznamu `CWinApp::OpenDocumentFile`MRU a volání , který dělá veškerou práci otevření souboru a aktualizaci seznamu MRU.

   Přizpůsobení této obslužné rutiny příkazu se nedoporučuje.

- ID_EDIT_CLEAR Vymaže aktuální výběr.

   V současné době neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat `CView`pro každou odvozenou třídu.

   `CEditView`poskytuje implementaci tohoto příkazu pomocí `CEdit::Clear`. Příkaz je zakázán, pokud není k dispozici žádný aktuální výběr.

   Pokud se rozhodnete implementovat tento příkaz, doporučujeme použít toto ID příkazu.

- ID_EDIT_CLEAR_ALL Vymaže celý dokument.

   V současné době neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat `CView`pro každou odvozenou třídu.

   Pokud se rozhodnete implementovat tento příkaz, doporučujeme použít toto ID příkazu. Ukázka ukázky [kurznice](../overview/visual-cpp-samples.md) knihovny MFC například implementace.

- ID_EDIT_COPY Zkopíruje aktuální výběr do schránky.

   V současné době neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat `CView`pro každou odvozenou třídu.

   `CEditView`Poskytuje implementaci tohoto příkazu, který zkopíruje aktuálně vybraný text `CEdit::Copy`do schránky jako CF_TEXT pomocí . Příkaz je zakázán, pokud není k dispozici žádný aktuální výběr.

   Pokud se rozhodnete implementovat tento příkaz, doporučujeme použít toto ID příkazu.

- ID_EDIT_CUT Vyjme aktuální výběr do schránky.

   V současné době neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat `CView`pro každou odvozenou třídu.

   `CEditView`Poskytuje implementaci tohoto příkazu, který vyjme aktuálně vybraný text `CEdit::Cut`do schránky jako CF_TEXT pomocí . Příkaz je zakázán, pokud není k dispozici žádný aktuální výběr.

   Pokud se rozhodnete implementovat tento příkaz, doporučujeme použít toto ID příkazu.

- ID_EDIT_FIND Zahájí operaci hledání, vyvolá nemodální dialogové okno hledání.

   V současné době neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat `CView`pro každou odvozenou třídu.

   `CEditView`poskytuje implementaci tohoto příkazu, který volá `OnEditFindReplace` pomocnou funkci implementace pro použití a uložení předchozího nastavení hledání a nahrazení v proměnných privátní implementace. Třída `CFindReplaceDialog` slouží ke správě nemodální dialog pro dotazování uživatele.

   Pokud se rozhodnete implementovat tento příkaz, doporučujeme použít toto ID příkazu.

- ID_EDIT_PASTE Vloží aktuální obsah schránky.

   V současné době neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat `CView`pro každou odvozenou třídu.

   `CEditView`Poskytuje implementaci tohoto příkazu, který zkopíruje aktuální data schránky `CEdit::Paste`nahrazující vybraný text pomocí . Příkaz je zakázán, pokud ve schránce není **žádná CF_TEXT.**

   `COleClientDoc`pouze poskytuje příkaz aktualizace obslužné rutiny příkazu pro tento příkaz. Pokud schránka neobsahuje vložitelnou položku nebo objekt OLE, bude příkaz zakázán. Jste zodpovědní za zápis obslužné rutiny pro skutečný příkaz provést skutečné vkládání. Pokud vaše aplikace OLE můžete také vložit jiné formáty, měli byste zadat vlastní update příkaz `COleClientDoc` obslužné rutiny v zobrazení nebo dokumentu (to znamená, že někde předtím v směrování cíle příkazu).

   Pokud se rozhodnete implementovat tento příkaz, doporučujeme použít toto ID příkazu.

   Pro nahrazení standardní implementace OLE `COleClientItem::CanPaste`použijte .

- ID_EDIT_PASTE_LINK Vloží odkaz z aktuálního obsahu schránky.

   V současné době neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat `CView`pro každou odvozenou třídu.

   `COleDocument`pouze poskytuje příkaz aktualizace obslužné rutiny příkazu pro tento příkaz. Pokud schránka neobsahuje propojitelnou položku nebo objekt OLE, bude příkaz zakázán. Jste zodpovědní za zápis obslužné rutiny pro skutečný příkaz provést skutečné vkládání. Pokud vaše aplikace OLE můžete také vložit jiné formáty, měli byste zadat vlastní update příkaz `COleDocument` obslužné rutiny v zobrazení nebo dokumentu (to znamená, že někde předtím v směrování cíle příkazu).

   Pokud se rozhodnete implementovat tento příkaz, doporučujeme použít toto ID příkazu.

   Pro nahrazení standardní implementace OLE `COleClientItem::CanPasteLink`použijte .

- ID_EDIT_PASTE_SPECIAL Vloží aktuální obsah schránky s možnostmi.

   V současné době neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat `CView`pro každou odvozenou třídu. Knihovna MFC neposkytuje toto dialogové okno.

   Pokud se rozhodnete implementovat tento příkaz, doporučujeme použít toto ID příkazu.

- ID_EDIT_REPEAT Zopakuje poslední operaci.

   V současné době neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat `CView`pro každou odvozenou třídu.

   `CEditView`poskytuje implementaci tohoto příkazu opakovat poslední operaci hledání. Používají se proměnné soukromé implementace pro poslední hledání. Příkaz je zakázán, pokud nelze vyhledat.

   Pokud se rozhodnete implementovat tento příkaz, doporučujeme použít toto ID příkazu.

- ID_EDIT_REPLACE Zahájí operaci nahrazení, vyvolá dialog o nemodálním nahrazení.

   V současné době neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat `CView`pro každou odvozenou třídu.

   `CEditView`poskytuje implementaci tohoto příkazu, který volá `OnEditFindReplace` pomocnou funkci implementace pro použití a uložení předchozího nastavení hledání a nahrazení v proměnných privátní implementace. Třída `CFindReplaceDialog` slouží ke správě nemodální dialog, který vyzve uživatele.

   Pokud se rozhodnete implementovat tento příkaz, doporučujeme použít toto ID příkazu.

- ID_EDIT_SELECT_ALL Vybere celý dokument.

   V současné době neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat `CView`pro každou odvozenou třídu.

   `CEditView`poskytuje implementaci tohoto příkazu, který vybere veškerý text v dokumentu. Příkaz je zakázán, pokud není k dispozici žádný text, který by bylo možné vybrat.

   Pokud se rozhodnete implementovat tento příkaz, doporučujeme použít toto ID příkazu.

- ID_EDIT_UNDO Vrátit zpět poslední operaci.

   V současné době neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat `CView`pro každou odvozenou třídu.

   `CEditView`poskytuje implementaci tohoto příkazu `CEdit::Undo`pomocí . Příkaz je zakázán, pokud `CEdit::CanUndo` vrátí hodnotu NEPRAVDA.

   Pokud se rozhodnete implementovat tento příkaz, doporučujeme použít toto ID příkazu.

- ID_EDIT_REDO Předělá poslední operaci.

   V současné době neexistuje žádná standardní implementace pro tento příkaz. Je nutné implementovat `CView`pro každou odvozenou třídu.

   Pokud se rozhodnete implementovat tento příkaz, doporučujeme použít toto ID příkazu.

- ID_WINDOW_NEW Otevře další okno aktivního dokumentu.

   `CMDIFrameWnd::OnWindowNew`implementuje tuto výkonnou funkci pomocí šablony dokumentu aktuálního dokumentu k vytvoření jiného rámce obsahujícího jiné zobrazení aktuálního dokumentu.

   Stejně jako většina příkazů nabídky rozhraní mdi (více dokumentů) je příkaz zakázán, pokud není k dispozici žádné aktivní podřízené okno MDI.

   Přizpůsobení této obslužné rutiny příkazu se nedoporučuje. Pokud chcete zadat příkaz, který vytvoří další zobrazení nebo okna rámců, budete pravděpodobně lépe vymyslet vlastní příkaz. Kód můžete naklonovat `CMDIFrameWnd::OnWindowNew` a upravit do konkrétního rámce a zobrazit třídy podle vašich představ.

- ID_WINDOW_ARRANGE Uspořádá ikony v dolní části okna MDI.

   `CMDIFrameWnd`implementuje tento standardní příkaz MDI `OnMDIWindowCmd`v pomocné funkci implementace . Tento pomocník mapuje ID příkazů na zprávy systému Windows MDI a proto může sdílet velké množství kódu.

   Stejně jako většina příkazů nabídky Okno MDI je příkaz zakázán, pokud není k dispozici žádné aktivní podřízené okno MDI.

   Přizpůsobení této obslužné rutiny příkazu se nedoporučuje.

- ID_WINDOW_CASCADE Kaskády okna tak, aby se překrývaly.

   `CMDIFrameWnd`implementuje tento standardní příkaz MDI `OnMDIWindowCmd`v pomocné funkci implementace . Tento pomocník mapuje ID příkazů na zprávy systému Windows MDI a proto může sdílet velké množství kódu.

   Stejně jako většina příkazů nabídky Okno MDI je příkaz zakázán, pokud není k dispozici žádné aktivní podřízené okno MDI.

   Přizpůsobení této obslužné rutiny příkazu se nedoporučuje.

- ID_WINDOW_TILE_HORZ dlaždice okna vodorovně.

   Tento příkaz je `CMDIFrameWnd` implementován stejně jako ID_WINDOW_CASCADE, s výjimkou jiné zprávy MDI systému Windows se používá pro operaci.

   Měli byste pro svou aplikaci vybrat výchozí orientaci dlaždic. To lze provést změnou ID položky nabídky "Dlaždice" na ID_WINDOW_TILE_HORZ nebo ID_WINDOW_TILE_VERT.

- ID_WINDOW_TILE_VERT Dlaždice okna svisle.

   Tento příkaz je `CMDIFrameWnd` implementován stejně jako ID_WINDOW_CASCADE, s výjimkou jiné zprávy MDI systému Windows se používá pro operaci.

   Měli byste pro svou aplikaci vybrat výchozí orientaci dlaždic. To lze provést změnou ID položky nabídky "Dlaždice" na ID_WINDOW_TILE_HORZ nebo ID_WINDOW_TILE_VERT.

- ID_WINDOW_SPLIT rozhraní klávesnice na splitter.

   `CView`zpracovává tento příkaz `CSplitterWnd` pro implementaci. Pokud je zobrazení součástí okna rozdělovače, bude tento `CSplitterWnd::DoKeyboardSplit`příkaz delegovat na funkci implementace . Tím umístíte rozdělovač do režimu, který uživatelům klávesnice umožní rozdělit nebo zrušit rozdělení okna rozdělovače.

   Tento příkaz je zakázán, pokud zobrazení není v rozdělovači.

   Přizpůsobení této obslužné rutiny příkazu se nedoporučuje.

- ID_APP_ABOUT vyvolá dialogové okno O.

   Neexistuje žádná standardní implementace pro aplikaci O box. Výchozí aplikace vytvořená průvodcem vytvoří vlastní třídu dialogu pro vaši aplikaci a použije ji jako pole O aplikaci. AppWizard také napíše triviální obslužnou rutinu příkazu, která zpracovává tento příkaz a vyvolá dialogové okno.

   Tento příkaz budete téměř vždy implementovat.

- ID_APP_EXIT Ukončit aplikaci.

   `CWinApp::OnAppExit`tento příkaz zpracovává odesláním WM_CLOSE zprávy do hlavního okna aplikace. Standardní vypnutí aplikace (výzva pro nečisté soubory a tak dále) `CFrameWnd` je zpracována implementací.

   Přizpůsobení této obslužné rutiny příkazu se nedoporučuje. Doporučuje `CWinApp::SaveAllModified` se `CFrameWnd` přepsání nebo logika uzávěrky.

   Pokud se rozhodnete implementovat tento příkaz, doporučujeme použít toto ID příkazu.

- ID_HELP_INDEX Obsahuje témata nápovědy z . HLP.

    > [!NOTE]
    >  Chcete-li tuto `CWinApp`funkci povolit, musíte ji připojit k mapování zpráv odvozené třídy.

   `CWinApp::OnHelpIndex`zpracovává tento příkaz triviálně voláním `CWinApp::WinHelp`.

   Přizpůsobení této obslužné rutiny příkazu se nedoporučuje.

- ID_HELP_USING Zobrazí nápovědu k použití nápovědy.

    > [!NOTE]
    >  Chcete-li tuto `CWinApp`funkci povolit, musíte ji připojit k mapování zpráv odvozené třídy.

   `CWinApp::OnHelpUsing`zpracovává tento příkaz triviálně voláním `CWinApp::WinHelp`.

   Přizpůsobení této obslužné rutiny příkazu se nedoporučuje.

- ID_CONTEXT_HELP Vstoupí do režimu nápovědy SHIFT-F1.

    > [!NOTE]
    >  Chcete-li tuto `CWinApp`funkci povolit, musíte ji připojit k mapování zpráv odvozené třídy.

   `CWinApp::OnContextHelp`tento příkaz zpracovává nastavením kurzoru režimu nápovědy, zadáním modální smyčky a čekáním na výběr okna, na které chcete získat nápovědu. Další podrobnosti o implementaci nápovědy knihovny MFC naleznete v [technické poznámce 28.](../mfc/tn028-context-sensitive-help-support.md)

   Přizpůsobení této obslužné rutiny příkazu se nedoporučuje.

- ID_HELP poskytuje pomoc v aktuálním kontextu

    > [!NOTE]
    >  Chcete-li tuto `CWinApp`funkci povolit, musíte ji připojit k mapování zpráv odvozené třídy.

   `CWinApp::OnHelp`zvládá tento příkaz získáním správného kontextu nápovědy pro aktuální kontext aplikace. To zpracovává jednoduché F1 pomoc, pomoc na okna zpráv a tak dále. Další podrobnosti o implementaci nápovědy knihovny MFC naleznete v [technické poznámce 28.](../mfc/tn028-context-sensitive-help-support.md)

   Přizpůsobení této obslužné rutiny příkazu se nedoporučuje.

- ID_DEFAULT_HELP Zobrazí výchozí nápovědu pro kontext.

    > [!NOTE]
    >  Chcete-li tuto `CWinApp`funkci povolit, musíte ji připojit k mapování zpráv odvozené třídy.

   Tento příkaz je obvykle `CWinApp::OnHelpIndex`mapován na .

   Pokud je požadovánrozdíl mezi výchozí nápovědou a indexem nápovědy, lze poskytnout jinou obslužnou rutinu příkazu.

- ID_NEXT_PANE přejde do dalšího podokna

   `CView`zpracovává tento příkaz `CSplitterWnd` pro implementaci. Pokud je zobrazení součástí okna rozdělovače, bude tento `CSplitterWnd::OnNextPaneCmd`příkaz delegovat na funkci implementace . Tím se přesune aktivní zobrazení do dalšího podokna v rozdělovači.

   Tento příkaz je zakázán, pokud zobrazení není v rozdělovači nebo není k dispozici žádné další podokno, do které by bylo možné přejít.

   Přizpůsobení této obslužné rutiny příkazu se nedoporučuje.

- ID_PREV_PANE přejde do předchozího podokna

   `CView`zpracovává tento příkaz `CSplitterWnd` pro implementaci. Pokud je zobrazení součástí okna rozdělovače, bude tento `CSplitterWnd::OnNextPaneCmd`příkaz delegovat na funkci implementace . Tím se přesune aktivní zobrazení do předchozího podokna v rozdělovači.

   Tento příkaz je zakázán, pokud zobrazení není v rozdělovači nebo neexistuje žádné předchozí podokno, do které by bylo možné přejít.

   Přizpůsobení této obslužné rutiny příkazu se nedoporučuje.

- ID_OLE_INSERT_NEW Vloží nový objekt OLE.

   V současné době neexistuje žádná standardní implementace pro tento příkaz. Musíte implementovat pro `CView`vaše odvozené třídy vložit novou položku OLE nebo objekt u aktuálního výběru.

   Tento příkaz by měly implementovat všechny klientské aplikace OLE. AppWizard, s možností OLE, vytvoří kostru implementace `OnInsertObject` ve vašem zobrazení třídy, které budete muset dokončit.

   Viz ukázkový příklad [knihovny MFC](../overview/visual-cpp-samples.md) OLE OCLIENT pro úplnou implementaci tohoto příkazu.

- ID_OLE_EDIT_LINKS úpravy propojení OLE

   `COleDocument`tento příkaz zpracovává pomocí implementace standardních propojení OLE za předpokladu Knihovny MFC. Implementace tohoto dialogu je přístupná `COleLinksDialog` prostřednictvím třídy. Pokud aktuální dokument neobsahuje žádné odkazy, je příkaz zakázán.

   Přizpůsobení této obslužné rutiny příkazu se nedoporučuje.

- ID_OLE_VERB_FIRST... POSLEDNÍ Rozsah ID pro slovesa OLE

   `COleDocument`Používá tento rozsah ID příkazu pro slovesa podporovaná aktuálně vybranou položkou nebo objektem OLE. To musí být rozsah, protože daný typ položky OLE nebo objektu může podporovat nula nebo více vlastních sloves. V nabídce aplikace byste měli mít jednu položku nabídky s ID ID_OLE_VERB_FIRST. Při spuštění programu bude nabídka aktualizována příslušným popisem slovesa nabídky (nebo rozbalovací nabídkou s mnoha slovesy). Správa nabídky OLE je zpracována službou `AfxOleSetEditMenu`, provádí se v obslužné rutině příkazu update command pro tento příkaz.

   Neexistují žádné explicitní obslužné rutiny příkazů pro zpracování každého id příkazu v tomto rozsahu. `COleDocument::OnCmdMsg`je přepsána tak, aby sutenvšechna ID příkazů v tomto rozsahu, přeměnila `COleClientItem::DoVerb`je na čísla sloves založených na nule a spustila server pro toto sloveso (pomocí ).

   Přizpůsobení nebo jiné použití tohoto rozsahu ID příkazu se nedoporučuje.

- ID_VIEW_TOOLBAR Zapíná a vypíná panel nástrojů.

   `CFrameWnd`zvládá tento příkaz a obslužnou rutinu ui příkazu update-command pro přepnutí viditelného stavu panelu nástrojů. Panel nástrojů musí být podřízeným oknem rámce s ID podřízeného okna AFX_IDW_TOOLBAR. Obslužná rutina příkazu ve skutečnosti přepíná viditelnost okna panelu nástrojů. `CFrameWnd::RecalcLayout`slouží k překreslení okna rámce s panelem nástrojů v novém stavu. Obslužná rutina příkazu aktualizace a příkazu zkontroluje položku nabídky, když je zobrazen panel nástrojů.

   Přizpůsobení této obslužné rutiny příkazu se nedoporučuje. Chcete-li přidat další panely nástrojů, budete chtít klonovat a upravovat obslužnou rutinu příkazu a obslužnou rutinu ui příkazu update-command pro tento příkaz.

- ID_VIEW_STATUS_BAR Zapíná a vypíná stavový řádek

   Tento příkaz je `CFrameWnd` implementován stejně jako ID_VIEW_TOOLBAR, s výjimkou jiného podřízeného okna ID (AFX_IDW_STATUS_BAR) se používá.

## <a name="update-only-command-handlers"></a>Obslužné rutiny příkazů pouze pro aktualizaci

Několik standardních ID příkazů se používá jako indikátory ve stavových stavových stavových stavových panelech. Ty používají stejný mechanismus zpracování ui příkazu update-command k zobrazení jejich aktuálního vizuálního stavu během doby nečinnosti aplikace. Vzhledem k tomu, že je uživatel nemůže vybrat (to znamená, že nelze vysunout podokno stavového řádku), nemá smysl mít pro tato ID příkazů obslužnou rutinu ON_COMMAND.

- ID_INDICATOR_CAPS : Indikátor zámku CAP.

- ID_INDICATOR_NUM : Indikátor zámku NUM.

- ID_INDICATOR_SCRL : Indikátor zámku SCRL.

- ID_INDICATOR_KANA : Indikátor zámku KANA (platí pouze pro japonské systémy).

Všechny tři z nich `CFrameWnd::OnUpdateKeyIndicator`jsou implementovány v aplikaci pomocník implementace, který používá ID příkazu mapovat na příslušný virtuální klíč. Běžná implementace povolí nebo zakáže (pro stavová `CCmdUI` podokna zakázáno = žádný text) objekt v závislosti na tom, zda je aktuálně uzamčen příslušný virtuální klíč.

Přizpůsobení této obslužné rutiny příkazu se nedoporučuje.

- ID_INDICATOR_EXT : Indikátor extended výběru.

- ID_INDICATOR_OVR : Indikátor OVeRstrike.

- ID_INDICATOR_REC : Indikátor RECording.

V současné době neexistuje standardní provádění těchto ukazatelů.

Pokud se rozhodnete tyto indikátory implementovat, doporučujeme použít tato ID indikátorů a udržovat pořadí indikátorů ve stavovém řádku (tj. v tomto pořadí: EXT, CAP, NUM, SCRL, OVR, REC).

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
