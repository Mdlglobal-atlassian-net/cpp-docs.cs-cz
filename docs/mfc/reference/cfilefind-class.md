---
title: "Třída CFileFind | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFileFind
- AFX/CFileFind
- AFX/CFileFind::CFileFind
- AFX/CFileFind::Close
- AFX/CFileFind::FindFile
- AFX/CFileFind::FindNextFile
- AFX/CFileFind::GetCreationTime
- AFX/CFileFind::GetFileName
- AFX/CFileFind::GetFilePath
- AFX/CFileFind::GetFileTitle
- AFX/CFileFind::GetFileURL
- AFX/CFileFind::GetLastAccessTime
- AFX/CFileFind::GetLastWriteTime
- AFX/CFileFind::GetLength
- AFX/CFileFind::GetRoot
- AFX/CFileFind::IsArchived
- AFX/CFileFind::IsCompressed
- AFX/CFileFind::IsDirectory
- AFX/CFileFind::IsDots
- AFX/CFileFind::IsHidden
- AFX/CFileFind::IsNormal
- AFX/CFileFind::IsReadOnly
- AFX/CFileFind::IsSystem
- AFX/CFileFind::IsTemporary
- AFX/CFileFind::MatchesMask
- AFX/CFileFind::CloseContext
- AFX/CFileFind::m_pTM
dev_langs:
- C++
helpviewer_keywords:
- CFileFind [MFC], CFileFind
- CFileFind [MFC], Close
- CFileFind [MFC], FindFile
- CFileFind [MFC], FindNextFile
- CFileFind [MFC], GetCreationTime
- CFileFind [MFC], GetFileName
- CFileFind [MFC], GetFilePath
- CFileFind [MFC], GetFileTitle
- CFileFind [MFC], GetFileURL
- CFileFind [MFC], GetLastAccessTime
- CFileFind [MFC], GetLastWriteTime
- CFileFind [MFC], GetLength
- CFileFind [MFC], GetRoot
- CFileFind [MFC], IsArchived
- CFileFind [MFC], IsCompressed
- CFileFind [MFC], IsDirectory
- CFileFind [MFC], IsDots
- CFileFind [MFC], IsHidden
- CFileFind [MFC], IsNormal
- CFileFind [MFC], IsReadOnly
- CFileFind [MFC], IsSystem
- CFileFind [MFC], IsTemporary
- CFileFind [MFC], MatchesMask
- CFileFind [MFC], CloseContext
- CFileFind [MFC], m_pTM
ms.assetid: 9990068c-b023-4114-9580-a50182d15240
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e890e59896d1f69264ab479168385cf2a05d9fb7
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2018
---
# <a name="cfilefind-class"></a>CFileFind – třída
Provede vyhledávání místního souboru a je základní třídou pro [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) a [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md), které provádí hledání souborů Internetu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CFileFind : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CFileFind::CFileFind](#cfilefind)|Vytvoří `CFileFind` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CFileFind::Close](#close)|Zavře žádost o vyhledávání.|  
|[CFileFind::FindFile](#findfile)|Vyhledá adresář pro zadaný název souboru.|  
|[CFileFind::FindNextFile](#findnextfile)|Pokračuje v hledání souborů z předchozího volání [FindFile](#findfile).|  
|[CFileFind::GetCreationTime](#getcreationtime)|Získá čas vytvoření souboru.|  
|[CFileFind::GetFileName](#getfilename)|Získá název, včetně přípony souboru nalezen|  
|[CFileFind::GetFilePath](#getfilepath)|Získá celou cestu k souboru nalezen.|  
|[CFileFind::GetFileTitle](#getfiletitle)|Získá název souboru nalezen. Název neobsahuje rozšíření.|  
|[CFileFind::GetFileURL](#getfileurl)|Získá adresu URL, včetně cesta k souboru, soubor nalezen.|  
|[CFileFind::GetLastAccessTime](#getlastaccesstime)|Získá čas posledního přístupu k souboru.|  
|[CFileFind::GetLastWriteTime](#getlastwritetime)|Získá dobu soubor byl poslední změnit a uložit.|  
|[CFileFind::GetLength](#getlength)|Získá délku nalezený soubor v bajtech.|  
|[CFileFind::GetRoot](#getroot)|Získá kořenový adresář souboru nalezen.|  
|[CFileFind::IsArchived](#isarchived)|Určuje, pokud je nalezen soubor archivovat.|  
|[CFileFind::IsCompressed](#iscompressed)|Určuje, pokud je nalezen soubor zkomprimuje.|  
|[CFileFind::IsDirectory](#isdirectory)|Určuje, zda soubor nalezen adresář.|  
|[CFileFind::IsDots](#isdots)|Určí, zda název souboru nalezen má název "."nebo"...", což indikuje, že je ve skutečnosti adresář.|  
|[CFileFind::IsHidden](#ishidden)|Určuje, zda je skrytý na nalezený soubor.|  
|[CFileFind::IsNormal](#isnormal)|Určuje, zda je soubor nalezen normální (jinými slovy, nemá žádné další atributy).|  
|[CFileFind::IsReadOnly](#isreadonly)|Určuje, zda soubor nalezen jen pro čtení.|  
|[CFileFind::IsSystem](#issystem)|Určuje, zda soubor nalezen systémový soubor.|  
|[CFileFind::IsTemporary](#istemporary)|Určuje, zda je dočasný soubor nalezen.|  
|[CFileFind::MatchesMask](#matchesmask)|Určuje požadovanou atributů souboru nalezen.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CFileFind::CloseContext](#closecontext)|Zavře soubor určený touto aktuální popisovač vyhledávání.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CFileFind::m_pTM](#m_ptm)|Ukazatel na `CAtlTransactionManager` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 `CFileFind` obsahuje členské funkce, které začínají vyhledávání, vyhledejte soubor a vrátí název, název nebo cesta k souboru. Pro hledání na Internetu, – členská funkce [GetFileURL](#getfileurl) vrátí adresu URL souboru.  
  
 `CFileFind` Základní třída pro dva další třídy MFC slouží k vyhledávání určitého serveru typy: `CGopherFileFind` funguje konkrétně se gopher servery, a `CFtpFileFind` funguje konkrétně se servery FTP. Společně poskytují tyto tři třídy bezproblémové mechanismus pro klienta najít soubory, bez ohledu na to, protokol serveru, typ souboru nebo umístění, v místním počítači nebo na vzdálený server.  
  
 Následující kód vytvoří výčet všech souborů v aktuálním adresáři, Tisk názvu každého souboru:  
  
 [!code-cpp[NVC_MFCFiles#31](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_1.cpp)]  
  
 Pro zjednodušení příkladu, tento kód používá standardní knihovna C++ `cout` třídy. `cout` Řádku může být nahrazena volání `CListBox::AddString`, například v programu s grafickým uživatelským rozhraním.  
  
 Další informace o tom, jak používat `CFileFind` a ostatní WinInet třídy, najdete v článku [Internet programování s WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CFileFind`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h  
  
##  <a name="cfilefind"></a>  CFileFind::CFileFind  
 Tento člen funkce je volána, když `CFileFind` vytvoření objektu.  
  
```  
CFileFind();  
CFileFind(CAtlTransactionManager* pTM);
```  
  
### <a name="parameters"></a>Parametry  
 `pTM`  
 Ukazatel na objekt CAtlTransactionManager  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CFileFind::GetFileName](#getfilename).  
  
##  <a name="close"></a>  CFileFind::Close  
 Volání této funkce člen ukončení hledání, resetování kontextu a uvolní všechny prostředky.  
  
```  
void Close();
```  
  
### <a name="remarks"></a>Poznámky  
 Po volání **Zavřít**, není nutné vytvořit nový `CFileFind` instance před voláním [FindFile](#findfile) zahájíte nové hledání.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CFileFind::GetFileName](#getfilename).  
  
##  <a name="closecontext"></a>  CFileFind::CloseContext  
 Zavře soubor určený touto aktuální popisovač vyhledávání.  
  
```  
virtual void CloseContext();
```  
  
### <a name="remarks"></a>Poznámky  
 Zavře soubor určený touto aktuální hodnota popisovač vyhledávání. Přepsání této funkci můžete změnit výchozí chování.  
  
 Je třeba zavolat [FindFile](#findfile) nebo [FindNextFile](#findnextfile) funkce alespoň jednou pro načtení popisovače platné vyhledávání. **FindFile** a `FindNextFile` funkce použití popisovače hledání najít soubory s názvy, které odpovídají zadaným názvem.  
  
##  <a name="findfile"></a>  CFileFind::FindFile  
 Volání této funkce člen otevřete hledání souborů.  
  
```  
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,  
    DWORD dwUnused = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `pstrName`  
 Ukazatel na řetězec, který obsahuje název souboru, který se najít. Pokud předáte **NULL** pro `pstrName`, **FindFile** nemá zástupný znak (*.\*) vyhledávání.  
  
 *dwUnused*  
 Vyhrazené aby **FindFile** polymorfní s odvozené třídy. Musí být 0.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0. Chcete-li získat rozšířené informace o chybě, volejte funkci Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360).  
  
### <a name="remarks"></a>Poznámky  
 Po volání **FindFile** zahájíte hledání souborů volání [FindNextFile](#findnextfile) načíst následné soubory. Je třeba volat `FindNextFile` alespoň jednou před voláním všechny následující atribut členské funkce:  
  
- [GetCreationTime](#getcreationtime)  
  
- [GetFileName](#getfilename)  
  
- [GetFileTitle](#getfiletitle)  
  
- [GetFilePath](#getfilepath)  
  
- [GetFileURL](#getfileurl)  
  
- [GetLastAccessTime](#getlastaccesstime)  
  
- [GetLastWriteTime](#getlastwritetime)  
  
- [GetLength –](#getlength)  
  
- [GetRoot](#getroot)  
  
- [IsArchived](#isarchived)  
  
- [IsCompressed](#iscompressed)  
  
- [IsDirectory](#isdirectory)  
  
- [IsDots](#isdots)  
  
- [IsHidden](#ishidden)  
  
- [Isnormal –](#isnormal)  
  
- [IsReadOnly](#isreadonly)  
  
- [IsSystem nastaveno](#issystem)  
  
- [IsTemporary](#istemporary)  
  
- [MatchesMask](#matchesmask)  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CFileFind::IsDirectory](#isdirectory).  
  
##  <a name="findnextfile"></a>  CFileFind::FindNextFile  
 Volání této funkce člen pokračujte hledání souborů z předchozího volání [FindFile](#findfile).  
  
```  
virtual BOOL FindNextFile();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud existují další soubory; nula, pokud je soubor nalezen naposledy v adresáři, nebo pokud došlo k chybě. Chcete-li získat rozšířené informace o chybě, volejte funkci Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360). Pokud je soubor nalezen posledního souboru v adresáři, nebo pokud neexistuje odpovídající soubory najdete, `GetLastError` funkce vrátí ERROR_NO_MORE_FILES.  
  
### <a name="remarks"></a>Poznámky  
 Je třeba volat `FindNextFile` alespoň jednou před voláním všechny následující atribut členské funkce:  
  
- [GetCreationTime](#getcreationtime)  
  
- [GetFileName](#getfilename)  
  
- [GetFileTitle](#getfiletitle)  
  
- [GetFilePath](#getfilepath)  
  
- [GetFileURL](#getfileurl)  
  
- [GetLastAccessTime](#getlastaccesstime)  
  
- [GetLastWriteTime](#getlastwritetime)  
  
- [GetLength –](#getlength)  
  
- [GetRoot](#getroot)  
  
- [IsArchived](#isarchived)  
  
- [IsCompressed](#iscompressed)  
  
- [IsDirectory](#isdirectory)  
  
- [IsDots](#isdots)  
  
- [IsHidden](#ishidden)  
  
- [Isnormal –](#isnormal)  
  
- [IsReadOnly](#isreadonly)  
  
- [IsSystem nastaveno](#issystem)  
  
- [IsTemporary](#istemporary)  
  
- [MatchesMask](#matchesmask)  
  
 `FindNextFile` zabalí funkci Win32 [FindNextFile](http://msdn.microsoft.com/library/windows/desktop/aa364428).  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CFileFind::IsDirectory](#isdirectory).  
  
##  <a name="getcreationtime"></a>  CFileFind::GetCreationTime  
 Volání této funkce člen získat čas vytvoření zadaného souboru.  
  
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
 Nenulové hodnoty v případě úspěchu; 0, pokud je neúspěšná. `GetCreationTime` Vrátí hodnotu 0, pouze pokud [FindNextFile](#findnextfile) nikdy byla volána v tomto `CFileFind` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Je třeba volat [FindNextFile](#findnextfile) alespoň jednou před voláním `GetCreationTime`.  
  
> [!NOTE]
>  Ne všechny systémy souborů použijte stejnou sémantiku implementovat časové razítko, vrátí tato funkce. Tato funkce může vrátit stejné hodnoty vrácené jiné časové razítko funkce, pokud základní systému souborů nebo ze serveru nepodporuje zachování atribut čas. Najdete v článku [Win32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) struktura informace o formátu času. Na některé operační systémy vrácený čas je v místní zóně do počítače se, že se soubor ocitne čase. V tématu Win32 [FileTimeToLocalFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724277) rozhraní API pro další informace.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CFileFind::GetLength](#getlength).  
  
##  <a name="getfilename"></a>  CFileFind::GetFileName  
 Volání této funkce člen získat název souboru nalezen.  
  
```  
virtual CString GetFileName() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Název souboru nedávno nalezen.  
  
### <a name="remarks"></a>Poznámky  
 Je třeba volat [FindNextFile](#findnextfile) alespoň jednou před voláním GetFileName.  
  
 `GetFileName` je jednou ze tří `CFileFind` členské funkce, které vracejí určitou formu název souboru. Následující seznam popisuje tři a jak se liší:  
  
- `GetFileName` Vrátí název souboru, včetně přípony. Například volání `GetFileName` vygenerovat zprávu uživatele o souboru `c:\myhtml\myfile.txt` vrátí název souboru `myfile.txt`.  
  
- [GetFilePath](#getfilepath) vrátí celá cesta k souboru. Například volání `GetFilePath` vygenerovat zprávu uživatele o souboru `c:\myhtml\myfile.txt` vrátí cestu k souboru `c:\myhtml\myfile.txt`.  
  
- [GetFileTitle](#getfiletitle) vrátí název souboru bez přípony souboru. Například volání `GetFileTitle` vygenerovat zprávu uživatele o souboru `c:\myhtml\myfile.txt` vrátí název souboru `myfile`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCFiles#32](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_2.cpp)]  
  
##  <a name="getfilepath"></a>  CFileFind::GetFilePath  
 Volání této funkce člen získat úplnou cestu zadaný soubor.  
  
```  
virtual CString GetFilePath() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Cesta zadaného souboru.  
  
### <a name="remarks"></a>Poznámky  
 Je třeba volat [FindNextFile](#findnextfile) alespoň jednou před voláním `GetFilePath`.  
  
 `GetFilePath` je jednou ze tří `CFileFind` členské funkce, které vracejí určitou formu název souboru. Následující seznam popisuje tři a jak se liší:  
  
- [GetFileName](#getfilename) vrátí název souboru, včetně přípony. Například volání `GetFileName` vygenerovat zprávu uživatele o souboru `c:\myhtml\myfile.txt` vrátí název souboru `myfile.txt`.  
  
- `GetFilePath` Vrátí celou cestu k souboru. Například volání `GetFilePath` vygenerovat zprávu uživatele o souboru `c:\myhtml\myfile.txt` vrátí cestu k souboru `c:\myhtml\myfile.txt`.  
  
- [GetFileTitle](#getfiletitle) vrátí název souboru bez přípony souboru. Například volání `GetFileTitle` vygenerovat zprávu uživatele o souboru `c:\myhtml\myfile.txt` vrátí název souboru `myfile`.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CFileFind::GetFileName](#getfilename).  
  
##  <a name="getfiletitle"></a>  CFileFind::GetFileTitle  
 Volání této funkce člen získat název souboru nalezen.  
  
```  
virtual CString GetFileTitle() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Název souboru.  
  
### <a name="remarks"></a>Poznámky  
 Je třeba volat [FindNextFile](#findnextfile) alespoň jednou před voláním `GetFileTitle`.  
  
 `GetFileTitle` je jednou ze tří `CFileFind` členské funkce, které vracejí určitou formu název souboru. Následující seznam popisuje tři a jak se liší:  
  
- [GetFileName](#getfilename) vrátí název souboru, včetně přípony. Například volání `GetFileName` vygenerovat zprávu uživatele o souboru `c:\myhtml\myfile.txt` vrátí název souboru `myfile.txt`.  
  
- [GetFilePath](#getfilepath) vrátí celá cesta k souboru. Například volání `GetFilePath` vygenerovat zprávu uživatele o souboru `c:\myhtml\myfile.txt` vrátí cestu k souboru `c:\myhtml\myfile.txt`.  
  
- `GetFileTitle` Vrátí název souboru bez přípony souboru. Například volání `GetFileTitle` vygenerovat zprávu uživatele o souboru `c:\myhtml\myfile.txt` vrátí název souboru `myfile`.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CFileFind::GetFileName](#getfilename).  
  
##  <a name="getfileurl"></a>  CFileFind::GetFileURL  
 Volání této funkce člena na zadané adrese URL načíst.  
  
```  
virtual CString GetFileURL() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Úplnou adresu URL.  
  
### <a name="remarks"></a>Poznámky  
 Je třeba volat [FindNextFile](#findnextfile) alespoň jednou před voláním `GetFileURL`.  
  
 `GetFileURL` je podobná – členská funkce [GetFilePath](#getfilepath)kromě toho, že se vrátí adresu URL ve formátu `file://path`. Například volání `GetFileURL` získat úplnou adresu URL pro `myfile.txt` vrátí adresu URL `file://c:\myhtml\myfile.txt`.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CFileFind::GetFileName](#getfilename).  
  
##  <a name="getlastaccesstime"></a>  CFileFind::GetLastAccessTime  
 Volání této funkce člen získat čas posledního přístupu k zadaný soubor.  
  
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
 Nenulové hodnoty v případě úspěchu; 0, pokud je neúspěšná. `GetLastAccessTime` Vrátí hodnotu 0, pouze pokud [FindNextFile](#findnextfile) nikdy byla volána v tomto `CFileFind` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Je třeba volat [FindNextFile](#findnextfile) alespoň jednou před voláním `GetLastAccessTime`.  
  
> [!NOTE]
>  Ne všechny systémy souborů použijte stejnou sémantiku implementovat časové razítko, vrátí tato funkce. Tato funkce může vrátit stejné hodnoty vrácené jiné časové razítko funkce, pokud základní systému souborů nebo ze serveru nepodporuje zachování atribut čas. Najdete v článku [Win32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) struktura informace o formátu času. Na některé operační systémy vrácený čas je v místní zóně do počítače se, že se soubor ocitne čase. V tématu Win32 [FileTimeToLocalFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724277) rozhraní API pro další informace.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CFileFind::GetLength](#getlength).  
  
##  <a name="getlastwritetime"></a>  CFileFind::GetLastWriteTime  
 Volání této funkce člen získat čas poslední změny souboru.  
  
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
 Nenulové hodnoty v případě úspěchu; 0, pokud je neúspěšná. `GetLastWriteTime` Vrátí hodnotu 0, pouze pokud [FindNextFile](#findnextfile) nikdy byla volána v tomto `CFileFind` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Je třeba volat [FindNextFile](#findnextfile) alespoň jednou před voláním `GetLastWriteTime`.  
  
> [!NOTE]
>  Ne všechny systémy souborů použijte stejnou sémantiku implementovat časové razítko, vrátí tato funkce. Tato funkce může vrátit stejné hodnoty vrácené jiné časové razítko funkce, pokud základní systému souborů nebo ze serveru nepodporuje zachování atribut čas. Najdete v článku [Win32_Find_Data](http://msdn.microsoft.com/library/windows/desktop/aa365740) struktura informace o formátu času. Na některé operační systémy vrácený čas je v místní zóně do počítače se, že se soubor ocitne čase. V tématu Win32 [FileTimeToLocalFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724277) rozhraní API pro další informace.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CFileFind::GetLength](#getlength).  
  
##  <a name="getlength"></a>  CFileFind::GetLength  
 Volání této funkce člen získat délku nalezený soubor v bajtech.  
  
```  
ULONGLONG GetLength() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Délka nalezený soubor v bajtech.  
  
### <a name="remarks"></a>Poznámky  
 Je třeba volat [FindNextFile](#findnextfile) alespoň jednou před voláním `GetLength`.  
  
 `GetLength` používá strukturu Win32 [WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) získat a vrátíte se hodnota velikosti souboru v bajtech.  
  
> [!NOTE]
>  Od verze MFC 7.0 `GetLength` podporuje typy 64bitové celé číslo. Dříve existující kód vytvořené s nástroji této novější verzi knihovny může vést k zkrácení upozornění.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCFiles#33](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_3.cpp)]  
  
##  <a name="getroot"></a>  CFileFind::GetRoot  
 Volání této funkce člen získat kořenovém souboru nalezen.  
  
```  
virtual CString GetRoot() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Kořen aktivní hledání.  
  
### <a name="remarks"></a>Poznámky  
 Je třeba volat [FindNextFile](#findnextfile) alespoň jednou před voláním `GetRoot`.  
  
 Členské funkce vrátí hodnotu specifikace jednotky a název cesty používá ke spuštění vyhledávání. Například volání [FindFile](#findfile) s `*.dat` výsledkem `GetRoot` vrací prázdný řetězec. Předávání cestu, například `c:\windows\system\*.dll`do **FindFile** výsledky `GetRoot` vrácení `c:\windows\system\`.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CFileFind::GetFileName](#getfilename).  
  
##  <a name="isarchived"></a>  CFileFind::IsArchived  
 Volání této funkce člen k určení, pokud je nalezen soubor archivovat.  
  
```  
BOOL IsArchived() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Aplikace označit soubor archivu, které chcete zálohovat nebo odebrány s FILE_ATTRIBUTE_ARCHIVE atribut souboru v identifikovat [WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) struktura.  
  
 Je třeba volat [FindNextFile](#findnextfile) alespoň jednou před voláním `IsArchived`.  
  
 V tématu – členská funkce [MatchesMask](#matchesmask) úplný seznam atributů souboru.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CFileFind::GetLength](#getlength).  
  
##  <a name="iscompressed"></a>  CFileFind::IsCompressed  
 Volání této funkce člen k určení, pokud je nalezen soubor zkomprimuje.  
  
```  
BOOL IsCompressed() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Komprimovaný soubor je označené jako FILE_ATTRIBUTE_COMPRESSED, atribut souboru identifikovat v [WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) struktura. Pro soubor tento atribut označuje, že všechna data v souboru se komprimují. Pro adresář tento atribut označuje, že komprese je výchozí pro nově vytvořené soubory a podadresáře.  
  
 Je třeba volat [FindNextFile](#findnextfile) alespoň jednou před voláním `IsCompressed`.  
  
 V tématu – členská funkce [MatchesMask](#matchesmask) úplný seznam atributů souboru.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CFileFind::GetLength](#getlength).  
  
##  <a name="isdirectory"></a>  CFileFind::IsDirectory  
 Volání této funkce člen k určení, pokud je nalezen soubor adresář.  
  
```  
BOOL IsDirectory() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Soubor, který je adresář je označené jako FILE_ATTRIBUTE_DIRECTORY v identifikuje atribut souboru [WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) struktura.  
  
 Je třeba volat [FindNextFile](#findnextfile) alespoň jednou před voláním `IsDirectory`.  
  
 V tématu – členská funkce [MatchesMask](#matchesmask) úplný seznam atributů souboru.  
  
### <a name="example"></a>Příklad  
 Tento program malé recurses každý adresář na jednotce C:\ a vytiskne název adresáře.  
  
 [!code-cpp[NVC_MFCFiles#34](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_4.cpp)]  
  
##  <a name="isdots"></a>  CFileFind::IsDots  
 Volání této funkce člen k testování pro aktuální adresář a nadřazený adresář označení při iterace v rámci soubory.  
  
```  
virtual BOOL IsDots() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud nalezen soubor s názvem "."nebo"...", což naznačuje, že nalezen soubor je ve skutečnosti adresář. Jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Je třeba volat [FindNextFile](#findnextfile) alespoň jednou před voláním `IsDots`.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CFileFind::IsDirectory](#isdirectory).  
  
##  <a name="ishidden"></a>  CFileFind::IsHidden  
 Volání této funkce člen, pokud je nalezen soubor skrytý.  
  
```  
BOOL IsHidden() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Skryté soubory, které jsou označené FILE_ATTRIBUTE_HIDDEN, atribut souboru stanovených ve [WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) struktura. Skrytý soubor není zahrnutý v seznamu běžných adresářů.  
  
 Je třeba volat [FindNextFile](#findnextfile) alespoň jednou před voláním `IsHidden`.  
  
 V tématu – členská funkce [MatchesMask](#matchesmask) úplný seznam atributů souboru.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CFileFind::GetLength](#getlength).  
  
##  <a name="isnormal"></a>  CFileFind::IsNormal  
 Volání této funkce člen k určení, pokud je nalezen soubor soubor normální.  
  
```  
BOOL IsNormal() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Soubory s FILE_ATTRIBUTE_NORMAL, atribut souboru stanovených ve [WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) struktura. Normální soubor má nastavené žádné jiné atributy. Všechny ostatní atributy souboru potlačí tento atribut.  
  
 Je třeba volat [FindNextFile](#findnextfile) alespoň jednou před voláním `IsNormal`.  
  
 V tématu – členská funkce [MatchesMask](#matchesmask) úplný seznam atributů souboru.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CFileFind::GetLength](#getlength).  
  
##  <a name="isreadonly"></a>  CFileFind::IsReadOnly  
 Volání této funkce člen k určení, zda se nachází soubor je jen pro čtení.  
  
```  
BOOL IsReadOnly() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Soubor určený jen pro čtení je označené jako FILE_ATTRIBUTE_READONLY, atribut souboru identifikovat v [WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) struktura. Aplikace může číst takový soubor, ale nemohou do něj zapisovat ani odstranit.  
  
 Je třeba volat [FindNextFile](#findnextfile) alespoň jednou před voláním `IsReadOnly`.  
  
 V tématu – členská funkce [MatchesMask](#matchesmask) úplný seznam atributů souboru.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CFileFind::GetLength](#getlength).  
  
##  <a name="issystem"></a>  CFileFind::IsSystem  
 Volání této funkce člen k určení, pokud je nalezen soubor některého systémového souboru.  
  
```  
BOOL IsSystem() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Systém souborů je označené jako FILE_ATTRIBUTE_SYSTEM, atribut souboru identifikovat v [WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) struktura. Systémový soubor je součástí, nebo se používá výhradně funkcí, operačního systému.  
  
 Je třeba volat [FindNextFile](#findnextfile) alespoň jednou před voláním `IsSystem`.  
  
 V tématu – členská funkce [MatchesMask](#matchesmask) úplný seznam atributů souboru.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CFileFind::GetLength](#getlength).  
  
##  <a name="istemporary"></a>  CFileFind::IsTemporary  
 Volání této funkce člen k určení, pokud je nalezen soubor dočasný soubor.  
  
```  
BOOL IsTemporary() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Dočasný soubor je označené jako FILE_ATTRIBUTE_TEMPORARY, atribut souboru identifikovat v [WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) struktura. Dočasný soubor se používá pro dočasné úložiště. Aplikace by měla zapisovat do souboru, pouze pokud je to nezbytně nutné. Většina dat soubor zůstane v paměti bez vyprazdňuje na médium, protože soubor má být odstraněna.  
  
 Je třeba volat [FindNextFile](#findnextfile) alespoň jednou před voláním `IsTemporary`.  
  
 V tématu – členská funkce [MatchesMask](#matchesmask) úplný seznam atributů souboru.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CFileFind::GetLength](#getlength).  
  
##  <a name="m_ptm"></a>  CFileFind::m_pTM  
 Ukazatel na `CAtlTransactionManager` objektu.  
  
```  
CAtlTransactionManager* m_pTM;  
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="matchesmask"></a>  CFileFind::MatchesMask  
 Volání této funkce člen k testování atributy souborů v souboru nalezen.  
  
```  
virtual BOOL MatchesMask(DWORD dwMask) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `dwMask`  
 Určuje jeden nebo více atributů souboru v identifikovat [WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) struktura souboru nalezen. Chcete-li vyhledat několik atributů, použijte bitová hodnota OR (&#124;) operátor. Je přípustné libovolnou kombinaci následující atributy:  
  
-   FILE_ATTRIBUTE_ARCHIVE soubor je soubor archivu. Označení souborů k zálohování nebo odebrání aplikací pomocí tohoto atributu.  
  
-   Se komprimují FILE_ATTRIBUTE_COMPRESSED soubor nebo adresář. Pro soubor to znamená, že všechna data v souboru se komprimují. Pro adresář to znamená, že komprese je výchozí pro nově vytvořené soubory a podadresáře.  
  
-   FILE_ATTRIBUTE_DIRECTORY soubor je adresář.  
  
-   FILE_ATTRIBUTE_NORMAL soubor nemá nastavené žádné jiné atributy. Tento atribut je platný pouze v případě, že použitá samostatně. Všechny ostatní atributy souboru potlačí tento atribut.  
  
-   FILE_ATTRIBUTE_HIDDEN souboru je skrytý. Není mají být zahrnuty v seznamu běžných adresářů.  
  
-   FILE_ATTRIBUTE_READONLY soubor je jen pro čtení. Aplikace můžete přečíst soubor, ale nelze do něj zapisovat nebo odstranit.  
  
-   FILE_ATTRIBUTE_SYSTEM soubor je součástí nebo se používá výhradně podle operačního systému.  
  
-   FILE_ATTRIBUTE_TEMPORARY soubor se používá pro dočasné úložiště. Aplikace by měla zapisovat do souboru, pouze pokud je to nezbytně nutné. Většina dat soubor zůstane v paměti bez vyprazdňuje na médium, protože soubor má být odstraněna.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0. Chcete-li získat rozšířené informace o chybě, volejte funkci Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360).  
  
### <a name="remarks"></a>Poznámky  
 Je třeba volat [FindNextFile](#findnextfile) alespoň jednou před voláním `MatchesMask`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCFiles#35](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_5.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CFtpFileFind – třída](../../mfc/reference/cftpfilefind-class.md)   
 [CGopherFileFind – třída](../../mfc/reference/cgopherfilefind-class.md)   
 [CInternetFile – třída](../../mfc/reference/cinternetfile-class.md)   
 [CGopherFile – třída](../../mfc/reference/cgopherfile-class.md)   
 [CHttpFile – třída](../../mfc/reference/chttpfile-class.md)
