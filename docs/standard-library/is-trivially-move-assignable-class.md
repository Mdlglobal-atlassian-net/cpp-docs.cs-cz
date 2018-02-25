---
title: "is_trivially_move_assignable třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_move_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_move_assignable
ms.assetid: 374f7322-0706-4bc1-a1a5-4191d0315e28
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 32cfcd78cdc57e9ac0c238a3046d034d5d97f114
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="istriviallymoveassignable-class"></a>is_trivially_move_assignable – třída
Ověřuje, zda má tento typ operátor přiřazení přesunutí trivial.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Ty>
struct is_trivially_move_assignable;
```  
  
#### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ, na který chcete odeslat dotaz.  
  
## <a name="remarks"></a>Poznámky  
 Instance predikátem typu obsahuje hodnotu true, pokud typ `Ty` je třída, která má trivial přesunutí operátor přiřazení, jinak má hodnotu false.  
  
 Operátor přiřazení přesunutí pro třídu `Ty` je jednoduchá pokud:  
  
 implicitně je poskytována  
  
 Třída `Ty` nemá žádné virtuální funkce  
  
 Třída `Ty` nemá žádné virtuální základny  
  
 operátory přiřazení pro přesunutí trivial mít třídy všechny členy nestatické datového typu třídy  
  
 operátory přiřazení pro přesunutí trivial mít třídy všechny členy nestatické datové pole typu třídy  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<type_traits >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [<type_traits>](../standard-library/type-traits.md)



