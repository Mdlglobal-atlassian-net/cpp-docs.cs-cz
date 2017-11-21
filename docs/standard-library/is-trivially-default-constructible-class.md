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
ms.openlocfilehash: a7c72fea2e3efeb877faf6803c13338017dbd7d8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 [< type_traits >](../standard-library/type-traits.md)



