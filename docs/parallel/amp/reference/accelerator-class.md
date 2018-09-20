---
title: Accelerator – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- AMPRT/accelerator
- AMPRT/Concurrency::accelerator::accelerator
- AMPRT/Concurrency::accelerator::create_view
- AMPRT/Concurrency::accelerator::get_all
- AMPRT/Concurrency::accelerator::get_auto_selection_view
- AMPRT/Concurrency::accelerator::get_dedicated_memory
- AMPRT/Concurrency::accelerator::get_default_cpu_access_type
- AMPRT/Concurrency::accelerator::get_default_view
- AMPRT/Concurrency::accelerator::get_description
- AMPRT/Concurrency::accelerator::get_device_path
- AMPRT/Concurrency::accelerator::get_has_display
- AMPRT/Concurrency::accelerator::get_is_debug
- AMPRT/Concurrency::accelerator::get_is_emulated
- AMPRT/Concurrency::accelerator::get_supports_cpu_shared_memory
- AMPRT/Concurrency::accelerator::get_supports_double_precision
- AMPRT/Concurrency::accelerator::get_supports_limited_double_precision
- AMPRT/Concurrency::accelerator::get_version
- AMPRT/Concurrency::accelerator::set_default
- AMPRT/Concurrency::accelerator::set_default_cpu_access_type
- AMPRT/Concurrency::accelerator::cpu_accelerator
- AMPRT/Concurrency::accelerator::dedicated_memory
- AMPRT/Concurrency::accelerator::default_accelerator
- AMPRT/Concurrency::accelerator::default_cpu_access_type
- AMPRT/Concurrency::accelerator::default_view
- AMPRT/Concurrency::accelerator::description
- AMPRT/Concurrency::accelerator::device_path
- AMPRT/Concurrency::accelerator::direct3d_ref
- AMPRT/Concurrency::accelerator::direct3d_warp
- AMPRT/Concurrency::accelerator::has_display
- AMPRT/Concurrency::accelerator::is_debug
- AMPRT/Concurrency::accelerator::is_emulated
- AMPRT/Concurrency::accelerator::supports_cpu_shared_memory
- AMPRT/Concurrency::accelerator::supports_double_precision
- AMPRT/Concurrency::accelerator::supports_limited_double_precision
- AMPRT/Concurrency::accelerator::version
dev_langs:
- C++
helpviewer_keywords:
- accelerator class
ms.assetid: 37eed593-cf87-4611-9cdc-e98df6c2377a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7748ae0f3993c1df97dcf97308fd6dfbfafdc8b6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375870"
---
# <a name="accelerator-class"></a>accelerator – třída

Akcelerátor je funkce hardwaru, která je optimalizovaná pro paralelní výpočty. Akcelerátor může být zařízení připojené k sběrnici PCIe (například GPU), nebo může být rozšířená instrukční sada v hlavním CPU.

## <a name="syntax"></a>Syntaxe

