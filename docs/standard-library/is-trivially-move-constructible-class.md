---
title: "is_trivially_move_constructible třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_move_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_move_constructible
ms.assetid: 740bdec7-65e5-47b3-b94f-a2479ceac3ec
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 17e564e89134a858eabf09b3f208461892da3fb3
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="istriviallymoveconstructible-class"></a>is_trivially_move_constructible – třída
Testy, pokud má typ trivial přesunout konstruktor.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Ty>
struct is_trivially_move_constructible;
```  
  
#### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ, na který chcete odeslat dotaz.  
  
## <a name="remarks"></a>Poznámky  
 Instance predikátem typu obsahuje hodnotu true, pokud typ `Ty` je třída, která má trivial konstruktor move, jinak má hodnotu false.  
  
 Konstruktor move pro třídu `Ty` je jednoduchá pokud:  
  
 implicitně je deklarovaná  
  
 jeho typy parametrů jsou rovnocenná implicitní deklarace  
  
 Třída `Ty` nemá žádné virtuální funkce  
  
 Třída `Ty` nemá žádné virtuální základny  
  
 Třída nemá žádné volatile nestatické datové členy  
  
 všechny přímo základny třídy `Ty` mít konstruktory trivial přesunutí  
  
 třídy všechny členy nestatické datového typu třídy mít konstruktory trivial přesunutí  
  
 třídy všechny členy nestatické datové pole typu třídy mít konstruktory trivial přesunutí  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<type_traits >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [<type_traits>](../standard-library/type-traits.md)



