---
title: statický specifikátor třídy úložiště | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- static variables, specifier
- storage classes, static
- static storage class specifiers
ms.assetid: 9bce361e-919b-46b9-8148-40d7ab0eb024
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8a7d61e39eb706721ddf936f88f5df02a6eddf96
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32386313"
---
# <a name="static-storage-class-specifier"></a>Statický specifikátor třídy úložiště
Proměnná definovaná na interní úrovni s **statické** – specifikátor třídy úložiště je globální doba platnosti, ale je viditelná pouze v rámci bloku v kterého je deklarovaná. Pro konstantní řetězce, pomocí **statické** je užitečné, protože ho nebude režii časté inicializace často říká funkcí.  
  
## <a name="remarks"></a>Poznámky  
Pokud není inicializaci explicitně **statické** proměnné, je inicializováno 0 ve výchozím nastavení. Uvnitř funkce **statické** způsobí, že úložiště přidělování a slouží jako definice. Vnitřní statické proměnné poskytují trvalé soukromé úložiště, které je viditelné pouze jedinou funkcí.  
  
## <a name="see-also"></a>Viz také  
[Třídy úložiště jazyka C](c-storage-classes.md)  
[Třídy úložiště (C++)](../cpp/storage-classes-cpp.md)  