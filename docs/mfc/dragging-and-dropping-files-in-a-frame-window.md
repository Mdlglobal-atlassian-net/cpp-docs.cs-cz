---
title: Přetahování souborů v okně s rámečkem | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- drag and drop [MFC], files
- drag and drop [MFC], File Manager
- Windows Explorer [MFC]
- File Manager drag and drop support [MFC]
- files [MFC], drag and drop
- frame windows [MFC], dragging and dropping files in
- drag and drop [MFC], Windows Explorer
ms.assetid: 85560fe9-121b-4105-bd7b-216b966e19fa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aa326dba7772ddcdccb304900df4460ce9754665
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33345568"
---
# <a name="dragging-and-dropping-files-in-a-frame-window"></a>Přetahování souborů v okně s rámečkem
Okně s rámečkem spravuje se v Průzkumníkovi souborů nebo správce souborového vztah.  
  
 Pomocí přidání několik inicializace volá v přepsání z `CWinApp` – členská funkce `InitInstance`, jak je popsáno v [CWinApp: třídy aplikace](../mfc/cwinapp-the-application-class.md), může mít vaše oken s rámečkem nepřímo otevřené soubory přetáhnout ze souboru Průzkumníka nebo správce souborového a vyřadit v rámci okna. V tématu [Správce souborů – přetažení](../mfc/special-cwinapp-services.md).  
  
## <a name="see-also"></a>Viz také  
 [Použití oken s rámečkem](../mfc/using-frame-windows.md)

