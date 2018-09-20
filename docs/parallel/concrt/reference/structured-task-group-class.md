---
title: structured_task_group – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- structured_task_group
- PPL/concurrency::structured_task_group
- PPL/concurrency::structured_task_group::structured_task_group
- PPL/concurrency::structured_task_group::cancel
- PPL/concurrency::structured_task_group::is_canceling
- PPL/concurrency::structured_task_group::run
- PPL/concurrency::structured_task_group::run_and_wait
- PPL/concurrency::structured_task_group::wait
dev_langs:
- C++
helpviewer_keywords:
- structured_task_group class
ms.assetid: 742afa8c-c7b6-482c-b0ba-04c809927b22
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4aa6df9afddc43980818439ee2c7bbd29ca2f848
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446072"
---
# <a name="structuredtaskgroup-class"></a>structured_task_group – třída

`structured_task_group` Třída reprezentuje kolekci vysoce strukturovaná paralelní práce. Můžete fronty jednotlivých paralelních úloh `structured_task_group` pomocí `task_handle` objekty a počkat na jejich dokončení nebo zrušení skupiny úloh před dokončením provádění, která ukončí všechny úkoly, které nebyly začal spuštění.

## <a name="syntax"></a>Syntaxe

```
class structured_task_group;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[structured_task_group](#ctor)|Přetíženo. Sestaví nový `structured_task_group` objektu.|
|[~ structured_task_group – destruktor](#dtor)|Odstraní `structured_task_group` objektu. Očekává se, že volání buď `wait` nebo `run_and_wait` metodu na objekt před spuštěním destruktor, pokud je spuštěn destruktor kvůli odvíjení zásobníku z důvodu výjimky.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Zrušit](#cancel)|Díky nezaručené pokus o zrušení podstromě pracovní kořenovým adresářem v této skupině úloh. Každá úloha naplánována na skupinu úloh bude zrušena přechodně Pokud je to možné.|
|[is_canceling –](#is_canceling)|Určuje, jestli je skupina úloh aktuálně uprostřed zrušením informuje volající. Neznamená to nutně, který `cancel` byla volána metoda `structured_task_group` objektu (i když například jistě kvalifikuje tuto metodu za účelem vrácení `true`). To může být případ, který `structured_task_group` objektu je probíhá vloženě a další skupinu úloh nahoru ve stromové struktuře práce byla zrušena. V případech, jako jsou tyto kde můžete určit modul runtime zrušení budou směrovat přes to předem `structured_task_group` objektu, `true` vrátí se také.|
|[Spuštění](#run)|Přetíženo. Naplánuje úlohy na `structured_task_group` objektu. Volající spravuje životnost `task_handle` objekt předaný `_Task_handle` parametru. Verze, která přebírá parametr `_Placement` způsobí, že na tendenční směrem k provádění v místě určeném v parametru úlohy.|
|[run_and_wait](#run_and_wait)|Přetíženo. Naplánuje úlohy spustit vložené na kontext volání za pomoci `structured_task_group` objekt pro zrušení plnou podporu. Pokud `task_handle` objekt je předán jako parametr `run_and_wait`, volající zodpovídá za správu životnosti `task_handle` objektu. Funkce vyčká, dokud všechny práce na `structured_task_group` objekt buď dokončí nebo byla zrušena.|
|[Počkej](#wait)|Počká, dokud nebudou všechny práce na `structured_task_group` již byla dokončena nebo zrušena.|

## <a name="remarks"></a>Poznámky

Existuje několik závažných omezení vztahujících se na využití `structured_task_group` objekt získalo výkonu:

- Jediný `structured_task_group` objekt nelze použít ve víc vláknech. Všechny operace na `structured_task_group` objekt se musí provádět ve vlákně, které vytvořil objekt. Dvě výjimky z tohoto pravidla jsou členské funkce `cancel` a `is_canceling`. Objekt nemusí být v seznamu zachycení výrazu lambda a použít v rámci úkolu, pokud úloha je jedním z operace zrušení.

- Všechny úlohy naplánované `structured_task_group` objektu jsou naplánovány prostřednictvím `task_handle` objekty, které musíte explicitně spravovat dobu životnosti.

- Více skupin může používat pouze v nezbytně vnořené pořadí. Pokud dvě `structured_task_group` jsou objekty deklarovány, druhý byl deklarován (vnitřní jeden) musíte destrukce před jakoukoli metodu s výjimkou `cancel` nebo `is_canceling` je volán na první z nich (vnějšího jeden). Tato podmínka platí v případě deklarování jednoduše více `structured_task_group` objektů v rámci stejné nebo funkčně vnořené obory, jakož i v případě úlohu, která se zařadila do fronty `structured_task_group` prostřednictvím `run` nebo `run_and_wait` metody.

- Na rozdíl od Obecné `task_group` všechny stavy třídy `structured_task_group` třídy se nedá vrátit zpět. Po zařazených do fronty úloh do skupiny a čekalo se na jejich dokončení, nemusí znovu použít stejné skupiny.

Další informace najdete v tématu [paralelismus](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`structured_task_group`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ppl.h

**Namespace:** souběžnosti

##  <a name="cancel"></a> Zrušit

Díky nezaručené pokus o zrušení podstromě pracovní kořenovým adresářem v této skupině úloh. Každá úloha naplánována na skupinu úloh bude zrušena přechodně Pokud je to možné.

```
void cancel();
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [zrušení](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

##  <a name="is_canceling"></a> is_canceling –

Určuje, jestli je skupina úloh aktuálně uprostřed zrušením informuje volající. Neznamená to nutně, který `cancel` byla volána metoda `structured_task_group` objektu (i když například jistě kvalifikuje tuto metodu za účelem vrácení `true`). To může být případ, který `structured_task_group` objektu je probíhá vloženě a další skupinu úloh nahoru ve stromové struktuře práce byla zrušena. V případech, jako jsou tyto kde můžete určit modul runtime zrušení budou směrovat přes to předem `structured_task_group` objektu, `true` vrátí se také.

```
bool is_canceling();
```

### <a name="return-value"></a>Návratová hodnota

Údaj o tom, zda `structured_task_group` objekt je uprostřed zrušení (nebo je zaručeno, že bude za chvíli).

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [zrušení](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

##  <a name="run"></a> Spuštění

Naplánuje úlohy na `structured_task_group` objektu. Volající spravuje životnost `task_handle` objekt předaný `_Task_handle` parametru. Verze, která přebírá parametr `_Placement` způsobí, že na tendenční směrem k provádění v místě určeném v parametru úlohy.

```
template<class _Function>
void run(
    task_handle<_Function>& _Task_handle);

template<class _Function>
void run(
    task_handle<_Function>& _Task_handle,
    location& _Placement);
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ objektu funkce, která bude volána k provedení tělo popisovač úkolu.

*_Task_handle*<br/>
Popisovač se plánované práce. Všimněte si, že má volající odpovědnost za dobu života tohoto objektu. Modul runtime bude očekávat, že chcete za provozu, dokud buď `wait` nebo `run_and_wait` byla volána metoda v tomto `structured_task_group` objektu.

*_Umístění.*<br/>
Odkaz na umístění, ve kterém úloha reprezentována `_Task_handle` parametrů by se měl spustit.

### <a name="remarks"></a>Poznámky

Modul runtime vytvoří kopii pracovní funkce, které můžete předat této metodě. Změny stavu, ke kterým dochází v objekt funkce, který můžete předat této metodě se nezobrazí v kopii tohoto objektu funkce.

Pokud `structured_task_group` destructs v důsledku uvolnění z výjimky zásobníku, nepotřebujete k zajištění, že má bylo provedeno volání buď `wait` nebo `run_and_wait` metody. V takovém případě se zrušit a čekání na úlohu reprezentována destruktor odpovídajícím způsobem `_Task_handle` parametr dokončit.

Vyvolá [invalid_multiple_scheduling –](invalid-multiple-scheduling-class.md) výjimku, pokud úloha zpracování určené pomocí `_Task_handle` parametr již byla plánována do objektu skupiny úloh prostřednictvím `run` – metoda a nepřichází žádná síťová volání buď `wait` nebo `run_and_wait` metoda na této skupině úloh.

##  <a name="run_and_wait"></a> run_and_wait –

Naplánuje úlohy spustit vložené na kontext volání za pomoci `structured_task_group` objekt pro zrušení plnou podporu. Pokud `task_handle` objekt je předán jako parametr `run_and_wait`, volající zodpovídá za správu životnosti `task_handle` objektu. Funkce vyčká, dokud všechny práce na `structured_task_group` objekt buď dokončí nebo byla zrušena.

```
template<class _Function>
task_group_status run_and_wait(task_handle<_Function>& _Task_handle);

template<class _Function>
task_group_status run_and_wait(const _Function& _Func);
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ objektu funkce, která bude vyvolána provádění úlohy.

*_Task_handle*<br/>
Popisovač pro úlohy, které se používají ke spouštění vložený kontext volání. Všimněte si, že má volající odpovědnost za dobu života tohoto objektu. Modul runtime bude pokračovat očekávat, že živé až `run_and_wait` metoda dokončí provádění.

*_Func*<br/>
Funkce, která bude volána k vyvolání tělo práce. To může být výraz lambda nebo jiného objektu, která podporuje verzi operátoru volání funkce s podpisem `void operator()()`.

### <a name="return-value"></a>Návratová hodnota

Údaj o tom, jestli bylo čekání uspokojeno nebo skupina úloh se zrušila, kvůli operaci zrušit explicitní nebo výjimky z jednoho z jejích úkolů. Další informace najdete v tématu [task_group_status –](concurrency-namespace-enums.md)

### <a name="remarks"></a>Poznámky

Všimněte si, že jedna nebo více úloh naplánovaných pro toto `structured_task_group` objekt může spustit vložené na kontext volání.

Pokud jeden nebo více následujících úloh naplánovaných pro toto `structured_task_group` objekt dojde k výjimce, modul runtime vybere jeden takový výjimka jeho výběru a šířit z volání `run_and_wait` metody.

Po návratu tato funkce `structured_task_group` objekt považován za konečný stav a neměl by se používat. Všimněte si, že využití po `run_and_wait` metoda vrátí hodnotu, bude mít za následek nedefinované chování.

V ostatním cesta spuštění, je nutné pověření k buď tuto metodu volat nebo `wait` metody před destruktor `structured_task_group` spustí.

##  <a name="ctor"></a> structured_task_group –

Sestaví nový `structured_task_group` objektu.

```
structured_task_group();

structured_task_group(cancellation_token _CancellationToken);
```

### <a name="parameters"></a>Parametry

*_CancellationToken*<br/>
Token zrušení pro přidružení k této skupiny strukturovaných úloh. Skupiny strukturovaných úloh se zruší, pokud je token zrušen.

### <a name="remarks"></a>Poznámky

Vytvoří konstruktor, který přijímá token zrušení `structured_task_group` , která budou zrušeny při zrušení zdroje přidružené k tokenu. Také poskytuje explicitní rušícího tokenu izoluje této skupiny strukturovaných úloh ze implicitní zrušení z nadřazené skupiny s tokenem jiný nebo žádný token.

##  <a name="dtor"></a> ~ structured_task_group

Odstraní `structured_task_group` objektu. Očekává se, že volání buď `wait` nebo `run_and_wait` metodu na objekt před spuštěním destruktor, pokud je spuštěn destruktor kvůli odvíjení zásobníku z důvodu výjimky.

```
~structured_task_group();
```

### <a name="remarks"></a>Poznámky

Pokud spuštění destruktoru v důsledku normálního provedení (například není uvolnění zásobníku z důvodu výjimky) a ani `wait` ani `run_and_wait` metod, destruktor může vyvolat [missing_wait –](missing-wait-class.md) došlo k výjimce.

##  <a name="wait"></a> Počkej

Počká, dokud nebudou všechny práce na `structured_task_group` již byla dokončena nebo zrušena.

```
task_group_status wait();
```

### <a name="return-value"></a>Návratová hodnota

Údaj o tom, jestli bylo čekání uspokojeno nebo skupina úloh se zrušila, kvůli operaci zrušit explicitní nebo výjimky z jednoho z jejích úkolů. Další informace najdete v tématu [task_group_status –](concurrency-namespace-enums.md)

### <a name="remarks"></a>Poznámky

Všimněte si, že jedna nebo více úloh naplánovaných pro toto `structured_task_group` objekt může spustit vložené na kontext volání.

Pokud jeden nebo více následujících úloh naplánovaných pro toto `structured_task_group` objekt dojde k výjimce, modul runtime vybere jeden takový výjimka jeho výběru a šířit z volání `wait` metody.

Po návratu tato funkce `structured_task_group` objekt považován za konečný stav a neměl by se používat. Všimněte si, že využití po `wait` metoda vrátí hodnotu, bude mít za následek nedefinované chování.

V ostatním cesta spuštění, je nutné pověření k buď tuto metodu volat nebo `run_and_wait` metody před destruktor `structured_task_group` spustí.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[task_group – třída](task-group-class.md)<br/>
[task_handle – třída](task-handle-class.md)
