---
title: 'TN024: Zprávy a prostředky definované knihovnou MFC'
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.messages
helpviewer_keywords:
- resources [MFC]
- Windows messages [MFC], MFC-defined
- messages [MFC], MFC
- TN024
ms.assetid: c65353ce-8096-454b-ad22-1a7a1dd9a788
ms.openlocfilehash: 26f6effbafd8136661f0b1dc9a6b22138a23e547
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50639631"
---
# <a name="tn024-mfc-defined-messages-and-resources"></a>TN024: Zprávy a prostředky definované knihovnou MFC

> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována, protože byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata mohou být nesprávné nebo zastaralé. Nejnovější informace se doporučuje vyhledat téma zájmu v dokumentaci online index.

Tato poznámka popisuje interní zprávy Windows a formáty prostředku využívané prostředím MFC. Tyto informace vysvětluje implementace rozhraní framework a vám pomůže při ladění aplikace. Pro můžete i když není oficiálně podporován, tyto informace můžete použít některé z těchto informací pro pokročilé implementace.

Tato poznámka obsahuje podrobnosti o privátní implementace MFC; veškerý obsah se mohou změnit v budoucnu. Windows zpráv knihovny MFC mají význam v rámci pouze jednu aplikaci, ale bude v budoucnu změnit tak, aby obsahovala systémová zprávy.

Rozsah MFC soukromých zpráv Windows a typy prostředků jsou v rozsahu vyhrazené "systém" odložit podle Microsoft Windows. Aktuálně nejsou všechna čísla v rozsahu se používají, a v budoucnu může sloužit nová čísla v rozsahu. Aktuálně používané čísla mohou být změněny.

MFC privátní Windows, které zprávy jsou v rozsahu 0x360 -> 0x37F.

MFC privátnímu prostředku, typy jsou v rozsahu 0xF0 -> 0xFF.

**Zprávy Windows privátní knihovny MFC**

Tyto zprávy Windows se používají místo virtuálních funkcí jazyka C++, kde vyžádáním relativně volné párování mezi objekty oken a kde by nebylo vhodné virtuální funkci jazyka C++.

Tyto soukromých zpráv Windows a přidružené parametr struktury jsou deklarovány v privátní hlaviček knihovny MFC "AFXPRIV. H'. Zobrazí se upozornění, že váš kód, který obsahuje tato záhlaví mohou spoléhat na nedokumentované chování a budou pravděpodobně přerušení v budoucích verzí knihovny MFC.

Ve výjimečných případech z museli zpracovávat jeden z následujících zpráv by měl používat ON_MESSAGE – makro mapy zpráv a zpracovala zpráva obecný formát LRESULT/WPARAM/LPARAM.

**WM_QUERYAFXWNDPROC**

Tato zpráva se pošle na okno, které se vytváří. Ta se odešle velmi brzy v procesu vytváření jako způsob zjištění, zda je WndProc **AfxWndProc. AfxWndProc** vrátí hodnotu 1.

|||
|-|-|
|wParam|Nepoužívá se|
|lParam|Nepoužívá se|
|vrací|1, pokud zpracovává **AfxWndProc**|

**WM_SIZEPARENT**

Tato zpráva se pošle podle okno rámce do své přímé podřízené objekty během změny velikosti (`CFrameWnd::OnSize` volání `CFrameWnd::RecalcLayout` který volá `CWnd::RepositionBars`) do umístění ovládacích panelů kolem okraji rámečku. AFX_SIZEPARENTPARAMS struktura obsahuje aktuální obdélník dostupných klientských nadřazený a HDWP, (který může mít hodnotu NULL), pomocí kterého se má volat `DeferWindowPos` minimalizovat překreslení.

|||
|-|-|
|wParam|Nepoužívá se|
|lParam|Adresa struktury AFX_SIZEPARENTPARAMS|
|vrací|Nepoužívá se (0)|

Ignoruje se zpráva označuje, že okno nemá účasti v rozložení.

**WM_SETMESSAGESTRING**

Tato zpráva se pošle okno rámce požádat jej aktualizovat řádek zprávy ve stavovém řádku. ID řetězce nebo LPCSTR může být zadaný (ale nikoli oba současně).

