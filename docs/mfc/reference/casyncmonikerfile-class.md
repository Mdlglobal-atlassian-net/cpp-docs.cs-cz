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
ms.openlocfilehash: cd399368e46e4e9a86b4c6260e07aee07b80defb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507504"
---
# <a name="casyncmonikerfile-class"></a>CAsyncMonikerFile Class

Poskytuje funkce pro použití asynchronních monikerů v ovládacích prvcích ActiveX (dříve ovládací prvky OLE).

## <a name="syntax"></a>Syntaxe

```
class CAsyncMonikerFile : public CMonikerFile
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CAsyncMonikerFile::CAsyncMonikerFile](#casyncmonikerfile)|`CAsyncMonikerFile` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CAsyncMonikerFile::Close](#close)|Zavře a uvolní všechny prostředky.|
|[CAsyncMonikerFile::GetBinding](#getbinding)|Načte ukazatel na vazbu asynchronního přenosu.|
|[CAsyncMonikerFile::GetFormatEtc](#getformatetc)|Načte formát dat v datovém proudu.|
|[CAsyncMonikerFile::Open](#open)|Otevře soubor asynchronně.|

### <a name="protected-methods"></a>Chráněné metody

|Name|Popis|
|----------|-----------------|
|[CAsyncMonikerFile::CreateBindStatusCallback](#createbindstatuscallback)|Vytvoří objekt modelu COM, který `IBindStatusCallback`implementuje.|
|[CAsyncMonikerFile::GetBindInfo](#getbindinfo)|Volá se systémovou knihovnou OLE k vyžádání informací o typu vazby, která se má vytvořit.|
|[CAsyncMonikerFile::GetPriority](#getpriority)|Volá se systémovou knihovnou OLE, aby se získala priorita vazby.|
|[CAsyncMonikerFile::OnDataAvailable](#ondataavailable)|Volá se, aby se poskytovala data, která jsou k dispozici klientovi během operací asynchronní vazby.|
|[CAsyncMonikerFile::OnLowResource](#onlowresource)|Volá se, když jsou prostředky nízké.|
|[CAsyncMonikerFile::OnProgress](#onprogress)|Volá se, aby se označoval průběh procesu stahování dat.|
|[CAsyncMonikerFile::OnStartBinding](#onstartbinding)|Volá se při spuštění vazby.|
|[CAsyncMonikerFile::OnStopBinding](#onstopbinding)|Volá se, když se zastaví asynchronní přenos.|

## <a name="remarks"></a>Poznámky

Odvozeno od [CMonikerFile](../../mfc/reference/cmonikerfile-class.md), které je zase odvozeno od [COleStreamFile](../../mfc/reference/colestreamfile-class.md), `CAsyncMonikerFile` používá rozhraní [IMoniker –](/windows/win32/api/objidl/nn-objidl-imoniker) k asynchronnímu přístupu ke všem datovým proudům, včetně načítání souborů asynchronně z adresy URL. Soubory mohou být vlastnosti DataPath ovládacích prvků ActiveX.

Asynchronní monikery se používají primárně v aplikacích s podporou Internetu a ovládacích prvků ActiveX k tomu, aby během přenosů souborů poskytovala uživatelské rozhraní s rychlostí odezvy. Hlavní příklad tohoto je použití [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md) k poskytnutí asynchronních vlastností ovládacích prvků ActiveX. `CDataPathProperty` Objekt se opakovaně vrátí zpět k označení dostupnosti nových dat během procesu výměny vlastností s délkou.

Další informace o použití asynchronních monikerů a ovládacích prvků ActiveX v internetových aplikacích naleznete v následujících článcích:

- [První kroky Internetu: Asynchronní monikery](../../mfc/asynchronous-monikers-on-the-internet.md)

- [První kroky Internetu: Ovládací prvky ActiveX](../../mfc/activex-controls-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CFile –](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

`CAsyncMonikerFile`

## <a name="requirements"></a>Požadavky

**Záhlaví:** AFXOLE. h

##  <a name="casyncmonikerfile"></a>CAsyncMonikerFile::CAsyncMonikerFile

`CAsyncMonikerFile` Vytvoří objekt.

```
CAsyncMonikerFile();
```

### <a name="remarks"></a>Poznámky

Nevytváří `IBindHost` rozhraní. `IBindHost`je použit pouze v případě, že jej zadáte do `Open` členské funkce.

Popis `IBindHost` rozhraní naleznete v Windows SDK.

##  <a name="close"></a>CAsyncMonikerFile:: Close

Voláním této funkce zavřete a vydáte všechny prostředky.

```
virtual void Close();
```

### <a name="remarks"></a>Poznámky

Lze ji volat v neotevřených nebo již uzavřených souborech.

##  <a name="createbindstatuscallback"></a>  CAsyncMonikerFile::CreateBindStatusCallback

Vytvoří objekt modelu COM, který `IBindStatusCallback`implementuje.

```
virtual IUnknown* CreateBindStatusCallback(IUnknown* pUnkControlling);
```

### <a name="parameters"></a>Parametry

*pUnkControlling*<br/>
Ukazatel na řízení Neznámý (vnější `IUnknown`) nebo null, pokud není použita agregace.

### <a name="return-value"></a>Návratová hodnota

Pokud *pUnkControlling* není null, funkce vrátí ukazatel na vnitřní `IUnknown` objekt na novém objektu com podporujícího. `IBindStatusCallback` Pokud `pUnkControlling` je null, funkce vrátí ukazatel `IUnknown` na nový objekt com podporující `IBindStatusCallback`.

### <a name="remarks"></a>Poznámky

`CAsyncMonikerFile`vyžaduje objekt COM, který implementuje `IBindStatusCallback`. Knihovna MFC implementuje takový objekt a je agregovatelné. Můžete přepsat `CreateBindStatusCallback` pro vrácení vlastního objektu com. Objekt modelu COM může agregovat implementaci knihovny MFC voláním `CreateBindStatusCallback` s řízením neznámého objektu com. Objekty modelu COM implementované pomocí `CCmdTarget` podpory modelu COM mohou načíst neznámou `CCmdTarget::GetControllingUnknown`kontrolu pomocí.

Alternativně může váš objekt COM delegovat na implementaci knihovny MFC voláním `CreateBindStatusCallback( NULL )`.

[CAsyncMonikerFile:: Open](#open) Calls `CreateBindStatusCallback`.

Další informace o asynchronních monikerech a asynchronních vazbách naleznete v rozhraní [IBindStatusCallback](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775060\(v=vs.85\)) a na [způsobu fungování asynchronní vazby a úložiště](/windows/win32/Stg/how-asynchronous-binding-and-storage-work). Diskuzi o agregaci naleznete v tématu [agregace](/windows/win32/com/aggregation). Všechna tři témata jsou uvedená v Windows SDK.

##  <a name="getbindinfo"></a>CAsyncMonikerFile:: GetBindInfo.

Volána od klienta asynchronního monikeru, aby označovala asynchronní moniker, jak chce vytvořit vazbu.

```
virtual DWORD GetBindInfo() const;
```

### <a name="return-value"></a>Návratová hodnota

Načte nastavení pro `IBindStatusCallBack`. Popis `IBindStatusCallback` rozhraní naleznete v Windows SDK.

### <a name="remarks"></a>Poznámky

Výchozí implementace nastavuje, aby vazba byla asynchronní, aby používala paměťové médium (datový proud) a používala model nabízených dat. Tuto funkci přepište, pokud chcete změnit chování vazby.

Jedním z důvodů, proč by to bylo, bylo vytvoření vazby pomocí modelu vyžádání dat namísto modelu vkládání dat. V modelu pro vyžádání dat klient zařídí operaci vazby a moniker při čtení poskytuje pouze data klientovi. V modelu pro vložení dat zastupuje moniker operaci asynchronní vazby a nepřetržitě upozorní klienta, kdykoli jsou k dispozici nová data.

##  <a name="getbinding"></a>CAsyncMonikerFile:: GetBinding

Voláním této funkce načtete ukazatel na vazbu asynchronního přenosu.

```
IBinding* GetBinding() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `IBinding` rozhraní poskytnuté při zahájení asynchronního přenosu. Vrátí hodnotu NULL, pokud z nějakého důvodu nelze přenos provést asynchronně.