```
class accelerator;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[akcelerátor konstruktor](#ctor)|Inicializuje novou instanci třídy `accelerator` třídy.|
|[~ accelerator – destruktor](#ctor)|Odstraní `accelerator` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[create_view](#create_view)|Vytvoří a vrátí `accelerator_view` objekt na tomto akcelerátoru.|
|[get_all](#get_all)|Vrátí vektor `accelerator` objekty, které představují všechny dostupné akcelerátory.|
|[get_auto_selection_view](#get_auto_selection_view)|Vrátí automatický výběr `accelerator_view`.|
|[get_dedicated_memory –](#get_dedicated_memory)|Vrátí velikost vyhrazené paměti pro `accelerator`, v kilobajtech.|
|[get_default_cpu_access_type](#get_default_cpu_access_type)|Vrátí výchozí [access_type](concurrency-namespace-enums-amp.md#access_type) pro vyrovnávací paměti vytvořené na tomto akcelerátoru.|
|[get_default_view](#get_default_view)|Vrátí výchozí `accelerator_view` objekt, který je přidružený `accelerator`.|
|[get_description –](#get_description)|Vrátí krátký popis `accelerator` zařízení.|
|[get_device_path](#get_device_path)|Vrátí cestu k zařízení.|
|[get_has_display](#get_has_display)|Určuje, zda `accelerator` je připojen k displeji.|
|[get_is_debug](#get_is_debug)|Určuje, zda `accelerator` má povolenu vrstvu DEBUG pro rozsáhlé hlášení chyb.|
|[get_is_emulated](#get_is_emulated)|Určuje, zda `accelerator` je emulován.|
|[get_supports_cpu_shared_memory](#get_supports_cpu_shared_memory)|Určuje, zda `accelerator` podporuje sdílenou paměť|
|[get_supports_double_precision](#get_supports_double_precision)|Určuje, zda `accelerator` je připojen k displeji.|
|[get_supports_limited_double_precision](#get_supports_limited_double_precision)|Určuje, zda `accelerator` má omezenou podporu pro matematiku s dvojitou přesností.|
|[get_version –](#get_version)|Vrátí verzi `accelerator`.|
|[set_default](#set_default)|Vrátí cestu k výchozí akcelerátor.|
|[set_default_cpu_access_type](#set_default_cpu_access_type)|Nastaví výchozí procesor [access_type](concurrency-namespace-enums-amp.md#access_type)pro pole a implicitní přidělení paměti provedené v tomto `accelerator`.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operator!=](#operator_neq)|Porovná tento `accelerator` objekt s jiným a vrátí `false` případě, že jsou totožné; v opačném případě vrátí `true`.|
|[operátor =](#operator_eq)|Zkopíruje obsah zadaného `accelerator` do tohoto objektu.|
|[operator==](#operator_eq_eq)|Porovná tento `accelerator` objekt s jiným a vrátí `true` případě, že jsou totožné; v opačném případě vrátí `false`.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[cpu_accelerator](#cpu_accelerator)|Získá konstantní řetězec CPU `accelerator`.|
|[dedicated_memory –](#dedicated_memory)|Získá velikost vyhrazené paměti pro `accelerator`, v kilobajtech.|
|[default_accelerator](#default_accelerator)|Získá konstantní řetězec pro výchozí `accelerator`.|
|[default_cpu_access_type](#default_cpu_access_type)|Získá nebo nastaví výchozí procesor [access_type](concurrency-namespace-enums-amp.md#access_type)pro pole a implicitní přidělení paměti provedené v tomto `accelerator`.|
|[default_view](#default_view)|Získá výchozí `accelerator_view` objekt, který je přidružený `accelerator`.|
|[Popis](#description)|Získá krátký popis `accelerator` zařízení.|
|[device_path](#device_path)|Získá cestu k zařízení.|
|[direct3d_ref](#direct3d_ref)|Získá konstantní řetězec pro odkaz rozhraní Direct3D `accelerator`.|
|[direct3d_warp](#direct3d_warp)|Získá konstantní řetězec `accelerator` objektu, lze použít pro spuštění kódu jazyka C++ AMP na vícejádrových procesorech pomocí Streaming SIMD Extensions (SSE).|
|[has_display](#has_display)|Získá logickou hodnotu, která určuje, zda `accelerator` je připojen k displeji.|
|[is_debug](#is_debug)|Určuje, zda `accelerator` má povolenu vrstvu DEBUG pro rozsáhlé hlášení chyb.|
|[is_emulated](#is_emulated)|Určuje, zda `accelerator` je emulován.|
|[supports_cpu_shared_memory](#supports_cpu_shared_memory)|Určuje, zda `accelerator` podporuje sdílenou paměť.|
|[supports_double_precision](#supports_double_precision)|Určuje, zda akcelerátor podporuje výpočty s dvojitou přesností.|
|[supports_limited_double_precision](#supports_limited_double_precision)|Určuje, zda má akcelerátor omezenou podporu pro matematiku s dvojitou přesností.|
|[Verze](#version)|Získá verzi `accelerator`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`accelerator`

## <a name="remarks"></a>Poznámky

Akcelerátor je funkce hardwaru, která je optimalizovaná pro paralelní výpočty. Akcelerátorem je často diskrétní GPU, ale může být virtuální hostitelské entity, jako je například zařízení DirectX REF, WARP (zařízení straně CPU, které je akcelerováno pomocí instrukcí SSE) nebo samotné CPU.

Můžete vytvořit `accelerator` objekt výčtu dostupných zařízení, nebo získáním výchozího zařízení, odkazovacího zařízení nebo zařízení WARP.

## <a name="requirements"></a>Požadavky

**Záhlaví:** amprt.h

**Namespace:** souběžnosti

##  <a name="dtor"></a> </a> ~ accelerator

Odstraní `accelerator` objektu.

```
~accelerator();
```

### <a name="return-value"></a>Návratová hodnota

##  <a name="ctor"></a> akcelerátor

Inicializuje novou instanci třídy [accelerator – třída](accelerator-class.md).

```
accelerator();

