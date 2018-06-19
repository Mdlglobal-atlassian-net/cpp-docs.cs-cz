---
title: Třída CFtpConnection | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFtpConnection
- AFXINET/CFtpConnection
- AFXINET/CFtpConnection::CFtpConnection
- AFXINET/CFtpConnection::Command
- AFXINET/CFtpConnection::CreateDirectory
- AFXINET/CFtpConnection::GetCurrentDirectory
- AFXINET/CFtpConnection::GetCurrentDirectoryAsURL
- AFXINET/CFtpConnection::GetFile
- AFXINET/CFtpConnection::OpenFile
- AFXINET/CFtpConnection::PutFile
- AFXINET/CFtpConnection::Remove
- AFXINET/CFtpConnection::RemoveDirectory
- AFXINET/CFtpConnection::Rename
- AFXINET/CFtpConnection::SetCurrentDirectory
dev_langs:
- C++
helpviewer_keywords:
- CFtpConnection [MFC], CFtpConnection
- CFtpConnection [MFC], Command
- CFtpConnection [MFC], CreateDirectory
- CFtpConnection [MFC], GetCurrentDirectory
- CFtpConnection [MFC], GetCurrentDirectoryAsURL
- CFtpConnection [MFC], GetFile
- CFtpConnection [MFC], OpenFile
- CFtpConnection [MFC], PutFile
- CFtpConnection [MFC], Remove
- CFtpConnection [MFC], RemoveDirectory
- CFtpConnection [MFC], Rename
- CFtpConnection [MFC], SetCurrentDirectory
ms.assetid: 5e3a0501-8893-49cf-a3d5-0628d8d6b936
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f43df1cb610c785688db982be2ddc4a19cf140b2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33374533"
---
# <a name="cftpconnection-class"></a>CFtpConnection – třída
Spravuje připojení k serveru FTP na Internet server a umožňuje přímé manipulaci adresářů a souborů na tomto serveru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CFtpConnection : public CInternetConnection  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CFtpConnection::CFtpConnection](#cftpconnection)|Vytvoří `CFtpConnection` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CFtpConnection::Command](#command)|Odešle příkaz přímo k serveru FTP.|  
|[CFtpConnection::CreateDirectory](#createdirectory)|Vytvoří adresář na serveru.|  
|[CFtpConnection::GetCurrentDirectory](#getcurrentdirectory)|Získá aktuální adresář pro toto připojení.|  
|[CFtpConnection::GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl)|Získá aktuální adresář pro toto připojení jako adresu URL.|  
|[CFtpConnection::GetFile](#getfile)|Získá soubor ze serveru připojeného|  
|[CFtpConnection::OpenFile](#openfile)|Otevře soubor na serveru připojený.|  
|[CFtpConnection::PutFile](#putfile)|Umístí soubor na serveru.|  
|[CFtpConnection::Remove](#remove)|Odebere soubor ze serveru.|  
|[CFtpConnection::RemoveDirectory](#removedirectory)|Zadaný adresář se odebere ze serveru.|  
|[CFtpConnection::Rename](#rename)|Přejmenuje soubor na serveru.|  
|[CFtpConnection::SetCurrentDirectory](#setcurrentdirectory)|Nastaví aktuální adresář serveru FTP.|  
  
## <a name="remarks"></a>Poznámky  
 FTP je jedním ze tří rozpoznáno tříd WinInet knihovny MFC služeb sítě Internet.  
  
 Ke komunikaci se serverem FTP Internet, musíte nejdřív vytvořit instanci [CInternetSession](../../mfc/reference/cinternetsession-class.md)a pak vytvořte `CFtpConnection` objektu. Nikdy vytvoříte `CFtpConnection` objektu přímo; místo toho volat [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection), která vytvoří `CFtpConnection` objektu a vrátí ukazatel na ni.  
  
 Další informace o tom, `CFtpConnection` funguje s ostatní třídy MFC Internetu najdete v článku [Internet programování s WinInet](../../mfc/win32-internet-extensions-wininet.md). Další informace o komunikaci s další dvě podporované služby, HTTP a gopher, viz třídy [CHttpConnection](../../mfc/reference/chttpconnection-class.md) a [CGopherConnection](../../mfc/reference/cgopherconnection-class.md).  
  
## <a name="example"></a>Příklad  
  Podívejte se na příklad v [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) přehledu třídy.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)  
  
 `CFtpConnection`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxinet.h  
  
##  <a name="cftpconnection"></a>  CFtpConnection::CFtpConnection  
 Tato funkce člen je volána k sestavení `CFtpConnection` objektu.  
  
```  
CFtpConnection(
    CInternetSession* pSession,  
    HINTERNET hConnected,  
    LPCTSTR pstrServer,  
    DWORD_PTR dwContext);

 
CFtpConnection(
    CInternetSession* pSession,  
    LPCTSTR pstrServer,  
    LPCTSTR pstrUserName = NULL,  
    LPCTSTR pstrPassword = NULL,  
    DWORD_PTR dwContext = 0,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,  
    BOOL bPassive = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `pSession`  
 Ukazatel na související [CInternetSession](../../mfc/reference/cinternetsession-class.md) objektu.  
  
 `hConnected`  
 Popisovač Windows aktuální relace Internetu.  
  
 `pstrServer`  
 Ukazatel na řetězec obsahující název serveru FTP.  
  
 `dwContext`  
 Identifikátor kontextu pro danou operaci. `dwContext` identifikuje vrácené informace o stavu operace [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback). Ve výchozím nastavení je 1; však můžete explicitně přiřadit konkrétní kontext ID pro operaci. Objekt a všechny práce, kterou dělá bude spojený s ID tohoto kontextu.  
  
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
  
 `bPassive`  
 Určuje režim pasivní nebo aktivní pro tuto relaci FTP. Pokud nastavena na **TRUE**, nastaví rozhraní API Win32 `dwFlag` k **INTERNET_FLAG_PASSIVE**.  
  
### <a name="remarks"></a>Poznámky  
 Nikdy vytvoříte `CFtpConnection` objektu přímo. Místo toho volat [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection), která vytvoří **CFptConnection** objektu.  
  
##  <a name="command"></a>  CFtpConnection::Command  
 Odešle příkaz přímo k serveru FTP.  
  
```  
CInternetFile* Command(
    LPCTSTR pszCommand,  
    CmdResponseType eResponse = CmdRespNone,  
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>Parametry  
 `pszCommand`  
 Ukazatel na řetězec, který obsahuje příkaz k odeslání.  
  
 *eResponse*  
 Určuje, zda je očekáván odpověď ze serveru FTP. Může být jedna z následujících hodnot:  
  
- **CmdRespNone** žádná odpověď se očekává.  
  
- **CmdRespRead** odpověď se očekává.  
  
 `dwFlags`  
 Hodnota obsahující příznaky, které řídí funkce. Úplný seznam najdete v tématu [FTPCommand](http://msdn.microsoft.com/library/windows/desktop/aa384133).  
  
 `dwContext`  
 Ukazatel na hodnotu obsahující hodnotu definované aplikací umožňují určit kontext aplikace ve zpětných volání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen emuluje funkce [FTPCommand](http://msdn.microsoft.com/library/windows/desktop/aa384133) fungovat, jak je popsáno v sadě Windows SDK.  
  
 Pokud dojde k chybě, MFC vyvolá výjimku typu [CInternetException](../../mfc/reference/cinternetexception-class.md).  
  
##  <a name="createdirectory"></a>  CFtpConnection::CreateDirectory  
 Volání této funkce člen k vytvoření adresáře na serveru připojený.  
  
```  
BOOL CreateDirectory(LPCTSTR pstrDirName);
```  
  
### <a name="parameters"></a>Parametry  
 `pstrDirName`  
 Ukazatel na řetězec, který obsahuje název adresáře pro vytvoření.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0. Pokud volání selže, funkce systému Windows [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) může být volána a zjistěte příčinu této chyby.  
  
### <a name="remarks"></a>Poznámky  
 Použití `GetCurrentDirectory` k určení aktuální pracovní adresář pro toto připojení k serveru. Není Předpokládejme, že vzdálený systém, můžete je připojený ke kořenový adresář.  
  
 `pstrDirName` Parametr může být buď částečně nebo plně kvalifikovaný název souboru vůči aktuálnímu adresáři. Zpětné lomítko (\\) nebo jako oddělovače adresář pro buď název lze použít lomítko (/). `CreateDirectory` Před použitím, překládá oddělovačů název adresáře na příslušné znaků.  
  
##  <a name="getcurrentdirectory"></a>  CFtpConnection::GetCurrentDirectory  
 Volání této funkce člen získat název aktuálního adresáře.  
  
```  
BOOL GetCurrentDirectory(CString& strDirName) const;  
  
BOOL GetCurrentDirectory(
    LPTSTR pstrDirName,  
    LPDWORD lpdwLen) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `strDirName`  
 Odkaz na řetězec, který se zobrazí název adresáře.  
  
 `pstrDirName`  
 Ukazatel na řetězec, který se zobrazí název adresáře.  
  
 `lpdwLen`  
 Ukazatel na DWORD, který obsahuje následující informace:  
  
|||  
|-|-|  
|V položce|Velikost vyrovnávací paměti odkazuje `pstrDirName`.|  
|Při návratu|Počet znaků, které jsou uložené na `pstrDirName`. Pokud – členská funkce selže a je vrácen ERROR_INSUFFICIENT_BUFFER, pak `lpdwLen` obsahuje počet bajtů, které aplikace musí přidělit k přijetí řetězce.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0. Pokud volání selže, funkce Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) může být volána a zjistěte příčinu této chyby.  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li místo toho získat název adresáře jako adresu URL, volejte [GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl).  
  
 Parametry `pstrDirName` nebo `strDirName` může být buď částečně kvalifikované názvy souborů vůči aktuálnímu adresáři nebo plně kvalifikovaný. Zpětné lomítko (\\) nebo jako oddělovače adresář pro buď název lze použít lomítko (/). `GetCurrentDirectory` Před použitím, překládá oddělovačů název adresáře na příslušné znaků.  
  
##  <a name="getcurrentdirectoryasurl"></a>  CFtpConnection::GetCurrentDirectoryAsURL  
 Volání této funkce člen se získat název aktuální adresář jako adresu URL.  
  
```  
BOOL GetCurrentDirectoryAsURL(CString& strDirName) const;  
  
BOOL GetCurrentDirectoryAsURL(
    LPTSTR pstrName,  
    LPDWORD lpdwLen) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `strDirName`  
 Odkaz na řetězec, který se zobrazí název adresáře.  
  
 `pstrDirName`  
 Ukazatel na řetězec, který se zobrazí název adresáře.  
  
 `lpdwLen`  
 Ukazatel na DWORD, který obsahuje následující informace:  
  
|||  
|-|-|  
|V položce|Velikost vyrovnávací paměti odkazuje `pstrDirName`.|  
|Při návratu|Počet znaků, které jsou uložené na `pstrDirName`. Pokud – členská funkce selže a je vrácen ERROR_INSUFFICIENT_BUFFER, pak `lpdwLen` obsahuje počet bajtů, které aplikace musí přidělit k přijetí řetězce.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0. Pokud volání selže, funkce Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) může být volána a zjistěte příčinu této chyby.  
  
### <a name="remarks"></a>Poznámky  
 `GetCurrentDirectoryAsURL` se chová stejně jako [GetCurrentDirectory](#getcurrentdirectory)  
  
 Parametr `strDirName` může být buď částečně kvalifikované názvy souborů vůči aktuálnímu adresáři nebo plně kvalifikovaný. Zpětné lomítko (\\) nebo jako oddělovače adresář pro buď název lze použít lomítko (/). `GetCurrentDirectoryAsURL` Před použitím, překládá oddělovačů název adresáře na příslušné znaků.  
  
##  <a name="getfile"></a>  CFtpConnection::GetFile  
 Volání této funkce člen od serveru FTP získat soubor a uložit v místním počítači.  
  
```  
BOOL GetFile(
    LPCTSTR pstrRemoteFile,  
    LPCTSTR pstrLocalFile,  
    BOOL bFailIfExists = TRUE,  
    DWORD dwAttributes = FILE_ATTRIBUTE_NORMAL,  
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>Parametry  
 `pstrRemoteFile`  
 Ukazatel na ukončené hodnotou null řetězec obsahující název souboru k načtení ze serveru FTP.  
  
 `pstrLocalFile`  
 Ukazatel na ukončené hodnotou null řetězec obsahující název souboru k vytvoření místního systému.  
  
 *bFailIfExists*  
 Určuje, zda název souboru může použít už existující soubor. Pokud název místního souboru již existuje, a tento parametr je **TRUE**, `GetFile` selže. V opačném `GetFile` vymaže existující kopii souboru.  
  
 `dwAttributes`  
 Určuje atributy souboru. To může být libovolnou kombinací následující příznaky FILE_ATTRIBUTE_ *.  
  
-   FILE_ATTRIBUTE_ARCHIVE soubor je soubor archivu. Označení souborů k zálohování nebo odebrání aplikací pomocí tohoto atributu.  
  
-   Se komprimují FILE_ATTRIBUTE_COMPRESSED soubor nebo adresář. Pro soubor komprese znamená, že všechna data v souboru se komprimují. Komprese pro adresář, je výchozí pro nově vytvořené soubory a podadresáře.  
  
-   FILE_ATTRIBUTE_DIRECTORY soubor je adresář.  
  
-   FILE_ATTRIBUTE_NORMAL soubor nemá nastavené žádné jiné atributy. Tento atribut je platný pouze v případě, že použitá samostatně. Všechny ostatní atributy souboru přepsat FILE_ATTRIBUTE_NORMAL:  
  
-   FILE_ATTRIBUTE_HIDDEN souboru je skrytý. Není mají být zahrnuty v seznamu běžných adresářů.  
  
-   FILE_ATTRIBUTE_READONLY soubor je jen pro čtení. Aplikace můžete přečíst soubor, ale nelze do něj zapisovat nebo odstranit.  
  
-   FILE_ATTRIBUTE_SYSTEM soubor je součástí nebo se používá výhradně podle operačního systému.  
  
-   FILE_ATTRIBUTE_TEMPORARY soubor se používá pro dočasné úložiště. Aplikace by měla zapisovat do souboru, pouze pokud je to nezbytně nutné. Většina dat soubor zůstane v paměti bez vyprazdňuje na médium, protože soubor má být odstraněna.  
  
 `dwFlags`  
 Určuje podmínky, za kterých dojde k přenosu. Tento parametr může být libovolná z `dwFlags` hodnoty popsané v [FtpGetFile](http://msdn.microsoft.com/library/windows/desktop/aa384157) ve Windows SDK.  
  
 `dwContext`  
 Identifikátor kontext pro načtení souboru. V tématu **poznámky** Další informace o `dwContext`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0. Pokud volání selže, funkce Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) může být volána a zjistěte příčinu této chyby.  
  
### <a name="remarks"></a>Poznámky  
 `GetFile` je nejdůležitější rutiny, která zpracovává všechny režie spojená s čtení souboru ze serveru FTP a uložena místně. Aplikace, které jenom načítají data souboru nebo Zavřít kontrolu nad přenos souborů, které vyžadují by měly používat `OpenFile` a [CInternetFile::Read](../../mfc/reference/cinternetfile-class.md#read) místo.  
  
 Pokud `dwFlags` je FILE_TRANSFER_TYPE_ASCII, překlad dat souboru taky převede ovládacího prvku a formátování znaků do Windows ekvivalenty. Výchozí přenos je binárního režimu, kde stažení souboru ve stejném formátu, který je uložen na serveru.  
  
 Obě `pstrRemoteFile` a `pstrLocalFile` může být buď částečně kvalifikované názvy souborů vůči aktuálnímu adresáři nebo plně kvalifikovaný. Zpětné lomítko (\\) nebo jako oddělovače adresář pro buď název lze použít lomítko (/). `GetFile` Před použitím, překládá oddělovačů název adresáře na příslušné znaků.  
  
 Přepsání `dwContext` výchozí identifikátor kontextu nastavit na hodnotu dle vlastního výběru. Identifikátor kontextu je přidružen tento konkrétní operace `CFtpConnection` objekt vytvořený jeho [CInternetSession](../../mfc/reference/cinternetsession-class.md) objektu. Hodnota je vrácen do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) poskytovat stav na operace, pomocí kterého se identifikuje. Najdete v článku [první kroky Internet: WinInet](../../mfc/wininet-basics.md) Další informace o kontextu identifikátor.  
  
##  <a name="openfile"></a>  CFtpConnection::OpenFile  
 Volání této funkce člen a otevřete soubor nachází na serveru FTP pro čtení nebo zápis.  
  
```  
CInternetFile* OpenFile(
    LPCTSTR pstrFileName,  
    DWORD dwAccess = GENERIC_READ,  
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>Parametry  
 `pstrFileName`  
 Ukazatel na řetězec, který obsahuje název souboru, který se otevřít.  
  
 *dwAccess*  
 Určuje, jak bude soubor přístupný. Může být všeobecné_čtení nebo všeobecné_zápis, ale ne obojí.  
  
 `dwFlags`  
 Určuje podmínky, za kterých dojde k následné přenosů. To může být libovolná z následující konstanty FTP_TRANSFER_ *:  
  
-   FTP_TRANSFER_TYPE_ASCII soubor přenáší pomocí metody přenos FTP ASCII (typ A). Převede ovládacího prvku a formátování informace do místní ekvivalenty.  
  
-   FTP_TRANSFER_TYPE_BINARY soubor přenáší data pomocí metody přenosu bitové kopie FTP's (typu I). Přenosy dat souboru přesně jako existuje beze změn. Toto je výchozí metodou přenosu.  
  
 `dwContext`  
 Identifikátor kontext pro otevření souboru. V tématu **poznámky** Další informace o `dwContext`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [CInternetFile](../../mfc/reference/cinternetfile-class.md) objektu.  
  
### <a name="remarks"></a>Poznámky  
 `OpenFile` je třeba používat v následujících situacích:  
  
-   Aplikace obsahuje data, která potřebují odesílat a vytvořen jako soubor na serveru FTP, ale, že data nejsou v místním souboru. Jednou `OpenFile` otevře soubor, aplikace používá [CInternetFile::Write](../../mfc/reference/cinternetfile-class.md#write) k odesílání dat souboru FTP na server.  
  
-   Aplikace musí načíst soubor ze serveru a umístěte ji do aplikace řízené paměť, místo zápisu na disk. Aplikace používá [CInternetFile::Read](../../mfc/reference/cinternetfile-class.md#read) po použití `OpenFile` k otevření souboru.  
  
-   Aplikace musí dobře úroveň kontroly nad přenosu souborů. Aplikace může například, chcete-li zobrazit průběh řízení informace o průběhu stavu přenos souboru při stahování souboru.  
  
 Po volání `OpenFile` a dokud volání **CInternetConnection::Close**, aplikace může volat pouze [CInternetFile::Read](../../mfc/reference/cinternetfile-class.md#read), [CInternetFile::Write](../../mfc/reference/cinternetfile-class.md#write), **CInternetConnection::Close**, nebo [CFtpFileFind::FindFile](../../mfc/reference/cftpfilefind-class.md#findfile). Volání funkcí jiných FTP pro stejné relace FTP se nezdaří a nastavit kód chyby na FTP_ETRANSFER_IN_PROGRESS.  
  
 `pstrFileName` Parametr může být buď částečně kvalifikovaný název souboru relativní k aktuálnímu adresáři nebo plně kvalifikovaný. Zpětné lomítko (\\) nebo jako oddělovače adresář pro buď název lze použít lomítko (/). `OpenFile` před jeho použitím překládá oddělovačů název adresáře na příslušné znaků.  
  
 Přepsání `dwContext` výchozí identifikátor kontextu nastavit na hodnotu dle vlastního výběru. Identifikátor kontextu je přidružen tento konkrétní operace `CFtpConnection` objekt vytvořený jeho [CInternetSession](../../mfc/reference/cinternetsession-class.md) objektu. Hodnota je vrácen do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) poskytovat stav na operace, pomocí kterého se identifikuje. Najdete v článku [první kroky Internet: WinInet](../../mfc/wininet-basics.md) Další informace o kontextu identifikátor.  
  
##  <a name="putfile"></a>  CFtpConnection::PutFile  
 Volání této funkce člen uložit soubor na serveru FTP.  
  
```  
BOOL PutFile(
    LPCTSTR pstrLocalFile,  
    LPCTSTR pstrRemoteFile,  
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>Parametry  
 `pstrLocalFile`  
 Ukazatel na řetězec, který obsahuje název souboru k odeslání z místního systému.  
  
 `pstrRemoteFile`  
 Ukazatel na řetězec, který obsahuje název souboru, který se vytvořit na serveru FTP.  
  
 `dwFlags`  
 Určuje podmínky, za kterých dojde k přenosu souboru. Může být konstanty FTP_TRANSFER_ * popsané v [OpenFile](#openfile).  
  
 `dwContext`  
 Identifikátor kontext k umístění souboru. V tématu **poznámky** Další informace o `dwContext`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0. Pokud volání selže, funkce Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) může být volána a zjistěte příčinu této chyby.  
  
### <a name="remarks"></a>Poznámky  
 `PutFile` je nejdůležitější rutiny, která zpracovává všechny operace spojené s ukládání souborů na serveru FTP. Aplikace, která jenom k odesílání dat nebo blíže kontrolu nad přenos souborů, které vyžadují by měly používat [OpenFile](#openfile) a [CInternetFile::Write](../../mfc/reference/cinternetfile-class.md#write).  
  
 Přepsání `dwContext` výchozí identifikátor kontextu nastavit na hodnotu dle vlastního výběru. Identifikátor kontextu je přidružen tento konkrétní operace `CFtpConnection` objekt vytvořený jeho [CInternetSession](../../mfc/reference/cinternetsession-class.md) objektu. Hodnota je vrácen do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) poskytovat stav na operace, pomocí kterého se identifikuje. Najdete v článku [první kroky Internet: WinInet](../../mfc/wininet-basics.md) Další informace o kontextu identifikátor.  
  
##  <a name="remove"></a>  CFtpConnection::Remove  
 Volání této funkce člen odstraňte zadaný soubor z připojeného serveru.  
  
```  
BOOL Remove(LPCTSTR pstrFileName);
```  
  
### <a name="parameters"></a>Parametry  
 `pstrFileName`  
 Ukazatel na řetězec obsahující název souboru, který chcete odebrat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0. Pokud volání selže, funkce Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) může být volána a zjistěte příčinu této chyby.  
  
### <a name="remarks"></a>Poznámky  
 `pstrFileName` Parametr může být buď částečně kvalifikovaný název souboru relativní k aktuálnímu adresáři nebo plně kvalifikovaný. Zpětné lomítko (\\) nebo jako oddělovače adresář pro buď název lze použít lomítko (/). **Odebrat** funkce překládá oddělovačů název adresáře na příslušné znaků před použitím.  
  
##  <a name="removedirectory"></a>  CFtpConnection::RemoveDirectory  
 Volání této funkce člena odebrat ze serveru připojeného zadaný adresář.  
  
```  
BOOL RemoveDirectory(LPCTSTR pstrDirName);
```  
  
### <a name="parameters"></a>Parametry  
 `pstrDirName`  
 Ukazatel na řetězec obsahující adresář, který chcete odebrat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0. Pokud volání selže, funkce Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) může být volána a zjistěte příčinu této chyby.  
  
### <a name="remarks"></a>Poznámky  
 Použití [GetCurrentDirectory](#getcurrentdirectory) k určení serveru aktuální pracovní adresář. Není Předpokládejme, že vzdálený systém, můžete je připojený ke kořenový adresář.  
  
 `pstrDirName` Parametr může být buď částečně nebo plně kvalifikovaný název souboru vůči aktuálnímu adresáři. Zpětné lomítko (\\) nebo jako oddělovače adresář pro buď název lze použít lomítko (/). `RemoveDirectory` Před použitím, překládá oddělovačů název adresáře na příslušné znaků.  
  
##  <a name="rename"></a>  CFtpConnection::Rename  
 Volání této funkce člen přejmenovat zadaný soubor na serveru připojený.  
  
```  
BOOL Rename(
    LPCTSTR pstrExisting,  
    LPCTSTR pstrNew);
```  
  
### <a name="parameters"></a>Parametry  
 `pstrExisting`  
 Ukazatel na řetězec obsahující aktuální název souboru, který se přejmenovat.  
  
 `pstrNew`  
 Ukazatel na řetězec obsahující nový název souboru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0. Pokud volání selže, funkce Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) může být volána a zjistěte příčinu této chyby.  
  
### <a name="remarks"></a>Poznámky  
 `pstrExisting` a `pstrNew` parametry může být buď částečně kvalifikovaný název souboru relativní k aktuálnímu adresáři nebo plně kvalifikovaný. Zpětné lomítko (\\) nebo jako oddělovače adresář pro buď název lze použít lomítko (/). **Přejmenujte** před použitím překládá oddělovačů název adresáře na příslušné znaků.  
  
##  <a name="setcurrentdirectory"></a>  CFtpConnection::SetCurrentDirectory  
 Volání této funkce člen změnit na jiný adresář na serveru FTP.  
  
```  
BOOL SetCurrentDirectory(LPCTSTR pstrDirName);
```  
  
### <a name="parameters"></a>Parametry  
 `pstrDirName`  
 Ukazatel na řetězec, který obsahuje název adresáře.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0. Pokud volání selže, funkce Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) může být volána a zjistěte příčinu této chyby.  
  
### <a name="remarks"></a>Poznámky  
 `pstrDirName` Parametr může být buď částečně nebo plně kvalifikovaný název souboru vůči aktuálnímu adresáři. Zpětné lomítko (\\) nebo jako oddělovače adresář pro buď název lze použít lomítko (/). `SetCurrentDirectory` Před použitím, překládá oddělovačů název adresáře na příslušné znaků.  
  
 Použití [GetCurrentDirectory](#getcurrentdirectory) k určení aktuální pracovní adresář serveru FTP. Není Předpokládejme, že vzdálený systém, můžete je připojený ke kořenový adresář.  
  
## <a name="see-also"></a>Viz také  
 [CInternetConnection – třída](../../mfc/reference/cinternetconnection-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CInternetConnection – třída](../../mfc/reference/cinternetconnection-class.md)   
 [CInternetSession – třída](../../mfc/reference/cinternetsession-class.md)
