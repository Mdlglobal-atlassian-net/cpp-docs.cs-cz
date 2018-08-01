---
title: Volání holé funkce | Dokumentace Microsoftu
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
ms.openlocfilehash: e395bcb32858bc63b3e848f20a7d794156876e26
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402026"
---
# <a name="naked-function-calls"></a>Volání holé funkce
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 Funkce deklarované s **naked** atribut jsou emitovány bez kódu prologu nebo epilogu umožňuje napsat vlastní sekvence vlastního kódu prologu/epilogu pomocí [vložený assembler](../assembler/inline/inline-assembler.md). Neviditelné funkce jsou k dispozici jako o pokročilou funkci. Umožňují deklarovat funkci, která je volána v jiném kontextu než C/C++ a proto vytvořit jiné předpoklady o kde parametry mají, nebo která registruje se zachovají. Příklady rutin, jako je například obslužné rutiny přerušení. Tato funkce je zvláště užitečná pro zápis ovladačů virtuálních zařízení (VxD).  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?  
  
-   [naked](../cpp/naked-cpp.md)  
  
-   [Pravidla holých funkcí a jejich omezení](../cpp/rules-and-limitations-for-naked-functions.md)  
  
-   [Důležité informace k zápisu kódu prologu/epilogu](../cpp/considerations-for-writing-prolog-epilog-code.md)  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také:  
 [Konvence volání](../cpp/calling-conventions.md)