---
title: CAsyncMonikerFile Class
ms.date: 11/04/2016
f1_keywords:
- CAsyncMonikerFile
- AFXOLE/CAsyncMonikerFile
- AFXOLE/CAsyncMonikerFile::CAsyncMonikerFile
- AFXOLE/CAsyncMonikerFile::Close
- AFXOLE/CAsyncMonikerFile::GetBinding
- AFXOLE/CAsyncMonikerFile::GetFormatEtc
- AFXOLE/CAsyncMonikerFile::Open
- AFXOLE/CAsyncMonikerFile::CreateBindStatusCallback
- AFXOLE/CAsyncMonikerFile::GetBindInfo
- AFXOLE/CAsyncMonikerFile::GetPriority
- AFXOLE/CAsyncMonikerFile::OnDataAvailable
- AFXOLE/CAsyncMonikerFile::OnLowResource
- AFXOLE/CAsyncMonikerFile::OnProgress
- AFXOLE/CAsyncMonikerFile::OnStartBinding
- AFXOLE/CAsyncMonikerFile::OnStopBinding
helpviewer_keywords:
- CAsyncMonikerFile [MFC], CAsyncMonikerFile
- CAsyncMonikerFile [MFC], Close
- CAsyncMonikerFile [MFC], GetBinding
- CAsyncMonikerFile [MFC], GetFormatEtc
- CAsyncMonikerFile [MFC], Open
- CAsyncMonikerFile [MFC], CreateBindStatusCallback
- CAsyncMonikerFile [MFC], GetBindInfo
- CAsyncMonikerFile [MFC], GetPriority
- CAsyncMonikerFile [MFC], OnDataAvailable
- CAsyncMonikerFile [MFC], OnLowResource
- CAsyncMonikerFile [MFC], OnProgress
- CAsyncMonikerFile [MFC], OnStartBinding
- CAsyncMonikerFile [MFC], OnStopBinding
ms.assetid: 17378b66-a49a-4b67-88e3-7756ad26a2fc
ms.openlocfilehash: b86cba0c2e8f7991902a552d404355d6c1474138
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62237854"
---
# <a name="casyncmonikerfile-class"></a>CAsyncMonikerFile Class

Poskytuje funkce pro používání asynchronních zástupných názvů v ovládacích prvcích ActiveX (dříve ovládací prvky OLE).

## <a name="syntax"></a>Syntaxe

