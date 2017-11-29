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
ms.openlocfilehash: abcafb8f94265d14a609481a187dcc53267718d3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 [Standardní C++ – referenční dokumentace knihoven](../standard-library/cpp-standard-library-reference.md)