explicit accelerator(const std::wstring& _Device_path);

accelerator(const accelerator& _Other);
```

### <a name="parameters"></a>Parametry

*_Device_path*<br/>
Cesta fyzického zařízení.

*Ji_né*<br/>
Akcelerátor, který má kopírovat.

##  <a name="cpu_accelerator"></a> cpu_accelerator –

Získá konstantní řetězec pro akcelerátor CPU.

```
static const wchar_t cpu_accelerator[];
```

##  <a name="create_view"></a> create_view –

Vytvoří a vrátí `accelerator_view` objekt na tomto akcelerátoru, pomocí zadané režim zařazování do fronty. Pokud není zadaný režim zařazování do fronty, nové `accelerator_view` používá [queuing_mode::immediate](concurrency-namespace-enums-amp.md#queuing_mode) režim zařazování do fronty.

```
accelerator_view create_view(queuing_mode qmode = queuing_mode_automatic);
```

### <a name="parameters"></a>Parametry

*qmode*<br/>
Režim zařazování do fronty.

### <a name="return-value"></a>Návratová hodnota

Nový `accelerator_view` objektu na tomto akcelerátoru, pomocí zadané režim zařazování do fronty.

##  <a name="dedicated_memory"></a> dedicated_memory –

Získá velikost vyhrazené paměti pro `accelerator`, v kilobajtech.

```
__declspec(property(get= get_dedicated_memory)) size_t dedicated_memory;
```

##  <a name="default_accelerator"></a> default_accelerator –

Získá konstantní řetězec pro výchozí `accelerator`.

```
static const wchar_t default_accelerator[];
```

##  <a name="default_cpu_access_type"></a> default_cpu_access_type

Výchozí procesor [access_type](concurrency-namespace-enums-amp.md#access_type)pro pole a implicitní přidělení paměti provedené v tomto `accelerator`.

```
__declspec(property(get= get_default_cpu_access_type)) access_type default_cpu_access_type;
```

##  <a name="default_view"></a> default_view –

Získá výchozí zobrazení akcelerátoru, který je přidružen `accelerator`.

```
__declspec(property(get= get_default_view)) accelerator_view default_view;
```

##  <a name="description"></a> Popis

Získá krátký popis `accelerator` zařízení.

```
__declspec(property(get= get_description)) std::wstring description;
```

##  <a name="device_path"></a> device_path –

Získá cestu k akcelerátoru. Cesta je jedinečná v systému.

```
__declspec(property(get= get_device_path)) std::wstring device_path;
```

##  <a name="direct3d_ref"></a> direct3d_ref –

Získá konstantní řetězec pro odkaz akcelerátorem Direct3D.

```
static const wchar_t direct3d_ref[];
```

##  <a name="direct3d_warp"></a> direct3d_warp –

Získá konstantní řetězec `accelerator` objektu, lze použít pro spuštění kódu C++ AMP na vícejádrových procesorech pomocí Streaming SIMD Extensions (SSE).

```
static const wchar_t direct3d_warp[];
```

##  <a name="get_all"></a> get_all

Vrátí vektor `accelerator` objekty, které představují všechny dostupné akcelerátory.

```
static inline std::vector<accelerator> get_all();
```

### <a name="return-value"></a>Návratová hodnota

Vektor dostupných akcelerátorů

##  <a name="get_auto_selection_view"></a> get_auto_selection_view

Vrátí automatický výběr accelerator_view, který se při zadat jako cíl výsledků parallel_for_each způsobí cílový objekt accelerator_view pro spouštění jádra parallel_for_each bude automaticky vybrán modulem runtime. Pro jiné účely akcelerátor_view vrácený tato metoda je stejný jako akcelerátor _view výchozího akcelerátoru

```
static accelerator_view __cdecl get_auto_selection_view();
```

### <a name="return-value"></a>Návratová hodnota

Automatický výběr accelerator_view.

##  <a name="get_dedicated_memory"></a> get_dedicated_memory –

Vrátí velikost vyhrazené paměti pro `accelerator`, v kilobajtech.

```
size_t get_dedicated_memory() const;

