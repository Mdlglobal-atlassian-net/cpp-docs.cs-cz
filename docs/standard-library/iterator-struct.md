---
title: "iterator – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xutility/std::iterator
dev_langs: C++
helpviewer_keywords:
- iterator class
- iterator struct
ms.assetid: c74c8000-8b18-4829-9b71-6103c4229b74
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 689ec4ab19b2e5079c31ab0a8677d25acf4e8899
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="iterator-struct"></a>iterator – struktura
Prázdný základní struktura, která používá k zajištění, že třídu uživatelem definované iterator správně funguje s **iterator_trait**s.  
  
## <a name="syntax"></a>Syntaxe  
```    
struct iterator {
   typedef Category iterator_category;
   typedef Type value_type;
   typedef Distance difference_type;
   typedef Distance distance_type;
   typedef Pointer pointer;
   typedef Reference reference;
   };  
```    
## <a name="remarks"></a>Poznámky  
 Šablona struktura slouží jako základní typ pro všechny iterátory. Definuje typy členů  
  
- `iterator_category`(synonymum pro parametr šablony `Category`).  
  
- `value_type`(synonymum pro parametr šablony **typu**).  
  
- `difference_type`(synonymum pro parametr šablony `Distance`).  
  
- `distance_type`(synonymum pro parametr šablony `Distance`)  
  
- `pointer`(synonymum pro parametr šablony `Pointer`).  
  
- `reference`(synonymum pro parametr šablony `Reference`).  
  
 Všimněte si, že `value_type` nesmí být typu konstanty. i když **ukazatel** bodů v objektu const **typ** a označí odkaz na objekt const **typu**.  
  
## <a name="example"></a>Příklad  
 V tématu [iterator_traits –](../standard-library/iterator-traits-struct.md) příklad toho, jak deklarování a použití typů v základní třídě iterator.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<iterator >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [\<iterator >](../standard-library/iterator.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)



