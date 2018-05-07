---
title: 'TN024: Zprávy definované MFC a prostředky | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.messages
dev_langs:
- C++
helpviewer_keywords:
- resources [MFC]
- Windows messages [MFC], MFC-defined
- messages [MFC], MFC
- TN024
ms.assetid: c65353ce-8096-454b-ad22-1a7a1dd9a788
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4dd403693dd860966cfcca42eacc909b01eb513b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="tn024-mfc-defined-messages-and-resources"></a>TN024: Zprávy a prostředky definované knihovnou MFC
> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována vzhledem k tomu, že byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata může být zastaralý nebo není správný. Nejnovější informace se doporučuje, vyhledejte téma týkající se v indexu online dokumentaci.  
  
 Tato poznámka popisuje interní zpráv systému Windows a využívané prostředím MFC formáty prostředku. Tyto informace popisuje implementace rozhraní a bude vám pomůže při ladění aplikace. Pro dobrodružná i když není oficiálně podporován, tyto informace můžete použít některé z těchto informací pro pokročilé implementace.  
  
 Tato poznámka obsahuje podrobnosti o privátní implementace MFC; veškerý obsah se mohou změnit v budoucnu. MFC privátní zpráv systému Windows mají význam v rámci oboru jenom jedna aplikace, ale bude v budoucnu změnit tak, aby obsahovala systémové zprávy.  
  
 Zprávy Windows privátní rozsah MFC a typy prostředků jsou v rozsahu vyhrazené "systém" vyčleněné systémem Microsoft Windows. Aktuálně nejsou všechna čísla v rozsazích se používají, a v budoucnu může sloužit nová čísla v rozsahu. Aktuálně používané čísla, která se dají změnit.  
  
 MFC privátní Windows, které zprávy jsou v rozsahu 0x360 -> 0x37F.  
  
 MFC privátního prostředku, které typy jsou v rozsahu 0xF0 -> 0xFF.  
  
 **Zprávy Windows privátní knihovny MFC**  
  
 Tyto zprávy Windows se používají místo virtuálních funkcí jazyka C++, pokud je poměrně volné párování požadované mezi objekty oken a kde by nebylo vhodné C++ virtuální funkce.  
  
 Tyto privátní zpráv systému Windows a přidružené parametr struktury jsou deklarované v hlavičce privátní MFC ' AFXPRIV. H ". Se upozornění, že některé z vašeho kódu, která zahrnuje tuto hlavičku může být spoléhat na nedokumentovanými chování a budou pravděpodobně přerušení v budoucnosti verze knihovny MFC.  
  
 Ve výjimečných případě museli zpracovat jeden z těchto zpráv, měli byste použít `ON_MESSAGE` zpráva makra mapy a zpracování zprávy v obecné LRESULT/WPARAM/LPARAM formátu.  
  
 **WM_QUERYAFXWNDPROC**  
  
 Tato zpráva je odeslána do okna, který je právě vytvářena. Ta se odešle velmi brzy v procesu vytváření jako způsobu určení, zda je WndProc **AfxWndProc. AfxWndProc** vrátí hodnotu 1.  
  
|||  
|-|-|  
|wParam|Nepoužívá se|  
|lParam|Nepoužívá se|  
|vrací|1, pokud zpracovává **AfxWndProc**|  
  
 **WM_SIZEPARENT**  
  
 Tuto zprávu posílá okně s rámečkem jeho přímé podřízené objekty při změně velikosti (**CFrameWnd::OnSize** volání `CFrameWnd::RecalcLayout` který volá `CWnd::RepositionBars`) změňte umístění ovládací pruhy kolem na straně rámečku. **AFX_SIZEPARENTPARAMS** struktura obsahuje aktuální rámeček dostupných klientů nadřazený a HDWP, (který může mít hodnotu NULL) ke které má být volání `DeferWindowPos` minimalizovat překreslení.  
  
|||  
|-|-|  
|wParam|Nepoužívá se|  
|lParam|Adresa **AFX_SIZEPARENTPARAMS** struktura|  
|vrací|Nepoužívá se (0)|  
  
 Ignorování zprávy označuje, že okno neberou v rámci v rozložení.  
  
 **WM_SETMESSAGESTRING**  
  
 Tato zpráva je odeslána do okna rámečkem a požádejte ho aktualizovat řádek zprávy ve stavovém řádku. Řetězec ID nebo LPCSTR může být zadaný (ale ne pomocí obou).  
  
