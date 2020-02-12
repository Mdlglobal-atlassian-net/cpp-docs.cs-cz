---
title: Funkce oboru názvů Concurrency::direct3d (AMP)
ms.date: 08/31/2018
f1_keywords:
- amp/Concurrency::direct3d::abs
- amp/Concurrency::direct3d::countbits
- amp/Concurrency::direct3d::create_accelerator_view
- amp/Concurrency::direct3d::d3d_access_lock
- amp/Concurrency::direct3d::d3d_access_unlock
- amp/Concurrency::direct3d::firstbithigh
- amp/Concurrency::direct3d::get_buffer
- amp/Concurrency::direct3d::get_device
- amp/Concurrency::direct3d::imax
- amp/Concurrency::direct3d::is_timeout_disabled
- amp/Concurrency::direct3d::mad
- amp/Concurrency::direct3d::noise
- amp/Concurrency::direct3d::radians
- amp/Concurrency::direct3d::reversebits
- amp/Concurrency::direct3d::saturate
- amp/Concurrency::direct3d::smoothstep
- amp/Concurrency::direct3d::step
- amp/Concurrency::direct3d::umin
ms.assetid: 28943b62-52c9-42dc-baf1-ca7b095c1a19
ms.openlocfilehash: 438d211ac2f15bf781b704a7d0d7484d1542f131
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127043"
---
# <a name="concurrencydirect3d-namespace-functions-amp"></a>Funkce oboru názvů Concurrency::direct3d (AMP)

