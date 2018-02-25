---
title: "is_nothrow_default_constructible – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::is_nothrow_default_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_default_constructible
ms.assetid: c576fcc9-5be1-43aa-b93a-64d3f1848887
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f113e293ea71b6fa60e48091e3b81dbe92554e96
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="isnothrowdefaultconstructible-class"></a>is_nothrow_default_constructible – třída
Ověřuje, zda má typ výchozí konstruktor není aktivována.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Ty>
struct is_nothrow_default_constructible;
```  
  
#### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ, na který chcete odeslat dotaz.  
  
## <a name="remarks"></a>Poznámky  
 Instance predikátem typu obsahuje hodnotu true, pokud typ `Ty` má nothrow výchozí konstruktor, jinak má hodnotu false. Instance typu predikátu je ekvivalentní `is_nothrow_constructible<Ty>`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<type_traits >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [<type_traits>](../standard-library/type-traits.md)



