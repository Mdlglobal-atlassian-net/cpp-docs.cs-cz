---
title: "Třída CAsyncMonikerFile | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 546e251f3387175812e6ba7f8cfed5d8a878d658
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="casyncmonikerfile-class"></a>CAsyncMonikerFile – třída
Poskytuje funkce pro použití asynchronní monikery v ovládacích prvcích ActiveX (dříve OLE prvky).  
  
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
|[CAsyncMonikerFile::GetBinding](#getbinding)|Načte ukazatel asynchronní přenos vazby.|  
|[CAsyncMonikerFile::GetFormatEtc](#getformatetc)|Načte formátu dat v datovém proudu.|  
|[CAsyncMonikerFile::Open](#open)|Otevře soubor asynchronně.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAsyncMonikerFile::CreateBindStatusCallback](#createbindstatuscallback)|Vytvoří objekt COM, který implementuje `IBindStatusCallback`.|  
|[CAsyncMonikerFile::GetBindInfo](#getbindinfo)|Voláno rozhraním OLE systému knihovnu, která se informace o požadavku na typ vazby, který se má vytvořit.|  
|[CAsyncMonikerFile::GetPriority](#getpriority)|Voláno rozhraním OLE systémová knihovna získat prioritu vazby.|  
|[CAsyncMonikerFile::OnDataAvailable](#ondataavailable)|Volá se poskytující data, jakmile je k dispozici klientovi během operací asynchronní vazby.|  
|[CAsyncMonikerFile::OnLowResource](#onlowresource)|Voláno, pokud mají nedostatek prostředků.|  
|[CAsyncMonikerFile::OnProgress](#onprogress)|Voláno k určení průběhu na datech proces stahování.|  
|[CAsyncMonikerFile::OnStartBinding](#onstartbinding)|Voláno, pokud je spuštění vazby.|  
|[CAsyncMonikerFile::OnStopBinding](#onstopbinding)|Voláno, když je zastavena asynchronního přenosu.|  
  
## <a name="remarks"></a>Poznámky  
 Odvozené od [CMonikerFile](../../mfc/reference/cmonikerfile-class.md), který je zase odvozen z [COleStreamFile](../../mfc/reference/colestreamfile-class.md), `CAsyncMonikerFile` používá [imoniker –](http://msdn.microsoft.com/library/windows/desktop/ms679705) rozhraní pro přístup k žádné datový proud asynchronně včetně asynchronní načítání souborů z adresy URL. Soubory lze datapath vlastností ovládacích prvků ActiveX.  
  
 Asynchronní monikery se používají primárně v internetových aplikací a ovládací prvky ActiveX zajistit reagující uživatelské rozhraní během přenosu souborů. Typickým příkladem toho je použití [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md) zajistit asynchronní vlastnosti pro ovládací prvky ActiveX. `CDataPathProperty` Objekt opakovaně získají zpětného volání k označení dostupnost nových dat systému exchange během zdlouhavé vlastnost.  
  
 Další informace o tom, jak použít asynchronní monikery a ovládací prvky ActiveX v internetových aplikací najdete v následujících článcích:  
  
- [Internetu první kroky: Asynchronní Monikery](../../mfc/asynchronous-monikers-on-the-internet.md)  
  
- [Internet první kroky: Ovládací prvky ActiveX](../../mfc/activex-controls-on-the-internet.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Cfile –](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 [CMonikerFile](../../mfc/reference/cmonikerfile-class.md)  
  
 `CAsyncMonikerFile`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxole.h  
  
##  <a name="casyncmonikerfile"></a>CAsyncMonikerFile::CAsyncMonikerFile  
 Vytvoří `CAsyncMonikerFile` objektu.  
  
```  
CAsyncMonikerFile();
```  
  
### <a name="remarks"></a>Poznámky  
 Nedojde k vytvoření `IBindHost` rozhraní. `IBindHost`se používá pouze v případě, že ho zadáte **otevřete** – členská funkce.  
  
 Popis `IBindHost` rozhraní, najdete v části Windows SDK.  
  
##  <a name="close"></a>CAsyncMonikerFile::Close  
 Volání této funkce zavřete a uvolní všechny prostředky.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Poznámky  
 Je možné volat na soubory vyberte nebo již uzavřené.  
  
##  <a name="createbindstatuscallback"></a>CAsyncMonikerFile::CreateBindStatusCallback  
 Vytvoří objekt COM, který implementuje `IBindStatusCallback`.  
  
```  
virtual IUnknown* CreateBindStatusCallback(IUnknown* pUnkControlling);
```  
  
### <a name="parameters"></a>Parametry  
 `pUnkControlling`  
 Ukazatel na řízení neznámý (vnější **IUnknown**) nebo **NULL** Pokud agregace není používán.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud `pUnkControlling` není **NULL**, funkce vrátí ukazatel k vnitřnímu **IUnknown** na nový objekt COM podporu `IBindStatusCallback`. Pokud `pUnkControlling` je **NULL**, funkce vrátí hodnotu ukazatel na **IUnknown** na nový objekt COM podporu `IBindStatusCallback`.  
  
### <a name="remarks"></a>Poznámky  
 `CAsyncMonikerFile`vyžaduje objektu COM, který implementuje `IBindStatusCallback`. MFC implementuje takového objektu a je agregovatelné. Můžete přepsat `CreateBindStatusCallback` vrátit vlastního objektu COM. Objektu COM můžete agregovat implementace MFC voláním `CreateBindStatusCallback` s řízení Neznámý objektu COM. COM – objekty implementovaná pomocí `CCmdTarget` Podpora COM můžete načíst řízení neznámé pomocí **CCmdTarget::GetControllingUnknown**.  
  
 Alternativně můžete delegovat objektu COM na implementace MFC voláním **CreateBindStatusCallback (NULL)**.  
  
 [CAsyncMonikerFile::Open](#open) volání `CreateBindStatusCallback`.  
  
 Další informace o asynchronní monikery a asynchronní vazby najdete v tématu [IBindStatusCallback](http://msdn.microsoft.com/library/ie/ms775060) rozhraní a [pracovní úložiště a jak asynchronní vazeb](http://msdn.microsoft.com/library/windows/desktop/aa379152). Informace agregace, naleznete v [agregace](http://msdn.microsoft.com/library/windows/desktop/ms686558). Všechny tři témata jsou ve Windows SDK.  
  
##  <a name="getbindinfo"></a>CAsyncMonikerFile::GetBindInfo  
 Volá se z klienta asynchronní Přezdívka říct asynchronní Přezdívka jak chce vytvořit vazbu.  
  
```  
virtual DWORD GetBindInfo() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Načte nastavení pro **IBindStatusCallBack**. Popis `IBindStatusCallback` rozhraní, najdete v části Windows SDK.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace nastaví vazbu jako asynchronní, k používání úložiště střední (datový proud) a použít model data push. Tato funkce přepsání, pokud chcete změnit chování vazby.  
  
 Jedním z důvodů to může být vytvořit vazbu pomocí model data pull místo model data push. Ve model vyžádání dat klienta jednotky operaci vazby a Přezdívka pouze poskytuje data pro klienta, pokud je pro čtení. Ve model datová oznámení Přezdívka jednotky operace asynchronní vazby a průběžně upozorní klient vždy, když je k dispozici nová data.  
  
##  <a name="getbinding"></a>CAsyncMonikerFile::GetBinding  
 Volání této funkce načíst ukazatel na asynchronní přenos vazby.  
  
```  
IBinding* GetBinding() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `IBinding` rozhraní dodané zahájení asynchronního přenosu. Vrátí **NULL** Pokud z nějakého důvodu nelze asynchronně provádí převod.  
  
### <a name="remarks"></a>Poznámky  
 To vám umožní řídit proces prostřednictvím pro přenos dat `IBinding` rozhraní, například s **IBinding::Abort**, **IBinding::Pause**, a **IBinding::Resume**.  
  
 Popis `IBinding` rozhraní, najdete v části Windows SDK.  
  
##  <a name="getformatetc"></a>CAsyncMonikerFile::GetFormatEtc  
 Volání této funkce načíst formát dat v datovém proudu.  
  
```  
FORMATETC* GetFormatEtc() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na strukturu Windows [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) pro aktuálně otevřenou datového proudu. Vrátí **NULL** Pokud Přezdívka nebyla byla svázána, pokud není asynchronní, nebo pokud ještě nebylo spuštěno asynchronní operaci.  
  
##  <a name="getpriority"></a>CAsyncMonikerFile::GetPriority  
 Vyvolání z klienta asynchronní Přezdívka spustí proces vytváření vazby pro příjem přednostně vlákno pro operace vazby.  
  
```  
virtual LONG GetPriority() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Priorita, kdy bude asynchronní přenos probíhat. Jeden z příznaků priority standardní vláken: **THREAD_PRIORITY_ABOVE_NORMAL**, **THREAD_PRIORITY_BELOW_NORMAL**, **THREAD_PRIORITY_HIGHEST**,  **THREAD_PRIORITY_IDLE**, **THREAD_PRIORITY_LOWEST**, **THREAD_PRIORITY_NORMAL**, a **THREAD_PRIORITY_TIME_CRITICAL**. Najdete v části funkce systému Windows [SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277) popis tyto hodnoty.  
  
### <a name="remarks"></a>Poznámky  
 `GetPriority`nelze volat přímo. **THREAD_PRIORITY_NORMAL** je vrácen výchozí implementace.  
  
##  <a name="ondataavailable"></a>CAsyncMonikerFile::OnDataAvailable  
 Volá asynchronní Přezdívka `OnDataAvailable` poskytování dat pro klienta, jakmile je k dispozici, vazby během asynchronní operace.  
  
```  
virtual void OnDataAvailable(DWORD dwSize, DWORD bscfFlag);
```  
  
### <a name="parameters"></a>Parametry  
 `dwSize`  
 Kumulativní velikost (v bajtech) k dispozici od začátku vazby data. Může být nula, která určuje, že množství dat, se nevztahuje na operaci nebo že jsou k dispozici žádné určitou velikostí.  
  
 *bscfFlag*  
 A **BSCF** hodnota výčtu. Může být jeden nebo více z následujících hodnot:  
  
- **BSCF_FIRSTDATANOTIFICATION** identifikuje první volání `OnDataAvailable` operace dané vazby.  
  
- **BSCF_INTERMEDIATEDATANOTIFICATION** identifikuje zprostředkující volání `OnDataAvailable` operace vazby.  
  
- **BSCF_LASTDATANOTIFICATION** identifikuje poslední volání `OnDataAvailable` operace vazby.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace této funkce neprovede žádnou akci. Podívejte se na následující příklad pro implementaci ukázka.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWinInet#5](../../mfc/codesnippet/cpp/casyncmonikerfile-class_1.cpp)]  
  
##  <a name="onlowresource"></a>CAsyncMonikerFile::OnLowResource  
 Voláno rozhraním Přezdívka po nízkou prostředky.  
  
```  
virtual void OnLowResource();
```  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace volá `GetBinding( )-> Abort( )`.  
  
##  <a name="onprogress"></a>CAsyncMonikerFile::OnProgress  
 Voláno rozhraním Přezdívka opakovaně udávajících aktuální průběh této operace vazby, obvykle v přiměřené intervalech během časově náročná operace.  
  
```  
virtual void OnProgress(
    ULONG ulProgress,  
    ULONG ulProgressMax,  
    ULONG ulStatusCode,  
    LPCTSTR szStatusText);
```  
  
### <a name="parameters"></a>Parametry  
 `ulProgress`  
 Označuje aktuální průběh operace vazby relativně k očekávané maximální uvedené v `ulProgressMax`.  
  
 `ulProgressMax`  
 Označuje očekávaný maximální hodnota, která `ulProgress` po dobu trvání volání `OnProgress` pro tuto operaci.  
  
 `ulStatusCode`  
 Poskytuje další informace týkající se průběh operace vazby. Platné hodnoty jsou převzaty z `BINDSTATUS` výčtu. Možné hodnoty najdete v části poznámky.  
  
 `szStatusText`  
 Informace o aktuální průběh, v závislosti na hodnotě `ulStatusCode`. Možné hodnoty najdete v části poznámky.  
  
### <a name="remarks"></a>Poznámky  
 Možné hodnoty `ulStatusCode` (a `szStatusText` pro každou hodnotu) jsou:  
  
 **BINDSTATUS_FINDINGRESOURCE**  
 Operace vytvoření vazby je hledání prostředku, který obsahuje objekt nebo úložiště je vázána na. `szStatusText` Poskytuje zobrazovaný název prostředku prohledávaný (například "www.microsoft.com").  
  
 **BINDSTATUS_CONNECTING**  
 Operace vytvoření vazby se připojuje k prostředku, který obsahuje objekt nebo úložiště je vázána na. `szStatusText` Poskytuje zobrazovaný název prostředku připojené k (například IP adresy).  
  
 **BINDSTATUS_SENDINGREQUEST**  
 Operace vytvoření vazby požaduje objekt nebo úložiště je vázána na. `szStatusText` Poskytuje zobrazovaný název objektu (například název souboru).  
  
 **BINDSTATUS_REDIRECTING**  
 Operace vytvoření vazby byl přesměrován do různých datových umístění. `szStatusText` Poskytuje zobrazovaný název nového umístění data.  
  
 **BINDSTATUS_USINGCACHEDCOPY**  
 Operace vytvoření vazby načítá požadovaný objekt nebo úložiště z kopie v mezipaměti. `szStatusText` Je **NULL**.  
  
 **BINDSTATUS_BEGINDOWNLOADDATA**  
 Přijetí objekt nebo úložiště je vázána na zahájení operace vazby. `szStatusText` Poskytuje zobrazovaný název umístění dat.  
  
 **BINDSTATUS_DOWNLOADINGDATA**  
 Operace vytvoření vazby i nadále přijímat úložiště je vázána na objekt. `szStatusText` Poskytuje zobrazovaný název umístění dat.  
  
 **BINDSTATUS_ENDDOWNLOADDATA**  
 Operace vytvoření vazby dokončil přijetí úložiště je vázána na objekt. `szStatusText` Poskytuje zobrazovaný název umístění dat.  
  
 **BINDSTATUS_CLASSIDAVAILABLE**  
 Instance objektu je svázán, je jenom o který se má vytvořit. `szStatusText` Poskytuje CLSID nového objektu ve formátu řetězce, a umožnil tak klientovi příležitost ke zrušení operace vazby, v případě potřeby.  
  
##  <a name="onstartbinding"></a>CAsyncMonikerFile::OnStartBinding  
 Potlačí tuto funkci v odvozených tříd pro provádění akcí po spuštění vazby.  
  
```  
virtual void OnStartBinding();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je volána zpět přezdívka. Výchozí implementace neprovede žádnou akci.  
  
##  <a name="onstopbinding"></a>CAsyncMonikerFile::OnStopBinding  
 Voláno rozhraním Přezdívka na konci operace vazby.  
  
```  
virtual void OnStopBinding(HRESULT hresult, LPCTSTR szError);
```  
  
### <a name="parameters"></a>Parametry  
 `hresult`  
 `HRESULT` Tohoto problému je chyba nebo hodnotu pro upozornění.  
  
 *szErrort*  
 Řetězec znaků popisující chybu.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto funkci k provádění akcí při přenosu je zastavena. Ve výchozím nastavení, funkce uvolní `IBinding`.  
  
 Popis `IBinding` rozhraní, najdete v části Windows SDK.  
  
##  <a name="open"></a>CAsyncMonikerFile::Open  
 Volání této funkce člen a otevřete soubor asynchronně.  
  
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
 `lpszURL`  
 Ukazatel na soubor otevřít asynchronně. Soubor může být platná adresa URL nebo název souboru.  
  
 `pError`  
 Ukazatel na soubor výjimky. V případě chyby nastaví se na příčinu.  
  
 `pMoniker`  
 Ukazatel rozhraní asynchronní Přezdívka `IMoniker`, přesné přezdívka, který je kombinací Přezdívka dokumentu vlastní, který může načíst s **IOleClientSite::GetMoniker (** *OLEWHICHMK_ KONTEJNER* **)**a moniker vytvořené z název cesty. Ovládací prvek můžete použít tento Přezdívka pro vazbu, ale nejedná se o Přezdívka měli uložit ovládacího prvku.  
  
 *pBindHost*  
 Ukazatel `IBindHost` rozhraní, které se použije k vytvoření Přezdívka z potenciálně relativní cesta. Pokud hostitel vazby je neplatný nebo neposkytuje přezdívka, volání výchozí **otevřete (** `lpszFileName` **,**`pError`**)**. Popis `IBindHost` rozhraní, najdete v části Windows SDK.  
  
 `pServiceProvider`  
 Ukazatel `IServiceProvider` rozhraní. Pokud na poskytovatele služby je neplatný, nebo neposkytne službu pro `IBindHost`, použije se výchozí hodnota volání **otevřete (** `lpszFileName` **,**`pError`**)**.  
  
 *pUnknown*  
 Ukazatel **IUnknown** rozhraní. Pokud `IServiceProvider` nenajde, dotazy funkce pro `IBindHost`. Pokud na poskytovatele služby je neplatný, nebo neposkytne službu pro `IBindHost`, použije se výchozí hodnota volání **otevřete (** `lpszFileName` **,**`pError`**)**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je soubor otevřít úspěšně; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Toto volání zahájí proces vytváření vazby.  
  
 Můžete použít adresu URL nebo název souboru pro `lpszURL` parametr. Příklad:  
  
 [!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/casyncmonikerfile-class_2.cpp)]  
  
 - nebo –  
  
 [!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/casyncmonikerfile-class_3.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [CMonikerFile – třída](../../mfc/reference/cmonikerfile-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CMonikerFile – třída](../../mfc/reference/cmonikerfile-class.md)   
 [CDataPathProperty – třída](../../mfc/reference/cdatapathproperty-class.md)
