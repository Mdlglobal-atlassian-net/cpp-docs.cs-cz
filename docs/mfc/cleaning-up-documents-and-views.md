---
title: Uklízení dokumentů a zobrazení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- views [MFC], cleaning up
- documents [MFC], cleaning up
- documents [MFC], closing
ms.assetid: 0c454db2-3644-434d-9e53-8108a7aedfe1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f4325b0de10861fc76ee9ab816376f40ba0ba587
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46437414"
---
# <a name="cleaning-up-documents-and-views"></a>Uklízení dokumentů a zobrazení

Pokud dokument se zavírá, nejprve volá rámec jeho [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) členskou funkci. Pokud jste přidělili paměti v haldě v průběhu operace dokumentu `DeleteContents` je nejlepším místem k jeho uvolnění.

> [!NOTE]
>  Data dokumentu v dokumentu destruktoru by neměl uvolnit. V případě aplikace SDI objekt dokument znova.

Můžete přepsat zobrazení destruktor pro uvolnění paměti, které jste přidělili v haldě.

## <a name="see-also"></a>Viz také

[Inicializace a uklízení dokumentů a zobrazení](../mfc/initializing-and-cleaning-up-documents-and-views.md)