```
class CAsyncMonikerFile : public CMonikerFile
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAsyncMonikerFile::CAsyncMonikerFile](#casyncmonikerfile)|Vytvoří `CAsyncMonikerFile` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAsyncMonikerFile::Close](#close)|Zavře a uvolní všechny prostředky.|
|[CAsyncMonikerFile::GetBinding](#getbinding)|Načte ukazatel na asynchronní přenos vazby.|
|[CAsyncMonikerFile::GetFormatEtc](#getformatetc)|Získá formát dat v datovém proudu.|
|[CAsyncMonikerFile::Open](#open)|Otevře soubor asynchronně.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CAsyncMonikerFile::CreateBindStatusCallback](#createbindstatuscallback)|Vytvoří objekt modelu COM, který implementuje `IBindStatusCallback`.|
|[CAsyncMonikerFile::GetBindInfo](#getbindinfo)|Voláno rozhraním systému knihovny OLE na informace o žádostech na typ vazby, který se má vytvořit.|
|[CAsyncMonikerFile::GetPriority](#getpriority)|Je voláno knihovny OLE systému získat prioritu vazby.|
|[CAsyncMonikerFile::OnDataAvailable](#ondataavailable)|Volána k poskytnutí dat, protože je k dispozici do klienta během operací asynchronního vazby.|
|[CAsyncMonikerFile::OnLowResource](#onlowresource)|Volá se, když mají nedostatek prostředků.|
|[CAsyncMonikerFile::OnProgress](#onprogress)|Volá se, aby indikoval průběh procesu stahování dat.|
|[CAsyncMonikerFile::OnStartBinding](#onstartbinding)|Volá se, když se zahajuje vazba.|
|[CAsyncMonikerFile::OnStopBinding](#onstopbinding)|Volá se, když se zastaví asynchronní přenos.|

## <a name="remarks"></a>Poznámky

Odvozený od [cmonikerfile –](../../mfc/reference/cmonikerfile-class.md), který je zase odvozen z [colestreamfile –](../../mfc/reference/colestreamfile-class.md), `CAsyncMonikerFile` používá [imoniker –](/windows/desktop/api/objidl/nn-objidl-imoniker) rozhraní pro přístup k jakékoli datový proud asynchronně včetně asynchronní načítání souborů z adresy URL. Soubory mohou být datapath vlastností ovládacích prvků ActiveX.

Asynchronní monikery se používají především v internetových aplikací a ovládací prvky ActiveX k zajištění responzivní uživatelské rozhraní během přenosu souborů. Typickým příkladem tohoto je použití [cdatapathproperty –](../../mfc/reference/cdatapathproperty-class.md) k poskytování asynchronní vlastností pro ovládací prvky ActiveX. `CDataPathProperty` Objektu se zobrazí opakovaně zpětného volání k označení dostupnost nových dat systému exchange během dlouhých vlastnost.

Další informace o tom, jak použít asynchronní monikery a ovládací prvky ActiveX v internetových aplikací najdete v následujících článcích:

- [První kroky Internetu: Asynchronní Monikery](../../mfc/asynchronous-monikers-on-the-internet.md)

- [První kroky Internetu: Ovládací prvky ActiveX](../../mfc/activex-controls-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

`CAsyncMonikerFile`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxole.h

##  <a name="casyncmonikerfile"></a>  CAsyncMonikerFile::CAsyncMonikerFile

Vytvoří `CAsyncMonikerFile` objektu.

```
CAsyncMonikerFile();
```

### <a name="remarks"></a>Poznámky

Nevytvoří `IBindHost` rozhraní. `IBindHost` se používá jenom v případě, že ho zadáte `Open` členskou funkci.

Popis `IBindHost` rozhraní, naleznete v sadě Windows SDK.

##  <a name="close"></a>  CAsyncMonikerFile::Close

Voláním této funkce zavřete a uvolnit všechny prostředky.

```
virtual void Close();
```

### <a name="remarks"></a>Poznámky

Můžete volat v neotevřených souborů již uzavřený.

##  <a name="createbindstatuscallback"></a>  CAsyncMonikerFile::CreateBindStatusCallback

Vytvoří objekt modelu COM, který implementuje `IBindStatusCallback`.

```
virtual IUnknown* CreateBindStatusCallback(IUnknown* pUnkControlling);
```

### <a name="parameters"></a>Parametry

*pUnkControlling*<br/>
Ukazatel na řídící neznámé (vnější `IUnknown`) nebo hodnota NULL, pokud se nepoužívá agregace.

### <a name="return-value"></a>Návratová hodnota

Pokud *pUnkControlling* nemá hodnotu NULL, funkce vrátí ukazatel na vnitřní `IUnknown` na nový objekt modelu COM podporuje `IBindStatusCallback`. Pokud `pUnkControlling` má hodnotu NULL, funkce vrátí ukazatel `IUnknown` na nový objekt modelu COM podporuje `IBindStatusCallback`.

### <a name="remarks"></a>Poznámky

`CAsyncMonikerFile` vyžaduje objekt modelu COM, který implementuje `IBindStatusCallback`. Knihovna MFC implementuje takového objektu a je agregovatelné. Můžete přepsat `CreateBindStatusCallback` vrátit objekt modelu COM. Váš objekt modelu COM může agregovat implementace MFC voláním `CreateBindStatusCallback` s řídící neznámou váš objekt modelu COM. COM objekty implementované pomocí `CCmdTarget` podporu modelu COM může načíst řídící neznámé pomocí `CCmdTarget::GetControllingUnknown`.

Alternativně můžete váš objekt modelu COM delegovat do implementace MFC voláním `CreateBindStatusCallback( NULL )`.

[CAsyncMonikerFile::Open](#open) volání `CreateBindStatusCallback`.

Další informace o asynchronní monikery a asynchronní vazby, najdete v článku [IBindStatusCallback](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775060\(v=vs.85\)) rozhraní a [pracovní úložiště a jak asynchronní vazby](/windows/desktop/Stg/how-asynchronous-binding-and-storage-work). Informace o agregaci naleznete v tématu [agregace](/windows/desktop/com/aggregation). Všechny tři témata jsou v sadě Windows SDK.

##  <a name="getbindinfo"></a>  CAsyncMonikerFile::GetBindInfo

Volá se z klienta asynchronní moniker asynchronní moniker zjistit, jak chce vytvořit vazbu.

```
virtual DWORD GetBindInfo() const;
```

### <a name="return-value"></a>Návratová hodnota

Načte nastavení pro `IBindStatusCallBack`. Popis `IBindStatusCallback` rozhraní, naleznete v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Výchozí implementace nastaví vazbu byla asynchronní, použijte úložiště média (datový proud) a použít model data push. Tato funkce přepište, pokud chcete změnit chování vazby.

Jedním z důvodů tím by se vytvořit vazbu pomocí modelu dat o přijetí změn místo model data push. V modelu data o přijetí změn klient jednotky operace připojení a monikeru pouze poskytuje data klientovi, když je pro čtení. V modelu datová oznámení zástupný název jednotky operace asynchronního připojení a průběžně upozorní klienta pokaždé, když jsou k dispozici nová data.

##  <a name="getbinding"></a>  CAsyncMonikerFile::GetBinding

Volání této funkce načtete ukazatel na asynchronní přenos vazby.

```
IBinding* GetBinding() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel `IBinding` rozhraní při zahájení asynchronní přenos. Vrátí hodnotu NULL, pokud pro přenos z nějakého důvodu není možné provést asynchronně.

