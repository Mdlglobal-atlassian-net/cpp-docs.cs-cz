---
title: _com_ptr_t::detach | Dokumentace Microsoftu
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
ms.openlocfilehash: cf38e433f7042707b502a4cba2088db9412adb29
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39405831"
---
# <a name="comptrtdetach"></a>_com_ptr_t::Detach
**Specifické pro Microsoft**  
  
 Extrahuje a vrátí zapouzdřený ukazatel rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Interface* Detach( ) throw( );  
```  
  
## <a name="remarks"></a>Poznámky  
 Extrahuje a vrátí zapouzdřený ukazatel rozhraní a poté vyčistí úložiště zapouzdřeného ukazatele na hodnotu NULL. Tím je ukazatel rozhraní vyjmut ze zapouzdření. Je na vás volat `Release` na Vrácený ukazatel rozhraní.  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také:  
 [_com_ptr_t – třída](../cpp/com-ptr-t-class.md)