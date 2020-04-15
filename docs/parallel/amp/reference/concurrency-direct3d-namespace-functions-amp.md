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
ms.openlocfilehash: e21b1f2869ab81973b341abc5371714fbf8580e2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375935"
---
# <a name="concurrencydirect3d-namespace-functions-amp"></a>Funkce oboru názvů Concurrency::direct3d (AMP)

||||
|-|-|-|
|[Abs](#abs)|[Svorku](#clamp)|[countbits](#countbits)|
|[create_accelerator_view](#create_accelerator_view)|[d3d_access_lock](#d3d_access_lock)||
|[d3d_access_try_lock](#d3d_access_try_lock)|[d3d_access_unlock](#d3d_access_unlock)|[firstbithigh](#firstbithigh)|
|[firstbitlow](#firstbitlow)|[get_buffer](#get_buffer)|[get_device](#get_device)|
|[Imax](#imax)|[imin](#imin)|[is_timeout_disabled](#is_timeout_disabled)|
|[Šílený](#mad)|[make_array](#make_array)|[Hluk](#noise)|
|[Radiánech](#radians)|[Rcp](#rcp)|[reversebits](#reversebits)|
|[Nasycení](#saturate)|[Znamení](#sign)|[smoothstep](#smoothstep)|
|[Krok](#step)|[Umax](#umax)|[umin](#umin)|

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp.h **Obor názvů:** Souběžnost

## <a name="abs"></a><a name="abs"></a>Abs

Vrátí absolutní hodnotu argumentu.

```cpp
inline int abs(int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Celočíselná hodnota

### <a name="return-value"></a>Návratová hodnota

Vrátí absolutní hodnotu argumentu.

## <a name="clamp"></a><a name="clamp"></a>Svorku

Vypočítá hodnotu prvního zadaného argumentu upnutého do rozsahu definovaného druhým a třetím zadaným argumentem.

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
Hodnota, která má být upnuta

*_Min*<br/>
Dolní mez upínacího rozsahu.

*_Max*<br/>
Horní mez upínacího rozsahu.

### <a name="return-value"></a>Návratová hodnota

Upnutá hodnota `_X`.

## <a name="countbits"></a><a name="countbits"></a>countbits

Spočítá počet nastavených bitů v _X

```cpp
inline unsigned int countbits(unsigned int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Nepodepsaná celá hodnota celého čísla

### <a name="return-value"></a>Návratová hodnota

Vrátí počet nastavených bitů v _X

## <a name="create_accelerator_view"></a><a name="create_accelerator_view"></a>create_accelerator_view

Vytvoří [accelerator_view](accelerator-view-class.md) objekt z ukazatele na rozhraní zařízení Direct3D.

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
Logický parametr, který určuje, zda má být časový limit zakázán pro nově vytvořené accelerator_view. To odpovídá příznaku D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT pro vytvoření zařízení Direct3D a slouží k označení, pokud operační systém by měl povolit úlohy, které trvá déle než 2 sekundy spustit bez resetování zařízení na windows timeout detekce a mechanismus obnovení. Použití tohoto příznaku se doporučuje, pokud potřebujete provádět časově náročné úkoly na accelerator_view.

*_Qmode*<br/>
[Queuing_mode,](concurrency-namespace-enums-amp.md#queuing_mode) který má být použit pro nově vytvořené accelerator_view. Tento parametr má výchozí `queuing_mode_automatic`hodnotu .

## <a name="return-value"></a>Návratová hodnota

Objekt `accelerator_view` vytvořený z předaná rozhraní zařízení Direct3D.

## <a name="remarks"></a>Poznámky

Tato funkce vytvoří `accelerator_view` nový objekt z existujícího ukazatele na rozhraní zařízení Direct3D. Pokud je volání funkce úspěšné, počet odkazů parametru se zvětší `AddRef` pomocí volání rozhraní. Objekt můžete bezpečně uvolnit, pokud již není vyžadován v kódu DirectX. Pokud volání metody selže, je vyvolána [runtime_exception.](runtime-exception-class.md)

Objekt, `accelerator_view` který vytvoříte pomocí této funkce je bezpečné pro přístup z více vláken. Je nutné synchronizovat souběžné použití objektu. `accelerator_view` Nesynchronizované souběžné použití `accelerator_view` objektu a nezpracovanérozhraní ID3D11Device způsobuje nedefinované chování.

Runtime C++ AMP poskytuje podrobné informace o chybě v režimu ladění pomocí `D3D11_CREATE_DEVICE_DEBUG` vrstvy ladění D3D, pokud použijete příznak.

## <a name="d3d_access_lock"></a><a name="d3d_access_lock"></a>d3d_access_lock

Získejte zámek na accelerator_view za účelem bezpečného provádění operací D3D na prostředky sdílené s accelerator_view. accelerator_view a všechny prostředky C++ AMP přidružené k tomuto accelerator_view interně převzít tento zámek při provádění operací a bude blokovat, zatímco jiné vlákno obsahuje přístupový zámek D3D. Tento zámek je non rekurzivní: Je nedefinované chování volat tuto funkci z vlákna, které již drží zámek. Je nedefinované chování provádět operace na accelerator_view nebo jakýkoli datový kontejner přidružený k accelerator_view z vlákna, který obsahuje zámek přístupu D3D. Viz také scoped_d3d_access_lock, třída ve stylu RAII pro přístupový zámek D3D založený na oboru.

```cpp
void __cdecl d3d_access_lock(accelerator_view& _Av);
```

### <a name="parameters"></a>Parametry

*_Av*<br/>
Accelerator_view zamknout.

## <a name="d3d_access_try_lock"></a><a name="d3d_access_try_lock"></a>d3d_access_try_lock

Pokus o získání přístupového zámku D3D na accelerator_view bez blokování.

```cpp
bool __cdecl d3d_access_try_lock(accelerator_view& _Av);
```

### <a name="parameters"></a>Parametry

*_Av*<br/>
Accelerator_view zamknout.

### <a name="return-value"></a>Návratová hodnota

true, pokud byl zámek získán, nebo false, pokud je aktuálně v držení jinévlákno.

## <a name="d3d_access_unlock"></a><a name="d3d_access_unlock"></a>d3d_access_unlock

Uvolněte přístupový zámek D3D na dané accelerator_view. Pokud volající vlákno nedrží zámek na accelerator_view výsledky nejsou definovány.

```cpp
void __cdecl d3d_access_unlock(accelerator_view& _Av);
```

### <a name="parameters"></a>Parametry

*_Av*<br/>
accelerator_view, pro které má být zámek uvolněn.

## <a name="firstbithigh"></a><a name="firstbithigh"></a>firstbithigh

Získá umístění první sada bit v _X, počínaje bit nejvyšší pořadí a pohybující se směrem k bit nejnižší pořadí.

```cpp
inline int firstbithigh(int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Celočíselná hodnota

### <a name="return-value"></a>Návratová hodnota

Umístění prvního nastaveného bitu

## <a name="firstbitlow"></a><a name="firstbitlow"></a>firstbitlow

Získá umístění první sada bit v _X, počínaje nejnižší pořadí bit a pracuje směrem k bit nejvyšší pořadí.

```cpp
inline int firstbitlow(int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Celočíselná hodnota

### <a name="return-value"></a>Návratová hodnota

Vrátí umístění prvního bitu.

## <a name="get_buffer"></a><a name="get_buffer"></a>get_buffer

Získejte rozhraní vyrovnávací paměti Direct3D, které je základem zadaného pole.

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
Pořadí pole.

*_Array*<br/>
Pole na Direct3D accelerator_view, pro které je vráceno základní rozhraní vyrovnávací paměti Direct3D.

### <a name="return-value"></a>Návratová hodnota

Ukazatel rozhraní IUnknown odpovídající vyrovnávací paměti Direct3D, která je základem pole.

## <a name="a-nameget_device-get_device"></a><a name="get_device">get_device

Získejte rozhraní zařízení D3D, které je základem accelerator_view.

```cpp
IUnknown* get_device(const accelerator_view Av);
```

### <a name="parameters"></a>Parametry

*Av*<br/>
D3D accelerator_view, pro které je vráceno základní rozhraní zařízení D3D.

### <a name="return-value"></a>Návratová hodnota

Ukazatel `IUnknown` rozhraní zařízení D3D, které je základem accelerator_view.

## <a name="imax"></a><a name="imax"></a>Imax

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

## <a name="imin"></a><a name="imin"></a>imin

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

## <a name="is_timeout_disabled"></a><a name="is_timeout_disabled"></a>is_timeout_disabled

Vrátí logický příznak označující, zda je časový čas pro zadaný accelerator_view zakázán. To odpovídá příznaku D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT pro vytvoření zařízení Direct3D.

```cpp
bool __cdecl is_timeout_disabled(const accelerator_view& _Accelerator_view);
```

### <a name="parameters"></a>Parametry

*_Accelerator_view*<br/>
Accelerator_view, pro které má být dotazováno nastavení zakázán časový čas.

### <a name="return-value"></a>Návratová hodnota

Logický příznak označující, zda je časový čas pro zadaný accelerator_view zakázán.

## <a name="mad"></a><a name="mad"></a>Šílený

Vypočítá součin prvního a druhého zadaného argumentu a přidá třetí zadaný argument.

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

`_X` \* Výsledek `_Y`  + . `_Z`

## <a name="make_array"></a><a name="make_array"></a>make_array

Vytvořte pole z ukazatele rozhraní vyrovnávací paměti Direct3D.

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
Pořadí pole, které má být vytvořeno.

*_Extent*<br/>
Rozsah, který popisuje tvar agregace pole.

*_Rv*<br/>
Zobrazení akcelerátoru D3D, ve kterém má být pole vytvořeno.

*_D3D_buffer*<br/>
IUnknown ukazatel rozhraní vyrovnávací paměti D3D k vytvoření pole z.

### <a name="return-value"></a>Návratová hodnota

Pole vytvořené pomocí poskytované vyrovnávací paměti Direct3D.

## <a name="noise"></a><a name="noise"></a>Hluk

Generuje náhodnou hodnotu pomocí algoritmu perlinového šumu.

```cpp
inline float noise(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou desetinnou hodnotou, ze které se vytváří perlinový šum

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu perlinového šumu v rozsahu od -1 do 1.

## <a name="radians"></a><a name="radians"></a>Radiánech

Převede _X ze stupňů na radiány.

```cpp
inline float radians(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí _X převedeny ze stupňů na radiány.

## <a name="rcp"></a><a name="rcp"></a>Rcp

Vypočítá reciproční zadaný argument pomocí rychlé aproximace.

```cpp
inline float rcp(float _X) restrict(amp);

inline double rcp(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota, pro kterou chcete vypočítat reciproční.

### <a name="return-value"></a>Návratová hodnota

Reciproční zadaný argument.

## <a name="reversebits"></a><a name="reversebits"></a>reversebits

Obrátí pořadí bitů v _X

```cpp
inline unsigned int reversebits(unsigned int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Nepodepsaná celá hodnota celého čísla

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu s bitovým pořadím obráceným v _X

## <a name="saturate"></a><a name="saturate"></a>Nasycení

Svorky _X v rozsahu 0 až 1

```cpp
inline float saturate(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí _X upnutvrozsahu 0 až 1.

## <a name="sign"></a><a name="sign"></a>Znamení

Určuje znaménko zadaného argumentu.

```cpp
inline int sign(int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Celočíselná hodnota

### <a name="return-value"></a>Návratová hodnota

Znamení argumentu.

## <a name="smoothstep"></a><a name="smoothstep"></a>smoothstep

Vrátí hladkou interpolaci Hermitu mezi 0 a 1, pokud je _X v rozsahu [_Min, _Max].

```cpp
inline float smoothstep(
    float _Min,
    float _Max,
    float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Min*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

*_Max*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu 0, pokud je _X menší než _Min; .1, je-li _X větší než _Max; v opačném případě hodnota mezi 0 a 1, pokud je _X v rozsahu [_Min, _Max]

## <a name="step"></a><a name="step"></a>Krok

Porovná dvě hodnoty, vrací 0 nebo 1 na základě které hodnoty je větší

```cpp
inline float step(
    float _Y,
    float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Y*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

*_X*<br/>
Hodnota s plovoucí desetinnou tálicí hodnotou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu 1, pokud je _X větší nebo rovna _Y; jinak 0

## <a name="umax"></a><a name="umax"></a>Umax

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

## <a name="umin"></a><a name="umin"></a>umin

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
