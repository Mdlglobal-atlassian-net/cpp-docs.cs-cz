---
title: Objekty oken
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], window
- Windows window [MFC]
- MFC, windows
- frame windows [MFC], C++ window objects
- window objects [MFC]
- windows [MFC], C++ window objects
- window messages [MFC]
- HWND
- messages [MFC], Windows
- Visual C++, window objects [MFC]
- HWND, window objects [MFC]
ms.assetid: 28b33ce2-af05-4617-9d03-1cb9a02be687
ms.openlocfilehash: b62f43aa0d37c5e614636b3d7543bc927d41039b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57299865"
---
# <a name="window-objects"></a>Objekty oken

Knihovna MFC poskytuje třídy [CWnd](../mfc/reference/cwnd-class.md) k zapouzdření `HWND` popisovač okna. `CWnd` Objekt je objekt jazyka C++ okna, liší od `HWND` Windows, která představuje okno, ale který ji obsahuje. Použít `CWnd` odvozovat vlastní podřízené okno třídy, nebo použijte některou z mnoha třídy MFC odvozené od `CWnd`. Třída `CWnd` je základní třída pro všechna okna, včetně oken s rámečkem v dialogových oknech, podřízená okna, ovládací prvky a ovládací pruhy, jako je například panely nástrojů. Dobrý přehled o [vztah mezi objektem okna v C++ a popisovačem HWND](../mfc/relationship-between-a-cpp-window-object-and-an-hwnd.md) je zásadní pro efektivní programování s knihovnou MFC.

Knihovna MFC poskytuje některé výchozí funkce a správa systému windows, ale lze odvodit vlastní třídu z `CWnd` a použít její členské funkce k přizpůsobení zadaná funkce. Můžete vytvořit podřízenou windows tak, že vytváří `CWnd` objektu a volání jeho [vytvořit](../mfc/reference/cwnd-class.md#create) členské funkce, pak můžete přizpůsobit podřízených oken pomocí `CWnd` členské funkce. Můžete vložit objekty odvozené z [CView](../mfc/reference/cview-class.md), jako je například zobrazení formuláře nebo zobrazení stromové struktury, v okně s rámečkem. A může podporovat více zobrazení dokumentů prostřednictvím rozdělovač podokna, získáte ho od třídy [CSplitterWnd](../mfc/reference/csplitterwnd-class.md).

Každý objekt odvozený od třídy `CWnd` obsahuje mapy zpráv, pomocí kterého můžete mapování zpráv Windows nebo ID příkazu pro svoje vlastní obslužné rutiny.

Obecná dokumentace na programování pro Windows je vhodným místem k zadání učit, jak používat `CWnd` členské funkce, které zapouzdřují `HWND` rozhraní API.

## <a name="functions-for-operating-on-a-cwnd"></a>Funkce pro provozování na třídy CWnd

`CWnd` a jeho [odvozené třídy oken](../mfc/derived-window-classes.md) poskytuje konstruktory, destruktory a členské funkce k inicializaci objektu, vytvořte základní struktury Windows a přístup k zapouzdřený objekt `HWND`. `CWnd` také poskytuje členské funkce, které provádí zapouzdření rozhraní Windows API pro odesílání zpráv, přístup ke stavu okna, převod souřadnic, aktualizace a posouvání, přístup k schránky a spoustu dalších úkolů. Většina Windows okno – rozhraní API pro správu, které využívají `HWND` jako členské funkce jsou zapouzdřeny argument `CWnd`. Názvy funkcí a jejich parametrů jsou zachovány v `CWnd` členskou funkci. Další informace o rozhraní API Windows zapouzdřena objektem `CWnd`, naleznete v tématu třídy [CWnd](../mfc/reference/cwnd-class.md).

## <a name="cwnd-and-windows-messages"></a>CWnd a zpráv Windows

Jedním z primárních účelů `CWnd` je poskytnout rozhraní pro zpracování zpráv Windows, jako je například WM_PAINT nebo wm_mousemove a. Mnoho členské funkce `CWnd` jsou obslužné rutiny pro standardní zprávy – těch, které začínají identifikátorem **afx_msg** a předpony "U", jako například `OnPaint` a `OnMouseMove`. [Zpracování a mapování zpráv](../mfc/message-handling-and-mapping.md) obsahuje zprávy a zpracování zpráv v podrobností. Tyto informace platí pro windows rozhraní framework a ty vytvoříte sami pro zvláštní účely.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Vztah mezi objektem okna v C++ a popisovačem HWND](../mfc/relationship-between-a-cpp-window-object-and-an-hwnd.md)

- [Odvozené třídy oken](../mfc/derived-window-classes.md)

- [Vytváření oken](../mfc/creating-windows.md)

- [Zničení objektů oken](../mfc/destroying-window-objects.md)

- [Odpojení třídy CWnd od jejího prvku HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)

- [Práce s objekty oken](../mfc/working-with-window-objects.md)

- [Kontexty zařízení](../mfc/device-contexts.md): objekty, které usnadňují nezávislé kreslení zařízení Windows

- [Grafické objekty](../mfc/graphic-objects.md): pera, štětce, písma, rastrové obrázky, palety, oblastí

## <a name="see-also"></a>Viz také:

[Windows](../mfc/windows.md)
