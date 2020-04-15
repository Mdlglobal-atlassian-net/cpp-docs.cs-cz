---
title: Implementace okna s CWindowImpl
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, windows
- windows [C++], subclassing
- windows [C++], superclassing
- windows [C++], ATL
- subclassing ATL window classes
- superclassing, ATL
ms.assetid: 3fc40550-f1d6-4702-8b7c-4cf682b6a855
ms.openlocfilehash: e5fdbf15ddd7edc69f0667a9b7e08c7c5e531a5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319453"
---
# <a name="implementing-a-window-with-cwindowimpl"></a>Implementace okna s CWindowImpl

Chcete-li implementovat okno, `CWindowImpl`odvodit třídu z . V odvozené třídě deklarujte mapu zpráv a funkce obslužné rutiny zprávy. Nyní můžete třídu používat třemi různými způsoby:

- [Vytvoření okna založeného na nové třídě systému Windows](#_atl_creating_a_window_based_on_a_new_windows_class)

- [Nadtřída existující třídy Windows](#_atl_superclassing_an_existing_windows_class)

- [Podtřídy existujícího okna](#_atl_subclassing_an_existing_window)

## <a name="creating-a-window-based-on-a-new-windows-class"></a><a name="_atl_creating_a_window_based_on_a_new_windows_class"></a>Vytvoření okna na základě nové třídy systému Windows

`CWindowImpl`obsahuje [DECLARE_WND_CLASS](reference/window-class-macros.md#declare_wnd_class) makro deklarovat informace o třídě systému Windows. Toto makro `GetWndClassInfo` implementuje funkci, která používá [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) k definování informací o nové třídě systému Windows. Při `CWindowImpl::Create` volání je tato třída systému Windows registrována a je vytvořeno nové okno.

> [!NOTE]
> `CWindowImpl`předá makru hodnotu `DECLARE_WND_CLASS` NULL, což znamená, že společnost ATL vygeneruje název třídy systému Windows. Chcete-li zadat vlastní název, předejte `CWindowImpl`řetězec DECLARE_WND_CLASS ve vaší odvozené třídě.

## <a name="example"></a>Příklad

Následuje příklad třídy, která implementuje okno založené na nové třídě systému Windows:

[!code-cpp[NVC_ATL_Windowing#64](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_1.h)]

Chcete-li vytvořit okno, `CMyWindow` vytvořte instanci a pak volání `Create` metody.

> [!NOTE]
> Chcete-li přepsat výchozí informace o `GetWndClassInfo` třídě systému Windows, `CWndClassInfo` implementujte metodu v odvozené třídě nastavením členů na příslušné hodnoty.

## <a name="superclassing-an-existing-windows-class"></a><a name="_atl_superclassing_an_existing_windows_class"></a>Nadřazení existující třídy Windows

DECLARE_WND_SUPERCLASS [DECLARE_WND_SUPERCLASS](reference/window-class-macros.md#declare_wnd_superclass) makro umožňuje vytvořit okno, které superclasses existující třídy systému Windows. Zadejte toto `CWindowImpl`makro v odvozené třídě. Stejně jako jakékoli jiné okno atl, zprávy jsou zpracovány mapy zpráv.

Při použití DECLARE_WND_SUPERCLASS bude registrována nová třída systému Windows. Tato nová třída bude stejná jako existující třída, kterou zadáte, ale nahradí proceduru okna `CWindowImpl::WindowProc` (nebo s vaší funkcí, která přepíše tuto metodu).

## <a name="example"></a>Příklad

Následuje příklad třídy, která přeřazuje standardní třídu Edit:

[!code-cpp[NVC_ATL_Windowing#65](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_2.h)]

Chcete-li vytvořit okno Úpravy se `CMyEdit` supertřídami, `Create` vytvořte instanci metody a pak ji zavolejte.

## <a name="subclassing-an-existing-window"></a><a name="_atl_subclassing_an_existing_window"></a>Podřazení existujícího okna

Chcete-li podtřídy existující okno, odvodit třídu z `CWindowImpl` a deklarovat mapu zprávy, jako ve dvou předchozích případech. Všimněte si však, že nezadáte žádné informace o třídě systému Windows, protože podtřídíte již existující okno.

Místo volání `Create`, `SubclassWindow` volání a předat popisovač do existujícího okna, které chcete podtřídy. Jakmile je okno podtřídy, `CWindowImpl::WindowProc` bude používat (nebo vaše funkce, která přepíše tuto metodu) přímé zprávy na mapu zpráv. Chcete-li odpojit okno podtřídy `UnsubclassWindow`od objektu, volejte . Původní postup okna okna bude poté obnoven.

## <a name="see-also"></a>Viz také

[Implementace okna](../atl/implementing-a-window.md)
