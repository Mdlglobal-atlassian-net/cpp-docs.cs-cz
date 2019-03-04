---
title: Funkce oboru názvů Concurrency::Direct3D (AMP)
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
ms.openlocfilehash: 0a2977faf094aafb6290063e39e062ffaeaaec81
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57281327"
---
# <a name="concurrencydirect3d-namespace-functions-amp"></a>Funkce oboru názvů Concurrency::Direct3D (AMP)

||||
|-|-|-|
|[abs](#abs)|[Stažení](#clamp)|[countbits –](#countbits)|
|[create_accelerator_view](#create_accelerator_view)|[d3d_access_lock](#d3d_access_lock)||
|[d3d_access_try_lock](#d3d_access_try_lock)|[d3d_access_unlock](#d3d_access_unlock)|[firstbithigh –](#firstbithigh)|
|[firstbitlow](#firstbitlow)|[get_buffer](#get_buffer)|[get_device](#get_device)|
|[imax](#imax)|[imin](#imin)|[is_timeout_disabled](#is_timeout_disabled)|
|[MAD –](#mad)|[make_array](#make_array)|[šumu](#noise)|
|[RADIANS](#radians)|[rcp](#rcp)|[reversebits –](#reversebits)|
|[Saturate](#saturate)|[sign](#sign)|[smoothstep](#smoothstep)|
|[Krok](#step)|[umax](#umax)|[umin](#umin)|

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp.h **Namespace:** Souběžnost

##  <a name="abs"></a>  abs

Vrátí absolutní hodnotu argumentu

```
inline int abs(int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Celočíselná hodnota

### <a name="return-value"></a>Návratová hodnota

Vrátí absolutní hodnotu argumentu.

##  <a name="clamp"></a>  Stažení

Vypočítá hodnotu prvního zadaného argumentu připnutého k oblasti definované druhý a třetí zadaný argument.

```
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
Hodnota, která má být přichycena

*_Min*<br/>
Dolní mez rozsahu upnutí.

*_Max*<br/>
Horní mez rozsahu upnutí.

### <a name="return-value"></a>Návratová hodnota

Přichycená hodnota parametru `_X`.

##  <a name="countbits"></a>  countbits –

Spočítá počet nastavených bitů v proměnné _X

```
inline unsigned int countbits(unsigned int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota celé číslo bez znaménka

### <a name="return-value"></a>Návratová hodnota

Vrátí počet nastavených bitů v proměnné _X

## <a name="create_accelerator_view"></a> create_accelerator_view –

Vytvoří [accelerator_view](accelerator-view-class.md) objekt z ukazatele na rozhraní zařízení Direct3D.

## <a name="syntax"></a>Syntaxe

```
accelerator_view create_accelerator_view(
    IUnknown * _D3D_device
    queuing_mode _Qmode = queuing_mode_automatic);

accelerator_view create_accelerator_view(
    accelerator& _Accelerator,
    bool _Disable_timeout
    queuing_mode _Qmode = queuing_mode_automatic);
```

#### <a name="parameters"></a>Parametry

*_Accelerator*<br/>
Akcelerátor, na kterém má být vytvořen nový objekt accelerator_view.

*_D3D_device*<br/>
Ukazatel na rozhraní zařízení Direct3D.

*_Disable_timeout*<br/>
Parametr logické hodnoty, která určuje, zda by mělo být zakázáno časový limit pro nově vytvořený objekt accelerator_view. To odpovídá příznaku D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT pro vytváření zařízení Direct3D a slouží k označení, pokud operační systém by měl umožnit pracovní vytížení, které trvat déle než 2 sekundy bez resetování zařízení za časový limit Windows mechanismus detekce a obnovení. Použití tohoto příznaku se doporučuje, když potřebujete provádět časově náročné úlohy v zobrazení accelerator_view.

*_Qmode*<br/>
[Queuing_mode –](concurrency-namespace-enums-amp.md#queuing_mode) má být použit pro nově vytvořený objekt accelerator_view. Tento parametr má výchozí hodnotu `queuing_mode_automatic`.

## <a name="return-value"></a>Návratová hodnota

`accelerator_view` Objekt vytvořený z předaného rozhraní zařízení Direct3D.

## <a name="remarks"></a>Poznámky

Tato funkce vytvoří nový `accelerator_view` objekt ze stávajícího ukazatele na rozhraní zařízení Direct3D. Pokud bude volání funkce úspěšné, je počet odkazů parametru zvýšen prostřednictvím `AddRef` volání do rozhraní. Když je už nebude potřeba v rámci DirectX kódu, můžete jej bezpečně uvolnit objektu. Pokud selže volání metody [runtime_exception](runtime-exception-class.md) je vyvolána výjimka.

`accelerator_view` Objekt, který vytvoříte pomocí této funkce je bezpečné pro vlákna. Je nutné synchronizovat souběžné použití objektu `accelerator_view` objektu. Nesynchronizované souběžné použití objektu `accelerator_view` objektu a hrubého rozhraní ID3D11Device způsobuje nedefinované chování.

Modul runtime C++ AMP poskytuje podrobné informace o chybě v režimu ladění pomocí vrstvy rozhraní D3D ladění, pokud použijete `D3D11_CREATE_DEVICE_DEBUG` příznak.

##  <a name="d3d_access_lock"></a>  d3d_access_lock

Získejte zámek na accelerator_view pro účely bezpečného provádění operací D3D na prostředcích sdílených s accelerator_view. Prostředky accelerator_view a všechny prostředky C++ AMP, vnitřně přidružené s tímto prostředkem accelerator_view přijmou toto uzamčení při provádění operací a budou blokovat, zatímco jiné vlákno drží zámek přístupu D3D. Tento zámek je nerekurzivní: Voláním této funkce z vlákna již obsahujícího zámek vyvolá nedefinované chování je. To je nedefinované chování k provádění operací na objektu accelerator_view nebo jakémkoli kontejneru dat spojeném s objektem accelerator_view z vlákna, které drží zámek přístupu D3D. Další informace naleznete v tématu scoped_d3d_access_lock, třídě stylu RAII pro obor zámku přístupu D3D.

```
void __cdecl d3d_access_lock(accelerator_view& _Av);
```

### <a name="parameters"></a>Parametry

*_Av*<br/>
Accelerator_view pro uzamčení.

##  <a name="d3d_access_try_lock"></a>  d3d_access_try_lock

Pokus o získání zámku přístupu D3D na accelerator_view bez blokování.

```
bool __cdecl d3d_access_try_lock(accelerator_view& _Av);
```

### <a name="parameters"></a>Parametry

*_Av*<br/>
Accelerator_view pro uzamčení.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud byl získán zámek, nebo hodnotu NEPRAVDA, pokud je právě načtený v jiném vlákně.

##  <a name="d3d_access_unlock"></a>  d3d_access_unlock

Uvolněte zámek přístupu D3D na daný objekt accelerator_view. Pokud volající vlákno není držitelem zámku objektu accelerator_view nejsou výsledky definovány.

```
void __cdecl d3d_access_unlock(accelerator_view& _Av);
```

### <a name="parameters"></a>Parametry

*_Av*<br/>
Accelerator_view, pro kterou má uvolní zámek.

##  <a name="firstbithigh"></a>  firstbithigh –

Zjistí umístění prvního nastaveného bitu v _X, počínaje bitu s nejvyšším pořadím a přesunem směrem k bitu s nejnižším pořadím.

```
inline int firstbithigh(int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Celočíselná hodnota

### <a name="return-value"></a>Návratová hodnota

Umístění prvního nastaveného bitu

##  <a name="firstbitlow"></a>  firstbitlow –

Zjistí umístění prvního nastaveného bitu v _X, počínaje bitu s nejnižším pořadím a přesunem směrem k bitu s nejvyšším pořadím.

```
inline int firstbitlow(int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Celočíselná hodnota

### <a name="return-value"></a>Návratová hodnota

Vrátí umístění prvního nastaveného bitu

##  <a name="get_buffer"></a>  get_buffer –

Získejte rozhraní vyrovnávací paměti Direct3D základního zadaného pole.

```
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
Řád objektu array.

*_Pole*<br/>
Pole accelerator_view rozhraní Direct3D, pro který je vrácen základní vyrovnávací paměti rozhraní Direct3D.

### <a name="return-value"></a>Návratová hodnota

Ukazatel rozhraní IUnknown odpovídající vyrovnávací paměti rozhraní Direct3D podkládající pole.

## <a name="a-namegetdevice-getdevice"></a><a name="get_device"> get_device –

Získejte rozhraní zařízení D3D accelerator_view základní.

```
IUnknown* get_device(const accelerator_view Av);
```

### <a name="parameters"></a>Parametry

*Av*<br/>
Accelerator_view rozhraní D3D, pro které je vráceno základní rozhraní D3D zařízení.

### <a name="return-value"></a>Návratová hodnota

`IUnknown` Ukazatele na rozhraní zařízení D3D základní accelerator_view.

##  <a name="imax"></a>  imax

Určí maximální číselnou hodnotu argumentů

```
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

Vrátit maximální číselnou hodnotu argumentů

##  <a name="imin"></a>  imin –

Určí minimální číselnou hodnotu argumentů

```
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

Vrátit minimální číselnou hodnotu argumentů

##  <a name="is_timeout_disabled"></a>  is_timeout_disabled –

Vrátí příznak logické hodnoty označující, pokud vypršení časového limitu je zakázáno pro zadaný accelerator_view. To odpovídá příznaku D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT pro vytváření zařízení Direct3D.

```
bool __cdecl is_timeout_disabled(const accelerator_view& _Accelerator_view);
```

### <a name="parameters"></a>Parametry

*_Accelerator_view*<br/>
Accelerator_view, pro který nastavení deaktivovaného časového limitu, je možné dotazovat.

### <a name="return-value"></a>Návratová hodnota

Příznak logické hodnoty označující, pokud vypršení časového limitu je zakázáno pro zadaný accelerator_view.

##  <a name="mad"></a>  mad

Vypočítá součin prvního a druhého zadaného argumentu, poté přičte třetí zadaný argument.

```
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
Prvního zadaného argumentu.

*_Y*<br/>
Druhý zadaný argument.

*_Z*<br/>
Třetí zadaný argument.

### <a name="return-value"></a>Návratová hodnota

Výsledek `_X` \* `_Y`  +  `_Z`.

##  <a name="make_array"></a>  make_array –

Vytvoří pole z ukazatele na rozhraní vyrovnávací paměti rozhraní Direct3D.

```
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
Typ elementu pole, které chcete vytvořit.

*_Rank*<br/>
Řád objektu array má být vytvořen.

*_Extent*<br/>
Objekt extent popisující tvar množiny pole.

*_Rv*<br/>
Zobrazení akcelerátoru D3D, na kterém se má vytvořit pole.

*_D3D_buffer*<br/>
Ukazatel na rozhraní IUnknown vyrovnávací paměti rozhraní D3D k vytvoření pole z.

### <a name="return-value"></a>Návratová hodnota

Pole vytvořené pomocí zadané vyrovnávací paměti rozhraní Direct3D.

##  <a name="noise"></a>  šumu

Vygeneruje náhodnou hodnotu pomocí algoritmu Perlinova šumu.

```
inline float noise(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
S plovoucí desetinnou čárkou, ze kterého se má generovat Perlinova šumu

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu The Perlinova šumu v rozsahu mezi -1 a 1

##  <a name="radians"></a>  RADIANS

Převede proměnnou _X ze stupňů na radiány.

```
inline float radians(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu proměnné _X ze stupňů na radiány

##  <a name="rcp"></a>  rcp

Vypočte střídavost zadaného argumentu pomocí rychlého odhadu.

```
inline float rcp(float _X) restrict(amp);

inline double rcp(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota, pro které chcete vypočítat převrácenou hodnotu.

### <a name="return-value"></a>Návratová hodnota

Převrácená hodnota zadaného argumentu.

##  <a name="reversebits"></a>  reversebits –

Obrátí pořadí bitů v proměnné _X

```
inline unsigned int reversebits(unsigned int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota celé číslo bez znaménka

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu s pořadí bitů v proměnné _X

##  <a name="saturate"></a>  Saturate

Omezí hodnotu proměnné _X z rozsahu 0 až 1

```
inline float saturate(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Hodnota s plovoucí desetinnou čárkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu proměnné _X omezen v rozsahu 0 až 1

##  <a name="sign"></a>  přihlášení

Určuje znak zadaného argumentu.

```
inline int sign(int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Celočíselná hodnota

### <a name="return-value"></a>Návratová hodnota

Znaménko argumentu.

##  <a name="smoothstep"></a>  smoothstep –

Vrátí smooth Hermitovu interpolaci mezi 0 a 1, pokud _X je v rozsahu [_Min, _Max].

```
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

Vrátí hodnotu 0, pokud _X je menší než _Min; 1, pokud je větší než _Max; proměnné _X v opačném případě hodnota mezi 0 a 1, pokud _X je v rozsahu [_Min, _Max]

##  <a name="step"></a>  Krok

Porovná dvě hodnoty a vrátí hodnotu 0 nebo 1 podle toho, která hodnota je větší

```
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

Vrátí hodnotu 1, pokud je proměnné _X větší než nebo rovna hodnotě _Y; jinak 0.

##  <a name="umax"></a>  UMAX

Určí maximální číselnou hodnotu argumentů

```
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

Vrátit maximální číselnou hodnotu argumentů

##  <a name="umin"></a>  umin –

Určí minimální číselnou hodnotu argumentů

```
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

Vrátit minimální číselnou hodnotu argumentů

## <a name="see-also"></a>Viz také:

[Concurrency::direct3d – obor názvů](concurrency-direct3d-namespace.md)
