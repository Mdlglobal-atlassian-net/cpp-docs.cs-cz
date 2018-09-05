---
title: Přidání popisovače zpráv knihovny ATL | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message handlers [C++]
- ATL, windows
- message handling [C++], ATL message handler
- windows [C++], ATL
- ATL, message handlers
ms.assetid: cdea38a1-0d9b-4f8d-bbd5-b4f063fb3eeb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 712f1b725afd52057deca8f05047c91bfc4affce
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43753407"
---
# <a name="adding-an-atl-message-handler"></a>Přidání popisovače zpráv knihovny ATL

Přidání obslužné rutiny zpráv (členská funkce, která zpracovává zprávy Windows) do ovládacího prvku, vyberte první ovládací prvek v zobrazení tříd. Otevřete **vlastnosti** okna, vyberte **zprávy** ikony a klikněte na rozevírací ovládací prvek v poli opačný požadovaná zpráva. Tato možnost přidá deklaraci obslužné rutiny zpráv v souboru záhlaví ovládacího prvku a kostru implementaci obslužné rutiny v soubor .cpp ovládacího prvku. Bude také přidat mapu zpráv a přidat záznam pro obslužnou rutinu.

Přidání popisovače zpráv v ATL se podobá přidání obslužné rutiny zpráv pro třídy knihovny MFC. Zobrazit [Přidání popisovače zpráv knihovny MFC](../mfc/reference/adding-an-mfc-message-handler.md) Další informace.

Tyto podmínky platí pouze pro přidání popisovače zpráv knihovny ATL:

- Obslužné rutiny zpráv podle stejné zásady vytváření názvů jako knihovny MFC.

- Do objektu map hlavní zprávy jsou přidávány nové položky mapování zprávy. Průvodce nedokáže rozpoznat mapy alternativní zpráv a zřetězení.

## <a name="see-also"></a>Viz také

[Implementace okna](../atl/implementing-a-window.md)

