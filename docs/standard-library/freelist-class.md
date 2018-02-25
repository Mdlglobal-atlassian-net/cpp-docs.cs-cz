---
title: "FreeList – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- allocators/stdext::freelist
- allocators/stdext::freelist::pop
- allocators/stdext::freelist::push
dev_langs:
- C++
helpviewer_keywords:
- stdext::freelist
- stdext::freelist [C++], pop
- stdext::freelist [C++], push
ms.assetid: 8ad7e35c-4c80-4479-8ede-1a2497b06d71
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2f0e85e247346e71093df393a69b91b579236e2f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="freelist-class"></a>freelist – třída
Spravuje seznam bloky paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <std::size_t Sz, class Max>  
class freelist
 : public Max
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`Sz`|Počet prvků v poli, která bude přidělena.|  
|`Max`|Maximální třída představující maximální počet elementů k uložení do seznamu volné. Maximální třída může být [max_none](../standard-library/max-none-class.md), [max_unbounded](../standard-library/max-unbounded-class.md), [max_fixed_size](../standard-library/max-fixed-size-class.md), nebo [max_variable_size](../standard-library/max-variable-size-class.md).|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída šablony spravuje seznam bloky paměti o velikosti `Sz` s maximální délkou seznamu určit maximální třídou předaná `Max`.  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[FreeList](#freelist)|Vytvoří objekt typu `freelist`.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[pop](#pop)|Odebere první blok paměti ze seznamu volné.|  
|[push](#push)|Blok paměti přidá do seznamu.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<alokátorů >  
  
 **Namespace:** stdext –  
  
##  <a name="freelist"></a>  FreeList::FreeList  
 Vytvoří objekt typu `freelist`.  
  
```
freelist();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="pop"></a>  FreeList::POP  
 Odebere první blok paměti ze seznamu volné.  
  
```
void *pop();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí ukazatele na blok paměti odebrat ze seznamu.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu `NULL` Pokud je seznam prázdný. Odebere, jinak hodnota prvního bloku paměti ze seznamu.  
  
##  <a name="push"></a>  FreeList::push  
 Blok paměti přidá do seznamu.  
  
```
bool push(void* ptr);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`ptr`|Ukazatel na paměti blok, který má být přidán do seznamu volné.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud `full` funkce max třídy vrací `false`, jinak hodnota `push` funkce vrátí `false`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `full` funkce max třídy vrací `false`, přidá bloku paměti, na kterou odkazuje tento – členská funkce `ptr` na první pozice v seznamu.  
  
## <a name="see-also"></a>Viz také  
 [\<allocators>](../standard-library/allocators-header.md)