### <a name="remarks"></a>Poznámky

To vám umožňuje řídit proces přenosu dat `IBinding` prostřednictvím rozhraní, například pomocí `IBinding::Abort`, `IBinding::Pause`a `IBinding::Resume`.

Popis `IBinding` rozhraní naleznete v Windows SDK.

##  <a name="getformatetc"></a>CAsyncMonikerFile::GetFormatEtc

Voláním této funkce načtete formát dat v datovém proudu.

```
FORMATETC* GetFormatEtc() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na strukturu Windows [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) pro aktuálně otevřený datový proud. Vrátí hodnotu NULL, pokud moniker nebyl svázán, pokud není asynchronní, nebo pokud nebyla zahájena asynchronní operace.

##  <a name="getpriority"></a>CAsyncMonikerFile:: GetPriority

Volá se od klienta asynchronního monikeru, protože proces vazby začíná přijmout prioritu určenou vláknu pro operaci vazby.

```
virtual LONG GetPriority() const;
```

### <a name="return-value"></a>Návratová hodnota

Priorita, na které bude prováděn asynchronní přenos. Jeden ze standardních příznaků priority vlákna: THREAD_PRIORITY_ABOVE_NORMAL, THREAD_PRIORITY_BELOW_NORMAL, THREAD_PRIORITY_HIGHEST, THREAD_PRIORITY_IDLE, THREAD_PRIORITY_LOWEST, THREAD_PRIORITY_NORMAL a THREAD_PRIORITY_TIME_CRITICAL. Popis těchto hodnot najdete v [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) funkce systému Windows.

### <a name="remarks"></a>Poznámky

`GetPriority`nesmí být volána přímo. THREAD_PRIORITY_NORMAL je vrácen výchozí implementací.

##  <a name="ondataavailable"></a>  CAsyncMonikerFile::OnDataAvailable

Asynchronní moniker zavolá `OnDataAvailable` , aby poskytoval data klientovi, jak bude k dispozici během asynchronních operací vazby.

```
virtual void OnDataAvailable(DWORD dwSize, DWORD bscfFlag);
```

### <a name="parameters"></a>Parametry

*nenulového dwSize funkci*<br/>
Kumulativní množství dat (v bajtech), která jsou k dispozici od začátku vazby. Může být nula, což znamená, že množství dat není relevantní pro operaci nebo že žádná konkrétní částka nebyla k dispozici.

*bscfFlag*<br/>
Hodnota výčtu BSCF. Může to být jedna nebo víc z následujících hodnot:

- BSCF_FIRSTDATANOTIFICATION identifikuje první volání `OnDataAvailable` pro danou operaci vazby.

- BSCF_INTERMEDIATEDATANOTIFICATION identifikuje zprostředkující volání `OnDataAvailable` pro operaci vazby.

- BSCF_LASTDATANOTIFICATION identifikuje poslední volání `OnDataAvailable` pro operaci vazby.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce neprovede žádnou akci. V následujícím příkladu se zobrazí ukázková implementace.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWinInet#5](../../mfc/codesnippet/cpp/casyncmonikerfile-class_1.cpp)]

##  <a name="onlowresource"></a>  CAsyncMonikerFile::OnLowResource

Volá se monikerem, když jsou prostředky nízké.

```
virtual void OnLowResource();
```

### <a name="remarks"></a>Poznámky

Výchozí volání `GetBinding( )-> Abort( )`implementace.

##  <a name="onprogress"></a>  CAsyncMonikerFile::OnProgress

Volána monikerem opakovaně k označení aktuálního průběhu této operace vazby, obvykle v přiměřených intervalech během operace s délkou.

```
virtual void OnProgress(
    ULONG ulProgress,
    ULONG ulProgressMax,
    ULONG ulStatusCode,
    LPCTSTR szStatusText);
