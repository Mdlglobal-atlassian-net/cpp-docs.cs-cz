---
title: "Třída kontejneru::swap | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: swap method
ms.assetid: 898c219c-bc8e-4d14-a149-6240426c693f
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 09229429c64e895a722d52d203f0259cf69e6d24
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="container-classswap"></a>Třída kontejneru::swap
> [!NOTE]
>  Toto téma se v dokumentaci k Visual C++ jako funkční příklad kontejnery použít ve standardní knihovně C++. Další informace najdete v tématu [kontejnery standardní knihovny C++](../standard-library/stl-containers.md).  
  
Prohození řízené pořadí mezi  **\*to** a jeho argumentem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void swap(Container& right);
```  
  
## <a name="remarks"></a>Poznámky  
Pokud  **\*this.get\_allocator ==** _správné_**.get_allocator**, provede prohození konstantní včas. Jinak provede několik element přiřazení a volá konstruktor úměrná počet elementů ve dvou řízené pořadí.  
  
## <a name="see-also"></a>Viz také  
[Ukázkový kontejner – třída](../standard-library/sample-container-class.md)
