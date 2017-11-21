---
title: "&lt;vlákno&gt; funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- thread/std::get_id
- thread/std::sleep_for
- thread/std::sleep_until
- thread/std::swap
- thread/std::yield
ms.assetid: bb1aa1ef-fe3f-4e2c-8b6e-e22dbf2f5a19
caps.latest.revision: "12"
manager: ghogen
helpviewer_keywords:
- std::get_id [C++]
- std::sleep_for [C++]
- std::sleep_until [C++]
- std::swap [C++]
- std::yield [C++]
ms.openlocfilehash: dd073f48eb926e8fec0017f63ab77a91eb65acff
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltthreadgt-functions"></a>&lt;vlákno&gt; funkce
||||  
|-|-|-|  
|[get_id –](#get_id)|[sleep_for –](#sleep_for)|[sleep_until –](#sleep_until)|  
|[swap](#swap)|[YIELD –](#yield)|  
  
##  <a name="get_id"></a>get_id –  
 Jednoznačně identifikuje aktuální vlákno provádění.  
  
```  
thread::id this_thread::get_id() noexcept;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Objekt typu [thread::id](../standard-library/thread-class.md) který jednoznačně identifikuje aktuální vlákno provádění.  
  
##  <a name="sleep_for"></a>sleep_for –  
 Blokuje volající vlákno.  
  
```  
template <class Rep,  
class Period>  
inline void sleep_for(const chrono::duration<Rep, Period>& Rel_time);
```  
  
### <a name="parameters"></a>Parametry  
 `Rel_time`  
 A [doba trvání](../standard-library/duration-class.md) objekt, který určuje časový interval.  
  
### <a name="remarks"></a>Poznámky  
 Funkce blokuje volající vlákno pro alespoň čas, která je zadána `Rel_time`. Tato funkce nevyvolá výjimku jakékoli výjimky.  
  
##  <a name="sleep_until"></a>sleep_until –  
 Volající vlákno blokuje alespoň do zadané doby.  
  
```  
template <class Clock, class Duration>  
void sleep_until(const chrono::time_point<Clock, Duration>& Abs_time);

void sleep_until(const xtime *Abs_time);
```  
  
### <a name="parameters"></a>Parametry  
 `Abs_time`  
 Představuje bod v čase.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce nevyvolá výjimku jakékoli výjimky.  
  
##  <a name="swap"></a>swap  
 Prohození stavy dva `thread` objekty.  
  
```  
void swap(thread& Left, thread& Right) noexcept;  
```  
  
### <a name="parameters"></a>Parametry  
 `Left`  
 Levé straně `thread` objektu.  
  
 `Right`  
 Právo `thread` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Volání funkcí `Left.swap(Right)`.  
  
##  <a name="yield"></a>YIELD –  
 Signály operačního systému spustit jiná vlákna i v případě, že aktuální vlákno by normálně nadále fungoval.  
  
```  
inline void yield() noexcept;  
```  
  
## <a name="see-also"></a>Viz také  
 [\<vlákno >](../standard-library/thread.md)