```

### <a name="return-value"></a>Návratová hodnota

Velikost vyhrazené paměti pro `accelerator`, v kilobajtech.

##  <a name="get_default_cpu_access_type"></a> get_default_cpu_access_type

Získá výchozí access_type procesoru pro vyrovnávací paměti vytvořené na tomto akcelerátoru

```
access_type get_default_cpu_access_type() const;

```

### <a name="return-value"></a>Návratová hodnota

Výchozí access_type procesoru pro vyrovnávací paměti vytvořené na tomto akcelerátoru.

##  <a name="get_default_view"></a> get_default_view –

Vrátí výchozí `accelerator_view` objekt, který je přidružený `accelerator`.

```
accelerator_view get_default_view() const;

```

### <a name="return-value"></a>Návratová hodnota

Výchozí hodnota `accelerator_view` objekt, který je přidružený `accelerator`.

##  <a name="get_description"></a> get_description –

Vrátí krátký popis `accelerator` zařízení.

```
std::wstring get_description() const;

```

### <a name="return-value"></a>Návratová hodnota

Krátký popis `accelerator` zařízení.

##  <a name="get_device_path"></a> get_device_path –

Vrátí cestu k akcelerátoru. Cesta je jedinečná v systému.

```
std::wstring get_device_path() const;

```

### <a name="return-value"></a>Návratová hodnota

Cesta instance systémová zařízení jedinečné.

##  <a name="get_has_display"></a> get_has_display –

Vrátí logickou hodnotu, která určuje, zda `accelerator` zvládne výstup na monitor.

```
bool get_has_display() const;

```

### <a name="return-value"></a>Návratová hodnota

`true` Pokud `accelerator` zvládne výstup na monitor; v opačném případě `false`.

##  <a name="get_is_debug"></a> get_is_debug –

Určuje, zda `accelerator` má povolenu vrstvu DEBUG pro rozsáhlé hlášení chyb.

```
bool get_is_debug() const;

```

### <a name="return-value"></a>Návratová hodnota

`true` Pokud `accelerator` má povolenu vrstvu DEBUG pro rozsáhlé hlášení chyb. V opačném případě `false`.

##  <a name="get_is_emulated"></a> get_is_emulated –

Určuje, zda `accelerator` je emulován.

```
bool get_is_emulated() const;

```

### <a name="return-value"></a>Návratová hodnota

`true` Pokud `accelerator` je emulován. V opačném případě `false`.

##  <a name="get_supports_cpu_shared_memory"></a> get_supports_cpu_shared_memory

Vrátí logickou hodnotu označující, zda akcelerátor podporuje paměť dostupnou akcelerátorem i Procesorem.

```
bool get_supports_cpu_shared_memory() const;

```

### <a name="return-value"></a>Návratová hodnota

`true` Pokud akcelerátor podporuje sdílenou paměť procesoru v opačném případě `false`.

##  <a name="get_supports_double_precision"></a> get_supports_double_precision

Vrátí logickou hodnotu, která určuje, zda akcelerátor podporuje výpočty s dvojitou přesností, včetně začleněny vynásobit sčítání (FMA), dělení, obrácené hodnoty a přetypování mezi `int` a `double`.

```
bool get_supports_double_precision() const;

