---
title: Implementace okna pomocí CWindowImpl
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, windows
- windows [C++], subclassing
- windows [C++], superclassing
- windows [C++], ATL
- subclassing ATL window classes
- superclassing, ATL
ms.assetid: 3fc40550-f1d6-4702-8b7c-4cf682b6a855
ms.openlocfilehash: 265c3145d8ceacae540286f72939dc046e7c8b35
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818073"
---
# <a name="implementing-a-window-with-cwindowimpl"></a>Implementace okna pomocí CWindowImpl

Implementace okna, odvoďte třídu z `CWindowImpl`. V odvozené třídě deklarujte mapy zpráv a funkcí obslužných rutin zpráv. Teď můžete použít třídu třemi různými způsoby:

- [Vytvoření okna založené na novou třídu s Windows](#_atl_creating_a_window_based_on_a_new_windows_class)

- [Nadřazené třídu existující Windows](#_atl_superclassing_an_existing_windows_class)

- [Podtřídy existujícímu oknu.](#_atl_subclassing_an_existing_window)

##  <a name="_atl_creating_a_window_based_on_a_new_windows_class"></a> Vytvoření okna založené na novou třídu s Windows

`CWindowImpl` obsahuje [DECLARE_WND_CLASS](reference/window-class-macros.md#declare_wnd_class) – makro, chcete-li deklarovat informace o třídě Windows. Implementuje toto makro `GetWndClassInfo` funkci, která používá [cwndclassinfo –](../atl/reference/cwndclassinfo-class.md) zadat informace novou třídu s Windows. Když `CWindowImpl::Create` nazývá tento Windows třída je registrována. a vytvoří se nové okno.

> [!NOTE]
>  `CWindowImpl` předá hodnotu NULL na `DECLARE_WND_CLASS` – makro, což znamená, že knihovny ATL bude generovat název třídy Windows. Chcete-li zadat vlastní název, předejte řetězec DECLARE_WND_CLASS v vaše `CWindowImpl`-odvozené třídy.

## <a name="example"></a>Příklad

Následuje příklad třídy, která implementuje okno založené na nové třídě Windows:

[!code-cpp[NVC_ATL_Windowing#64](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_1.h)]

Vytvoření časového období, vytvořit instanci `CMyWindow` a následně zavolat `Create` metoda.

> [!NOTE]
>  Chcete-li přepsat výchozí třída informace o Windows, implementovat `GetWndClassInfo` metoda v odvozené třídy tak, že nastavíte `CWndClassInfo` členy do příslušné hodnoty.

##  <a name="_atl_superclassing_an_existing_windows_class"></a> Superclassing existující třídu Windows

[DECLARE_WND_SUPERCLASS](reference/window-class-macros.md#declare_wnd_superclass) – makro vám umožní vytvořit okno této nadřazené třídy existující Windows třídy. Zadejte toto makro v vaše `CWindowImpl`-odvozené třídy. Stejně jako ostatní okna ATL zprávy zpracovává mapu zpráv.

Při použití DECLARE_WND_SUPERCLASS novou třídu s Windows se zaregistruje. Tato nová třída bude stejná jako existující třídy, ale nahradí proceduru okna s `CWindowImpl::WindowProc` (nebo funkci, která přepíše tuto metodu).

## <a name="example"></a>Příklad

Následující je příkladem třídu této nadřazené třídy standardní upravit třídy:

[!code-cpp[NVC_ATL_Windowing#65](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_2.h)]

K vytvoření okna supertřídu upravit, vytvoření instance `CMyEdit` a následně zavolat `Create` metody.

##  <a name="_atl_subclassing_an_existing_window"></a> Vytvoření podtřídy existujícímu oknu.

K podtřídou existujícímu oknu, odvoďte třídu z `CWindowImpl` a deklarovat mapy zpráv, jako v předchozích dvou případů. Všimněte si však, že nezadáte žádné informace o třídě Windows, protože se již existujícímu oknu. podtřídy.

Namísto volání metody `Create`, volání `SubclassWindow` a předejte jej do existujícího okna chcete podtřídy popisovač. Jakmile podtřídou třídy okna, se bude používat `CWindowImpl::WindowProc` (nebo funkci, která přepíše tuto metodu) ke směrování zpráv v mapování zprávy. Chcete-li odpojit rozčleněných do podtříd okna z objektu, volejte `UnsubclassWindow`. Původní proceduru okna v okně se pak obnoví.

## <a name="see-also"></a>Viz také:

[Implementace okna](../atl/implementing-a-window.md)
