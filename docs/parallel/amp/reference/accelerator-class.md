---
title: accelerator – třída
ms.date: 11/04/2016
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
helpviewer_keywords:
- accelerator class
ms.assetid: 37eed593-cf87-4611-9cdc-e98df6c2377a
ms.openlocfilehash: 72a570ab28696730f835c42748a6ea12b865ca55
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422267"
---
# <a name="accelerator-class"></a>accelerator – třída

Akcelerátor je hardwarová schopnost, která je optimalizovaná pro náročné zpracování dat. Akcelerátor může být zařízení připojené ke sběrnici PCIe (například GPU), nebo se může jednat o rozšířenou sadu instrukcí v hlavním procesoru.

## <a name="syntax"></a>Syntaxe

```cpp
class accelerator;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[akcelerátor – konstruktor](#ctor)|Inicializuje novou instanci třídy `accelerator`.|
|[~ akcelerátorový destruktor](#ctor)|Odstraní objekt `accelerator`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[create_view](#create_view)|Vytvoří a vrátí objekt `accelerator_view` v tomto akcelerátoru.|
|[get_all](#get_all)|Vrátí Vektor objektů `accelerator`, které reprezentují všechny dostupné akcelerátory.|
|[get_auto_selection_view](#get_auto_selection_view)|Vrátí `accelerator_view`automatického výběru.|
|[get_dedicated_memory](#get_dedicated_memory)|Vrátí vyhrazenou paměť pro `accelerator`v kilobajtech.|
|[get_default_cpu_access_type](#get_default_cpu_access_type)|Vrátí výchozí [access_type](concurrency-namespace-enums-amp.md#access_type) pro vyrovnávací paměti vytvořené na tomto akcelerátoru.|
|[get_default_view](#get_default_view)|Vrátí výchozí `accelerator_view` objekt, který je spojen s `accelerator`.|
|[get_description](#get_description)|Vrátí krátký popis zařízení `accelerator`.|
|[get_device_path](#get_device_path)|Vrátí cestu k zařízení.|
|[get_has_display](#get_has_display)|Určuje, zda je `accelerator` připojeno k zobrazení.|
|[get_is_debug](#get_is_debug)|Určuje, zda `accelerator` má povolenou vrstvu ladění pro rozsáhlé hlášení chyb.|
|[get_is_emulated](#get_is_emulated)|Určuje, zda je `accelerator` emulované.|
|[get_supports_cpu_shared_memory](#get_supports_cpu_shared_memory)|Určuje, jestli `accelerator` podporuje sdílenou paměť.|
|[get_supports_double_precision](#get_supports_double_precision)|Určuje, zda je `accelerator` připojeno k zobrazení.|
|[get_supports_limited_double_precision](#get_supports_limited_double_precision)|Určuje, zda má `accelerator` omezená podpora pro matematiku s dvojitou přesností.|
|[get_version](#get_version)|Vrátí verzi `accelerator`.|
|[set_default](#set_default)|Vrátí cestu k výchozímu akcelerátoru.|
|[set_default_cpu_access_type](#set_default_cpu_access_type)|Nastaví výchozí [ACCESS_TYPE](concurrency-namespace-enums-amp.md#access_type)procesoru pro pole a implicitní přidělení paměti provedené v tomto `accelerator`.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operator!=](#operator_neq)|Porovná tento objekt `accelerator` s jiným objektem a vrátí **hodnotu false** , pokud jsou stejné. v opačném případě vrátí **hodnotu true**.|
|[operátor =](#operator_eq)|Zkopíruje obsah zadaného objektu `accelerator` do tohoto objektu.|
|[operator = = – operátor](#operator_eq_eq)|Porovná tento objekt `accelerator` s jiným objektem a vrátí **hodnotu true** , pokud jsou stejné. v opačném případě vrátí **hodnotu false**.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[cpu_accelerator](#cpu_accelerator)|Načte řetězcovou konstantu pro `accelerator`procesoru.|
|[dedicated_memory](#dedicated_memory)|Načte vyhrazenou paměť pro `accelerator`v kilobajtech.|
|[default_accelerator](#default_accelerator)|Načte řetězcovou konstantu pro výchozí `accelerator`.|
|[default_cpu_access_type](#default_cpu_access_type)|Získá nebo nastaví výchozí [ACCESS_TYPE](concurrency-namespace-enums-amp.md#access_type)procesoru pro pole a implicitní přidělení paměti provedené v tomto `accelerator`.|
|[default_view](#default_view)|Získá výchozí objekt `accelerator_view`, který je spojen s `accelerator`.|
|[název](#description)|Získá krátký popis zařízení `accelerator`.|
|[device_path](#device_path)|Získá cestu k zařízení.|
|[direct3d_ref](#direct3d_ref)|Načte řetězcovou konstantu pro referenční `accelerator`Direct3D.|
|[direct3d_warp](#direct3d_warp)|Získává řetězcovou konstantu pro objekt `accelerator`, který můžete použít ke spouštění C++ kódu amp na vícejádrových procesorech, které používají streaming SIMD Extensions (SSE).|
|[has_display](#has_display)|Získá logickou hodnotu, která označuje, zda je `accelerator` připojen k zobrazení.|
|[is_debug](#is_debug)|Určuje, zda `accelerator` má povolenou vrstvu ladění pro rozsáhlé hlášení chyb.|
|[is_emulated](#is_emulated)|Určuje, zda je `accelerator` emulované.|
|[supports_cpu_shared_memory](#supports_cpu_shared_memory)|Určuje, zda `accelerator` podporuje sdílenou paměť.|
|[supports_double_precision](#supports_double_precision)|Označuje, zda akcelerátor podporuje matematiku s dvojitou přesností.|
|[supports_limited_double_precision](#supports_limited_double_precision)|Označuje, zda akcelerátor má omezené podpory pro matematiku s dvojitou přesností.|
|[version](#version)|Získá verzi `accelerator`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`accelerator`

## <a name="remarks"></a>Poznámky

Akcelerátor je hardwarová schopnost, která je optimalizovaná pro náročné zpracování dat. Akcelerátor je často diskrétní grafický procesor, ale může se jednat o virtuální entitu na straně hostitele, jako je například zařízení s ODKAZem na rozhraní DirectX, pokřivení (zařízení na straně procesoru, které je urychleno pomocí instrukcí SSE) nebo samotného procesoru.

Objekt `accelerator` můžete vytvořit vytvořením výčtu dostupných zařízení nebo získáním výchozího zařízení, referenčního zařízení nebo zařízení v OSNOVě.

## <a name="requirements"></a>Požadavky

**Záhlaví:** amprt. h

**Obor názvů:** Concurrency

## <a name="dtor"></a></a> ~ akcelerátor

Odstraní objekt `accelerator`.

```cpp
~accelerator();
```

### <a name="return-value"></a>Návratová hodnota

## <a name="ctor"></a>Accelerator

Inicializuje novou instanci [třídy akcelerátoru](accelerator-class.md).

```cpp
accelerator();