### <a name="remarks"></a>Poznámky

To umožňuje řídit proces pro přenos dat `IBinding` rozhraní, například s `IBinding::Abort`, `IBinding::Pause`, a `IBinding::Resume`.

Popis `IBinding` rozhraní, naleznete v sadě Windows SDK.

##  <a name="getformatetc"></a>  CAsyncMonikerFile::GetFormatEtc

Voláním této funkce načtete formát dat v datovém proudu.

```
FORMATETC* GetFormatEtc() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na strukturu Windows [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) pro aktuálně otevřený datového proudu. Vrátí hodnotu NULL, pokud nebyla byla svázána monikeru, pokud není asynchronní, nebo pokud ještě nebylo spuštěno asynchronní operace.

##  <a name="getpriority"></a>  CAsyncMonikerFile::GetPriority

Volané z klienta asynchronní moniker proces vytváření vazby začne přijímat přednostně vlákno pro operace vazby.

```
virtual LONG GetPriority() const;
```

### <a name="return-value"></a>Návratová hodnota

Priorita, ve kterém se asynchronní přenos proběhnout. Jedním z příznaků priority standardní vlákna: THREAD_PRIORITY_ABOVE_NORMAL THREAD_PRIORITY_BELOW_NORMAL, THREAD_PRIORITY_HIGHEST, THREAD_PRIORITY_IDLE, THREAD_PRIORITY_LOWEST, THREAD_PRIORITY_NORMAL a THREAD_PRIORITY_TIME_CRITICAL. Podívat se na funkci Windows [SetThreadPriority](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) popis z těchto hodnot.

### <a name="remarks"></a>Poznámky

`GetPriority` nemůže se volat přímo. THREAD_PRIORITY_NORMAL vrátí výchozí implementaci.

##  <a name="ondataavailable"></a>  CAsyncMonikerFile::OnDataAvailable

Volá asynchronní moniker `OnDataAvailable` předávat data do klienta, protože je k dispozici, vazby během asynchronní operace.

```
virtual void OnDataAvailable(DWORD dwSize, DWORD bscfFlag);
```

### <a name="parameters"></a>Parametry

*dwSize*<br/>
Souhrnně za (v bajtech) k dispozici od začátku vazby data. Může být nula, označující, že objem dat se nevztahuje na operaci nebo že bez ohledu na konkrétní začal být k dispozici.

*bscfFlag*<br/>
Hodnota výčtu BSCF. Může být jeden nebo více z následujících hodnot:

- První volání identifikuje BSCF_FIRSTDATANOTIFICATION `OnDataAvailable` pro operace dané připojení.

- BSCF_INTERMEDIATEDATANOTIFICATION identifikuje zprostředkující volání `OnDataAvailable` pro operace připojení.

- BSCF_LASTDATANOTIFICATION identifikuje poslední volání `OnDataAvailable` pro operace připojení.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce nemá žádný účinek. Podívejte se na následující příklad ukázku implementace.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWinInet#5](../../mfc/codesnippet/cpp/casyncmonikerfile-class_1.cpp)]

##  <a name="onlowresource"></a>  CAsyncMonikerFile::OnLowResource

Voláno rozhraním monikeru, když mají nedostatek prostředků.

```
virtual void OnLowResource();
```

### <a name="remarks"></a>Poznámky

Výchozí implementace volá `GetBinding( )-> Abort( )`.

##  <a name="onprogress"></a>  CAsyncMonikerFile::OnProgress

Je voláno moniker opakovaně k označení aktuální průběh této operace připojení, obvykle v rozumné intervalech během operace s delším průběhem.

```
virtual void OnProgress(
    ULONG ulProgress,
    ULONG ulProgressMax,
    ULONG ulStatusCode,
    LPCTSTR szStatusText);
