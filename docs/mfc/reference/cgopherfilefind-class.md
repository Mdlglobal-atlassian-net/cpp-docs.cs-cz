---
title: "Třída CGopherFileFind | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CGopherFileFind
- AFXINET/CGopherFileFind
- AFXINET/CGopherFileFind::CGopherFileFind
- AFXINET/CGopherFileFind::FindFile
- AFXINET/CGopherFileFind::FindNextFile
- AFXINET/CGopherFileFind::GetCreationTime
- AFXINET/CGopherFileFind::GetLastAccessTime
- AFXINET/CGopherFileFind::GetLastWriteTime
- AFXINET/CGopherFileFind::GetLength
- AFXINET/CGopherFileFind::GetLocator
- AFXINET/CGopherFileFind::GetScreenName
- AFXINET/CGopherFileFind::IsDots
dev_langs: C++
helpviewer_keywords:
- CGopherFileFind [MFC], CGopherFileFind
- CGopherFileFind [MFC], FindFile
- CGopherFileFind [MFC], FindNextFile
- CGopherFileFind [MFC], GetCreationTime
- CGopherFileFind [MFC], GetLastAccessTime
- CGopherFileFind [MFC], GetLastWriteTime
- CGopherFileFind [MFC], GetLength
- CGopherFileFind [MFC], GetLocator
- CGopherFileFind [MFC], GetScreenName
- CGopherFileFind [MFC], IsDots
ms.assetid: 8465a979-6323-496d-ab4b-e81383fb999d
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 06b71e3cbebc7ed052fafff077d951a7f3ade810
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cgopherfilefind-class"></a>CGopherFileFind – třída
Usnadňuje hledání souborů Internetu gopher serverů.  
  
