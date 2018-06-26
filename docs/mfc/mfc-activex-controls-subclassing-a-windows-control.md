---
title: 'Ovládací prvky MFC ActiveX: Vytvoření podtřídy ovládacího prvku Windows | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: e44366927cf5d17b5ec5edeebafb396b4e3f1b28
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929702"
---
# <a name="mfc-activex-controls-subclassing-a-windows-control"></a>MFC – ovládací prvky ActiveX: Vytvoření podtřídy ovládacího prvku systému Windows
Tento článek popisuje proces pro vytvoření podtřídy ovládacího prvku Windows běžné k vytvoření ovládacího prvku ActiveX. Vytvoření podtřídy existující Windows řízení je rychlý způsob, jak vyvíjet ovládacího prvku ActiveX. Nový ovládací prvek bude mít schopnosti rozčleněné ovládací prvek Windows, jako je například vykreslování a reagovat na kliknutí myší. Ukázka ovládací prvky MFC ActiveX [tlačítko](../visual-cpp-samples.md) je příklad vytvoření podtřídy ovládacího prvku systému Windows.  
  
 Chcete podtřídy ovládacího prvku Windows proveďte následující úlohy:  
  
-   [Přepsat IsSubclassedControl a PreCreateWindow – členské funkce COleControl](#_core_overriding_issubclassedcontrol_and_precreatewindow)  
  
-   [Upravit OnDraw – členská funkce](#_core_modifying_the_ondraw_member_function)  
  
-   [Zpracovat všechny ActiveX řízení zprávy (OCM) projeví do ovládacího prvku](#_core_handling_reflected_window_messages)  
  
    > [!NOTE]
    >  Velkou část těchto úkolů se provádí pro vás Průvodce ovládacím prvkem ActiveX Pokud vyberete řízení být rozčlenění pomocí **vyberte nadřazené okno třídy** v rozevíracím seznamu **nastavení řízení** stránky.  
  
 O vytvoření podtřídy ovládacího prvku najdete v článku znalostní báze Q243454 Další informace.  
  
##  <a name="_core_overriding_issubclassedcontrol_and_precreatewindow"></a> Přepsání IsSubclassedControl a PreCreateWindow –  
 K přepsání `PreCreateWindow` a `IsSubclassedControl`, přidejte následující řádky kódu **chráněné** části deklarace třídy ovládacího prvku:  
  
 [!code-cpp[NVC_MFC_AxSub#1](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_1.h)]  
  
 V řídicím souboru implementace (. CPP), přidejte následující řádky kódu implementovat dvě přepsané funkce:  
  
 [!code-cpp[NVC_MFC_AxSub#2](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_2.cpp)]  
  
 Všimněte si, že v tomto příkladu tlačítko okna pro ovládací prvek je uveden v `PreCreateWindow`. Však může být rozčlenění všechny standardní ovládací prvky systému Windows. Další informace o standardní ovládací prvky Windows najdete v tématu [ovládací prvky](../mfc/controls-mfc.md).  
  
 Při vytvoření podtřídy ovládacího prvku systému Windows, můžete zadat konkrétní okno Styl (WS_) nebo rozšířené okno příznaky styl (WS_EX_) pro použití při vytváření okna ovládacího prvku. Můžete nastavit hodnoty pro tyto parametry v `PreCreateWindow` – členská funkce změnou `cs.style` a `cs.dwExStyle` struktury pole. Změny těchto polí je třeba pomocí **nebo** operace, pokud chcete zachovat výchozí příznaky, které jsou nastaveny podle třídy `COleControl`. Například pokud ovládací prvek je vytvoření podtřídy ovládacího prvku TLAČÍTKA a chcete zobrazit jako zaškrtávací políčko, vložte následující kód do implementace `CSampleCtrl::PreCreateWindow`, před příkaz return:  
  
 [!code-cpp[NVC_MFC_AxSub#3](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_3.cpp)]  
  
 Tato operace přidá příznak bs_checkbox – styl a nechat výchozí styl příznak (ws_child –) třídy `COleControl` beze změn.  
  
##  <a name="_core_modifying_the_ondraw_member_function"></a> Úprava OnDraw – členská funkce  
 Pokud chcete, aby vaše rozčleněné ovládací prvek chcete zachovat stejné vzhled jako odpovídající ovládacího prvku Windows, `OnDraw` členské funkce ovládacího prvku by měl obsahovat jenom volání `DoSuperclassPaint` – členská funkce, jako v následujícím příkladu:  
  
 [!code-cpp[NVC_MFC_AxSub#4](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_4.cpp)]  
  
 `DoSuperclassPaint` – Členská funkce, implementované `COleControl`, používá k vykreslení ovládacího prvku v rámci zadané zařízení v rámci ohraničující obdélník proceduru okno ovládacího prvku systému Windows. Díky tomu ovládacího prvku viditelné i v případě, že není aktivní.  
  
> [!NOTE]
>  `DoSuperclassPaint` – Členská funkce budou fungovat jenom s typy těchto ovládacích prvků, které umožňují kontextu zařízení mají být předány jako *wParam* WM_PAINT zprávy. To zahrnuje některé standardní ovládací prvky systému Windows, jako je například POSUVNÍK a tlačítko a všechny běžné ovládací prvky. Pro ovládací prvky, které nepodporují toto chování budete muset zadat vlastní kód pro správné zobrazení ovládacího prvku neaktivní.  
  
##  <a name="_core_handling_reflected_window_messages"></a> Zpracování Reflektovaných zpráv oken  
 Ovládací prvky Windows obvykle odesílají některé okno zprávy do své nadřazené okno. Některé z těchto zpráv, jako je například wm_command –, poskytují oznámení akce uživatelem. Jiné, jako je například WM_CTLCOLOR –, se používají k získání informací od nadřazeného okna. Ovládací prvek ActiveX obvykle komunikuje s nadřazeného okna jiným způsobem. Oznámení se předávají pomocí aktivaci událostí (odesílání oznámení událostí) a informace o kontejneru ovládací prvek byl získán přístup k vedlejším vlastnostem kontejneru. Protože tyto komunikace techniky, – kontejnery ovládacích prvků ActiveX neočekává zpracovat žádné okno zprávy odeslané ovládacího prvku.  
  
 Aby se zabránilo kontejneru příjem zprávy okna odeslané rozčleněné ovládací prvek Windows, `COleControl` vytvoří okno navíc sloužit jako nadřazeného ovládacího prvku. Toto okno navíc názvem "reflector", se vytvoří pouze pro ovládací prvek ActiveX, podtřídy Windows řízení a má stejnou velikost a umístění jako okně řízení. Okno reflector zachycuje některé zprávy okna a odešle je zpět do ovládacího prvku. Ovládací prvek v postupu její okno, pak může zpracovat tyto reflektované zprávy provedením akcí, které jsou vhodné pro ovládací prvek ActiveX (například aktivuje událost). V tématu [identifikátory Reflektovaných zpráv oken](../mfc/reflected-window-message-ids.md) seznam zachycené windows zpráv a jejich odpovídajících reflektovaných zpráv.  
  
 Kontejneru ovládacího prvku ActiveX může být navržena k provedení reflexe zpráv, sebe, což eliminuje potřebu `COleControl` vytvořit okno reflector a snižuje běhu režie pro rozčleněné ovládací prvek Windows. `COleControl` zjistí, zda kontejner podporuje tato funkce kontrolou MessageReflect vedlejším vlastnosti s hodnotou **TRUE**.  
  
 Zpracování zpráv reflektované oken, přidat položku do mapy zpráv řízení a implementovat funkci obslužné rutiny. Protože reflektované zprávy není součástí standardní sadu zpráv, které jsou definované v systému Windows, zobrazení tříd nepodporuje přidávání takové obslužné rutiny zpráv. Však není obtížné ručně přidejte obslužnou rutinu.  
  
 Přidání obslužné rutiny zpráv reflektované okno zprávy ručně postupujte takto:  
  
-   Ve třídě ovládacího prvku. Soubor H deklarovat funkci obslužné rutiny. Funkce návratový typ měli **LRESULT** a dva parametry s typy **WPARAM** a **LPARAM**, v uvedeném pořadí. Příklad:  
  
     [!code-cpp[NVC_MFC_AxSub#5](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_5.h)]  
    [!code-cpp[NVC_MFC_AxSub#6](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_6.h)]  
  
-   Ve třídě ovládacího prvku. CPP soubor, přidejte on_message – záznam do mapy zpráv. Parametry tato položka musí být identifikátor zprávy a název obslužné rutiny. Příklad:  
  
     [!code-cpp[NVC_MFC_AxSub#7](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_7.cpp)]  
  
-   Také v. Soubor CPP implementovat `OnOcmCommand` – členská funkce zpracovat zrcadlené zprávy. *WParam* a *lParam* parametry jsou stejné jako původní okno zprávy.  
  
 Příklad projeví zpracování zpráv, naleznete ukázce ovládací prvky MFC ActiveX [tlačítko](../visual-cpp-samples.md). Ukazuje `OnOcmCommand` obslužná rutina, která zjistí kód BN_CLICKED oznámení a reaguje ohlásí (odesílajícím) `Click` událostí.  
  
## <a name="see-also"></a>Viz také  
 [MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)