```

### <a name="parameters"></a>Parametry

*ulProgress*<br/>
Označuje aktuální průběh operace připojení vzhledem k očekávané maximální podle *ulProgressMax*.

*ulProgressMax*<br/>
Označuje očekávaný maximální hodnotu *ulProgress* po dobu trvání volání `OnProgress` pro tuto operaci.

*ulStatusCode*<br/>
Poskytuje další informace o průběhu operace připojení. Platné hodnoty jsou převzaty z `BINDSTATUS` výčtu. Možné hodnoty najdete v článku poznámky.

*szStatusText*<br/>
Informace o aktuální průběh, závisí na hodnotě *ulStatusCode*. Možné hodnoty najdete v článku poznámky.

### <a name="remarks"></a>Poznámky

Možné hodnoty pro *ulStatusCode* (a *szStatusText* pro každou hodnotu) jsou:

|||
|-|-|
|BINDSTATUS_FINDINGRESOURCE  |Operace připojení je hledání, který obsahuje objekt nebo úložiště je vázána na prostředek. *SzStatusText* obsahuje zobrazovaný název prostředku vyhledávaná (například "www.microsoft.com").  |
|BINDSTATUS_CONNECTING  |Operace připojení se připojuje k prostředku, který obsahuje objekt nebo vázání na úložiště. *SzStatusText* obsahuje zobrazovaný název prostředku připojení k (například IP adresa).  |
|BINDSTATUS_SENDINGREQUEST|Operace připojení požaduje objekt nebo vázání na úložiště. *SzStatusText* obsahuje zobrazovaný název objektu (například název souboru).|
|BINDSTATUS_REDIRECTING  |Operace připojení byl přesměrován do různých datových umístění. *SzStatusText* obsahuje zobrazovaný název nové umístění data.  |
|BINDSTATUS_USINGCACHEDCOPY  |Operace připojení je načítání požadovaný objekt nebo úložiště z kopie v mezipaměti. *SzStatusText* má hodnotu NULL.  |
|BINDSTATUS_BEGINDOWNLOADDATA  |Operace připojení byl zahájen příjem objektu nebo úložiště svázaný s. *SzStatusText* obsahuje zobrazovaný název data umístění.|
|BINDSTATUS_DOWNLOADINGDATA  |Operace připojení i nadále přijímat objektu nebo úložiště svázaný s. *SzStatusText* obsahuje zobrazovaný název data umístění.  |
|BINDSTATUS_ENDDOWNLOADDATA  |Operace připojení bylo dokončeno přijetí objektu nebo úložiště svázaný s. *SzStatusText* obsahuje zobrazovaný název data umístění.  |
|BINDSTATUS_CLASSIDAVAILABLE  |Instance objektu svázaný s je jen o který se má vytvořit. *SzStatusText* poskytuje CLSID nového objektu ve formátu řetězce, a umožnil tak klientovi příležitost ke zrušení operace vazby v případě potřeby.  |

##  <a name="onstartbinding"></a>  CAsyncMonikerFile::OnStartBinding

Přepsání této funkce ve vaší odvozené třídy k provádění akcí, když se zahajuje vazba.

```
virtual void OnStartBinding();
```

### <a name="remarks"></a>Poznámky

Tato funkce je volána zpět monikeru. Výchozí implementace nemá žádný účinek.

##  <a name="onstopbinding"></a>  CAsyncMonikerFile::OnStopBinding

Je voláno moniker na konci operace připojení.

```
virtual void OnStopBinding(HRESULT hresult, LPCTSTR szError);
```

### <a name="parameters"></a>Parametry

*Hodnota HRESULT*<br/>
HRESULT, který je chybu nebo upozornění hodnotu.

*szErrort*<br/>
Znakový řetězec popisující chybu.

### <a name="remarks"></a>Poznámky

Potlačí tuto funkci k provádění akcí, když se zastaví přenos. Ve výchozím nastavení, funkce uvolní `IBinding`.

Popis `IBinding` rozhraní, naleznete v sadě Windows SDK.

##  <a name="open"></a>  CAsyncMonikerFile::Open

Voláním této členské funkce a otevřete soubor asynchronně.

```
virtual BOOL Open(
    LPCTSTR lpszURL,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszURL,
    IBindHost* pBindHost,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    IBindHost* pBindHost,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszURL,
    IServiceProvider* pServiceProvider,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    IServiceProvider* pServiceProvider,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszURL,
    IUnknown* pUnknown,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    IUnknown* pUnknown,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>Parametry

*lpszURL*<br/>
Ukazatel na soubor otevřít asynchronně. Soubor může být platná adresa URL nebo název souboru.

*pError*<br/>
Ukazatel na soubor výjimky. V případě chyby bude nastavena na příčinu.

*pMoniker*<br/>
Ukazatel na rozhraní asynchronní moniker `IMoniker`, přesné monikeru, který je kombinací identifikátoru dokumentu vlastní monikeru, který můžete získat pomocí `IOleClientSite::GetMoniker(OLEWHICHMK_CONTAINER)`a monikeru vytvořené z názvu cesty. Ovládací prvek můžete používat tento zástupný název pro vytvoření vazby, ale to není moniker by měl ovládací prvek uložit.

*pBindHost*<br/>
Ukazatel `IBindHost` rozhraní, které se použije k vytvoření zástupný název z potenciálně relativní cestu. Je-li hostitele vazby je neplatný nebo neposkytuje monikeru, volání výchozí `Open(lpszFileName,pError)`. Popis `IBindHost` rozhraní, naleznete v sadě Windows SDK.

*pServiceProvider*<br/>
Ukazatel `IServiceProvider` rozhraní. Pokud poskytovatel služeb je neplatný, nebo nebude schopen poskytnout službu `IBindHost`, výchozí hodnota volání `Open(lpszFileName,pError)`.

*pUnknown*<br/>
Ukazatel `IUnknown` rozhraní. Pokud `IServiceProvider` není nalezen, funkce dotazů pro `IBindHost`. Pokud poskytovatel služeb je neplatný, nebo nebude schopen poskytnout službu `IBindHost`, výchozí hodnota volání `Open(lpszFileName,pError)`.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je soubor otevřen úspěšně; jinak 0.

### <a name="remarks"></a>Poznámky

Toto volání zahájí proces vytváření vazby.

Můžete použít adresu URL nebo název souboru pro *lpszURL* parametru. Příklad:

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/casyncmonikerfile-class_2.cpp)]

\- nebo –

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/casyncmonikerfile-class_3.cpp)]

## <a name="see-also"></a>Viz také:

[CMonikerFile – třída](../../mfc/reference/cmonikerfile-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CMonikerFile – třída](../../mfc/reference/cmonikerfile-class.md)<br/>
[CDataPathProperty – třída](../../mfc/reference/cdatapathproperty-class.md)