|||
|-|-|
|wParam|Řetězec ID (nebo nula)|
|lParam|LPCSTR pro řetězec (nebo hodnota NULL)|
|vrací|Nepoužívá se (0)|

**WM_IDLEUPDATECMDUI**

Tato zpráva se pošle v nečinnosti provádět aktualizace doby nečinnosti obslužné rutiny aktualizace příkazů uživatelského rozhraní. Pokud okno (obvykle ovládací panel) zpracovává zprávy, vytvoří `CCmdUI` (nebo objektu odvozené třídy) a volat `CCmdUI::DoUpdate` pro každý "položky" v okně. To zase hledá obslužnou rutinu ON_UPDATE_COMMAND_UI pro objekty v řetězci obslužná rutina příkazu.

|||
|-|-|
|wParam|BOOL bDisableIfNoHandler|
|lParam|Nepoužívá se (0)|
|vrací|Nepoužívá se (0)|

*bDisableIfNoHandler* zakázat objekt uživatelského rozhraní, pokud dojde ON_UPDATE_COMMAND_UI ani obslužnou rutinu ON_COMMAND nenulové.

**WM_EXITHELPMODE**

Tato zpráva se odešle do `CFrameWnd` režim, který ukončíte kontextové nápovědy. Přijetí této zprávy ukončí modální smyčka tím, že `CFrameWnd::OnContextHelp`.

|||
|-|-|
|wParam|Nepoužívá se (0)|
|lParam|Nepoužívá se (0)|
|vrací|Nepoužívá se|

**WM_INITIALUPDATE**

Tato zpráva přijde šablonou dokumentu na všechny následníky okna rámce při není bezpečný pro jejich počáteční aktualizace. Mapuje se na volání `CView::OnInitialUpdate` však lze použít v ostatních `CWnd`-odvozené třídy pro další konečný aktualizaci.

|||
|-|-|
|wParam|Nepoužívá se (0)|
|lParam|Nepoužívá se (0)|
|vrací|Nepoužívá se (0)|

**WM_RECALCPARENT**

Tato zpráva se pošle podle zobrazení k jeho nadřazenému oknu (získané prostřednictvím `GetParent`) vynuťte přepočítání rozložení (obvykle bude volat nadřazené `RecalcLayout`). To se používá v serverových aplikacích OLE kde je nezbytné pro rámec růst s velikostí celková velikost zobrazení.

Je-li nadřazené okno tuto zprávu zpracuje ji by měl vrátí hodnotu PRAVDA a zadejte RECT předaný lParam s novou velikost klientské oblasti. Používá se v `CScrollView` správně zpracovat posuvníky (místo na mimo okno, když se přidají) při objektu serveru je aktivovat v místě.

|||
|-|-|
|wParam|Nepoužívá se (0)|
|lParam|Lprect – rectClient, může mít hodnotu NULL|
|vrací|Hodnota TRUE, pokud nový klientský obdélník vrátí, FALSE v opačném případě|

**WM_SIZECHILD**

Tato zpráva je odeslána `COleResizeBar` k jeho nadřazenému oknu (prostřednictvím `GetOwner`) když uživatel změní velikost panelu změny velikosti s úchyty pro změnu velikosti. `COleIPFrameWnd` Pokus o umístění okna rámce, protože uživatel požaduje reaguje na tuto zprávu.

Nové obdélník podle klienta souřadnicích relativních k okno rámce, který obsahuje změny velikosti panelu, je na který odkazuje lParam.

|||
|-|-|
|wParam|Nepoužívá se (0)|
|lParam|Lprect – rectNew|
|vrací|Nepoužívá se (0)|

**WM_DISABLEMODAL**

Tato zpráva se pošle se všem oknům rozbalovací vlastní okna rámce, který je právě deaktivována. Okno rámce používá k určení, jestli se má zakázat v automaticky otevíraném okně výsledek.

Můžete to provést zvláštní zpracování v automaticky otevíraném okně, když rámec přejde do modálního stavu nebo zabránit získávání zakázána určité automaticky otevíraná okna. Popisy tlačítek zničit samotné při oknem rámce přejde do modálního stavu, například pomocí tuto zprávu.

