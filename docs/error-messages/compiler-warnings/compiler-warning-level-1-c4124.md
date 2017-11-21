---
title: "Kompilátoru (úroveň 1) upozornění C4124 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4124
dev_langs: C++
helpviewer_keywords: C4124
ms.assetid: c08c3a65-9584-47a1-a147-44f00c4b230e
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3de13cb50444530fc0917330771b693f60a7e5f5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4124"></a>C4124 kompilátoru upozornění (úroveň 1)
__fastcall s povolenou kontrolou zásobníku je neefektivní  
  
 `__fastcall` – Klíčové slovo se použila se kontrola zásobníku povolené.  
  
 `__fastcall` Konvence generuje kód rychlejší, ale zásobník kontrola způsobí, že pomalejší kód. Při použití `__fastcall`, zásobník kontrolu s vypnout **check_stack –** – Direktiva pragma nebo /Gs.  
  
 Jenom pro první funkce deklarovaný za těchto podmínek se objeví toto upozornění.