```

### <a name="parameters"></a>Parametry

*ulProgress*<br/>
Označuje aktuální průběh operace vazby vzhledem k očekávanému maximu uvedenému v *ulProgressMax*.

*ulProgressMax*<br/>
Označuje očekávanou maximální hodnotu *ulProgress* pro dobu trvání volání `OnProgress` pro tuto operaci.

*ulStatusCode*<br/>
Poskytuje další informace týkající se průběhu operace vazby. Platné hodnoty jsou pořízeny `BINDSTATUS` z výčtu. Možné hodnoty najdete v části poznámky.

*szStatusText*<br/>
Informace o aktuálním průběhu v závislosti na hodnotě *ulStatusCode* Možné hodnoty najdete v části poznámky.

### <a name="remarks"></a>Poznámky

Možné hodnoty pro *ulStatusCode* (a *szStatusText* pro každou hodnotu) jsou:

|||
|-|-|
|BINDSTATUS_FINDINGRESOURCE  |Operace BIND hledá prostředek, na kterém je uložený objekt nebo úložiště, na kterém je vázáno. *SzStatusText* poskytuje zobrazované jméno hledaného prostředku (například "www.Microsoft.com").  |
|BINDSTATUS_CONNECTING  |Operace BIND se připojuje k prostředku, který obsahuje objekt nebo úložiště, na které je vázáno. *SzStatusText* poskytuje zobrazované jméno prostředku, ke kterému se připojuje (například IP adresa).  |
|BINDSTATUS_SENDINGREQUEST|Operace BIND požaduje objekt nebo úložiště, na které je vázáno. *SzStatusText* poskytuje zobrazované jméno objektu (například název souboru).|
|BINDSTATUS_REDIRECTING  |Operace vazby byla přesměrována na jiné umístění dat. *SzStatusText* poskytuje zobrazované jméno nového umístění dat.  |
|BINDSTATUS_USINGCACHEDCOPY  |Operace BIND načítá požadovaný objekt nebo úložiště z kopie v mezipaměti. *SzStatusText* má hodnotu null.  |
|BINDSTATUS_BEGINDOWNLOADDATA  |Operace BIND zahájila příjem objektu nebo úložiště svázaného s. *SzStatusText* poskytuje zobrazovaný název umístění dat.|
|BINDSTATUS_DOWNLOADINGDATA  |Operace vazby nadále přijímá objekt nebo úložiště, na které je vázáno. *SzStatusText* poskytuje zobrazovaný název umístění dat.  |
|BINDSTATUS_ENDDOWNLOADDATA  |Operace BIND dokončila přijímání objektu nebo úložiště, na které je vázáno. *SzStatusText* poskytuje zobrazovaný název umístění dat.  |
|BINDSTATUS_CLASSIDAVAILABLE  |Instance objektu, na který se váže, je právě vytvořena. *SzStatusText* poskytuje identifikátor CLSID nového objektu ve formátu řetězce a umožňuje klientovi možnost zrušit operaci vazby, pokud je to žádoucí.  |

##  <a name="onstartbinding"></a>  CAsyncMonikerFile::OnStartBinding

Tuto funkci v odvozených třídách přepište, aby prováděla akce při spuštění vazby.

```
virtual void OnStartBinding();
```

### <a name="remarks"></a>Poznámky

Tato funkce je volána zpět monikerem. Výchozí implementace neprovádí žádnou akci.

##  <a name="onstopbinding"></a>CAsyncMonikerFile::OnStopBinding

Volá se monikerem na konci operace vazby.

```
virtual void OnStopBinding(HRESULT hresult, LPCTSTR szError);
```

### <a name="parameters"></a>Parametry

*HRESULT*<br/>
Hodnota HRESULT, která je chybou nebo upozorněním.

*szErrort*<br/>
Řetězec znaků popisující chybu.

### <a name="remarks"></a>Poznámky

Přepište tuto funkci, aby se prováděly akce, když se přenos zastaví. Ve výchozím nastavení vydává `IBinding`funkce.

Popis `IBinding` rozhraní naleznete v Windows SDK.

##  <a name="open"></a>CAsyncMonikerFile:: Open

Zavolejte tuto členskou funkci pro asynchronní otevření souboru.

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
Ukazatel na soubor, který se má spustit asynchronně. Soubor může být libovolná platná adresa URL nebo název souboru.

*pError*<br/>
Ukazatel na výjimky souboru. V případě chyby bude nastavena na příčinu.

*pMoniker*<br/>
Ukazatel na rozhraní `IMoniker`asynchronního monikeru, přesný moniker, který je kombinací vlastního monikeru dokumentu, který můžete načíst pomocí `IOleClientSite::GetMoniker(OLEWHICHMK_CONTAINER)`a moniker vytvořený z názvu cesty. Ovládací prvek může použít tento moniker k vytvoření vazby, ale toto není moniker, který by měl ovládací prvek Uložit.

*pBindHost*<br/>
Ukazatel na `IBindHost` rozhraní, které bude použito k vytvoření monikeru z potenciálně relativní cesty. Pokud je hostitel BIND neplatný nebo neposkytuje moniker, je výchozím `Open(lpszFileName,pError)`voláním. Popis `IBindHost` rozhraní naleznete v Windows SDK.

*pServiceProvider*<br/>
Ukazatel na `IServiceProvider` rozhraní. Pokud je poskytovatel služeb neplatný nebo neposkytne službu pro `IBindHost`, použije se `Open(lpszFileName,pError)`výchozí volání.

*pUnknown*<br/>
Ukazatel na `IUnknown` rozhraní. Pokud `IServiceProvider` je nalezen, funkce se dotazuje `IBindHost`pro. Pokud je poskytovatel služeb neplatný nebo neposkytne službu pro `IBindHost`, použije se `Open(lpszFileName,pError)`výchozí volání.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je soubor otevřen úspěšně; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Toto volání inicializuje proces vazby.

Pro parametr *lpszURL* můžete použít adresu URL nebo název souboru. Příklad:

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/casyncmonikerfile-class_2.cpp)]

\- nebo –

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/casyncmonikerfile-class_3.cpp)]

## <a name="see-also"></a>Viz také:

[CMonikerFile – třída](../../mfc/reference/cmonikerfile-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CMonikerFile – třída](../../mfc/reference/cmonikerfile-class.md)<br/>
[CDataPathProperty – třída](../../mfc/reference/cdatapathproperty-class.md)
