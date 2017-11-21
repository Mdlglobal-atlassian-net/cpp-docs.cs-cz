---
title: "C3859 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3859
dev_langs: C++
helpviewer_keywords: C3859
ms.assetid: 40e93b25-4393-4467-90de-035434a665c7
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8a132eb7dbf09421ad5c99249b0208e5f901156b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3859"></a>C3859 chyby kompilátoru
rozsah virtuální paměti pro PCH překročena; prosím znovu zkompiluje s možností příkazového řádku z '-Zmvalue' nebo vyšší  
  
 Předkompilované hlavičky je příliš malá pro množství dat, které kompilátor pokouší put v ní. Použití **/Zm** kompilátoru příznak k určení větší hodnotu předkompilovaný hlavičkový soubor. Další informace najdete v tématu [/Zm (zadat paměti omezení přidělení předkompilované hlavičky)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md).