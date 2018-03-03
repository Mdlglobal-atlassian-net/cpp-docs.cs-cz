---
title: "Správa paměti: Přidělení haldy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- memory [MFC], detecting leaks
- delete operator [MFC], using with debug MFC
- heap allocation [MFC], described
- memory allocation [MFC], heap memory
- memory leaks [MFC], detecting
- new operator [MFC], using with debug MFC
- heap allocation [MFC]
- detecting memory leaks [MFC]
ms.assetid: a5d949c6-1b79-476e-9c66-513a558203d9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 34fbb82a28c145ad2d376f0647fbd75faeb9401c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="memory-management-heap-allocation"></a>Správa paměti: Přidělení haldy
Halda je vyhrazená pro potřeby přidělení paměti programu. Je oblast kromě kód programu a zásobníku. Typické programy C použít funkce `malloc` a **volné** a přidělit paměť haldy navrácení. Ladicí verze knihovny MFC poskytuje upravené verze předdefinované operátory jazyka C++ **nové** a **odstranit** a přidělit navrácení objekty v halda paměti.  
  
 Při použití **nové** a **odstranit** místo `malloc` a **volné**, budete moci využít ladění vylepšení správy paměti knihovny tříd , což může být užitečné při zjišťování nevracení paměti. Při vytváření váš program s prodejní verze knihovny MFC, standardní verze **nové** a **odstranit** operátory poskytovat účinný způsob alokace a zrušit přidělení paměti (prodejní verze knihovny MFC neposkytuje upravené verze těchto operátorů).  
  
 Všimněte si, že je celková velikost objekty přidělené v haldě omezena pouze dostupné virtuální paměti systému.  
  
## <a name="see-also"></a>Viz také  
 [Správa paměti](../mfc/memory-management.md)

