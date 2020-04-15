---
title: CAsyncMonikerFile – třída
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
ms.openlocfilehash: 57ab463445f249b4e9393f19af103b7588962d5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376996"
---
# <a name="casyncmonikerfile-class"></a>CAsyncMonikerFile – třída

Poskytuje funkce pro použití asynchronních zástupných názvů v ovládacích prvcích ActiveX (dříve ovládací prvky OLE).

## <a name="syntax"></a>Syntaxe

```
class CAsyncMonikerFile : public CMonikerFile
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CAsyncMonikerFile::CAsyncMonikerFile](#casyncmonikerfile)|Vytvoří `CAsyncMonikerFile` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CAsyncMonikerFile::Zavřít](#close)|Zavře a uvolní všechny prostředky.|
|[CAsyncMonikerFile::GetBinding](#getbinding)|Načte ukazatel na vazbu asynchronního přenosu.|
|[CAsyncMonikerFile::GetFormatEtc](#getformatetc)|Načte formát dat v datovém proudu.|
|[CAsyncMonikerFile::Otevřít](#open)|Otevře soubor asynchronně.|

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CAsyncMonikerFile::CreateBindStatusCallback](#createbindstatuscallback)|Vytvoří objekt COM, `IBindStatusCallback`který implementuje .|
|[CAsyncMonikerFile::GetBindInfo](#getbindinfo)|Volána systémovou knihovnou OLE k vyžádání informací o typu vazby, která má být vytvořena.|
|[CAsyncMonikerFile::GetPriority](#getpriority)|Volána systémovou knihovnou OLE získat prioritu vazby.|
|[CAsyncMonikerFile::OnDataK dispozici](#ondataavailable)|Nazývá poskytnout data, jakmile bude k dispozici klientovi během operací asynchronní vazby.|
|[CAsyncMonikerFile::OnLowResource](#onlowresource)|Nazývá se, když jsou nízké zdroje.|
|[CAsyncMonikerFile::OnProgress](#onprogress)|Nazývá se k označení průběhu procesu stahování dat.|
|[CAsyncMonikerFile::OnStartBinding](#onstartbinding)|Volána při spuštění vazby.|
|[CAsyncMonikerFile::OnStopBinding](#onstopbinding)|Nazývá se při zastavení asynchronního přenosu.|

## <a name="remarks"></a>Poznámky

Odvozeno z [CMonikerFile](../../mfc/reference/cmonikerfile-class.md), který je zase odvozen `CAsyncMonikerFile` z [COleStreamFile](../../mfc/reference/colestreamfile-class.md), používá rozhraní [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker) pro přístup k libovolnému datovému proudu asynchronně, včetně načítání souborů asynchronně z adresy URL. Soubory mohou být vlastnosti datové cesty ovládacích prvků ActiveX.

Asynchronní zástupné názvy se používají především v internetových aplikacích a ovládacích prvcích ActiveX k zajištění responzivního uživatelského rozhraní během přenosu souborů. Ukázkovým příkladem je použití [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md) k poskytnutí asynchronních vlastností ovládacích prvků ActiveX. Objekt `CDataPathProperty` bude opakovaně získat zpětné volání označující dostupnost nových dat během procesu zdlouhavé výměny vlastností.

Další informace o použití asynchronních zástupných názvů a ovládacích prvků ActiveX v internetových aplikacích naleznete v následujících článcích:

- [První kroky internetu: Asynchronní přezdívky](../../mfc/asynchronous-monikers-on-the-internet.md)

- [První kroky Internetu: Ovládací prvky ActiveX](../../mfc/activex-controls-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Soubor C](../../mfc/reference/cfile-class.md)

[Soubor COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[Soubor CMoniker](../../mfc/reference/cmonikerfile-class.md)

`CAsyncMonikerFile`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxole.h

## <a name="casyncmonikerfilecasyncmonikerfile"></a><a name="casyncmonikerfile"></a>CAsyncMonikerFile::CAsyncMonikerFile

Vytvoří `CAsyncMonikerFile` objekt.

```
CAsyncMonikerFile();
```

### <a name="remarks"></a>Poznámky

Nevytváří `IBindHost` rozhraní. `IBindHost`se používá pouze v případě, že jej zadáte v `Open` členské funkci.

Popis rozhraní naleznete `IBindHost` v části Sada Windows SDK.

## <a name="casyncmonikerfileclose"></a><a name="close"></a>CAsyncMonikerFile::Zavřít

Voláním této funkce zavřete a uvolníte všechny prostředky.

```
virtual void Close();
```

### <a name="remarks"></a>Poznámky

Lze volat na neotevřené nebo již uzavřené soubory.

## <a name="casyncmonikerfilecreatebindstatuscallback"></a><a name="createbindstatuscallback"></a>CAsyncMonikerFile::CreateBindStatusCallback

Vytvoří objekt COM, `IBindStatusCallback`který implementuje .

```
virtual IUnknown* CreateBindStatusCallback(IUnknown* pUnkControlling);
```

### <a name="parameters"></a>Parametry

*pUnkControlling*<br/>
Ukazatel na řízení neznámý (vnější) `IUnknown`nebo NULL, pokud agregace není používán.

### <a name="return-value"></a>Návratová hodnota

Pokud *pUnkControlling* není NULL, funkce vrátí ukazatel `IUnknown` na vnitřní na `IBindStatusCallback`nový objekt COM podporující . Pokud `pUnkControlling` je NULL, funkce vrátí `IUnknown` ukazatel na nový objekt `IBindStatusCallback`COM podporující .

### <a name="remarks"></a>Poznámky

`CAsyncMonikerFile`vyžaduje objekt COM, `IBindStatusCallback`který implementuje . Knihovna MFC implementuje takový objekt a je agregovatelný. Můžete přepsat `CreateBindStatusCallback` vrátit vlastní objekt COM. Objekt COM může agregovat implementaci `CreateBindStatusCallback` knihovny MFC voláním s řízením neznámý objektu COM. Objekty COM `CCmdTarget` implementované pomocí podpory modelu `CCmdTarget::GetControllingUnknown`COM mohou načíst řízení neznámý pomocí .

Objekt COM může být přenesen na implementaci knihovny `CreateBindStatusCallback( NULL )`MFC voláním .

[CAsyncMonikerFile::Otevřít](#open) `CreateBindStatusCallback`volání .

Další informace o asynchronních zástupných názvech a asynchronní vazbě naleznete v rozhraní [IBindStatusCallback](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775060\(v=vs.85\)) a [jak funguje asynchronní vazby a úložiště](/windows/win32/Stg/how-asynchronous-binding-and-storage-work). Diskuse o agregaci naleznete [v tématu Agregace](/windows/win32/com/aggregation). Všechna tři témata jsou v sadě Windows SDK.

## <a name="casyncmonikerfilegetbindinfo"></a><a name="getbindinfo"></a>CAsyncMonikerFile::GetBindInfo

Volána z klienta asynchronní zástupný název sdělit asynchronní zástupný název, jak chce vázat.

```
virtual DWORD GetBindInfo() const;
```

### <a name="return-value"></a>Návratová hodnota

Načte nastavení `IBindStatusCallBack`pro . Popis rozhraní naleznete `IBindStatusCallback` v části Sada Windows SDK.

### <a name="remarks"></a>Poznámky

Výchozí implementace nastaví vazbu jako asynchronní, použít paměťové médium (datový proud) a použít model nabízená datových dat. Přepsat tuto funkci, pokud chcete změnit chování vazby.

Jedním z důvodů pro to by bylo vázat pomocí modelu vyžádat data namísto modelu nabízená data. V modelu vyžádat data klient řídí operaci vazby a zástupný název poskytuje pouze data klientovi při čtení. V modelu nabízená data zástupný název řídí operaci asynchronní vazby a průběžně upozorní klienta vždy, když jsou k dispozici nová data.

## <a name="casyncmonikerfilegetbinding"></a><a name="getbinding"></a>CAsyncMonikerFile::GetBinding

Volání této funkce načíst ukazatel na asynchronní přenos vazby.

```
IBinding* GetBinding() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `IBinding` rozhraní poskytované při zahájení asynchronního přenosu. Vrátí hodnotu NULL, pokud z nějakého důvodu nelze přenos provést asynchronně.

