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
ms.openlocfilehash: 686d5eef4aaa67785aa56133d820b637fbf4bb86
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364758"
---
# <a name="message-categories"></a>Kategorie zpráv

Jaké druhy zpráv píšete obslužné rutiny pro Existují tři hlavní kategorie:

1. zprávy Windows

   To zahrnuje především ty zprávy začínající **předponou WM_,** s výjimkou WM_COMMAND. Zprávy systému Windows jsou zpracovávány okny a zobrazeními. Tyto zprávy mají často parametry, které se používají při určování, jak zpracovat zprávu.

1. Kontrolní oznámení

   To zahrnuje WM_COMMAND oznámení z ovládacích prvků a dalších podřízených oken do nadřazených oken. Ovládací prvek pro úpravy například odešle nadřazenému ovládacímu prvku zprávu WM_COMMAND obsahující kód oznámení ovládacího prvku EN_CHANGE, když uživatel provedl akci, která mohla změnit text v ovládacím prvku pro úpravy. Obslužná rutina okna pro zprávu reaguje na zprávu odpovídajícím způsobem, jako je například načítání textu v ovládacím prvku.

   Rozhraní framework směruje zprávy s oznámením ovládacího prvku jako ostatní **WM_** zprávy. Jednou výjimkou je však BN_CLICKED zpráva o znacích ovládacího prvku odeslaná tlačítky, když na ně uživatel klepne. Tato zpráva je považována speciálně jako příkazová zpráva a směrována jako ostatní příkazy.

1. Příkazové zprávy

   To zahrnuje WM_COMMAND oznámení z objektů uživatelského rozhraní: nabídky, tlačítka panelu nástrojů a klávesy akcelerátoru. Rozhraní framework zpracovává příkazy odlišně od jiných zpráv a mohou být zpracovány více druhy objektů, jak je vysvětleno v [command targets](../mfc/command-targets.md).

## <a name="windows-messages-and-control-notification-messages"></a><a name="_core_windows_messages_and_control.2d.notification_messages"></a>Zprávy systému Windows a zprávy o oznamování ovládacího prvku

Zprávy v kategoriích 1 a 2 – Zprávy systému Windows a oznámení `CWnd`o řízení – jsou zpracovávány okny: objekty tříd odvozených z třídy . To `CFrameWnd`zahrnuje `CMDIFrameWnd` `CMDIChildWnd`, `CView` `CDialog`, , , a vlastní třídy odvozené z těchto základních tříd. Tyto objekty zapouzdřují `HWND`popisovač do okna systému Windows.

## <a name="command-messages"></a><a name="_core_command_messages"></a>Zprávy příkazů

Zprávy v kategorii 3 – příkazy – mohou být zpracovány širší škálou objektů: dokumenty, šablony dokumentů a samotný objekt aplikace kromě oken a zobrazení. Pokud příkaz přímo ovlivňuje určitý objekt, má smysl, aby tento objekt zpracovat příkaz. Například příkaz Otevřít v nabídce Soubor je logicky přidružen k aplikaci: aplikace otevře po přijetí příkazu zadaný dokument. Takže obslužná rutina příkazu Open je členskou funkcí třídy aplikace. Další informace o příkazy a jak jsou směrovány do objektů, naleznete [v tématu Jak framework volá obslužnou rutinu](../mfc/how-the-framework-calls-a-handler.md).

## <a name="see-also"></a>Viz také

[Zprávy a příkazy v prostředí .NET Framework](../mfc/messages-and-commands-in-the-framework.md)
