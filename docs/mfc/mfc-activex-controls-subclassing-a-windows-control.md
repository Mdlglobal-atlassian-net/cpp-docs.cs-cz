---
title: 'MFC – ovládací prvky ActiveX: Vytvoření podtřídy ovládacího prvku systému Windows'
ms.date: 09/12/2018
f1_keywords:
- precreatewindow
- IsSubclassed
helpviewer_keywords:
- OnDraw method, MFC ActiveX controls
- subclassing
- DoSuperclassPaint method [MFC]
- subclassing Windows controls
- subclassing, Windows controls
- reflected messages, in ActiveX controls
- PreCreateWindow method, overriding
- MFC ActiveX controls [MFC], subclassed controls
- MFC ActiveX controls [MFC], creating
- IsSubclassed method [MFC]
ms.assetid: 3236d4de-401f-49b7-918d-c84559ecc426
ms.openlocfilehash: ccebbad22be92b84fa2fd84434f788484d332cce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376001"
---
# <a name="mfc-activex-controls-subclassing-a-windows-control"></a>MFC – ovládací prvky ActiveX: Vytvoření podtřídy ovládacího prvku systému Windows

Tento článek popisuje proces podřazení společného ovládacího prvku systému Windows k vytvoření ovládacího prvku ActiveX. Podřazení existujícího ovládacího prvku systému Windows je rychlý způsob, jak vyvinout ovládací prvek ActiveX. Nový ovládací prvek bude mít schopnosti podtřídy ovládacího prvku systému Windows, jako je například malování a reakce na kliknutí myší. [Tlačítko](../overview/visual-cpp-samples.md) ukázky ovládacích prvků ActiveX knihovny MFC je příkladem podřadného nastavení ovládacího prvku systému Windows.

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být použita pro nový vývoj. Další informace o moderních technologiích, které nahrazují ovládací prvky ActiveX, naleznete [v tématu ActiveX Controls](activex-controls.md).

Chcete-li podtřídovat ovládací prvek systému Windows, proveďte následující úkoly:

