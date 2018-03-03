---
title: "Přepsání standardního směrování příkazů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], overriding
- command handling [MFC], routing commands
- overriding, standard command routing
ms.assetid: 872b698a-7432-40c4-9008-68721e8effa5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6a8f926a2aa9ed48dac24f75850876bbd1e04ef4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="overriding-the-standard-command-routing"></a>Přepsání standardního směrování příkazů
Ve výjimečných případech při musí implementovat některé varianta standardní framework směrování, lze jej přepsat. Cílem je, chcete-li změnit směrování v jedné nebo více tříd přepsáním `OnCmdMsg` v těchto tříd. Postupujte následovně:  
  
-   Ve třídě, která dělí pořadí předat objekt jiný než výchozí.  
  
-   V dialogu Nový objekt nevýchozí nebo cíle příkazů ho pak může předat příkazy, které.  
  
 Pokud některé nový objekt vložíte do směrování, její třída musí být příkaz cílovou třídu. Ve vašem přepsání verzích `OnCmdMsg`, volejte na verzi, která jste přepsání. Najdete v článku [oncmdmsg –](../mfc/reference/ccmdtarget-class.md#oncmdmsg) funkce člena třídy `CCmdTarget` v *odkaz knihovny MFC* a verzí v těchto tříd jako `CView` a **CDocument** v Zadaný zdroj kódu příklady.  
  
## <a name="see-also"></a>Viz také  
 [Jakým způsobem volá framework obslužnou rutinu](../mfc/how-the-framework-calls-a-handler.md)

