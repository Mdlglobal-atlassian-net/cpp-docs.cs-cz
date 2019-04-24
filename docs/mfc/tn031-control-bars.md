---
title: 'TN031: Ovládací pruhy'
ms.date: 11/04/2016
f1_keywords:
- vc.controls.bars
helpviewer_keywords:
- control bars [MFC], styles
- CStatusBar class [MFC], Tech Note 31 usage
- CControlBar class [MFC], Tech Note 31 usage
- CControlBar class [MFC], deriving from
- control bars [MFC], classes [MFC]
- CDialogBar class [MFC], Tech Note 31 usage
- CToolBar class [MFC], Tech Note 31 usage
- TN031
- styles [MFC], control bars
ms.assetid: 8cb895c0-40ea-40ef-90ee-1dd29f34cfd1
ms.openlocfilehash: 39309408c6d1fc6cbb4223eda22c511865f14498
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62305630"
---
# <a name="tn031-control-bars"></a>TN031: Ovládací pruhy

> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována, protože byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata mohou být nesprávné nebo zastaralé. Nejnovější informace se doporučuje vyhledat téma zájmu v dokumentaci online index.

Tato poznámka popisuje třídy panel ovládacích prvků v knihovně MFC: Obecné [ccontrolbar –](#_mfcnotes_ccontrolbar), [cstatusbar –](#_mfcnotes_cstatusbar), [ctoolbar –](#_mfcnotes_ctoolbar), [CDialogBar](#_mfcnotes_cdialogbar)a `CDockBar`.

## <a name="_mfcnotes_ccontrolbar"></a> Ccontrolbar –

A `ControlBar` je `CWnd`-odvozené třídy, které:

- Je umístěno na horní nebo dolní části okna rámce.

- Může obsahovat podřízené položky, které jsou buď řízení na základě HWND (například `CDialogBar`) nebo jiných-`HWND` podle položky (například `CToolBar`, `CStatusBar`).

Ovládací pruhy podporují další styly:

- PIN kód CBRS_TOP (výchozí) na panelu ovládacího prvku do horní části.

- PIN kód CBRS_BOTTOM panelu ovládacího prvku do dolní části.

- Proveďte CBRS_NOALIGN není přemístit ovládací panel, když změní velikost nadřazené.

Třídy odvozené z `CControlBar` poskytují zajímavější implementace:

- `CStatusBar` Stavový řádek položky jsou podokna stavu panel obsahující text.

- `CToolBar` Panel nástrojů, jsou položky rastrového obrázku tlačítka v řádku.

- `CDialogBar` Rámeček panelu nástrojů jako s windows na úrovni standard ovládací prvky (vytvořené z prostředku šablony dialogového okna).

- `CDockBar` Zobecněný oblasti ukotvení dalších `CControlBar` odvozené objekty. Zvláštní členské funkce a proměnné, které jsou k dispozici v této třídě jsou pravděpodobně v budoucích verzích změnit.

Všechny ovládací prvek panelu objekty/windows bude podřízená okna některé nadřazené okno rámce. Obvykle jsou přidány na stejné úrovni jako klientskou oblast rámce (například klienta MDI nebo zobrazení). Identifikátor podřízené okno Ovládací panel je důležité. Výchozí rozložení ovládacího panelu funguje jenom pro ovládacích panelů s ID v rozsahu AFX_IDW_CONTROLBAR_FIRST k AFX_IDW_CONTROLBAR_LAST. Všimněte si, že i když existuje velká škála 256 ovládacího panelu ID, první 32 tyto ovládací panel identifikátory jsou speciální od přímo podporuje architektura náhledu tisku.

`CControlBar` Třída poskytuje standardní implementace pro:

- Zarovnání panel ovládacího prvku na horní, dolní nebo obou stranách rámce.

- Přidělování ovládací prvek položky pole.

- Podporuje implementaci odvozené třídy.

Objekty panelu ovládacího prvku jazyka C++ bude vložen obvykle jako členy `CFrameWnd` odvozené třídy a kdy se vyčistí nadřazené `HWND` a objekt, jsou zničeny. Pokud je potřeba přidělit objekt panelu ovládacího prvku na haldě, stačí nastavit *m_bAutoDestruct* člen **TRUE** aby ovládacím panelu "**odstranit tento**" při `HWND` zničen.

> [!NOTE]
>  Pokud vytvoříte vlastní `CControlBar`-odvozené třídy, nikoli pomocí jedné z knihovny MFC odvozené třídy, jako například `CStatusBar`, `CToolBar`, nebo `CDialogBar`, budete muset nastavit *m_dwStyle* datový člen. To můžete udělat v přepsání z `Create`:

```
// CMyControlBar is derived from CControlBar
BOOL CMyControlBar::Create(CWnd* pParentWnd,
    DWORD dwStyle,
    UINT nID)
{
    m_dwStyle = dwStyle;

.
.
.
}
```

**Algoritmus ovládací panel rozložení**

Algoritmus ovládací prvek panel rozložení je velmi snadné. Okno rámce odešle zprávu WM_SIZEPARENT na všechny podřízené položky v oblasti panelu ovládacího prvku. Spolu se tato zpráva je předán ukazatel na klientský obdélník nadřazeného objektu. Tato zpráva se pošle na podřízené položky v pořadí vykreslování. Tyto informace použít podřízené položky Ovládacích panelů umístit sami a snížení velikosti nadřazeného objektu klientské oblasti. Poslední obdélník, který je ponecháno normální klientské oblasti (méně ovládací pruhy) se používá k umístění okna hlavní klient (obvykle klienta, zobrazení nebo rozdělovač okna MDI).

Zobrazit `CWnd::RepositionBars` a `CFrameWnd::RecalcLayout` další podrobnosti.

MFC privátní Windows zprávy, včetně WM_SIZEPARENT, jsou popsány v [Technická poznámka 24](../mfc/tn024-mfc-defined-messages-and-resources.md).

## <a name="_mfcnotes_cstatusbar"></a>  CStatusBar

Stavový řádek je ovládací panel, který má na řádku podoken textového výstupu. Existují dva běžné způsoby použití podoken textového výstupu:

- Jako řádek zprávy

     (například standardní nabídky Nápověda řádek zprávy). Tyto jsou obvykle přistupuje na 0 založený indexovat

- Jako indikátory stavu

     (například Zakončení, počet a SCRL ukazatele). Ty jsou obvykle přístupné pomocí ID řetězce nebo příkaz.

Písmo stavový řádek je 10 bodů MS alternativními názvy subjektu Serif (závisí Průvodce návrhem aplikace rozhraní Windows nebo písmo mapovačů nejlepší shodu švýcarský proporcionální písma 10 bodů). V některých verzích Windows, jako je například japonská verze se liší písma vybrali.

Barvy použité ve stavovém řádku jsou také v souladu s doporučením Průvodce návrhem aplikace rozhraní Windows. Tyto barvy nejsou pevně zakódované a se dynamicky mění v reakci na vlastní uživatelské nastavení v Ovládacích panelech.

|Položka|Hodnota barvy Windows|Výchozí RGB|
|----------|-------------------------|-----------------|
|Stav pozadí panelu|COLOR_BTNFACE|RGB(192, 192, 192)|
|Text stavového řádku|COLOR_BTNTEXT|RGB(000, 000, 000)|
|Stavový řádek levého nebo horního okraje|COLOR_BTNHIGHLIGHT|RGB(255, 255, 255)|
|Stavový řádek bot/pravé hrany|COLOR_BTNSHADOW|RGB(128, 128, 128)|

**Ccmdui – podpora pro cstatusbar –**

Způsob, jakým jsou obvykle aktualizovány ukazatele je mechanismem ON_UPDATE_COMMAND_UI. Na určitou dobu nečinné zavolá stavový řádek ON_UPDATE_COMMAND_UI obslužná rutina s ID řetězce podokna indikátoru.

Můžete volat ON_UPDATE_COMMAND_UI obslužné rutiny:

- `Enable`: K povolení nebo zakázání podokna. Zakázané panel vypadá stejně jako Povolené podokno, ale text je neviditelné (to znamená, vypne indikátoru text).

- `SetText`: Chcete-li změnit text. Buďte opatrní, pokud to použít, protože v podokně se mění svou velikost automaticky.

Odkazovat na třídu [cstatusbar –](../mfc/reference/cstatusbar-class.md) v *knihovny tříd* podrobnosti o `CStatusBar` tvorbu a přizpůsobení rozhraní API. Většina přizpůsobení stavových řádků se má počítat dřív, než stavový řádek je zpočátku viditelné.

Stavový řádek podporuje pouze jedno podokno pružně roztáhnout, obvykle první podokno. Velikost tohoto podokna je ve skutečnosti minimální velikost. Pokud stavový řádek je větší než minimální velikost všech podoken, dostanou všechny dodatečnou šířku pružně roztáhnout podokna. Výchozí aplikace se stavový řádek má zarovnaný doprava ukazatele pro Zakončení, počet a SCRL, protože je první podokno pružně roztáhnout.

## <a name="_mfcnotes_ctoolbar"></a>  Ctoolbar –

Panel nástrojů se ovládací panel s řádkem rastrového obrázku tlačítka, který může obsahovat oddělovače. Jsou podporovány dvě styly tlačítek: tlačítek a zaškrtávacího políčka tlačítka. Přepínač funkce skupiny se dají vytvářet pomocí tlačítka zaškrtávací políčko a ON_UPDATE_COMMAND_UI.

Všechna rastrového obrázku tlačítka na panelu nástrojů pocházejí z jednoho rastrového obrázku. Tento rastrový obrázek musí obsahovat jednu image nebo glyfů pro každé tlačítko. Pořadí Image/glyfy rastrového obrázku nastaven je obvykle stejné pořadí, ve kterém bude nutné vykreslit na obrazovce. (Toto můžete změnit pomocí vlastního nastavení rozhraní API.)

Každé tlačítko musí mít stejnou velikost. Výchozí hodnota je standardní 24 × 22 pixelů. Každá image/piktogramu musí mít stejnou velikost a musí být vedle sebe v rastrového obrázku. Výchozí velikost image/piktogram je 16 × 15 pixelů. Proto pro panel nástrojů s 10 tlačítka (pomocí standardní velikosti), je nutné rastrový obrázek, který je 160 pixelů na šířku a 15 pixelů na výšku.

Každé tlačítko má jeden a pouze jeden image/glyfů. Jiné tlačítko stavy a styly (třeba, stisknutí snižování kapacity, zakázat, zakázané dolů, neurčitý) algorithmically generují z jedné image/piktogram. Teoreticky lze použít libovolné barvy rastrového obrázku nebo DIB. Algoritmus pro generování jiné tlačítko stavy funguje nejlíp odstíny šedé při původní bitové kopie. Podívejte se na standardním panelu nástrojů tlačítka a klipart tlačítko panelu nástrojů k dispozici v ukázce MFC Obecné [klipart](../overview/visual-cpp-samples.md) příklady.

Barvy používané v panelu nástrojů jsou také v souladu s doporučením Průvodce návrhem aplikace rozhraní Windows. Tyto barvy nejsou pevně zakódované a se dynamicky mění v reakci na vlastní uživatelské nastavení v Ovládacích panelech.

|Položka|Hodnota barvy Windows|Výchozí RGB|
|----------|-------------------------|-----------------|
|Pozadí panelu nástrojů|COLOR_BTNFACE|RGB(192,192,192)|
|Levého nebo horního okraje tlačítka na panelu nástrojů|COLOR_BTNHIGHLIGHT|RGB(255,255,255)|
|Bot/pravé hrany tlačítka na panelu nástrojů|COLOR_BTNSHADOW|RGB(128,128,128)|

Rastrového obrázku tlačítka panelu nástrojů jsou také obarveny, jako by byly standardní ovládací prvky tlačítka Windows. Tato přebarvení vyvolá se v případě rastrového obrázku je načten z prostředku a v reakci na změnu v systémové barvy v reakci na vlastní uživatelské nastavení v Ovládacích panelech. Tyto barvy rastrového obrázku panelu nástrojů se automaticky obarveny, takže by měl třeba používat opatrně. Pokud nechcete, aby k mít část vaší rastrový obrázek obarveny, použijte barva, která přibližuje jeden z namapované hodnoty RGB. Mapování se provádí v závislosti na přesné hodnoty RGB.

|Hodnota RGB|Dynamicky mapované hodnoty barev|
|---------------|------------------------------------|
|RGB(000, 000, 000)|COLOR_BTNTEXT|
|RGB(128, 128, 128)|COLOR_BTNSHADOW|
|RGB(192, 192, 192)|COLOR_BTNFACE|
|RGB(255, 255, 255)|COLOR_BTNHIGHLIGHT|

Odkazovat na třídu [ctoolbar –](../mfc/reference/ctoolbar-class.md) *knihovny tříd* podrobnosti o `CToolBar` tvorbu a přizpůsobení rozhraní API. Většina přizpůsobení panelů nástrojů má počítat dřív, než panelu nástrojů je zpočátku viditelné.

Přizpůsobení rozhraní API je možné upravit tlačítko ID, styly, šířka oddělovací a které obrázek nebo glyfů se používá pro tlačítka, které. Ve výchozím nastavení není potřeba pomocí těchto rozhraní API.

## <a name="ccmdui-support-for-ctoolbar"></a>Ccmdui – podpora pro ctoolbar –

Pomocí mechanismu ON_UPDATE_COMMAND_UI je způsob, jakým jsou vždy aktualizovat tlačítka na panelu nástrojů. Panelu nástrojů na určitou dobu nečinné, zavolá ON_UPDATE_COMMAND_UI obslužná rutina s Identifikátorem příkazu toto tlačítko. ON_UPDATE_COMMAND_UI není volána pro oddělovače, ale je volána pro tlačítek a zaškrtávacího políčka tlačítka.

Můžete volat ON_UPDATE_COMMAND_UI obslužné rutiny:

- `Enable`: K povolení nebo zakázání tlačítka. Funguje to stejně tlačítek a zaškrtávacího políčka tlačítka.

- `SetCheck`: K nastavení stavu zaškrtnutí tlačítka. Toto volání pro tlačítka panelu nástrojů, se změní na tlačítko zaškrtávacího políčka. `SetCheck` přijímá parametr, který může být 0 (není zaškrtnuté), 1 (čtverečkovaný) nebo 2 (neurčitý)

- `SetRadio`: Zkrácený tvar vlastností `SetCheck`.

Zaškrtněte políčko tlačítka jsou tlačítka, zaškrtávací políčko "AUTO"; To znamená když uživatel stiskne, je jejich okamžitě změní stav. Zaškrtnutí je mimo provoz nebo stisknuté stav. Neexistuje žádný způsob předdefinované uživatelské rozhraní změnit tlačítko do stavu "neurčitý"; který se musí provést prostřednictvím kódu.

Přizpůsobení rozhraní API vám umožní změnit stav daného tlačítka, ideálně byste měli změnit tyto stavy v obslužné rutině ON_UPDATE_COMMAND_UI pro příkaz, který představuje tlačítko panelu nástrojů. Nezapomeňte, že zpracování při nečinnosti se změní stav tlačítka na panelu nástrojů s popisovačem ON_UPDATE_COMMAND_UI tak všechny změny na tyto stavy provedená prostřednictvím SetButtonStyle může ztratit po další nečinnosti.

Tlačítka panelu nástrojů pošle wm_command – zprávy jako normální tlačítka nebo nabídka položek a jsou obvykle zpracovávány obslužnou rutinu ON_COMMAND ve stejné třídě, která poskytuje obslužné rutiny ON_UPDATE_COMMAND_UI.

Existují čtyři nástrojů styly tlačítek (TBBS_ hodnoty) používá pro zobrazení stavů:

- TBBS_CHECKED:   Aktuálně je zaškrtnuté políčko (dolů).

- TBBS_INDETERMINATE:   Zaškrtávací políčko je aktuálně neurčitý.

- TBBS_DISABLED:   Tlačítko je aktuálně zakázaný.

- TBBS_PRESSED:   Aktuálně se stiskne tlačítko.

Šest oficiální styly tlačítek Průvodce návrhem aplikace rozhraní Windows jsou reprezentovány TBBS následující hodnoty:

- Up = 0

- Myši dolů = TBBS_PRESSED (&#124; jakýkoli styl)

- Zakázané = TBBS_DISABLED

- Dolů = TBBS_CHECKED

- Dolů zakázáno = TBBS_CHECKED &#124; TBBS_DISABLED

- Neurčitá = TBBS_INDETERMINATE

##  <a name="_mfcnotes_cdialogbar"></a> CDialogBar

Panel dialogového okna se ovládací panel, který obsahuje standardní ovládací prvky Windows. Funguje stejně jako dialogové okno obsahuje ovládací prvky a podporuje tabulátor mezi nimi. Taky funguje jako dialogové okno, používá k reprezentaci panelu šablony dialogového okna.

A `CDialogBar` slouží k náhledu nástrojů, který obsahuje standardní kontrolní prvky stisknutelných.

Pomocí `CDialogBar` se například `CFormView`. Musí definovat šablony dialogového okna pro panel dialogového okna a odeberte všechny styly, s výjimkou WS_CHILD. Všimněte si, že dialogového okna nesmí být viditelné.

Oznámení ovládacího prvku pro `CDialogBar` se pošle na nadřazený ovládací prvek panel (stejně jako tlačítka na panelu nástrojů).

## <a name="ccmdui-support-for-cdialogbar"></a>Ccmdui – podpora pro CDialogBar

Dialogové okno tlačítek se musí aktualizovat prostřednictvím mechanismu ON_UPDATE_COMMAND_UI obslužné rutiny. Na určitou dobu nečinné, panel dialogového okna zavolá obslužnou rutinu ON_UPDATE_COMMAND_UI s Identifikátorem příkazu všechna tlačítka, které máte ID > = 0x8000 (to znamená, v rozsahu ID příkazů).

Můžete volat ON_UPDATE_COMMAND_UI obslužné rutiny:

- Povolit: k povolení nebo zakázání tlačítka.

- SetText –: Chcete-li změnit text na tlačítku.

Přizpůsobení lze provést pomocí standardní okno Správce rozhraní API.

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
