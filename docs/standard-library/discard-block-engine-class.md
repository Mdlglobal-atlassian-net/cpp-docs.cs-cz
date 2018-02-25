---
title: "discard_block_engine – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- random/std::discard_block_engine
dev_langs:
- C++
helpviewer_keywords:
- discard_block_engine class
ms.assetid: aa84808e-38fe-4fa0-9f73-d5b9a653345b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 89cfd599f1f51c70f2e4ac108b32ccbe8bc6ae68
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="discardblockengine-class"></a>discard_block_engine – třída
Generuje náhodné pořadí zrušením hodnot vrácených jeho základní modul.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class Engine, size_t P, size_t R>  
class discard_block_engine;  
```  
  
#### <a name="parameters"></a>Parametry  
 `Engine`  
 Typ základního modulu.  
  
 `P`  
 **Velikost bloku**. Počet hodnot v jednotlivých bloků.  
  
 `R`  
 **Použít bloku**. Počet hodnot v jednotlivých bloků, které se používají. Ostatní jsou zahozeny ( `P`  -  `R`). **Předběžnou**: `0 < R ≤ P`  
  
## <a name="members"></a>Členové  
  
||||  
|-|-|-|  
|`discard_block_engine::discard_block_engine`|`discard_block_engine::base`|`discard_block_engine::discard`|  
|`discard_block_engine::operator()`|`discard_block_engine::base_type`|`discard_block_engine::seed`|  
  
 Další informace o modulu členy najdete v tématu [ \<náhodných >](../standard-library/random.md).  
  
## <a name="remarks"></a>Poznámky  
 Tato třída šablony Popisuje modul adaptér, který produkuje hodnoty zrušením některé z hodnot vrácených jeho základní modul.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<náhodných >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [\<random>](../standard-library/random.md)

