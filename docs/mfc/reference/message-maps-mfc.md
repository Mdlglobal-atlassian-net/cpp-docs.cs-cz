---
title: Mapy zpráv (MFC)
ms.date: 09/07/2019
helpviewer_keywords:
- message maps [MFC], MFC
- Windows messages [MFC], message maps
- messages [MFC], Windows
- MFC, messages
ms.assetid: 3f9855e4-9d7d-4b64-8f3f-a19ea3cf79ba
ms.openlocfilehash: 8080becf1a1a153322bfd03cbd7006eaf2ce4e13
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356577"
---
# <a name="message-maps-mfc"></a>Mapy zpráv (MFC)

V této části odkazu jsou uvedena všechna [makra mapování zpráv](../../mfc/reference/message-map-macros-mfc.md) a všechny položky mapy zpráv [CWnd](../../mfc/reference/cwnd-class.md) spolu s odpovídajícími prototypy členských funkcí:

|Kategorie|Popis|
|--------------|-----------------|
|Obslužná rutina zprávy PŘÍKAZ\_U PŘÍKAZU|Zpracovává `WM_COMMAND` zprávy generované výběry nabídek uživatele nebo přístupovými klávesami nabídky.|
|[Obslužné rutiny oznamovacích zpráv v podřízených oknech](../../mfc/reference/child-window-notification-message-handlers.md)|Zpracování oznámení z podřízených oken.|
|[obslužné rutiny zpráv WM_](../../mfc/reference/handlers-for-wm-messages.md)|Zpracování `WM_` zpráv, `WM_PAINT`například .|
|[Uživatelem definované obslužné rutiny zpráv](../../mfc/reference/user-defined-handlers.md)|Zpracování zpráv definovaných uživatelem.|

(Vysvětlení terminologie a konvencí použitých v tomto odkazu naleznete v [tématu Použití křížového odkazu na mapu zpráv](../../mfc/reference/how-to-use-the-message-map-cross-reference.md).)

Vzhledem k tomu, že systém Windows je operační systém orientovaný na zprávy, velká část programování pro prostředí systému Windows zahrnuje zpracování zpráv. Pokaždé, když dojde k události, jako je stisknutí klávesy nebo klepnutí myší, je do aplikace odeslána zpráva, která pak musí událost zpracovat.

Knihovna tříd Microsoft Foundation nabízí programovací model optimalizovaný pro programování založené na textech. V tomto modelu "mapy zpráv" se používají k určení, které funkce budou zpracovávat různé zprávy pro konkrétní třídu. Mapy zpráv obsahují jedno nebo více maker, které určují, které zprávy budou zpracovány pomocí kterých funkcí. Mapa zpráv obsahující `ON_COMMAND` makro může například vypadat přibližně takto:

[!code-cpp[NVC_MFCMessageMaps#16](../../mfc/reference/codesnippet/cpp/message-maps-mfc_1.cpp)]

Makro `ON_COMMAND` se používá ke zpracování zpráv příkazů generovaných nabídkami, tlačítky a klávesami akcelerátoru. [Makra](../../mfc/reference/message-map-macros-mfc.md) jsou k dispozici pro mapování následujících položek:

## <a name="windows-messages"></a>Zprávy systému Windows

- Kontrolní oznámení

- Uživatelem definované zprávy

## <a name="command-messages"></a>Zprávy příkazů

- Registrované uživatelem definované zprávy

- Aktualizační zprávy uživatelského rozhraní

## <a name="ranges-of-messages"></a>Rozsahy zpráv

- Příkazy

- Aktualizovat zprávy obslužné rutiny

- Kontrolní oznámení

Přestože makra mapy zpráv jsou důležitá, obvykle je nebudete muset používat přímo. Je to proto, [že Průvodce třídou](mfc-class-wizard.md) automaticky vytvoří položky mapy zpráv ve zdrojových souborech při přidružování funkcí zpracování zpráv se zprávami. Kdykoli budete chtít upravit nebo přidat položku mapy zpráv, můžete použít Průvodce třídou.

> [!NOTE]
> Průvodce třídou nepodporuje rozsahy map zpráv. Tyto položky mapy zpráv je nutné napsat sami.

Mapy zpráv jsou však důležitou součástí knihovny tříd microsoft foundation. Měli byste pochopit, co dělají, a dokumentace je k dispozici pro ně.

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)
