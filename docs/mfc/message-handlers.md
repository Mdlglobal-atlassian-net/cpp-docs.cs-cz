---
title: Obslužné rutiny zpráv
ms.date: 11/04/2016
helpviewer_keywords:
- message handlers [MFC]
- command handling [MFC], message handlers
- handlers [MFC]
- message handling [MFC], message handler functions
- handlers [MFC], command
- handlers [MFC], message
ms.assetid: 51bc4e76-dbe3-4cc2-b026-3199d56b2fa9
ms.openlocfilehash: 0d3ed6239b638a0e161cd7e3580f4fe6e1b4a7e7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383753"
---
# <a name="message-handlers"></a>Obslužné rutiny zpráv

V knihovně MFC, vyhrazené *obslužná rutina* funkce zpracovává každou samostatnou zprávu. Obslužná rutina zprávy funkce jsou členské funkce třídy. Tato dokumentace používá podmínky *obslužná rutina zprávy členskou funkci*, *obslužná rutina zprávy funkce*, *obslužná rutina zprávy*, a *obslužná rutina*Zaměnitelně. Některé druhy obslužné rutiny zpráv se také označují jako "obslužné rutiny příkazů."

Zápis účty obslužné rutiny zpráv pro velkou část práce při psaní rozhraní framework aplikace. Tento článek řady popisuje, jak funguje mechanismus zpracování zpráv.

Co dělá obslužné rutiny pro zprávy, to nemá cokoliv, co chcete v reakci na tuto zprávu. Můžete vytvořit pomocí okna Vlastnosti třídy obslužné rutiny a pak vyplňte obslužné rutiny kódu pomocí editoru zdrojového kódu.

Vám pomůže všem zařízením služby Microsoft Visual C++ a knihovnou MFC napsat obslužné rutině. Seznam všech tříd naleznete v tématu [– přehled knihovny tříd](../mfc/class-library-overview.md) v *odkaz knihovny MFC*.

## <a name="see-also"></a>Viz také:

[Zprávy a příkazy v prostředí .NET Framework](../mfc/messages-and-commands-in-the-framework.md)
