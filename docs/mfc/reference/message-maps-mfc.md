---
title: Mapy zpráv (MFC)
ms.date: 09/07/2019
helpviewer_keywords:
- message maps [MFC], MFC
- Windows messages [MFC], message maps
- messages [MFC], Windows
- MFC, messages
ms.assetid: 3f9855e4-9d7d-4b64-8f3f-a19ea3cf79ba
ms.openlocfilehash: 4305d9b1db297eebcb189d2fad98b8c634ed1133
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908044"
---
# <a name="message-maps-mfc"></a>Mapy zpráv (MFC)

V této části najdete seznam všech [maker s mapováním zpráv](../../mfc/reference/message-map-macros-mfc.md) a všechny položky mapování zpráv [CWnd](../../mfc/reference/cwnd-class.md) spolu s odpovídajícími prototypy členských funkcí:

|Kategorie|Popis|
|--------------|-----------------|
|Obslužná rutina zprávy příkazu\_|Zpracovává `WM_COMMAND` zprávy vygenerované výběry nabídky uživatele nebo přístupové klíče nabídky.|
|[Obslužné rutiny oznamovacích zpráv v podřízených oknech](../../mfc/reference/child-window-notification-message-handlers.md)|Zpracování zpráv s oznámením z podřízených oken.|
|[Obslužné rutiny zpráv WM_](../../mfc/reference/handlers-for-wm-messages.md)|Zpracování `WM_` zpráv, jako je `WM_PAINT`například.|
|[Obslužné rutiny zpráv definované uživatelem](../../mfc/reference/user-defined-handlers.md)|Zpracování zpráv definovaných uživatelem.|

(Vysvětlení terminologie a konvence použité v tomto odkazu najdete v tématu [Jak používat křížové odkazy na mapu zpráv](../../mfc/reference/how-to-use-the-message-map-cross-reference.md).)

Vzhledem k tomu, že Windows je operační systém orientovaný na zprávy, zahrnuje velkou část programování pro prostředí systému Windows zpracování zpráv. Pokaždé, když dojde k události, jako je klávesová zkratka nebo kliknutí myší, se do aplikace pošle zpráva, která musí tuto událost zpracovat.

Knihovna Microsoft Foundation Class nabízí programovací model optimalizovaný pro programování na základě zpráv. V tomto modelu se používají mapy zpráv k určení, které funkce budou zpracovávat různé zprávy pro určitou třídu. Mapy zpráv obsahují jedno nebo více maker, která určují, které zprávy bude zpracováno funkcemi. Například mapa zpráv obsahující `ON_COMMAND` makro může vypadat přibližně takto:

[!code-cpp[NVC_MFCMessageMaps#16](../../mfc/reference/codesnippet/cpp/message-maps-mfc_1.cpp)]

`ON_COMMAND` Makro se používá ke zpracování zpráv příkazů generovaných nabídkami, tlačítky a klávesami akcelerátorů. K dispozici jsou [makra](../../mfc/reference/message-map-macros-mfc.md) pro mapování následujících:

## <a name="windows-messages"></a>Zprávy systému Windows

- Oznámení řízení

- Uživatelem definované zprávy

## <a name="command-messages"></a>Zprávy příkazů

- Registrované uživatelem definované zprávy

- Zprávy o aktualizacích uživatelského rozhraní

## <a name="ranges-of-messages"></a>Rozsahy zpráv

- Příkazy

- Aktualizovat zprávy obslužné rutiny

- Oznámení řízení

I když jsou makra map zpráv důležitá, obecně je nemusíte používat přímo. Důvodem je, že [Průvodce třídou](mfc-class-wizard.md) automaticky vytvoří položky mapování zpráv ve zdrojových souborech, když je použijete k přidružení funkcí pro zpracování zpráv se zprávami. Kdykoli budete chtít upravit nebo přidat položku mapování zpráv, můžete použít Průvodce třídami.

> [!NOTE]
>  Průvodce třídami nepodporuje rozsahy mapování zpráv. Tyto položky mapování zpráv musíte zapsat sami.

Mapy zpráv jsou ale důležitou součástí knihovna Microsoft Foundation Class. Měli byste porozumět tomu, co dělají, a dokumentace je k dispozici.

## <a name="see-also"></a>Viz také:

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)
