---
title: "C2891 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2891
dev_langs: C++
helpviewer_keywords: C2891
ms.assetid: e12cfb2d-df45-4b0d-b155-c51d17e812fa
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6c35294472fe4142e7e6689adfc5f5f71c27b664
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2891"></a>C2891 chyby kompilátoru
"parametr": nelze převést na adresu parametr šablony  
  
 Adresa parametru šablony nelze provést, pokud se nejedná lvalue. Parametry typu nejsou hodnoty lvalue, protože mají žádnou adresu. Bez – typ hodnoty v seznamech parametr šablony, které nejsou hodnoty lvalue také nemají adresu. Toto je ukázkový kód, který způsobuje, že C2891 chyby kompilátoru, protože hodnota zadaná jako parametr šablony je kopii generované kompilátorem argumentu šablony.  
  
```  
template <int i> int* f() { return &i; }  
```  
  
 Parametry šablony, které jsou hodnoty lvalue, jako je například odkazové typy, můžete jeho adresu provedli.  
  
```  
template <int& r> int* f() { return &r; }  
```  
  
 Chcete-li tuto chybu, nepřebírají adresu parametr šablony Pokud se nejedná lvalue.