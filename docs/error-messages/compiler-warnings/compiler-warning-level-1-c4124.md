---
title: Kompilátoru (úroveň 1) upozornění C4124 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4124
dev_langs:
- C++
helpviewer_keywords:
- C4124
ms.assetid: c08c3a65-9584-47a1-a147-44f00c4b230e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: accd58c123bcd74e54176eed5eb974c3df33dbab
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4124"></a>C4124 kompilátoru upozornění (úroveň 1)
__fastcall s povolenou kontrolou zásobníku je neefektivní  
  
 `__fastcall` – Klíčové slovo se použila se kontrola zásobníku povolené.  
  
 `__fastcall` Konvence generuje kód rychlejší, ale zásobník kontrola způsobí, že pomalejší kód. Při použití `__fastcall`, zásobník kontrolu s vypnout **check_stack –** – Direktiva pragma nebo /Gs.  
  
 Jenom pro první funkce deklarovaný za těchto podmínek se objeví toto upozornění.