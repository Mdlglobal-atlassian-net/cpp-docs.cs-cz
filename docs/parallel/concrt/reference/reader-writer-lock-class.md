---
title: reader_writer_lock – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- reader_writer_lock
- CONCRT/concurrency::reader_writer_lock
- CONCRT/concurrency::reader_writer_lock::scoped_lock
- CONCRT/concurrency::reader_writer_lock::scoped_lock_read
- CONCRT/concurrency::reader_writer_lock::reader_writer_lock
- CONCRT/concurrency::reader_writer_lock::lock
- CONCRT/concurrency::reader_writer_lock::lock_read
- CONCRT/concurrency::reader_writer_lock::try_lock
- CONCRT/concurrency::reader_writer_lock::try_lock_read
- CONCRT/concurrency::reader_writer_lock::unlock
dev_langs:
- C++
helpviewer_keywords:
- reader_writer_lock class
ms.assetid: 91a59cd2-ca05-4b74-8398-d826d9f86736
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4a2f48a80efca0ec6e85a315b355a6482fb2096b
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692266"
---
# <a name="readerwriterlock-class"></a>reader_writer_lock – třída
Zapisovač předvoleb zámku na základě fronty čtení a zápis s místní pouze otáčí. Zámek uděluje nejprve v – nejprve out (FIFO) přístup k zapisovače a starves čtečky průběžné zatížení zapisovačů.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class reader_writer_lock;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-classes"></a>Veřejné třídy  
  
