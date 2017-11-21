---
title: "Bezpečnost vlákna v standardní knihovně C++ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- thread safety
- C++ Standard Library, thread safety
- thread safety, C++ Standard Library
ms.assetid: 9351c8fb-4539-4728-b0e9-226e2ac4284b
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a30ad3887ace197276556aab929a7d16ae7922e1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="thread-safety-in-the-c-standard-library"></a>Bezpečný přístup z více vláken ve standardní knihovně C++
Platí následující pravidla bezpečný přístup z více vláken na všechny třídy v standardní knihovna C++ – to zahrnuje `shared_ptr`, jak je popsáno níže.  Někdy jsou k dispozici větší záruku – například standardní iostream objekty, jak je popsáno níže a typy určený speciálně pro více vláken, jako jsou ty v [ \<atomic >](../standard-library/atomic.md).  
  
 Objekt je bezpečné pro přístup z více vláken pro čtení z více vláken. Například zadána objekt A je bezpečné číst A z vlákna 1 a z vlákna 2 současně.  
  
 Pokud objekt zapisuje jedním vláknem, pak všechny čte a zapisuje tento objekt na stejné nebo jiná vlákna musí být chráněny. Například zadána objekt A, pokud se o přístup z více vláken 1 zápis A pak vlákno 2, musí být zabránit čtení nebo zápisu do A.  
  
 Je bezpečné číst a zapisovat do jedné instance typu i v případě jiné vlákno je čtení nebo zápisu do jiné instance stejného typu. Například zadané objekty A a B stejného typu, je bezpečné při ve vláknu 1 probíhá zápis A a B je načítán ve vláknu 2.  
  
## <a name="sharedptr"></a>shared_ptr  
 Více vláken současně může číst a zapisovat jiné [shared_ptr](../standard-library/shared-ptr-class.md) objekty, i když jsou tyto objekty kopií, které sdílejí vlastnictví.  
  
## <a name="iostream"></a>iostream  
 Objekty standardní iostream `cin`, `cout`, `cerr`, `clog`, `wcin`, `wcout`, `wcerr`, a `wclog` stejným pravidlům jako jiné třídy, se tato výjimka: je bezpečné zápis do objektu z více vláken. Například může vlákno 1 zapsat do [cout](../standard-library/iostream.md#cout) ve stejnou dobu jako vláken 2. Ale to může způsobit výstup z dvěma vlákny na být Smíšeného.  
  
> [!NOTE]
>  Čtení z datového proudu vyrovnávací paměti se nepovažuje za operace čtení. Místo toho považuje za operaci zápisu, protože se změnil stav třídy.  
  
## <a name="see-also"></a>Viz také  
 [Přehled knihovny C++ Standard](../standard-library/cpp-standard-library-overview.md)