> [!NOTE]
>  Třídy `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` a jejich členové jsou zastaralé protože nepracují na platformě Windows XP, ale budou i nadále fungovat na starší operační systémy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CGopherFileFind : public CFileFind  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CGopherFileFind::CGopherFileFind](#cgopherfilefind)|Vytvoří `CGopherFileFind` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CGopherFileFind::FindFile](#findfile)|Vyhledá soubor na serveru gopher.|  
|[CGopherFileFind::FindNextFile](#findnextfile)|Pokračuje v hledání souborů z předchozího volání [FindFile](#findfile).|  
|[CGopherFileFind::GetCreationTime](#getcreationtime)|Získá čas vytvoření zadaného souboru.|  
|[CGopherFileFind::GetLastAccessTime](#getlastaccesstime)|Získá čas posledního přístupu k zadaný soubor.|  
|[CGopherFileFind::GetLastWriteTime](#getlastwritetime)|Získá dobu do posledního zápisu zadaný soubor.|  
|[CGopherFileFind::GetLength](#getlength)|Získá délku nalezený soubor v bajtech.|  
|[CGopherFileFind::GetLocator](#getlocator)|Získání `CGopherLocator` objektu.|  
|[CGopherFileFind::GetScreenName](#getscreenname)|Získá název obrazovky gopher.|  
|[CGopherFileFind::IsDots](#isdots)|Testy pro aktuální adresář a nadřazené značky directory během iterace v rámci soubory.|  
  
## <a name="remarks"></a>Poznámky  
 `CGopherFileFind`obsahuje členské funkce, které začínají vyhledávání, vyhledejte soubor a návratovou adresu URL souboru.  
  
 Ostatní třídy MFC určená pro Internet a místního souboru vyhledávat obsahují [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) a [CFileFind](../../mfc/reference/cfilefind-class.md). Společně s `CGopherFileFind`, tyto třídy poskytují bezproblémové mechanismus pro uživatele k vyhledání konkrétních souborů, bez ohledu na to, protokol serveru, typ souboru nebo umístění (místní počítač nebo vzdáleném serveru.) Všimněte si, že neexistuje žádná třída knihovny MFC pro vyhledávání na serverech HTTP, protože HTTP nepodporuje přímé souboru manipulaci vyžadovanou hledání.  
  
> [!NOTE]
> `CGopherFileFind`nepodporuje následující členské funkce její základní třída [CFileFind](../../mfc/reference/cfilefind-class.md):  
  
- [GetRoot](../../mfc/reference/cfilefind-class.md#getroot)  
  
- [GetFileName](../../mfc/reference/cfilefind-class.md#getfilename)  
  
- [GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath)  
  
- [GetFileTitle](../../mfc/reference/cfilefind-class.md#getfiletitle)  
  
- [GetFileURL](../../mfc/reference/cfilefind-class.md#getfileurl)  
  
 Kromě toho, pokud se používá s `CGopherFileFind`, `CFileFind` – členská funkce [IsDots](../../mfc/reference/cfilefind-class.md#isdots) je vždy **FALSE**.  
  
 Další informace o tom, jak používat `CGopherFileFind` a ostatní WinInet třídy, najdete v článku [Internet programování s WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFileFind](../../mfc/reference/cfilefind-class.md)  
  
 `CGopherFileFind`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxinet.h  
  
##  <a name="cgopherfilefind"></a>CGopherFileFind::CGopherFileFind  
 Tato funkce člen je volána k sestavení `CGopherFileFind` objektu.  
  
```  
explicit CGopherFileFind(
    CGopherConnection* pConnection,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>Parametry  
 `pConnection`  
 Ukazatel [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) objektu.  
  
 `dwContext`  
 Identifikátor kontextu pro danou operaci. V tématu **poznámky** Další informace o `dwContext`.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí hodnota pro `dwContext` odesílají MFC k `CGopherFileFind` objektu z [CInternetSession](../../mfc/reference/cinternetsession-class.md) objekt vytvořený `CGopherFileFind` objektu. Když vytvoříte `CGopherFileFind` objekt, můžete přepsat výchozí identifikátor kontextu nastavit na hodnotu dle vlastního výběru. Identifikátor kontextu je vrácen do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) poskytovat stav na objekt, ke kterému se identifikuje. Najdete v článku [první kroky Internet: WinInet](../../mfc/wininet-basics.md) Další informace o kontextu identifikátor.  
  
##  <a name="findfile"></a>CGopherFileFind::FindFile  
 Volání této funkce člen najít soubor gopher.  
  
```  
virtual BOOL FindFile(
    CGopherLocator& refLocator,  
    LPCTSTR pstrString,  
    DWORD dwFlags = INTERNET_FLAG_RELOAD);

 
virtual BOOL FindFile(
    LPCTSTR pstrString,  
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```  
  
### <a name="parameters"></a>Parametry  
 `refLocator`  
 Odkaz na [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) objektu.  
  
 *pstrString*  
 Ukazatel na řetězec, který obsahuje název souboru.  
  
 `dwFlags`  
 Příznaky popisující, jak zpracovat tuto relaci. Platné příznaky jsou:  
  
-   INTERNET_FLAG_RELOAD získat data ze vzdáleného serveru, i když je v místní mezipaměti.  
  
-   INTERNET_FLAG_DONT_CACHE Neukládat do mezipaměti dat, buď místně nebo v žádné brány.  
  
-   Žádosti o INTERNET_FLAG_SECURE zabezpečené transakce v drátové síti s Secure Sockets Layer nebo procento Tento příznak se vztahuje na pouze požadavky HTTP.  
  
-   INTERNET_FLAG_USE_EXISTING Pokud je to možné, opakovaně používat existující připojení k serveru pro nové **FindFile** požadavků, místo vytvoření nové relace pro každý požadavek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0. Chcete-li získat rozšířené informace o chybě, volejte funkci Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360).  
  
### <a name="remarks"></a>Poznámky  
 Po volání **FindFile** načíst první objekt gopher, můžete volat [FindNextFile](#findnextfile) se budou načítat soubory následné gopher.  
  
##  <a name="findnextfile"></a>CGopherFileFind::FindNextFile  
 Volání této funkce člen pokračujte hledání souboru zahájena volání [CGopherFileFind::FindFile](#findfile).  
  
```  
virtual BOOL FindNextFile();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud existují další soubory; nula, pokud je soubor nalezen naposledy v adresáři, nebo pokud došlo k chybě. Chcete-li získat rozšířené informace o chybě, volejte funkci Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360). Pokud je soubor nalezen posledního souboru v adresáři, nebo pokud neexistuje odpovídající soubory najdete, `GetLastError` funkce vrátí ERROR_NO_MORE_FILES.  
  
##  <a name="getcreationtime"></a>CGopherFileFind::GetCreationTime  
 Získá čas vytvoření pro aktuální soubor.  
  
```  
virtual BOOL GetCreationTime(FILETIME* pTimeStamp) const;  
virtual BOOL GetCreationTime(CTime& refTime) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `pTimeStamp`  
 Ukazatel [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284) struktura obsahující čas vytvoření souboru.  
  
 `refTime`  
 Odkaz na [CTime](../../atl-mfc-shared/reference/ctime-class.md) objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; 0, pokud je neúspěšná. `GetCreationTime`Vrátí hodnotu 0, pouze pokud [FindNextFile](#findnextfile) nikdy byla volána v tomto `CGopherFileFind` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Je třeba volat [FindNextFile](#findnextfile) alespoň jednou před voláním `GetCreationTime`.  
  
> [!NOTE]
>  Ne všechny systémy souborů použijte stejnou sémantiku implementovat časové razítko, vrátí tato funkce. Tato funkce může vrátit stejné hodnoty vrácené jiné časové razítko funkce, pokud základní systému souborů nebo ze serveru nepodporuje zachování atribut čas. Najdete v článku [Win32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) struktura informace o formátu času. U některých operačních systémů vrácený čas je v místní zóně do počítače se, že se soubor ocitne čase. V tématu Win32 [FileTimeToLocalFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724277) rozhraní API pro další informace.  
  
##  <a name="getlastaccesstime"></a>CGopherFileFind::GetLastAccessTime  
 Získá čas posledního přístupu k zadaný soubor.  
  
```  
virtual BOOL GetLastAccessTime(CTime& refTime) const;  
virtual BOOL GetLastAccessTime(FILETIME* pTimeStamp) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `refTime`  
 Odkaz na [CTime](../../atl-mfc-shared/reference/ctime-class.md) objektu.  
  
 `pTimeStamp`  
 Ukazatel [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284) struktura obsahující čas posledního přístupu k souboru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; 0, pokud je neúspěšná. `GetLastAccessTime`Vrátí hodnotu 0, pouze pokud [FindNextFile](#findnextfile) nikdy byla volána v tomto `CGopherFileFind` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Je třeba volat [FindNextFile](#findnextfile) alespoň jednou před voláním `GetLastAccessTime`.  
  
> [!NOTE]
>  Ne všechny systémy souborů použijte stejnou sémantiku implementovat časové razítko, vrátí tato funkce. Tato funkce může vrátit stejné hodnoty vrácené jiné časové razítko funkce, pokud základní systému souborů nebo ze serveru nepodporuje zachování atribut čas. Najdete v článku [Win32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) struktura informace o formátu času. U některých operačních systémů vrácený čas je v místní zóně do počítače se, že se soubor ocitne čase. V tématu Win32 [FileTimeToLocalFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724277) rozhraní API pro další informace.  
  
##  <a name="getlastwritetime"></a>CGopherFileFind::GetLastWriteTime  
 Získá čas poslední změny souboru.  
  
```  
virtual BOOL GetLastWriteTime(FILETIME* pTimeStamp) const;  
virtual BOOL GetLastWriteTime(CTime& refTime) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `pTimeStamp`  
 Ukazatel [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284) struktura obsahující času posledního zápisu souboru na.  
  
 `refTime`  
 Odkaz na [CTime](../../atl-mfc-shared/reference/ctime-class.md) objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; 0, pokud je neúspěšná. `GetLastWriteTime`Vrátí hodnotu 0, pouze pokud [FindNextFile](#findnextfile) nikdy byla volána v tomto `CGopherFileFind` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Je třeba volat [FindNextFile](#findnextfile) alespoň jednou před voláním `GetLastWriteTime`.  
  
> [!NOTE]
>  Ne všechny systémy souborů použijte stejnou sémantiku implementovat časové razítko, vrátí tato funkce. Tato funkce může vrátit stejné hodnoty vrácené jiné časové razítko funkce, pokud základní systému souborů nebo ze serveru nepodporuje zachování atribut čas. Najdete v článku [Win32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) struktura informace o formátu času. U některých operačních systémů vrácený čas je v místní zóně do počítače se, že se soubor ocitne čase. V tématu Win32 [FileTimeToLocalFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724277) rozhraní API pro další informace.  
  
##  <a name="getlength"></a>CGopherFileFind::GetLength  
 Volání této funkce člen získat délku v bajtech nalezený soubor.  
  
```  
virtual ULONGLONG GetLength() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Délka v bajtech souboru nalezen.  
  
### <a name="remarks"></a>Poznámky  
 `GetLength`používá strukturu Win32 [WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) má být získána hodnota velikosti souboru v bajtech.  
  
> [!NOTE]
>  Od verze MFC 7.0 `GetLength` podporuje typy 64bitové celé číslo. Dříve existující kód vytvořené s nástroji této novější verzi knihovny může mít za následek zkrácení upozornění.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CFile::GetLength](../../mfc/reference/cfile-class.md#getlength) (základní třída implementace).  
  
##  <a name="getlocator"></a>CGopherFileFind::GetLocator  
 Volání této funkce člen získat [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) objektu, který [FindFile](#findfile) používá k nalezení gopher souboru.  
  
```  
CGopherLocator GetLocator() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CGopherLocator` objektu.  
  
##  <a name="getscreenname"></a>CGopherFileFind::GetScreenName  
 Volání této funkce člen získat název obrazovky gopher.  
  
```  
CString GetScreenName() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Název obrazovky gopher.  
  
##  <a name="isdots"></a>CGopherFileFind::IsDots  
 Testy pro aktuální adresář a nadřazené značky directory během iterace v rámci soubory.  
  
```  
virtual BOOL IsDots() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud nalezen soubor s názvem "."nebo"...", což naznačuje, že nalezen soubor je ve skutečnosti adresář. Jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Je třeba volat [FindNextFile](#findnextfile) alespoň jednou před voláním `IsDots`.  
  
## <a name="see-also"></a>Viz také  
 [CFileFind – třída](../../mfc/reference/cfilefind-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CFtpFileFind – třída](../../mfc/reference/cftpfilefind-class.md)   
 [CFileFind – třída](../../mfc/reference/cfilefind-class.md)   
 [CInternetFile – třída](../../mfc/reference/cinternetfile-class.md)   
 [CGopherFile – třída](../../mfc/reference/cgopherfile-class.md)   
 [CHttpFile – třída](../../mfc/reference/chttpfile-class.md)
