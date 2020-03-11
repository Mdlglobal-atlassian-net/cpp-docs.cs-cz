---
title: CurrentScheduler – třída
ms.date: 11/04/2016
f1_keywords:
- CurrentScheduler
- CONCRT/concurrency::CurrentScheduler
- CONCRT/concurrency::CurrentScheduler::Create
- CONCRT/concurrency::CurrentScheduler::CreateScheduleGroup
- CONCRT/concurrency::CurrentScheduler::Detach
- CONCRT/concurrency::CurrentScheduler::Get
- CONCRT/concurrency::CurrentScheduler::GetNumberOfVirtualProcessors
- CONCRT/concurrency::CurrentScheduler::GetPolicy
- CONCRT/concurrency::CurrentScheduler::Id
- CONCRT/concurrency::CurrentScheduler::IsAvailableLocation
- CONCRT/concurrency::CurrentScheduler::RegisterShutdownEvent
- CONCRT/concurrency::CurrentScheduler::ScheduleTask
helpviewer_keywords:
- CurrentScheduler class
ms.assetid: 31c20e0e-4cdf-49b4-8220-d726130aad2b
ms.openlocfilehash: 6bf61af9ff55722553353a045c87501dbd27fad9
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78867124"
---
# <a name="currentscheduler-class"></a>CurrentScheduler – třída

Představuje abstrakci aktuálního plánovače přidruženého k volajícímu kontextu.

## <a name="syntax"></a>Syntaxe

```cpp
class CurrentScheduler;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Vytvoření](#create)|Vytvoří nový Plánovač, jehož chování je popsáno parametrem `_Policy` a připojí ho k volajícímu kontextu. Nově vytvořený Plánovač se stane aktuálním plánovačem pro volající kontext.|
|[CreateScheduleGroup –](#createschedulegroup)|Přetíženo. Vytvoří novou skupinu plánu v rámci plánovače přidruženého k volajícímu kontextu. Verze, která přebírá parametr `_Placement` způsobí, že úlohy v nově vytvořené skupině Schedule budou posunuty ke spuštění v umístění určeném parametrem.|
|[Detach](#detach)|Odpojí aktuálního plánovače od volajícího kontextu a obnoví dříve připojeného plánovače jako aktuální Plánovač, pokud existuje. Po návratu této metody je volající kontext spravován plánovačem, který byl dříve připojen k kontextu pomocí metody `CurrentScheduler::Create` nebo `Scheduler::Attach`.|
|[Get](#get)|Vrátí ukazatel na Scheduler přidružený k volajícímu kontextu, označovaný také jako aktuální Plánovač.|
|[Getnumberofvirtualprocessors –](#getnumberofvirtualprocessors)|Vrátí aktuální počet virtuálních procesorů pro Plánovač přidružený k volajícímu kontextu.|
|[GetPolicy –](#getpolicy)|Vrátí kopii zásady, pomocí které byl vytvořen aktuální Plánovač.|
|[ID](#id)|Vrátí jedinečný identifikátor aktuálního plánovače.|
|[Isavailablelocation –](#isavailablelocation)|Určuje, zda je dané umístění k dispozici v aktuálním plánovači.|
|[RegisterShutdownEvent –](#registershutdownevent)|Způsobí, že popisovač události systému Windows předaný parametrem `_ShutdownEvent` bude signalizované, když se Plánovač přidružený k aktuálnímu kontextu ukončí a zničí sám sebe. V okamžiku signalizace události je dokončena veškerá práce, která byla naplánována do plánovače. Pomocí této metody lze zaregistrovat více událostí vypnutí.|
|[ScheduleTask –](#scheduletask)|Přetíženo. Naplánuje úlohu s lehkým zatížením v rámci plánovače přidruženého k volajícímu kontextu. Úloha s lehkým zatížením bude umístěna do skupiny plánování určené modulem runtime. Verze, která přebírá parametr `_Placement` způsobí, že se úloha na zadaném umístění posune směrem k provedení.|

## <a name="remarks"></a>Poznámky

Pokud není k volajícímu kontextu přidružen žádný Plánovač (viz [Scheduler](scheduler-class.md)), mnoho metod v rámci třídy `CurrentScheduler` bude mít za následek připojení výchozího plánovače procesu. To může také znamenat, že výchozí Plánovač procesu se vytvoří během takového volání.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CurrentScheduler`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ConcRT. h

**Obor názvů:** souběžnost

## <a name="create"></a>Vytvořeny

Vytvoří nový Plánovač, jehož chování je popsáno parametrem `_Policy` a připojí ho k volajícímu kontextu. Nově vytvořený Plánovač se stane aktuálním plánovačem pro volající kontext.

```cpp
static void __cdecl Create(const SchedulerPolicy& _Policy);
```

