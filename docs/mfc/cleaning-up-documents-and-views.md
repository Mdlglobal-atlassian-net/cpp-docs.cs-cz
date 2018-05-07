---
title: Uklízení dokumentů a zobrazení | Microsoft Docs
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
ms.openlocfilehash: 2dfe54c13db6f44bc70289380ae5f50d99c3722b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cleaning-up-documents-and-views"></a>Uklízení dokumentů a zobrazení
Při zavírání dokumentu nejprve volá rámec jeho [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) – členská funkce. Pokud jste přidělili libovolná paměť v haldě v průběhu operace dokumentu `DeleteContents` je nejlepší místo k navrácení ho.  
  
> [!NOTE]
>  Data dokumentu v dokumentu – destruktor nesmí zrušit přidělení. V případě aplikace SDI objekt dokument znova.  
  
 Můžete přepsat zobrazení destruktor se zrušit přidělení žádné paměti, které jste přidělili v haldě.  
  
## <a name="see-also"></a>Viz také  
 [Inicializace a uklízení dokumentů a zobrazení](../mfc/initializing-and-cleaning-up-documents-and-views.md)

