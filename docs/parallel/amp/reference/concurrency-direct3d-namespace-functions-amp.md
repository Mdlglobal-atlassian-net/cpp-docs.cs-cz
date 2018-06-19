---
title: Concurrency::Direct3D – obor názvů funkcí (a) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- amp/Concurrency::direct3d::abs
- amp/Concurrency::direct3d::countbits
- amp/Concurrency::direct3d::create_accelerator_view
- amp/Concurrency::direct3d::d3d_access_lock
- amp/Concurrency::direct3d::d3d_access_unlock
- amp/Concurrency::direct3d::firstbithigh
- amp/Concurrency::direct3d::get_buffer
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
dev_langs:
- C++
ms.assetid: 28943b62-52c9-42dc-baf1-ca7b095c1a19
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 57015cc84053216e76f3459170c3dde9a26bb43c
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33693725"
---
# <a name="concurrencydirect3d-namespace-functions-amp"></a>Funkce Concurrency::Direct3D – obor názvů (AMP)
||||  
|-|-|-|  
|[Abs](#abs)|[svorka](#clamp)|[countbits –](#countbits)|
|[create_accelerator_view](#create_accelerator_view)|||
|[d3d_access_lock](#d3d_access_lock)|[d3d_access_try_lock](#d3d_access_try_lock)|[d3d_access_unlock](#d3d_access_unlock)|  
|[firstbithigh –](#firstbithigh)|[firstbitlow –](#firstbitlow)|[get_buffer](#get_buffer)|  
|[imax](#imax)|[imin](#imin)|[is_timeout_disabled](#is_timeout_disabled)|  
|[MAD –](#mad)|[make_array](#make_array)|[šumu](#noise)|  
|[radiánech](#radians)|[rcp](#rcp)|[reversebits –](#reversebits)|  
|[saturate –](#saturate)|[sign](#sign)|[smoothstep –](#smoothstep)|  
|[Krok](#step)|[umax](#umax)|[umin –](#umin)|  

## <a name="requirements"></a>Požadavky
**Záhlaví:** amp.h **Namespace:** souběžnosti
  
##  <a name="abs"></a>  Abs  
 Vrátí absolutní hodnotu argumentu  
  
```  
inline int abs(int _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Celočíselná hodnota  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí absolutní hodnotu argumentu.  
  
##  <a name="clamp"></a>  svorka  
 Vypočítá hodnotu první zadaného argumentu těsně na definované druhý a třetí argument zadaný rozsah.  
  
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
 `_X`  
 Hodnota, která má být těsně  
  
 `_Min`  
 Dolní mez montážní rozsahu.  
  
 `_Max`  
 Horní mez montážní rozsahu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Clamped hodnota `_X`.  
  
##  <a name="countbits"></a>  countbits –  
 Spočítá počet sadu bitů _X  
  
```  
inline unsigned int countbits(unsigned int _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota celé číslo bez znaménka  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet sadu bitů v _X  

## <a name="create_accelerator_view"></a> create_accelerator_view –  
Vytvoří [accelerator_view](accelerator-view-class.md) objekt z ukazatel na rozhraní Direct3D zařízení.  
  
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
 `_Accelerator`  
 Accelerator, na kterém má být vytvořen nový accelerator_view.  
  
 `_D3D_device`  
 Ukazatel rozhraní Direct3D zařízení.  
  
 `_Disable_timeout`  
 Logický parametr, který určuje, zda by mělo být zakázáno časový limit pro nově vytvořený accelerator_view. To odpovídá příznak D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT pro vytvoření Direct3D – zařízení a slouží k označení, pokud se operační systém by měl povolit úlohy, které trvat déle než 2 sekundy provést bez resetování zařízení podle časového limitu systému Windows mechanismus detekce a obnovení. Pokud je potřeba časově náročné úkoly na accelerator_view se doporučuje použít tento příznak.  
  
 `_Qmode`  
 [Queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode) má být použit pro nově vytvořený accelerator_view. Tento parametr má výchozí hodnotu `queuing_mode_automatic`.  
  
## <a name="return-value"></a>Návratová hodnota  
 `accelerator_view` Objekt vytvořený z rozhraní zařízení předaný Direct3D.  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce vytvoří novou `accelerator_view` objekt z existující ukazatel na rozhraní Direct3D zařízení. Pokud je úspěšné volání funkce, se zvýší počet odkazů parametr prostřednictvím `AddRef` volání rozhraní. Objekt můžete bezpečně uvolnit, když už se nevyžaduje v kódu DirectX. Pokud selže volání metody, [runtime_exception](runtime-exception-class.md) je vyvolána výjimka.  
  
 `accelerator_view` Objekt, který vytvoříte pomocí této funkce je zaručeno bezpečné používání vláken. Souběžné používání musí synchronizovat `accelerator_view` objektu. Rozcházejí souběžných využití `accelerator_view` objekt a rozhraní nezpracovaná ID3D11Device způsobí, že nedefinované chování.  
  
 Modul runtime C++ AMP poskytuje podrobné informace o chybě v režimu ladění pomocí vrstvě D3D ladění, pokud použijete `D3D11_CREATE_DEVICE_DEBUG` příznak.  
  
  
##  <a name="d3d_access_lock"></a>  d3d_access_lock –  
 Získejte zámek na accelerator_view za účelem provádění bezpečně D3D operací s prostředky, které jsou sdíleny s accelerator_view. Accelerator_view a všechny prostředky C++ AMP přidružené k této accelerator_view interně trvat tento zámek při provádění operací a bude blokovat, zatímco jiné vlákno obsahuje zámek D3D přístup. Tato zámek je tohoto nerekurzivního: je nedefinovaný chování pro volání této funkce z vlákna, která již obsahuje zámek. Je definován chování k provádění operací na accelerator_view nebo všech dat kontejneru přidruženého k accelerator_view z vlákna, která obsahuje zámek D3D přístup. Další informace najdete v části scoped_d3d_access_lock, třídu stylu RAII na obor D3D přístup zámek.  
  
```  
void __cdecl d3d_access_lock(accelerator_view& _Av);
```  
  
### <a name="parameters"></a>Parametry  
 `_Av`  
 Accelerator_view k uzamčení.  
  
##  <a name="d3d_access_try_lock"></a>  d3d_access_try_lock  
 Pokuste se získat zámek D3D přístup accelerator_view bez blokování.  
  
```  
bool __cdecl d3d_access_try_lock(accelerator_view& _Av);
```  
  
### <a name="parameters"></a>Parametry  
 `_Av`  
 Accelerator_view k uzamčení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud se získal zámek, nebo hodnotu NEPRAVDA, pokud je aktuálně uchovávat jiné vlákno.  
  
##  <a name="d3d_access_unlock"></a>  d3d_access_unlock –  
 Uvolní zámek D3D přístup na danou accelerator_view. Pokud volající vlákno nemá zámek accelerator_view výsledky nejsou definovány.  
  
```  
void __cdecl d3d_access_unlock(accelerator_view& _Av);
```  
  
### <a name="parameters"></a>Parametry  
 `_Av`  
 Accelerator_view, pro kterou se uvolnit zámek.  
  
##  <a name="firstbithigh"></a>  firstbithigh –  
 Získá umístění první sada bit v _X, počínaje bit s nejvyšším pořadím a pro cestu k bitové nejnižší pořadí.  
  
```  
inline int firstbithigh(int _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Celočíselná hodnota  
  
### <a name="return-value"></a>Návratová hodnota  
 Umístění první bitová sada  
  
##  <a name="firstbitlow"></a>  firstbitlow –  
 Získá umístění první sada bit v _X, počínaje bit nejnižší pořadí a práci směrem k bit s nejvyšším pořadím.  
  
```  
inline int firstbitlow(int _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Celočíselná hodnota  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí první nastavit chvíli umístění  
  
##  <a name="get_buffer"></a>  get_buffer –  
 Získáte rozhraní vyrovnávací paměti Direct3D – základní zadané pole.  
  
```  
template<
    typename value_type,  
    int _Rank  
>  
IUnknown *get_buffer(
    const array<value_type, _Rank>& _Array)  ;  
```  
  
### <a name="parameters"></a>Parametry  
 `value_type`  
 Typ elementů v poli.  
  
 `_Rank`  
 Pořadí pole.  
  
 `_Array`  
 Pole na Direct3D – accelerator_view, pro který je vrácen základní rozhraní Direct3D vyrovnávací paměti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel rozhraní IUnknown odpovídající do vyrovnávací paměti Direct3D – základní pole.  
  
##  <a name="imax"></a>  Imax –  
 Určit maximální číselná hodnota, která jsou argumenty  
  
```  
inline int imax(
    int _X,  
    int _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Celočíselná hodnota  
  
 `_Y`  
 Celočíselná hodnota  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí maximální hodnotu číselného argumenty  
  
##  <a name="imin"></a>  imin –  
 Určení minimální číselná hodnota z argumentů  
  
```  
inline int imin(
    int _X,  
    int _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Celočíselná hodnota  
  
 `_Y`  
 Celočíselná hodnota  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí minimální hodnotu číselného argumenty  
  
##  <a name="is_timeout_disabled"></a>  is_timeout_disabled –  
 Vrátí logický příznak indikující, pokud je pro zadaný accelerator_view zakázané časový limit. To odpovídá příznak D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT pro vytvoření Direct3D zařízení.  
  
```  
bool __cdecl is_timeout_disabled(const accelerator_view& _Accelerator_view);
```  
  
### <a name="parameters"></a>Parametry  
 `_Accelerator_view`  
 Accelerator_view, pro který má být dotazována časový limit zakázané nastavení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Logický příznak indikující, pokud je pro zadaný accelerator_view zakázané časový limit.  
  
##  <a name="mad"></a>  mad  
 Vypočítá součin první a druhý zadaný argument a potom přidá třetí zadaného argumentu.  
  
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
 `_X`  
 První zadaného argumentu.  
  
 `_Y`  
 Druhý zadaného argumentu.  
  
 `_Z`  
 Třetí zadaného argumentu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výsledek `_X`  *  `_Y`  +  `_Z`.  
  
##  <a name="make_array"></a>  make_array –  
 Vytvořte pole z Direct3D – ukazatele rozhraní vyrovnávací paměti.  
  
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
 `value_type`  
 Typ elementu pole, který se má vytvořit.  
  
 `_Rank`  
 Pořadí pole, který se má vytvořit.  
  
 `_Extent`  
 Rozsah popisující obrazec agregace pole.  
  
 `_Rv`  
 Zobrazení akcelerátoru D3D, na kterém má být vytvořen pole.  
  
 `_D3D_buffer`  
 IUnknown – ukazatele rozhraní D3D vyrovnávací paměti k vytvoření pole z.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pole vytvořené pomocí zadané vyrovnávací paměti Direct3D.  
  
##  <a name="noise"></a>  šumu  
 Generuje náhodná hodnota pomocí algoritmu Perlin šumu  
  
```  
inline float noise(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 S plovoucí desetinnou čárkou, ze které se mají vygenerovat Perlin šumu  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací hodnotu šumu Perlin v rozsahu od -1 a 1  
  
##  <a name="radians"></a>  radiánech  
 Převede _X z stupňů radiánech  
  
```  
inline float radians(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí _X převést z stupňů na radiánech  
  
##  <a name="rcp"></a>  rcp  
 Pomocí rychlé aproximace vypočítá vzájemné zadaného argumentu.  
  
```  
inline float rcp(float _X) restrict(amp);

 
inline double rcp(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota, pro které chcete výpočetní vzájemné.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vzájemná zadaného argumentu.  
  
##  <a name="reversebits"></a>  reversebits –  
 Obrátí pořadí bity v _X  
  
```  
inline unsigned int reversebits(unsigned int _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota celé číslo bez znaménka  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu s pořadím bit vrátit v _X  
  
##  <a name="saturate"></a>  saturate –  
 Svorky _X v rozsahu 0 až 1  
  
```  
inline float saturate(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí _X těsně v rozsahu 0 až 1  
  
##  <a name="sign"></a>  Přihlášení  
 Vrátí znaménko zadaného argumentu.  
  
```  
inline int sign(int _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Celočíselná hodnota  
  
### <a name="return-value"></a>Návratová hodnota  
 Znaménko argumentu.  
  
##  <a name="smoothstep"></a>  smoothstep –  
 Vrátí smooth interpolace Hermite mezi 0 a 1, pokud _X je v rozsahu [_min –, _maximální].  
  
```  
inline float smoothstep(
    float _Min,  
    float _Max,  
    float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Min`  
 Hodnota s plovoucí desetinnou čárkou  
  
 `_Max`  
 Hodnota s plovoucí desetinnou čárkou  
  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu 0, pokud _X je menší než _min –; 1, pokud _X je větší než _maximální; jinak hodnotu mezi 0 a 1, pokud _X je v rozsahu [_min –, _maximální]  
  
##  <a name="step"></a>  Krok  
 Porovná dvě hodnoty, vrácení 0 nebo 1 na základě toho, která hodnota větší  
  
```  
inline float step(
    float _Y,  
    float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Y`  
 Hodnota s plovoucí desetinnou čárkou  
  
 `_X`  
 Hodnota s plovoucí desetinnou čárkou  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu 1, pokud _X je větší než nebo rovno _Y; 0, jinak hodnota  
  
##  <a name="umax"></a>  UMAX –  
 Určit maximální číselná hodnota, která jsou argumenty  
  
```  
inline unsigned int umax(
    unsigned int _X,  
    unsigned int _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Celočíselná hodnota  
  
 `_Y`  
 Celočíselná hodnota  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí maximální hodnotu číselného argumenty  
  
##  <a name="umin"></a>  umin –  
 Určení minimální číselná hodnota z argumentů  
  
```  
inline unsigned int umin(
    unsigned int _X,  
    unsigned int _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Celočíselná hodnota  
  
 `_Y`  
 Celočíselná hodnota  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí minimální hodnotu číselného argumenty  
  
## <a name="see-also"></a>Viz také  
 [Concurrency::direct3d – obor názvů](concurrency-direct3d-namespace.md)
