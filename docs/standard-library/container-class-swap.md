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
ms.openlocfilehash: 13d083c596dcbaa275ed8d0f05ded2c5cb5547eb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
