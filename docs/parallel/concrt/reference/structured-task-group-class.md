---
title: structured_task_group – třída
ms.date: 11/04/2016
f1_keywords:
- structured_task_group
- PPL/concurrency::structured_task_group
- PPL/concurrency::structured_task_group::structured_task_group
- PPL/concurrency::structured_task_group::cancel
- PPL/concurrency::structured_task_group::is_canceling
- PPL/concurrency::structured_task_group::run
- PPL/concurrency::structured_task_group::run_and_wait
- PPL/concurrency::structured_task_group::wait
helpviewer_keywords:
- structured_task_group class
ms.assetid: 742afa8c-c7b6-482c-b0ba-04c809927b22
ms.openlocfilehash: 93dd79b755f79dcb4857c1b1c4856362b0bd45dd
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78884115"
---
# <a name="structured_task_group-class"></a>structured_task_group – třída

Třída `structured_task_group` představuje vysoce strukturovaná kolekce paralelní práce. Jednotlivé paralelní úkoly lze zařadit do fronty `structured_task_group` pomocí objektů `task_handle` a počkat na jejich dokončení, nebo zrušit skupinu úloh předtím, než budou dokončeny. tím dojde k přerušení všech úloh, které nezačaly běžet.

## <a name="syntax"></a>Syntaxe

```cpp
class structured_task_group;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[structured_task_group](#ctor)|Přetíženo. Vytvoří nový objekt `structured_task_group`.|
|[~ structured_task_group destruktor](#dtor)|Odstraní objekt `structured_task_group`. Očekává se, že před provedením destruktoru zavoláte metodu `wait` nebo `run_and_wait` objektu, pokud se destruktor neprovádí jako výsledek zrušení zásobníku z důvodu výjimky.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[operaci](#cancel)|Provede se nejvhodnějším pokusem o zrušení podstromu práce s kořenem v této skupině úloh. Pokud je to možné, všechny úlohy naplánované ve skupině úloh se přestanou přeruší.|
|[is_canceling](#is_canceling)|Informuje volajícího, zda je skupina úloh aktuálně v průběhu zrušení. To neznamená nutně najevo, že byla volána metoda `cancel` pro objekt `structured_task_group` (i když taková hodnota je v tomto případě taková, že tato metoda vrátí **hodnotu true**). Může se jednat o případ, že objekt `structured_task_group` spouští inline a další v pracovní větvi se zrušila. V případech, jako jsou ty, kde modul runtime může určit předem čas, kdy bude zrušení projít tímto objektem `structured_task_group`, bude vrácena také **hodnota true** .|
|[spouštěl](#run)|Přetíženo. Naplánuje úlohu na objekt `structured_task_group`. Volající spravuje dobu života objektu `task_handle` předaného v parametru `_Task_handle`. Verze, která přebírá parametr `_Placement` způsobí, že se úkol na základě umístění určeného parametrem posune na spuštěno.|
|[run_and_wait](#run_and_wait)|Přetíženo. Naplánuje spuštění úlohy vložené do volajícího kontextu s asistencí objektu `structured_task_group` pro úplnou podporu zrušení. Pokud je objekt `task_handle` předán jako parametr pro `run_and_wait`, je volajícím zodpovědný za správu životnosti objektu `task_handle`. Funkce potom počká, dokud nebudou všechny práce na objektu `structured_task_group` buď dokončeny, nebo zrušeny.|
|[Počkej](#wait)|Počká, dokud nebude dokončena veškerá práce na `structured_task_group` nebo zrušena.|

## <a name="remarks"></a>Poznámky

K dispozici je řada vážných omezení pro použití objektu `structured_task_group`, aby bylo možné získat výkon:

- Jeden objekt `structured_task_group` nemůže být použit více vlákny. Všechny operace s objektem `structured_task_group` musí být provedeny vláknem, který objekt vytvořil. Dvě výjimky z tohoto pravidla jsou členské funkce `cancel` a `is_canceling`. Objekt nesmí být v seznamu zachycení výrazu lambda a lze jej použít v rámci úlohy, pokud úloha nepoužívá jednu z operací zrušení.

- Všechny úlohy naplánované na objekt `structured_task_group` jsou plánovány pomocí `task_handle` objektů, které je nutné explicitně spravovat život.

- Více skupin lze použít pouze v absolutním vnořeném pořadí. Pokud jsou deklarovány dva objekty `structured_task_group`, musí být druhá deklarovaná (vnitřní) deklarace destrukci před jakoukoliv metodou, s výjimkou `cancel` nebo `is_canceling` je volána na první straně (vnější). Tento stav má hodnotu true v případě pouhého deklarování více `structured_task_group` objektů ve stejném nebo funkčně vnořeném oboru a také v případě úkolu, který byl zařazen do fronty `structured_task_group` prostřednictvím `run` nebo `run_and_wait`ch metod.

- Na rozdíl od obecné `task_group` třídy jsou všechny stavy ve `structured_task_group` třídy finální. Po zařazení úkolů do skupiny a čekání na jejich dokončení můžete znovu použít stejnou skupinu.

Další informace najdete v tématu [Task paralelismus](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`structured_task_group`

## <a name="requirements"></a>Požadavky

**Záhlaví:** PPL. h

**Obor názvů:** souběžnost

## <a name="cancel"></a>operaci

Provede se nejvhodnějším pokusem o zrušení podstromu práce s kořenem v této skupině úloh. Pokud je to možné, všechny úlohy naplánované ve skupině úloh se přestanou přeruší.

```cpp
void cancel();
```

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [zrušení](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

## <a name="is_canceling"></a>is_canceling

Informuje volajícího, zda je skupina úloh aktuálně v průběhu zrušení. To neznamená nutně najevo, že byla volána metoda `cancel` pro objekt `structured_task_group` (i když taková hodnota je v tomto případě taková, že tato metoda vrátí **hodnotu true**). Může se jednat o případ, že objekt `structured_task_group` spouští inline a další v pracovní větvi se zrušila. V případech, jako jsou ty, kde modul runtime může určit předem čas, kdy bude zrušení projít tímto objektem `structured_task_group`, bude vrácena také **hodnota true** .

```cpp
bool is_canceling();
```

### <a name="return-value"></a>Návratová hodnota

Označení toho, zda je objekt `structured_task_group` v průběhu zrušení (nebo je zaručena jeho krátce).

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [zrušení](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

## <a name="run"></a>spouštěl

Naplánuje úlohu na objekt `structured_task_group`. Volající spravuje dobu života objektu `task_handle` předaného v parametru `_Task_handle`. Verze, která přebírá parametr `_Placement` způsobí, že se úkol na základě umístění určeného parametrem posune na spuštěno.

```cpp
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
Typ objektu funkce, který bude vyvolán pro provedení textu popisovače úlohy.

