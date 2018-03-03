---
title: "Volání holé funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- virtual device drivers
- VXD virtual device drivers
- virtual device drivers, naked function calls
- naked functions
- prolog code
- epilog code
- naked keyword [C++]
- naked keyword [C++], storage-class attribute
ms.assetid: 2a66847a-a43f-4541-a7be-c9f5f29b5fdb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eed53718d211ac2152978c2a4d36e6a82c5c8024
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="naked-function-calls"></a>Volání holé funkce
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 Funkce deklarovat s `naked` atribut jsou vygenerované bez kódu prologu nebo epilogu, umožňuje psát vlastní vlastní prologu/epilogu pořadí pomocí [vloženého assembleru](../assembler/inline/inline-assembler.md). Holé funkce jsou uvedeny jako pokročilá funkce. Umožňují deklarovat funkci, která je volána z kontextu než C/C++ a proto zkontrolujte různých předpokladů o kde parametry mají nebo která registruje se zachovají. Příklady zahrnují rutiny, jako je například obslužné rutiny přerušení. Tato funkce je obzvláště užitečná pro zapisovače virtuální ovladače zařízení (VxD).  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
  
-   [holé](../cpp/naked-cpp.md)  
  
-   [Pravidla holých funkcí a jejich omezení](../cpp/rules-and-limitations-for-naked-functions.md)  
  
-   [Důležité informace k zápisu kódu prologu/epilogu](../cpp/considerations-for-writing-prolog-epilog-code.md)  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Konvence volání](../cpp/calling-conventions.md)