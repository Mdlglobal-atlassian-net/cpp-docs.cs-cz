---
title: C2567 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2567
dev_langs:
- C++
helpviewer_keywords:
- C2567
ms.assetid: 9c140ac9-7059-47e6-9ba1-e7939c8c0dc3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 05f89362f36a6ba576e9829153f0d8931c4975c6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33229686"
---
# <a name="compiler-error-c2567"></a>C2567 chyby kompilátoru
Nelze otevřít metadata v 'file', soubor může byly odstraněny nebo přesunuty  
  
 Soubor metadat, který se odkazuje ve zdroji (s `#using`) nebyl nalezen ve stejném adresáři proces kompilátoru back-end, jako byl proces front-endu kompilátoru. V tématu [#using – direktiva](../../preprocessor/hash-using-directive-cpp.md) Další informace.  
  
 C2567 může dojít, když kompilujete s **/c** na jednom počítači a pokusíte se generování kódu v době propojování na jiném počítači. Další informace najdete v tématu [/ltgc (vytváření kódu v době propojování)](../../build/reference/ltcg-link-time-code-generation.md)).  
  
 Také může znamenat, že váš počítač měl žádná další paměť.  
  
 Chcete-li tuto chybu, ujistěte se, že soubor metadat je ve stejném umístění adresáře pro všechny fáze procesu sestavení.