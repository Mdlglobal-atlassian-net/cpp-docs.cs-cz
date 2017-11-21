---
title: "forward_iterator_tag – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xutility/std::forward_iterator_tag
dev_langs: C++
helpviewer_keywords:
- forward_iterator_tag struct
- forward_iterator_tag class
ms.assetid: 68b633ac-b135-4e9e-837d-14248a262ec5
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2a6d48940faf4645421a863411058ebfce1949aa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="forwarditeratortag-struct"></a>forward_iterator_tag – struktura
Třídu, která poskytuje návratový typ pro **iterator_category –** funkce, která představuje dopředného iterator.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct forward_iterator_tag    : public input_iterator_tag {};
```  
  
## <a name="remarks"></a>Poznámky  
 Třídy značky kategorie se používají jako zkompilovat značky pro výběr algoritmů. Funkce šablony musí zjistit, co nejvíce určitou kategorii její argument iterator tak, aby v době kompilace může použít algoritmus maximální efektivitou. Pro každý iterator typu `Iterator`, `iterator_traits` <  `Iterator` >  **:: iterator_category –** musí být definován jako nejvíce značky kategorii, která popisuje iteraci chování.  
  
 Typ je stejný jako **iterator** \< **Iter**> **:: iterator_category –** při **Iter** popisuje objekt, který může sloužit jako dopředného iterator.  
  
## <a name="example"></a>Příklad  
 V tématu [iterator_traits –](../standard-library/iterator-traits-struct.md) nebo [random_access_iterator_tag –](../standard-library/random-access-iterator-tag-struct.md) příklad použití **iterator_tag**s.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<iterator >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [input_iterator_tag – struktura](../standard-library/input-iterator-tag-struct.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Standardní C++ – referenční dokumentace knihoven](../standard-library/cpp-standard-library-reference.md)



