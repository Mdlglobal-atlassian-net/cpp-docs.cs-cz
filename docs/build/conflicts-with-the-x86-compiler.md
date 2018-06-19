---
title: Je v konfliktu s x86 kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8e47f0d3-afe0-42d9-9efa-de239ddd3a05
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7cd72de4922c297b4a230e0dc0fb606b56a2a473
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366910"
---
# <a name="conflicts-with-the-x86-compiler"></a>Konflikty s kompilátorem x86
Datové typy, které jsou větší než 4 bajtů nejsou zarovnány automaticky v zásobníku při použití x86 kompilátoru ke kompilaci aplikace. Protože architektura x86 kompilátoru je zarovnaný zásobníku 4bajtové, nic větší než 4 bajtů, například 64bitové celé číslo, nemůže být automaticky zarovnáno na adresu 8 bajtů.  
  
 Práce s nezarovnanými daty má dva důsledky.  
  
-   Může trvat déle než trvá pro přístup k umístění zarovnaný přístup nezarovnané umístění.  
  
-   Nezarovnané umístění nelze použít v propojené operace.  
  
 Pokud požadujete více přísné zarovnání, použijte `__declspec(align(N)) on your variable declarations`. To způsobí, že kompilátor dynamicky zarovná zásobník, aby splňovaly vaše požadavky. Dynamické nastavení zásobníku v době běhu může způsobit pomalejší provádění aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Typy a úložiště](../build/types-and-storage.md)   
 [align](../cpp/align-cpp.md)