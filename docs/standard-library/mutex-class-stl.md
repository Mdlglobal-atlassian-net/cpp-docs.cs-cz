---
title: "mutex – třída (standardní knihovna C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- mutex/std::mutex
- mutex/std::mutex::mutex
- mutex/std::mutex::lock
- mutex/std::mutex::native_handle
- mutex/std::mutex::try_lock
- mutex/std::mutex::unlock
dev_langs: C++
ms.assetid: 7999d055-f74f-4303-810f-8d3c9cde2f69
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
helpviewer_keywords:
- std::mutex [C++]
- std::mutex [C++], mutex
- std::mutex [C++], lock
- std::mutex [C++], native_handle
- std::mutex [C++], try_lock
- std::mutex [C++], unlock
ms.openlocfilehash: 37a6d72ab7f79c24606a5ffb0dcafe1e6c6d1e18
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="mutex-class-c-standard-library"></a>mutex – třída (standardní knihovna C++)
Představuje *mutex typu*. Objekty tohoto typu lze vynutit vzájemné vyloučení v rámci programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class mutex;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[mutex](#mutex)|Vytvoří `mutex` objektu.|  
|[mutex:: ~ mutex – destruktor](#dtormutex_destructor)|Uvolní všechny prostředky, které byly používány `mutex` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Zámek](#lock)|Blokuje volající vlákno, dokud vlákno získá vlastnictví `mutex`.|  
|[native_handle –](#native_handle)|Vrátí implementace konkrétní typ, který reprezentuje objekt mutex popisovač.|  
|[try_lock –](#try_lock)|Pokusí se získat vlastnictví `mutex` bez blokování.|  
|[odemknutí](#unlock)|Uvolní vlastnictví `mutex`.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<mutex >  
  
 **Namespace:** – std  
  
##  <a name="lock"></a>mutex::LOCK –
 Blokuje volající vlákno, dokud vlákno získá vlastnictví `mutex`.  
  
```cpp  
void lock();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud již vlastní volající vlákno `mutex`, chování není definován.  
  
##  <a name="mutex"></a>mutex::mutex – konstruktor  
 Vytvoří `mutex` objekt, který není uzamčený.  
  
```cpp  
constexpr mutex() noexcept;
```  
  
##  <a name="dtormutex_destructor"></a>mutex:: ~ mutex – destruktor  
 Uvolní všechny prostředky, které jsou používány `mutex` objektu.  
  
```cpp  
~mutex();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud při spuštění destruktoru, není objekt uzamčen, chování nedefinovaný.  
  
##  <a name="native_handle"></a>mutex::native_handle –
 Vrátí implementace konkrétní typ, který reprezentuje objekt mutex popisovač. Popisovač mutex lze způsoby konkrétní implementace.  
  
```
native_handle_type native_handle();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `native_handle_type`je definován jako `Concurrency::critical_section *` který vložena jako `void *`.  
  
##  <a name="try_lock"></a>mutex::try_lock –
 Pokusí se získat vlastnictví `mutex` bez blokování.  
  
```cpp  
bool try_lock();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud metoda úspěšně získá vlastnictví `mutex`, jinak hodnota `false`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud již vlastní volající vlákno `mutex`, chování není definován.  
  
##  <a name="unlock"></a>mutex::Unlock –
 Uvolní vlastnictví `mutex`.  
  
```cpp  
void unlock();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud není vlastníkem volající vlákno `mutex`, chování není definován.  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex >](../standard-library/mutex.md)



