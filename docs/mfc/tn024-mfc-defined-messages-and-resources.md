---
title: 'TN024: Zprávy a prostředky definované knihovnou MFC'
ms.date: 11/04/2016
helpviewer_keywords:
- resources [MFC]
- Windows messages [MFC], MFC-defined
- messages [MFC], MFC
- TN024
ms.assetid: c65353ce-8096-454b-ad22-1a7a1dd9a788
ms.openlocfilehash: 24bcacd46b839babe9c9c89facb1cc56d18c0ee5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370355"
---
# <a name="tn024-mfc-defined-messages-and-resources"></a>TN024: Zprávy a prostředky definované knihovnou MFC

> [!NOTE]
> Následující technická poznámka nebyla aktualizována od doby, kdy byla poprvé zahrnuta do online dokumentace. V důsledku toho mohou být některé postupy a témata zastaralé nebo nesprávné. Chcete-li získat nejnovější informace, doporučujeme vyhledat téma zájmu v online indexu dokumentace.

Tato poznámka popisuje interní zprávy systému Windows a formáty prostředků používané knihovnou MFC. Tyto informace vysvětlují implementaci rozhraní a pomohou při ladění aplikace. Pro dobrodružné, i když všechny tyto informace jsou oficiálně nepodporované, můžete použít některé z těchto informací pro pokročilé implementace.

Tato poznámka obsahuje podrobnosti soukromé implementace knihovny MFC. veškerý obsah se může v budoucnu změnit. Soukromé zprávy systému Windows knihovny MFC mají význam pouze v rozsahu jedné aplikace, ale v budoucnu se změní tak, aby obsahovaly zprávy celého systému.

Rozsah soukromých zpráv knihovny MFC a typů prostředků systému Windows je v vyhrazeném rozsahu systému vyhrazeném systémem Microsoft Windows. V současné době se nepoužívají všechna čísla v rozsahu a v budoucnu mohou být použita nová čísla v rozsahu. Aktuálně používaná čísla mohou být změněna.

Soukromé zprávy systému Windows knihovny MFC jsou v rozsahu 0x360->0x37F.

Typy soukromých prostředků knihovny MFC jsou v rozsahu 0xF0->0xFF.

**Soukromé zprávy systému Windows knihovny MFC**

Tyto zprávy systému Windows se používají místo virtuálních funkcí jazyka C++, kde je vyžadována relativně volná vazba mezi objekty okna a kde virtuální funkce jazyka C++ by nebyla vhodná.

Tyto soukromé zprávy systému Windows a přidružené struktury parametrů jsou deklarovány v privátní záhlaví knihovny MFC AFXPRIV. H'. Upozorňujeme, že jakýkoli kód, který obsahuje toto záhlaví, může spoléhat na nezdokumentované chování a pravděpodobně se v budoucích verzích knihovny MFC přeruší.

Ve výjimečných případech, kdy potřebujete zpracovat jednu z těchto zpráv, byste měli použít makro mapy zpráv ON_MESSAGE zprávy a zpracovat zprávu v obecném formátu LRESULT/WPARAM/LPARAM.

**WM_QUERYAFXWNDPROC**

Tato zpráva je odeslána do okna, které je vytvářeno. To je odesláno velmi brzy v procesu vytváření jako metoda určení, zda Je WndProc **AfxWndProc. AfxWndProc** vrátí 1.

|||
|-|-|
|wParam|Nepoužívá se.|
|Lparam|Nepoužívá se.|
|vrací|1, pokud je **zpracována afxWndProc**|

**WM_SIZEPARENT**

Tato zpráva je odeslána okno rámce jeho bezprostřední`CFrameWnd::OnSize` děti `CFrameWnd::RecalcLayout` během `CWnd::RepositionBars`změna velikosti (volání, které volá) pro přemístění ovládacích panelů kolem strany rámce. AFX_SIZEPARENTPARAMS struktura obsahuje aktuální dostupný klient obdélník nadřazeného a HDWP (což může být NULL), s níž chcete volat `DeferWindowPos` minimalizovat překreslení.

|||
|-|-|
|wParam|Nepoužívá se.|
|Lparam|Adresa AFX_SIZEPARENTPARAMS struktury|
|vrací|Nepoužívá se (0)|

Ignorování zprávy znamená, že okno se neúčastní rozložení.

**WM_SETMESSAGESTRING**

