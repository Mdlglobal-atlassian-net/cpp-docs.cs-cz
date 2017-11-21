---
title: "atomic_flag – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- atomic/std::atomic_flag
- atomic/std::atomic_flag::clear
- atomic/std::atomic_flag::test_and_set
dev_langs: C++
ms.assetid: 17f0c2f5-fd39-4a44-873a-b569720a670e
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cdc475e674a1316f5e1441adadb6add65a52df5c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="atomicflag-structure"></a>atomic_flag – struktura
Popisuje, objektu, která atomicky nastaví a vymaže `bool` příznak. Operace na atomic příznaky jsou vždy bez zámku.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct atomic_flag;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Vymazat](#clear)|Nastaví příznak uložené na `false`.|  
|[test_and_set](#test_and_set)|Nastaví příznak uložené na `true` a vrátí hodnotu počáteční příznak.|  
  
## <a name="remarks"></a>Poznámky  
 `atomic_flag`objekty lze předat jiné členské funkce [atomic_flag_clear –](../standard-library/atomic-functions.md#atomic_flag_clear), [atomic_flag_clear_explicit –](../standard-library/atomic-functions.md#atomic_flag_clear_explicit), [atomic_flag_test_and_set –](../standard-library/atomic-functions.md#atomic_flag_test_and_set), a [ atomic_flag_test_and_set_explicit –](../standard-library/atomic-functions.md#atomic_flag_test_and_set_explicit). Může být inicializovat pomocí hodnoty `ATOMIC_FLAG_INIT`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<atomic >  
  
 **Namespace:** – std  
  
##  <a name="clear"></a>atomic_flag::clear –
 Nastaví `bool` příznak, který je uložen v `*this` k `false`, v rámci zadaného [memory_order –](../standard-library/atomic-enums.md#memory_order_enum) omezení.  
  
```
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) volatile noexcept;
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Order`  
 A [memory_order –](../standard-library/atomic-enums.md#memory_order_enum).  
  
##  <a name="test_and_set"></a>atomic_flag::test_and_set –
 Nastaví `bool` příznak, který je uložen v `*this` k `true`, v rámci zadaného [memory_order –](../standard-library/atomic-enums.md#memory_order_enum) omezení.  
  
```
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) volatile noexcept;
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Order`  
 A [memory_order –](../standard-library/atomic-enums.md#memory_order_enum).  
  
### <a name="return-value"></a>Návratová hodnota  
 Počáteční hodnota příznak, který je uložen v `*this`.  
  
## <a name="see-also"></a>Viz také  
 [\<Atomic >](../standard-library/atomic.md)