explicit accelerator(const std::wstring& _Device_path);

accelerator(const accelerator& _Other);
```

### <a name="parameters"></a>Parametry

*_Device_path*<br/>
Cesta fyzického zařízení.

*_Other*<br/>
Akcelerátor, který chcete zkopírovat.

## <a name="cpu_accelerator"></a>cpu_accelerator

Načte řetězcovou konstantu pro akcelerátor procesoru.

```cpp
static const wchar_t cpu_accelerator[];
```

## <a name="create_view"></a>create_view

Vytvoří a vrátí objekt `accelerator_view` v tomto akcelerátoru pomocí zadaného režimu služby Řízení front zpráv. Pokud není zadán režim služby Řízení front zpráv, používá nový `accelerator_view` režim služby [queuing_mode:: Immediate](concurrency-namespace-enums-amp.md#queuing_mode) Queuing.

```cpp
accelerator_view create_view(queuing_mode qmode = queuing_mode_automatic);
```

### <a name="parameters"></a>Parametry

*qmode*<br/>
Režim služby Řízení front zpráv.

### <a name="return-value"></a>Návratová hodnota

Nový objekt `accelerator_view` v tomto akcelerátoru pomocí zadaného režimu služby Řízení front zpráv.

## <a name="dedicated_memory"></a>dedicated_memory

Načte vyhrazenou paměť pro `accelerator`v kilobajtech.

```cpp
__declspec(property(get= get_dedicated_memory)) size_t dedicated_memory;
```

## <a name="default_accelerator"></a>default_accelerator

Načte řetězcovou konstantu pro výchozí `accelerator`.

```cpp
static const wchar_t default_accelerator[];
```

## <a name="default_cpu_access_type"></a>default_cpu_access_type

Výchozí [access_type](concurrency-namespace-enums-amp.md#access_type)procesoru pro pole a implicitní přidělení paměti provedené v tomto `accelerator`.

```cpp
__declspec(property(get= get_default_cpu_access_type)) access_type default_cpu_access_type;
```

## <a name="default_view"></a>default_view

Získá výchozí zobrazení akcelerátoru, které je přidruženo k `accelerator`.

```cpp
__declspec(property(get= get_default_view)) accelerator_view default_view;
```

## <a name="description"></a>název

Získá krátký popis zařízení `accelerator`.

```cpp
__declspec(property(get= get_description)) std::wstring description;
```

## <a name="device_path"></a>device_path

Získá cestu akcelerátoru. Cesta je v systému jedinečná.

```cpp
__declspec(property(get= get_device_path)) std::wstring device_path;
```

## <a name="direct3d_ref"></a>direct3d_ref

Načte řetězcovou konstantu pro referenční akcelerátor Direct3D.

```cpp
static const wchar_t direct3d_ref[];
```

## <a name="direct3d_warp"></a>direct3d_warp

Získá řetězcovou konstantu pro objekt `accelerator`, který můžete použít ke spuštění kódu C++ amp na vícejádrových procesorech pomocí streaming SIMD Extensions (SSE).

```cpp
static const wchar_t direct3d_warp[];
```

## <a name="get_all"></a>get_all

Vrátí Vektor objektů `accelerator`, které reprezentují všechny dostupné akcelerátory.

```cpp
static inline std::vector<accelerator> get_all();
```

### <a name="return-value"></a>Návratová hodnota

Vektor dostupných akcelerátorů

## <a name="get_auto_selection_view"></a>get_auto_selection_view

Vrátí accelerator_view automatického výběru, který je v případě, že je zadán jako cílový parallel_for_each výsledků, v cílovém accelerator_view pro spuštění jádra parallel_for_each, které má modul runtime automaticky vybrat. Pro všechny ostatní účely je accelerator_view vrácená touto metodou stejná jako výchozí accelerator_view výchozího akcelerátoru.

```cpp
static accelerator_view __cdecl get_auto_selection_view();
```

### <a name="return-value"></a>Návratová hodnota

Accelerator_view automatického výběru.

## <a name="get_dedicated_memory"></a>get_dedicated_memory

Vrátí vyhrazenou paměť pro `accelerator`v kilobajtech.

```cpp
size_t get_dedicated_memory() const;
```

### <a name="return-value"></a>Návratová hodnota

Vyhrazená paměť pro `accelerator`v kilobajtech.

## <a name="get_default_cpu_access_type"></a>get_default_cpu_access_type

Získá výchozí access_type procesoru pro vyrovnávací paměti vytvořené na tomto akcelerátoru.

```cpp
access_type get_default_cpu_access_type() const;
```

### <a name="return-value"></a>Návratová hodnota

Výchozí access_type procesoru pro vyrovnávací paměti vytvořené na tomto akcelerátoru.

## <a name="get_default_view"></a>get_default_view

Vrátí výchozí `accelerator_view` objekt, který je spojen s `accelerator`.

```cpp
accelerator_view get_default_view() const;
```

### <a name="return-value"></a>Návratová hodnota

Výchozí `accelerator_view` objekt, který je spojen s `accelerator`.

## <a name="get_description"></a>get_description

Vrátí krátký popis zařízení `accelerator`.

```cpp
std::wstring get_description() const;
```

### <a name="return-value"></a>Návratová hodnota

Krátký popis zařízení `accelerator`.

## <a name="get_device_path"></a>get_device_path

Vrátí cestu akcelerátoru. Cesta je v systému jedinečná.

```cpp
std::wstring get_device_path() const;
```

### <a name="return-value"></a>Návratová hodnota

Jedinečná cesta k instanci zařízení v rámci systému

## <a name="get_has_display"></a>get_has_display

Vrací logickou hodnotu, která označuje, zda `accelerator` může výstup zobrazit.

```cpp
bool get_has_display() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud `accelerator` může výstup zobrazit; v opačném případě **false**.

