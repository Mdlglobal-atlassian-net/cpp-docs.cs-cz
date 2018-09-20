---
title: 'MFC – ovládací prvky ActiveX: Vytvoření podtřídy ovládacího prvku Windows | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- precreatewindow
- IsSubclassed
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 94b989594316f2eac3e65fad2cb5bf419e7ee2eb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46407532"
---
# <a name="mfc-activex-controls-subclassing-a-windows-control"></a>MFC – ovládací prvky ActiveX: Vytvoření podtřídy ovládacího prvku systému Windows

Tento článek popisuje postup pro vytvoření podtřídy ovládacího prvku běžné Windows k vytvoření ovládacího prvku ActiveX. Existující Windows vytvoření podtřídy ovládacího prvku je rychlý způsob, jak vyvinout ovládací prvek ActiveX. Nový ovládací prvek bude mít na schopnosti rozčleněné ovládací prvek Windows, jako je vykreslování a reakce na kliknutí myší. Ukázka ovládací prvky MFC ActiveX [tlačítko](../visual-cpp-samples.md) je příklad vytvoření podtřídy ovládacího prvku Windows.

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být používána při novém vývoji. Další informace o moderních technologií, které nahrazují ActiveX naleznete v tématu [ovládací prvky ActiveX](activex-controls.md).

Pokud chcete podtřídy ovládacího prvku Windows proveďte následující úlohy:

