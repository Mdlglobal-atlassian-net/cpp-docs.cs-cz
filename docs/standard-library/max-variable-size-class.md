---
title: "max_variable_size – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- allocators/stdext::max_variable_size
- allocators/stdext::max_variable_size::allocated
- allocators/stdext::max_variable_size::deallocated
- allocators/stdext::max_variable_size::full
- allocators/stdext::max_variable_size::released
- allocators/stdext::max_variable_size::saved
dev_langs:
- C++
helpviewer_keywords:
- stdext::max_variable_size
- stdext::max_variable_size [C++], allocated
- stdext::max_variable_size [C++], deallocated
- stdext::max_variable_size [C++], full
- stdext::max_variable_size [C++], released
- stdext::max_variable_size [C++], saved
ms.assetid: 9f2e9df0-4148-4b37-bc30-f8eca0ef86ae
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d9d7b1a5f9f1ef1a53a3d8bb5ee69a1e353b0edb
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="maxvariablesize-class"></a>max_variable_size – třída
Popisuje [maximálního počtu třída](../standard-library/allocators-header.md) objekt, který omezuje [freelist](../standard-library/freelist-class.md) objekt, který má maximální délku, která je přibližně přímo úměrná počtu přidělené bloky paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class max_variable_size
```  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[max_variable_size](#max_variable_size)|Vytvoří objekt typu `max_variable_size`.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[Přidělené](#allocated)|Zvětší počet bloků přidělené paměti.|  
|[Zrušeno](#deallocated)|Snižuje počet přidělené bloky paměti.|  
|[Úplná](#full)|Vrátí hodnotu, která určuje, zda více bloky paměti by měla být přidán do seznamu volné.|  
|[Vydání](#released)|Snižuje počet paměti bloků v seznamu volné.|  
|[saved](#saved)|Zvýší počet bloky paměti v seznamu volné.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<alokátorů >  
  
 **Namespace:** stdext –  
  
##  <a name="allocated"></a>  max_variable_size::allocated  
 Zvětší počet bloků přidělené paměti.  
  
```
void allocated(std::size_t _Nx = 1);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`_Nx`|Hodnota přírůstku.|  
  
### <a name="remarks"></a>Poznámky  
 Tento člen funkce přidá `_Nx` uložené hodnotu `_Nallocs`. Tato funkce člen je volána po každém úspěšném volání pomocí `cache_freelist::allocate` operátor `new`. Argument `_Nx` je počet bloků paměti v bloku dat přidělené operátor `new`.  
  
##  <a name="deallocated"></a>  max_variable_size::deallocated  
 Snižuje počet přidělené bloky paměti.  
  
```
void deallocated(std::size_t _Nx = 1);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`_Nx`|Hodnota přírůstku.|  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce odečítá `_Nx` z uložené hodnoty `_Nallocs`. Tato funkce člen je volána po každé pro volání `cache_freelist::deallocate` operátor `delete`. Argument `_Nx` je počet bloků paměti v bloku dat navrácena operátorem `delete`.  
  
##  <a name="full"></a>  max_variable_size::full  
 Vrátí hodnotu, která určuje, zda více bloky paměti by měla být přidán do seznamu volné.  
  
```
bool full();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud `_Nallocs / 16 + 16 <= _Nblocks`.  
  
### <a name="remarks"></a>Poznámky  
 Tento člen funkce volá `cache_freelist::deallocate`. Pokud se volání vrátí `true`, `deallocate` vloží bloku paměti v seznamu volné; Pokud vrátí hodnotu false, `deallocate` operátor volání `delete` se zrušit přidělení bloku.  
  
##  <a name="max_variable_size"></a>  max_variable_size::max_variable_size  
 Vytvoří objekt typu `max_variable_size`.  
  
```
max_variable_size();
```  
  
### <a name="remarks"></a>Poznámky  
 Konstruktor inicializuje uložené hodnoty `_Nblocks` a `_Nallocs` na hodnotu nula.  
  
##  <a name="released"></a>  max_variable_size::released  
 Snižuje počet paměti bloků v seznamu volné.  
  
```
void released();
```  
  
### <a name="remarks"></a>Poznámky  
 Tento člen funkce sníží uložené hodnoty `_Nblocks`. `released` Je volána funkce člena třídy aktuální maximální `cache_freelist::allocate` vždy, když odebere blok paměti ze seznamu volné.  
  
##  <a name="saved"></a>  max_variable_size::saved  
 Zvýší počet bloky paměti v seznamu volné.  
  
```
void saved();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen zvýší uložené hodnoty `_Nblocks`. Tento člen funkce volá `cache_freelist::deallocate` vždy, když vloží blok paměti v seznamu volné.  
  
## <a name="see-also"></a>Viz také  
 [\<allocators>](../standard-library/allocators-header.md)



