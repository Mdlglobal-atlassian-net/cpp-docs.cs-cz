---
title: Vztah k rozhraní API jazyka C | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.mfc
dev_langs:
- C++
helpviewer_keywords:
- books [MFC], about MFC and Windows SDK
- books [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- Windows API [MFC], and MFC
ms.assetid: 334e8efc-f3cc-4018-bc2e-02908b2a39fe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5d06c4adfa5493929a24c233fa923451c7bf0f95
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33379226"
---
# <a name="relationship-to-the-c-language-api"></a>Vztah k rozhraní API jazyka C
Jeden vlastnosti, která nastavuje knihovna Microsoft Foundation Class (MFC) kromě jiných knihovny tříd pro systém Windows je velmi zavřít mapování na rozhraní API systému Windows, které jsou napsané v jazyce C. Navíc je možné obecně kombinovat volání knihovny tříd volně pomocí přímé volání rozhraní API systému Windows. Tento přímý přístup, ale neznamená, že třídy se o úplné nahrazení pro toto rozhraní API. Vývojáři musí stále příležitostně volat přímo na některé funkce systému Windows, jako [SetCursor](http://msdn.microsoft.com/library/windows/desktop/ms648393) a [GetSystemMetrics](http://msdn.microsoft.com/library/windows/desktop/ms724385), např. Funkce systému Windows je zabalen členské funkce tříd tehdy, když je výhodu tak.  
  
 Protože je někdy nutné vytvářet nativní volání funkce systému Windows, byste měli mít přístup k dokumentaci rozhraní API jazyka C systému Windows. Tato dokumentace je součástí Microsoft Visual C++.  
  
> [!NOTE]
>  Přehled o tom, jak funguje knihovny MFC framework najdete v tématu [použití tříd pro zápis aplikace pro Windows](../mfc/using-the-classes-to-write-applications-for-windows.md).  
  
## <a name="see-also"></a>Viz také  
 [Obecná filozofie návrhu tříd](../mfc/general-class-design-philosophy.md)
