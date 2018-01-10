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
ms.workload: cplusplus
ms.openlocfilehash: 979d77ad5b5bd0b68dd539695d6cb1b60b099c55
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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