Tato zpráva je odeslána do okna rámce a požádá ji o aktualizaci řádku zprávy ve stavovém řádku. Lze zadat ID řetězce nebo LPCSTR (ale ne obojí).

|||
|-|-|
|wParam|ID řetězce (nebo nula)|
|Lparam|LPCSTR pro řetězec (nebo NULL)|
|vrací|Nepoužívá se (0)|

**WM_IDLEUPDATECMDUI**

Tato zpráva je odeslána v době nečinnosti k implementaci aktualizace nečinnosti obslužné rutiny příkazu aktualizace příkazu. Pokud okno (obvykle ovládací panel) zpracovává zprávu, `CCmdUI` vytvoří objekt (nebo objekt odvozené třídy) a volání `CCmdUI::DoUpdate` pro každou z "položek" v okně. To bude zase kontrolovat obslužnou rutinu ON_UPDATE_COMMAND_UI pro objekty v řetězci obslužné rutiny příkazu.

|||
|-|-|
|wParam|BOOL bDisableIfNoHandler|
|Lparam|Nepoužívá se (0)|
|vrací|Nepoužívá se (0)|

*bDisableIfNoHandler* je nenulová zakázat objekt ui, pokud není ani ON_UPDATE_COMMAND_UI ani obslužná rutina ON_COMMAND.

**WM_EXITHELPMODE**

Tato zpráva je `CFrameWnd` zaúčtována do tohoto ukončovat kontextově citlivý režim nápovědy. Přijetí této zprávy ukončí modální `CFrameWnd::OnContextHelp`smyčky spuštěné společností .

|||
|-|-|
|wParam|Nepoužívá se (0)|
|Lparam|Nepoužívá se (0)|
|vrací|Nepoužívá se.|

**WM_INITIALUPDATE**

Tato zpráva je odeslána šablonou dokumentu všem potomkům okna rámce, když je pro ně bezpečné provést počáteční aktualizaci. Mapuje se na `CView::OnInitialUpdate` volání, ale `CWnd`může být použit v jiných odvozených třídách pro další aktualizaci jednoho výstřelu.

|||
|-|-|
|wParam|Nepoužívá se (0)|
|Lparam|Nepoužívá se (0)|
|vrací|Nepoužívá se (0)|

**WM_RECALCPARENT**

Tato zpráva je odeslána zobrazením do `GetParent`nadřazeného okna (získaného prostřednictvím) k vynucení přepočtu rozvržení (obvykle bude rodič volat). `RecalcLayout` Používá se v aplikacích serveru OLE, kde je nezbytné pro rámec zvětšit velikost jako celková velikost zobrazení roste.

Pokud nadřazené okno zpracuje tuto zprávu, měla by vrátit hodnotu TRUE a vyplnit rect předanou v lParam novou velikostí klientské oblasti. Používá se `CScrollView` v správně zpracovat posuvníky (místo pak na vnější straně okna při jejich přidání) při aktivaci objektu serveru na místě.

|||
|-|-|
|wParam|Nepoužívá se (0)|
|Lparam|LPRECT rectClient, může být NULL|
|vrací|PRAVDA, pokud byl vrácen nový obdélník klienta, JINAK NEPRAVDA|

**WM_SIZECHILD**

Tato zpráva je `COleResizeBar` odeslána do `GetOwner`okna vlastníka (přes) při uživatel změní velikost pruhu s úchyty pro měnit velikost. `COleIPFrameWnd`odpoví na tuto zprávu pokusem o přemístění okna rámce podle požadavku uživatele.

Nový obdélník, vzhledem k souřadnice klienta vzhledem k okno rámce, který obsahuje velikost pruhu, je ukázal na lParam.

|||
|-|-|
|wParam|Nepoužívá se (0)|
|Lparam|LPRECT rectNovinka|
|vrací|Nepoužívá se (0)|

**WM_DISABLEMODAL**

Tato zpráva je odeslána do všech automaticky otevíraných oken vlastněných deaktivovaným oknem rámce. Okno rámce používá výsledek k určení, zda chcete zakázat automaticky otevírané okno.

Můžete to použít k provedení speciálnízpracování v automaticky otevírané okno, když snímek vstoupí do modálního stavu nebo aby některé pop-up okna od získání zakázán. Popisky pomocí této zprávy zničit sami, když okno rámce přejde do modálního stavu, například.

