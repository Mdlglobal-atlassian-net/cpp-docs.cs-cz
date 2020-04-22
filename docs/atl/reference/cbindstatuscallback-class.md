---
title: Třída CBindStatusCallback
ms.date: 11/04/2016
f1_keywords:
- CBindStatusCallback
- ATLCTL/ATL::CBindStatusCallback
- ATLCTL/ATL::CBindStatusCallback::CBindStatusCallback
- ATLCTL/ATL::CBindStatusCallback::Download
- ATLCTL/ATL::CBindStatusCallback::GetBindInfo
- ATLCTL/ATL::CBindStatusCallback::GetPriority
- ATLCTL/ATL::CBindStatusCallback::OnDataAvailable
- ATLCTL/ATL::CBindStatusCallback::OnLowResource
- ATLCTL/ATL::CBindStatusCallback::OnObjectAvailable
- ATLCTL/ATL::CBindStatusCallback::OnProgress
- ATLCTL/ATL::CBindStatusCallback::OnStartBinding
- ATLCTL/ATL::CBindStatusCallback::OnStopBinding
- ATLCTL/ATL::CBindStatusCallback::StartAsyncDownload
- ATLCTL/ATL::CBindStatusCallback::m_dwAvailableToRead
- ATLCTL/ATL::CBindStatusCallback::m_dwTotalRead
- ATLCTL/ATL::CBindStatusCallback::m_pFunc
- ATLCTL/ATL::CBindStatusCallback::m_pT
- ATLCTL/ATL::CBindStatusCallback::m_spBindCtx
- ATLCTL/ATL::CBindStatusCallback::m_spBinding
- ATLCTL/ATL::CBindStatusCallback::m_spMoniker
- ATLCTL/ATL::CBindStatusCallback::m_spStream
helpviewer_keywords:
- asynchronous data transfer [C++]
- data transfer [C++]
- data transfer [C++], asynchronous
- CBindStatusCallback class
ms.assetid: 0f5da276-6031-4418-b2a9-a4750ef29e77
ms.openlocfilehash: 0ae7f4fcdba18be84d99140e395b6f2ac3db792a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748209"
---
# <a name="cbindstatuscallback-class"></a>Třída CBindStatusCallback

Tato třída implementuje `IBindStatusCallback` rozhraní.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T,
    int nBindFlags = BINDF_ASYNCHRONOUS | BINDF_ASYNCSTORAGE | BINDF_GETNEWESTVERSION | BINDF_NOWRITECACHE>
class ATL_NO_VTABLE CBindStatusCallback : public CComObjectRootEx <T ::_ThreadModel::ThreadModelNoCS>,
    public IBindStatusCallbackImpl<T>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída obsahující funkci, která bude volána jako data přijata.

