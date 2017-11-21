---
title: "Třída CFtpFileFind | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFtpFileFind
- AFXINET/CFtpFileFind
- AFXINET/CFtpFileFind::CFtpFileFind
- AFXINET/CFtpFileFind::FindFile
- AFXINET/CFtpFileFind::FindNextFile
- AFXINET/CFtpFileFind::GetFileURL
dev_langs: C++
helpviewer_keywords:
- CFtpFileFind [MFC], CFtpFileFind
- CFtpFileFind [MFC], FindFile
- CFtpFileFind [MFC], FindNextFile
- CFtpFileFind [MFC], GetFileURL
ms.assetid: 9667cf01-657f-4b11-b9db-f11e5a7b4e4c
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ff064892172a4d1ab9d31c67be031935650c6c16
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cftpfilefind-class"></a>CFtpFileFind – třída
Usnadňuje hledání souborů Internetu serverů FTP.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CFtpFileFind : public CFileFind  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CFtpFileFind::CFtpFileFind](#cftpfilefind)|Vytvoří `CFtpFileFind` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CFtpFileFind::FindFile](#findfile)|Vyhledá soubor na serveru FTP.|  
|[CFtpFileFind::FindNextFile](#findnextfile)|Pokračuje v hledání souborů z předchozího volání [FindFile](#findfile).|  
|[CFtpFileFind::GetFileURL](#getfileurl)|Získá adresu URL, včetně cesty souboru nalezen.|  
  
## <a name="remarks"></a>Poznámky  
 `CFtpFileFind`obsahuje členské funkce, které začínají vyhledávání, vyhledejte soubor a vrátit adresu URL nebo další popisné informace o souboru.  
  
 Ostatní třídy MFC určená pro Internet a místního souboru vyhledávat obsahují [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) a [CFileFind](../../mfc/reference/cfilefind-class.md). Společně s `CFtpFileFind`, tyto třídy poskytují bezproblémové mechanismus pro klienta k vyhledání konkrétních souborů, bez ohledu na serveru protokolu nebo typ souboru (místní počítač nebo vzdálený server). Všimněte si, že neexistuje žádná třída knihovny MFC pro vyhledávání na serverech HTTP, protože HTTP nepodporuje přímé souboru manipulaci požadované pro hledání.  
  
 Další informace o tom, jak používat `CFtpFileFind` a ostatní WinInet třídy, najdete v článku [Internet programování s WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje, jak vytvořit výčet všechny soubory v aktuálním adresáři serveru FTP.  
  
 [!code-cpp[NVC_MFCWinInet#8](../../mfc/codesnippet/cpp/cftpfilefind-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFileFind](../../mfc/reference/cfilefind-class.md)  
  
 `CFtpFileFind`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxinet.h  
  
##  <a name="cftpfilefind"></a>CFtpFileFind::CFtpFileFind  
 Tato funkce člen je volána k sestavení `CFtpFileFind` objektu.  
  
```  
explicit CFtpFileFind(
    CFtpConnection* pConnection,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>Parametry  
 `pConnection`  
 Ukazatel na `CFtpConnection` objektu. Připojení k serveru FTP můžete získat voláním [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection).  
  
 `dwContext`  
 Identifikátor kontext pro `CFtpFileFind` objektu. V tématu **poznámky** Další informace o tomto parametru.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí hodnota pro `dwContext` odesílají MFC k `CFtpFileFind` objektu z [CInternetSession](../../mfc/reference/cinternetsession-class.md) objekt vytvořený `CFtpFileFind` objektu. Můžete přepsat výchozí identifikátor kontextu nastavit na hodnotu dle vlastního výběru. Identifikátor kontextu je vrácen do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) poskytovat stav na objekt, ke kterému se identifikuje. Najdete v článku [první kroky Internet: WinInet](../../mfc/wininet-basics.md) Další informace o kontextu identifikátor.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad v přehledu třídy dříve v tomto tématu.  
  
##  <a name="findfile"></a>CFtpFileFind::FindFile  
 Volání této funkce člen najít soubor FTP.  
  
```  
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,  
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```  
  
### <a name="parameters"></a>Parametry  
 `pstrName`  
 Ukazatel na řetězec, který obsahuje název souboru, který se najít. Pokud **NULL**, provede volání hledání pomocí zástupných znaků (*).  
  
 `dwFlags`  
 Příznaky popisující, jak zpracovat tuto relaci. Tyto příznaky mohou být kombinovány s bitový operátor OR (&#124;) a jsou následující:  
  
-   INTERNET_FLAG_RELOAD získat data z drátového připojení i v případě, že je v místní mezipaměti. Toto je výchozí příznak.  
  
-   INTERNET_FLAG_DONT_CACHE Neukládat do mezipaměti dat, buď místně nebo v žádné brány.  
  
-   INTERNET_FLAG_RAW_DATA přepsat výchozí nastavení vrátit nezpracovaná data ( [WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) struktury pro FTP).  
  
-   Zabezpečuje INTERNET_FLAG_SECURE transakce v drátové síti (Secure Sockets Layer) nebo procento Tento příznak se vztahuje na pouze požadavky HTTP.  
  
-   INTERNET_FLAG_EXISTING_CONNECT Pokud je to možné, opakovaně používat existující připojení k serveru pro nové **FindFile** požadavků místo vytvoření nové relace pro každý požadavek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0. Chcete-li získat rozšířené informace o chybě, volejte funkci Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360).  
  
### <a name="remarks"></a>Poznámky  
 Po volání **FindFile** načíst první soubor FTP, můžete volat [FindNextFile](#findnextfile) se budou načítat soubory následné FTP.  
  
### <a name="example"></a>Příklad  
  Podívejte se na předchozí příklad v tomto tématu.  
  
##  <a name="findnextfile"></a>CFtpFileFind::FindNextFile  
 Volání této funkce člen pokračujte hledání souboru zahájena volání [FindFile](#findfile) – členská funkce.  
  
```  
virtual BOOL FindNextFile();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud existují další soubory; nula, pokud je soubor nalezen naposledy v adresáři, nebo pokud došlo k chybě. Chcete-li získat rozšířené informace o chybě, volejte funkci Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360). Pokud je soubor nalezen posledního souboru v adresáři, nebo pokud neexistuje odpovídající soubory najdete, `GetLastError` funkce vrátí ERROR_NO_MORE_FILES.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce musí volat alespoň jednou před voláním jakékoli funkce atribut (viz [CFileFind::FindNextFile](../../mfc/reference/cfilefind-class.md#findnextfile)).  
  
 `FindNextFile`zabalí funkci Win32 [FindNextFile](http://msdn.microsoft.com/library/windows/desktop/aa364428).  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad dříve v tomto tématu.  
  
##  <a name="getfileurl"></a>CFtpFileFind::GetFileURL  
 Volání této funkce člen získat adresu URL zadaného souboru.  
  
```  
CString GetFileURL() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Soubor a cestu Universal prostředků Lokátor (URL).  
  
### <a name="remarks"></a>Poznámky  
 `GetFileURL`je podobná – členská funkce [CFileFind::GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath)kromě toho, že se vrátí adresu URL ve formátu `ftp://moose/dir/file.txt`.  
  
## <a name="see-also"></a>Viz také  
 [CFileFind – třída](../../mfc/reference/cfilefind-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CGopherFileFind – třída](../../mfc/reference/cgopherfilefind-class.md)   
 [CInternetFile – třída](../../mfc/reference/cinternetfile-class.md)   
 [CGopherFile – třída](../../mfc/reference/cgopherfile-class.md)   
 [CHttpFile – třída](../../mfc/reference/chttpfile-class.md)
