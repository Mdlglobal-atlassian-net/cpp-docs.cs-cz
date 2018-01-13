---
title: Technologie Active a knihovny DLL | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- in-process server DLLs
- Automation [C++], DLLs
- DLLs [C++], Active Technology
- Active technology [C++]
- MFC DLLs [C++], Active Technology
ms.assetid: 3ed27f8d-164a-4562-ad61-9f2333404cc7
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 44dcc58aed4025af2e3e2177e978633c13f0ef20
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="active-technology-and-dlls"></a>Technologie Active a knihovny DLL
Technologie Active umožňuje serverům objektu k implementaci zcela uvnitř knihovny DLL. Tento typ serveru se říká server v procesu. MFC nepodporuje zcela v procesu servery pro úpravy s náhledem, všechny funkce především, protože technologie Active neposkytuje způsob, jak se server připojí do kontejneru hlavní zpráva smyčky. MFC vyžaduje přístup ke smyčce zpráv aplikace typu kontejner pro zpracování klávesy akcelerátoru a zpracování doby nečinnosti.  
  
 Pokud píšete serveru automatizace a váš server nemá žádné uživatelské rozhraní, můžete nastavit váš server v rámci procesu a umístí jej zcela do knihovny DLL.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
  
-   [Automatizační servery](../mfc/automation-servers.md)  
  
## <a name="see-also"></a>Viz také  
 [Knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md)