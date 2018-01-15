---
title: "type_index – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: typeindex/std::type_index
dev_langs: C++
helpviewer_keywords: type_index class
ms.assetid: db366119-74cb-43e8-aacf-9679e561fa2f
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e27a626a7371c0358f05c49b33d0a9c1a019e72e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="typeindex-class"></a>type_index – třída
`type_index` Třída zabalí ukazatel na [type_info – třída](../cpp/type-info-class.md) pomoct indexování tyto objekty.  
  
type_index – třída {veřejné: type_index (const type_info & tinfo); const char *name() const; size_t – hash_code() const; bool – operátor == (const type_info & doprava) const; bool – operátor! = (const type_info & doprava) const; <(const type_ bool – operátor informace o & doprava) const; BOOL – operátor\<= (const type_info & doprava) const; bool – operátor > (const type_info & doprava) const; bool – operátor > = (const type_info & doprava) const;};  
  
 Konstruktor inicializuje `ptr` k `&tinfo`.  
  
 `name`Vrátí `ptr->name()`.  
  
 `hash_code`Vrátí`ptr->hash_code().`  
  
 `operator==`Vrátí `*ptr == right.ptr`.  
  
 `operator!=`Vrátí `!(*this == right)`.  
  
 `operator<`Vrátí `*ptr->before(*right.ptr)`.  
  
 `operator<=`Vrátí`!(right < *this).`  
  
 `operator>`Vrátí `right < *this`.  
  
 `operator>=`Vrátí `!(*this < right)`.  
  
## <a name="see-also"></a>Viz také  
 [Informace běhového typu](../cpp/run-time-type-information.md)   
 [\<typeindex >](../standard-library/typeindex.md)



