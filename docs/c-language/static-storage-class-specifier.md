---
title: "statický specifikátor třídy úložiště | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- static variables, specifier
- storage classes, static
- static storage class specifiers
ms.assetid: 9bce361e-919b-46b9-8148-40d7ab0eb024
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0a51dfc10ac0ae05a67a280b4b76c2c92eb57a0b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="static-storage-class-specifier"></a>Statický specifikátor třídy úložiště
Proměnná definovaná na interní úrovni s **statické** – specifikátor třídy úložiště je globální doba platnosti, ale je viditelná pouze v rámci bloku v kterého je deklarovaná. Pro konstantní řetězce, pomocí **statické** je užitečné, protože ho nebude režii časté inicializace často říká funkcí.  
  
## <a name="remarks"></a>Poznámky  
Pokud není inicializaci explicitně **statické** proměnné, je inicializováno 0 ve výchozím nastavení. Uvnitř funkce **statické** způsobí, že úložiště přidělování a slouží jako definice. Vnitřní statické proměnné poskytují trvalé soukromé úložiště, které je viditelné pouze jedinou funkcí.  
  
## <a name="see-also"></a>Viz také  
[Třídy úložiště jazyka C](c-storage-classes.md)  
[Třídy úložiště (C++)](../cpp/storage-classes-cpp.md)  