---
title: InitInstance – členská funkce
ms.date: 11/04/2016
f1_keywords:
- InitInstance
helpviewer_keywords:
- InitInstance method [MFC]
- applications [MFC], initializing
- MFC, initializing
- initializing MFC applications
ms.assetid: 4ef09267-ff7f-4c39-91a0-57454a264f83
ms.openlocfilehash: c1f83f794cc40fa7f4d290fa4a147fe9f7e074be
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508375"
---
# <a name="initinstance-member-function"></a>InitInstance – členská funkce

Operační systém Windows umožňuje spustit více než jednu kopii nebo "instanci" stejné aplikace. `WinMain`volá [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) pokaždé, když se spustí nová instance aplikace.

Standardní `InitInstance` implementace vytvořená Průvodcem aplikací knihovny MFC provádí následující úlohy:

- Jako jeho ústřední akce vytvoří šablony dokumentů, které zase vytvoří dokumenty, zobrazení a okna s rámečkem. Popis tohoto procesu najdete v tématu [Vytvoření šablony dokumentu](../mfc/document-template-creation.md).

- Načte standardní možnosti souborů ze souboru. ini nebo z registru Windows, včetně názvů naposledy použitých souborů.

- Zaregistruje jednu nebo více šablon dokumentů.

- Pro aplikaci MDI vytvoří hlavní okno rámce.

- Zpracuje příkazový řádek pro otevření dokumentu zadaného v příkazovém řádku nebo pro otevření nového prázdného dokumentu.

Můžete přidat vlastní inicializační kód nebo upravit kód napsaný průvodcem.

> [!NOTE]
>  Aplikace MFC musí být inicializovány jako jednovláknový objekt apartment (STA). Pokud zavoláte [funkce CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex) do `InitInstance` svého přepsání, zadejte COINIT_APARTMENTTHREADED (místo COINIT_MULTITHREADED).

## <a name="see-also"></a>Viz také:

[CWinApp: Třída aplikace](../mfc/cwinapp-the-application-class.md)
