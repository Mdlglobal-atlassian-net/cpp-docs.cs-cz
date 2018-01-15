---
title: "underlying_type třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: type_traits/std::underlying_type
dev_langs: C++
helpviewer_keywords: underlying_type
ms.assetid: 691ddce3-2677-4480-bd35-d933fab85d3e
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8c345c6751ac962602a863d52addce2a7d4f0fcb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="underlyingtype-class"></a>underlying_type – třída
Vytvoří základní integrální typ pro typ výčtu.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>  
struct underlying_type;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ, který chcete upravit.  
  
## <a name="remarks"></a>Poznámky  
 `type` Typedef člena třídy šablony názvy základní integrální typ `T`, když `T` je typ výčtu jinak neexistuje žádné člen typedef `type`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<type_traits >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [<type_traits>](../standard-library/type-traits.md)



