---
title: "C3888 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3888
dev_langs: C++
helpviewer_keywords: C3888
ms.assetid: 40820812-79c5-4dcd-a19d-b4164d25fc8a
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e6f0310324afcbde112623959c4dc3b11155fed1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3888"></a>C3888 chyby kompilátoru
"název": const výrazu přidruženého k tomuto členu literálové datové nepodporuje C + +/ CLI  
  
 *Název* data člena, který je deklarovaný s [literálu](../../windows/literal-cpp-component-extensions.md) – klíčové slovo je inicializovaný s hodnotou kompilátor nepodporuje. Kompilátor podporuje pouze konstantní celočíselný, výčtu nebo typ řetězce. Pravděpodobnou příčinou pro **C3888** chyby je, že datový člen je inicializován s bajtové pole.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zkontrolujte, zda člen deklarované literálové datové podporovaného typu.  
  
## <a name="see-also"></a>Viz také  
 [literál](../../windows/literal-cpp-component-extensions.md)