### <a name="remarks"></a>Poznámky

To umožňuje řídit proces přenosu dat `IBinding` prostřednictvím rozhraní, `IBinding::Abort` `IBinding::Pause`například `IBinding::Resume`pomocí aplikace , a .

Popis rozhraní naleznete `IBinding` v části Sada Windows SDK.

## <a name="casyncmonikerfilegetformatetc"></a><a name="getformatetc"></a>CAsyncMonikerFile::GetFormatEtc

Volání této funkce načíst formát dat v datovém proudu.

```
FORMATETC* GetFormatEtc() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na strukturu Windows [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) pro aktuálně otevřený datový proud. Vrátí hodnotu NULL, pokud zástupný název nebyl vázán, pokud není asynchronní nebo pokud asynchronní operace nebyla zahájena.

## <a name="casyncmonikerfilegetpriority"></a><a name="getpriority"></a>CAsyncMonikerFile::GetPriority

Volána z klienta asynchronní zástupný název jako proces vazby začne přijímat prioritu danou vlákno pro operaci vazby.

```
virtual LONG GetPriority() const;
```

### <a name="return-value"></a>Návratová hodnota

Priorita, při které bude probíhat asynchronní přenos. Jeden z příznaků priority standardního vlákna: THREAD_PRIORITY_ABOVE_NORMAL, THREAD_PRIORITY_BELOW_NORMAL, THREAD_PRIORITY_HIGHEST, THREAD_PRIORITY_IDLE, THREAD_PRIORITY_LOWEST, THREAD_PRIORITY_NORMAL a THREAD_PRIORITY_TIME_CRITICAL. Popis těchto hodnot naleznete ve funkci Systému Windows [SetThreadPriority.](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority)

### <a name="remarks"></a>Poznámky

`GetPriority`by nemělbýt volán přímo. THREAD_PRIORITY_NORMAL je vrácena výchozí implementací.

## <a name="casyncmonikerfileondataavailable"></a><a name="ondataavailable"></a>CAsyncMonikerFile::OnDataK dispozici

Asynchronní zástupný název volá `OnDataAvailable` poskytnout data klientovi, jakmile bude k dispozici, během operací asynchronní vazby.

```
virtual void OnDataAvailable(DWORD dwSize, DWORD bscfFlag);
```

### <a name="parameters"></a>Parametry

*dwVelikost*<br/>
Kumulativní množství (v bajtech) dat, které jsou k dispozici od začátku vazby. Může být nula, což znamená, že množství dat není relevantní pro operaci, nebo že žádné konkrétní množství k dispozici.

*bscfFlag*<br/>
Hodnota výčtu BSCF. Může se na nich vyvěsit jedna nebo více z následujících hodnot:

- BSCF_FIRSTDATANOTIFICATION Identifikuje první volání `OnDataAvailable` pro danou operaci vazby.

- BSCF_INTERMEDIATEDATANOTIFICATION Identifikuje volání zprostředkovatele `OnDataAvailable` pro operaci vazby.

- BSCF_LASTDATANOTIFICATION Identifikuje poslední volání `OnDataAvailable` pro operaci vazby.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce neprovede žádné provádění. Naleznete v následujícím příkladu pro ukázkovou implementaci.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWinInet#5](../../mfc/codesnippet/cpp/casyncmonikerfile-class_1.cpp)]

## <a name="casyncmonikerfileonlowresource"></a><a name="onlowresource"></a>CAsyncMonikerFile::OnLowResource

Volat zástupný název při nedostatek prostředků.

```
virtual void OnLowResource();
```

### <a name="remarks"></a>Poznámky

Výchozí volání `GetBinding( )-> Abort( )`implementace .

## <a name="casyncmonikerfileonprogress"></a><a name="onprogress"></a>CAsyncMonikerFile::OnProgress

Volat zástupný název opakovaně k označení aktuální průběh této operace vazby, obvykle v přiměřených intervalech během zdlouhavé operace.

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
Označuje očekávanou maximální hodnotu *ulProgress* po `OnProgress` dobu volání pro tuto operaci.

*ulStatusCode*<br/>
Obsahuje další informace týkající se průběhu operace vazby. Platné hodnoty jsou `BINDSTATUS` převzaty z výčtu. Možné hodnoty naleznete v tématu Poznámky.

*szStatusText*<br/>
Informace o aktuálním průběhu v závislosti na hodnotě *ulStatusCode*. Možné hodnoty naleznete v tématu Poznámky.

### <a name="remarks"></a>Poznámky

Možné hodnoty pro *ulStatusCode* (a *szStatusText* pro každou hodnotu) jsou:

|||
|-|-|
|BINDSTATUS_FINDINGRESOURCE  |Operace vazby je hledání prostředku, který obsahuje objekt nebo úložiště je vázán. *SzStatusText* poskytuje zobrazovaný název hledaného prostředku (například "www.microsoft.com").  |
|BINDSTATUS_CONNECTING  |Operace vazby se připojuje k prostředku, který obsahuje objekt nebo úložiště, které je vázáno. *SzStatusText* poskytuje zobrazovaný název prostředku, ke němuž se připojuje (například IP adresa).  |
|BINDSTATUS_SENDINGREQUEST|Operace vazby požaduje, aby byl objekt nebo úložiště vázáno. *SzStatusText* poskytuje zobrazovaný název objektu (například název souboru).|
|BINDSTATUS_REDIRECTING  |Operace vazby byla přesměrována do jiného umístění dat. *SzStatusText* poskytuje zobrazovaný název nového umístění dat.  |
|BINDSTATUS_USINGCACHEDCOPY  |Operace vazby načítá požadovaný objekt nebo úložiště z kopie uložené v mezipaměti. *SzStatusText* je NULL.  |
|BINDSTATUS_BEGINDOWNLOADDATA  |Operace vazby začala přijímat objekt nebo úložiště, ke kterým je vázán. *SzStatusText* poskytuje zobrazovaný název umístění dat.|
|BINDSTATUS_DOWNLOADINGDATA  |Operace vazby nadále přijímá objekt nebo úložiště, ke které je vázáno. *SzStatusText* poskytuje zobrazovaný název umístění dat.  |
|BINDSTATUS_ENDDOWNLOADDATA  |Operace vazby dokončila příjem objektu nebo úložiště, ke kterým je vázán. *SzStatusText* poskytuje zobrazovaný název umístění dat.  |
|BINDSTATUS_CLASSIDAVAILABLE  |Instance objektu, který je vázán na je právě chystá k vytvoření. *SzStatusText* poskytuje CLSID nového objektu ve formátu řetězce, což umožňuje klientovi možnost zrušit operaci vazby, pokud je to žádoucí.  |

## <a name="casyncmonikerfileonstartbinding"></a><a name="onstartbinding"></a>CAsyncMonikerFile::OnStartBinding

Přepsat tuto funkci v odvozených třídách provádět akce při spuštění vazby.

```
virtual void OnStartBinding();
```

### <a name="remarks"></a>Poznámky

Tato funkce je volána zpět zástupný název. Výchozí implementace neprovede žádné provádění.

## <a name="casyncmonikerfileonstopbinding"></a><a name="onstopbinding"></a>CAsyncMonikerFile::OnStopBinding

Volat zástupný název na konci operace vazby.

```
virtual void OnStopBinding(HRESULT hresult, LPCTSTR szError);
```

### <a name="parameters"></a>Parametry

*Hresult*<br/>
HRESULT, která je hodnota chyby nebo upozornění.

*szError*<br/>
Řetězec znaků popisující chybu.

### <a name="remarks"></a>Poznámky

Přepsat tuto funkci provádět akce při zastavení přenosu. Ve výchozím nastavení funkce `IBinding`uvolní .

Popis rozhraní naleznete `IBinding` v části Sada Windows SDK.

## <a name="casyncmonikerfileopen"></a><a name="open"></a>CAsyncMonikerFile::Otevřít

Volání této členské funkce otevřít soubor asynchronně.

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
Ukazatel na soubor, který má být otevřen asynchronně. Soubor může být libovolný platný URL nebo název souboru.

*chyba*<br/>
Ukazatel na výjimky souboru. V případě chyby bude nastavena na příčinu.

*pMoniker*<br/>
Ukazatel na rozhraní asynchronní ho zástupný název `IMoniker`, přesný zástupný název, který je kombinací vlastní zástupný název `IOleClientSite::GetMoniker(OLEWHICHMK_CONTAINER)`dokumentu, který můžete načíst s , a zástupný název vytvořený z názvu cesty. Ovládací prvek můžete použít tento zástupné skupina k vazbě, ale toto není zástupné položky ovládací prvek by měl uložit.

*pBindHost*<br/>
Ukazatel na `IBindHost` rozhraní, které bude použito k vytvoření zástupný název z potenciálně relativní cesty. Pokud je hostitel vazby neplatný nebo neposkytuje zástupný název, volání je výchozí pro `Open(lpszFileName,pError)`. Popis rozhraní naleznete `IBindHost` v části Sada Windows SDK.

*pServiceProvider*<br/>
Ukazatel na `IServiceProvider` rozhraní. Pokud je poskytovatel služeb neplatný nebo `IBindHost`službu neposkytuje `Open(lpszFileName,pError)`, je volání ve výchozím nastavení nastaveno na .

*pNení známo*<br/>
Ukazatel na `IUnknown` rozhraní. Pokud `IServiceProvider` je nalezen, funkce `IBindHost`dotazy pro . Pokud je poskytovatel služeb neplatný nebo `IBindHost`službu neposkytuje `Open(lpszFileName,pError)`, je volání ve výchozím nastavení nastaveno na .

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je soubor úspěšně otevřen; jinak 0.

### <a name="remarks"></a>Poznámky

Toto volání zahájí proces vazby.

Pro parametr *lpszURL* můžete použít adresu URL nebo název souboru. Příklad:

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/casyncmonikerfile-class_2.cpp)]

\-nebo -

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/casyncmonikerfile-class_3.cpp)]

## <a name="see-also"></a>Viz také

[CMonikerFile – třída](../../mfc/reference/cmonikerfile-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CMonikerFile – třída](../../mfc/reference/cmonikerfile-class.md)<br/>
[CDataPathProperty – třída](../../mfc/reference/cdatapathproperty-class.md)
