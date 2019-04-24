---
title: Mapy odvozených zpráv
ms.date: 11/19/2018
helpviewer_keywords:
- message handling [MFC], derived message handlers
- messages, routing
- message maps [MFC], derived
- derived message maps
ms.assetid: 21829556-6e64-40c3-8279-fed85d99de77
ms.openlocfilehash: fcdff67c57e932e414a2b61b28cd0498ab997c60
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62173581"
---
# <a name="derived-message-maps"></a>Mapy odvozených zpráv

Během zpráva zpracování, kontrola zprávu třídy vlastní mapy není konec mapování zpráv scénáře. Co se stane, když třída `CMyView` (odvozený od `CView`) nemá žádné odpovídající položky pro zprávu

Mějte na paměti, která `CView`, základní třída `CMyView`, je zase odvozen z `CWnd`. Proto `CMyView` *je* `CView` a *je* `CWnd`. Každý z těchto tříd má vlastní mapu zpráv. Obrázek "A zobrazit hierarchii" níže zobrazuje hierarchický vztah tříd, ale mějte na paměti, že `CMyView` objektu je jeden objekt, který má vlastnosti všechny tři třídy.

![Hierarchie zobrazení](../mfc/media/vc38621.gif "hierarchie zobrazení") <br/>
A View Hierarchy

Pokud nejde spárovat zprávu ve třídě `CMyView`na mapu zpráv, rozhraní také prohledává mapy zpráv z přímé základní třídy. `BEGIN_MESSAGE_MAP` – Makro na začátku mapu zpráv určuje názvy dvou tříd jako argumenty:

[!code-cpp[NVC_MFCMessageHandling#2](../mfc/codesnippet/cpp/derived-message-maps_1.cpp)]

První argument názvy třídy, ke kterému patří mapování zprávy. Druhý argument obsahuje spojení s přímé základní třídy – `CView` tady – takže rozhraní můžete vyhledávat příliš jeho mapování zprávy.

Obslužné rutiny zpráv, které jsou k dispozici v základní třídě jsou tedy zděděny odvozenou třídou. To je velmi podobně jako normální virtuální členské funkce bez nutnosti provádět všechny členské funkce obslužných rutin virtuální.

Pokud žádná obslužná rutina je nalezena v žádném z mapy zpráv základní třídy, se provádí zpracování výchozí zprávy. Pokud má zpráva příkazu, rozhraní ho přesměruje do další cíli příkazu. Pokud je standardní zprávy Windows, předávání zpráv do odpovídající výchozí proceduru okna.

Na rychlost mapování zpráv odpovídající, rozhraní ukládá do mezipaměti poslední shody na pravděpodobnost, že ho bude tato zpráva znovu. Důsledkem tohoto objektu je procesy framework poměrně efektivní neošetřená zprávy. Mapy zpráv jsou také místo efektivnější než implementace, které používají virtuální funkce.

## <a name="see-also"></a>Viz také:

[Jak framework prohledává mapy zpráv](../mfc/how-the-framework-searches-message-maps.md)
