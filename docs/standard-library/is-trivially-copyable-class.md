---
title: "is_trivially_copyable třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: type_traits/std::is_trivially_copyable
dev_langs: C++
helpviewer_keywords: is_trivially_copyable
ms.assetid: 89a53bf8-036c-4108-91e1-fe34adbde8b3
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c6f3cf5f6ca0fc6168c061df2ec276f058abea51
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="istriviallycopyable-class"></a>is_trivially_copyable – třída
Ověřuje, zda je typ trivially kopírovatelná typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>
struct is_trivially_copyable;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ, na který chcete odeslat dotaz.  
  
## <a name="remarks"></a>Poznámky  
 Instance predikátem typu obsahuje hodnotu true, pokud typ `T` trivially kopírovatelná typu, jinak má hodnotu false. Trivially kopírovatelná typy mít žádné operace netriviální kopírování, operace přesunutí nebo destruktory. Obecně platí operace kopírování se považuje za trivial, pokud se dá implementovat jako bitové kopie. Vestavěné typy a pole trivially kopírovatelná typů jsou trivially kopírovatelná.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<type_traits >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [<type_traits>](../standard-library/type-traits.md)



