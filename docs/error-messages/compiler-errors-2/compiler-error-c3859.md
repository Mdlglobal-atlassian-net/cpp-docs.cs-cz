---
title: "C3859 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3859
dev_langs:
- C++
helpviewer_keywords:
- C3859
ms.assetid: 40e93b25-4393-4467-90de-035434a665c7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d3a240771c0b2e104ef7c51b187d4040500edaae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3859"></a>C3859 chyby kompilátoru
rozsah virtuální paměti pro PCH překročena; prosím znovu zkompiluje s možností příkazového řádku z '-Zmvalue' nebo vyšší  
  
 Předkompilované hlavičky je příliš malá pro množství dat, které kompilátor pokouší put v ní. Použití **/Zm** kompilátoru příznak k určení větší hodnotu předkompilovaný hlavičkový soubor. Další informace najdete v tématu [/Zm (zadat paměti omezení přidělení předkompilované hlavičky)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md).