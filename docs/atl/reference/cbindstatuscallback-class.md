---
title: Cbindstatuscallback – třída
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
ms.openlocfilehash: 16e97b994ad30fdd4c255dac45e8b56fd04f663a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50583310"
---
# <a name="cbindstatuscallback-class"></a>Cbindstatuscallback – třída

Tato třída implementuje `IBindStatusCallback` rozhraní.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T,
    int nBindFlags = BINDF_ASYNCHRONOUS | BINDF_ASYNCSTORAGE | BINDF_GETNEWESTVERSION | BINDF_NOWRITECACHE>
class ATL_NO_VTABLE CBindStatusCallback : public CComObjectRootEx <T ::_ThreadModel::ThreadModelNoCS>,
    public IBindStatusCallbackImpl<T>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaši třídu obsahující funkci, která bude volána, jako jsou data přijata.

*nBindFlags*<br/>
Určuje příznaky vazby, které jsou vráceny pomocí [GetBindInfo](#getbindinfo). Výchozí implementace nastaví vazbu byla asynchronní, načte nejnovější verze datového objektu a neukládá načtená data v mezipaměti disku.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CBindStatusCallback::CBindStatusCallback](#cbindstatuscallback)|Konstruktor|
|[Cbindstatuscallback –:: ~ cbindstatuscallback –](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CBindStatusCallback::Download](#download)|Vytvoří statickou metodu, která se spustí proces stahování `CBindStatusCallback` objektu a volání `StartAsyncDownload`.|
|[CBindStatusCallback::GetBindInfo](#getbindinfo)|Volané asynchronní moniker na informace o žádostech na typ vazby, který se má vytvořit.|
|[CBindStatusCallback::GetPriority](#getpriority)|Volané asynchronní moniker zobrazíte prioritu operace připojení. Implementace knihovny ATL vrátí `E_NOTIMPL`.|
|[CBindStatusCallback::OnDataAvailable](#ondataavailable)|Volá se, aby poskytují data do vaší aplikace, protože je k dispozici. Čte data a pak volá funkci předán do ní použít data.|
|[CBindStatusCallback::OnLowResource](#onlowresource)|Volá se, když mají nedostatek prostředků. Implementace knihovny ATL vrátí hodnotu S_OK.|
|[CBindStatusCallback::OnObjectAvailable](#onobjectavailable)|Volané asynchronní moniker předat ukazatel rozhraní objektu do vaší aplikace. Implementace knihovny ATL vrátí hodnotu S_OK.|
|[CBindStatusCallback::OnProgress](#onprogress)|Volá se, aby se indikoval průběh procesu stahování dat. Implementace knihovny ATL vrátí hodnotu S_OK.|
|[CBindStatusCallback::OnStartBinding](#onstartbinding)|Volá se při spuštění vazby.|
|[CBindStatusCallback::OnStopBinding](#onstopbinding)|Volá se, když se zastaví přenos asynchronní data.|
|[CBindStatusCallback::StartAsyncDownload](#startasyncdownload)|Inicializuje bajty k dispozici a přečtené bajty na nulu, vytvoří objekt stisknutelného typu datový proud z adresy URL a volání `OnDataAvailable` pokaždé, když se data jsou k dispozici.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CBindStatusCallback::m_dwAvailableToRead](#m_dwavailabletoread)|Počet bajtů ke čtení k dispozici.|
|[CBindStatusCallback::m_dwTotalRead](#m_dwtotalread)|Celkový počet bajtů ke čtení.|
|[CBindStatusCallback::m_pFunc](#m_pfunc)|Ukazatel na funkci volá, když data jsou k dispozici.|
|[CBindStatusCallback::m_pT](#m_pt)|Ukazatel na objekt žádosti o přenos dat asynchronní.|
|[CBindStatusCallback::m_spBindCtx](#m_spbindctx)|Ukazatel [IBindCtx](/windows/desktop/api/objidl/nn-objidl-ibindctx) rozhraní pro aktuální operaci bind.|
|[CBindStatusCallback::m_spBinding](#m_spbinding)|Ukazatel `IBinding` rozhraní pro aktuální operaci bind.|
|[CBindStatusCallback::m_spMoniker](#m_spmoniker)|Ukazatel [imoniker –](/windows/desktop/api/objidl/nn-objidl-imoniker) rozhraní pro adresu URL k použití.|
|[CBindStatusCallback::m_spStream](#m_spstream)|Ukazatel [IStream](/windows/desktop/api/objidl/nn-objidl-istream) rozhraní pro přenos dat.|

## <a name="remarks"></a>Poznámky

`CBindStatusCallback` Implementuje třída `IBindStatusCallback` rozhraní. `IBindStatusCallback` musí být implementované v aplikaci, aby ho mohli dostávat oznámení od asynchronní datové přenosy. Používá asynchronní moniker poskytované systémem `IBindStatusCallback` metody odesílat a přijímat informace o datech asynchronní přenos do a z objektu.

Obvykle `CBindStatusCallback` objekt je přidružený operace konkrétní připojení. Například v [ASYNCHRONNÍ](../../visual-cpp-samples.md) ukázka, když nastavíte vlastnost adresa URL ho vytvoří `CBindStatusCallback` objektu ve volání `Download`:

[!code-cpp[NVC_ATL_Windowing#86](../../atl/codesnippet/cpp/cbindstatuscallback-class_1.h)]

Funkce zpětného volání používá asynchronní moniker `OnData` volat vaší aplikace, když má data. Asynchronní monikeru je poskytované systémem.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CComObjectRootBase`

`IBindStatusCallback`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`CBindStatusCallback`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

##  <a name="cbindstatuscallback"></a>  CBindStatusCallback::CBindStatusCallback

Konstruktor

```
CBindStatusCallback();
```

### <a name="remarks"></a>Poznámky

Vytvoří objekt pro příjem oznámení týkající se přenosu dat asynchronní. Jeden objekt se obvykle vytvoří pro každou operaci bind.

Konstruktor také inicializuje [m_pT](#m_pt) a [m_pFunc](#m_pfunc) na hodnotu NULL.

##  <a name="dtor"></a>  Cbindstatuscallback –:: ~ cbindstatuscallback –

Destruktor.

```
~CBindStatusCallback();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky.

##  <a name="download"></a>  CBindStatusCallback::Download

Vytvoří `CBindStatusCallback` objektu a volání `StartAsyncDownload` spustit stahovat data asynchronně ze zadané adresy URL.

```
static HRESULT Download(
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```

### <a name="parameters"></a>Parametry

*PT*<br/>
[in] Ukazatel na objekt žádosti o přenos dat asynchronní. `CBindStatusCallback` Objektu je založena na tento objekt třídy.

*pFunc*<br/>
[in] Ukazatel na funkci, která bude přijímat data, která je pro čtení. Funkce je členem třídy objektu typu `T`. Zobrazit [StartAsyncDownload](#startasyncdownload) pro syntaxe a příkladu.

*bstrURL*<br/>
[in] Adresa URL k získání dat z. Může být libovolný platný název adresy URL nebo souboru. Nemůže mít hodnotu NULL. Příklad:

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnkContainer*<br/>
[in] `IUnknown` Kontejneru. Ve výchozím nastavení s hodnotou NULL.

*bRelative*<br/>
[in] Příznak označující, zda je relativní nebo absolutní adresu URL. FALSE ve výchozím nastavení, což znamená, adresa URL je absolutní.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Pokaždé, když jsou k dispozici data jsou odeslána do objektu prostřednictvím `OnDataAvailable`. `OnDataAvailable` čte data a volá funkci, na které odkazuje *pFunc* (například data uložit nebo vytisknout na obrazovce).

##  <a name="getbindinfo"></a>  CBindStatusCallback::GetBindInfo

Volá se, aby monikeru zjistit, jak vytvořit vazbu.

```
STDMETHOD(GetBindInfo)(
    DWORD* pgrfBSCF,
    BINDINFO* pbindinfo);
```

### <a name="parameters"></a>Parametry

*pgrfBSCF*<br/>
[out] Ukazatel na BINDF hodnot výčtu označující, jak by měl nastat operace připojení. Ve výchozím nastavení s použitím následujících hodnot výčtu:

BINDF_ASYNCHRONOUS asynchronní stahování.

BINDF_ASYNCSTORAGE `OnDataAvailable` vrátí E_PENDING, pokud data ještě nejsou k dispozici místo zablokovaná, dokud se data jsou k dispozici.

BINDF_GETNEWESTVERSION operace připojení, načtěte nejnovější verze data.

BINDF_NOWRITECACHE, které by neměly ukládat operaci bind načíst data v mezipaměti disku.

*pbindinfo*<br/>
[out v] Ukazatel `BINDINFO` struktury poskytuje další informace o jak chce, aby objekt vázání.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Výchozí implementace nastaví vazbu byla asynchronní a k použití modelu datová oznámení. V modelu datová oznámení zástupný název jednotky operace asynchronního připojení a průběžně upozorní klienta pokaždé, když jsou k dispozici nová data.

##  <a name="getpriority"></a>  CBindStatusCallback::GetPriority

Volané asynchronní moniker zobrazíte prioritu operace připojení.

```
STDMETHOD(GetPriority)(LONG* pnPriority);
```

### <a name="parameters"></a>Parametry

*pnPriority*<br/>
[out] Adresa **dlouhé** proměnné, která v případě úspěchu, obdrží prioritu.

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

##  <a name="m_dwavailabletoread"></a>  CBindStatusCallback::m_dwAvailableToRead

Slouží k ukládání počet bajtů ke čtení k dispozici.

```
DWORD m_dwAvailableToRead;
```

### <a name="remarks"></a>Poznámky

Inicializována na hodnotu nula `StartAsyncDownload`.

##  <a name="m_dwtotalread"></a>  CBindStatusCallback::m_dwTotalRead

Přenos dat asynchronní čtení kumulativní součet bajtů.

```
DWORD m_dwTotalRead;
```

### <a name="remarks"></a>Poznámky

Zvýší pokaždé, když `OnDataAvailable` je volán počet skutečně přečtených bajtů. Inicializována na hodnotu nula `StartAsyncDownload`.

##  <a name="m_pfunc"></a>  CBindStatusCallback::m_pFunc

Funkce odkazované `m_pFunc` je volán `OnDataAvailable` po přečte dostupná data (například data uložit nebo vytisknout na obrazovce).

```
ATL_PDATAAVAILABLE m_pFunc;
```

### <a name="remarks"></a>Poznámky

Funkce odkazované `m_pFunc` je členem třídy objektu a má následující syntaxi:

```
void Function_Name(
   CBindStatusCallback<T>* pbsc,
   BYTE* pBytes,
   DWORD dwSize
   );
```

##  <a name="m_pt"></a>  CBindStatusCallback::m_pT

Ukazatel na objekt žádosti o přenos dat asynchronní.

```
T* m_pT;
```

### <a name="remarks"></a>Poznámky

`CBindStatusCallback` Objektu je založena na tento objekt třídy.

##  <a name="m_spbindctx"></a>  CBindStatusCallback::m_spBindCtx

Ukazatel [IBindCtx](/windows/desktop/api/objidl/nn-objidl-ibindctx) rozhraní, které poskytuje přístup ke kontextu vazby (objekt, který obsahuje informace o operaci vazby konkrétní moniker).

```
CComPtr<IBindCtx> m_spBindCtx;
```

### <a name="remarks"></a>Poznámky

Inicializováno v `StartAsyncDownload`.

##  <a name="m_spbinding"></a>  CBindStatusCallback::m_spBinding

Ukazatel `IBinding` rozhraní aktuální operace připojení.

```
CComPtr<IBinding> m_spBinding;
```

### <a name="remarks"></a>Poznámky

Inicializováno v `OnStartBinding` a vydanou v `OnStopBinding`.

##  <a name="m_spmoniker"></a>  CBindStatusCallback::m_spMoniker

Ukazatel [imoniker –](/windows/desktop/api/objidl/nn-objidl-imoniker) rozhraní pro adresu URL k použití.

```
CComPtr<IMoniker> m_spMoniker;
```

### <a name="remarks"></a>Poznámky

Inicializováno v `StartAsyncDownload`.

##  <a name="m_spstream"></a>  CBindStatusCallback::m_spStream

Ukazatel [IStream](/windows/desktop/api/objidl/nn-objidl-istream) rozhraní aktuální operace připojení.

```
CComPtr<IStream> m_spStream;
```

### <a name="remarks"></a>Poznámky

Inicializováno v `OnDataAvailable` z `STGMEDIUM` struktury, když příznak BCSF BCSF_FIRSTDATANOTIFICATION a když je příznak BCSF BCSF_LASTDATANOTIFICATION uvolní.

##  <a name="ondataavailable"></a>  CBindStatusCallback::OnDataAvailable

Volání asynchronní moniker poskytnuté systémem `OnDataAvailable` poskytující data do objektu, protože je k dispozici.

```
STDMETHOD(
    OnDataAvailable)(DWORD grfBSCF,
    DWORD dwSize,
    FORMATETC* /* pformatetc */,
    STGMEDIUM* pstgmed);
```

### <a name="parameters"></a>Parametry

*grfBSCF*<br/>
[in] Hodnota výčtu BSCF. Jeden nebo více z následujících akcí: BSCF_FIRSTDATANOTIFICATION, BSCF_INTERMEDIARYDATANOTIFICATION nebo BSCF_LASTDATANOTIFICATION.

*dwSize*<br/>
[in] Souhrnně za (v bajtech) k dispozici od začátku vazby data. Může být nula, která znamená, že objem dat se nevztahuje nebo, že bez ohledu na konkrétní začal být k dispozici.

*pformatetc*<br/>
[in] Ukazatel [FORMATETC](/windows/desktop/com/the-formatetc-structure) strukturu, která obsahuje formát dat k dispozici. Pokud neexistuje žádný format, může být CF_NULL.

*pstgmed*<br/>
[in] Ukazatel [STGMEDIUM](/windows/desktop/com/the-stgmedium-structure) struktura, která uchovává skutečná data, která je teď k dispozici.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

`OnDataAvailable` čte data a potom volá metodu třídu objektu (například data uložit nebo vytisknout na obrazovce). Zobrazit [CBindStatusCallback::StartAsyncDownload](#startasyncdownload) podrobnosti.

##  <a name="onlowresource"></a>  CBindStatusCallback::OnLowResource

Volá se, když mají nedostatek prostředků.

```
STDMETHOD(OnLowResource)(DWORD /* dwReserved */);
```

### <a name="parameters"></a>Parametry

*dwReserved*<br/>
Vyhrazená.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK.

##  <a name="onobjectavailable"></a>  CBindStatusCallback::OnObjectAvailable

Volané asynchronní moniker předat ukazatel rozhraní objektu do vaší aplikace.

```
STDMETHOD(OnObjectAvailable)(REFID /* riid */, IUnknown* /* punk */);
```

### <a name="parameters"></a>Parametry

*riid*<br/>
Identifikátor rozhraní požadované rozhraní. Nevyužité.

*punk*<br/>
Adresa rozhraní IUnknown. Nevyužité.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK.

##  <a name="onprogress"></a>  CBindStatusCallback::OnProgress

Volá se, aby se indikoval průběh procesu stahování dat.

```
STDMETHOD(OnProgress)(
    ULONG /* ulProgress */,
    ULONG /* ulProgressMax */,
    ULONG /* ulStatusCode */,
    LPCWSTRONG /* szStatusText */);
```

### <a name="parameters"></a>Parametry

*ulProgress*<br/>
Dlouhé celé číslo bez znaménka. Nevyužité.

*ulProgressMax*<br/>
Dlouhé celé číslo bez znaménka nepoužitý.

*ulStatusCode*<br/>
Dlouhé celé číslo bez znaménka. Nevyužité.

*szStatusText*<br/>
Adresa řetězcovou hodnotu. Nevyužité.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK.

##  <a name="onstartbinding"></a>  CBindStatusCallback::OnStartBinding

Nastaví datový člen [m_spBinding](#m_spbinding) k `IBinding` ukazatel v *pBinding*.

```
STDMETHOD(OnStartBinding)(DWORD /* dwReserved */, IBinding* pBinding);
```

### <a name="parameters"></a>Parametry

*dwReserved*<br/>
Vyhrazeno pro budoucí použití.

*pBinding*<br/>
[in] Adresa rozhraní IBinding aktuální vazby operace. To nemůže být NULL. Klient by měl zavolá funkci AddRef pro tento ukazatel zachovávat odkaz na objekt binding.

##  <a name="onstopbinding"></a>  CBindStatusCallback::OnStopBinding

Verze `IBinding` ukazatel v datovém členovi [m_spBinding](#m_spbinding).

```
STDMETHOD(OnStopBinding)(HRESULT hresult, LPCWSTR /* szError */);
```

### <a name="parameters"></a>Parametry

*Hodnota HRESULT*<br/>
Stavový kód vrácený ze operace připojení.

*szError*<br/>
Adresa řetězcovou hodnotu. Nevyužité.

### <a name="remarks"></a>Poznámky

Je voláno poskytnuté systémem asynchronní moniker označuje konec operace připojení.

##  <a name="startasyncdownload"></a>  CBindStatusCallback::StartAsyncDownload

Začne stahovat data asynchronně ze zadané adresy URL.

```
HRESULT StartAsyncDownload(
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```

### <a name="parameters"></a>Parametry

*PT*<br/>
[in] Ukazatel na objekt žádosti o přenos dat asynchronní. `CBindStatusCallback` Objektu je založena na tento objekt třídy.

*pFunc*<br/>
[in] Ukazatel na funkci, která přijímá data, který je čten. Funkce je členem třídy objektu typu `T`. Zobrazit **poznámky** pro syntaxe a příkladu.

*bstrURL*<br/>
[in] Adresa URL k získání dat z. Může být libovolný platný název adresy URL nebo souboru. Nemůže mít hodnotu NULL. Příklad:

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnkContainer*<br/>
[in] `IUnknown` Kontejneru. Ve výchozím nastavení s hodnotou NULL.

*bRelative*<br/>
[in] Příznak označující, zda je relativní nebo absolutní adresu URL. FALSE ve výchozím nastavení, což znamená, adresa URL je absolutní.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Pokaždé, když jsou k dispozici data jsou odeslána do objektu prostřednictvím `OnDataAvailable`. `OnDataAvailable` čte data a volá funkci, na které odkazuje *pFunc* (například data uložit nebo vytisknout na obrazovce).

Funkce odkazované *pFunc* je členem třídy objektu a má následující syntaxi:

```
void Function_Name(
    CBindStatusCallback<T>* pbsc,
    BYTE* pBytes,
    DWORD dwSize);
```

V následujícím příkladu (z [ASYNCHRONNÍ](../../visual-cpp-samples.md) ukázkové), funkce `OnData` zapíše přijatá data do textového pole.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#87](../../atl/codesnippet/cpp/cbindstatuscallback-class_2.h)]

## <a name="see-also"></a>Viz také

[Přehled tříd](../../atl/atl-class-overview.md)
