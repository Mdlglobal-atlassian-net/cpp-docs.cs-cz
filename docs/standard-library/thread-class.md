---
title: "Thread – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- thread/std::thread
- thread/std::thread::id Class
- thread/std::thread::thread
- thread/std::thread::detach
- thread/std::thread::get_id
- thread/std::thread::hardware_concurrency
- thread/std::thread::join
- thread/std::thread::joinable
- thread/std::thread::native_handle
- thread/std::thread::swap
dev_langs: C++
ms.assetid: df249bc7-ff81-4ff9-a6d6-5e3d9a8f56a1
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
helpviewer_keywords:
- std::thread [C++]
- std::thread [C++], thread
- std::thread [C++], detach
- std::thread [C++], get_id
- std::thread [C++], hardware_concurrency
- std::thread [C++], join
- std::thread [C++], joinable
- std::thread [C++], native_handle
- std::thread [C++], swap
ms.openlocfilehash: 70f791044d7ebdcb97ee53d4c99bd1db4ed3561b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="thread-class"></a>thread – třída
Definuje objekt, který umožňuje sledovat a spravovat vlákno provádění v rámci aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class thread;
```  
  
## <a name="remarks"></a>Poznámky  
 Pro sledování a správu vlákna provádění v rámci aplikace lze použít `thread`. Objekt vlákna, který je vytvořen pomocí výchozího konstruktoru, není přidružen k žádnému vláknu provádění. Objekt vlákna, který byl vytvořen pomocí volatelného objektu, vytváří nové vlákno provádění a volá v něm volatelný objekt. Objekty vláken mohou být přesunuty, ale nemohou být zkopírovány. Proto může být vlákno provádění přidruženo pouze k jednomu objektu vlákna.  
  
 Každé vlákno provádění má jedinečný identifikátor typu `thread::id`. Funkce `this_thread::get_id` vrací identifikátor volajícího vlákna. Členská funkce `thread::get_id` vrací identifikátor vlákna, které je objektem vlákna spravováno. Pro objekt vlákna vytvořený s výchozím nastavením vrací metoda `thread::get_id` objekt, který má hodnotu shodnou pro všechny objekty vlákna vytvořené s výchozím nastavením a rozdílnou od hodnoty, která je metodou `this_thread::get_id` vrácena pro jakékoli vlákno provádění, které by mohlo být připojeno v době volání.  
  
## <a name="members"></a>Členové  
  
### <a name="public-classes"></a>Veřejné třídy  
  
|Název|Popis|  
|----------|-----------------|  
|[Thread::ID – třída](#id_class)|Jednoznačně identifikuje přidružené vlákno.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[přístup z více vláken](#thread)|Vytvoří `thread` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[odpojení](#detach)|Odpojí přidružené vlákno od objektu `thread`.|  
|[get_id –](#get_id)|Vrací jedinečný identifikátor přidruženého vlákna.|  
|[hardware_concurrency](#hardware_concurrency)|Statické. Vrací odhadovaný počet kontextů hardwarových vláken.|  
|[připojení k](#join)|Blokuje, dokud se přidružené vlákno nedokončí.|  
|[spojitelného](#joinable)|Určuje, zda je přidružené vlákno spojitelné.|  
|[native_handle –](#native_handle)|Vrátí typ specifický pro implementaci představující popisovač vlákna.|  
|[swap](#swap)|Zamění stav objektu se zadaným objektem `thread`.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[Thread::Operator =](#op_eq)|Přidruží vlákno k aktuálnímu objektu `thread`.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<vlákno >  
  
 **Namespace:** – std  
  
##  <a name="detach"></a>Thread::detach –
 Umožňuje odpojit přidružené vlákno. Operační systém je zodpovědný za uvolnění prostředků přístup z více vláken na ukončení.  
  
```
void detach();
```  
  
### <a name="remarks"></a>Poznámky  
 Po volání `detach`, následných volání [get_id –](#get_id) vrátit [id](#id_class).  
  
 Pokud podproces, který je přidružený k volání objektu není spojitelného, funkce vyvolá [system_error –](../standard-library/system-error-class.md) s kódem chyby `invalid_argument`.  
  
 Pokud podproces, který je přidružený k volání objektu je neplatný, funkce vyvolá `system_error` s kódem chyby `no_such_process`.  
  
##  <a name="get_id"></a>Thread::get_id –
 Vrací jedinečný identifikátor přidružený vlákno.  
  
```
id get_id() const noexcept;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A [thread::id](#id_class) objekt, který jednoznačně identifikuje přidružené vlákno, nebo `thread::id()` Pokud žádný přístup z více vláken je přidružený k objektu.  
  
##  <a name="hardware_concurrency"></a>Thread::hardware_concurrency –
 Statickou metodu, která vrátí odhad počtu kontexty hardwaru přístup z více vláken.  
  
```
static unsigned int hardware_concurrency() noexcept;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odhad počtu kontexty hardwaru přístup z více vláken. Pokud hodnotu nelze vypočítat, nebo není dobře definované, tato metoda vrátí hodnotu 0.  
  
##  <a name="id_class"></a>Thread::ID – třída  
 Poskytuje jedinečný identifikátor pro každý podproces provádění v procesu.  
  
```
class thread::id {
    id() noexcept;
};
```  
  
### <a name="remarks"></a>Poznámky  
 Výchozí konstruktor vytvoří objekt, který nelze použít k porovnání rovna `thread::id` objekt pro jakékoli existující vlákno.  
  
 Všechny výchozí sestavený `thread::id` porovnat objekty stejné.  
  
##  <a name="join"></a>Thread::JOIN –
 Bloky, dokud se nedokončí vlákno spuštění, který je spojen s volající objekt.  
  
```
void join();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud volání úspěšné, následující volání [get_id –](#get_id) volání objektu vrátit výchozí [thread::id](#id_class) , porovnat není rovno `thread::id` z jakékoli existující vlákno; Pokud neproběhne úspěšně volání , hodnotu, která je vrácena `get_id` se nemění.  
  
##  <a name="joinable"></a>Thread::joinable –
 Určuje, jestli je přidružené vlákno *spojitelného*.  
  
```
bool joinable() const noexcept;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud je související vlákno *spojitelného*, jinak hodnota `false`.  
  
### <a name="remarks"></a>Poznámky  
 Objekt vlákno je *spojitelného* Pokud `get_id() != id()`.  
  
##  <a name="native_handle"></a>Thread::native_handle –
 Vrátí typ specifický pro implementaci představující popisovač vlákna. Popisovač podprocesu lze způsoby konkrétní implementace.  
  
```
native_handle_type native_handle();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `native_handle_type`je definován jako Win32 `HANDLE` který vložena jako `void *`.  
  
##  <a name="op_eq"></a>Thread::Operator =  
 Přidruží vlákno zadaný objekt aktuálního objektu.  
  
```
thread& operator=(thread&& Other) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Other`  
 A `thread` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 `*this`  
  
### <a name="remarks"></a>Poznámky  
 Volání metody odpojit, pokud je volání objekt spojitelného.  
  
 Po přidružení se `Other` nastavena do stavu sestavený výchozí.  
  
##  <a name="swap"></a>Thread::swap –
 Prohození stav objektu se u zadané `thread` objektu.  
  
```
void swap(thread& Other) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Other`  
 A `thread` objektu.  
  
##  <a name="thread"></a>Thread::Thread – konstruktor  
 Vytvoří `thread` objektu.  
  
```
thread() noexcept;
template <class Fn, class... Args>
explicit thread(Fn&& F, Args&&... A);

thread(thread&& Other) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `F`  
 Definované aplikací funkce být vykonán vlákno.  
  
 `A`  
 Seznam argumentů, které mají být předány `F`.  
  
 `Other`  
 Existující objekt `thread`.  
  
### <a name="remarks"></a>Poznámky  
 První konstruktoru vytvoří objekt, který není přidružený podproces provádění. Hodnota, která je vrácena voláním `get_id` konstruovaný objekt je `thread::id()`.  
  
 Druhý konstruktor vytvoří objekt, který je spojen s nové vlákno provádění a spustí pseudo funkce `INVOKE` která je definovaná v [ \<funkční >](../standard-library/functional.md). Pokud není dost prostředků je možné spustit nové vlákno, funkce vyvolá [system_error –](../standard-library/system-error-class.md) objekt, který má chybový kód `resource_unavailable_try_again`. Pokud volání `F` ukončí s nezachycenou výjimku [ukončit](../standard-library/exception-functions.md#terminate) je volána.  
  
 Třetí konstruktoru vytvoří objekt, který je spojen s podproces, který je přidružen `Other`. `Other`pak je nastaven na výchozí sestavený stavu.  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)   
 [\<vlákno >](../standard-library/thread.md)



