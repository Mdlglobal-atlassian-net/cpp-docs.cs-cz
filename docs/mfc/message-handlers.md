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
ms.openlocfilehash: 25805187f88c5423ea41cd7cbe346e44e7d7d36a
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907465"
---
# <a name="message-handlers"></a>Obslužné rutiny zpráv

V knihovně MFC zpracovává vyhrazená funkce *obslužné rutiny* každou samostatnou zprávu. Funkce obslužných rutin zpráv jsou členské funkce třídy. Tato dokumentace používá výrazy *– členské funkce obslužných rutin zpráv*, *funkce obslužných*rutin zpráv, *popisovače zpráv*a *obslužné rutiny* . Některé druhy obslužných rutin zpráv se označují také jako "obslužné rutiny příkazu".

Psaní účtů obslužných rutin zpráv pro velký podíl vaší práce v zápisu aplikace architektury. Tato rodina článků popisuje, jak funguje mechanismus zpracování zpráv.

K čemu obslužná rutina zprávy slouží bez ohledu na to, co chcete v reakci na tuto zprávu provést. Obslužné rutiny lze vytvořit pomocí [Průvodce třídou](reference/mfc-class-wizard.md) třídy a potom vyplnit kód obslužné rutiny pomocí editoru zdrojového kódu.

K psaní obslužných rutin můžete použít všechny funkce sady C++ Microsoft Visual a MFC. Seznam všech tříd naleznete v tématu [Přehled knihovny tříd](../mfc/class-library-overview.md) v *Referenci knihovny MFC*.

## <a name="see-also"></a>Viz také:

[Zprávy a příkazy v prostředí .NET Framework](../mfc/messages-and-commands-in-the-framework.md)