|||
|-|-|
|wParam|Nepoužívá se (0)|
|Lparam|Nepoužívá se (0)|
|vrací|Nenulová **NOT** nezakácet okno, 0 znamená, že okno bude zakázáno|

**WM_FLOATSTATUS**

Tato zpráva je odeslána do všech automaticky otevíraných oken vlastněných oknem rámce, pokud je rámeček aktivován nebo deaktivován jiným oknem rámce nejvyšší úrovně. To je používáno při `CMiniFrameWnd`implementaci MFS_SYNCACTIVE v , aby aktivace těchto pop-up okna v synchronizaci s aktivací horní úrovně okna rámce.

|||
|-|-|
|wParam|Je jedna z následujících hodnot:<br /><br /> FS_SHOW<br /><br /> FS_HIDE<br /><br /> FS_ACTIVATE<br /><br /> FS_DEACTIVATE<br /><br /> FS_ENABLEFS_DISABLE<br /><br /> FS_SYNCACTIVE|
|Lparam|Nepoužívá se (0)|

Vrácená hodnota by měla být nenulová, pokud je nastavena FS_SYNCACTIVE a okno syncronizes jeho aktivace s nadřazený rámec. `CMiniFrameWnd`vrátí nenulovou, pokud je styl nastaven na MFS_SYNCACTIVE.

Další informace naleznete v `CMiniFrameWnd`implementaci .

## <a name="wm_activatetoplevel"></a>WM_ACTIVATETOPLEVEL

Tato zpráva je odeslána do okna nejvyšší úrovně, pokud je okno v jeho "skupině nejvyšší úrovně" aktivováno nebo deaktivováno. Okno je součástí skupiny nejvyšší úrovně, pokud se jedná o okno nejvyšší úrovně (bez nadřazeného nebo vlastníka) nebo je vlastněno takovým oknem. Tato zpráva je podobná jako WM_ACTIVATEAPP, ale funguje v situacích, kdy jsou okna patřící do různých procesů smíchána v hierarchii jednoho okna (běžné v aplikacích OLE).

## <a name="wm_commandhelp-wm_helphittest-wm_exithelpmode"></a>WM_COMMANDHELP, WM_HELPHITTEST, WM_EXITHELPMODE

Tyto zprávy se používají při implementaci kontextové nápovědy. Další informace naleznete v [technické poznámce 28.](../mfc/tn028-context-sensitive-help-support.md)

## <a name="mfc-private-resource-formats"></a>Formáty soukromých prostředků knihovny MFC

Knihovna MFC v současné době definuje dva formáty soukromých prostředků: RT_TOOLBAR a RT_DLGINIT.

## <a name="rt_toolbar-resource-format"></a>RT_TOOLBAR formát zdroje

Výchozí panel nástrojů dodaný aplikací AppWizard je založen na vlastním prostředku RT_TOOLBAR, který byl zaveden v knihovně MFC 4.0. Tento prostředek můžete upravit pomocí editoru panelu nástrojů.

## <a name="rt_dlginit-resource-format"></a>RT_DLGINIT formát zdroje

Jeden formát soukromého prostředku knihovny MFC se používá k ukládání dalších informací o inicializaci dialogu. To zahrnuje počáteční řetězce uložené v poli se seznamem. Formát tohoto prostředku není určen k ruční úpravě, ale je zpracován visual c++.

Visual C++ a tento RT_DLGINIT prostředek nejsou nutné k použití související funkce knihovny MFC, protože existují alternativa rozhraní API k použití informací v prostředku. Použití visual c++ usnadňuje psaní, údržbu a překlad aplikace v dlouhodobém horizontu.

Základní struktura RT_DLGINIT zdroje je následující:

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

Opakovaná část obsahuje ID ovládacího prvku, do kterých se má zpráva odeslat, číslo zprávy k odeslání (normální zpráva systému Windows) a proměnnou délku dat. Zpráva systému Windows je odeslána ve formuláři:

```
SendDlgItemMessage(<Control ID>, <Message #>, 0, &<Data>);
```

Jedná se o velmi obecný formát, který umožňuje všechny zprávy systému Windows a datový obsah. Editor prostředků Visual C++ a knihovna MFC podporují pouze omezenou podmnožinu zpráv systému Windows: CB_ADDSTRING pro počáteční volby seznamu pro pole se seznamem (data jsou textový řetězec).

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