### <a name="parameters"></a>Parametry

*_Policy*<br/>
Zásady plánovače, které popisují chování nově vytvořeného plánovače.

### <a name="remarks"></a>Poznámky

Příloha plánovače do volajícího kontextu implicitně umístí počet odkazů do plánovače.

Po vytvoření plánovače pomocí metody `Create` je třeba zavolat metodu [CurrentScheduler::D etach](#detach) v určitém okamžiku v budoucnu, aby bylo možné Plánovač vypnout.

Pokud je tato metoda volána z kontextu, který je již připojen k jinému plánovači, existující Plánovač je zapamatovat jako předchozí Plánovač a nově vytvořený Plánovač se bude považovat za aktuálního plánovače. Při volání metody `CurrentScheduler::Detach` v pozdějším bodě bude předchozí Plánovač obnoven jako aktuální Plánovač.

Tato metoda může vyvolat různé výjimky, včetně [scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md) a [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md).

## <a name="createschedulegroup"></a>CreateScheduleGroup –

Vytvoří novou skupinu plánu v rámci plánovače přidruženého k volajícímu kontextu. Verze, která přebírá parametr `_Placement` způsobí, že úlohy v nově vytvořené skupině Schedule budou posunuty ke spuštění v umístění určeném parametrem.

```cpp
static ScheduleGroup* __cdecl CreateScheduleGroup();

static ScheduleGroup* __cdecl CreateScheduleGroup(location& _Placement);
```

### <a name="parameters"></a>Parametry

*_Placement*<br/>
Odkaz na umístění, kde budou úkoly v rámci skupiny plánování posunuty k provedení.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nově vytvořenou skupinu plánu. Na tento objekt `ScheduleGroup` je umístěn počáteční počet odkazů.

### <a name="remarks"></a>Poznámky

Tato metoda způsobí, že se vytvoří výchozí Plánovač procesu a/nebo připojí se k volajícímu kontextu, pokud není momentálně k volajícímu kontextu přidružen žádný Plánovač.

Až skončíte s plánováním práce, musíte vyvolat metodu [release](schedulegroup-class.md#release) pro skupinu plánů. Plánovač odstraní skupinu plánů, když je dokončená veškerá práce zařazená do fronty.

Všimněte si, že pokud jste tento Plánovač výslovně vytvořili, musíte před vydáním aktuálního kontextu z něj uvolnit všechny odkazy na jejich plánování ve skupinách.

## <a name="detach"></a>Dělitel

Odpojí aktuálního plánovače od volajícího kontextu a obnoví dříve připojeného plánovače jako aktuální Plánovač, pokud existuje. Po návratu této metody je volající kontext spravován plánovačem, který byl dříve připojen k kontextu pomocí metody `CurrentScheduler::Create` nebo `Scheduler::Attach`.

```cpp
static void __cdecl Detach();
```

### <a name="remarks"></a>Poznámky

Metoda `Detach` implicitně odstraní počet odkazů z plánovače.

Pokud není k volajícímu kontextu připojen žádný Plánovač, volání této metody způsobí, že bude vyvolána výjimka [scheduler_not_attached](scheduler-not-attached-class.md) .

Volání této metody z kontextu, který je interní a spravovaný plánovačem, nebo kontextu, který byl připojen pomocí metody jiné než [Scheduler:: Attach](scheduler-class.md#attach) nebo [CurrentScheduler:: Create](#create) , bude mít za následek vyvolanou výjimku [improper_scheduler_detach](improper-scheduler-detach-class.md) .

## <a name="get"></a>Čtěte

Vrátí ukazatel na Scheduler přidružený k volajícímu kontextu, označovaný také jako aktuální Plánovač.

```cpp
static Scheduler* __cdecl Get();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na Plánovač přidružený k volajícímu kontextu (aktuální Plánovač).

### <a name="remarks"></a>Poznámky

Tato metoda způsobí, že se vytvoří výchozí Plánovač procesu a/nebo připojí se k volajícímu kontextu, pokud není momentálně k volajícímu kontextu přidružen žádný Plánovač. Do objektu `Scheduler` vráceného touto metodou se neumísťují žádné další odkazy.

## <a name="getnumberofvirtualprocessors"></a>Getnumberofvirtualprocessors –

Vrátí aktuální počet virtuálních procesorů pro Plánovač přidružený k volajícímu kontextu.

```cpp
static unsigned int __cdecl GetNumberOfVirtualProcessors();
```

### <a name="return-value"></a>Návratová hodnota

Pokud je Plánovač přidružen k volajícímu kontextu, aktuální počet virtuálních procesorů tohoto plánovače; v opačném případě hodnota `-1`.

### <a name="remarks"></a>Poznámky

Tato metoda nebude mít za následek přílohu Scheduleru, pokud volající kontext ještě není přidružen ke Scheduleru.

Návratová hodnota z této metody je okamžitý odběr vzorkování počtu virtuálních procesorů pro Plánovač přidružený k volajícímu kontextu. Tato hodnota může být zastaralá na okamžik, kdy se vrátí.

## <a name="getpolicy"></a>GetPolicy –

Vrátí kopii zásady, pomocí které byl vytvořen aktuální Plánovač.

```cpp
static SchedulerPolicy __cdecl GetPolicy();
```

### <a name="return-value"></a>Návratová hodnota

Kopie zásady, pomocí které byl vytvořen aktuální Plánovač.

### <a name="remarks"></a>Poznámky

Tato metoda způsobí, že se vytvoří výchozí Plánovač procesu a/nebo připojí se k volajícímu kontextu, pokud není momentálně k volajícímu kontextu přidružen žádný Plánovač.

## <a name="id"></a>Účet

Vrátí jedinečný identifikátor aktuálního plánovače.

```cpp
static unsigned int __cdecl Id();
```

### <a name="return-value"></a>Návratová hodnota

Pokud je Plánovač spojen s volajícím kontextem, jedinečný identifikátor pro tohoto plánovače; v opačném případě hodnota `-1`.

### <a name="remarks"></a>Poznámky

Tato metoda nebude mít za následek přílohu Scheduleru, pokud volající kontext ještě není přidružen ke Scheduleru.

## <a name="isavailablelocation"></a>Isavailablelocation –

Určuje, zda je dané umístění k dispozici v aktuálním plánovači.

```cpp
static bool __cdecl IsAvailableLocation(const location& _Placement);
```

### <a name="parameters"></a>Parametry

*_Placement*<br/>
Odkaz na umístění pro dotazování aktuálního plánovače o.

### <a name="return-value"></a>Návratová hodnota

Označení, zda je umístění zadané v argumentu `_Placement` k dispozici v aktuálním plánovači.

### <a name="remarks"></a>Poznámky

Tato metoda nebude mít za následek přílohu Scheduleru, pokud volající kontext ještě není přidružen ke Scheduleru.

Všimněte si, že návratová hodnota je okamžitý odběr vzorkování, zda je dané umístění k dispozici. V případě existence více schedulerů může dynamická správa prostředků přidávat nebo odbírat prostředky z schedulerů v jakémkoli okamžiku. K tomu by se mohlo stát, že dané umístění může změnit dostupnost.

## <a name="registershutdownevent"></a>RegisterShutdownEvent –

Způsobí, že popisovač události systému Windows předaný parametrem `_ShutdownEvent` bude signalizované, když se Plánovač přidružený k aktuálnímu kontextu ukončí a zničí sám sebe. V okamžiku signalizace události je dokončena veškerá práce, která byla naplánována do plánovače. Pomocí této metody lze zaregistrovat více událostí vypnutí.

```cpp
static void __cdecl RegisterShutdownEvent(HANDLE _ShutdownEvent);
```

### <a name="parameters"></a>Parametry

*_ShutdownEvent*<br/>
Popisovač objektu události systému Windows, který bude signalizovat modulem runtime při ukončení plánovače přidruženého k aktuálnímu kontextu a zničení sám sebe.

### <a name="remarks"></a>Poznámky

Pokud není k volajícímu kontextu připojen žádný Plánovač, volání této metody způsobí, že bude vyvolána výjimka [scheduler_not_attached](scheduler-not-attached-class.md) .

## <a name="scheduletask"></a>ScheduleTask –

Naplánuje úlohu s lehkým zatížením v rámci plánovače přidruženého k volajícímu kontextu. Úloha s lehkým zatížením bude umístěna do skupiny plánování určené modulem runtime. Verze, která přebírá parametr `_Placement` způsobí, že se úloha na zadaném umístění posune směrem k provedení.

```cpp
static void __cdecl ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data);

static void __cdecl ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data,
    location& _Placement);
```

### <a name="parameters"></a>Parametry

*_Proc*<br/>
Ukazatel na funkci, která se má provést, aby provedla tělo úlohy s lehkým zatížením.

*_Data*<br/>
Anulování ukazatele na data, která budou předána do těla úkolu jako parametr.

*_Placement*<br/>
Odkaz na umístění, kde bude úloha s lehkým zatížením posunuta k provedení v.

### <a name="remarks"></a>Poznámky

Tato metoda způsobí, že se vytvoří výchozí Plánovač procesu a/nebo připojí se k volajícímu kontextu, pokud není momentálně k volajícímu kontextu přidružen žádný Plánovač.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[Scheduler – třída](scheduler-class.md)<br/>
[PolicyElementKey –](concurrency-namespace-enums.md)<br/>
[Plánovač úloh](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
