---
title: "is_error_condition_enum – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: system_error/std::is_error_condition_enum
dev_langs: C++
helpviewer_keywords: is_error_condition_enum class
ms.assetid: 752bb87a-c61c-4304-9254-5aaf228b59c0
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d26913c9767f35c131605a8f7abee87396e753a2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="iserrorconditionenum-class"></a>is_error_condition_enum – třída
Představuje predikátem typu, který vyhledá [error_condition](../standard-library/error-condition-class.md) výčtu.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <_Enum>
class is_error_condition_enum;
```  
  
## <a name="remarks"></a>Poznámky  
 Instanci tohoto objektu [predikátem typu](../standard-library/type-traits.md) blokování hodnota true, pokud typ `_Enum` je vhodný pro ukládání do objektu typu hodnota výčtu `error_condition`.  
  
 Je přípustné, chcete-li přidat specializací na tento typ pro uživatelem definované typy.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<system_error – >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [< type_traits >](../standard-library/type-traits.md)   
 [< system_error – >](../standard-library/system-error.md)



