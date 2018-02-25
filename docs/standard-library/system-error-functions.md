---
title: "&lt;system_error –&gt; funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- system_error/std::generic_category
- system_error/std::make_error_code
- system_error/std::make_error_condition
- system_error/std::system_category
ms.assetid: 57d6f15f-f0b7-4e2f-80fe-31d3c320ee33
caps.latest.revision: 
manager: ghogen
helpviewer_keywords:
- std::generic_category
- std::make_error_code
- std::make_error_condition
- std::system_category
ms.openlocfilehash: 78e39c11d58fddc6bc15d6c18257b43aa427b892
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="ltsystemerrorgt-functions"></a>&lt;system_error –&gt; funkce
||||  
|-|-|-|  
|[generic_category](#generic_category)|[make_error_code](#make_error_code)|[make_error_condition](#make_error_condition)|  
|[system_category](#system_category)|  
  
##  <a name="generic_category"></a>  generic_category  
 Představuje kategorii pro obecné chyby.  
  
```
extern const error_category& generic_category();
```  
  
### <a name="remarks"></a>Poznámky  
 `generic_category` Objektu je implementací [error_category](../standard-library/error-category-class.md).  
  
##  <a name="make_error_code"></a>  make_error_code –  
 Vytvoří objekt kódu chyby.  
  
```
error_code make_error_code(generic_errno _Errno);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`_Errno`|Hodnota výčtu ukládat v objektu, kód chyby.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Objekt, kód chyby.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="make_error_condition"></a>  make_error_condition –  
 Vytvoří objekt podmínku chyby.  
  
```
error_condition make_error_condition(generic_errno _Errno);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`_Errno`|Hodnota výčtu uložit do objektu podmínku chyby.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Objekt, podmínku chyby.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="system_category"></a>  system_category  
 Představuje kategorii pro chyby způsobené některé nízké úrovně systému.  
  
```
extern const error_category& system_category();
```  
  
### <a name="remarks"></a>Poznámky  
 `system_category` Objektu je implementací [error_category](../standard-library/error-category-class.md).  
  
## <a name="see-also"></a>Viz také  
 [<system_error>](../standard-library/system-error.md)



