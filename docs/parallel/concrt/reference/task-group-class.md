---
title: task_group – třída
ms.date: 07/20/2018
f1_keywords:
- task_group
- PPL/concurrency::task_group
- PPL/concurrency::task_group::task_group
helpviewer_keywords:
- task_group class
ms.openlocfilehash: 60c147f38ddc3936f47aea0cfd1ab1548b382441
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142570"
---
# <a name="task_group-class"></a>task_group – třída

Třída `task_group` představuje kolekci paralelní práce, která může být očekávána nebo zrušena.

## <a name="syntax"></a>Syntaxe

```cpp
class task_group;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[task_group](#ctor)|Přetíženo. Vytvoří nový objekt `task_group`.|
|[~ task_group destruktor](#dtor)|Odstraní objekt `task_group`. Očekává se, že zavoláte buď metodu `wait` nebo `run_and_wait` objektu před spuštěním destruktoru, pokud se destruktor neprovádí jako výsledek zrušení zásobníku z důvodu výjimky.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[operaci](#cancel)|Provede se nejvhodnějším pokusem o zrušení podstromu práce s kořenem v této skupině úloh. Pokud je to možné, všechny úlohy naplánované ve skupině úloh se přestanou přeruší.|
|[is_canceling](#is_canceling)|Informuje volajícího, zda je skupina úloh aktuálně v průběhu zrušení. To neznamená nutně najevo, že byla volána metoda `cancel` pro objekt `task_group` (i když taková skutečnost by tato metoda vracela `true`). Může se jednat o případ, že objekt `task_group` spouští inline a další v pracovní větvi se zrušila. V případech, jako jsou ty, kde modul runtime může určit předem čas, kdy bude zrušení procházet tímto objektem `task_group`, se vrátí také `true`.|
|[spouštěl](#run)|Přetíženo. Naplánuje úlohu na objekt `task_group`. Pokud je objekt `task_handle` předán jako parametr pro `run`, je volajícím zodpovědný za správu životnosti objektu `task_handle`. Verze metody, která přebírá odkaz na objekt funkce jako parametr, zahrnuje přidělení haldy uvnitř modulu runtime, který může být méně kvalitní než použití verze, která přebírá odkaz na objekt `task_handle`. Verze, která přebírá parametr `_Placement` způsobí, že se úkol na základě umístění určeného parametrem posune na spuštěno.|
|[run_and_wait](#run_and_wait)|Přetíženo. Naplánuje spuštění úlohy vložené do volajícího kontextu s asistencí objektu `task_group` pro úplnou podporu zrušení. Funkce potom počká, dokud nebudou všechny práce na objektu `task_group` buď dokončeny, nebo zrušeny. Pokud je objekt `task_handle` předán jako parametr pro `run_and_wait`, je volajícím zodpovědný za správu životnosti objektu `task_handle`.|
|[Počkej](#wait)|Počká, dokud nebudou všechny práce na `task_group`m objektu buď dokončeny, nebo zrušeny.|

## <a name="remarks"></a>Poznámky

Na rozdíl od silně omezené `structured_task_group` třídy je `task_group`á třída mnohem obecnější konstrukce. Nemá žádná omezení popsaná [structured_task_group](structured-task-group-class.md). objekty `task_group` můžou být bezpečně používané napříč vlákny a využívají se v bezplatné formě. Nevýhodou `task_group` konstrukce je, že se nemusí provádět stejně jako `structured_task_group` konstrukce pro úlohy, které provádějí malé množství práce.

Další informace najdete v tématu [Task paralelismus](../task-parallelism-concurrency-runtime.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`task_group`

## <a name="requirements"></a>Požadavky

**Záhlaví:** PPL. h

**Obor názvů:** souběžnost

## <a name="cancel"></a>operaci

Provede se nejvhodnějším pokusem o zrušení podstromu práce s kořenem v této skupině úloh. Pokud je to možné, všechny úlohy naplánované ve skupině úloh se přestanou přeruší.

```cpp
void cancel();
```

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [zrušení](../cancellation-in-the-ppl.md).

## <a name="is_canceling"></a>is_canceling

Informuje volajícího, zda je skupina úloh aktuálně v průběhu zrušení. To neznamená nutně najevo, že byla volána metoda `cancel` pro objekt `task_group` (i když taková skutečnost by tato metoda vracela `true`). Může se jednat o případ, že objekt `task_group` spouští inline a další v pracovní větvi se zrušila. V případech, jako jsou ty, kde modul runtime může určit předem čas, kdy bude zrušení procházet tímto objektem `task_group`, se vrátí také `true`.

```cpp
bool is_canceling();
```

### <a name="return-value"></a>Návratová hodnota

Označení toho, zda je objekt `task_group` v průběhu zrušení (nebo je zaručena jeho krátce).

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [zrušení](../cancellation-in-the-ppl.md).

## <a name="run"></a>spouštěl

Naplánuje úlohu na objekt `task_group`. Pokud je objekt `task_handle` předán jako parametr pro `run`, je volajícím zodpovědný za správu životnosti objektu `task_handle`. Verze metody, která přebírá odkaz na objekt funkce jako parametr, zahrnuje přidělení haldy uvnitř modulu runtime, který může být méně kvalitní než použití verze, která přebírá odkaz na objekt `task_handle`. Verze, která přebírá parametr `_Placement` způsobí, že se úkol na základě umístění určeného parametrem posune na spuštěno.

```cpp
template<
   typename _Function
