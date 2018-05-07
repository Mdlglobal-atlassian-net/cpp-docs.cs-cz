---
title: 'TN028: Podpora kontextové nápovědy | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.help
dev_langs:
- C++
helpviewer_keywords:
- context-sensitive Help [MFC], MFC applications
- TN028
- resource identifiers, context-sensitive Help
ms.assetid: 884f1c55-fa27-4d4c-984f-30907d477484
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 58caed14e6b7080405cceb30cfb90623d28dc83e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="tn028-context-sensitive-help-support"></a>TN028: Podpora kontextové nápovědy
Tato poznámka popisuje pravidla pro přiřazování ID kontexty nápovědy a další pomoc problémy v prostředí MFC. Podpora kontextové nápovědy vyžaduje kompilátor nápovědy, která je k dispozici v jazyce Visual C++.  
  
> [!NOTE]
>  Kromě implementace Kontextová nápověda pomocí WinHelp, MFC také podporuje používání nápovědy HTML. Další informace o tuto podporu a programování s nápovědou HTML najdete v tématu [nápovědy HTML: Context-Sensitive Nápověda pro vaše programy](../mfc/html-help-context-sensitive-help-for-your-programs.md).  
  
## <a name="types-of-help-supported"></a>Typy podporované nápovědy  
 Existují dva typy Kontextová nápověda implementovaná v aplikacích Windows. První, označuje jako "Nápověda F1" zahrnuje spuštění WinHelp s odpovídající kontext založen na aktuálně aktivní objektu. Druhá je režim "Shift + F1". V tomto režimu změní myší na kurzor nápovědy a pokračuje uživatel kliknout na objekt. V tomto bodě se spustí WinHelp poskytnout nápovědu pro objekt, který uživatel klepl.  
  
 Microsoft Foundation třídy implementovat obě tyto formuláře nápovědy. Kromě toho rozhraní podporuje dva příkazy jednoduché nápovědy, pomůže Index a použití pomoci.  
  
## <a name="help-files"></a>Soubory nápovědy  
 Microsoft Foundation třídy předpokládají do jednoho souboru nápovědy. Tento soubor nápovědy musí mít stejný název a cestu jako aplikace. Například pokud spustitelný soubor je C:\MyApplication\MyHelp.exe musí být v souboru nápovědy C:\MyApplication\MyHelp.hlp. Nastavení cesty prostřednictvím `m_pszHelpFilePath` členské proměnné [CWinApp – třída](../mfc/reference/cwinapp-class.md).  
  
## <a name="help-context-ranges"></a>Rozsahy kontextové nápovědy  
 Výchozí implementace MFC vyžaduje program podle některá pravidla o přiřazení kontextové nápovědy ID. Tato pravidla jsou určitý rozsah ID přidělené na konkrétní ovládací prvky. Tato pravidla můžete přepsat zadáním jiné implementace různých funkcí souvisejících s člen.  
  
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
  
## <a name="simple-help-commands"></a>Příkazy jednoduchý "Nápověda"  
 Existují dva jednoduché příkazy nápovědy, které implementují Microsoft Foundation třídy:  
  
