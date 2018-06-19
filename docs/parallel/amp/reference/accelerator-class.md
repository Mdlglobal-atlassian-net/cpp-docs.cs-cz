---
title: Accelerator – třída | Microsoft Docs
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
ms.openlocfilehash: b40177af3796a17d32e78e628c41ea694f69ed9f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33694750"
---
# <a name="accelerator-class"></a>accelerator – třída
Je akcelerátor schopnost hardwaru, která je optimalizovaná pro data paralelní výpočty. Akcelerátor může být zařízení připojené ke sběrnici PCIe (například grafického procesoru), nebo může být rozšířené instrukce nastavit na hlavní procesoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class accelerator;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Accelerator – konstruktor](#ctor)|Inicializuje novou instanci třídy `accelerator` třídy.|  
|[~ accelerator – destruktor](#ctor)|Zničí `accelerator` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[create_view](#create_view)|Vytvoří a vrátí `accelerator_view` objektu na tento akcelerátoru.|  
|[get_all](#get_all)|Vrátí vektor `accelerator` objekty, které představují všechny dostupné akcelerátorů.|  
|[get_auto_selection_view](#get_auto_selection_view)|Vrátí automatický výběr `accelerator_view`.|  
|[get_dedicated_memory –](#get_dedicated_memory)|Vrátí vyhrazené paměti pro `accelerator`, v kilobajtech.|  
|[get_default_cpu_access_type](#get_default_cpu_access_type)|Vrátí výchozí [access_type](concurrency-namespace-enums-amp.md#access_type) pro vyrovnávací paměti na této akcelerátoru vytvořit.|  
|[get_default_view](#get_default_view)|Vrátí výchozí `accelerator_view` objekt, který je přidružen `accelerator`.|  
|[get_description –](#get_description)|Vrátí krátký popis `accelerator` zařízení.|  
|[get_device_path](#get_device_path)|Vrátí cestu zařízení.|  
|[get_has_display](#get_has_display)|Určuje, zda `accelerator` je připojen k zobrazení.|  
|[get_is_debug](#get_is_debug)|Určuje, zda `accelerator` má vrstvě ladění pro rozsáhlé zasílání zpráv o chybách povoleno.|  
|[get_is_emulated](#get_is_emulated)|Určuje, zda `accelerator` je emulovaných síťových zařízení.|  
|[get_supports_cpu_shared_memory](#get_supports_cpu_shared_memory)|Určuje, zda `accelerator` podporuje sdílené paměti|  
|[get_supports_double_precision](#get_supports_double_precision)|Určuje, zda `accelerator` je připojen k zobrazení.|  
|[get_supports_limited_double_precision](#get_supports_limited_double_precision)|Určuje, zda `accelerator` má omezenou podporu pro matematické dvojitou přesností.|  
|[get_version –](#get_version)|Vrátí verzi `accelerator`.|  
|[set_default](#set_default)|Vrátí cestu akcelerátoru výchozí.|  
|[set_default_cpu_access_type](#set_default_cpu_access_type)|Nastaví výchozí procesoru [access_type](concurrency-namespace-enums-amp.md#access_type)pro pole a přidělení paměti implicitní provedené v tomto `accelerator`.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[operator!=](#operator_neq)|Porovná tato `accelerator` objekt s jinou a vrátí `false` případě, že jsou totožné; jinak vrátí `true`.|  
|[operátor =](#operator_eq)|Zkopíruje obsah zadaného `accelerator` k tomuto objektu.|  
|[operator==](#operator_eq_eq)|Porovná tato `accelerator` objekt s jinou a vrátí `true` případě, že jsou totožné; jinak vrátí `false`.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[cpu_accelerator](#cpu_accelerator)|Získá řetězec konstantní pro procesoru `accelerator`.|  
|[dedicated_memory –](#dedicated_memory)|Získá vyhrazené paměti pro `accelerator`, v kilobajtech.|  
|[default_accelerator](#default_accelerator)|Získá řetězec konstantní pro výchozí `accelerator`.|  
|[default_cpu_access_type](#default_cpu_access_type)|Získá nebo nastaví výchozí procesoru [access_type](concurrency-namespace-enums-amp.md#access_type)pro pole a přidělení paměti implicitní provedené v tomto `accelerator`.|  
|[default_view](#default_view)|Získá výchozí `accelerator_view` objekt, který je přidružen `accelerator`.|  
|[Popis](#description)|Získá krátký popis `accelerator` zařízení.|  
|[device_path](#device_path)|Získá cestu zařízení.|  
|[direct3d_ref](#direct3d_ref)|Získá konstantní řetězec pro odkaz Direct3D – `accelerator`.|  
|[direct3d_warp](#direct3d_warp)|Získá řetězec konstantní pro `accelerator` objektů, které můžete pro spouštění kódu C++ AMP v vícejádrovými procesory, které používají Streaming SIMD Extensions (SSE).|  
|[has_display](#has_display)|Získá logickou hodnotu, která určuje, zda `accelerator` je připojen k zobrazení.|  
|[is_debug](#is_debug)|Určuje, zda `accelerator` má vrstvě ladění pro rozsáhlé zasílání zpráv o chybách povoleno.|  
|[is_emulated](#is_emulated)|Určuje, zda `accelerator` je emulovaných síťových zařízení.|  
|[supports_cpu_shared_memory](#supports_cpu_shared_memory)|Určuje, zda `accelerator` podporuje sdílené paměti.|  
|[supports_double_precision](#supports_double_precision)|Určuje, zda akcelerátor podporuje matematické dvojitou přesností.|  
|[supports_limited_double_precision](#supports_limited_double_precision)|Určuje, zda akcelerátor má omezenou podporu pro matematické dvojitou přesností.|  
|[Verze](#version)|Získá verzi `accelerator`.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `accelerator`  
  
## <a name="remarks"></a>Poznámky  
 Je akcelerátor schopnost hardwaru, která je optimalizovaná pro data paralelní výpočty. Často je akcelerátor diskrétní grafického procesoru, ale může být také virtuální hostitelské entity, například zařízení DirectX REF, OSNOVĚ (procesoru na straně zařízení, které je akcelerován prostřednictvím SSE pokyny) nebo procesor, sám sebe.  
  
 Můžete vytvořit `accelerator` objektu vytváření výčtu zařízení k dispozici, nebo získání výchozího zařízení, odkaz na zařízení nebo zařízení OSNOVĚ.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** amprt.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="dtor"></a> </a> ~ akcelerátoru 

 Zničí `accelerator` objektu.  
  
```  
~accelerator();
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
##  <a name="ctor"></a> akcelerátoru 

 Inicializuje novou instanci třídy [accelerator – třída](accelerator-class.md).  
  
```  
accelerator();

 
explicit accelerator(const std::wstring& _Device_path);

 
accelerator(const accelerator& _Other);
```  
  
### <a name="parameters"></a>Parametry  
 `_Device_path`  
 Cesta fyzického zařízení.  
  
 `_Other`  
 Akcelerátor pro kopírování.  
  
##  <a name="cpu_accelerator"></a> cpu_accelerator – 

 Získá řetězec konstantní pro akcelerátoru procesoru.  
  
```  
static const wchar_t cpu_accelerator[];  
```  
  
##  <a name="create_view"></a> create_view – 

 Vytvoří a vrátí `accelerator_view` objektu na tento akcelerátoru pomocí zadané služby Řízení front režimu. Pokud není zadán režim řazení do fronty, nové `accelerator_view` používá [queuing_mode::immediate](concurrency-namespace-enums-amp.md#queuing_mode) služby Řízení front režimu.  
  
```  
accelerator_view create_view(queuing_mode qmode = queuing_mode_automatic);
```  
  
### <a name="parameters"></a>Parametry  
 `qmode`  
 Režim řazení do fronty.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nový `accelerator_view` objektu na tento akcelerátoru pomocí zadané služby Řízení front režimu.  
  
##  <a name="dedicated_memory"></a> dedicated_memory – 

 Získá vyhrazené paměti pro `accelerator`, v kilobajtech.  
  
```  
__declspec(property(get= get_dedicated_memory)) size_t dedicated_memory;  
```  
  
##  <a name="default_accelerator"></a> default_accelerator – 

 Získá řetězec konstantní pro výchozí `accelerator`.  
  
```  
static const wchar_t default_accelerator[];  
```  
  
##  <a name="default_cpu_access_type"></a> default_cpu_access_type 

 Výchozí hodnota procesoru [access_type](concurrency-namespace-enums-amp.md#access_type)pro pole a přidělení paměti implicitní probíhají tento to `accelerator`.  
  
```  
__declspec(property(get= get_default_cpu_access_type)) access_type default_cpu_access_type;  
```  
  
##  <a name="default_view"></a> default_view – 

 Získá výchozí akcelerátoru zobrazení, který je spojen s `accelerator`.  
  
```  
__declspec(property(get= get_default_view)) accelerator_view default_view;  
```  
  
##  <a name="description"></a> Popis 

 Získá krátký popis `accelerator` zařízení.  
  
```  
__declspec(property(get= get_description)) std::wstring description;  
```  
  
##  <a name="device_path"></a> device_path – 

 Získá cestu akcelerátor. Cesta je jedinečná v systému.  
  
```  
__declspec(property(get= get_device_path)) std::wstring device_path;  
```  
  
##  <a name="direct3d_ref"></a> direct3d_ref – 

 Získá řetězec konstantní pro akcelerátor Direct3D – referenční dokumentace.  
  
```  
static const wchar_t direct3d_ref[];  
```  
  
##  <a name="direct3d_warp"></a> direct3d_warp – 

 Získá řetězec konstantní pro `accelerator` objektů, které můžete pro spouštění vašeho kódu C++ AMP v vícejádrovými procesory pomocí Streaming SIMD Extensions (SSE).  
  
```  
static const wchar_t direct3d_warp[];  
```  
  
##  <a name="get_all"></a> get_all 

 Vrátí vektor `accelerator` objekty, které představují všechny dostupné akcelerátorů.  
  
```  
static inline std::vector<accelerator> get_all();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vektor dostupné akcelerátorů  
  
##  <a name="get_auto_selection_view"></a> get_auto_selection_view 

 Vrátí accelerator_view výběr automaticky, který v případě zadaný jako cíl výsledky parallel_for_each – v accelerator_view cíl pro provádění jádra parallel_for_each – být automaticky vybrány modulem runtime. Pro jiné účely accelerator_view vrácená touto metodou je stejný jako výchozí accelerator_view výchozí akcelerátoru  
  
```  
static accelerator_view __cdecl get_auto_selection_view();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Accelerator_view – výběr automaticky.  
  
##  <a name="get_dedicated_memory"></a> get_dedicated_memory – 

 Vrátí vyhrazené paměti pro `accelerator`, v kilobajtech.  
  
```  
size_t get_dedicated_memory() const;

 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vyhrazené paměti pro `accelerator`, v kilobajtech.  
  
##  <a name="get_default_cpu_access_type"></a> get_default_cpu_access_type 

 Získá access_type procesoru výchozí pro vyrovnávací paměti vytvořit v této akcelerátoru  
  
```  
access_type get_default_cpu_access_type() const;

 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Access_type výchozí procesoru pro vyrovnávací paměti na této akcelerátoru vytvořit.  
  
##  <a name="get_default_view"></a> get_default_view – 

 Vrátí výchozí `accelerator_view` objekt, který je přidružen `accelerator`.  
  
```  
accelerator_view get_default_view() const;

 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výchozí hodnota `accelerator_view` objekt, který je přidružen `accelerator`.  
  
##  <a name="get_description"></a> get_description – 

 Vrátí krátký popis `accelerator` zařízení.  
  
```  
std::wstring get_description() const;

 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Krátký popis `accelerator` zařízení.  
  
##  <a name="get_device_path"></a> get_device_path – 

 Vrátí cestu akcelerátor. Cesta je jedinečná v systému.  
  
```  
std::wstring get_device_path() const;

 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Cesta instance systémové jedinečný zařízení.  
  
##  <a name="get_has_display"></a> get_has_display – 

 Vrátí logickou hodnotu, která určuje, zda `accelerator` výstup můžete na zobrazení.  
  
```  
bool get_has_display() const;

 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud `accelerator` výstup můžete k zobrazení; jinak `false`.  
  
##  <a name="get_is_debug"></a> get_is_debug – 

 Určuje, zda `accelerator` má vrstvě ladění pro rozsáhlé zasílání zpráv o chybách povoleno.  
  
```  
bool get_is_debug() const;

 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud `accelerator` má vrstvě ladění pro rozsáhlé zasílání zpráv o chybách povoleno. V opačném `false`.  
  
##  <a name="get_is_emulated"></a> get_is_emulated – 

 Určuje, zda `accelerator` je emulovaných síťových zařízení.  
  
```  
bool get_is_emulated() const;

 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud `accelerator` je emulovaných síťových zařízení. V opačném `false`.  
  
##  <a name="get_supports_cpu_shared_memory"></a> get_supports_cpu_shared_memory 

 Vrátí logickou hodnotu udávající, zda akcelerátor podporuje paměti dostupné jak akcelerátor a procesoru.  
  
```  
bool get_supports_cpu_shared_memory() const;

 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud je akcelerátor podporuje procesoru sdílené paměti; v opačném `false`.  
  
##  <a name="get_supports_double_precision"></a> get_supports_double_precision 

 Vrátí logickou hodnotu, která určuje, zda akcelerátor podporuje Dvojitá přesnost matematické, včetně začleněny násobení přidat FMA (–), dělení, vzájemné a přetypování mezi `int` a `double`.  
  
```  
bool get_supports_double_precision() const;

 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud je akcelerátor podporuje Dvojitá přesnost matematické; v opačném `false`.  
  
##  <a name="get_supports_limited_double_precision"></a> get_supports_limited_double_precision 

 Vrátí logickou hodnotu, která určuje, zda má akcelerátor omezenou podporu pro Dvojitá přesnost matematické. Pokud má jenom omezenou podporu, pak začleněny násobkem přidat FMA (–), akcelerátor dělení, vzájemné a přetypování mezi `int` a `double` nejsou podporovány.  
  
```  
bool get_supports_limited_double_precision() const;

 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud akcelerátor má omezenou podporu pro Dvojitá přesnost matematické; v opačném `false`.  
  
##  <a name="get_version"></a> get_version – 

 Vrátí verzi `accelerator`.  
  
```  
unsigned int get_version() const;

 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Verze `accelerator`.  
  
##  <a name="has_display"></a> has_display – 

 Získá logickou hodnotu, která určuje, zda `accelerator` výstup můžete na zobrazení.  
  
```  
__declspec(property(get= get_has_display)) bool has_display;  
```  
  
##  <a name="is_debug"></a> is_debug – 

 Získá logickou hodnotu, která určuje, zda `accelerator` má vrstvě ladění pro rozsáhlé zasílání zpráv o chybách povoleno.  
  
```  
__declspec(property(get= get_is_debug)) bool is_debug;  
```  
  
##  <a name="is_emulated"></a> is_emulated – 

 Získá logickou hodnotu, která určuje, zda `accelerator` je emulovaných síťových zařízení.  
  
```  
__declspec(property(get= get_is_emulated)) bool is_emulated;  
```  
  
##  <a name="operator_neq"></a> Operator! = 

 Porovná tato `accelerator` objekt s jinou a vrátí `false` případě, že jsou totožné; jinak vrátí `true`.  
  
```  
bool operator!= (const accelerator& _Other) const;

 
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `accelerator` Objekt k porovnání s touto.  
  
### <a name="return-value"></a>Návratová hodnota  
 `false` Pokud dva `accelerator` objekty jsou stejné, jinak hodnota `true`.  
  
##  <a name="operator_eq"></a> operátor = 

 Zkopíruje obsah zadaného `accelerator` k tomuto objektu.  
  
```  
accelerator& operator= (const accelerator& _Other);
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `accelerator` Objekt, který chcete zkopírovat z.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na toto `accelerator` objektu.  
  
##  <a name="operator_eq_eq"></a> Operator == 

 Porovná tato `accelerator` objekt s jinou a vrátí `true` případě, že jsou totožné; jinak vrátí `false`.  
  
```  
bool operator== (const accelerator& _Other) const;

 
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `accelerator` Objekt k porovnání s touto.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud dalších `accelerator` objekt je stejné jako to `accelerator` objektu; jinak `false`.  
  
##  <a name="set_default"></a> set_default 

 Nastaví výchozí akcelerátoru má být použit pro všechny operace implicitně používá výchozí akcelerátoru. Tato metoda pouze úspěšná, pokud ještě nebyl použit akcelerátoru vybrané výchozí runtime v operaci, která se implicitně používá výchozí akcelerátoru  
  
```  
static inline bool set_default(std::wstring _Path);
```  
  
### <a name="parameters"></a>Parametry  
 `_Path`  
 Cesta k akcelerátor.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud volání úspěšné v akcelerátoru výchozí nastavení. V opačném `false`.  
  
##  <a name="set_default_cpu_access_type"></a> set_default_cpu_access_type 

 Nastavte access_type procesoru výchozí pro pole vytvořena na tento akcelerátoru nebo pro přidělení paměti implicitní jako součást array_views získat přístup na tomto tento akcelerátoru. Tato metoda bude úspěšná pouze pokud default_cpu_access_type pro akcelerátor nebyl dosud elementem předchozím voláním této metody a default_cpu_access_type vybraný modul runtime pro tento akcelerátoru nebyl dosud použit pro přidělování pole nebo pro přidělení paměti implicitní zálohování array_view získat přístup na tento akcelerátoru.  
  
```  
bool set_default_cpu_access_type(access_type _Default_cpu_access_type);
```  
  
### <a name="parameters"></a>Parametry  
 `_Default_cpu_access_type`  
 Access_type procesoru výchozí má být použit pro pole/array_view přidělení paměti na této akcelerátoru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Logickou hodnotu udávající, pokud access_type procesoru výchozí pro akcelerátor byl úspěšně nastaven.  
  
##  <a name="supports_cpu_shared_memory"></a> supports_cpu_shared_memory 

 Získá logickou hodnotu, která určuje zda `accelerator` podporuje sdílené paměti.  
  
```  
__declspec(property(get= get_supports_cpu_shared_memory)) bool supports_cpu_shared_memory;  
```  
  
##  <a name="supports_double_precision"></a> supports_double_precision 

 Získá logickou hodnotu, která určuje, zda akcelerátor podporuje matematické dvojitou přesností.  
  
```  
__declspec(property(get= get_supports_double_precision)) bool supports_double_precision;  
```  
  
##  <a name="supports_limited_double_precision"></a> supports_limited_double_precision 

 Získá logickou hodnotu, která určuje, zda má akcelerátor omezenou podporu pro Dvojitá přesnost matematické. Pokud má jenom omezenou podporu, pak začleněny násobkem přidat FMA (–), akcelerátor dělení, vzájemné a přetypování mezi `int` a `double` nejsou podporovány.  
  
```  
__declspec(property(get= get_supports_limited_double_precision)) bool supports_limited_double_precision;  
```  
  
##  <a name="version"></a> Verze 

 Získá verzi `accelerator`.  
  
```  
__declspec(property(get= get_version)) unsigned int version;  
```  
  
##  <a name="dtor"></a> </a> ~ accelerator_view 

 Zničí [accelerator_view](accelerator-view-class.md) objektu.  
  
```  
~accelerator_view();
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
##  <a name="accelerator"></a> akcelerátoru 

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
 `_Other`  
 `accelerator_view` Objekt, který chcete kopírovat.  
  
##  <a name="create_marker"></a> create_marker 

 Vrátí budoucí sledování dokončení všech příkazů odeslání, pokud k tomuto `accelerator_view` objektu.  
  
```  
concurrency::completion_future create_marker();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Budoucí sledování dokončení všech příkazů odeslání, pokud k tomuto `accelerator_view` objektu.  
  
##  <a name="flush"></a> Vyprázdnění 

 Odešle všechny čekající příkazy zařazených do fronty [accelerator_view](accelerator-view-class.md) objekt, který chcete akcelerátor pro spuštění.  
  
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

 Vrátí logickou hodnotu, která určuje, zda modul runtime automaticky vybere odpovídající akcelerátoru když je předána accelerator_view [parallel_for_each –](../../../parallel/concrt/reference/concurrency-namespace-functions.md#parallel_for_each).  
  
```  
bool get_is_auto_selection() const;

 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud modul runtime automaticky vybere odpovídající akcelerátoru; v opačném `false`.  
  
##  <a name="get_is_debug"></a> get_is_debug – 

 Vrátí logickou hodnotu, která určuje, zda [accelerator_view](accelerator-view-class.md) objekt má vrstvě ladění pro rozsáhlé zasílání zpráv o chybách povoleno.  
  
```  
bool get_is_debug() const;

 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Logická hodnota, která určuje, zda `accelerator_view` objekt má vrstvě ladění pro rozsáhlé zasílání zpráv o chybách povoleno.  
  
##  <a name="get_queuing_mode"></a> get_queuing_mode – 

 Vrátí hodnotu režimu front zpráv pro [accelerator_view](accelerator-view-class.md) objektu.  
  
```  
queuing_mode get_queuing_mode() const;

 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Režim řazení do fronty pro `accelerator_view` objektu.  
  
##  <a name="get_version"></a> get_version – 

 Vrátí verzi [accelerator_view](accelerator-view-class.md).  
  
```  
unsigned int get_version() const;

 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Verze `accelerator_view`.  
  
##  <a name="is_auto_selection"></a> is_auto_selection 

 Získá logickou hodnotu, která určuje, zda modul runtime automaticky vybere odpovídající akcelerátoru když je předána accelerator_view [parallel_for_each –](../../../parallel/concrt/reference/concurrency-namespace-functions.md#parallel_for_each).  
  
```  
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;  
```  
  
##  <a name="is_debug"></a> is_debug – 

 Získá logickou hodnotu, která určuje, zda [accelerator_view](accelerator-view-class.md) objekt má vrstvě ladění pro rozsáhlé zasílání zpráv o chybách povoleno.  
  
```  
__declspec(property(get= get_is_debug)) bool is_debug;  
```  
  
##  <a name="operator_neq"></a> Operator! = 

 Porovná tato [accelerator_view](accelerator-view-class.md) objekt s jinou a vrátí `false` případě, že jsou totožné; jinak vrátí `true`.  
  
```  
bool operator!= (const accelerator_view& _Other) const;

 
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `accelerator_view` Objekt k porovnání s touto.  
  
### <a name="return-value"></a>Návratová hodnota  
 `false` Pokud dva objekty jsou stejné. v opačném `true`.  
  
##  <a name="operator_eq"></a> operátor = 

 Zkopíruje obsah zadaného [accelerator_view](accelerator-view-class.md) objekt s touto.  
  
```  
accelerator_view& operator= (const accelerator_view& _Other);
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `accelerator_view` Objekt, který chcete zkopírovat z.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na upravenou `accelerator_view` objektu.  
  
##  <a name="operator_eq_eq"></a> Operator == 

 Porovná tato [accelerator_view](accelerator-view-class.md) objekt s jinou a vrátí `true` případě, že jsou totožné; jinak vrátí `false`.  
  
```  
bool operator== (const accelerator_view& _Other) const;

 
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `accelerator_view` Objekt k porovnání s touto.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud dva objekty jsou stejné. v opačném `false`.  
  
##  <a name="queuing_mode"></a> queuing_mode 

 Získá režim front zpráv pro [accelerator_view](accelerator-view-class.md) objektu.  
  
```  
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;  
```  
  
##  <a name="version"></a> Verze 

 Získá verzi [accelerator_view](accelerator-view-class.md).  
  
```  
__declspec(property(get= get_version)) unsigned int version;  
```  
  
##  <a name="wait"></a> Počkej 

 Všechny příkazy odeslané na čeká [accelerator_view](accelerator-view-class.md) objekt, který chcete dokončit.  
  
```  
void wait();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `void`.  
  
## <a name="see-also"></a>Viz také  
 [Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
