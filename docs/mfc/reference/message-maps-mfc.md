---
title: Mapy zpráv (MFC)
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.messages
helpviewer_keywords:
- message maps [MFC], MFC
- Windows messages [MFC], message maps
- messages [MFC], Windows
- MFC, messages
ms.assetid: 3f9855e4-9d7d-4b64-8f3f-a19ea3cf79ba
ms.openlocfilehash: 91b7f21d92b2f899895b008b3fab8b541aec9963
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412784"
---
# <a name="message-maps-mfc"></a>Mapy zpráv (MFC)

Tento oddíl odkaz obsahuje seznam všech [makra mapování zpráv](../../mfc/reference/message-map-macros-mfc.md) a všechny [CWnd](../../mfc/reference/cwnd-class.md) prototypy funkce mapy zpráv položky spolu s odpovídající člen:

|Kategorie|Popis|
|--------------|-----------------|
|DÁLE\_obslužná rutina příkazu zprávy|Zpracovává `WM_COMMAND` zprávy generované uživatelské možnosti nabídky nebo nabídky přístupové klíče.|
|[Obslužné rutiny oznamovacích zpráv v podřízených oknech](../../mfc/reference/child-window-notification-message-handlers.md)|Zpracování zpráv s oznámením z podřízených oken.|
|[Wm_ – obslužné rutiny zpráv](../../mfc/reference/handlers-for-wm-messages.md)|Zpracování `WM_` zprávy, jako například `WM_PAINT`.|
|[Obslužné rutiny zpráv definovaný uživatelem](../../mfc/reference/user-defined-handlers.md)|Zpracování zpráv definovaný uživatelem.|

(Vysvětlení terminologie a konvencích použitých v tomto odkazu najdete v tématu [použití křížových odkazů mapování zpráv](../../mfc/reference/how-to-use-the-message-map-cross-reference.md).)

Protože Windows orientovaných na zprávu operačního systému, velká část programování pro prostředí Windows zahrnuje zpracování zpráv. Vyvolá se pokaždé, když událost jako stisk klávesy nebo myš, klikněte na tlačítko, zpráva se odešle do aplikace, kterou musíte následně zpracovat události.

Knihovny Microsoft Foundation Class nabízí programovací model, který je optimalizovaný pro programování založené na zprávách. V tomto modelu "mapy zprávy" se používají k určení, funkcích, které bude zpracovávat různé zprávy pro určité třídy. Zprávy maps obsahují jeden nebo více makra, které určují, které zprávy bude zpracován adresou funkcích, které. Například zpráva mapy obsahující `ON_COMMAND` – makro může vypadat přibližně takto:

[!code-cpp[NVC_MFCMessageMaps#16](../../mfc/reference/codesnippet/cpp/message-maps-mfc_1.cpp)]

`ON_COMMAND` – Makro se používá ke zpracování příkazu zprávy generované nabídek, tlačítek a přístupové klávesy. [Makra](../../mfc/reference/message-map-macros-mfc.md) jsou k dispozici pro následující mapování:

## <a name="windows-messages"></a>Zprávy Windows

- Oznámení ovládacího prvku

- Uživatelem definované zprávy

## <a name="command-messages"></a>Zprávy příkazů

- Registrované uživatelské zprávy

- Zprávy o aktualizaci uživatelského rozhraní

## <a name="ranges-of-messages"></a>Oblasti zpráv

- Příkazy

- Aktualizujte obslužné rutiny zpráv

- Oznámení ovládacího prvku

Makra map zpráv jsou důležité, obvykle není nutné používat přímo. Je to proto, že v okně Vlastnosti automaticky vytvoří mapu zpráv položky ve zdrojových souborech, při použití funkce zpracování zprávy přidružit zprávy. Pokaždé, když chcete upravit nebo přidat položku mapy zpráv, můžete v okně Vlastnosti.

> [!NOTE]
>  V okně Vlastnosti nepodporuje oblasti map zpráv. Tyto položky mapování zpráv musíte napsat sami.

Mapy zpráv, ale jsou důležitou součástí knihovny Microsoft Foundation Class. Měli byste pochopit, co dělají a dokumentace, kterou pro ně.

## <a name="see-also"></a>Viz také:

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)