|||  
|-|-|  
|wParam|Řetězec ID (nebo nula)|  
|lParam|LPCSTR pro řetězec (nebo hodnota NULL)|  
|vrací|Nepoužívá se (0)|  
  
 **WM_IDLEUPDATECMDUI**  
  
 Tato zpráva je odeslána v nečinnosti implementovat doby nečinnosti aktualizace obslužné rutiny aktualizace příkaz uživatelského rozhraní. Pokud okno (obvykle ovládacích pruhů) zpracovává zprávy, vytvoří `CCmdUI` (nebo objektu odvozené třídy) a volání **CCmdUI::DoUpdate** pro každou z "položky" v okně. To zase zkontroluje `ON_UPDATE_COMMAND_UI` obslužné rutiny pro objekty v řetězu obslužná rutina příkazu.  
  
|||  
|-|-|  
|wParam|BOOL bDisableIfNoHandler|  
|lParam|Nepoužívá se (0)|  
|vrací|Nepoužívá se (0)|  
  
 *bDisableIfNoHandler* nenulový a zakázat objekt uživatelského rozhraní, pokud není ani `ON_UPDATE_COMMAND_UI` ani `ON_COMMAND` obslužné rutiny.  
  
 **WM_EXITHELPMODE**  
  
 Tato zpráva je odeslána do `CFrameWnd` režimu, které chcete-li ukončit závislé na kontextu pomoci. Přijetí této zprávy ukončí modální smyčky spustí **CFrameWnd::OnContextHelp.**  
  
|||  
|-|-|  
|wParam|Nepoužívá se (0)|  
|lParam|Nepoužívá se (0)|  
|vrací|Nepoužívá se|  
  
 **WM_INITIALUPDATE**  
  
 Tato zpráva je odeslána šablony dokumentu všech potomků okně s rámečkem při je bezpečné, aby se jejich počáteční aktualizace. Se mapuje na volání `CView::OnInitialUpdate` ale můžou používat v jiných `CWnd`-odvozených tříd pro jiné jednorázové aktualizaci.  
  
|||  
|-|-|  
|wParam|Nepoužívá se (0)|  
|lParam|Nepoužívá se (0)|  
|vrací|Nepoužívá se (0)|  
  
 **WM_RECALCPARENT**  
  
 Tuto zprávu zobrazení odesílají do jeho nadřazeného okna (získat prostřednictvím `GetParent`) Chcete-li vynutit přepočítání rozložení (obvykle bude volat nadřazený `RecalcLayout`). To se používá v aplikace serveru OLE tam, kde je nezbytné pro rámec zvětšují s růstem celková velikost zobrazení.  
  
 Pokud tuto zprávu zpracuje nadřazeného okna měl by vrátí hodnotu TRUE a vyplnění Rect – předaná lParam s novou velikost klientské oblasti. To se používá v `CScrollView` správně zpracovat posuvníky (místo na mimo okno při přidání) po objekt serveru aktivaci.  
  
|||  
|-|-|  
|wParam|Nepoužívá se (0)|  
|lParam|Lprect – rectClient, může mít hodnotu NULL|  
|vrací|Hodnota TRUE, pokud je to nový klient obdélníku vrácen, FALSE jinak hodnota|  
  
 **WM_SIZECHILD**  
  
 Tato zpráva se odešle pomocí `COleResizeBar` do okna jeho vlastníka (prostřednictvím `GetOwner`) když uživatel změní velikost panelu změny velikosti s popisovači změny velikosti. `COleIPFrameWnd` Probíhá pokus o změnit umístění okně s rámečkem jako uživatel vyžaduje reaguje na tuto zprávu.  
  
 Je nové obdélníku, zadaný v klienta souřadnicích relativních k rámce okna, která obsahuje změny velikosti panelu, na kterou lParam odkazoval.  
  
|||  
|-|-|  
|wParam|Nepoužívá se (0)|  
|lParam|Lprect – rectNew|  
|vrací|Nepoužívá se (0)|  
  
 **WM_DISABLEMODAL**  
  
 Tato zpráva je odeslána do všech automaticky otevíraná okna vlastníkem rámec okna, který je právě deaktivována. Okně s rámečkem používá výsledek k určení, zda chcete zakázat překryvné okno.  
  
 Můžete to provést speciální zpracování v místním okně, když rámečku přejde modální stavu nebo za účelem udržování určité automaticky otevíraná okna od získávání zakázána. Popisy tlačítek destroy sami, když se okně s rámečkem dostane do modální stavu, například pomocí této zprávy.  
  
