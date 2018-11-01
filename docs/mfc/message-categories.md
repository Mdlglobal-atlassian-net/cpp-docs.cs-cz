---
title: Kategorie zpráv
ms.date: 11/04/2016
helpviewer_keywords:
- messages [MFC], categories
- control-notification messages [MFC]
- Windows messages [MFC], categories
- controls [MFC], notifications
- command messages [MFC]
- messages [MFC], Windows
- message handling [MFC], message types
ms.assetid: 68e1db75-9da6-4a4d-b2c2-dc4d59f8d87b
ms.openlocfilehash: e8b7385a233c2074fe9bfc491d89de7629c730c0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50619853"
---
# <a name="message-categories"></a>Kategorie zpráv

Jaké typy zpráv, které při zápisu obslužných rutin pro existují tři hlavní kategorie:

1. zprávy Windows

   Jedná se především zpráv, počínaje **WM_** předponu, s výjimkou wm_command –. Zprávy Windows provádí služba systému windows a zobrazení. Tyto zprávy mají často parametry, které se používají při určování, jak zpracovat zprávy.

1. Oznámení ovládacího prvku

   To zahrnuje wm_command – zprávy oznámení z ovládacích prvků a jiných podřízených oken do své nadřazené windows. Například ovládací prvek úprav odešle svého nadřazeného objektu wm_command – zprávy obsahující kód EN_CHANGE oznámení ovládacího prvku, když uživatel má provést akce, která mohou být ovlivněny textu v textovém poli. V okně obslužné rutiny pro zprávy jsou reaguje na zprávy oznámení některé vhodným způsobem, jako je například načítání textu v ovládacím prvku.

   Rozhraní framework směruje zprávy s oznámením ovládacího prvku jako jiné **WM_** zprávy. Jedinou výjimkou je však BN_CLICKED oznámení ovládacího prvku zprávy odeslané tlačítka, když uživatel klikne, je. Tato zpráva je speciálně jako zprávou příkazu zpracovány a směrovat stejně jako ostatní příkazy.

1. Zprávy příkazů

   Jedná se o wm_command – zprávy oznámení z objektů uživatelského rozhraní: nabídek, tlačítek panelu nástrojů a přístupové klávesy. Rozhraní framework zpracovává příkazy jinak než ostatní zprávy a je možné je zpracovávat pomocí další typy objektů, jak je vysvětleno v [cíle příkazů](../mfc/command-targets.md).

##  <a name="_core_windows_messages_and_control.2d.notification_messages"></a> Zprávy Windows a zprávy s oznámením ovládacího prvku

Zprávy do kategorií, 1 a 2 – Windows zprávy a oznámení ovládacích prvků – provádí služba systému windows: objekty třídy odvozené od třídy `CWnd`. Jedná se o `CFrameWnd`, `CMDIFrameWnd`, `CMDIChildWnd`, `CView`, `CDialog`, a vlastní třídy odvozené z těchto základních tříd. Tyto objekty zapouzdřují `HWND`, popisovač okna Windows.

##  <a name="_core_command_messages"></a> Zprávy příkazů

Zprávy v kategorii 3 – příkazy – mohou být zpracovány širší objektů: dokumenty, šablony dokumentů a objekt aplikace kromě systému windows a zobrazení. Příkaz přímo ovlivní Některé konkrétní objekt, je vhodné, aby tento objekt zpracování příkazu. Například otevřete příkaz v nabídce Soubor je logicky spojený s aplikací: aplikace se otevře zadaný dokument při přijetí příkazu. Proto je obslužnou rutinu pro příkaz Otevřít členské funkce třídy aplikace. Další informace o příkazech a jak se směrují do objektů naleznete v tématu [jakým způsobem volá Framework obslužnou rutinu](../mfc/how-the-framework-calls-a-handler.md).

## <a name="see-also"></a>Viz také

[Zprávy a příkazy v prostředí .NET Framework](../mfc/messages-and-commands-in-the-framework.md)

