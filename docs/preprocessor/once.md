---
title: Jakmile | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.once
- once_CPP
dev_langs: C++
helpviewer_keywords:
- once pragma
- pragmas, once
ms.assetid: c7517556-6403-4b16-8898-f2aa0a6f685f
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c04d411a6b0075d2fa08d846ad3b8a1bbb020c17
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="once"></a>once
Určuje, že soubor bude pomocí kompilátoru při kompilaci souboru zdrojového kódu obsažen (otevřen) pouze jednou.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
#pragma once  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Použití `#pragma once` může snížit dobu sestavení jako kompilátor nebude otevřít a přečíst soubor po první #include souboru v jednotce překlad. Tento proces se označuje jako *více zahrnují optimalizace*. Má podobný vliv *#include ochrana* stylu, které používá makro preprocesoru definice, aby více zahrnutí obsah souboru. To také pomáhá zabránit porušení *jednu definici pravidla*– požadavek na všechny šablony, typy, funkce a objekty mají více než jednu definici v kódu.  
  
 Příklad:  
  
```  
// header.h  
#pragma once  
// Code placed here is included only once per translation unit  
  
```  
  
 Doporučujeme, abyste `#pragma once` direktivy pro nový kód, protože není znečištění směrovány správu globálního oboru názvů s symbol preprocesoru. Vyžaduje méně zadáte, je méně rušivě a nemohou způsobit kolizí symbol – chyb vzniklých při různých hlavičkových souborů pomocí stejné symbol preprocesoru jako hodnota ochrana. Není součástí standardní C++, ale jeho přenositelnosti implementované několik běžných kompilátory.  
  
 Neexistuje žádné výhody použít i #include ochrana stylu a `#pragma once` ve stejném souboru. Kompilátor rozpozná #include ochrana stylu a implementuje násobek zahrnují optimalizace, stejně jako `#pragma once` – direktiva, pokud žádný jiný komentář kódu nebo direktivy preprocesoru pochází před nebo po standardní formu stylu:  
  
```  
// header.h  
// Demonstration of the #include guard idiom.  
// Note that the defined symbol can be arbitrary.  
#ifndef HEADER_H_     // equivalently, #if !defined HEADER_H_  
#define HEADER_H_  
// Code placed here is included only once per translation unit  
#endif // HEADER_H_  
  
```  
  
 Doporučujeme #include ochrana stylu při kód musí být přenosný na kompilátory, které neimplementují `#pragma once` – direktiva, můžete zachovat konzistenci stávající kód, nebo když zahrnují více optimalizace není možné. Tato situace může nastat v projektech komplexní při vytváření aliasů systému souborů nebo alias patří cesty zabránit kompilátoru z identifikace identické vložené soubory kanonický cestou.  
  
 Dejte pozor, abyste používat `#pragma once` nebo #include ochrana stylu hlavičky souborů, které jsou navržené jako zahrnuta vícekrát, používání preprocesoru symboly k řízení jejich důsledky. Příklad tohoto návrhu v tématu \<assert.h > soubor hlaviček. Také je potřeba spravovat zahrnout cesty, kde se vyhněte se vytváření více cest k zahrnuté soubory, které můžete vůbec nemělo více zahrnují optimalizace pro obě #include chrání a `#pragma once`.  
  
## <a name="see-also"></a>Viz také  
 [Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)