*_Task_handle*<br/>
Popisovač plánované práce. Všimněte si, že volající má zodpovědnost za životnost tohoto objektu. Modul runtime bude nadále čekat na živý, dokud není pro tento objekt `structured_task_group` volána metoda `wait` nebo `run_and_wait`.

*_Placement*<br/>
Odkaz na umístění, kde by měla být spuštěna úloha reprezentovaná parametrem `_Task_handle`.

### <a name="remarks"></a>Poznámky

Modul runtime vytvoří kopii pracovní funkce, kterou předáte do této metody. Všechny změny stavu, ke kterým dojde v objektu funkce, který předáte této metodě, se nezobrazí ve vaší kopii objektu funkce.

Pokud `structured_task_group` destrukturuje jako výsledek uvolnění zásobníku z výjimky, není nutné zaručit, že bylo provedeno volání metody `wait` nebo `run_and_wait`. V takovém případě destruktor bude patřičně zrušit a počkat na dokončení úlohy reprezentované parametrem `_Task_handle`.

Vyvolá výjimku [invalid_multiple_scheduling](invalid-multiple-scheduling-class.md) , pokud je popisovač úlohy předaný parametrem `_Task_handle` již naplánován na objekt skupiny úloh prostřednictvím metody `run` a neexistuje žádné volání metody `wait` nebo `run_and_wait` v této skupině úloh.

## <a name="run_and_wait"></a>run_and_wait

Naplánuje spuštění úlohy vložené do volajícího kontextu s asistencí objektu `structured_task_group` pro úplnou podporu zrušení. Pokud je objekt `task_handle` předán jako parametr pro `run_and_wait`, je volajícím zodpovědný za správu životnosti objektu `task_handle`. Funkce potom počká, dokud nebudou všechny práce na objektu `structured_task_group` buď dokončeny, nebo zrušeny.

