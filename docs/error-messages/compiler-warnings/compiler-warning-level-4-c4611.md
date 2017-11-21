---
title: "Kompilátoru (úroveň 4) upozornění C4611 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4611
dev_langs: C++
helpviewer_keywords: C4611
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8f2ed128d37ff4c09247097d771bc62a97f6e757
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4611"></a>C4611 kompilátoru upozornění (úroveň 4)
interakce mezi 'function' a odstraňování objektů C++ je jiný přenositelností  
  
 Na některých platformách, funkce, které obsahují **catch** nemusí podporovat sémantiku objekt C++ odstranění, když jsou mimo rozsah.  
  
 Chcete-li se neočekávanému chování vyhnout, nepoužívejte **catch** v funkce, které mají konstruktory a destruktory.  
  
 Se objeví toto upozornění pouze jednou; v tématu [– Direktiva pragma upozornění](../../preprocessor/warning.md).