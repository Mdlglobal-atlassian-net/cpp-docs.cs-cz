---
title: 'Servery: Implementace serveru'
ms.date: 11/04/2016
helpviewer_keywords:
- servers, implementing
- OLE server applications [MFC], implementing OLE servers
ms.assetid: 5bd57e8e-3b23-4f23-9597-496fac2d24b5
ms.openlocfilehash: a5c89ff1256d557ef417b9e53ce76bbf1b5d6196
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51518954"
---
# <a name="servers-implementing-a-server"></a>Servery: Implementace serveru

Tento článek vysvětluje kód, který vytvoří Průvodce aplikací knihovny MFC pro vizuální úpravy serverové aplikace. Pokud nepoužíváte Průvodce aplikací, tento článek uvádí oblasti, kde je nutné napsat kód pro implementaci serverové aplikace.

Pokud používáte Průvodce aplikací k vytvoření nové serverové aplikace, poskytuje značné množství kódu pro konkrétní server za vás. Pokud přidáváte vizuální úpravy funkce serveru do existující aplikace, musí mít kód, který by před přidáním zbytek kódu nezbytné serveru zadali Průvodce aplikací.

Kód serveru, který obsahuje Průvodce aplikací spadá do několika kategorií:

- Definování prostředků serveru:

  - Prostředek nabídky, který se používá při serveru upravuje vloženou položku v samostatném okně.

  - Prostředky nabídek a panelů nástrojů použít, pokud je na místě aktivní server.

  Další informace o těchto prostředků najdete v tématu [nabídky a prostředky: serverové doplňky](../mfc/menus-and-resources-server-additions.md).

- Definuje třídu položky odvozené z `COleServerItem`. Další podrobnosti o serverové položky, naleznete v tématu [servery: serverové položky](../mfc/servers-server-items.md).

- Změna základní třídu třídy dokumentu má `COleServerDoc`. Další podrobnosti najdete v tématu [servery: implementace dokumentů serveru](../mfc/servers-implementing-server-documents.md).

- Definování třídy rámec okno odvozené z `COleIPFrameWnd`. Další podrobnosti najdete v tématu [servery: implementace místní rámce Windows](../mfc/servers-implementing-in-place-frame-windows.md).

- Vytvářet položku pro serverové aplikace v registrační databázi Windows a registrovat novou instanci serveru pomocí systému OLE. Informace v tomto tématu najdete v tématu [registrace](../mfc/registration.md).

- Inicializace a spuštění aplikace. Informace v tomto tématu najdete v tématu [registrace](../mfc/registration.md).

Další informace najdete v tématu [odvozenou třídu COleServerItem](../mfc/reference/coleserveritem-class.md), [coleserverdoc –](../mfc/reference/coleserverdoc-class.md), a [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md) v *knihovny tříd*.

## <a name="see-also"></a>Viz také

[Servery](../mfc/servers.md)<br/>
[Kontejnery](../mfc/containers.md)<br/>
[Nabídky a prostředky (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Registrace](../mfc/registration.md)

