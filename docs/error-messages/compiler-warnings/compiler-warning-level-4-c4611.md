---
title: Kompilátoru (úroveň 4) upozornění C4611 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4611
dev_langs:
- C++
helpviewer_keywords:
- C4611
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5946c10b5e0e0e7e08f1ee37c77120896937adb1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293150"
---
# <a name="compiler-warning-level-4-c4611"></a>C4611 kompilátoru upozornění (úroveň 4)
interakce mezi 'function' a odstraňování objektů C++ je jiný přenositelností  
  
 Na některých platformách, funkce, které obsahují **catch** nemusí podporovat sémantiku objekt C++ odstranění, když jsou mimo rozsah.  
  
 Chcete-li se neočekávanému chování vyhnout, nepoužívejte **catch** v funkce, které mají konstruktory a destruktory.  
  
 Se objeví toto upozornění pouze jednou; v tématu [– Direktiva pragma upozornění](../../preprocessor/warning.md).