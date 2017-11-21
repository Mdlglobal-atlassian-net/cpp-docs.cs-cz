---
title: "alignment_of – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::alignment_of
dev_langs: C++
helpviewer_keywords:
- alignment_of class
- alignment_of
ms.assetid: 4141c59a-f94e-41c4-93fd-9ea578b27387
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2e20d01c50ea743f62c1cca9e45eedd86a5d4b8c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="alignmentof-class"></a>alignment_of – třída
Získá zarovnání zadaného typu. Tato struktura je implementována z hlediska [alignof](../cpp/alignof-and-alignas-cpp.md). Použití `alignof` přímo při jednoduše je potřeba zadat dotaz na hodnotu zarovnání. Alignment_of používejte, když potřebujete integrální konstanta, například při provádění odesílání značky.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Ty>
struct alignment_of;
```  
  
#### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ, na který chcete odeslat dotaz.  
  
## <a name="remarks"></a>Poznámky  
 Typ dotazu obsahuje hodnotu zarovnání typu `Ty`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<type_traits >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [< type_traits >](../standard-library/type-traits.md)   
 [aligned_storage – třída](../standard-library/aligned-storage-class.md)
