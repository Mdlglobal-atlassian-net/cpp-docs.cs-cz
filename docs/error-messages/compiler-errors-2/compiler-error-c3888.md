---
title: C3888 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3888
dev_langs:
- C++
helpviewer_keywords:
- C3888
ms.assetid: 40820812-79c5-4dcd-a19d-b4164d25fc8a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c11c897f35a6c395c4bc6ee6a64be51fa810911b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3888"></a>C3888 chyby kompilátoru
"název": const výrazu přidruženého k tomuto členu literálové datové nepodporuje C + +/ CLI  
  
 *Název* data člena, který je deklarovaný s [literálu](../../windows/literal-cpp-component-extensions.md) – klíčové slovo je inicializovaný s hodnotou kompilátor nepodporuje. Kompilátor podporuje pouze konstantní celočíselný, výčtu nebo typ řetězce. Pravděpodobnou příčinou pro **C3888** chyby je, že datový člen je inicializován s bajtové pole.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zkontrolujte, zda člen deklarované literálové datové podporovaného typu.  
  
## <a name="see-also"></a>Viz také  
 [Literál](../../windows/literal-cpp-component-extensions.md)