|||  
|-|-|  
|wParam|Nepoužívá se (0)|  
|lParam|Nepoužívá se (0)|  
|vrací|Nenulová k **není** zakázat okna, 0 znamená okno bude zakázán.|  
  
 **WM_FLOATSTATUS**  
  
 Tato zpráva je odeslána do všech automaticky otevíraná okna vlastníkem okně s rámečkem při rámečku je buď aktivace nebo deaktivace pomocí jiného nejvyšší úrovně rámce okna. Toto je používáno implementace **MFS_SYNCACTIVE** v `CMiniFrameWnd`, aby synchronizovaná s aktivace nejvyšší úrovně rámce okna aktivace tato automaticky otevíraná okna.  
  
|||  
|-|-|  
|wParam|Je jedním z následujících hodnot:<br /><br /> **FS_SHOW**<br /><br /> **FS_HIDE**<br /><br /> **FS_ACTIVATE**<br /><br /> **FS_DEACTIVATE**<br /><br /> **FS_ENABLEFS_DISABLE**<br /><br /> **FS_SYNCACTIVE**|  
|lParam|Nepoužívá se (0)|  
  
 Návratová hodnota by měla být nulová Pokud **FS_SYNCACTIVE** je sada a synchronizuje okno její aktivaci s použitím nadřazeného rámce. `CMiniFrameWnd` vrátí nenulový styl nastavena na **MFS_SYNCACTIVE.**  
  
 Další informace najdete v tématu implementace `CMiniFrameWnd`.  
  
## <a name="wmactivatetoplevel"></a>WM_ACTIVATETOPLEVEL  
 Tato zpráva je odeslána do nejvyšší úrovně okna při aktivace nebo deaktivace okna v jeho "nejvyšší úrovně skupinu". Okno je součástí skupiny nejvyšší úrovně, pokud je okno nejvyšší úrovně (žádný nadřazený nebo vlastníka), nebo je vlastněná serverem takového okna. Tato zpráva je podobný používají, aby **WM_ACTIVATEAPP,** , ale funguje v situacích, kde jsou kombinované windows, které patří do různých procesů v jednom okně hierarchii (v aplikacích OLE běžné).  
  
## <a name="wmcommandhelp-wmhelphittest-wmexithelpmode"></a>WM_EXITHELPMODE WM_COMMANDHELP, WM_HELPHITTEST,  
 Tyto zprávy se používají k implementaci Kontextová nápověda. Naleznete [Technická poznámka 28](../mfc/tn028-context-sensitive-help-support.md) Další informace.  
  
## <a name="mfc-private-resource-formats"></a>Formáty prostředku privátní knihovny MFC  
 V současné době MFC definuje dva formáty privátního prostředku: **rt_toolbar –** a **RT_DLGINIT**.  
  
## <a name="rttoolbar-resource-format"></a>Formát rt_toolbar – prostředek  
 Výchozí panel nástrojů poskytl objekty AppWizard je založena na **rt_toolbar –** vlastních prostředků, která byla představena v MFC 4.0. Můžete upravit tento prostředek pomocí editoru panelu nástrojů.  
  
## <a name="rtdlginit-resource-format"></a>Formát prostředku RT_DLGINIT  
 Jednoho formátu privátního prostředku MFC slouží k uložení informace o inicializaci navíc dialogové okno. To zahrnuje počáteční řetězce, které jsou uložené v poli se seznamem. Formát tohoto prostředku nespouští ručně upravovat, ale jsou zpracována Visual C++.  
  
 Visual C++ a to **RT_DLGINIT** prostředků nemusí používat související funkce MFC, protože rozhraní API alternativu k použití informací v prostředku. Pomocí Visual C++ proto jednodušší k zápisu, udržovat a převede dlouhodobě vaší aplikace.  
  
 Základní struktura **RT_DLGINIT** prostředků je následující:  
  
```  
+---------------+    \  
| Control ID    |   UINT             |  
+---------------+    |  
| Message #     |   UINT             |  
+---------------+    |  
|length of data |   DWORD            |  
+---------------+    |   Repeated  
|   Data        |   Variable Length  |   for each control  
|   ...         |   and Format       |   and message  
+---------------+    /  
|     0         |   BYTE  
+---------------+  
```  
  
 Opakované část obsahuje ID ovládacího prvku odeslat zprávu, zpráva # pro odesílání (normální zpráva systému Windows) a proměnlivou délkou dat. Ve formuláři je odeslána zpráva systému Windows:  
  
```  
SendDlgItemMessage(<Control ID>, <Message #>, 0, &<Data>);
```  
  
 To je velmi obecná formát, povolení všechny zpráv systému Windows a dat obsahu. Editor prostředků Visual C++ a rozhraní MFC podporují jenom omezenou podmnožinou zpráv systému Windows: CB_ADDSTRING pro počáteční seznam možností pro pole se seznamem (data je textový řetězec).  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

