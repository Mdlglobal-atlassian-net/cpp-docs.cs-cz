---
title: Propojení v názvech s rozsahem třídy | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- scope [C++], linkage rules
- linkage [C++], scope linkage rules
- names [C++], scope linkage rules
- classes [C++], scope
- external linkage, scope linkage rules
- class names [C++], linkage
- classes [C++], names
- scope [C++], class names
- class scope [C++], linkage in names with
ms.assetid: 45275ff3-6e94-4967-82c8-ba540ef4da28
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9eb58f87e998fbe1eeeb9b26eb0da75046a9079d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418969"
---
# <a name="linkage-in-names-with-class-scope"></a>Propojení v názvech s rozsahem třídy
Následující pravidla propojení platí pro názvy s oborem třídy:  
  
-   Statické členy třídy mají vnější propojení.  
  
-   Členské funkce tříd mají vnější propojení.  
  
-   Výčty a názvy `typedef` nemají žádné propojení.  
  
 **Konkrétní Microsoft**  
  
-   Funkce deklarované jako funkce `friend` musí mít vnější propojení. Deklarací statické funkce s klíčovým slovem `friend` dojde k chybě.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Program a propojení](../cpp/program-and-linkage-cpp.md)