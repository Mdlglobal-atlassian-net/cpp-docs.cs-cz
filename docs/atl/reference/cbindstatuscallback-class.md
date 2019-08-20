---
title: CBindStatusCallback – třída
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
ms.openlocfilehash: 89c65ff034cf7471c379b28116a741b62269a00c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497606"
---
# <a name="cbindstatuscallback-class"></a>CBindStatusCallback – třída

Tato třída implementuje `IBindStatusCallback` rozhraní.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T,
    int nBindFlags = BINDF_ASYNCHRONOUS | BINDF_ASYNCSTORAGE | BINDF_GETNEWESTVERSION | BINDF_NOWRITECACHE>
class ATL_NO_VTABLE CBindStatusCallback : public CComObjectRootEx <T ::_ThreadModel::ThreadModelNoCS>,
    public IBindStatusCallbackImpl<T>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída obsahující funkci, která bude volána jako data jsou přijata.

*nBindFlags*<br/>
Určuje příznaky vazeb, které jsou vraceny pomocí [GetBindInfo](#getbindinfo). Výchozí implementace nastaví, aby vazba byla asynchronní, získá nejnovější verzi dat nebo objektu a neuloží načtená data do diskové mezipaměti.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CBindStatusCallback::CBindStatusCallback](#cbindstatuscallback)|Konstruktor|
|[CBindStatusCallback:: ~ CBindStatusCallback](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CBindStatusCallback::D stáhn](#download)|Statická metoda, která spustí proces stahování, vytvoří `CBindStatusCallback` objekt a volání. `StartAsyncDownload`|
|[CBindStatusCallback:: GetBindInfo.](#getbindinfo)|Volá se asynchronním monikerem pro vyžádání informací o typu vazby, která se má vytvořit.|
|[CBindStatusCallback:: GetPriority](#getpriority)|Volá se asynchronním monikerem, aby se získala priorita operace vazby. Implementace knihovny ATL vrátí `E_NOTIMPL`.|
|[CBindStatusCallback::OnDataAvailable](#ondataavailable)|Volá se, aby se do vaší aplikace poskytovala data, jakmile bude k dispozici. Přečte data a pak zavolá předanou funkci, aby mohla data používat.|
|[CBindStatusCallback::OnLowResource](#onlowresource)|Volá se, když jsou prostředky nízké. Implementace ATL vrací S_OK.|
|[CBindStatusCallback::OnObjectAvailable](#onobjectavailable)|Volá se asynchronním monikerem, aby se předal ukazatel rozhraní objektu pro vaši aplikaci. Implementace ATL vrací S_OK.|
|[CBindStatusCallback:: Progress](#onprogress)|Volá se, aby se označoval průběh procesu stahování dat. Implementace ATL vrací S_OK.|
|[CBindStatusCallback::OnStartBinding](#onstartbinding)|Volá se při spuštění vazby.|
|[CBindStatusCallback::OnStopBinding](#onstopbinding)|Volá se, když se zastaví asynchronní přenos dat.|
|[CBindStatusCallback::StartAsyncDownload](#startasyncdownload)|Inicializuje dostupné bajty a přečtené bajty na nulu, vytvoří objekt datového proudu typu push z adresy URL a zavolá `OnDataAvailable` všechna data, která jsou k dispozici.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CBindStatusCallback::m_dwAvailableToRead](#m_dwavailabletoread)|Počet bajtů, které jsou k dispozici pro čtení.|
|[CBindStatusCallback::m_dwTotalRead](#m_dwtotalread)|Celkový počet přečtených bajtů|
|[CBindStatusCallback::m_pFunc](#m_pfunc)|Ukazatel na funkci volanou, když jsou data k dispozici.|
|[CBindStatusCallback::m_pT](#m_pt)|Ukazatel na objekt požadující přenos asynchronních dat.|
|[CBindStatusCallback::m_spBindCtx](#m_spbindctx)|Ukazatel na rozhraní [IBindCtx](/windows/win32/api/objidl/nn-objidl-ibindctx) pro aktuální operaci vazby.|
|[CBindStatusCallback::m_spBinding](#m_spbinding)|Ukazatel na `IBinding` rozhraní pro aktuální operaci vazby.|
|[CBindStatusCallback::m_spMoniker](#m_spmoniker)|Ukazatel na rozhraní [IMoniker –](/windows/win32/api/objidl/nn-objidl-imoniker) adresy URL, která se má použít.|
|[CBindStatusCallback::m_spStream](#m_spstream)|Ukazatel na rozhraní [IStream](/windows/win32/api/objidl/nn-objidl-istream) pro přenos dat.|

## <a name="remarks"></a>Poznámky

`CBindStatusCallback` Třída`IBindStatusCallback` implementuje rozhraní. `IBindStatusCallback`musí být implementováno vaší aplikací, aby mohl přijímat oznámení z asynchronního přenosu dat. Asynchronní moniker poskytnutý systémem používá `IBindStatusCallback` metody k posílání a přijímání informací o asynchronním přenosu dat do a z vašeho objektu.

`CBindStatusCallback` Objekt je obvykle přidružen k určité operaci vazby. Například v [asynchronní](../../overview/visual-cpp-samples.md) ukázce při nastavování vlastnosti URL vytvoří `CBindStatusCallback` objekt `Download`v volání:

[!code-cpp[NVC_ATL_Windowing#86](../../atl/codesnippet/cpp/cbindstatuscallback-class_1.h)]

Asynchronní moniker používá funkci `OnData` zpětného volání pro volání aplikace, když má data. Asynchronní moniker je poskytován systémem.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CComObjectRootBase`

`IBindStatusCallback`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`CBindStatusCallback`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl. h

##  <a name="cbindstatuscallback"></a>CBindStatusCallback::CBindStatusCallback

Konstruktor

```
CBindStatusCallback();
```

### <a name="remarks"></a>Poznámky

Vytvoří objekt pro příjem oznámení o asynchronním přenosu dat. Pro každou operaci vazby je obvykle vytvořen jeden objekt.

Konstruktor také inicializuje [m_pT](#m_pt) a [m_pFunc](#m_pfunc) na hodnotu null.

##  <a name="dtor"></a>CBindStatusCallback:: ~ CBindStatusCallback

Destruktor.

```
~CBindStatusCallback();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky.

##  <a name="download"></a>CBindStatusCallback::D stáhn

Vytvoří objekt a volání `StartAsyncDownload` , která spustí asynchronní stahování dat ze zadané adresy URL. `CBindStatusCallback`

```
static HRESULT Download(
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```

### <a name="parameters"></a>Parametry

*pT*<br/>
pro Ukazatel na objekt požadující přenos asynchronních dat. `CBindStatusCallback` Objekt je založena na třídě tohoto objektu.

*pFunc*<br/>
pro Ukazatel na funkci, která přijímá data, která jsou čtena. Funkce je členem třídy typu `T`objektu. Syntaxe a příklad najdete v tématu [StartAsyncDownload](#startasyncdownload) .

*bstrURL*<br/>
pro Adresa URL, ze které se mají získat data Může to být libovolná platná adresa URL nebo název souboru. Nemůže mít hodnotu NULL. Příklad:

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnkContainer*<br/>
pro `IUnknown` Kontejneru. Ve výchozím nastavení je NULL.

*bRelative*<br/>
pro Příznak označující, zda je adresa URL relativní nebo absolutní. Hodnota FALSE ve výchozím nastavení, což znamená, že adresa URL je absolutní.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Pokaždé, když jsou data k dispozici, se do `OnDataAvailable`objektu odesílají prostřednictvím. `OnDataAvailable`přečte data a zavolá funkci, na kterou odkazuje *pFunc* (například pro uložení dat nebo jejich tisk na obrazovku).

##  <a name="getbindinfo"></a>CBindStatusCallback:: GetBindInfo.

Volá se, aby se oznámilo, jak se má moniker vytvořit.

```
STDMETHOD(GetBindInfo)(
    DWORD* pgrfBSCF,
    BINDINFO* pbindinfo);
```

### <a name="parameters"></a>Parametry

*pgrfBSCF*<br/>
mimo Ukazatel na hodnoty výčtu BINDF, který označuje, jak by měla probíhat operace vazby. Ve výchozím nastavení se nastaví s následujícími hodnotami výčtu:

BINDF_ASYNCHRONOUS asynchronní stahování.

BINDF_ASYNCSTORAGE `OnDataAvailable` vrátí E_PENDING, pokud data ještě nejsou k dispozici, ale neblokuje dokud nejsou k dispozici data.

BINDF_GETNEWESTVERSION operace vazby by měla načíst nejnovější verzi dat.

BINDF_NOWRITECACHE operace vazby by neměla ukládat načtená data do diskové mezipaměti.

*pbindinfo*<br/>
[in, out] Ukazatel na strukturu, `BINDINFO` která poskytuje další informace o tom, jak objekt chce vytvořit vazbu.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Výchozí implementace nastaví, aby vazba byla asynchronní a aby používala model nabízených dat. V modelu vkládání dat zastupuje moniker v rámci operace asynchronní vazby a nepřetržitě upozorní klienta, kdykoli jsou k dispozici nová data.

##  <a name="getpriority"></a>CBindStatusCallback:: GetPriority

Volá se asynchronním monikerem, aby se získala priorita operace vazby.

```
STDMETHOD(GetPriority)(LONG* pnPriority);
```

### <a name="parameters"></a>Parametry

*pnPriority*<br/>
mimo Adresa **dlouhé** proměnné, která po úspěchu získá prioritu.

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

##  <a name="m_dwavailabletoread"></a>CBindStatusCallback::m_dwAvailableToRead

Dá se použít k uložení počtu bajtů, které se mají přečíst.

```
DWORD m_dwAvailableToRead;
```

### <a name="remarks"></a>Poznámky

Inicializováno na nulu `StartAsyncDownload`v.

##  <a name="m_dwtotalread"></a>CBindStatusCallback::m_dwTotalRead

Kumulativní součet přečtených bajtů v asynchronním přenosu dat.

```
DWORD m_dwTotalRead;
```

### <a name="remarks"></a>Poznámky

Přírůstkové pokaždé `OnDataAvailable` je voláno počtem bajtů, které jsou ve skutečnosti čteny. Inicializováno na nulu `StartAsyncDownload`v.

##  <a name="m_pfunc"></a>  CBindStatusCallback::m_pFunc

Funkce, na kterou se odkazuje `m_pFunc` pomocí, je `OnDataAvailable` volána po načtení dostupných dat (například pro uložení dat nebo při tisku na obrazovku).

```
ATL_PDATAAVAILABLE m_pFunc;
```

### <a name="remarks"></a>Poznámky

Funkce, na kterou `m_pFunc` ukazuje, je členem třídy objektu a má následující syntaxi:

```
void Function_Name(
   CBindStatusCallback<T>* pbsc,
   BYTE* pBytes,
   DWORD dwSize
   );
```

##  <a name="m_pt"></a>CBindStatusCallback::m_pT

Ukazatel na objekt požadující přenos asynchronních dat.

```
T* m_pT;
```

### <a name="remarks"></a>Poznámky

`CBindStatusCallback` Objekt je založena na třídě tohoto objektu.

##  <a name="m_spbindctx"></a>CBindStatusCallback::m_spBindCtx

Ukazatel na rozhraní [IBindCtx](/windows/win32/api/objidl/nn-objidl-ibindctx) , které poskytuje přístup k kontextu vazby (objekt, který ukládá informace o konkrétní operaci vazby monikeru).

```
CComPtr<IBindCtx> m_spBindCtx;
```

### <a name="remarks"></a>Poznámky

Inicializováno `StartAsyncDownload`v.

##  <a name="m_spbinding"></a>CBindStatusCallback::m_spBinding

Ukazatel na `IBinding` rozhraní aktuální operace vazby.

```
CComPtr<IBinding> m_spBinding;
```

### <a name="remarks"></a>Poznámky

Inicializováno `OnStartBinding` v a vydány v `OnStopBinding`.

##  <a name="m_spmoniker"></a>CBindStatusCallback::m_spMoniker

Ukazatel na rozhraní [IMoniker –](/windows/win32/api/objidl/nn-objidl-imoniker) adresy URL, která se má použít.

```
CComPtr<IMoniker> m_spMoniker;
```

### <a name="remarks"></a>Poznámky

Inicializováno `StartAsyncDownload`v.

##  <a name="m_spstream"></a>CBindStatusCallback::m_spStream

Ukazatel na rozhraní [IStream](/windows/win32/api/objidl/nn-objidl-istream) aktuální operace vazby.

```
CComPtr<IStream> m_spStream;
```

### <a name="remarks"></a>Poznámky

Inicializováno `OnDataAvailable` ve `STGMEDIUM` struktuře, když je příznak BCSF BCSF_FIRSTDATANOTIFICATION a uvolněn, když je příznak BCSF BCSF_LASTDATANOTIFICATION.

##  <a name="ondataavailable"></a>CBindStatusCallback::OnDataAvailable

Asynchronní moniker zadaný systémem zavolá `OnDataAvailable` k poskytnutí dat objektu, jakmile bude k dispozici.

```
STDMETHOD(
    OnDataAvailable)(DWORD grfBSCF,
    DWORD dwSize,
    FORMATETC* /* pformatetc */,
    STGMEDIUM* pstgmed);
```

### <a name="parameters"></a>Parametry

*grfBSCF*<br/>
pro Hodnota výčtu BSCF. Jednu nebo více z následujících možností: BSCF_FIRSTDATANOTIFICATION, BSCF_INTERMEDIARYDATANOTIFICATION nebo BSCF_LASTDATANOTIFICATION.

*nenulového dwSize funkci*<br/>
pro Kumulativní množství dat (v bajtech), která jsou k dispozici od začátku vazby. Může být nula, což znamená, že množství dat není relevantní nebo že žádná konkrétní částka nebyla k dispozici.

*pformatetc*<br/>
pro Ukazatel na strukturu [FORMATETC](/windows/win32/com/the-formatetc-structure) , která obsahuje formát dat, která jsou k dispozici. Pokud není žádný formát, může být CF_NULL.

*pstgmed*<br/>
pro Ukazatel na strukturu [STGMEDIUM](/windows/win32/com/the-stgmedium-structure) , která obsahuje skutečná data, která jsou nyní k dispozici.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

`OnDataAvailable`přečte data a pak zavolá metodu třídy vašeho objektu (například pro uložení dat nebo tisku na obrazovku). Podrobnosti najdete v tématu [CBindStatusCallback:: StartAsyncDownload](#startasyncdownload) .

##  <a name="onlowresource"></a>CBindStatusCallback::OnLowResource

Volá se, když jsou prostředky nízké.

```
STDMETHOD(OnLowResource)(DWORD /* dwReserved */);
```

### <a name="parameters"></a>Parametry

*dwReserved*<br/>
Rezervovaný.

### <a name="return-value"></a>Návratová hodnota

Vrací hodnotu S_OK.

##  <a name="onobjectavailable"></a>CBindStatusCallback::OnObjectAvailable

Volá se asynchronním monikerem, aby se předal ukazatel rozhraní objektu pro vaši aplikaci.

```
STDMETHOD(OnObjectAvailable)(REFID /* riid */, IUnknown* /* punk */);
```

### <a name="parameters"></a>Parametry

*riid*<br/>
Identifikátor rozhraní požadovaného rozhraní Nepoužívané.

*punk*<br/>
Adresa rozhraní IUnknown. Nepoužívané.

### <a name="return-value"></a>Návratová hodnota

Vrací hodnotu S_OK.

##  <a name="onprogress"></a>CBindStatusCallback:: Progress

Volá se, aby se označoval průběh procesu stahování dat.

```
STDMETHOD(OnProgress)(
    ULONG /* ulProgress */,
    ULONG /* ulProgressMax */,
    ULONG /* ulStatusCode */,
    LPCWSTRONG /* szStatusText */);
```

### <a name="parameters"></a>Parametry

*ulProgress*<br/>
Dlouhé celé číslo bez znaménka. Nepoužívané.

*ulProgressMax*<br/>
Dlouhé celé číslo bez znaménka.

*ulStatusCode*<br/>
Dlouhé celé číslo bez znaménka. Nepoužívané.

*szStatusText*<br/>
Adresa řetězcové hodnoty. Nepoužívané.

### <a name="return-value"></a>Návratová hodnota

Vrací hodnotu S_OK.

##  <a name="onstartbinding"></a>CBindStatusCallback::OnStartBinding

Nastaví datový člen [m_spBinding](#m_spbinding) na `IBinding` ukazatel v *pBinding*.

```
STDMETHOD(OnStartBinding)(DWORD /* dwReserved */, IBinding* pBinding);
```

### <a name="parameters"></a>Parametry

*dwReserved*<br/>
Vyhrazeno pro budoucí použití.

*pBinding*<br/>
pro Adresa rozhraní IBinding aktuální operace vazby Tato hodnota nemůže být NULL. Klient by měl zavolat AddRef na tento ukazatel, aby zachoval odkaz na objekt vazby.

##  <a name="onstopbinding"></a>CBindStatusCallback::OnStopBinding

Uvolní ukazatel v datovém členu [m_spBinding.](#m_spbinding) `IBinding`

```
STDMETHOD(OnStopBinding)(HRESULT hresult, LPCWSTR /* szError */);
```

### <a name="parameters"></a>Parametry

*HRESULT*<br/>
Stavový kód vrácený z operace BIND.

*szError*<br/>
Adresa řetězcové hodnoty. Nepoužívané.

### <a name="remarks"></a>Poznámky

Volá se asynchronním monikerem zadaným systémem k označení konce operace vazby.

##  <a name="startasyncdownload"></a>CBindStatusCallback::StartAsyncDownload

Spustí asynchronní stahování dat ze zadané adresy URL.

```
HRESULT StartAsyncDownload(
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```

### <a name="parameters"></a>Parametry

*pT*<br/>
pro Ukazatel na objekt požadující přenos asynchronních dat. `CBindStatusCallback` Objekt je založena na třídě tohoto objektu.

*pFunc*<br/>
pro Ukazatel na funkci, která přijímá čtená data. Funkce je členem třídy typu `T`objektu. Syntaxe a příklad najdete v části **poznámky** .

*bstrURL*<br/>
pro Adresa URL, ze které se mají získat data Může to být libovolná platná adresa URL nebo název souboru. Nemůže mít hodnotu NULL. Příklad:

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnkContainer*<br/>
pro `IUnknown` Kontejneru. Ve výchozím nastavení je NULL.

*bRelative*<br/>
pro Příznak označující, zda je adresa URL relativní nebo absolutní. Hodnota FALSE ve výchozím nastavení, což znamená, že adresa URL je absolutní.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Pokaždé, když jsou data k dispozici, se do `OnDataAvailable`objektu odesílají prostřednictvím. `OnDataAvailable`přečte data a zavolá funkci, na kterou odkazuje *pFunc* (například pro uložení dat nebo jejich tisk na obrazovku).

Funkce, na kterou odkazuje *pFunc* , je členem třídy objektu a má následující syntaxi:

```
void Function_Name(
    CBindStatusCallback<T>* pbsc,
    BYTE* pBytes,
    DWORD dwSize);
```

V následujícím příkladu (pořízených z [asynchronní](../../overview/visual-cpp-samples.md) ukázky) funkce `OnData` zapisuje přijatá data do textového pole.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#87](../../atl/codesnippet/cpp/cbindstatuscallback-class_2.h)]

## <a name="see-also"></a>Viz také:

[Přehled třídy](../../atl/atl-class-overview.md)
