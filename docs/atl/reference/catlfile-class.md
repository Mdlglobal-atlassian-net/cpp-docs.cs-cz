---
title: "Třída CAtlFile | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlFile
- ATLFILE/ATL::CAtlFile
- ATLFILE/ATL::CAtlFile::CAtlFile
- ATLFILE/ATL::CAtlFile::Create
- ATLFILE/ATL::CAtlFile::Flush
- ATLFILE/ATL::CAtlFile::GetOverlappedResult
- ATLFILE/ATL::CAtlFile::GetPosition
- ATLFILE/ATL::CAtlFile::GetSize
- ATLFILE/ATL::CAtlFile::LockRange
- ATLFILE/ATL::CAtlFile::Read
- ATLFILE/ATL::CAtlFile::Seek
- ATLFILE/ATL::CAtlFile::SetSize
- ATLFILE/ATL::CAtlFile::UnlockRange
- ATLFILE/ATL::CAtlFile::Write
- ATLFILE/ATL::CAtlFile::m_pTM
dev_langs:
- C++
helpviewer_keywords:
- CAtlFile class
ms.assetid: 93ed160b-af2a-448c-9cbe-e5fa46c199bb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a66e697a3599e7bfeef0f1d5d147e19b668222ce
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="catlfile-class"></a>CAtlFile – třída
Tato třída poskytuje dynamické obálku kolem Windows zpracování souborů rozhraní API.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CAtlFile : public CHandle
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlFile::CAtlFile](#catlfile)|Konstruktor|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlFile::Create](#create)|Voláním této metody lze vytvořit nebo otevřít soubor.|  
|[CAtlFile::Flush](#flush)|Voláním této metody lze vymazat vyrovnávací paměti pro soubor a způsobit, že všechna data ve vyrovnávací paměti pro zápis do souboru.|  
|[CAtlFile::GetOverlappedResult](#getoverlappedresult)|Volejte tuto metodu za účelem získání výsledků překryté operace na souboru.|  
|[CAtlFile::GetPosition](#getposition)|Volejte tuto metodu za účelem získání aktuálního umístění ukazatele souboru ze souboru.|  
|[CAtlFile::GetSize](#getsize)|Volejte tuto metodu za účelem získání velikost v bajtech souboru.|  
|[CAtlFile::LockRange](#lockrange)|Volejte tuto metodu za účelem uzamčení oblasti, v souboru s jinými procesy zabránit v přístupu k jeho.|  
|[CAtlFile::Read](#read)|Volejte tuto metodu za účelem čtení dat ze souboru začínající na pozici ukazatele souboru.|  
|[CAtlFile::Seek](#seek)|Voláním této metody lze přesunout ukazatel souboru souboru.|  
|[CAtlFile::SetSize](#setsize)|Volejte tuto metodu a nastavit velikost souboru.|  
|[CAtlFile::UnlockRange](#unlockrange)|Volejte tuto metodu k odemknutí oblast souboru.|  
|[CAtlFile::Write](#write)|Voláním této metody lze zapisovat data do souboru začínající na pozici ukazatele souboru.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlFile::m_pTM](#m_ptm)|Ukazatel na `CAtlTransactionManager` objektu|  
  
## <a name="remarks"></a>Poznámky  
 Při zpracování souboru potřeba je poměrně jednoduché, ale další abstrakce, než poskytuje rozhraní API systému Windows je nutná, bez včetně závislostí MFC pomocí této třídy.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CHandle](../../atl/reference/chandle-class.md)  
  
 `CAtlFile`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlfile.h  
  
##  <a name="catlfile"></a>CAtlFile::CAtlFile  
 Konstruktor  
  
```
CAtlFile() throw();
CAtlFile(CAtlTransactionManager* pTM = NULL) throw();
CAtlFile(CAtlFile& file) throw();
explicit CAtlFile(HANDLE hFile) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `file`  
 Objekt souboru.  
  
 `hFile`  
 Popisovač souboru.  
  
 `pTM`  
 Ukazatel na objekt CAtlTransactionManager  
  
### <a name="remarks"></a>Poznámky  
 Konstruktor copy přenáší vlastnictví popisovač souboru z původní `CAtlFile` objekt, který chcete nově vytvořený objekt.  
  
##  <a name="create"></a>CAtlFile::Create  
 Voláním této metody lze vytvořit nebo otevřít soubor.  
  
```
HRESULT Create(
    LPCTSTR szFilename,
    DWORD dwDesiredAccess,
    DWORD dwShareMode,
    DWORD dwCreationDisposition,
    DWORD dwFlagsAndAttributes = FILE_ATTRIBUTE_NORMAL,
    LPSECURITY_ATTRIBUTES lpsa = NULL,
    HANDLE hTemplateFile = NULL) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *szFilename*  
 Název souboru  
  
 `dwDesiredAccess`  
 Požadovaný přístup. V tématu `dwDesiredAccess` v [CreateFile](http://msdn.microsoft.com/library/windows/desktop/aa363858) ve Windows SDK.  
  
 `dwShareMode`  
 Režim sdílené složky. V tématu `dwShareMode` v **CreateFile**.  
  
 `dwCreationDisposition`  
 Vytvoření dispozice. V tématu `dwCreationDisposition` v **CreateFile**.  
  
 `dwFlagsAndAttributes`  
 Příznaky a atributy. V tématu `dwFlagsAndAttributes` v **CreateFile**.  
  
 `lpsa`  
 Atributy zabezpečení. V tématu *lpSecurityAttributes* v **CreateFile**.  
  
 `hTemplateFile`  
 Soubor šablony. V tématu `hTemplateFile` v **CreateFile**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` na úspěch nebo Chyba `HRESULT` při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Volání [CreateFile](http://msdn.microsoft.com/library/windows/desktop/aa363858) vytvořit nebo otevřít soubor.  
  
##  <a name="flush"></a>CAtlFile::Flush  
 Voláním této metody lze vymazat vyrovnávací paměti pro soubor a způsobit, že všechna data ve vyrovnávací paměti pro zápis do souboru.  
  
```
HRESULT Flush() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` na úspěch nebo Chyba `HRESULT` při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Volání [FlushFileBuffers](http://msdn.microsoft.com/library/windows/desktop/aa364439) Vyprázdnit data ve vyrovnávací paměti do souboru.  
  
##  <a name="getoverlappedresult"></a>CAtlFile::GetOverlappedResult  
 Volejte tuto metodu za účelem získání výsledků překryté operace na souboru.  
  
```
HRESULT GetOverlappedResult(
    LPOVERLAPPED pOverlapped,
    DWORD& dwBytesTransferred,
    BOOL bWait) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pOverlapped`  
 Překryté struktury. V tématu `lpOverlapped` v [funkce GetOverlappedResult](http://msdn.microsoft.com/library/windows/desktop/ms683209) ve Windows SDK.  
  
 *dwBytesTransferred*  
 Počet bajtů přenesených. V tématu *lpNumberOfBytesTransferred* v `GetOverlappedResult`.  
  
 `bWait`  
 Možnost čekání. V tématu `bWait` v `GetOverlappedResult`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` na úspěch nebo Chyba `HRESULT` při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Volání [funkce GetOverlappedResult](http://msdn.microsoft.com/library/windows/desktop/ms683209) získat výsledky překryté operace na souboru.  
  
##  <a name="getposition"></a>CAtlFile::GetPosition  
 Volejte tuto metodu za účelem získání aktuálního umístění ukazatele souboru.  
  
```
HRESULT GetPosition(ULONGLONG& nPos) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nPos`  
 Pozice v bajtech.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` na úspěch nebo Chyba `HRESULT` při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Volání [funkce SetFilePointer](http://msdn.microsoft.com/library/windows/desktop/aa365541) získat aktuální umístění ukazatele souboru.  
  
##  <a name="getsize"></a>CAtlFile::GetSize  
 Volejte tuto metodu za účelem získání velikost v bajtech souboru.  
  
```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nLen`  
 Počet bajtů v souboru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` na úspěch nebo Chyba `HRESULT` při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Volání [funkce GetFileSize](http://msdn.microsoft.com/library/windows/desktop/aa364955) se získat velikost v bajtech souboru.  
  
##  <a name="lockrange"></a>CAtlFile::LockRange  
 Volejte tuto metodu za účelem uzamčení oblasti, v souboru s jinými procesy zabránit v přístupu k jeho.  
  
```
HRESULT LockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nPos`  
 Pozice v souboru, kde by měl začínat zámek.  
  
 `nCount`  
 Délka rozsah bajtů, které se uzamkne.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` na úspěch nebo Chyba `HRESULT` při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Volání [LockFile](http://msdn.microsoft.com/library/windows/desktop/aa365202) k uzamčení oblasti, v souboru. Zamykací bajty v souboru brání přístupu k těchto bajtů s jinými procesy. Zamknete více než jedné oblasti souboru, ale žádné překrývající se oblasti jsou povoleny. Při odemknutí oblasti pomocí [CAtlFile::UnlockRange](#unlockrange), rozsah bajtů musí přesně odpovídat oblasti, která byla dříve uzamčena. `LockRange`nesloučí přiléhající oblasti; Pokud jsou dva uzamčení oblasti vedle sebe, je třeba každý odemknout samostatně.  
  
##  <a name="m_ptm"></a>CAtlFile::m_pTM  
 Ukazatel na `CAtlTransactionManager` objektu.  
  
```
CAtlTransactionManager* m_pTM;
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="read"></a>CAtlFile::Read  
 Volejte tuto metodu za účelem čtení dat ze souboru začínající na pozici ukazatele souboru.  
  
```
HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    DWORD& nBytesRead) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped,
    LPOVERLAPPED_COMPLETION_ROUTINE pfnCompletionRoutine) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pBuffer`  
 Ukazatel do vyrovnávací paměti, která bude přijímat data načtená ze souboru.  
  
 `nBufSize`  
 Velikost vyrovnávací paměti v bajtech.  
  
 `nBytesRead`  
 Počet přečtených bajtů.  
  
 `pOverlapped`  
 Překryté struktury. V tématu `lpOverlapped` v [ReadFile](http://msdn.microsoft.com/library/windows/desktop/aa365467) ve Windows SDK.  
  
 `pfnCompletionRoutine`  
 Dokončení rutiny. V tématu *lpCompletionRoutine* v [readfileex spuštěná](http://msdn.microsoft.com/library/windows/desktop/aa365468) ve Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` na úspěch nebo Chyba `HRESULT` při selhání.  
  
### <a name="remarks"></a>Poznámky  
 První tři formuláře volání [ReadFile](http://msdn.microsoft.com/library/windows/desktop/aa365467), poslední [readfileex spuštěná](http://msdn.microsoft.com/library/windows/desktop/aa365468) čtení dat ze souboru. Použití [CAtlFile::Seek](#seek) přesunout ukazatele souboru.  
  
##  <a name="seek"></a>CAtlFile::Seek  
 Voláním této metody lze přesunout ukazatel souboru souboru.  
  
```
HRESULT Seek(
    LONGLONG nOffset,
    DWORD dwFrom = FILE_CURRENT) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nOffset`  
 Posun od počátečního bodu určeného vlastností `dwFrom`.  
  
 `dwFrom`  
 Výchozí bod (FILE_BEGIN, FILE_CURRENT nebo FILE_END).  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` na úspěch nebo Chyba `HRESULT` při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Volání [funkce SetFilePointer](http://msdn.microsoft.com/library/windows/desktop/aa365541) přesunout ukazatele souboru.  
  
##  <a name="setsize"></a>CAtlFile::SetSize  
 Volejte tuto metodu a nastavit velikost souboru.  
  
```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nNewLen`  
 Nové délka souboru v bajtech.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` na úspěch nebo Chyba `HRESULT` při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Volání [funkce SetFilePointer](http://msdn.microsoft.com/library/windows/desktop/aa365541) a [funkce SetEndOfFile](http://msdn.microsoft.com/library/windows/desktop/aa365531) nastavit velikost souboru. Při návratu ukazatele souboru je nastavený na konci souboru.  
  
##  <a name="unlockrange"></a>CAtlFile::UnlockRange  
 Volejte tuto metodu k odemknutí oblast souboru.  
  
```
HRESULT UnlockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nPos`  
 Pozice v souboru, kde by měl začínat odemčení.  
  
 `nCount`  
 Délka rozsahu bajtů k odemknutí.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` na úspěch nebo Chyba `HRESULT` při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Volání [UnlockFile](http://msdn.microsoft.com/library/windows/desktop/aa365715) k odemknutí oblast souboru.  
  
##  <a name="write"></a>CAtlFile::Write  
 Voláním této metody lze zapisovat data do souboru začínající na pozici ukazatele souboru.  
  
```
HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped,
    LPOVERLAPPED_COMPLETION_ROUTINE pfnCompletionRoutine) throw();

HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    DWORD* pnBytesWritten = NULL) throw();

HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pBuffer`  
 Vyrovnávací paměť obsahující data, která má být zapsán do souboru.  
  
 `nBufSize`  
 Počet bajtů, které se mají přenést z vyrovnávací paměti.  
  
 `pOverlapped`  
 Překryté struktury. V tématu `lpOverlapped` v [WriteFile](http://msdn.microsoft.com/library/windows/desktop/aa365747) ve Windows SDK.  
  
 `pfnCompletionRoutine`  
 Dokončení rutiny. V tématu *lpCompletionRoutine* v [writefileex spuštěná](http://msdn.microsoft.com/library/windows/desktop/aa365748) ve Windows SDK.  
  
 `pnBytesWritten`  
 Zapsaných bajtů.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` na úspěch nebo Chyba `HRESULT` při selhání.  
  
### <a name="remarks"></a>Poznámky  
 První tři formuláře volání [WriteFile](http://msdn.microsoft.com/library/windows/desktop/aa365747), poslední volání [writefileex spuštěná](http://msdn.microsoft.com/library/windows/desktop/aa365748) zapsat data do souboru. Použití [CAtlFile::Seek](#seek) přesunout ukazatele souboru.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka rámeček](../../visual-cpp-samples.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)   
 [CHandle – třída](../../atl/reference/chandle-class.md)
