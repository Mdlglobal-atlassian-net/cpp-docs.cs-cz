---
title: "Uklízení dokumentů a zobrazení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- views [MFC], cleaning up
- documents [MFC], cleaning up
- documents [MFC], closing
ms.assetid: 0c454db2-3644-434d-9e53-8108a7aedfe1
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f9bb1cbcb58e2693b33693b390a09d3826c77cfd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cleaning-up-documents-and-views"></a>Uklízení dokumentů a zobrazení
Při zavírání dokumentu nejprve volá rámec jeho [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) – členská funkce. Pokud jste přidělili libovolná paměť v haldě v průběhu operace dokumentu `DeleteContents` je nejlepší místo k navrácení ho.  
  
> [!NOTE]
>  Data dokumentu v dokumentu – destruktor nesmí zrušit přidělení. V případě aplikace SDI objekt dokument znova.  
  
 Můžete přepsat zobrazení destruktor se zrušit přidělení žádné paměti, které jste přidělili v haldě.  
  
## <a name="see-also"></a>Viz také  
 [Inicializace a Uklízení dokumentů a zobrazení](../mfc/initializing-and-cleaning-up-documents-and-views.md)

