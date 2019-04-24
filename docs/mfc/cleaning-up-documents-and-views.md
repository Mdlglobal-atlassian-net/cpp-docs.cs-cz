---
title: Uklízení dokumentů a zobrazení
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], cleaning up
- documents [MFC], cleaning up
- documents [MFC], closing
ms.assetid: 0c454db2-3644-434d-9e53-8108a7aedfe1
ms.openlocfilehash: 940c768823d26950d9710fb1d1a52e6a1955fead
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62327155"
---
# <a name="cleaning-up-documents-and-views"></a>Uklízení dokumentů a zobrazení

Pokud dokument se zavírá, nejprve volá rámec jeho [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) členskou funkci. Pokud jste přidělili paměti v haldě v průběhu operace dokumentu `DeleteContents` je nejlepším místem k jeho uvolnění.

> [!NOTE]
>  Data dokumentu v dokumentu destruktoru by neměl uvolnit. V případě aplikace SDI objekt dokument znova.

Můžete přepsat zobrazení destruktor pro uvolnění paměti, které jste přidělili v haldě.

## <a name="see-also"></a>Viz také:

[Inicializace a uklízení dokumentů a zobrazení](../mfc/initializing-and-cleaning-up-documents-and-views.md)