>
void run(
   const _Function& _Func
);

template<
   typename _Function
>
void run(
   const _Function& _Func,
   location& _Placement
);

template<
   typename _Function
>
void run(
   task_handle<_Function>& _Task_handle
);

template<
   typename _Function
>
void run(
   task_handle<_Function>& _Task_handle,
   location& _Placement
);
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ objektu funkce, který bude vyvolán pro provedení textu popisovače úlohy.

*_Func*<br/>
Funkce, která bude volána k vyvolání těla úkolu. Může to být výraz lambda nebo jiný objekt, který podporuje verzi operátoru volání funkce s podpisem `void operator()()`.

*_Placement*<br/>
Odkaz na umístění, kde by měla být spuštěna úloha reprezentovaná parametrem `_Func`.

*_Task_handle*<br/>
Popisovač plánované práce. Všimněte si, že volající má zodpovědnost za životnost tohoto objektu. Modul runtime bude nadále čekat na živý, dokud není pro tento objekt `task_group` volána metoda `wait` nebo `run_and_wait`.

### <a name="remarks"></a>Poznámky

Modul runtime naplánuje poskytnutou pracovní funkci na pozdější dobu, což může být po návratu funkce volání. Tato metoda používá objekt [task_handle](task-handle-class.md) k uložení kopie zadané pracovní funkce. Proto všechny změny stavu, ke kterým dojde v objektu funkce, který předáte této metodě, se nezobrazí ve vaší kopii objektu funkce. Kromě toho se ujistěte, že životnost všech objektů, které předáváte ukazatelem nebo odkazem na pracovní funkci, zůstávají platné, dokud funkce Work nevrátí.

Pokud `task_group` destrukturuje jako výsledek uvolnění zásobníku z výjimky, není nutné zaručit, že bylo provedeno volání metody `wait` nebo `run_and_wait`. V takovém případě destruktor bude patřičně zrušit a počkat na dokončení úlohy reprezentované parametrem `_Task_handle`.

Metoda vyvolá výjimku [invalid_multiple_scheduling](invalid-multiple-scheduling-class.md) , pokud popisovač úlohy předaný parametrem `_Task_handle` již byl naplánován na objekt skupiny úloh prostřednictvím metody `run` a neexistuje žádné volání metody `wait` nebo `run_and_wait` v této skupině úloh.

## <a name="run_and_wait"></a>run_and_wait

Naplánuje spuštění úlohy vložené do volajícího kontextu s asistencí objektu `task_group` pro úplnou podporu zrušení. Funkce potom počká, dokud nebudou všechny práce na objektu `task_group` buď dokončeny, nebo zrušeny. Pokud je objekt `task_handle` předán jako parametr pro `run_and_wait`, je volajícím zodpovědný za správu životnosti objektu `task_handle`.

