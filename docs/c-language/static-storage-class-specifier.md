---
title: "statický specifikátor třídy úložiště | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- static variables, specifier
- storage classes, static
- static storage class specifiers
ms.assetid: 9bce361e-919b-46b9-8148-40d7ab0eb024
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c957b78eeb506e9f1f91a670cf5cc4d52ad72878
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="static-storage-class-specifier"></a>Statický specifikátor třídy úložiště
Proměnná definovaná na interní úrovni s **statické** – specifikátor třídy úložiště je globální doba platnosti, ale je viditelná pouze v rámci bloku v kterého je deklarovaná. Pro konstantní řetězce, pomocí **statické** je užitečné, protože ho nebude režii časté inicializace často říká funkcí.  
  
## <a name="remarks"></a>Poznámky  
Pokud není inicializaci explicitně **statické** proměnné, je inicializováno 0 ve výchozím nastavení. Uvnitř funkce **statické** způsobí, že úložiště přidělování a slouží jako definice. Vnitřní statické proměnné poskytují trvalé soukromé úložiště, které je viditelné pouze jedinou funkcí.  
  
## <a name="see-also"></a>Viz také  
[Třídy úložiště jazyka C](c-storage-classes.md)  
[Třídy úložiště (C++)](../cpp/storage-classes-cpp.md)  