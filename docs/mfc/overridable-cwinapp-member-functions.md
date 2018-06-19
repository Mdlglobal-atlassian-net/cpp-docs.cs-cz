---
title: Přepisovatelné členské funkce CWinApp | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CWinApp
dev_langs:
- C++
helpviewer_keywords:
- overriding [MFC], overridable functions in CWinApp
- application class [MFC]
- CWinApp class [MFC], overridables
ms.assetid: 07183d5e-734b-45d9-a8b6-9dde4adac0b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d454ce65a2068a00f9b2c7f5934951f295738c12
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33347708"
---
# <a name="overridable-cwinapp-member-functions"></a>Přepisovatelné členské funkce CWinApp
[CWinApp](../mfc/reference/cwinapp-class.md) poskytuje několik klíče přepisovatelné členské funkce (`CWinApp` nahradí tyto členy z třídy [CWinThread](../mfc/reference/cwinthread-class.md), ze kterého `CWinApp` odvozuje):  
  
-   [InitInstance –](../mfc/initinstance-member-function.md)  
  
-   [Spustit](../mfc/run-member-function.md)  
  
-   [ExitInstance –](../mfc/exitinstance-member-function.md)  
  
-   [ONIDLE –](../mfc/onidle-member-function.md)  
  
 Jediným `CWinApp` – členská funkce, které je nutné přepsat je `InitInstance`.  
  
## <a name="see-also"></a>Viz také  
 [CWinApp – třída aplikace](../mfc/cwinapp-the-application-class.md)
