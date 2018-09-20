---
title: Obslužné rutiny zpráv | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message handlers [MFC]
- command handling [MFC], message handlers
- handlers [MFC]
- message handling [MFC], message handler functions
- handlers [MFC], command
- handlers [MFC], message
ms.assetid: 51bc4e76-dbe3-4cc2-b026-3199d56b2fa9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 22dde243bb6d8e8a283e670804d4b8b6cad9082c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46406747"
---
# <a name="message-handlers"></a>Obslužné rutiny zpráv

V knihovně MFC, vyhrazené *obslužná rutina* funkce zpracovává každou samostatnou zprávu. Obslužná rutina zprávy funkce jsou členské funkce třídy. Tato dokumentace používá podmínky *obslužná rutina zprávy členskou funkci*, *obslužná rutina zprávy funkce*, *obslužná rutina zprávy*, a *obslužná rutina*Zaměnitelně. Některé druhy obslužné rutiny zpráv se také označují jako "obslužné rutiny příkazů."

Zápis účty obslužné rutiny zpráv pro velkou část práce při psaní rozhraní framework aplikace. Tento článek řady popisuje, jak funguje mechanismus zpracování zpráv.

Co dělá obslužné rutiny pro zprávy, to nemá cokoliv, co chcete v reakci na tuto zprávu. Můžete vytvořit pomocí okna Vlastnosti třídy obslužné rutiny a pak vyplňte obslužné rutiny kódu pomocí editoru zdrojového kódu.

Vám pomůže všem zařízením služby Microsoft Visual C++ a knihovnou MFC napsat obslužné rutině. Seznam všech tříd naleznete v tématu [– přehled knihovny tříd](../mfc/class-library-overview.md) v *odkaz knihovny MFC*.

## <a name="see-also"></a>Viz také

[Zprávy a příkazy v prostředí .NET Framework](../mfc/messages-and-commands-in-the-framework.md)

