---
title: "Třída CGopherConnection | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CGopherConnection
- AFXINET/CGopherConnection
- AFXINET/CGopherConnection::CGopherConnection
- AFXINET/CGopherConnection::CreateLocator
- AFXINET/CGopherConnection::GetAttribute
- AFXINET/CGopherConnection::OpenFile
dev_langs: C++
helpviewer_keywords:
- CGopherConnection [MFC], CGopherConnection
- CGopherConnection [MFC], CreateLocator
- CGopherConnection [MFC], GetAttribute
- CGopherConnection [MFC], OpenFile
ms.assetid: b5b96aea-ac99-430e-bd84-d1372b43f78f
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d669ebc954b73d848e22dc373704ab3434074274
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cgopherconnection-class"></a>CGopherConnection – třída
Spravuje vaše připojení k serveru Internet gopher.  
  
> [!NOTE]
>  Třídy `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` a jejich členové jsou zastaralé protože nepracují na platformě Windows XP, ale budou i nadále fungovat na starší operační systémy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CGopherConnection : public CInternetConnection  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CGopherConnection::CGopherConnection](#cgopherconnection)|Vytvoří `CGopherConnection` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CGopherConnection::CreateLocator](#createlocator)|Vytvoří [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) objekt, který chcete najít soubory na gopher serveru.|  
|[CGopherConnection::GetAttribute](#getattribute)|Načte informace o atributu o gopher objektu.|  
|[CGopherConnection::OpenFile](#openfile)|Otevře se soubor gopher.|  
  
## <a name="remarks"></a>Poznámky  
 Službu gopher je jedním ze tří internetové služby rozpoznáno tříd WinInet knihovny MFC.  
  
 Třída `CGopherConnection` obsahuje konstruktor a tři další členské funkce, které spravovat službu gopher: [OpenFile](#openfile), [CreateLocator](#createlocator), a [GetAttribute](#getattribute).  
  
 Pro komunikaci se serverem gopher Internet, musíte nejdřív vytvořit instanci [CInternetSession](../../mfc/reference/cinternetsession-class.md)a pak zavolají [CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection), která vytvoří `CGopherConnection` objekt a vrátí ukazatel na ni. Nikdy vytvoříte `CGopherConnection` objektu přímo.  
  
 Další informace o tom, `CGopherConnection` funguje s ostatní třídy MFC Internetu najdete v článku [Internet programování s WinInet](../../mfc/win32-internet-extensions-wininet.md). Další informace o použití další dvě podporované internetové služby, FTP a HTTP viz třídy [CHttpConnection](../../mfc/reference/chttpconnection-class.md) a [CFtpConnection](../../mfc/reference/cftpconnection-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)  
  
 `CGopherConnection`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxinet.h  
  
##  <a name="cgopherconnection"></a>CGopherConnection::CGopherConnection  
 Tato funkce člen je volána k sestavení `CGopherConnection` objektu.  
  
```  
CGopherConnection(
    CInternetSession* pSession,  
    HINTERNET hConnected,  
    LPCTSTR pstrServer,  
    DWORD_PTR dwContext);

 
CGopherConnection(
    CInternetSession* pSession,  
    LPCTSTR pstrServer,  
    LPCTSTR pstrUserName = NULL,  
    LPCTSTR pstrPassword = NULL,  
    DWORD_PTR dwContext = 0,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```  
  
### <a name="parameters"></a>Parametry  
 `pSession`  
 Ukazatel na související [CInternetSession](../../mfc/reference/cinternetsession-class.md) objektu.  
  
 `hConnected`  
 Popisovač Windows aktuální relace Internetu.  
  
 `pstrServer`  
 Ukazatel na řetězec obsahující název serveru FTP.  
  
 `dwContext`  
 Identifikátor kontextu pro danou operaci. `dwContext`identifikuje vrácené informace o stavu operace [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback). Ve výchozím nastavení je 1; však můžete explicitně přiřadit konkrétní kontext ID pro operaci. Objekt a všechny práce, kterou dělá bude spojený s ID tohoto kontextu.  
  
 `pstrUserName`  
 Ukazatel na řetězec ukončené hodnotou null, který určuje jméno uživatele k přihlášení. Pokud **NULL**, výchozí hodnota je anonymní.  
  
 `pstrPassword`  
 Ukazatel na řetězec ukončené hodnotou null, který určuje heslo pro použití k protokolování. Pokud oba `pstrPassword` a `pstrUserName` jsou **NULL**, výchozí anonymního hesla je uživatelské jméno e-mailu. Pokud `pstrPassword` je **NULL** (nebo prázdný řetězec), ale `pstrUserName` není **NULL**, se používá prázdné heslo. Následující tabulka popisuje chování čtyři možné nastavení `pstrUserName` a `pstrPassword`:  
  
|`pstrUserName`|`pstrPassword`|Uživatelské jméno odeslané na FTP server|Heslo odeslat na FTP server|  
|--------------------|--------------------|---------------------------------|---------------------------------|  
|**NULL** nebo ""|**NULL** nebo ""|"anonymní"|Uživatelské jméno e-mailu|  
|Není- **NULL** řetězec|**NULL** nebo ""|`pstrUserName`|" "|  
|**NULL** jinou hodnotu než **NULL** řetězec|**CHYBA**|**CHYBA**||  
|Není- **NULL** řetězec|Není- **NULL** řetězec|`pstrUserName`|`pstrPassword`|  
  
 `nPort`  
 Číslo, které identifikuje port TCP/IP použít na serveru.  
  
### <a name="remarks"></a>Poznámky  
 Nikdy vytvoříte `CGopherConnection` přímo. Místo toho volat [CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection), která vytvoří `CGopherConnection` objektu a vrátí ukazatel na ni.  
  
##  <a name="createlocator"></a>CGopherConnection::CreateLocator  
 Volání této funkce člen vytvořit lokátor gopher najít nebo soubor na serveru gopher identifikovat.  
  
```  
CGopherLocator CreateLocator(
    LPCTSTR pstrDisplayString,  
    LPCTSTR pstrSelectorString,  
    DWORD dwGopherType);  
  
static CGopherLocator CreateLocator(LPCTSTR pstrLocator);

 
static CGopherLocator CreateLocator(
    LPCTSTR pstrServerName,  
    LPCTSTR pstrDisplayString,  
    LPCTSTR pstrSelectorString,  
    DWORD dwGopherType,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```  
  
### <a name="parameters"></a>Parametry  
 `pstrDisplayString`  
 Ukazatel na řetězec, který obsahuje název dokumentu gopher nebo adresáře, které mají být načteny. Pokud `pstrDisplayString` parametr **NULL**, je vrácen výchozí adresář pro gopher server.  
  
 `pstrSelectorString`  
 Ukazatel na řetězec selektor k odeslání na server gopher za účelem načtení položku. `pstrSelectorString`může být **NULL**.  
  
 *dwGopherType*  
 Tato hodnota určuje, zda `pstrSelectorString` odkazuje na adresář nebo dokumentu, a zda je žádost gopher nebo gopher +. Najdete v části atributy pro strukturu [GOPHER_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa384215) ve Windows SDK.  
  
 `pstrLocator`  
 Ukazatel na řetězec, který určuje soubor otevřete. Obecně platí, tento řetězec je vrácená z volání [CGopherFileFind::GetLocator](../../mfc/reference/cgopherfilefind-class.md#getlocator).  
  
 *pstrServerName*  
 Ukazatel na řetězec obsahující název serveru gopher.  
  
 `nPort`  
 Číslo identifikující port Internetu pro toto připojení.  
  
### <a name="return-value"></a>Návratová hodnota  
 A [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) objektu.  
  
### <a name="remarks"></a>Poznámky  
 Statické verzi – členská funkce vyžaduje, abyste zadejte server, zatímco verze nestatické používá název serveru z objekt připojení.  
  
 K načtení informací ze serveru gopher, musíte aplikaci nejprve získat lokátoru gopher. Aplikace musí pak považovat za Lokátor neprůhledného token (to znamená, aplikace můžete použít Lokátor, ale ne přímo pracovat s nebo jejímu porovnání). Za normálních okolností aplikace používá Lokátor pro volání [CGopherFileFind::FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile) – členská funkce načíst konkrétní informace.  
  
##  <a name="getattribute"></a>CGopherConnection::GetAttribute  
 Volání této funkce člen načíst ze serveru gopher konkrétní atribut informace o položce.  
  
```  
BOOL GetAttribute(
    CGopherLocator& refLocator    CString strRequestedAttributes,  
    CString& strResult,);
```  
  
### <a name="parameters"></a>Parametry  
 `refLocator`  
 Odkaz na [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) objektu.  
  
 *strRequestedAttributes*  
 Oddělených mezerami řetězec určující názvy požadované atributy.  
  
 `strResult`  
 Odkaz na [CString](../../atl-mfc-shared/reference/cstringt-class.md) která přijme Typ lokátoru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0. Pokud volání selže, funkce Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) může být volána a zjistěte příčinu této chyby.  
  
##  <a name="openfile"></a>CGopherConnection::OpenFile  
 Volání této funkce člen otevřít soubor na serveru gopher.  
  
```  
CGopherFile* OpenFile(
    CGopherLocator& refLocator,  
    DWORD dwFlags = 0,  
    LPCTSTR pstrView = NULL,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>Parametry  
 `refLocator`  
 Odkaz na [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) objektu.  
  
 `dwFlags`  
 Libovolnou kombinaci INTERNET_FLAG_ * příznaky. V tématu [CInternetSession::OpenUrl](../../mfc/reference/cinternetsession-class.md#openurl) Další informace o INTERNET_FLAG_\* příznaky.  
  
 `pstrView`  
 Ukazatel na řetězec zobrazení souboru. Pokud existuje několik zobrazení souboru na serveru, tento parametr určuje zobrazení, které soubor otevřít. Pokud `pstrView` je **NULL**, se používá výchozí zobrazení souboru.  
  
 `dwContext`  
 ID kontextu pro otevíraný soubor. V tématu **poznámky** Další informace o `dwContext`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [CGopherFile](../../mfc/reference/cgopherfile-class.md) objekt, který chcete otevřít.  
  
### <a name="remarks"></a>Poznámky  
 Přepsání `dwContext` výchozí identifikátor kontextu nastavit na hodnotu dle vlastního výběru. Identifikátor kontextu je přidružen tento konkrétní operace `CGopherConnection` objekt vytvořený jeho [CInternetSession](../../mfc/reference/cinternetsession-class.md) objektu. Hodnota je vrácen do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) poskytovat stav na operace, pomocí kterého se identifikuje. Najdete v článku [první kroky Internet: WinInet](../../mfc/wininet-basics.md) Další informace o kontextu identifikátor.  
  
## <a name="see-also"></a>Viz také  
 [CInternetConnection – třída](../../mfc/reference/cinternetconnection-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CFtpConnection – třída](../../mfc/reference/cftpconnection-class.md)   
 [CHttpConnection – třída](../../mfc/reference/chttpconnection-class.md)   
 [CInternetConnection – třída](../../mfc/reference/cinternetconnection-class.md)   
 [CGopherLocator – třída](../../mfc/reference/cgopherlocator-class.md)   
 [CGopherFile – třída](../../mfc/reference/cgopherfile-class.md)   
 [CInternetSession – třída](../../mfc/reference/cinternetsession-class.md)
