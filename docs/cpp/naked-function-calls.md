---
title: Volání holé funkce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b9d7b42f08d68af9838bf908efdbcc59a0540b91
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="naked-function-calls"></a>Volání holé funkce
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 Funkce deklarovat s `naked` atribut jsou vygenerované bez kódu prologu nebo epilogu, umožňuje psát vlastní vlastní prologu/epilogu pořadí pomocí [vloženého assembleru](../assembler/inline/inline-assembler.md). Holé funkce jsou uvedeny jako pokročilá funkce. Umožňují deklarovat funkci, která je volána z kontextu než C/C++ a proto zkontrolujte různých předpokladů o kde parametry mají nebo která registruje se zachovají. Příklady zahrnují rutiny, jako je například obslužné rutiny přerušení. Tato funkce je obzvláště užitečná pro zapisovače virtuální ovladače zařízení (VxD).  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
  
-   [naked](../cpp/naked-cpp.md)  
  
-   [Pravidla holých funkcí a jejich omezení](../cpp/rules-and-limitations-for-naked-functions.md)  
  
-   [Důležité informace k zápisu kódu prologu/epilogu](../cpp/considerations-for-writing-prolog-epilog-code.md)  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Konvence volání](../cpp/calling-conventions.md)