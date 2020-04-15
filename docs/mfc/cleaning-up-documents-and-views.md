---
title: Uklízení dokumentů a zobrazení
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], cleaning up
- documents [MFC], cleaning up
- documents [MFC], closing
ms.assetid: 0c454db2-3644-434d-9e53-8108a7aedfe1
ms.openlocfilehash: 06ff60a2cf6245f64e80d899c13a8444558fcf0b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374625"
---
# <a name="cleaning-up-documents-and-views"></a>Uklízení dokumentů a zobrazení

Při zavření dokumentu framework nejprve volá jeho [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) členské funkce. Pokud jste přidělili všechny paměti na haldě v `DeleteContents` průběhu operace dokumentu, je nejlepší místo pro navrátit.

> [!NOTE]
> V destruktoru dokumentu byste neměli navrátit data dokumentu. V případě aplikace SDI může být objekt dokumentu znovu použit.

Můžete přepsat destruktor zobrazení a navrátit paměť, kterou jste přidělili na haldě.

## <a name="see-also"></a>Viz také

[Inicializace a uklízení dokumentů a zobrazení](../mfc/initializing-and-cleaning-up-documents-and-views.md)