|Název|Popis|  
|----------|-----------------|  
|[reader_writer_lock::scoped_lock – třída](#scoped_lock_class)|K výjimce bezpečné RAII obálku kterého lze získat `reader_writer_lock` zamknout objekty jako zapisovač.|  
|[reader_writer_lock::scoped_lock_read – třída](#scoped_lock_read_class)|K výjimce bezpečné RAII obálku kterého lze získat `reader_writer_lock` zamknout objekty jako čtečka čipových karet.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[reader_writer_lock](#ctor)|Vytvoří nový `reader_writer_lock` objektu.|  
|[~reader_writer_lock Destructor](#dtor)|Zničí `reader_writer_lock` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[lock](#lock)|Získá zámek čtení a zápis jako zapisovač.|  
|[lock_read](#lock_read)|Získá zámek čtení a zápis pro čtenáře. Pokud existují uživatelé vytvářející obsah, je nutné čekat, až se provádí pomocí active čtečky. Čtečka jednoduše zaregistruje zájmu o zámek a čeká zapisovače pro uvolnění.|  
|[try_lock](#try_lock)|Pokusí se získat zámek čtení a zápis jako zapisovač bez blokování.|  
|[try_lock_read](#try_lock_read)|Pokusí se získat zámek čtení a zápis pro čtenáře bez blokování.|  
|[odemknutí](#unlock)|Odemkne zámek čtení a zápis podle kdo uzamkne ji čtečka nebo zapisovač.|  
  
## <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [synchronizační datové struktury](../../../parallel/concrt/synchronization-data-structures.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `reader_writer_lock`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrt.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="lock"></a> Zámek 

 Získá zámek čtení a zápis jako zapisovač.  
  
```
void lock();
```  
  
### <a name="remarks"></a>Poznámky  
 Je často bezpečnější využívat [scoped_lock](#scoped_lock_class) konstrukce k získání a uvolněte `reader_writer_lock` objektu jako zapisovač výjimku bezpečným způsobem.  
  
 Po zapisovač se pokusí získat zámek, všechny budoucí čtečky zablokuje, dokud zapisovače mít úspěšně získali a vydání zámek. Tato uzamčení je tendenční směrem zapisovače a můžete omezují čtečky průběžné zatížení zapisovačů.  
  
 Zapisovačů jsou zřetězené tak, aby zapisovač ukončení zámek uvolní další zapisovače v řádku.  
  
 Pokud zámek již držené volání kontextu [improper_lock](improper-lock-class.md) dojde k výjimce.  
  
##  <a name="lock_read"></a> lock_read – 

 Získá zámek čtení a zápis pro čtenáře. Pokud existují uživatelé vytvářející obsah, je nutné čekat, až se provádí pomocí active čtečky. Čtečka jednoduše zaregistruje zájmu o zámek a čeká zapisovače pro uvolnění.  
  
```
void lock_read();
```  
  
### <a name="remarks"></a>Poznámky  
 Často je bezpečnější využívat [scoped_lock_read –](#scoped_lock_read_class) konstrukce k získání a uvolněte `reader_writer_lock` objektu jako čtečku výjimku bezpečným způsobem.  
  
 Pokud existují zapisovače čekání na zámek, bude čtečky Počkejte, dokud všechny zapisovače v řádku získali a vydání zámek. Tato uzamčení je tendenční směrem zapisovače a můžete omezují čtečky průběžné zatížení zapisovačů.  
  
##  <a name="ctor"></a> reader_writer_lock 

 Vytvoří nový `reader_writer_lock` objektu.  
  
```
reader_writer_lock();
```  
  
##  <a name="dtor"></a> ~ reader_writer_lock 

 Zničí `reader_writer_lock` objektu.  
  
```
~reader_writer_lock();
```  
  
### <a name="remarks"></a>Poznámky  
 Očekává se, že zámek trvá už při spuštění destruktoru. Povolení zapisovače zámek pro čtení k destruct s zámek stále uchovávat výsledky v nedefinované chování.  
  
##  <a name="scoped_lock_class"></a>  reader_writer_lock::scoped_lock – třída  
 K výjimce bezpečné RAII obálku kterého lze získat `reader_writer_lock` zamknout objekty jako zapisovač.  
  
```
class scoped_lock;
``` 
## <a name="scoped_lock_ctor"></a> scoped_lock::scoped_lock 

Vytvoří `scoped_lock` objektů a získá `reader_writer_lock` objekt předaná `_Reader_writer_lock` parametr jako zapisovač. Pokud zámek trvá jiné vlákno, toto volání se zablokuje.  
  
  
```
explicit _CRTIMP scoped_lock(reader_writer_lock& _Reader_writer_lock);
```  
  
#### <a name="parameters"></a>Parametry  
 `_Reader_writer_lock`  
 `reader_writer_lock` Objekt, který chcete získat jako zapisovač.  
  
## <a name="scoped_lock_dtor"></a> scoped_lock –:: ~ scoped_lock – 

Zničí `reader_writer_lock` objektu a uvolní zámek zadán v jeho konstruktoru.   

```
~scoped_lock();
```  
  
##  <a name="scoped_lock_read_class"></a>  reader_writer_lock::scoped_lock_read – třída  
 K výjimce bezpečné RAII obálku kterého lze získat `reader_writer_lock` zamknout objekty jako čtečka čipových karet.  
  
```
class scoped_lock_read;
```  
  
##  <a name="try_lock"></a> try_lock – 

 Pokusí se získat zámek čtení a zápis jako zapisovač bez blokování.  

## <a name="scoped_lock_read_ctor"></a> scoped_lock_read::scoped_lock_read 

Vytvoří `scoped_lock_read` objektů a získá `reader_writer_lock` objekt předaná `_Reader_writer_lock` parametr jako čtečka čipových karet. Pokud zámek trvá jiné vlákno jako zapisovač nebo existují čekající na zpracování zapisovače, toto volání se zablokuje.  
  
```
explicit _CRTIMP scoped_lock_read(reader_writer_lock& _Reader_writer_lock);
```  
  
#### <a name="parameters"></a>Parametry  
 `_Reader_writer_lock`  
 `reader_writer_lock` Objekt, který chcete získat jako čtečka čipových karet.  
  
## <a name="a-namescopedlockreaddtor--readerwriterlockscopedlockreadscopedlockread-destructor"></a><a name="scoped_lock_read_dtor">  reader_writer_lock::scoped_lock_read:: ~ scoped_lock_read – destruktor
Zničí `scoped_lock_read` objektu a uvolní zámek zadán v jeho konstruktoru.  

```
~scoped_lock_read();
```  
  
## <a name="try_lock"></a> try_lock – 

```
bool try_lock();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud se získal zámek, hodnota `true`, jinak hodnota `false`.  
  
##  <a name="try_lock_read"></a> try_lock_read – 

 Pokusí se získat zámek čtení a zápis pro čtenáře bez blokování.  
  
```
bool try_lock_read();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud se získal zámek, hodnota `true`, jinak hodnota `false`.  
  
##  <a name="unlock"></a> odemknutí 

 Odemkne zámek čtení a zápis podle kdo uzamkne ji čtečka nebo zapisovač.  
  
```
void unlock();
```  
  
### <a name="remarks"></a>Poznámky  
 Při čekání na zámek zapisovače verzi zámek vždy přejde na další zápis v pořadí FIFO. Tato uzamčení je tendenční směrem zapisovače a můžete omezují čtečky průběžné zatížení zapisovačů.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [critical_section – třída](critical-section-class.md)
