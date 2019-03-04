---
title: 'Kontejnery: Klientské položky'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE containers [MFC], client items
- client items and OLE containers
ms.assetid: 231528b5-0744-4f83-8897-083bf55ed087
ms.openlocfilehash: 0c7f4a63cb9a31b52be2d3574ddad29313df6a4d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57298279"
---
# <a name="containers-client-items"></a>Kontejnery: Klientské položky

Tento článek vysvětluje, co jsou klientské položky a z třídy, vaše aplikace by měl být odvozen jeho klientské položky.

Klientské položky jsou datové položky, které patří do jiné aplikace, které jsou součástí nebo odkazuje dokument aplikace kontejneru OLE. Klientské položky, jejichž data jsou obsažena v rámci dokumentu jsou vložené; ty, jejichž data se ukládají v jiném umístění odkazuje dokument kontejneru jsou propojeny.

Třída dokumentu v aplikaci OLE je odvozená od třídy [coledocument –](../mfc/reference/coledocument-class.md) spíše než z `CDocument`. `COleDocument` Třída dědí z `CDocument` všechny funkce potřebné pro používání architektury dokumentu/zobrazení, na které MFC aplikace využívají. `COleDocument` také definuje rozhraní, které považuje za soubor dokumentu `CDocItem` objekty. Několik `COleDocument` členské funkce jsou k dispozici pro přidávání, načítání a odstranění prvků této kolekce.

Každý kontejner aplikace by měl být odvozen z aspoň jednu třídu `COleClientItem`. Objekty této třídy představují položky vložené nebo propojené v dokumentu OLE. Tyto objekty existují po celou dobu životnosti dokumentu, které je obsahují, dokud se neodstraní z dokumentu.

`CDocItem` je základní třídou pro `COleClientItem` a `COleServerItem`. Objekty tříd odvozených z těchto dvou fungují jako prostředníci mezi položky OLE a klientské a serverové aplikace, v uvedeném pořadí. Pokaždé, když se přidá nová položka OLE v dokumentu rozhraní MFC přidá nový objekt z klientské aplikace `COleClientItem`-odvozené třídy dokumentu kolekce `CDocItem` objekty.

## <a name="see-also"></a>Viz také:

[Kontejnery](../mfc/containers.md)<br/>
[Kontejnery: Složené soubory](../mfc/containers-compound-files.md)<br/>
[Kontejnery: Problémy uživatelského rozhraní](../mfc/containers-user-interface-issues.md)<br/>
[Kontejnery: Pokročilé funkce](../mfc/containers-advanced-features.md)<br/>
[COleClientItem – třída](../mfc/reference/coleclientitem-class.md)<br/>
[COleServerItem – třída](../mfc/reference/coleserveritem-class.md)