```

### <a name="return-value"></a>Návratová hodnota

`true` Pokud akcelerátor podporuje výpočty s dvojitou přesností v opačném případě `false`.

##  <a name="get_supports_limited_double_precision"></a> get_supports_limited_double_precision

Vrátí logickou hodnotu, která určuje, zda má akcelerátor omezenou podporu pro výpočty s dvojitou přesností. Pokud akcelerátor podporuje pouze omezená, pak začleněny vícenásobně sčítání (FMA), dělení, obrácené hodnoty a přetypování mezi `int` a `double` nejsou podporovány.

```
bool get_supports_limited_double_precision() const;

```

### <a name="return-value"></a>Návratová hodnota

`true` Pokud má akcelerátor omezenou podporu pro výpočty s dvojitou přesností v opačném případě `false`.

##  <a name="get_version"></a> get_version –

Vrátí verzi `accelerator`.

```
unsigned int get_version() const;

```

### <a name="return-value"></a>Návratová hodnota

Verze `accelerator`.

##  <a name="has_display"></a> has_display –

Získá logickou hodnotu, která určuje, zda `accelerator` zvládne výstup na monitor.

```
__declspec(property(get= get_has_display)) bool has_display;
```

##  <a name="is_debug"></a> is_debug –

Získá logickou hodnotu, která určuje, zda `accelerator` má povolenu vrstvu DEBUG pro rozsáhlé hlášení chyb.

```
__declspec(property(get= get_is_debug)) bool is_debug;
```

##  <a name="is_emulated"></a> is_emulated –

Získá logickou hodnotu, která určuje, zda `accelerator` je emulován.

```
__declspec(property(get= get_is_emulated)) bool is_emulated;
```

##  <a name="operator_neq"></a> Operator! =

Porovná tento `accelerator` objekt s jiným a vrátí `false` případě, že jsou totožné; v opačném případě vrátí `true`.

```
bool operator!= (const accelerator& _Other) const;

```

### <a name="parameters"></a>Parametry

*Ji_né*<br/>
`accelerator` Objekt k porovnání s touto položkou.

### <a name="return-value"></a>Návratová hodnota

`false` Pokud dvě `accelerator` jsou objekty stejné; jinak `true`.

##  <a name="operator_eq"></a> operátor =

Zkopíruje obsah zadaného `accelerator` do tohoto objektu.

```
accelerator& operator= (const accelerator& _Other);
```

### <a name="parameters"></a>Parametry

*Ji_né*<br/>
`accelerator` Objektu, který chcete kopírovat.

### <a name="return-value"></a>Návratová hodnota

Odkaz na tento `accelerator` objektu.

##  <a name="operator_eq_eq"></a> Operator ==

Porovná tento `accelerator` objekt s jiným a vrátí `true` případě, že jsou totožné; v opačném případě vrátí `false`.

```
bool operator== (const accelerator& _Other) const;

