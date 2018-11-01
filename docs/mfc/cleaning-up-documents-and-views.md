---
title: Uklízení dokumentů a zobrazení
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], cleaning up
- documents [MFC], cleaning up
- documents [MFC], closing
ms.assetid: 0c454db2-3644-434d-9e53-8108a7aedfe1
ms.openlocfilehash: 1357a02379a848af23a6f78dee29e5b6adc1efcc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653892"
---
# <a name="cleaning-up-documents-and-views"></a>Uklízení dokumentů a zobrazení

Pokud dokument se zavírá, nejprve volá rámec jeho [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) členskou funkci. Pokud jste přidělili paměti v haldě v průběhu operace dokumentu `DeleteContents` je nejlepším místem k jeho uvolnění.

> [!NOTE]
>  Data dokumentu v dokumentu destruktoru by neměl uvolnit. V případě aplikace SDI objekt dokument znova.

Můžete přepsat zobrazení destruktor pro uvolnění paměti, které jste přidělili v haldě.

## <a name="see-also"></a>Viz také

[Inicializace a uklízení dokumentů a zobrazení](../mfc/initializing-and-cleaning-up-documents-and-views.md)

