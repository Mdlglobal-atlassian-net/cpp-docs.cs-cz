---
title: C3859 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3859
dev_langs:
- C++
helpviewer_keywords:
- C3859
ms.assetid: 40e93b25-4393-4467-90de-035434a665c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d2f8c51f25c09881e10e980276fc2035a6a70aed
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3859"></a>C3859 chyby kompilátoru
rozsah virtuální paměti pro PCH překročena; prosím znovu zkompiluje s možností příkazového řádku z '-Zmvalue' nebo vyšší  
  
 Předkompilované hlavičky je příliš malá pro množství dat, které kompilátor pokouší put v ní. Použití **/Zm** kompilátoru příznak k určení větší hodnotu předkompilovaný hlavičkový soubor. Další informace najdete v tématu [/Zm (zadat paměti omezení přidělení předkompilované hlavičky)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md).