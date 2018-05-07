---
title: SDI a MDI | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- frame windows [MFC], SDI applications
- frame windows [MFC], MDI applications
- MFC, windows
- single document interface (SDI) [MFC], applications
- MDI [MFC], vs. SDI
ms.assetid: bb7239d9-4759-4f63-bfff-44a04b48c067
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: db63efe8d7e2622610bb56f5e6885b72b705093b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="sdi-and-mdi"></a>Rozhraní SDI a knihovna MDI
MFC usnadňuje práci s jedním dokumentu (SDI rozhraní) a rozhraní více dokumentů (MDI) aplikace.  
  
 Aplikace SDI povolit pouze jeden okně s rámečkem otevřít dokument najednou. Aplikace MDI povolit více dokumentů, oken s rámečkem otevřené ve stejné instanci aplikace. Aplikace MDI má období v rámci které více MDI podřízená okna, které jsou okna s rámečkem sami, můžou být otevřené, každý obsahující samostatný dokument. V některých aplikacích může být podřízená okna různých typů, například windows graf a tabulku windows. V takovém případě panelu nabídek můžete změnit, jako jsou aktivované podřízených oken MDI různých typů.  
  
> [!NOTE]
>  V systému Windows 95 a novější aplikace jsou běžně SDI protože operační systém přijal zobrazení "dokumentu-zarovnaný na střed".  
  
 Další informace najdete v tématu [dokumenty, zobrazení a Framework](../mfc/documents-views-and-the-framework.md).  
  
## <a name="see-also"></a>Viz také  
 [Použití tříd pro psaní aplikací pro Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
