---
title: Přepsání standardního směrování příkazů | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], overriding
- command handling [MFC], routing commands
- overriding, standard command routing
ms.assetid: 872b698a-7432-40c4-9008-68721e8effa5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 58156f6d1c361c24dc6cf04a9208157d614f91a8
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929007"
---
# <a name="overriding-the-standard-command-routing"></a>Přepsání standardního směrování příkazů
Ve výjimečných případech při musí implementovat některé varianta standardní framework směrování, lze jej přepsat. Cílem je, chcete-li změnit směrování v jedné nebo více tříd přepsáním `OnCmdMsg` v těchto tříd. Postupujte následovně:  
  
-   Ve třídě, která dělí pořadí předat objekt jiný než výchozí.  
  
-   V dialogu Nový objekt nevýchozí nebo cíle příkazů ho pak může předat příkazy, které.  
  
 Pokud některé nový objekt vložíte do směrování, její třída musí být příkaz cílovou třídu. Ve vašem přepsání verzích `OnCmdMsg`, volejte na verzi, která jste přepsání. Najdete v článku [oncmdmsg –](../mfc/reference/ccmdtarget-class.md#oncmdmsg) funkce člena třídy `CCmdTarget` v *odkaz knihovny MFC* a verzí v těchto tříd jako `CView` a `CDocument` v zadaný zdroj kódu příklady.  
  
## <a name="see-also"></a>Viz také  
 [Jakým způsobem volá framework obslužnou rutinu](../mfc/how-the-framework-calls-a-handler.md)

