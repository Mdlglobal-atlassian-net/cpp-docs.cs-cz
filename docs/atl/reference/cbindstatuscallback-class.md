---
title: "Třída CBindStatusCallback | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
helpviewer_keywords:
- asynchronous data transfer [C++]
- data transfer [C++]
- data transfer [C++], asynchronous
- CBindStatusCallback class
ms.assetid: 0f5da276-6031-4418-b2a9-a4750ef29e77
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 90546e2eb63c2b5dd9eb16a0ececfee2629562cf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cbindstatuscallback-class"></a>CBindStatusCallback – třída
Tato třída implementuje `IBindStatusCallback` rozhraní.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T,
    int nBindFlags = BINDF_ASYNCHRONOUS |   BINDF_ASYNCSTORAGE | BINDF_GETNEWESTVERSION | BINDF_NOWRITECACHE>  
class ATL_NO_VTABLE CBindStatusCallback : public CComObjectRootEx
 <T ::_ThreadModel::ThreadModelNoCS>,
    public IBindStatusCallbackImpl<T>
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Třídě, která obsahuje funkce, která bude volána, jako jsou data přijata.  
  
 *nBindFlags*  
 Určuje příznaky vazby, které se vrátí pomocí [GetBindInfo](#getbindinfo). Výchozí implementace nastaví vazbu jako asynchronní, načte nejnovější verzi dat nebo objekt a neukládá načtená data v mezipaměti disku.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CBindStatusCallback::CBindStatusCallback](#cbindstatuscallback)|Konstruktor|  
|[CBindStatusCallback:: ~ CBindStatusCallback](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CBindStatusCallback::Download](#download)|Vytvoří statickou metodu, která se spouští proces stahování `CBindStatusCallback` objekt a volání `StartAsyncDownload`.|  
|[CBindStatusCallback::GetBindInfo](#getbindinfo)|Voláno rozhraním asynchronní Přezdívka pro informace o požadavku na typ vazby, který se má vytvořit.|  
|[CBindStatusCallback::GetPriority](#getpriority)|Voláno rozhraním asynchronní Přezdívka získat prioritu operace vazby. Implementace ATL vrátí `E_NOTIMPL`.|  
|[CBindStatusCallback::OnDataAvailable](#ondataavailable)|Voláno k poskytování dat do vaší aplikace, jakmile je k dispozici. Čte data a potom volá funkci předaný tato data použít.|  
|[CBindStatusCallback::OnLowResource](#onlowresource)|Voláno, pokud mají nedostatek prostředků. Implementace ATL vrátí `S_OK`.|  
|[CBindStatusCallback::OnObjectAvailable](#onobjectavailable)|Voláno rozhraním asynchronní Přezdívka předat objekt ukazatele rozhraní do vaší aplikace. Implementace ATL vrátí `S_OK`.|  
|[CBindStatusCallback::OnProgress](#onprogress)|Volá se informace o průběhu dat. proces stahování. Implementace ATL vrátí `S_OK`.|  
|[CBindStatusCallback::OnStartBinding](#onstartbinding)|Volá se při spuštění vazby.|  
|[CBindStatusCallback::OnStopBinding](#onstopbinding)|Volá se při přenosu dat asynchronní je zastavena.|  
|[CBindStatusCallback::StartAsyncDownload](#startasyncdownload)|Inicializuje dostupných bajtů a načíst počet bajtů na nulu, vytvoří objekt typ nabízeného datového proudu z adresy URL a volání `OnDataAvailable` pokaždé, když jsou k dispozici data.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CBindStatusCallback::m_dwAvailableToRead](#m_dwavailabletoread)|Počet bajtů, které jsou k dispozici pro čtení.|  
|[CBindStatusCallback::m_dwTotalRead](#m_dwtotalread)|Celkový počet bajtů přečtených.|  
|[CBindStatusCallback::m_pFunc](#m_pfunc)|Ukazatel na funkci volána, když jsou k dispozici data.|  
|[CBindStatusCallback::m_pT](#m_pt)|Ukazatel na objekt požaduje přenos dat asynchronní.|  
|[CBindStatusCallback::m_spBindCtx](#m_spbindctx)|Ukazatel [IBindCtx](http://msdn.microsoft.com/library/windows/desktop/ms693755) rozhraní pro aktuální operace vazby.|  
|[CBindStatusCallback::m_spBinding](#m_spbinding)|Ukazatel `IBinding` rozhraní pro aktuální operace vazby.|  
|[CBindStatusCallback::m_spMoniker](#m_spmoniker)|Ukazatel [imoniker –](http://msdn.microsoft.com/library/windows/desktop/ms679705) rozhraní pro adresa URL pro použití.|  
|[CBindStatusCallback::m_spStream](#m_spstream)|Ukazatel [IStream on Request](http://msdn.microsoft.com/library/windows/desktop/aa380034) rozhraní pro přenos dat.|  
  
## <a name="remarks"></a>Poznámky  
 `CBindStatusCallback` Třída implementuje `IBindStatusCallback` rozhraní. `IBindStatusCallback`musí být implementované vaše aplikace, takže může přijímat oznámení z přenosu dat asynchronní. Asynchronní Přezdívka poskytované systémem používá `IBindStatusCallback` metody odesílat a přijímat informace o datech asynchronní přenos do a z objektu.  
  
 Obvykle `CBindStatusCallback` objekt je přidružený ke konkrétní vazby operaci. Například v [ASYNCHRONNÍ](../../visual-cpp-samples.md) ukázkové, když nastavíte vlastnost URL vytvoří `CBindStatusCallback` objekt ve volání `Download`:  
  
 [!code-cpp[NVC_ATL_Windowing#86](../../atl/codesnippet/cpp/cbindstatuscallback-class_1.h)]  
  
 Asynchronní Přezdívka je funkce zpětného volání `OnData` volat aplikace, pokud obsahuje data. Asynchronní Přezdívka je poskytované systémem.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CComObjectRootBase`  
  
 `IBindStatusCallback`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `CBindStatusCallback`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlctl.h  
  
##  <a name="cbindstatuscallback"></a>CBindStatusCallback::CBindStatusCallback  
 Konstruktor  
  
```
CBindStatusCallback();
```  
  
### <a name="remarks"></a>Poznámky  
 Vytvoří objekt pro příjem oznámení týkající se přenos dat asynchronní. Jeden objekt se obvykle vytvoří pro každou operaci vazby.  
  
 Konstruktor inicializuje také [m_pT](#m_pt) a [m_pFunc](#m_pfunc) k **NULL**.  
  
##  <a name="dtor"></a>CBindStatusCallback:: ~ CBindStatusCallback  
 Destruktor.  
  
```
~CBindStatusCallback();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny přidělené prostředky.  
  
##  <a name="download"></a>CBindStatusCallback::Download  
 Vytvoří `CBindStatusCallback` objekt a volání `StartAsyncDownload` zahájíte stahování dat asynchronně ze zadané adresy URL.  
  
```
static HRESULT Download(  
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 *pT*  
 [v] Ukazatel na objekt požaduje přenos dat asynchronní. `CBindStatusCallback` Objektu je převést na šablonu pro třídu tohoto objektu.  
  
 *pFunc*  
 [v] Ukazatel na funkci, která přijímá data, která je pro čtení. Funkce je členem skupiny třídu objektu typu `T`. V tématu [StartAsyncDownload](#startasyncdownload) syntaxe a příklady.  
  
 `bstrURL`  
 [v] Adresa URL k získání dat z. Může být libovolný platný název adresy URL nebo souboru. Nemůže být **NULL**. Příklad:  
  
 `CComBSTR mybstr =_T("http://somesite/data.htm")`  
  
 `pUnkContainer`  
 [v] **IUnknown** kontejneru. **NULL** ve výchozím nastavení.  
  
 `bRelative`  
 [v] Příznak určující, zda je relativní nebo absolutní adresu URL. **FALSE** ve výchozím nastavení, což znamená, adresa URL je absolutní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní `HRESULT` hodnoty.  
  
### <a name="remarks"></a>Poznámky  
 Pokaždé, když jsou k dispozici data jsou odeslána do objektu prostřednictvím `OnDataAvailable`. `OnDataAvailable`čte data a volá funkci, na kterou odkazuje *pFunc* (například k uložení dat nebo tisku na obrazovce).  
  
##  <a name="getbindinfo"></a>CBindStatusCallback::GetBindInfo  
 Voláno k informování přezdívka, jak vytvořit vazbu.  
  
```
STDMETHOD(GetBindInfo)(
    DWORD* pgrfBSCF,
    BINDINFO* pbindinfo);
```  
  
### <a name="parameters"></a>Parametry  
 *pgrfBSCF*  
 [out] Ukazatel na **BINDF** hodnot výčtu, která určuje, jak k by mělo dojít operace vazby. Ve výchozím nastavení s následujícími hodnotami výčtu:  
  
 **BINDF_ASYNCHRONOUS** asynchronní stahování.  
  
 **BINDF_ASYNCSTORAGE** `OnDataAvailable` vrátí **E_PENDING** při dat ještě není k dispozici místo zablokovaná, dokud data nejsou k dispozici.  
  
 **BINDF_GETNEWESTVERSION** operaci vazby musí načíst nejnovější verzi data.  
  
 **BINDF_NOWRITECACHE** operace vazby neměli načtená data ukládat do mezipaměti disku.  
  
 *pbindinfo*  
 [ve out] Ukazatel **VAZBĚ** struktura, která poskytuje další informace o tom, jak objekt chce vázání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní `HRESULT` hodnoty.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace nastaví vazbu být asynchronní a používat model data push. V modelu dat nabízené Přezdívka jednotky operace asynchronní vazby a nepřetržitě upozorní klient vždy, když je k dispozici nová data.  
  
##  <a name="getpriority"></a>CBindStatusCallback::GetPriority  
 Voláno rozhraním asynchronní Přezdívka získat prioritu operace vazby.  
  
```
STDMETHOD(GetPriority)(LONG* pnPriority);
```  
  
### <a name="parameters"></a>Parametry  
 *pnPriority*  
 [out] Adresa z **DLOUHO** proměnné, která v případě úspěchu obdrží prioritu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **E_NOTIMPL**.  
  
##  <a name="m_dwavailabletoread"></a>CBindStatusCallback::m_dwAvailableToRead  
 Slouží k uložení počet bajtů, které jsou k dispozici ke čtení.  
  
```
DWORD m_dwAvailableToRead;
```  
  
### <a name="remarks"></a>Poznámky  
 Inicializovaného nula `StartAsyncDownload`.  
  
##  <a name="m_dwtotalread"></a>CBindStatusCallback::m_dwTotalRead  
 Přenos dat asynchronní si přečíst kumulativní součet bajtů.  
  
```
DWORD m_dwTotalRead;
```  
  
### <a name="remarks"></a>Poznámky  
 Zvýší pokaždé, když `OnDataAvailable` volá počet bajtů ve skutečnosti číst. Inicializovaného nula `StartAsyncDownload`.  
  
##  <a name="m_pfunc"></a>CBindStatusCallback::m_pFunc  
 Funkce na kterou odkazuje `m_pFunc` volá `OnDataAvailable` poté, co ho načte všechna dostupná data (například k uložení dat nebo tisku na obrazovce).  
  
```
ATL_PDATAAVAILABLE m_pFunc;
```  
  
### <a name="remarks"></a>Poznámky  
 Funkce na kterou odkazuje `m_pFunc` je členem skupiny třídu objektu a má následující syntaxi:  
  
```  
void Function_Name(  
   CBindStatusCallback<T>* pbsc,  
   BYTE* pBytes,  
   DWORD dwSize  
   );  
```  
  
##  <a name="m_pt"></a>CBindStatusCallback::m_pT  
 Ukazatel na objekt požaduje přenos dat asynchronní.  
  
```
T* m_pT;
```  
  
### <a name="remarks"></a>Poznámky  
 `CBindStatusCallback` Objektu je převést na šablonu pro třídu tohoto objektu.  
  
##  <a name="m_spbindctx"></a>CBindStatusCallback::m_spBindCtx  
 Ukazatel na [IBindCtx](http://msdn.microsoft.com/library/windows/desktop/ms693755) rozhraní, která poskytuje přístup k kontext vazby (objekt, který obsahuje informace o operaci vazbu na konkrétní přezdívka).  
  
```
CComPtr<IBindCtx> m_spBindCtx;
```  
  
### <a name="remarks"></a>Poznámky  
 Inicializovaného v `StartAsyncDownload`.  
  
##  <a name="m_spbinding"></a>CBindStatusCallback::m_spBinding  
 Ukazatel `IBinding` rozhraní aktuální operace vazby.  
  
```
CComPtr<IBinding> m_spBinding;
```  
  
### <a name="remarks"></a>Poznámky  
 Inicializovaného v `OnStartBinding` a vydat v `OnStopBinding`.  
  
##  <a name="m_spmoniker"></a>CBindStatusCallback::m_spMoniker  
 Ukazatel [imoniker –](http://msdn.microsoft.com/library/windows/desktop/ms679705) rozhraní pro adresa URL pro použití.  
  
```
CComPtr<IMoniker> m_spMoniker;
```  
  
### <a name="remarks"></a>Poznámky  
 Inicializovaného v `StartAsyncDownload`.  
  
##  <a name="m_spstream"></a>CBindStatusCallback::m_spStream  
 Ukazatel [IStream on Request](http://msdn.microsoft.com/library/windows/desktop/aa380034) rozhraní aktuální operace vazby.  
  
```
CComPtr<IStream> m_spStream;
```  
  
### <a name="remarks"></a>Poznámky  
 Inicializovaného v `OnDataAvailable` z **STGMEDIUM** struktury, kdy **BCSF** příznak je **BCSF_FIRSTDATANOTIFICATION** a uvolní, pokud **BCSF**  je příznak **BCSF_LASTDATANOTIFICATION**.  
  
##  <a name="ondataavailable"></a>CBindStatusCallback::OnDataAvailable  
 Volání poskytnuté systémem asynchronní Přezdívka `OnDataAvailable` k poskytnutí dat pro objekt, jakmile je k dispozici.  
  
```
STDMETHOD(  
    OnDataAvailable)(DWORD grfBSCF,
    DWORD dwSize,
    FORMATETC* /* pformatetc */,
    STGMEDIUM* pstgmed);
```  
  
### <a name="parameters"></a>Parametry  
 *grfBSCF*  
 [v] A **BSCF** hodnota výčtu. Jeden nebo více z následujících: **BSCF_FIRSTDATANOTIFICATION**, **BSCF_INTERMEDIARYDATANOTIFICATION**, nebo **BSCF_LASTDATANOTIFICATION**.  
  
 `dwSize`  
 [v] Kumulativní velikost (v bajtech) k dispozici od začátku vazby data. Může být nula, která určuje, že množství dat, není relevantní nebo že jsou k dispozici žádná konkrétní dobu.  
  
 *pformatetc*  
 [v] Ukazatel [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682242) struktura, která obsahuje formát všechna dostupná data. Pokud není žádný formát, může být **CF_NULL**.  
  
 *pstgmed*  
 [v] Ukazatel [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms695269) struktura, která obsahuje skutečná data, která je nyní k dispozici.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní `HRESULT` hodnoty.  
  
### <a name="remarks"></a>Poznámky  
 `OnDataAvailable`čte data a potom volá metodu třídu objektu (například k uložení dat nebo tisku na obrazovce). V tématu [CBindStatusCallback::StartAsyncDownload](#startasyncdownload) podrobnosti.  
  
##  <a name="onlowresource"></a>CBindStatusCallback::OnLowResource  
 Voláno, pokud mají nedostatek prostředků.  
  
```
STDMETHOD(OnLowResource)(DWORD /* dwReserved */);
```  
  
### <a name="parameters"></a>Parametry  
 `dwReserved`  
 Vyhrazena.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`.  
  
##  <a name="onobjectavailable"></a>CBindStatusCallback::OnObjectAvailable  
 Voláno rozhraním asynchronní Přezdívka předat objekt ukazatele rozhraní do vaší aplikace.  
  
```
STDMETHOD(OnObjectAvailable)(REFID /* riid */, IUnknown* /* punk */);
```  
  
### <a name="parameters"></a>Parametry  
 `riid`  
 Identifikátor rozhraní požadované rozhraní. Nepoužívá se.  
  
 `punk`  
 Adresa rozhraní IUnknown. Nepoužívá se.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`.  
  
##  <a name="onprogress"></a>CBindStatusCallback::OnProgress  
 Volá se informace o průběhu dat. proces stahování.  
  
```
STDMETHOD(OnProgress)(
    ULONG /* ulProgress */,
    ULONG /* ulProgressMax */,
    ULONG /* ulStatusCode */,
    LPCWSTRONG /* szStatusText */);
```  
  
### <a name="parameters"></a>Parametry  
 `ulProgress`  
 Dlouhé celé číslo bez znaménka. Nepoužívá se.  
  
 `ulProgressMax`  
 Dlouhé celé číslo bez znaménka nepoužitý.  
  
 `ulStatusCode`  
 Dlouhé celé číslo bez znaménka. Nepoužívá se.  
  
 `szStatusText`  
 Adresa řetězcovou hodnotu. Nepoužívá se.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`.  
  
##  <a name="onstartbinding"></a>CBindStatusCallback::OnStartBinding  
 Nastaví datový člen [m_spBinding](#m_spbinding) k `IBinding` ukazatel v `pBinding`.  
  
```
STDMETHOD(OnStartBinding)(DWORD /* dwReserved */, IBinding* pBinding);
```  
  
### <a name="parameters"></a>Parametry  
 `dwReserved`  
 Vyhrazeno pro budoucí použití.  
  
 `pBinding`  
 [v] Adresy rozhraní IBinding aktuální operace připojení. To nemůže mít hodnotu NULL. Klient by měly volat addref – na tento ukazatel zachovat odkaz na objekt vazby.  
  
##  <a name="onstopbinding"></a>CBindStatusCallback::OnStopBinding  
 Verze `IBinding` ukazatel v datový člen [m_spBinding](#m_spbinding).  
  
```
STDMETHOD(OnStopBinding)(HRESULT hresult, LPCWSTR /* szError */);
```  
  
### <a name="parameters"></a>Parametry  
 `hresult`  
 Stavový kód vrácená z operace vazby.  
  
 szStatusText  
 Adresa řetězcovou hodnotu nepoužitý.  
  
### <a name="remarks"></a>Poznámky  
 Voláno rozhraním poskytnuté systémem asynchronní Přezdívka jako upozornění na ukončení operace vazby.  
  
##  <a name="startasyncdownload"></a>CBindStatusCallback::StartAsyncDownload  
 Spustí se asynchronně stahování dat ze zadané adresy URL.  
  
```
HRESULT StartAsyncDownload(  
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 *pT*  
 [v] Ukazatel na objekt požaduje přenos dat asynchronní. `CBindStatusCallback` Objektu je převést na šablonu pro třídu tohoto objektu.  
  
 *pFunc*  
 [v] Ukazatel na funkci, která přijímá data, který je čten. Funkce je členem skupiny třídu objektu typu `T`. V tématu **poznámky** syntaxe a příklady.  
  
 `bstrURL`  
 [v] Adresa URL k získání dat z. Může být libovolný platný název adresy URL nebo souboru. Nemůže být **NULL**. Příklad:  
  
 `CComBSTR mybstr =_T("http://somesite/data.htm")`  
  
 `pUnkContainer`  
 [v] **IUnknown** kontejneru. **NULL** ve výchozím nastavení.  
  
 `bRelative`  
 [v] Příznak určující, zda je relativní nebo absolutní adresu URL. **FALSE** ve výchozím nastavení, což znamená, adresa URL je absolutní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní `HRESULT` hodnoty.  
  
### <a name="remarks"></a>Poznámky  
 Pokaždé, když jsou k dispozici data jsou odeslána do objektu prostřednictvím `OnDataAvailable`. `OnDataAvailable`čte data a volá funkci, na kterou odkazuje *pFunc* (například k uložení dat nebo tisku na obrazovce).  
  
 Funkce na kterou odkazuje *pFunc* je členem skupiny třídu objektu a má následující syntaxi:  
  
 `void Function_Name(`  
  
 `CBindStatusCallback<T>*` `pbsc` `,`  
  
 `BYTE*` `pBytes` `,`  
  
 `DWORD``dwSize`  
  
 `);`  
  
 V následujícím příkladu (převzaty z [ASYNCHRONNÍ](../../visual-cpp-samples.md) ukázkové), funkce `OnData` přijatých dat. zapisuje do textového pole.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#87](../../atl/codesnippet/cpp/cbindstatuscallback-class_2.h)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)
