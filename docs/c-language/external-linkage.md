---
title: Externí propojení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- linkage [C++], external
- external linkage, about external linkage
- external linkage
ms.assetid: a6f8ea69-b405-4cdd-bf12-ad5462b73183
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 43301686d5bdb964cf08e8123ff4c55475228567
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="external-linkage"></a>Externí propojení
Pokud první deklaraci na úrovni souboru rozsah pro identifikátor nepoužívá **statické** specifikátor třídy úložiště, objekt má externí propojení.  
  
 Pokud deklarace identifikátoru pro funkci neobsahuje žádné *specifikátor třídy úložiště*, jeho propojení je určeno přesně, jako kdyby byly deklarovat s *specifikátor třídy úložiště* `extern`. Pokud deklarace identifikátoru objektu obsahuje rozsah souboru a neexistuje žádný *specifikátor třídy úložiště*, jeho propojení je externí.  
  
 Název identifikátoru s vnějším propojením na stejnou funkci nebo objekt dat provádí ostatní deklarace pro stejný název pomocí vnějšího propojení. Ve stejné jednotce překladu nebo v různých jednotkách překladu mohou být dvě deklarace. Pokud má objekt nebo funkce také globální životnost, jsou funkce nebo objekt sdíleny napříč celým programem.  
  
## <a name="see-also"></a>Viz také  
 [Používání příkazu extern pro specifikaci propojení](../cpp/using-extern-to-specify-linkage.md)