```

### <a name="parameters"></a>Parametry

*Ji_né*<br/>
`accelerator` Objekt k porovnání s touto položkou.

### <a name="return-value"></a>Návratová hodnota

`true` Pokud druhá `accelerator` objekt je stejné jako to `accelerator` objektu; v opačném případě `false`.

##  <a name="set_default"></a> set_default

Nastaví výchozí akcelerátor pro jakoukoli operaci, která implicitně používá výchozí akcelerátor. Tato metoda bude úspěšná pouze pokud ještě nebyl použit vybrané výchozí akcelerátor modulu runtime v operaci, která implicitně používá výchozí akcelerátor

```
static inline bool set_default(std::wstring _Path);
```

### <a name="parameters"></a>Parametry

*Cesta z_pětného*<br/>
Cesta k akcelerátoru.

### <a name="return-value"></a>Návratová hodnota

`true` Pokud je volání úspěšné při nastavování výchozího akcelerátoru. V opačném případě `false`.

##  <a name="set_default_cpu_access_type"></a> set_default_cpu_access_type

Nastavte výchozí access_type procesoru pro pole vytvořené na tomto akcelerátoru nebo implicitní přidělení paměti jako část hodnoty array_views přístupnou přístup na tento akcelerátor. Tato metoda bude úspěšná pouze pokud přepsat předchozí volání této metody již nebyla default_cpu_access_type pro akcelerátor a default_cpu_access_type runtime, vybrané pro tento akcelerátor nebyla použita ještě pro přidělení matici nebo pro zálohování array_view přístup na tento akcelerátor implicitní paměť přidělení.

```
bool set_default_cpu_access_type(access_type _Default_cpu_access_type);
```

### <a name="parameters"></a>Parametry

*_Default_cpu_access_type*<br/>
Výchozí access_type procesoru pro přidělení paměti pro array/array_view na tomto akcelerátoru.

### <a name="return-value"></a>Návratová hodnota

Logická hodnota označující, pokud byl úspěšně nastaven výchozí objekt access_type pro akcelerátor.

##  <a name="supports_cpu_shared_memory"></a> supports_cpu_shared_memory

Získá logickou hodnotu označující, zda `accelerator` podporuje sdílenou paměť.

```
__declspec(property(get= get_supports_cpu_shared_memory)) bool supports_cpu_shared_memory;
```

##  <a name="supports_double_precision"></a> supports_double_precision

Získá logickou hodnotu, která určuje, zda akcelerátor podporuje výpočty s dvojitou přesností.

```
__declspec(property(get= get_supports_double_precision)) bool supports_double_precision;
```

##  <a name="supports_limited_double_precision"></a> supports_limited_double_precision

Získá logickou hodnotu, která určuje, zda má akcelerátor omezenou podporu pro výpočty s dvojitou přesností. Pokud akcelerátor podporuje pouze omezená, pak začleněny vícenásobně sčítání (FMA), dělení, obrácené hodnoty a přetypování mezi `int` a `double` nejsou podporovány.

```
__declspec(property(get= get_supports_limited_double_precision)) bool supports_limited_double_precision;
```

##  <a name="version"></a> Verze

Získá verzi `accelerator`.

```
__declspec(property(get= get_version)) unsigned int version;
```

##  <a name="dtor"></a> </a> ~ accelerator_view

Odstraní [accelerator_view](accelerator-view-class.md) objektu.

```
~accelerator_view();
```

### <a name="return-value"></a>Návratová hodnota

##  <a name="accelerator"></a> akcelerátor

Získá `accelerator` objekt pro [accelerator_view](accelerator-view-class.md) objektu.

```
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;
```

##  <a name="ctor"></a> accelerator_view

Inicializuje novou instanci třídy [accelerator_view](accelerator-view-class.md) zkopírováním existující `accelerator_view` objektu.

```
accelerator_view(const accelerator_view& _Other);
```

### <a name="parameters"></a>Parametry

*Ji_né*<br/>
`accelerator_view` Objektu, který chcete zkopírovat.

##  <a name="create_marker"></a> create_marker

Vrátí objekt future ke sledování dokončení všech příkazů dosud zaslaných tomuto `accelerator_view` objektu.

```
concurrency::completion_future create_marker();
```

### <a name="return-value"></a>Návratová hodnota

Objekt future ke sledování dokončení všech příkazů dosud zaslaných tomuto `accelerator_view` objektu.

##  <a name="flush"></a> Vyprázdnění

Odešle všechny příkazy čekající ve frontě [accelerator_view](accelerator-view-class.md) objekt akcelerátoru ke spuštění.

```
void flush();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí `void`.

##  <a name="get_accelerator"></a> get_accelerator –

Vrátí `accelerator` objekt pro [accelerator_view](accelerator-view-class.md) objektu.

```
accelerator get_accelerator() const;

```

### <a name="return-value"></a>Návratová hodnota

`accelerator` Objekt pro `accelerator_view` objektu.

##  <a name="get_is_auto_selection"></a> get_is_auto_selection

