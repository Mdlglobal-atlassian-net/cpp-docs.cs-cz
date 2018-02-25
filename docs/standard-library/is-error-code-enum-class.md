---
title: "is_error_code_enum – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- system_error/std::is_error_code_enum
dev_langs:
- C++
helpviewer_keywords:
- is_error_code_enum class
ms.assetid: cee5be2d-7c20-4cec-a352-1ab8b7d32601
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5c7eb2de5bf2669f7833fffb8003ee1f0886c4bf
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="iserrorcodeenum-class"></a>is_error_code_enum – třída
Představuje predikátem typu, který vyhledá [error_code](../standard-library/error-code-class.md) výčtu.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <_Enum>
class is_error_code_enum;
```  
  
## <a name="remarks"></a>Poznámky  
 Instanci tohoto objektu [predikátem typu](../standard-library/type-traits.md) blokování hodnota true, pokud typ `_Enum` je vhodný pro ukládání do objektu typu hodnota výčtu `error_code`.  
  
 Je přípustné, chcete-li přidat specializací na tento typ pro uživatelem definované typy.  
  
## <a name="requirements"></a>Požadavky  
 **Header:** \<system_error>  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [<type_traits>](../standard-library/type-traits.md)   
 [<system_error>](../standard-library/system-error.md)