## <a name="get_is_debug"></a>get_is_debug

Určuje, zda `accelerator` má povolenou vrstvu ladění pro rozsáhlé hlášení chyb.

```cpp
bool get_is_debug() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud `accelerator` má povolenou vrstvu ladění pro rozsáhlé hlášení chyb. V opačném případě **false**.

## <a name="get_is_emulated"></a>get_is_emulated

Určuje, zda je `accelerator` emulované.

```cpp
bool get_is_emulated() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je `accelerator` emulované. V opačném případě **false**.

## <a name="get_supports_cpu_shared_memory"></a>get_supports_cpu_shared_memory

Vrátí logickou hodnotu, která označuje, zda akcelerátor podporuje paměť přístupná akcelerátorem i PROCESORem.

```cpp
bool get_supports_cpu_shared_memory() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud akcelerátor podporuje sdílenou paměť procesoru; v opačném případě **false**.

## <a name="get_supports_double_precision"></a>get_supports_double_precision

Vrátí logickou hodnotu, která označuje, zda akcelerátor podporuje matematiku s dvojitou přesností, včetně pojistky (FMA), dělení, vzájemnosti a přetypování mezi **int** a **dvojitou** přesností.

```cpp
bool get_supports_double_precision() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud akcelerátor podporuje matematiku s dvojitou přesností; v opačném případě **false**.