Vrátí logickou hodnotu, která určuje, zda modul runtime automaticky vybere odpovídající akcelerátor Pokud je předán accelerator_view [parallel_for_each](../../../parallel/concrt/reference/concurrency-namespace-functions.md#parallel_for_each).

```
bool get_is_auto_selection() const;

```

### <a name="return-value"></a>Návratová hodnota

`true` Pokud modul runtime automaticky vybere odpovídající akcelerátor; v opačném případě `false`.

##  <a name="get_is_debug"></a> get_is_debug –

Vrátí logickou hodnotu, která určuje, zda [accelerator_view](accelerator-view-class.md) objekt má povolenu vrstvu DEBUG pro rozsáhlé hlášení chyb.

```
bool get_is_debug() const;

```

### <a name="return-value"></a>Návratová hodnota

Logická hodnota, která určuje, zda `accelerator_view` objekt má povolenu vrstvu DEBUG pro rozsáhlé hlášení chyb.

##  <a name="get_queuing_mode"></a> get_queuing_mode –

Vrátí režim zařazování do fronty pro [accelerator_view](accelerator-view-class.md) objektu.

```
queuing_mode get_queuing_mode() const;

```

### <a name="return-value"></a>Návratová hodnota

Režim zařazování do fronty pro `accelerator_view` objektu.

##  <a name="get_version"></a> get_version –

Vrátí verzi [accelerator_view](accelerator-view-class.md).

```
unsigned int get_version() const;

```

### <a name="return-value"></a>Návratová hodnota

Verze `accelerator_view`.

##  <a name="is_auto_selection"></a> is_auto_selection

Získá logickou hodnotu, která určuje, zda modul runtime automaticky vybere odpovídající akcelerátor Pokud je předán accelerator_view [parallel_for_each](../../../parallel/concrt/reference/concurrency-namespace-functions.md#parallel_for_each).

```
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;
```

##  <a name="is_debug"></a> is_debug –

Získá logickou hodnotu, která určuje, zda [accelerator_view](accelerator-view-class.md) objekt má povolenu vrstvu DEBUG pro rozsáhlé hlášení chyb.

```
__declspec(property(get= get_is_debug)) bool is_debug;
```

##  <a name="operator_neq"></a> Operator! =

Porovná tento [accelerator_view](accelerator-view-class.md) objekt s jiným a vrátí `false` případě, že jsou totožné; v opačném případě vrátí `true`.

```
bool operator!= (const accelerator_view& _Other) const;

```

### <a name="parameters"></a>Parametry

*Ji_né*<br/>
`accelerator_view` Objekt k porovnání s touto položkou.

### <a name="return-value"></a>Návratová hodnota

`false` Pokud jsou oba objekty stejné. v opačném případě `true`.

##  <a name="operator_eq"></a> operátor =

Zkopíruje obsah zadaného [accelerator_view](accelerator-view-class.md) do tohoto objektu.

```
accelerator_view& operator= (const accelerator_view& _Other);
```

### <a name="parameters"></a>Parametry

*Ji_né*<br/>
`accelerator_view` Objektu, který chcete kopírovat.

### <a name="return-value"></a>Návratová hodnota

Odkaz na upravené `accelerator_view` objektu.

##  <a name="operator_eq_eq"></a> Operator ==

Porovná tento [accelerator_view](accelerator-view-class.md) objekt s jiným a vrátí `true` případě, že jsou totožné; v opačném případě vrátí `false`.

```
bool operator== (const accelerator_view& _Other) const;

```

### <a name="parameters"></a>Parametry

*Ji_né*<br/>
`accelerator_view` Objekt k porovnání s touto položkou.

### <a name="return-value"></a>Návratová hodnota

`true` Pokud jsou oba objekty stejné. v opačném případě `false`.

##  <a name="queuing_mode"></a> queuing_mode –

Načte režim zařazování do fronty pro [accelerator_view](accelerator-view-class.md) objektu.

```
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;
```

##  <a name="version"></a> Verze

Získá verzi [accelerator_view](accelerator-view-class.md).

```
__declspec(property(get= get_version)) unsigned int version;
```

##  <a name="wait"></a> Počkej

Čeká na všech příkazů zaslaných [accelerator_view](accelerator-view-class.md) objektu na dokončení.

```
void wait();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí `void`.

## <a name="see-also"></a>Viz také

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