*nBindFlags*<br/>
Určuje příznaky vazby, které jsou vráceny [getbindinfo](#getbindinfo). Výchozí implementace nastaví vazbu tak, aby byla asynchronní, načte nejnovější verzi data/objektu a neuloží načtená data do mezipaměti disku.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CBindStatusCallback::CBindStatusCallback](#cbindstatuscallback)|Konstruktor|
|[CBindStatusCallback::~CBindStatusCallback](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CBindStatusCallback::Download](#download)|Statická metoda, která spustí `CBindStatusCallback` proces stahování, `StartAsyncDownload`vytvoří objekt a zavolá .|
|[CBindStatusCallback::GetBindInfo](#getbindinfo)|Volána asynchronní zástupný název požadovat informace o typu vazby, které mají být vytvořeny.|
|[CBindStatusCallback::GetPriority](#getpriority)|Volána asynchronní zástupný název získat prioritu operace vazby. Implementace ATL `E_NOTIMPL`vrátí .|
|[CBindStatusCallback::OnDataAvailable](#ondataavailable)|Volána k poskytování dat do aplikace, jakmile bude k dispozici. Přečte data a pak zavolá funkci, která jí byla předána, aby data používala.|
|[CBindStatusCallback::OnLowResource](#onlowresource)|Nazývá se, když jsou nízké zdroje. Implementace ATL vrátí S_OK.|
|[CBindStatusCallback::OnObjectAvailable](#onobjectavailable)|Volána asynchronní zástupný název předat ukazatel rozhraní objektu do aplikace. Implementace ATL vrátí S_OK.|
|[CBindStatusCallback::OnProgress](#onprogress)|Nazývá se k označení průběhu procesu stahování dat. Implementace ATL vrátí S_OK.|
|[CBindStatusCallback::OnStartBinding](#onstartbinding)|Volána při spuštění vazby.|
|[CBindStatusCallback::OnStopBinding](#onstopbinding)|Nazývá se při zastavení asynchronního přenosu dat.|
|[CBindStatusCallback::StartAsyncDownload](#startasyncdownload)|Inicializuje dostupné bajty a bajty se čtení na nulu, vytvoří objekt datového proudu push typu z adresy URL a zavolá `OnDataAvailable` pokaždé, když jsou k dispozici data.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CBindStatusCallback::m_dwAvailableToRead](#m_dwavailabletoread)|Počet bajtů, které jsou k dispozici ke čtení.|
|[CBindStatusCallback::m_dwTotalRead](#m_dwtotalread)|Celkový počet přečtených bajtů.|
|[CBindStatusCallback::m_pFunc](#m_pfunc)|Ukazatel na funkci volanou, když jsou k dispozici data.|
|[CBindStatusCallback::m_pT](#m_pt)|Ukazatel na objekt požadující asynchronní přenos dat.|
|[CBindStatusCallback::m_spBindCtx](#m_spbindctx)|Ukazatel na rozhraní [IBindCtx](/windows/win32/api/objidl/nn-objidl-ibindctx) pro aktuální operaci vazby.|
|[CBindStatusCallback::m_spBinding](#m_spbinding)|Ukazatel na `IBinding` rozhraní pro aktuální operaci vazby.|
|[CBindStatusCallback::m_spMoniker](#m_spmoniker)|Ukazatel na rozhraní [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker) pro adresu URL použít.|
|[CBindStatusCallback::m_spStream](#m_spstream)|Ukazatel na rozhraní [IStream](/windows/win32/api/objidl/nn-objidl-istream) pro přenos dat.|

## <a name="remarks"></a>Poznámky

Třída `CBindStatusCallback` implementuje rozhraní `IBindStatusCallback`. `IBindStatusCallback`musí být implementována vaší aplikací, aby mohla přijímat oznámení z asynchronního přenosu dat. Asynchronní zástupný název poskytovaný systémem používá `IBindStatusCallback` metody pro odesílání a přijímání informací o asynchronním přenosu dat do a z objektu.

`CBindStatusCallback` Objekt je obvykle spojen s konkrétní operace vazby. Například v [async](../../overview/visual-cpp-samples.md) vzorku při nastavení vlastnosturl, vytvoří `CBindStatusCallback` objekt ve `Download`volání :

[!code-cpp[NVC_ATL_Windowing#86](../../atl/codesnippet/cpp/cbindstatuscallback-class_1.h)]

Asynchronní zástupný název používá funkci `OnData` zpětného volání k volání aplikace, pokud má data. Asynchronní zástupný název je poskytován systémem.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CComObjectRootBase`

`IBindStatusCallback`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`CBindStatusCallback`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

## <a name="cbindstatuscallbackcbindstatuscallback"></a><a name="cbindstatuscallback"></a>CBindStatusCallback::CBindStatusCallback

Konstruktor

```
CBindStatusCallback();
```

### <a name="remarks"></a>Poznámky

Vytvoří objekt pro příjem oznámení týkajících se asynchronního přenosu dat. Obvykle jeden objekt je vytvořen pro každou operaci vazby.

Konstruktor také inicializuje [m_pT](#m_pt) a [m_pFunc](#m_pfunc) na hodnotu NULL.

## <a name="cbindstatuscallbackcbindstatuscallback"></a><a name="dtor"></a>CBindStatusCallback::~CBindStatusCallback

Destruktor.

```
~CBindStatusCallback();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené zdroje.

## <a name="cbindstatuscallbackdownload"></a><a name="download"></a>CBindStatusCallback::Download

Vytvoří `CBindStatusCallback` objekt a `StartAsyncDownload` volá a začít stahovat data asynchronně ze zadané adresy URL.

```
static HRESULT Download(
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```

### <a name="parameters"></a>Parametry

*Pt*<br/>
[v] Ukazatel na objekt požadující asynchronní přenos dat. Objekt `CBindStatusCallback` je templatized na třídu tohoto objektu.

*pFunc*<br/>
[v] Ukazatel na funkci, která přijímá data, která je přečtena. Funkce je členem třídy typu `T`objektu . Syntaxi a příklad najdete v [tématu StartAsyncDownload.](#startasyncdownload)

*bstrURL*<br/>
[v] Adresa URL pro získání dat. Může být libovolný platný název adresy URL nebo souboru. Nemůže být null. Příklad:

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnkContainer*<br/>
[v] Kontejneru. `IUnknown` Null ve výchozím nastavení.

*bRelativní*<br/>
[v] Příznak označující, zda je adresa URL relativní nebo absolutní. Ve výchozím nastavení nepravda, což znamená, že adresa URL je absolutní.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Pokaždé, když jsou data k dispozici, jsou odeslána do objektu prostřednictvím `OnDataAvailable`aplikace . `OnDataAvailable`čte data a volá funkci, na kterou *pFunc* ukazuje (například pro uložení dat nebo jejich tisk na obrazovku).

## <a name="cbindstatuscallbackgetbindinfo"></a><a name="getbindinfo"></a>CBindStatusCallback::GetBindInfo

Volána, aby řekla zástupné společnosti, jak se vázat.

```
STDMETHOD(GetBindInfo)(
    DWORD* pgrfBSCF,
    BINDINFO* pbindinfo);
```

### <a name="parameters"></a>Parametry

*pgrfBSCF*<br/>
[out] Ukazatel na hodnoty výčtu BINDF označující, jak by měla operace vazby probíhat. Ve výchozím nastavení nastavte následující hodnoty výčtu:

BINDF_ASYNCHRONOUS Asynchronní stahování.

BINDF_ASYNCSTORAGE `OnDataAvailable` vrátí E_PENDING, pokud data ještě nejsou k dispozici, nikoli blokování, dokud nejsou data k dispozici.

BINDF_GETNEWESTVERSION Operace vazby by měla načíst nejnovější verzi dat.

BINDF_NOWRITECACHE Operace vazby by neměla ukládat načtená data do mezipaměti disku.

*pbindinfo*<br/>
[dovnitř, ven] Ukazatel na `BINDINFO` strukturu poskytující další informace o tom, jak objekt chce vazbu dojít.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Výchozí implementace nastaví vazbu jako asynchronní a použít model datové hospo- V modelu nabízená data zástupný název řídí operaci asynchronní vazby a průběžně upozorní klienta vždy, když jsou k dispozici nová data.

## <a name="cbindstatuscallbackgetpriority"></a><a name="getpriority"></a>CBindStatusCallback::GetPriority

Volána asynchronní zástupný název získat prioritu operace vazby.

```
STDMETHOD(GetPriority)(LONG* pnPriority);
```

### <a name="parameters"></a>Parametry

*pnPriorita*<br/>
[out] Adresa **long** proměnné, která, na úspěch, obdrží prioritu.

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

## <a name="cbindstatuscallbackm_dwavailabletoread"></a><a name="m_dwavailabletoread"></a>CBindStatusCallback::m_dwAvailableToRead

Lze použít k uložení počtu bajtů, které jsou k dispozici ke čtení.

```
DWORD m_dwAvailableToRead;
```

### <a name="remarks"></a>Poznámky

Inicializováno `StartAsyncDownload`na nulu v .

## <a name="cbindstatuscallbackm_dwtotalread"></a><a name="m_dwtotalread"></a>CBindStatusCallback::m_dwTotalRead

Kumulativní součet bajtů přečtených v asynchronním přenosu dat.

```
DWORD m_dwTotalRead;
```

### <a name="remarks"></a>Poznámky

Zvýšení pokaždé, když `OnDataAvailable` je volána počet bajtů skutečně číst. Inicializováno `StartAsyncDownload`na nulu v .

## <a name="cbindstatuscallbackm_pfunc"></a><a name="m_pfunc"></a>CBindStatusCallback::m_pFunc

Funkce, na `m_pFunc` kterou se `OnDataAvailable` vztahuje funkce, na kterou se vztahuje, je volána po čtení dostupných dat (například k uložení dat nebo tisku na obrazovku).

```
ATL_PDATAAVAILABLE m_pFunc;
```

### <a name="remarks"></a>Poznámky

Funkce, na `m_pFunc` kterou se vztahuje od člena, je členem třídy objektu a má následující syntaxi:

```cpp
void Function_Name(
   CBindStatusCallback<T>* pbsc,
   BYTE* pBytes,
   DWORD dwSize
   );
```

## <a name="cbindstatuscallbackm_pt"></a><a name="m_pt"></a>CBindStatusCallback::m_pT

Ukazatel na objekt požadující asynchronní přenos dat.

```
T* m_pT;
```

### <a name="remarks"></a>Poznámky

Objekt `CBindStatusCallback` je templatized na třídu tohoto objektu.

## <a name="cbindstatuscallbackm_spbindctx"></a><a name="m_spbindctx"></a>CBindStatusCallback::m_spBindCtx

Ukazatel na rozhraní [IBindCtx,](/windows/win32/api/objidl/nn-objidl-ibindctx) který poskytuje přístup k kontextu vazby (objekt, který ukládá informace o operaci vazby konkrétní zástupný název).

```
CComPtr<IBindCtx> m_spBindCtx;
```

### <a name="remarks"></a>Poznámky

Inicializováno v . `StartAsyncDownload`

## <a name="cbindstatuscallbackm_spbinding"></a><a name="m_spbinding"></a>CBindStatusCallback::m_spBinding

Ukazatel na `IBinding` rozhraní aktuální operace vazby.

```
CComPtr<IBinding> m_spBinding;
```

### <a name="remarks"></a>Poznámky

Inicializováno `OnStartBinding` `OnStopBinding`a uvolněno v .

## <a name="cbindstatuscallbackm_spmoniker"></a><a name="m_spmoniker"></a>CBindStatusCallback::m_spMoniker

Ukazatel na rozhraní [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker) pro adresu URL, která má být používána.

```
CComPtr<IMoniker> m_spMoniker;
```

### <a name="remarks"></a>Poznámky

Inicializováno v . `StartAsyncDownload`

## <a name="cbindstatuscallbackm_spstream"></a><a name="m_spstream"></a>CBindStatusCallback::m_spStream

Ukazatel na rozhraní [IStream](/windows/win32/api/objidl/nn-objidl-istream) aktuální operace vazby.

```
CComPtr<IStream> m_spStream;
```

### <a name="remarks"></a>Poznámky

Inicializována ze `OnDataAvailable` `STGMEDIUM` struktury při BCSF_FIRSTDATANOTIFICATION příznaku BCSF a uvolněna při BCSF_LASTDATANOTIFICATION příznaku BCSF.

## <a name="cbindstatuscallbackondataavailable"></a><a name="ondataavailable"></a>CBindStatusCallback::OnDataAvailable

Systémem dodaný asynchronní zástupný název `OnDataAvailable` volá poskytnout data objektu, jakmile bude k dispozici.

```
STDMETHOD(
    OnDataAvailable)(DWORD grfBSCF,
    DWORD dwSize,
    FORMATETC* /* pformatetc */,
    STGMEDIUM* pstgmed);
```

### <a name="parameters"></a>Parametry

*grfBSCF*<br/>
[v] Hodnota výčtu BSCF. Jeden nebo více z následujících možností: BSCF_FIRSTDATANOTIFICATION, BSCF_INTERMEDIARYDATANOTIFICATION nebo BSCF_LASTDATANOTIFICATION.

*dwVelikost*<br/>
[v] Kumulativní množství (v bajtech) dat, které jsou k dispozici od začátku vazby. Může být nula, což znamená, že množství dat není relevantní nebo že nebyla k dispozici žádná konkrétní částka.

*pformatetc*<br/>
[v] Ukazatel na [formatetc](/windows/win32/com/the-formatetc-structure) strukturu, která obsahuje formát dostupných dat. Pokud neexistuje žádný formát, lze CF_NULL.

*pstgmed*<br/>
[v] Ukazatel na [stgmedium](/windows/win32/com/the-stgmedium-structure) strukturu, která obsahuje skutečná data nyní k dispozici.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

`OnDataAvailable`přečte data, pak volá metodu třídy objektu (například k uložení dat nebo vytisknout na obrazovku). Viz [CBindStatusCallback::StartAsyncDownload](#startasyncdownload) podrobnosti.

## <a name="cbindstatuscallbackonlowresource"></a><a name="onlowresource"></a>CBindStatusCallback::OnLowResource

Nazývá se, když jsou nízké zdroje.

```
STDMETHOD(OnLowResource)(DWORD /* dwReserved */);
```

### <a name="parameters"></a>Parametry

*dwVyhrazeno*<br/>
Vyhrazeno.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

## <a name="cbindstatuscallbackonobjectavailable"></a><a name="onobjectavailable"></a>CBindStatusCallback::OnObjectAvailable

Volána asynchronní zástupný název předat ukazatel rozhraní objektu do aplikace.

```
STDMETHOD(OnObjectAvailable)(REFID /* riid */, IUnknown* /* punk */);
```

### <a name="parameters"></a>Parametry

*riid řekl:*<br/>
Identifikátor rozhraní požadovaného rozhraní. Nepoužívá se.

*Punk*<br/>
Adresa rozhraní IUnknown. Nepoužívá se.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

## <a name="cbindstatuscallbackonprogress"></a><a name="onprogress"></a>CBindStatusCallback::OnProgress

Nazývá se k označení průběhu procesu stahování dat.

```
STDMETHOD(OnProgress)(
    ULONG /* ulProgress */,
    ULONG /* ulProgressMax */,
    ULONG /* ulStatusCode */,
    LPCWSTRONG /* szStatusText */);
```

### <a name="parameters"></a>Parametry

*ulProgress*<br/>
Nepodepsané dlouhé celé číslo. Nepoužívá se.

*ulProgressMax*<br/>
Nepodepsané dlouhé celé číslo Nepoužito.

*ulStatusCode*<br/>
Nepodepsané dlouhé celé číslo. Nepoužívá se.

*szStatusText*<br/>
Adresa řetězcové hodnoty. Nepoužívá se.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

## <a name="cbindstatuscallbackonstartbinding"></a><a name="onstartbinding"></a>CBindStatusCallback::OnStartBinding

Nastaví [m_spBinding](#m_spbinding) datového `IBinding` prvku na ukazatel v *pBinding*.

```
STDMETHOD(OnStartBinding)(DWORD /* dwReserved */, IBinding* pBinding);
```

### <a name="parameters"></a>Parametry

*dwVyhrazeno*<br/>
Vyhrazeno pro budoucí použití.

*pVazba*<br/>
[v] Adresa rozhraní IBinding aktuální operace vazby. To nemůže být NULL. Klient by měl volat AddRef na tento ukazatel zachovat odkaz na objekt vazby.

## <a name="cbindstatuscallbackonstopbinding"></a><a name="onstopbinding"></a>CBindStatusCallback::OnStopBinding

Uvolní `IBinding` ukazatel v [m_spBinding](#m_spbinding)datového člena .

```
STDMETHOD(OnStopBinding)(HRESULT hresult, LPCWSTR /* szError */);
```

### <a name="parameters"></a>Parametry

*Hresult*<br/>
Stavový kód vrácený z operace vazby.

*chyba szError*<br/>
Adresa řetězcové hodnoty. Nepoužívá se.

### <a name="remarks"></a>Poznámky

Volat systémem dodané asynchronní zástupný název k označení konce operace vazby.

## <a name="cbindstatuscallbackstartasyncdownload"></a><a name="startasyncdownload"></a>CBindStatusCallback::StartAsyncDownload

Spustí stahování dat asynchronně ze zadané adresy URL.

```
HRESULT StartAsyncDownload(
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```

### <a name="parameters"></a>Parametry

*Pt*<br/>
[v] Ukazatel na objekt požadující asynchronní přenos dat. Objekt `CBindStatusCallback` je templatized na třídu tohoto objektu.

*pFunc*<br/>
[v] Ukazatel na funkci, která přijímá data, která jsou čtena. Funkce je členem třídy typu `T`objektu . Syntaxe a příklad naleznete v **tématu Poznámky.**

*bstrURL*<br/>
[v] Adresa URL pro získání dat. Může být libovolný platný název adresy URL nebo souboru. Nemůže být null. Příklad:

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnkContainer*<br/>
[v] Kontejneru. `IUnknown` Null ve výchozím nastavení.

*bRelativní*<br/>
[v] Příznak označující, zda je adresa URL relativní nebo absolutní. Ve výchozím nastavení nepravda, což znamená, že adresa URL je absolutní.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Pokaždé, když jsou data k dispozici, jsou odeslána do objektu prostřednictvím `OnDataAvailable`aplikace . `OnDataAvailable`čte data a volá funkci, na kterou *pFunc* ukazuje (například pro uložení dat nebo jejich tisk na obrazovku).

Funkce, na kterou *pFunc* ukazuje, je členem třídy objektu a má následující syntaxi:

```cpp
void Function_Name(
    CBindStatusCallback<T>* pbsc,
    BYTE* pBytes,
    DWORD dwSize);
```

V následujícím příkladu (převzato z [ukázky ASYNC)](../../overview/visual-cpp-samples.md) funkce `OnData` zapíše přijatá data do textového pole.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#87](../../atl/codesnippet/cpp/cbindstatuscallback-class_2.h)]

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