## <a name="get_supports_limited_double_precision"></a>get_supports_limited_double_precision

Vrací logickou hodnotu, která označuje, zda akcelerátor má omezené podpory pro matematiku s dvojitou přesností. Pokud akcelerátor má pouze omezené podpory, pak se nepodporují pojistá vynásobené násobení (FMA), dělení, reciproční a přetypování mezi **int** a **Double** .

```cpp
bool get_supports_limited_double_precision() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud má akcelerátor omezené podpory pro matematiku s dvojitou přesností; v opačném případě **false**.

## <a name="get_version"></a>get_version

Vrátí verzi `accelerator`.

```cpp
unsigned int get_version() const;
```

### <a name="return-value"></a>Návratová hodnota

Verze `accelerator`.

## <a name="has_display"></a>has_display

Získá logickou hodnotu, která označuje, zda `accelerator` může výstup zobrazit.

```cpp
__declspec(property(get= get_has_display)) bool has_display;
```

## <a name="is_debug"></a>is_debug

Získá logickou hodnotu, která označuje, zda `accelerator` má povolenou vrstvu ladění pro rozsáhlé hlášení chyb.

```cpp
__declspec(property(get= get_is_debug)) bool is_debug;
```

## <a name="is_emulated"></a>is_emulated

Získá logickou hodnotu, která označuje, zda je `accelerator` emulovana.

```cpp
__declspec(property(get= get_is_emulated)) bool is_emulated;
```

## <a name="operator_neq"></a>! = – operátor

Porovná tento objekt `accelerator` s jiným objektem a vrátí **hodnotu false** , pokud jsou stejné. v opačném případě vrátí **hodnotu true**.

```cpp
bool operator!= (const accelerator& _Other) const;
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
Objekt `accelerator`, který se má porovnat s tímto.

