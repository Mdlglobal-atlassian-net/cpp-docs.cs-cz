---
title: "is_trivially_copy_assignable třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_copy_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_copy_assignable
ms.assetid: 7410133e-f367-493f-92a7-e34e3ec5e879
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c8fe1f72d609c30dbd7abf9fb0d0ca6803d90a29
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="istriviallycopyassignable-class"></a>is_trivially_copy_assignable Class
Ověřuje, zda má tento typ operátor přiřazení trivial kopírování.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Ty>
struct is_trivially_copy_assignable;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ, na který chcete odeslat dotaz.  
  
## <a name="remarks"></a>Poznámky  
 Instance predikátem typu obsahuje hodnotu true, pokud typ `T` je třída, která má trivial kopie operátor přiřazení, jinak má hodnotu false.  
  
 Přiřazení konstruktor pro třídu `T` je jednoduchá, pokud je implicitně poskytována, třída `T` nemá žádné virtuální funkce třídy `T` nemá žádné virtuální základů, mít trivial třídy všechny členy nestatické datového typu třídy operátory přiřazení a třídy všechny členy nestatické datové pole typu třídy mají operátory trivial přiřazení.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<type_traits >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [<type_traits>](../standard-library/type-traits.md)