- [Přepsat členské funkce IsSubclassedControl a PreCreateWindow cOleControl](#_core_overriding_issubclassedcontrol_and_precreatewindow)

- [Změna členské funkce OnDraw](#_core_modifying_the_ondraw_member_function)

- [Zpracování všech zpráv ovládacího prvku ActiveX (OCM), které se projeví v ovládacím prvku](#_core_handling_reflected_window_messages)

   > [!NOTE]
   > Velká část této práce se provádí za vás Průvodcem ovládacím prvkem ActiveX, pokud vyberete ovládací prvek, který má být podtřídou pomocí rozevíracího seznamu **Vybrat nadřazenou třídu okna** na stránce **Nastavení ovládacího prvku.**

## <a name="overriding-issubclassedcontrol-and-precreatewindow"></a><a name="_core_overriding_issubclassedcontrol_and_precreatewindow"></a>Přepsání IsSubclassedControl a PreCreateWindow

Chcete-li `PreCreateWindow` `IsSubclassedControl`přepsat a , přidejte následující řádky kódu do **chráněné** části deklarace třídy ovládacího prvku:

[!code-cpp[NVC_MFC_AxSub#1](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_1.h)]

V souboru implementace ovládacího prvku (. CPP), přidejte následující řádky kódu k implementaci dvou potlačených funkcí:

[!code-cpp[NVC_MFC_AxSub#2](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_2.cpp)]

Všimněte si, že v tomto příkladu `PreCreateWindow`je ovládací prvek tlačítka systému Windows určen v aplikaci . Všechny standardní ovládací prvky systému Windows však mohou být podtřídy. Další informace o standardních ovládacích prvcích systému Windows naleznete v [tématu Controls](../mfc/controls-mfc.md).

Při podřadné třídě ovládacího prvku systému Windows můžete chtít zadat konkrétní styl okna (WS_) nebo příznaky rozšířeného stylu okna (WS_EX_), které se mají použít při vytváření okna ovládacího prvku. Hodnoty těchto parametrů můžete nastavit `PreCreateWindow` v členské funkci `cs.style` úpravou `cs.dwExStyle` polí a struktura. Změny těchto polí by měly být provedeny pomocí operace **OR,** aby `COleControl`se zachovaly výchozí příznaky, které jsou nastaveny třídou . Například pokud ovládací prvek je podtřídy button ovládacího prvku a chcete, aby ovládací prvek se `CSampleCtrl::PreCreateWindow`zobrazí jako zaškrtávací políčko, vložte následující řádek kódu do implementace , před příkaz return:

[!code-cpp[NVC_MFC_AxSub#3](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_3.cpp)]

Tato operace přidá příznak stylu BS_CHECKBOX, přičemž výchozí příznak `COleControl` stylu (WS_CHILD) třídy zůstane beze změny.

## <a name="modifying-the-ondraw-member-function"></a><a name="_core_modifying_the_ondraw_member_function"></a>Úprava členské funkce OnDraw

Pokud chcete, aby ovládací prvek podtřídy zachovat stejný vzhled `OnDraw` jako odpovídající ovládací prvek systému `DoSuperclassPaint` Windows, členská funkce pro ovládací prvek by měla obsahovat pouze volání členské funkce, jako v následujícím příkladu:

[!code-cpp[NVC_MFC_AxSub#4](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_4.cpp)]

Členská `DoSuperclassPaint` funkce implementovaná aplikací `COleControl`, používá proceduru okna ovládacího prvku systému Windows k nakreslení ovládacího prvku v kontextu zadaného zařízení v rámci ohraničovacího obdélníku. Díky ovládacímu prvku viditelné i v případě, že není aktivní.

> [!NOTE]
> Členská `DoSuperclassPaint` funkce bude pracovat pouze s těmi typy ovládacích prvku, které umožňují kontext zařízení, které mají být předány jako *wParam* zprávy WM_PAINT. To zahrnuje některé standardní ovládací prvky systému Windows, například SCROLLBAR a BUTTON a všechny běžné ovládací prvky. Pro ovládací prvky, které nepodporují toto chování, budete muset zadat vlastní kód správně zobrazit neaktivní ovládací prvek.

## <a name="handling-reflected-window-messages"></a><a name="_core_handling_reflected_window_messages"></a>Zpracování zpráv odraženého okna

Ovládací prvky systému Windows obvykle odesílají určité zprávy okna do nadřazeného okna. Některé z těchto zpráv, například WM_COMMAND, poskytují oznámení o akci uživatele. Jiné, například WM_CTLCOLOR, se používají k získání informací z nadřazeného okna. Ovládací prvek ActiveX obvykle komunikuje s nadřazeným oknem jinými prostředky. Oznámení jsou sdělovány spouštění událostí (odesílání oznámení událostí) a informace o kontejneru ovládacího prvku se získá přístup k vlastnostem okolí kontejneru. Vzhledem k tomu, že tyto komunikační techniky existují, neočekává se, že kontejnery ovládacího prvku ActiveX budou zpracovávat všechny zprávy okna odeslané ovládacím prvkem.

Chcete-li zabránit kontejneru přijímat zprávy okna odeslané `COleControl` podtřídou ovládacího prvku systému Windows, vytvoří další okno sloužit jako nadřazený ovládacíprvek. Toto další okno, nazývané "reflektor", je vytvořeno pouze pro ovládací prvek ActiveX, který podřizuje ovládací prvek systému Windows a má stejnou velikost a umístění jako ovládací okno. Okno reflektoru zachytí určité zprávy okna a odešle je zpět do ovládacího prvku. Ovládací prvek v jeho okno postup pak můžete zpracovat tyto odražené zprávy tím, že akce vhodné pro ovládací prvek ActiveX (například spuštění události). Seznam zachycených zpráv systému Windows a odpovídajících odražených zpráv naleznete v [tématu ID zpráv s odraženým oknem.](../mfc/reflected-window-message-ids.md)

Kontejner ovládacího prvku ActiveX může být navržen tak, `COleControl` aby prováděl samotný odraz zpráv, což eliminuje potřebu vytvořit okno reflektoru a snižuje režii za běhu pro ovládací prvek systému Windows s podtřídou. `COleControl`zjistí, zda kontejner podporuje tuto schopnost kontrolou vlastnosti ambient MessageReflect s hodnotou **TRUE**.

Chcete-li zpracovat zprávu s odraženým oknem, přidejte položku na mapu řídicí zprávy a implementujte funkci obslužné rutiny. Vzhledem k tomu, že odražené zprávy nejsou součástí standardní sady zpráv definovaných systémem Windows, zobrazení tříd nepodporuje přidání těchto obslužných rutin zpráv. Však není obtížné přidat obslužnou rutinu ručně.

Chcete-li přidat obslužnou rutinu zprávy pro zprávu s odraženým oknem ručně, postupujte takto:

- V kontrolní třídě . H, deklarujte funkci obslužné rutiny. Funkce by měla mít návratový typ **LRESULT** a dva parametry s typy **WPARAM** a **LPARAM**, resp. Příklad:

   [!code-cpp[NVC_MFC_AxSub#5](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_5.h)]
    [!code-cpp[NVC_MFC_AxSub#6](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_6.h)]

- V kontrolní třídě . cpp, přidejte položku ON_MESSAGE do mapy zpráv. Parametry této položky by měly být identifikátor zprávy a název funkce obslužné rutiny. Příklad:

   [!code-cpp[NVC_MFC_AxSub#7](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_7.cpp)]

- Také v . CPP, implementujte `OnOcmCommand` členní funkci ke zpracování odražené zprávy. Parametry *wParam* a *lParam* jsou stejné jako u původní zprávy okna.

Příklad zpracování odražených zpráv naleznete v části Ovládací prvek ActiveX knihovny MFC [– ukázkový panel BUTTON](../overview/visual-cpp-samples.md). Ukazuje obslužnou rutinu, `OnOcmCommand` která detekuje BN_CLICKED kódu oznámení `Click` a reaguje spuštěním (odesláním) události.

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)