|||
|-|-|
|wParam|Nepoužívá se (0)|
|lParam|Nepoužívá se (0)|
|vrací|Nenulový k **není** zakázat v okně, 0 znamená, v okně se deaktivuje.|

**WM_FLOATSTATUS**

Tato zpráva se pošle se všem oknům rozbalovací vlastněné okno rámce, když rámec je buď aktivuje nebo deaktivuje podle jiného okna nejvyšší úrovně rámce. Používá se v implementaci MFS_SYNCACTIVE v `CMiniFrameWnd`, k aktivaci těchto automaticky otevíraná okna udržovat synchronizované s aktivací okna rámce.

|||
|-|-|
|wParam|Je jedním z následujících hodnot:<br /><br /> FS_SHOW<br /><br /> FS_HIDE<br /><br /> FS_ACTIVATE<br /><br /> FS_DEACTIVATE<br /><br /> FS_ENABLEFS_DISABLE<br /><br /> FS_SYNCACTIVE|
|lParam|Nepoužívá se (0)|

Návratová hodnota by měla být nenulové Pokud FS_SYNCACTIVE je sada a synchronizuje okno jeho aktivaci s použitím nadřazeného rámce. `CMiniFrameWnd` Vrátí nenulové, pokud je nastaven styl MFS_SYNCACTIVE.

Další informace najdete v tématu provádění `CMiniFrameWnd`.

## <a name="wmactivatetoplevel"></a>WM_ACTIVATETOPLEVEL

Tato zpráva se pošle na okno nejvyšší úrovně, když se aktivuje nebo deaktivuje okno v jeho "nejvyšší úrovně skupina". Okno je součástí skupiny nejvyšší úrovně, pokud je okno nejvyšší úrovně (žádné nadřazené nebo vlastník) nebo vlastníkem je takové okno. Tato zpráva se používá podobný WM_ACTIVATEAPP však lze použít v situacích, kdy jsou windows, které patří do různých procesů kombinovat v jednom okně hierarchii (běžné v aplikacích OLE).

## <a name="wmcommandhelp-wmhelphittest-wmexithelpmode"></a>WM_EXITHELPMODE WM_COMMANDHELP WM_HELPHITTEST,

Tyto zprávy se používají v implementaci kontextové nápovědy. Najdete [Technická poznámka 28](../mfc/tn028-context-sensitive-help-support.md) Další informace.

## <a name="mfc-private-resource-formats"></a>Formáty prostředku privátní knihovny MFC

V současné době MFC definuje dva formáty privátnímu prostředku: rt_toolbar – a RT_DLGINIT.

## <a name="rttoolbar-resource-format"></a>Rt_toolbar – prostředek formátu

Výchozí nástrojů poskytovaných AppWizard je založená na vlastní prostředek rt_toolbar –, která byla zavedena v MFC 4.0. Můžete upravit tento prostředek pomocí editoru panelu nástrojů.

## <a name="rtdlginit-resource-format"></a>Formát prostředku RT_DLGINIT

Jeden formát privátnímu prostředku knihovny MFC slouží k uložení informace o inicializaci navíc dialogového okna. To zahrnuje počáteční řetězce uložené v poli se seznamem. Formát tohoto prostředku nespouští ručně upravit, ale je zpracována Visual C++.

Visual C++ a tento prostředek RT_DLGINIT nemusí použít související funkce MFC, protože existují API alternativu k použití informací v prostředku. Pomocí Visual C++ je mnohem jednodušší psaní, udržovat a překládat vaší aplikace v dlouhodobém horizontu.

Základní struktura RT_DLGINIT prostředků vypadá takto:

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

Opakované oddíl obsahuje ID ovládacího prvku k odeslání zprávy, zprávu # pro odesílání (normální zpráva Windows) a s proměnnou délkou data. Zprávy Windows se posílá ve formuláři:

```
SendDlgItemMessage(<Control ID>, <Message #>, 0, &<Data>);
```

To je velmi obecného formátu, všechny zprávy Windows a data obsahu. Editor prostředků Visual C++ a knihovnou MFC podporují jenom omezenou podmnožinou zpráv Windows: CB_ADDSTRING pro počáteční seznam voleb pro pole se seznamem (data je textový řetězec).

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