```cpp
template<
   class _Function
>
task_group_status run_and_wait(
   task_handle<_Function>& _Task_handle
);

template<
   class _Function
>
task_group_status run_and_wait(
   const _Function& _Func
);
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ objektu funkce, který bude vyvolán pro spuštění těla úkolu.

*_Task_handle*<br/>
Popisovač úlohy, který bude spuštěn vložený v kontextu volání. Všimněte si, že volající má zodpovědnost za životnost tohoto objektu. Modul runtime bude nadále čekat na živý, dokud metoda `run_and_wait` nedokončí provádění.

*_Func*<br/>
Funkce, která bude volána k vyvolání těla práce. Může to být výraz lambda nebo jiný objekt, který podporuje verzi operátoru volání funkce s podpisem `void operator()()`.

### <a name="return-value"></a>Návratová hodnota

Označení, zda bylo čekání splněno, nebo byla zrušena skupina úloh z důvodu explicitní operace zrušení nebo vyvolání výjimky z jedné z jejích úkolů. Další informace najdete v tématu [task_group_status](concurrency-namespace-enums.md#task_group_status).

### <a name="remarks"></a>Poznámky

Všimněte si, že jedna nebo více úloh, které jsou naplánovány na tento objekt `task_group`, mohou provádět vložené v kontextu volání.

Pokud jedna nebo více úloh naplánovaných tomuto objektu `task_group` vyvolá výjimku, modul runtime vybere jednu takovou výjimku, kterou si zvolí, a rozšíří ji ze volání metody `run_and_wait`.

Při návratu z metody `run_and_wait` u objektu `task_group` modul runtime obnoví objekt do čistého stavu, ve kterém lze znovu použít. To zahrnuje případ, kdy byl objekt `task_group` zrušen.

V nevýjimečné cestě spuštění máte mandát volat buď tuto metodu, nebo metodu `wait` před tím, než se spustí destruktor `task_group`.

## <a name="ctor"></a>task_group

Vytvoří nový objekt `task_group`.

```cpp
task_group();

task_group(
   cancellation_token _CancellationToken
);
```

### <a name="parameters"></a>Parametry

*_CancellationToken*<br/>
Token zrušení, který se má přidružit k této skupině úloh. Po zrušení tokenu se skupina úloh zruší.

### <a name="remarks"></a>Poznámky

Konstruktor, který přijímá token zrušení, vytvoří `task_group`, který se zruší při zrušení zdroje přidruženého k tokenu. Poskytnutí explicitního tokenu zrušení taky izoluje tuto skupinu úloh od účasti v implicitním zrušení z nadřazené skupiny s jiným tokenem nebo bez tokenu.

## <a name="dtor"></a>~ task_group

Odstraní objekt `task_group`. Očekává se, že zavoláte buď metodu `wait` nebo `run_and_wait` objektu před spuštěním destruktoru, pokud se destruktor neprovádí jako výsledek zrušení zásobníku z důvodu výjimky.

```cpp
~task_group();
```

### <a name="remarks"></a>Poznámky

Pokud je destruktor spuštěn jako výsledek normálního spuštění (například bez převinutí zásobníku z důvodu výjimky) a nejsou volány žádné metody `wait` ani `run_and_wait`, může destruktor vyvolat výjimku [missing_wait](missing-wait-class.md) .

## <a name="wait"></a>Počkej

Počká, dokud nebudou všechny práce na `task_group`m objektu buď dokončeny, nebo zrušeny.

```cpp
task_group_status wait();
```

### <a name="return-value"></a>Návratová hodnota

Označení, zda bylo čekání splněno, nebo byla zrušena skupina úloh z důvodu explicitní operace zrušení nebo vyvolání výjimky z jedné z jejích úkolů. Další informace najdete v tématu [task_group_status](concurrency-namespace-enums.md#task_group_status).

### <a name="remarks"></a>Poznámky

Všimněte si, že jedna nebo více úloh, které jsou naplánovány na tento objekt `task_group`, mohou provádět vložené v kontextu volání.

Pokud jedna nebo více úloh naplánovaných tomuto objektu `task_group` vyvolá výjimku, modul runtime vybere jednu takovou výjimku, kterou si zvolí, a rozšíří ji ze volání metody `wait`.

Volání `wait` u objektu `task_group` ho obnoví do čistého stavu, ve kterém se dá znovu použít. To zahrnuje případ, kdy byl objekt `task_group` zrušen.

V nevýjimečné cestě spuštění máte mandát volat buď tuto metodu, nebo metodu `run_and_wait` před tím, než se spustí destruktor `task_group`.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[structured_task_group – třída](structured-task-group-class.md)<br/>
[task_handle – třída](task-handle-class.md)