### <a name="return-value"></a>Návratová hodnota

**false** , pokud jsou dva objekty `accelerator` stejné; v opačném případě **true**.

## <a name="operator_eq"></a>operátor =

Zkopíruje obsah zadaného objektu `accelerator` do tohoto objektu.

```cpp
accelerator& operator= (const accelerator& _Other);
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
Objekt `accelerator`, ze kterého se má kopírovat.

### <a name="return-value"></a>Návratová hodnota

Odkaz na tento objekt `accelerator`.

## <a name="operator_eq_eq"></a>operator = = – operátor

Porovná tento objekt `accelerator` s jiným objektem a vrátí **hodnotu true** , pokud jsou stejné. v opačném případě vrátí **hodnotu false**.

```cpp
bool operator== (const accelerator& _Other) const;
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
Objekt `accelerator`, který se má porovnat s tímto.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je jiný objekt `accelerator` stejný jako tento objekt `accelerator`; v opačném případě **false**.

## <a name="set_default"></a>set_default

Nastaví výchozí akcelerátor, který se má použít pro libovolnou operaci, která implicitně používá výchozí akcelerátor. Tato metoda je úspěšná pouze v případě, že v operaci, která implicitně používá výchozí akcelerátor, již nebyl použit výchozí akcelerátor vybraný pro modul runtime.

```cpp
static inline bool set_default(std::wstring _Path);
```

### <a name="parameters"></a>Parametry

*_Path*<br/>
Cesta k akcelerátoru.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je volání úspěšné při nastavení výchozího akcelerátoru. V opačném případě **false**.

## <a name="set_default_cpu_access_type"></a>set_default_cpu_access_type

Nastavte výchozí access_type procesoru pro pole vytvořená v tomto akcelerátoru nebo pro implicitní přidělení paměti jako součást array_views k tomuto akcelerátoru. Tato metoda je úspěšná pouze v případě, že default_cpu_access_type pro akcelerátor již nebyl potlačen předchozím voláním této metody a modul runtime vybraný default_cpu_access_type pro tento akcelerátor ještě nebyl použit pro přidělení pole nebo pro implicitní přidělení paměti při zálohování array_view k tomuto akcelerátoru.

```cpp
bool set_default_cpu_access_type(access_type _Default_cpu_access_type);
```

### <a name="parameters"></a>Parametry

*_Default_cpu_access_type*<br/>
Výchozí access_type procesoru, který se má použít pro přidělení paměti Array/array_view v tomto akcelerátoru.

### <a name="return-value"></a>Návratová hodnota

Logická hodnota označující, zda byl úspěšně nastaven výchozí access_type procesoru pro akcelerátor.

## <a name="supports_cpu_shared_memory"></a>supports_cpu_shared_memory

Získá logickou hodnotu, která označuje, zda `accelerator` podporuje sdílenou paměť.

```cpp
__declspec(property(get= get_supports_cpu_shared_memory)) bool supports_cpu_shared_memory;
```

## <a name="supports_double_precision"></a>supports_double_precision

Získá logickou hodnotu, která označuje, zda akcelerátor podporuje matematiku s dvojitou přesností.

```cpp
__declspec(property(get= get_supports_double_precision)) bool supports_double_precision;
```

## <a name="supports_limited_double_precision"></a>supports_limited_double_precision

Získá logickou hodnotu, která označuje, zda akcelerátor má omezené podpory pro matematiku s dvojitou přesností. Pokud akcelerátor má jenom omezené podpory, pak se v něm nepodporují pojistá vynásobení doplňku (FMA), dělení, přetypování a přetypování mezi `int` a `double`.

```cpp
__declspec(property(get= get_supports_limited_double_precision)) bool supports_limited_double_precision;
```

## <a name="version"></a>znění

Získá verzi `accelerator`.

```cpp
__declspec(property(get= get_version)) unsigned int version;
```

## <a name="see-also"></a>Viz také

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
