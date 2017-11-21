---
title: "is_trivially_move_assignable třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_trivially_move_assignable
dev_langs: C++
helpviewer_keywords: is_trivially_move_assignable
ms.assetid: 374f7322-0706-4bc1-a1a5-4191d0315e28
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 078d138126a432e3be0c2709b4ae351f2383ae44
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 [< type_traits >](../standard-library/type-traits.md)



