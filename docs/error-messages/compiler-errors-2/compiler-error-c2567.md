---
title: "C2567 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2567
dev_langs: C++
helpviewer_keywords: C2567
ms.assetid: 9c140ac9-7059-47e6-9ba1-e7939c8c0dc3
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1bbdc535f75230da05a92eb0498176da40e918ea
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2567"></a>C2567 chyby kompilátoru
Nelze otevřít metadata v 'file', soubor může byly odstraněny nebo přesunuty  
  
 Soubor metadat, který se odkazuje ve zdroji (s `#using`) nebyl nalezen ve stejném adresáři proces kompilátoru back-end, jako byl proces front-endu kompilátoru. V tématu [#using – direktiva](../../preprocessor/hash-using-directive-cpp.md) Další informace.  
  
 C2567 může dojít, když kompilujete s **/c** na jednom počítači a pokusíte se generování kódu v době propojování na jiném počítači. Další informace najdete v tématu [/ltgc (vytváření kódu v době propojování)](../../build/reference/ltcg-link-time-code-generation.md)).  
  
 Také může znamenat, že váš počítač měl žádná další paměť.  
  
 Chcete-li tuto chybu, ujistěte se, že soubor metadat je ve stejném umístění adresáře pro všechny fáze procesu sestavení.