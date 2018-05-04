---
title: _com_ptr_t::detach | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::Detach
dev_langs:
- C++
helpviewer_keywords:
- Detach method [C++]
ms.assetid: 0652053e-af37-44e9-a278-2522212ebfed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6fbe8fd203c3fda75e83aee623254676dacaf1da
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="comptrtdetach"></a>_com_ptr_t::Detach
**Konkrétní Microsoft**  
  
 Extrahuje a vrátí zapouzdřený ukazatel rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Interface* Detach( ) throw( );  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Extrahuje a vrátí ukazatel zapouzdřené rozhraní a pak vymaže obsah zapouzdřeného ukazatel úložiště **NULL**. Tím je ukazatel rozhraní vyjmut ze zapouzdření. Je na vás k volání **verze** na ukazatel vrácený rozhraní.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [_com_ptr_t – třída](../cpp/com-ptr-t-class.md)