||||
|-|-|-|
|[ABS](#abs)|[Clamp](#clamp)|[countbits –](#countbits)|
|[create_accelerator_view](#create_accelerator_view)|[d3d_access_lock](#d3d_access_lock)||
|[d3d_access_try_lock](#d3d_access_try_lock)|[d3d_access_unlock](#d3d_access_unlock)|[firstbithigh –](#firstbithigh)|
|[firstbitlow –](#firstbitlow)|[get_buffer](#get_buffer)|[get_device](#get_device)|
|[imax](#imax)|[imin](#imin)|[is_timeout_disabled](#is_timeout_disabled)|
|[Mad –](#mad)|[make_array](#make_array)|[neobsažných](#noise)|
|[rad](#radians)|[rcp](#rcp)|[reversebits –](#reversebits)|
|[saturate –](#saturate)|[sign](#sign)|[smoothstep –](#smoothstep)|
|[Krok](#step)|[společnosti](#umax)|[umin](#umin)|

## <a name="requirements"></a>Požadavky

**Záhlaví:** **obor názvů** amp. h: souběžnost

## <a name="abs"></a>ABS

Vrátí absolutní hodnotu argumentu.

```cpp
inline int abs(int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Celočíselná hodnota

### <a name="return-value"></a>Návratová hodnota

Vrátí absolutní hodnotu argumentu.

## <a name="clamp"></a>Clamp

Vypočítá hodnotu prvního zadaného argumentu připnutého do rozsahu definovaného druhým a třetím zadaným argumentem.

```cpp
inline float clamp(
    float _X,
    float _Min,
    float _Max) restrict(amp);

inline int clamp(
    int _X,
    int _Min,
    int _Max) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota, která se má svorka

*_Min*<br/>
Dolní mez rozsahu svorky.

*_Max*<br/>
Horní mez rozsahu svorky.

### <a name="return-value"></a>Návratová hodnota

Připnuté hodnota `_X`.

## <a name="countbits"></a>countbits –

Spočítá počet sad bitů v _X.

```cpp
inline unsigned int countbits(unsigned int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Celočíselná hodnota bez znaménka

### <a name="return-value"></a>Návratová hodnota

Vrátí počet sad bitů v _X.

## <a name="create_accelerator_view"></a>create_accelerator_view

Vytvoří objekt [accelerator_view](accelerator-view-class.md) z ukazatele na rozhraní zařízení Direct3D.

## <a name="syntax"></a>Syntaxe

```cpp
accelerator_view create_accelerator_view(
    IUnknown * _D3D_device
    queuing_mode _Qmode = queuing_mode_automatic);

accelerator_view create_accelerator_view(
    accelerator& _Accelerator,
    bool _Disable_timeout
    queuing_mode _Qmode = queuing_mode_automatic);
```

### <a name="parameters"></a>Parametry

*_Accelerator*<br/>
Akcelerátor, na kterém má být vytvořen nový accelerator_view.

*_D3D_device*<br/>
Ukazatel na rozhraní zařízení Direct3D.

*_Disable_timeout*<br/>
Logický parametr určující, zda má být pro nově vytvořenou accelerator_view časový limit zakázán. To odpovídá příznaku D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT pro vytváření zařízení Direct3D a používá se k označení, jestli má operační systém umožňovat spuštění úloh, které trvá déle než 2 sekundy, a to bez resetování zařízení na časový limit Windows. mechanismus detekce a obnovení. Použití tohoto příznaku se doporučuje, pokud potřebujete provádět časově náročné úlohy na accelerator_view.

*_Qmode*<br/>
[Queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode) , která se má použít pro nově vytvořenou accelerator_view Tento parametr má výchozí hodnotu `queuing_mode_automatic`.

## <a name="return-value"></a>Návratová hodnota

Objekt `accelerator_view` vytvořený z předaného rozhraní zařízení Direct3D.

## <a name="remarks"></a>Poznámky

Tato funkce vytvoří nový objekt `accelerator_view` z existujícího ukazatele na rozhraní zařízení Direct3D. Pokud je volání funkce úspěšné, je počet odkazů parametru zvýšen pomocí `AddRef` volání rozhraní. Objekt můžete bezpečně uvolnit, pokud už ho nepotřebujete v kódu DirectX. Pokud volání metody neproběhne úspěšně, je vyvolána [runtime_exception](runtime-exception-class.md) .

Objekt `accelerator_view`, který vytvoříte pomocí této funkce, je bezpečný pro přístup z více vláken. Je nutné synchronizovat souběžné použití objektu `accelerator_view`. Nesynchronizované souběžné použití objektu `accelerator_view` a nezpracované ID3D11Device rozhraní způsobí nedefinované chování.

Modul C++ runtime amp poskytuje podrobné informace o chybě v režimu ladění pomocí vrstvy ladění D3D, pokud použijete příznak `D3D11_CREATE_DEVICE_DEBUG`.

## <a name="d3d_access_lock"></a>d3d_access_lock

Získá zámek accelerator_view pro účely bezpečného provádění operací D3D na prostředcích sdílených s accelerator_view. Accelerator_view a všechny C++ prostředky amp přidružené k tomuto accelerator_view vnitřně přijímají tento zámek při provádění operací a zablokuje se, zatímco jiné vlákno obsahuje zámek přístupu D3D. Tento zámek je nerekurzivní: Jedná se o nedefinované chování pro volání této funkce z vlákna, které již zámek obsahuje. Jedná se o nedefinované chování, které provádí operace na accelerator_view nebo jakémkoli kontejneru dat přidruženém k accelerator_view z vlákna, které obsahuje zámek přístupu D3D. Viz také scoped_d3d_access_lock třída RAII pro zámek přístupu D3D založený na oboru.

```cpp
void __cdecl d3d_access_lock(accelerator_view& _Av);
```

### <a name="parameters"></a>Parametry

*_Av*<br/>
Accelerator_view pro zámek.

## <a name="d3d_access_try_lock"></a>d3d_access_try_lock

Došlo k pokusu o získání zámku přístupu D3D na accelerator_view bez blokování.

```cpp
bool __cdecl d3d_access_try_lock(accelerator_view& _Av);
```

### <a name="parameters"></a>Parametry

*_Av*<br/>
Accelerator_view pro zámek.

### <a name="return-value"></a>Návratová hodnota

true, pokud byl zámek získán, nebo false, pokud je v současné době držen jiným vláknem.

## <a name="d3d_access_unlock"></a>d3d_access_unlock

Uvolněte zámek přístupu D3D na daném accelerator_view. Pokud volající vlákno nedrží zámek na accelerator_view výsledky nejsou definovány.

```cpp
void __cdecl d3d_access_unlock(accelerator_view& _Av);
```

### <a name="parameters"></a>Parametry

*_Av*<br/>
Accelerator_view, pro který se má zámek uvolnit

## <a name="firstbithigh"></a>firstbithigh –

Získá umístění prvního nastaveného bitu v _X, počínaje bitem s nejvyšším pořadím a přesunem směrem k bitu s nejnižším pořadím.

```cpp
inline int firstbithigh(int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Celočíselná hodnota

### <a name="return-value"></a>Návratová hodnota

Umístění prvního nastaveného bitu

## <a name="firstbitlow"></a>firstbitlow –

Získá umístění prvního nastaveného bitu v _X, počínaje nejnižším pořadím a funkčností směrem k bitu s nejvyšším pořadím.

```cpp
inline int firstbitlow(int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Celočíselná hodnota

### <a name="return-value"></a>Návratová hodnota

Vrátí umístění prvního nastaveného bitu.

## <a name="get_buffer"></a>get_buffer

Načte rozhraní pro vyrovnávací paměť Direct3D, které je podkladové pro zadané pole.

```cpp
template<
    typename value_type,
    int _Rank
>
IUnknown *get_buffer(
    const array<value_type, _Rank>& _Array)  ;
```

### <a name="parameters"></a>Parametry

*value_type*<br/>
Typ prvků v poli.

*_Rank*<br/>
Rozměr pole.

*_Array*<br/>
Pole na accelerator_view Direct3D, pro které se vrátí základní rozhraní vyrovnávací paměti Direct3D.

### <a name="return-value"></a>Návratová hodnota

Ukazatel rozhraní IUnknown odpovídající vyrovnávací paměti Direct3D podkladového pole.

## <a name="a-nameget_device-get_device"></a><a name="get_device"> get_device

Získejte rozhraní zařízení D3D, které je podkladové accelerator_view.

```cpp
IUnknown* get_device(const accelerator_view Av);
```

### <a name="parameters"></a>Parametry

*Audiovizuální*<br/>
Accelerator_view D3D, pro který je vráceno základní rozhraní zařízení D3D.

### <a name="return-value"></a>Návratová hodnota

Ukazatel rozhraní `IUnknown` zařízení D3D, které je podkladem accelerator_view.

## <a name="imax"></a>imax

Určení maximální číselné hodnoty argumentů

```cpp
inline int imax(
    int _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Celočíselná hodnota

*_Y*<br/>
Celočíselná hodnota

### <a name="return-value"></a>Návratová hodnota

Vrátí maximální číselnou hodnotu argumentů.

## <a name="imin"></a>imin

Určení minimální číselné hodnoty argumentů

```cpp
inline int imin(
    int _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Celočíselná hodnota

*_Y*<br/>
Celočíselná hodnota

### <a name="return-value"></a>Návratová hodnota

Vrátí minimální číselnou hodnotu argumentů.

## <a name="is_timeout_disabled"></a>is_timeout_disabled

Vrátí logický příznak označující, zda je časový limit pro zadaný accelerator_view zakázán. To odpovídá příznaku D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT pro vytvoření zařízení Direct3D.

```cpp
bool __cdecl is_timeout_disabled(const accelerator_view& _Accelerator_view);
```

### <a name="parameters"></a>Parametry

*_Accelerator_view*<br/>
Accelerator_view, pro který se má zadat dotaz na nastavení časový limit zakázán.

### <a name="return-value"></a>Návratová hodnota

Logický příznak označující, zda je časový limit pro zadanou accelerator_view zakázán.

## <a name="mad"></a>Mad –

Vypočítá součin prvního a druhého zadaného argumentu a potom přidá třetí zadaný argument.

```cpp
inline float mad(
    float _X,
    float _Y,
    float _Z) restrict(amp);

inline double mad(
    double _X,
    double _Y,
    double _Z) restrict(amp);

inline int mad(
    int _X,
    int _Y,
    int _Z) restrict(amp);

inline unsigned int mad(
    unsigned int _X,
    unsigned int _Y,
    unsigned int _Z) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
První zadaný argument.

*_Y*<br/>
Druhý zadaný argument.

*_Z*<br/>
Třetí zadaný argument.

### <a name="return-value"></a>Návratová hodnota

Výsledek `_X` \* `_Y` + `_Z`.

## <a name="make_array"></a>make_array

Vytvoří pole z ukazatele rozhraní vyrovnávací paměti Direct3D.

```cpp
template<
    typename value_type,
    int _Rank
>
array<value_type, _Rank> make_array(
    const extent<_Rank>& _Extent,
    const Concurrency::accelerator_view& _Rv,
    IUnknown* _D3D_buffer)  ;
```

### <a name="parameters"></a>Parametry

*value_type*<br/>
Typ prvku pole, které má být vytvořeno.

*_Rank*<br/>
Rozměr pole, které má být vytvořeno.

*_Extent*<br/>
Rozsah, který popisuje tvar agregace pole.

*_Rv*<br/>
Zobrazení akcelerátoru D3D, na kterém má být pole Vytvořeno.

*_D3D_buffer*<br/>
Ukazatel rozhraní IUnknown vyrovnávací paměti D3D, ze kterého se má vytvořit pole

### <a name="return-value"></a>Návratová hodnota

Pole vytvořené pomocí poskytnuté vyrovnávací paměti Direct3D.

## <a name="noise"></a>neobsažných

Generuje náhodnou hodnotu pomocí algoritmu Perlin šumu.

```cpp
inline float noise(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou, ze které se má generovat Perlin šum

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu šumu Perlin v rozsahu od-1 do 1.

## <a name="radians"></a>rad

Převede _X ze stupňů na radiány.

```cpp
inline float radians(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí _X převedené ze stupňů na radiány.

## <a name="rcp"></a>rcp

Vypočítá reciproční zadaný argument pomocí rychlé aproximace.

```cpp
inline float rcp(float _X) restrict(amp);

inline double rcp(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota, pro kterou se má vypočítat reciproční.

### <a name="return-value"></a>Návratová hodnota

Převrácená část zadaného argumentu.

## <a name="reversebits"></a>reversebits –

Obrátí pořadí bitů v _X

```cpp
inline unsigned int reversebits(unsigned int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Celočíselná hodnota bez znaménka

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu se zpětným pořadím vráceným v _X

## <a name="saturate"></a>saturate –

Svorky _X v rozsahu od 0 do 1.

```cpp
inline float saturate(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí _X svorkou v rozsahu 0 až 1.

## <a name="sign"></a>osobě

Určuje znaménko zadaného argumentu.

```cpp
inline int sign(int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Celočíselná hodnota

### <a name="return-value"></a>Návratová hodnota

Znaménko argumentu.

## <a name="smoothstep"></a>smoothstep –

Vrátí plynulou Hermitovu interpolaci mezi 0 a 1, pokud je _X v rozsahu [_Min, _Max].

```cpp
inline float smoothstep(
    float _Min,
    float _Max,
    float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Min*<br/>
Hodnota s plovoucí desetinnou čárkou

*_Max*<br/>
Hodnota s plovoucí desetinnou čárkou

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí 0, pokud je _X menší než _Min; 1, pokud je _X větší než _Max; v opačném případě hodnota mezi 0 a 1, pokud _X v rozsahu [_Min, _Max]

## <a name="step"></a>Krok

Porovná dvě hodnoty, vrátí hodnotu 0 nebo 1 podle toho, která hodnota je větší.

```cpp
inline float step(
    float _Y,
    float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Y*<br/>
Hodnota s plovoucí desetinnou čárkou

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu 1, pokud _X je větší nebo rovna _Y; v opačném případě 0

## <a name="umax"></a>společnosti

Určení maximální číselné hodnoty argumentů

```cpp
inline unsigned int umax(
    unsigned int _X,
    unsigned int _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Celočíselná hodnota

*_Y*<br/>
Celočíselná hodnota

### <a name="return-value"></a>Návratová hodnota

Vrátí maximální číselnou hodnotu argumentů.

## <a name="umin"></a>umin

Určení minimální číselné hodnoty argumentů

```cpp
inline unsigned int umin(
    unsigned int _X,
    unsigned int _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Celočíselná hodnota

*_Y*<br/>
Celočíselná hodnota

### <a name="return-value"></a>Návratová hodnota

Vrátí minimální číselnou hodnotu argumentů.

## <a name="see-also"></a>Viz také

[Concurrency::direct3d – obor názvů](concurrency-direct3d-namespace.md)
