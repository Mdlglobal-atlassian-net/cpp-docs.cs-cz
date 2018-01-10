---
title: "is_trivially_default_constructible – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_trivially_default_constructible
dev_langs: C++
helpviewer_keywords: is_trivially_default_constructible
ms.assetid: 653ecd73-909f-4dd8-b95a-d1164d1c2da4
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6b936e6cfa3557591a5be9ec2cafda36920039c3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="istriviallydefaultconstructible-class"></a>is_trivially_default_constructible – třída
Testy, pokud má typ trivial výchozí konstruktor.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Ty>
struct is_trivially_default_constructible;
```  
  
#### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ, na který chcete odeslat dotaz.  
  
## <a name="remarks"></a>Poznámky  
 Instance predikátem typu obsahuje hodnotu true, pokud typ `Ty` je třída, která má triviálního konstruktoru, jinak má hodnotu false.  
  
 Výchozí konstruktor pro třídu `Ty` je jednoduchá pokud:  
  
-   je implicitně deklarované výchozí konstruktor  
  
-   Třída `Ty` nemá žádné virtuální funkce  
  
-   Třída `Ty` nemá žádné virtuální základny  
  
-   všechny přímo základny třídy `Ty` mít trivial konstruktory  
  
-   třídy všech členů nestatické datového typu třídy mají trivial konstruktory  
  
-   třídy všech členů nestatické datové pole typu třídy mají trivial konstruktory  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<type_traits >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [<type_traits>](../standard-library/type-traits.md)



