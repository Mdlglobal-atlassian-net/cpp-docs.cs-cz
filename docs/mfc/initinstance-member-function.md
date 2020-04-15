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
ms.openlocfilehash: 2cf5b266348e299fe761ba40bd2cfb849f02b9ab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377195"
---
# <a name="initinstance-member-function"></a>InitInstance – členská funkce

Operační systém Windows umožňuje spustit více než jednu kopii nebo "instanci" stejné aplikace. `WinMain`volá [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) pokaždé, když se spustí nová instance aplikace.

Standardní `InitInstance` implementace vytvořená Průvodcem aplikací knihovny MFC provádí následující úkoly:

- Jako svou centrální akci vytvoří šablony dokumentů, které zase vytvářejí okna dokumentů, pohledů a rámečků. Popis tohoto procesu naleznete v tématu [Vytvoření šablony dokumentu](../mfc/document-template-creation.md).

- Načte standardní možnosti souborů ze souboru INI nebo registru systému Windows, včetně názvů naposledy použitých souborů.

- Zaregistruje jednu nebo více šablon dokumentů.

- Pro aplikaci MDI vytvoří okno hlavního rámce.

- Zpracuje příkazový řádek, aby otevřel dokument určený na příkazovém řádku nebo otevřel nový prázdný dokument.

Můžete přidat vlastní inicializační kód nebo upravit kód napsaný průvodcem.

> [!NOTE]
> Aplikace MFC musí být inicializovány jako jednovláknový objekt apartment (STA). Pokud zavoláte [CoInitializeExV](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex) v `InitInstance` přepsání, zadejte COINIT_APARTMENTTHREADED (spíše než COINIT_MULTITHREADED).

## <a name="see-also"></a>Viz také

[CWinApp – třída aplikace](../mfc/cwinapp-the-application-class.md)
