---
title: "is_move_assignable třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_move_assignable
dev_langs: C++
helpviewer_keywords: is_move_assignable
ms.assetid: f33137f2-0639-4912-8745-bc0f9fd18d28
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9fba36cfb8b23a804a6851810294b54bf65c5055
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ismoveassignable-class"></a>is_move_assignable – třída
Testy, pokud typ lze přesunout přiřazené.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>
struct is_move_assignable;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ, na který chcete odeslat dotaz.  
  
## <a name="remarks"></a>Poznámky  
 Typ je přesunout přiřadit, pokud lze přiřadit deklarátor odkazu na typ odkaz na typ. Je ekvivalentní predikátem typu `is_assignable<T&, T&&>`. Přesuňte typy Přiřaditelné obsahují kde Skalární typy a typy tříd, které mají generované kompilátorem nebo uživatelsky definovaných přesunout operátory přiřazení.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<type_traits >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [<type_traits>](../standard-library/type-traits.md)