```cpp
template<class _Function>
task_group_status run_and_wait(task_handle<_Function>& _Task_handle);

template<class _Function>
task_group_status run_and_wait(const _Function& _Func);
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ objektu funkce, který bude vyvolán pro provedení úlohy.

*_Task_handle*<br/>
Popisovač úlohy, který bude spuštěn vložený v kontextu volání. Všimněte si, že volající má zodpovědnost za životnost tohoto objektu. Modul runtime bude nadále čekat na živý, dokud metoda `run_and_wait` nedokončí provádění.

*_Func*<br/>
Funkce, která bude volána k vyvolání těla práce. Může to být lambda nebo jiný objekt, který podporuje verzi operátoru volání funkce s podpisem `void operator()()`.

### <a name="return-value"></a>Návratová hodnota

Označení, zda bylo čekání splněno, nebo byla zrušena skupina úloh z důvodu explicitní operace zrušení nebo vyvolání výjimky z jedné z jejích úkolů. Další informace najdete v tématu [task_group_status](concurrency-namespace-enums.md)

### <a name="remarks"></a>Poznámky

Všimněte si, že jedna nebo více úloh, které jsou naplánovány na tento objekt `structured_task_group`, mohou provádět vložené v kontextu volání.

Pokud jedna nebo více úloh naplánovaných tomuto objektu `structured_task_group` vyvolá výjimku, modul runtime vybere jednu takovou výjimku, kterou si zvolí, a rozšíří ji ze volání metody `run_and_wait`.

Po návratu této funkce se objekt `structured_task_group` považuje za konečný stav a neměl by se používat. Všimněte si, že využití po vrácení metody `run_and_wait` bude mít za následek nedefinované chování.

V nevýjimečné cestě spuštění máte mandát volat buď tuto metodu, nebo metodu `wait` před tím, než se spustí destruktor `structured_task_group`.

## <a name="ctor"></a>structured_task_group

Vytvoří nový objekt `structured_task_group`.

```cpp
structured_task_group();

structured_task_group(cancellation_token _CancellationToken);
```

### <a name="parameters"></a>Parametry

*_CancellationToken*<br/>
Token zrušení, který se má přidružit k této strukturované skupině úloh. Strukturovaný skupinový úkol bude po zrušení tokenu zrušen.

### <a name="remarks"></a>Poznámky

Konstruktor, který přijímá token zrušení, vytvoří `structured_task_group`, který se zruší při zrušení zdroje přidruženého k tokenu. Poskytnutí explicitního tokenu zrušení taky izoluje tuto strukturovanou skupinu úloh od účasti v implicitním zrušení z nadřazené skupiny s jiným tokenem nebo bez tokenu.

## <a name="dtor"></a>~ structured_task_group

Odstraní objekt `structured_task_group`. Očekává se, že před provedením destruktoru zavoláte metodu `wait` nebo `run_and_wait` objektu, pokud se destruktor neprovádí jako výsledek zrušení zásobníku z důvodu výjimky.

```cpp
~structured_task_group();
```

### <a name="remarks"></a>Poznámky

Pokud je destruktor spuštěn jako výsledek normálního spuštění (například bez převinutí zásobníku z důvodu výjimky) a nejsou volány žádné metody `wait` ani `run_and_wait`, může destruktor vyvolat výjimku [missing_wait](missing-wait-class.md) .

## <a name="wait"></a>Počkej

Počká, dokud nebude dokončena veškerá práce na `structured_task_group` nebo zrušena.

```cpp
task_group_status wait();
```

### <a name="return-value"></a>Návratová hodnota

Označení, zda bylo čekání splněno, nebo byla zrušena skupina úloh z důvodu explicitní operace zrušení nebo vyvolání výjimky z jedné z jejích úkolů. Další informace najdete v tématu [task_group_status](concurrency-namespace-enums.md)

### <a name="remarks"></a>Poznámky

Všimněte si, že jedna nebo více úloh, které jsou naplánovány na tento objekt `structured_task_group`, mohou provádět vložené v kontextu volání.

Pokud jedna nebo více úloh naplánovaných tomuto objektu `structured_task_group` vyvolá výjimku, modul runtime vybere jednu takovou výjimku, kterou si zvolí, a rozšíří ji ze volání metody `wait`.

Po návratu této funkce se objekt `structured_task_group` považuje za konečný stav a neměl by se používat. Všimněte si, že využití po vrácení metody `wait` bude mít za následek nedefinované chování.

V nevýjimečné cestě spuštění máte mandát volat buď tuto metodu, nebo metodu `run_and_wait` před tím, než se spustí destruktor `structured_task_group`.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[task_group – třída](task-group-class.md)<br/>
[task_handle – třída](task-handle-class.md)