- [Členské funkce IsSubclassedControl a PreCreateWindow COleControl – přepsat](#_core_overriding_issubclassedcontrol_and_precreatewindow)

- [Upravit OnDraw členská funkce](#_core_modifying_the_ondraw_member_function)

- [Zpracovat všechny ActiveX ovládacího prvku zprávy (OCM) odrazí na ovládacím prvku](#_core_handling_reflected_window_messages)

    > [!NOTE]
    >  Velká část této práce se provádí za vás Průvodce ovládacím prvkem ActiveX Pokud vyberete ovládací prvek má rozčlenit do podtříd pomocí **vyberte nadřazené třídu okna** rozevíracího seznamu na **nastavení** stránky.

Najdete v článku znalostní báze Q243454 Další informace o vytvoření podtřídy ovládacího prvku.

##  <a name="_core_overriding_issubclassedcontrol_and_precreatewindow"></a> Přepsání IsSubclassedControl a PreCreateWindow

K přepsání `PreCreateWindow` a `IsSubclassedControl`, přidejte následující řádky kódu, který **chráněné** části deklarace třídy ovládacího prvku:

[!code-cpp[NVC_MFC_AxSub#1](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_1.h)]

V souboru implementace ovládacího prvku (. CPP), přidejte následující řádky kódu implementovat dvě přepsaná funkce:

[!code-cpp[NVC_MFC_AxSub#2](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_2.cpp)]

Všimněte si, že v tomto příkladu Windows ovládacímu prvku tlačítko je zadán v `PreCreateWindow`. Však může být rozčlenění všechny standardní ovládací prvky Windows. Další informace o standardní ovládací prvky Windows najdete v tématu [ovládací prvky](../mfc/controls-mfc.md).

Při vytvoření podtřídy ovládacího prvku Windows, můžete zadat konkrétní okno Styl (WS_) nebo rozšířené okno příznaky styl (WS_EX_) který se má použít při vytváření okna ovládacího prvku. Můžete nastavit hodnoty těchto parametrů v `PreCreateWindow` členskou funkci tak, že upravíte `cs.style` a `cs.dwExStyle` struktury pole. By měl být provedeny změny těchto polí pomocí **nebo** operace, chcete-li zachovat výchozí příznaky, které jsou nastaveny podle třídy `COleControl`. Například pokud ovládací prvek je vytvoření podtřídy ovládacího prvku tlačítko a ovládací prvek se zobrazí jako zaškrtávací políčko, vložte následující řádek kódu do implementace `CSampleCtrl::PreCreateWindow`, před příkaz return:

[!code-cpp[NVC_MFC_AxSub#3](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_3.cpp)]

Tato operace přidá příznak stylu BS_CHECKBOX nechejte výchozí styl příznak (WS_CHILD) třídy `COleControl` beze změn.

##  <a name="_core_modifying_the_ondraw_member_function"></a> Úprava OnDraw členská funkce

Pokud chcete zachovat stejné vzhled jako odpovídající ovládací prvek Windows, váš ovládací prvek rozčleněný `OnDraw` členské funkce pro ovládací prvek by měl obsahovat pouze volání `DoSuperclassPaint` členská funkce, jako v následujícím příkladu:

[!code-cpp[NVC_MFC_AxSub#4](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_4.cpp)]

`DoSuperclassPaint` Členské funkce implementované `COleControl`, používá proceduru okna ovládacího prvku Windows nakreslete ovládací prvek v rámci zadané zařízení v rámci ohraničující obdélník. Díky tomu ovládací prvek viditelný i v případě, že není aktivní.

> [!NOTE]
>  `DoSuperclassPaint` Členská funkce, které budou fungovat jenom s typy ovládacích prvků, které umožňují kontextu zařízení mají být předány jako *wParam* WM_PAINT zprávy. To zahrnuje některé standardní ovládací prvky Windows, jako je například POSUVNÍK a tlačítko a všechny běžné ovládací prvky. Pro ovládací prvky, které nepodporují toto chování budete muset poskytnout vlastní kód pro správné zobrazení ovládacího prvku neaktivní.

##  <a name="_core_handling_reflected_window_messages"></a> Zpracování Reflektovaných zpráv oken

Ovládací prvky Windows obvykle odesílají některé okno zprávy do své nadřazené okno. Některé z následujících zpráv, jako je například wm_command –, poskytují oznámení o akci uživatele. Jiné, jako je například WM_CTLCOLOR –, se používají k získání informací z nadřazené okno. Ovládací prvek ActiveX je obvykle komunikuje s nadřazené okno jiným způsobem. Oznámení jsou předány podle vyvolává události (odesílání oznámení událostí), a informace o kontejneru ovládacího prvku se získá přístup k vedlejším vlastnostem kontejneru. Vzhledem k tomu, že existují tyto postupy komunikace nepředpokládá zpracovávat všechny zprávy okna zaslaná z ovládacího prvku ActiveX – kontejnery ovládacích prvků.

Aby se zabránilo kontejneru příjem okno zprávy odesílané rozčleněné ovládací prvek Windows, `COleControl` vytvoří okno navíc sloužit jako nadřazeného ovládacího prvku. Toto okno navíc nazývá "reflector", je vytvořen pouze pro ovládací prvek ActiveX, podtřídy Windows, řídit a má stejnou velikost a umístění jako okno ovládacího prvku. V okně reflector zachycuje některé zprávy okna a odešle zpět do ovládacího prvku. Ovládacího prvku, v jeho proceduru okna můžete následně zpracovat tyto reflektované zprávy provedením akce, které jsou vhodné pro ovládací prvek ActiveX (například aktivaci události). Zobrazit [projeví identifikátory zpráv oken](../mfc/reflected-window-message-ids.md) seznam windows zachycené zprávy a jejich odpovídající reflektovaných zpráv.

Kontejneru ovládacího prvku ActiveX mohou být určené k provádění reflexe zprávy, samostatně, což eliminuje potřebu `COleControl` k vytvoření okna reflector a zkrácení doby spuštění režie pro ovládací prvek rozčleněný Windows. `COleControl` zjistí, zda kontejner podporuje tuto funkci tak, že zkontrolujete vlastnost MessageReflect okolí s hodnotou **TRUE**.

Aby se zpracovala zpráva reflektovaný okna, přidejte záznam do mapování ovládacích prvků zprávu a implementovat funkci obslužné rutiny. Protože reflektované zprávy, které nejsou součástí standardní sadu zpráv, které jsou definované ve Windows, zobrazení tříd nepodporuje přidávání tyto obslužné rutiny zpráv. To však není obtížné ruční přidání obslužné rutiny.

Chcete-li přidat obslužné rutiny zpráv pro zprávu reflektovaný okna ručně takto:

- Ve třídě ovládacího prvku. Soubor H, deklarujte funkci obslužné rutiny. Funkce by měla mít typ vrácené hodnoty **LRESULT** a dva parametry s typy **WPARAM** a **LPARAM**v uvedeném pořadí. Příklad:

     [!code-cpp[NVC_MFC_AxSub#5](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_5.h)]
    [!code-cpp[NVC_MFC_AxSub#6](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_6.h)]

- Ve třídě ovládacího prvku. CPP soubor, přidejte záznam ON_MESSAGE v mapování zprávy. Parametry této položky by měl být identifikátor zprávy a název obslužné rutiny. Příklad:

     [!code-cpp[NVC_MFC_AxSub#7](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_7.cpp)]

- Také v. Soubor CPP implementovat `OnOcmCommand` členskou funkci ke zpracování reflektovaných zpráv. *WParam* a *lParam* parametry jsou stejné jako původní zprávy okna.

Pro příklad, jak projeví zpracování zpráv, najdete ukázky ovládacích prvků ActiveX knihovny MFC [tlačítko](../visual-cpp-samples.md). Ukazuje `OnOcmCommand` obslužná rutina, která kód upozornění BN_CLICKED detekuje hrozby a reaguje tak ohlásí (odesílání) `Click` událostí.

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)

