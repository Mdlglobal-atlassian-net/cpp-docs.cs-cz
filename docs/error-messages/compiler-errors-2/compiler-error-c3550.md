---
title: C3550 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3550
dev_langs:
- C++
helpviewer_keywords:
- C3550
ms.assetid: 9f2d5ffc-e429-41a1-89e3-7acc4fd47e14
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 91003af2069ba32083caefa8f5a79cbe0e7cd9c9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3550"></a>C3550 chyby kompilátoru
v tomto kontextu je povoleno pouze prostý 'decltype(auto).  
  
 Pokud `decltype(auto)` slouží jako zástupný symbol pro návratový typ funkce, musíte ho použít samostatně. Nelze zadat jako součást deklaraci ukazatele (`decltype(auto*)`), odkaz na prohlášení (`decltype(auto&)`), nebo jakékoli jiné takové kvalifikace.  
  
## <a name="see-also"></a>Viz také  
 [auto](../../cpp/auto-cpp.md)