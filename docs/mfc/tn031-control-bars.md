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
ms.openlocfilehash: 37c3a15c281018260e65508dee3799ab0011dbfe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370309"
---
# <a name="tn031-control-bars"></a>TN031: Ovládací pruhy

> [!NOTE]
> Následující technická poznámka nebyla aktualizována od doby, kdy byla poprvé zahrnuta do online dokumentace. V důsledku toho mohou být některé postupy a témata zastaralé nebo nesprávné. Chcete-li získat nejnovější informace, doporučujeme vyhledat téma zájmu v online indexu dokumentace.

Tato poznámka popisuje třídy ovládacího panelu v knihovně MFC: obecné [CControlBar](#_mfcnotes_ccontrolbar), `CDockBar` [CStatusBar](#_mfcnotes_cstatusbar), [CToolBar](#_mfcnotes_ctoolbar), [CDialogBar](#_mfcnotes_cdialogbar)a .

## <a name="ccontrolbar"></a><a name="_mfcnotes_ccontrolbar"></a>Ovládací panel CControl

A `ControlBar` je `CWnd`odvozená třída, která:

- Je zarovnán k hornímu nebo dolnímu rohu okna rámce.

- Může obsahovat podřízené položky, které jsou `CDialogBar`buď ovládací`HWND` prvky založené na `CToolBar` `CStatusBar`HWND (například ) nebo nezaložené položky (například , ).

Ovládací panely podporují další styly:

- CBRS_TOP (Výchozí) připněte ovládací panel nahoru.

- CBRS_BOTTOM Připnout ovládací panel dolů.

- CBRS_NOALIGN Při změně velikosti nadřazeného panelu neměnte řídicí panel.

Třídy odvozené z `CControlBar` poskytují zajímavější implementace:

- `CStatusBar`Stavový řádek, položky jsou podokna stavového řádku obsahující text.

- `CToolBar`Panel nástrojů, položky jsou bitmapová tlačítka zarovnaná v řádku.

- `CDialogBar`Rámeček podobný panelu nástrojů obsahující standardní ovládací prvky systému Windows (vytvořený z prostředku šablony dialogu).

- `CDockBar`Zobecněná dokovací `CControlBar` oblast pro jiné odvozené objekty. Konkrétní členské funkce a proměnné, které jsou k dispozici v této třídě, se pravděpodobně změní v budoucích verzích.

Všechny objekty/okna ovládacího panelu budou podřízenými okny některého nadřazeného okna rámce. Obvykle jsou přidány jako na stejné úrovni do klientské oblasti rámce (například klienta MDI nebo zobrazení). ID podřízeného okna ovládacího panelu je důležité. Výchozí rozložení ovládacího panelu funguje pouze pro ovládací panely s ID v rozsahu AFX_IDW_CONTROLBAR_FIRST k AFX_IDW_CONTROLBAR_LAST. Všimněte si, že i když existuje rozsah 256 ID ovládacího panelu, prvních 32 těchto ID ovládacího panelu jsou zvláštní, protože jsou přímo podporovány architekturou náhledu tisku.

Třída `CControlBar` poskytuje standardní implementaci pro:

- Zarovnání ovládacího panelu k horní, dolní nebo obě strany rámečku.

- Přidělení polí položek ovládacího prvku.

- Podpora implementace odvozených tříd.

Objekty ovládacího panelu C++ budou `CFrameWnd` obvykle vloženy jako členové odvozené `HWND` třídy a budou vyčištěny, když jsou zničeny nadřazené objekty a objekt. Pokud potřebujete přidělit objekt ovládacího panelu na haldě, můžete jednoduše nastavit *m_bAutoDestruct* člen na `HWND` **HODNOTU TRUE,** aby ovládací panel **"odstranit "** při zničení.

> [!NOTE]
> Pokud vytvoříte `CControlBar`vlastní odvozené třídy, nikoli pomocí jedné z odvozených `CStatusBar`tříd `CToolBar`knihovny MFC, například , nebo `CDialogBar`, budete muset nastavit *m_dwStyle* datový člen. To lze provést v přepsání `Create`:

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

**Algoritmus rozložení ovládacího panelu**

Algoritmus rozložení ovládacího panelu je velmi jednoduchý. Okno rámce odešle zprávu WM_SIZEPARENT všem dětem v rozsahu ovládacího panelu. Spolu s touto zprávou je předán ukazatel na obdélník klienta nadřazené. Tato zpráva je odeslána dětem v pořadí vykreslovací. Podřízené ovládací panely používají tyto informace k umístění sebe a ke zmenšení velikosti nadřazené klientské oblasti. Konečný obdélník, který je ponechán pro normální klientskou oblast (méně ovládacích panelů) se používá k umístění hlavního okna klienta (obvykle klienta MDI, zobrazení nebo rozdělovač okna).

Viz `CWnd::RepositionBars` `CFrameWnd::RecalcLayout` a další podrobnosti.

Soukromé zprávy systému Windows knihovny MFC, včetně WM_SIZEPARENT, jsou popsány v [technické poznámce 24](../mfc/tn024-mfc-defined-messages-and-resources.md).

## <a name="cstatusbar"></a><a name="_mfcnotes_cstatusbar"></a>Stavový panel C

Stavový řádek je ovládací panel, který má řádek oken výstupu textu. Existují dva běžné způsoby použití podoken výstupu textu:

- Jako řádek zprávy

     (například standardní řádek nápovědy nabídky). Ty jsou obvykle přístupné indexovaným indexovaným

- Jako indikátory stavu

     (například indikátory Cap, NUM a SCRL). Ty jsou obvykle přístupné pomocí ID řetězce/příkazu.

Písmo stavového řádku je 10bodové MS Sans Serif (podle příručky pro návrh aplikace rozhraní systému Windows nebo mapovačů písem, které nejlépe odpovídají 10bodovému švýcarskému proporcionálnímu písmu). V některých verzích systému Windows, například v japonské edici, se vybraná písma liší.

Barvy použité ve stavovém řádku jsou také konzistentní s doporučením Průvodce návrhem aplikace rozhraní systému Windows. Tyto barvy nejsou pevně zakódovány a dynamicky se mění v reakci na přizpůsobení uživatele v Ovládacích panelech.

|Položka|Hodnota Windows COLOR|Výchozí RGB|
|----------|-------------------------|-----------------|
|Pozadí stavového řádku|COLOR_BTNFACE|RGB(192, 192, 192)|
|Text stavového řádku|COLOR_BTNTEXT|RGB(000, 000, 000)|
|Stavový řádek horní/levé hrany|COLOR_BTNHIGHLIGHT|RGB(255, 255, 255)|
|Stavový řádek bot/pravé hrany|COLOR_BTNSHADOW|RGB(128, 128, 128)|

**Podpora CCmdUI pro CStatusBar**

Způsob, jakým jsou ukazatele obvykle aktualizovány, je prostřednictvím mechanismu ON_UPDATE_COMMAND_UI. V době nečinnosti bude stavový řádek volat obslužnou rutinu ON_UPDATE_COMMAND_UI s ID řetězce podokna indikátorů.

Obslužná rutina ON_UPDATE_COMMAND_UI může volat:

- `Enable`: Povolení nebo zakázání podokna. Zakázané podokno vypadá přesně jako povolené podokno, ale text je neviditelný (to znamená, že vypne indikátor textu).

- `SetText`: Změna textu. Pokud tuto možnost použijete, buďte opatrní, protože velikost podokna se automaticky nezmění.

Podrobnosti o rozhraních `CStatusBar` API pro vytváření a přizpůsobení naleznete v části [CStatusBar](../mfc/reference/cstatusbar-class.md) třídy v odkazu na *knihovnu tříd.* Většina přizpůsobení stavových pruhů by měla být provedena před tím, než je stavový řádek zpočátku viditelný.

Stavový řádek podporuje pouze jedno pružné podokno, obvykle první podokno. Velikost tohoto podokna je opravdu minimální velikost. Pokud je stavový řádek větší než minimální velikost všech podoken, bude rejnokového podokna přidělena další šířka. Výchozí aplikace se stavovým panelem má ukazatele zarovnané doprava pro CAP, NUM a SCRL, protože první podokno je pružné.

## <a name="ctoolbar"></a><a name="_mfcnotes_ctoolbar"></a>Ctoolbar

Panel nástrojů je ovládací panel s řadou bitmapových tlačítek, která mohou obsahovat oddělovače. Podporovány jsou dva styly tlačítek: tlačítka a zaškrtávací políčka. Funkce skupiny rádií lze sestavit pomocí zaškrtávacích tlačítek a ON_UPDATE_COMMAND_UI.

Všechna bitmapová tlačítka v pruhu nástrojů jsou převzata z jedné bitmapy. Tato bitmapa musí obsahovat jeden obraz nebo glyf pro každé tlačítko. Obvykle je pořadí obrazů/glyfů v bitmapě stejné pořadí, ve kterém budou vykresleny na obrazovce. (To lze změnit pomocí rozhraní API pro přizpůsobení.)

Každé tlačítko musí mít stejnou velikost. Výchozí hodnota je standardní obrazové body o rozměrech 24 x 22. Každý obrázek/glyf musí mít stejnou velikost a musí být v bitmapě vedle sebe. Výchozí velikost obrázku/glyfu je 16 x 15 pixelů. Proto pro panel nástrojů s 10 tlačítky (pomocí standardních velikostí) potřebujete bitmapu, která je široká 160 pixelů a vysoká 15 pixelů.

Každé tlačítko má jeden a pouze jeden obrázek/glyf. Různé stavy a styly tlačítek (například stisknuté, nahoru, dolů, zakázané, zakázané dolů, neurčité) jsou algoritmicky generovány z tohoto jednoho obrázku/glyfu. Teoreticky lze použít libovolnou barevnou bitmapu nebo DIB. Algoritmus pro generování různých stavů tlačítek funguje nejlépe, pokud je původní obraz odstíny šedé. Podívejte se na standardní tlačítka panelu nástrojů a klipart tlačítka panelu nástrojů, který je uveden v příkladech ukázkový [klipart](../overview/visual-cpp-samples.md) Knihovny MFC.

Barvy použité na panelu nástrojů jsou také konzistentní s doporučením Průvodce návrhem aplikace rozhraní systému Windows. Tyto barvy nejsou pevně zakódovány a dynamicky se mění v reakci na přizpůsobení uživatele v Ovládacích panelech.

|Položka|Hodnota Windows COLOR|Výchozí RGB|
|----------|-------------------------|-----------------|
|Pozadí panelu nástrojů|COLOR_BTNFACE|RGB (192 192 192)|
|Tlačítka panelu nástrojů horní/levé okraje|COLOR_BTNHIGHLIGHT|RGB (255 255 255)|
|Tlačítka panelu nástrojů bot/pravé hrany|COLOR_BTNSHADOW|RGB (128 128 128)|

Kromě toho jsou bitmapová tlačítka panelu nástrojů přebarvena, jako by se jednalo o standardní ovládací prvky tlačítek systému Windows. K tomuto přebarvení dochází, když je bitmapa načtena z prostředku a v reakci na změnu systémových barev v reakci na přizpůsobení uživatele v Ovládacích panelech. Následující barvy v bitmapě panelu nástrojů budou automaticky přebarveny, takže by měly být používány opatrně. Pokud si nepřejete, aby část rastrového mapy byla přebarvena, použijte barvu, která se těsně blíží jedné z mapovaných hodnot RGB. Mapování se provádí na základě přesných hodnot RGB.

|Hodnota RGB|Dynamicky mapovaná hodnota COLOR|
|---------------|------------------------------------|
|RGB(000, 000, 000)|COLOR_BTNTEXT|
|RGB(128, 128, 128)|COLOR_BTNSHADOW|
|RGB(192, 192, 192)|COLOR_BTNFACE|
|RGB(255, 255, 255)|COLOR_BTNHIGHLIGHT|

Podrobnosti o rozhraních API pro vytváření `CToolBar` a přizpůsobení naleznete v části [CToolBar](../mfc/reference/ctoolbar-class.md) v odkazu na *knihovnu tříd.* Většina přizpůsobení panelů nástrojů by měla být provedena před tím, než je panel nástrojů zpočátku viditelný.

Rozhraní API pro přizpůsobení lze použít k úpravě ID tlačítek, stylů, šířky rozpěrky a toho, který obrázek/glyf se používá pro jaké tlačítko. Ve výchozím nastavení není nutné používat tato api.

## <a name="ccmdui-support-for-ctoolbar"></a>Podpora CCmdUI pro CToolBar

Způsob, jakým jsou tlačítka panelu nástrojů vždy aktualizována, je prostřednictvím mechanismu ON_UPDATE_COMMAND_UI. V době nečinnosti bude panel nástrojů volat obslužnou rutinu ON_UPDATE_COMMAND_UI s ID příkazu tohoto tlačítka. ON_UPDATE_COMMAND_UI se nenazývá pro oddělovače, ale je volána pro tlačítka a zaškrtávací políčka.

Obslužná rutina ON_UPDATE_COMMAND_UI může volat:

- `Enable`: Chcete-li tlačítko povolit nebo zakázat. To funguje stejně pro tlačítka a zaškrtávací políčka tlačítka.

- `SetCheck`: Nastavení stavu kontroly tlačítka. Volání maže pro tlačítko panelu nástrojů se změní na zaškrtávací políčko tlačítko. `SetCheck`má parametr, který může být 0 (není zaškrtnuto), 1 (zaškrtnuto) nebo 2 (neurčitý)

- `SetRadio`: Zkratka `SetCheck`pro .

Zaškrtávací políčka tlačítka jsou "AUTO" zaškrtávací políčka tlačítka; to znamená, že když je uživatel stiskne, okamžitě změní stav. Zaškrtnuto je stav dolů nebo v depresi. Neexistuje žádný vestavěný způsob uživatelského rozhraní, který by změnil tlačítko do "neurčitého" stavu. které musí být provedeny prostřednictvím kódu.

Rozhraní API pro vlastní nastavení vám umožní změnit stav daného tlačítka panelu nástrojů, nejlépe byste měli změnit tyto stavy v obslužné rutině ON_UPDATE_COMMAND_UI pro příkaz, který představuje tlačítko panelu nástrojů. Nezapomeňte, že nečinné zpracování změní stav tlačítek panelu nástrojů s obslužnou rutinou ON_UPDATE_COMMAND_UI, takže všechny změny těchto stavů provedené prostřednictvím SetButtonStyle se mohou po dalším nečinnosti ztratit.

Tlačítka panelu nástrojů budou odesílat WM_COMMAND zprávy, jako jsou normální tlačítka nebo položky nabídky, a obvykle je zpracovává obslužná rutina ON_COMMAND ve stejné třídě, která poskytuje obslužnou rutinu ON_UPDATE_COMMAND_UI.

Pro stavy zobrazení se používají čtyři styly tlačítek panelu nástrojů (TBBS_ hodnoty):

- TBBS_CHECKED: Zaškrtávací políčko je aktuálně zaškrtnuto (dolů).

- TBBS_INDETERMINATE: Zaškrtávací políčko je momentálně neurčité.

- TBBS_DISABLED: Tlačítko je momentálně zakázáno.

- TBBS_PRESSED: Tlačítko je právě stisknuto.

Šest oficiálních stylů tlačítek Průvodce návrhem aplikace rozhraní systému Windows je reprezentováno následujícími hodnotami TBBS:

- Nahoru = 0

- Mouse Down = TBBS_PRESSED (&#124; jakýkoli jiný styl)

- Zakázáno = TBBS_DISABLED

- Dolů = TBBS_CHECKED

- Vypnuto down = TBBS_CHECKED &#124; &#124; TBBS_DISABLED

- Neurčitý = TBBS_INDETERMINATE

## <a name="cdialogbar"></a><a name="_mfcnotes_cdialogbar"></a>Panel CDialog

Dialogové okno je ovládací panel, který obsahuje standardní ovládací prvky systému Windows. Funguje jako dialog v tom, že obsahuje ovládací prvky a podporuje tabulátory mezi nimi. Funguje také jako dialog v tom, že používá šablonu dialogu k reprezentaci pruhu.

A `CDialogBar` se používá pro panel nástrojů náhledu tisku, který obsahuje standardní ovládací prvky tlačítek.

Použití `CDialogBar` je jako `CFormView`použití . Pro dialogový pruh je nutné definovat šablonu dialogového okna a odebrat všechny styly kromě WS_CHILD. Všimněte si, že dialogové okno nesmí být viditelné.

Ovládací upozornění pro `CDialogBar` a budou odeslána nadřazené ovládacího panelu (stejně jako tlačítka panelu nástrojů).

## <a name="ccmdui-support-for-cdialogbar"></a>Podpora CCmdUI pro CDialogBar

Tlačítka dialogového panelu by měla být aktualizována prostřednictvím mechanismu obslužné rutiny ON_UPDATE_COMMAND_UI. V době nečinnosti bude dialogový panel volat obslužnou rutinu ON_UPDATE_COMMAND_UI s ID příkazu všech tlačítek, která mají ID >= 0x8000 (tj. v rozsahu ID příkazu).

Obslužná rutina ON_UPDATE_COMMAND_UI může volat:

- Povolit: chcete-li tlačítko povolit nebo zakázat.

- SetText: chcete-li změnit text tlačítka.

Vlastní nastavení lze provést prostřednictvím standardních rozhraní API správce oken.

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