-   Id_help_index –, které je implementované [CWinApp::OnHelpIndex](../mfc/reference/cwinapp-class.md#onhelpindex)  
  
-   Id_help_using –, které je implementované [CWinApp::OnHelpUsing](../mfc/reference/cwinapp-class.md#onhelpusing)  
  
 První příkaz zobrazí indexu nápovědy pro aplikaci. U druhé se zobrazí v nápovědě uživatele na pomocí programu WinHelp.  
  
## <a name="context-sensitive-help-f1-help"></a>Kontextové nápovědy (Nápověda F1)  
 Klávesy F1 je obvykle přeložená na příkaz s ID `ID_HELP` podle akcelerátor umístí do tabulky akcelerátorů hlavního okna. `ID_HELP` Také lze generovat příkazového tlačítka s ID `ID_HELP` na pole hlavní okno nebo dialogové okno.  
  
 Bez ohledu na to, jak `ID_HELP` příkaz se vygeneruje, se směruje jako normální příkaz, dokud nebude dosaženo obslužná rutina příkazu. Další informace o architektuře směrování příkazů MFC, najdete v části [Technická poznámka 21](../mfc/tn021-command-and-message-routing.md). Pokud aplikace má nápovědy povoleno, `ID_HELP` příkaz bude zpracovávat [CWinApp::OnHelp](../mfc/reference/cwinapp-class.md#onhelp). Objekt aplikace přijímá zprávy nápovědy a pak směruje příkaz správně. To je nezbytné, protože výchozí směrování příkazů není vhodný pro určení nejvíce kontextu.  
  
 `CWinApp::OnHelp` se pokusí spustit WinHelp v následujícím pořadí:  
  
1.  Kontroluje aktivní `AfxMessageBox` volání s pomůže ID. Pokud je aktuálně aktivní okno se zprávou, WinHelp se spustí s kontextem vhodné pro dané pole zpráva.  
  
2.  Odešle zprávu WM_COMMANDHELP na aktivní okno. Pokud toto okno spuštěním WinHelp neodpoví, stejná zpráva dokud zpracovat zprávu nebo aktuální není nejvyšší úrovně okně pak posílá nadřazených členů toto okno.  
  
3.  Id_default_help – příkaz odešle do hlavního okna. Tím se spustí výchozího nápovědy. Tento příkaz je obvykle namapována na `CWinApp::OnHelpIndex`.  
  
 Globálně přepsat výchozí ID základní hodnoty (například 0x10000 pro příkazy a 0x20000 pro prostředky, jako je například dialogová okna), by měly přepsat aplikaci [CWinApp::WinHelp](../mfc/reference/cwinapp-class.md#winhelp).  
  
 Pokud chcete přepsat, tato funkce a způsobem, že je určen kontextové nápovědy, by měla řídit WM_COMMANDHELP zprávy. Můžete chtít poskytují podrobnější nápovědy směrování než poskytuje rozhraní, protože pouze probíhá hloubky aktuální podřízeného okna MDI. Můžete také zadat konkrétnější nápovědy pro konkrétní okno nebo dialogové okno, případně podle aktuální vnitřní stav tohoto objektu nebo aktivní ovládací prvek v dialogovém okně.  
  
## <a name="wmcommandhelp"></a>WM_COMMANDHELP  
  
```  
 
afx_msg LRESULT CWnd::OnCommandHelp(WPARAM wParam, LPARAM lParam)  
 
```  
  
 WM_COMMANDHELP je privátní zpráva Windows MFC, který je přijatých aktivní okno, pokud se požaduje nápovědy. Když okna obdrží tuto zprávu, může volat `CWinApp::WinHelp` s kontextem, který odpovídá okna vnitřní stav.  
  
 `lParam`  
 Obsahuje kontext aktuálně k dispozici nápověda. `lParam` Pokud byla zjištěna žádná nápověda kontextu je nulová. Implementace `OnCommandHelp` můžete použít ID kontextu v `lParam` k určení různých kontext nebo můžete stačí předat jej do `CWinApp::WinHelp`.  
  
 `wParam`  
 Se nepoužívá a bude nula.  
  
 Pokud `OnCommandHelp` volání funkce `CWinApp::WinHelp`, měla by vrátit `TRUE`. Vrácení `TRUE` zastaví směrování tohoto příkazu pro jiné třídy a další windows.  
  
## <a name="help-mode-shiftf1-help"></a>Režim nápovědy (Shift + F1 – Nápověda)  
 Jde o druhou podobu Kontextová nápověda. Tento režim je obecně zadání stisknutím kláves SHIFT + F1 nebo prostřednictvím nabídky panelu nástrojů. Je implementovaný jako příkaz (**id_context_help –**). Hák filtr zpráv se nepoužívá k převede tento příkaz při modální dialogové okno nebo nabídky je aktivní, proto tento příkaz je k dispozici pouze uživateli, když se aplikace spouští hlavní message pump (`CWinApp::Run`).  
  
 Po zadání tohoto režimu, ukazatelem myši nápovědy se zobrazí přes všechny oblasti aplikace, i v případě, že aplikace by za normálních okolností zobrazit svou vlastní kurzor pro tuto oblast (např. nastavení velikosti ohraničení okno). Uživatel je možné používat myš nebo klávesnice a vyberte příkaz. Místo provedení příkazu, zobrazení nápovědy na tento příkaz. Také uživatel může kliknout na objekt viditelný na obrazovce, například tlačítka na panelu nástrojů a zobrazí nápovědu pro tento objekt. Tento režim nápovědy poskytuje `CWinApp::OnContextHelp`.  
  
 Během provádění této smyčky, všechny klávesové vstup je neaktivní, s výjimkou klíče, které přístup k nabídce. Navíc se stále provádí překlad příkaz prostřednictvím `PreTranslateMessage` umožňující uživateli pomocí klávesy akcelerátoru a zobrazit nápovědu k tomuto příkazu.  
  
 Pokud existují konkrétní překlady nebo akce trvá umístit `PreTranslateMessage` funkce, který by neměl probíhat během režimu SHIFT + F1 – Nápověda, měli byste zkontrolovat `m_bHelpMode` členem `CWinApp` před provedením těchto operací. `CDialog` Implementace `PreTranslateMessage` kontroluje to před voláním `IsDialogMessage`, např. Během režimu SHIFT + F1 to zakáže "dialogové okno navigační" klávesy na nemodální dialogová okna. Kromě toho `CWinApp::OnIdle` je stále volána v průběhu této smyčky.  
  
 Pokud se uživatel rozhodne příkazu v nabídce, se zpracovává jako nápovědu v tomto příkazu (prostřednictvím **WM_COMMANDHELP**, viz níže). Pokud uživatel klikne viditelné oblast okna aplikace, rozhodne, zda je klikněte na tlačítko nonclient nebo klikněte na klienta. `OnContextHelp` mapování obslužných rutin nonclient klikne na kliknutí klienta automaticky. Pokud je klient kliknutím, pak odešle **WM_HELPHITTEST** do okna označeného. Pokud toto okno vrátí nenulovou hodnotu, tato hodnota se používá jako kontext nápovědu. Pokud vrátí hodnotu nula, `OnContextHelp` pokusí nadřazeného okna (a které se jeho nadřazeným prvkem a tak dále). Pokud nelze určit kontext nápovědy, výchozí hodnota je k odeslání **id_default_help –** příkaz do hlavního okna, která se pak (obvykle) mapuje na `CWinApp::OnHelpIndex`.  
  
## <a name="wmhelphittest"></a>WM_HELPHITTEST  
  
```  
 
afx_msg LRESULT CWnd::OnHelpHitTest(
WPARAM, LPARAM lParam)  
```  
  
 **WM_HELPHITTEST** je zprávu MFC privátní windows, který přijme aktivní okno klikli během režimu SHIFT + F1 – Nápověda. Když okna obdrží tuto zprávu, vrátí ID pomůže DWORD pro použití podle WinHelp.  
  
 LOWORD(lParam)  
 obsahuje souřadnice zařízení osy x, kde myši označeného relativně k klientské oblasti okna.  
  
 HIWORD(lParam)  
 obsahuje souřadnice osy y.  
  
 `wParam`  
 Se nepoužívá a bude nula. Pokud je vrácená hodnota nenulové, WinHelp je volán s tohoto kontextu. Pokud návratovou hodnotu nula, nadřazeného okna je dotazován na nápovědu.  
  
 V mnoha případech můžete využít přístupů k testování kódu, které už můžete mít. V tématu implementace **CToolBar::OnHelpHitTest** příklad zpracování **WM_HELPHITTEST** zprávy (kód využívá vstupů do testovací kód použitý na tlačítka a popisy tlačítek v `CControlBar`).  
  
## <a name="mfc-application-wizard-support-and-makehm"></a>Podpora průvodce aplikací MFC a makehm –  
 Průvodce aplikací MFC vytvoří soubory potřebné k vytvoření souboru nápovědy (soubory .cnt a HPJ). Zahrnuje také řadu soubory .rtf předem, které jsou přijímány kompilátoru nápovědy společnosti Microsoft. Řadu témata jsou dokončeny, ale některé může být nutné upravit pro konkrétní aplikaci.  
  
 Makehm – nástroj podporuje automatické vytváření souboru "Nápověda mapování". Makehm – nástroj může překládat prostředků aplikace. H soubor k mapování souboru nápovědy. Příklad:  
  
```  
#define IDD_MY_DIALOG   2000  
#define ID_MY_COMMAND   150  
```  
  
 bude převeden na:  
  
```  
HIDD_MY_DIALOG    0x207d0  
HID_MY_COMMAND    0x10096  
```  
  
 Tento formát je kompatibilní se zařízením kompilátoru nápovědy, který mapuje ID kontextu (čísla na pravé straně) s názvy tématu (symbolů na levé straně).  
  
 Zdrojový kód pro makehm – je k dispozici ve vzorku, nástroje pro programování MFC [makehm –](../visual-cpp-samples.md).  
  
## <a name="adding-help-support-after-running-the-mfc-application-wizard"></a>Přidání podpory nápovědy po spuštění Průvodce aplikací MFC  
 Nejlepší způsob, jak přidat Nápověda k aplikaci je zaškrtnutí políčka "Context-sensitive Help" na stránce Pokročilé funkce, Průvodce aplikací MFC před vytvořením aplikace. Tímto způsobem Průvodce aplikací MFC automaticky přidá položek mapování nezbytné zprávu na vaše `CWinApp`-odvozené třídy pro podporu nápovědy.  
  
## <a name="help-on-message-boxes"></a>Nápovědy na okna zpráv  
 Nápovědu k oken zpráv (někdy nazývané výstrahy) je podporováno prostřednictvím `AfxMessageBox` funkce, obálka pro `MessageBox` rozhraní API systému Windows.  
  
 Existují dvě verze `AfxMessageBox`, jeden pro použití s ID řetězce a druhou pro použití s ukazatel na řetězec (`LPCSTR`):  
  
```  
int AFXAPI AfxMessageBox(LPCSTR lpszText,
    UINT nType,
    UINT nIDHelp);

int AFXAPI AfxMessageBox(UINT nIDPrompt,
    UINT nType,
    UINT nIDHelp);
```  
  
 V obou případech je zadání volitelné pomůže ID.  
  
 V prvním případě výchozí hodnota pro nIDHelp je 0, který označuje žádná nápověda pro toto okno se zprávou. Stisknutí klávesy F1 při například zpráva pole je aktivní, uživatel neobdrží nápovědy (i v případě, že aplikace podporuje Nápověda). Pokud to není žádoucí, je třeba a ID pomohou stanovit nIDHelp.  
  
 V druhém případě je výchozí hodnota pro nIDHelp -1, která označuje, že ID pomoci je stejný jako nIDPrompt. Nápověda bude fungovat pouze v případě, že aplikace je povoleno nápovědy, samozřejmě). Pro nIDHelp by měl poskytovat 0, pokud chcete splnit žádná podpora nápovědy do pole zpráva. Budete chtít zpráva, která má být nápovědy povoleno, ale požadavky ID nápovědy jiný než nIDPrompt, jednoduše zadejte kladnou hodnotu pro nIDHelp z nIDPrompt.  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

