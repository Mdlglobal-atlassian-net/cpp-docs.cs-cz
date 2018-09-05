---
title: Catlfile – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d3d6ff72f9f5011d7c4e0f0b65cca9a82227b70d
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43753250"
---
# <a name="catlfile-class"></a>Catlfile – třída

Tato třída poskytuje rozhraní API pro zpracování souborů dynamického zajišťování obálku Windows.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

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
|[CAtlFile::Create](#create)|Volejte tuto metodu za účelem vytvoření nebo otevření souboru.|
|[CAtlFile::Flush](#flush)|Voláním této metody lze vymazat vyrovnávací paměť pro soubor a způsobit, že všechna data ve vyrovnávací paměti k zápisu do souboru.|
|[CAtlFile::GetOverlappedResult](#getoverlappedresult)|Volejte tuto metodu za účelem získání výsledků překrytá operace na souboru.|
|[CAtlFile::GetPosition](#getposition)|Voláním této metody k získání aktuální ukazatel pozice v souboru ze souboru.|
|[CAtlFile::GetSize](#getsize)|Volejte tuto metodu za účelem získání velikost v bajtech souboru.|
|[CAtlFile::LockRange](#lockrange)|Volejte tuto metodu za účelem uzamčení oblasti v souboru, který má bránit dalším procesům v přístupu k nim.|
|[CAtlFile::Read](#read)|Volejte tuto metodu za účelem čtení dat ze souboru začínající na pozici ukazatele souboru.|
|[CAtlFile::Seek](#seek)|Voláním této metody lze přesunout ukazatel na soubor souboru.|
|[CAtlFile::SetSize](#setsize)|Voláním této metody lze nastavit velikost souboru.|
|[CAtlFile::UnlockRange](#unlockrange)|Volejte tuto metodu za účelem odemknout oblasti souboru.|
|[CAtlFile::Write](#write)|Volání této metody zapsat data do souboru začínající na pozici ukazatele souboru.|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CAtlFile::m_pTM](#m_ptm)|Ukazatel na `CAtlTransactionManager` objektu|

## <a name="remarks"></a>Poznámky

Při zpracování souborů potřeby je poměrně jednoduchá, ale další abstrakce, než poskytuje rozhraní API Windows je nutné, bez zahrnutí knihovny MFC závislosti, použijte tuto třídu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Chandle –](../../atl/reference/chandle-class.md)

`CAtlFile`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlfile.h

##  <a name="catlfile"></a>  CAtlFile::CAtlFile

Konstruktor

```
CAtlFile() throw();
CAtlFile(CAtlTransactionManager* pTM = NULL) throw();
CAtlFile(CAtlFile& file) throw();
explicit CAtlFile(HANDLE hFile) throw();
```

### <a name="parameters"></a>Parametry

*Soubor*  
Soubor objektu.

*hfile –*  
Popisovač souboru.

*Druh*  
Ukazatel na catltransactionmanager – objekt

### <a name="remarks"></a>Poznámky

Kopírovací konstruktor převede vlastnictví popisovač souboru z původní `CAtlFile` do nově vytvořeného objektu.

##  <a name="create"></a>  CAtlFile::Create

Volejte tuto metodu za účelem vytvoření nebo otevření souboru.

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

*dwDesiredAccess*  
Požadovaný přístup. Zobrazit *dwDesiredAccess* v [CreateFile](/windows/desktop/api/fileapi/nf-fileapi-createfilea) v sadě Windows SDK.

*dwShareMode*  
Režim sdílené složky. Zobrazit *dwShareMode* v `CreateFile`.

*dwCreationDisposition*  
Vytvoření dispozice. Zobrazit *dwCreationDisposition* v `CreateFile`.

*dwFlagsAndAttributes*  
Příznaky a atributy. Zobrazit *dwFlagsAndAttributes* v `CreateFile`.

*lpsa*  
Atributy zabezpečení. Zobrazit *lpSecurityAttributes* v `CreateFile`.

*hTemplateFile*  
Soubor šablony. Zobrazit *hTemplateFile* v `CreateFile`.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volání [CreateFile](/windows/desktop/api/fileapi/nf-fileapi-createfilea) vytvořit nebo otevřít soubor.

##  <a name="flush"></a>  CAtlFile::Flush

Voláním této metody lze vymazat vyrovnávací paměť pro soubor a způsobit, že všechna data ve vyrovnávací paměti k zápisu do souboru.

```
HRESULT Flush() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volání [FlushFileBuffers](/windows/desktop/api/fileapi/nf-fileapi-flushfilebuffers) Vyprázdnit data ve vyrovnávací paměti do souboru.

##  <a name="getoverlappedresult"></a>  CAtlFile::GetOverlappedResult

Volejte tuto metodu za účelem získání výsledků překrytá operace na souboru.

```
HRESULT GetOverlappedResult(
    LPOVERLAPPED pOverlapped,
    DWORD& dwBytesTransferred,
    BOOL bWait) throw();
```

### <a name="parameters"></a>Parametry

*pOverlapped*  
Překryté struktury. Zobrazit *lpOverlapped* v [GetOverlappedResult](/windows/desktop/api/ioapiset/nf-ioapiset-getoverlappedresult) v sadě Windows SDK.

*dwBytesTransferred*  
Počet bajtů přenesených. Zobrazit *lpNumberOfBytesTransferred* v `GetOverlappedResult`.

*bWait*  
Políčko čekání. Zobrazit *bWait* v `GetOverlappedResult`.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volání [GetOverlappedResult](/windows/desktop/api/ioapiset/nf-ioapiset-getoverlappedresult) k získání požadovaných výsledků překrytá operace na souboru.

##  <a name="getposition"></a>  CAtlFile::GetPosition

Voláním této metody k získání aktuální ukazatel pozice v souboru.

```
HRESULT GetPosition(ULONGLONG& nPos) const throw();
```

### <a name="parameters"></a>Parametry

*nPos –*  
Pozice v bajtech.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volání [funkce SetFilePointer](/windows/desktop/api/fileapi/nf-fileapi-setfilepointer) zobrazíte aktuální ukazatel pozice v souboru.

##  <a name="getsize"></a>  CAtlFile::GetSize

Volejte tuto metodu za účelem získání velikost v bajtech souboru.

```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>Parametry

*nLen*  
Počet bajtů v souboru.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volání [funkce GetFileSize](/windows/desktop/api/fileapi/nf-fileapi-getfilesize) získáte velikost v bajtech souboru.

##  <a name="lockrange"></a>  CAtlFile::LockRange

Volejte tuto metodu za účelem uzamčení oblasti v souboru, který má bránit dalším procesům v přístupu k nim.

```
HRESULT LockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>Parametry

*nPos –*  
Pozice v souboru, ve kterém chcete spustit zámek.

*nCount*  
Délka rozsahu bajtů uzamčení.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volání [LockFile](/windows/desktop/api/fileapi/nf-fileapi-lockfile) k uzamčení oblasti v souboru. Zamykací bajty v souboru brání v přístupu k těmto bajtů s jinými procesy. Můžeš více než jedné oblasti souboru, ale žádné překrývající se oblasti jsou povoleny. Po odemknutí oblast pomocí [CAtlFile::UnlockRange](#unlockrange), rozsah bajtů musí přesně odpovídat oblasti, která dříve byla uzamčena. `LockRange` nesloučí sousední oblasti; Pokud jsou dvě oblasti uzamčené vedle sebe, musí každý odemknout samostatně.

##  <a name="m_ptm"></a>  CAtlFile::m_pTM

Ukazatel `CAtlTransactionManager` objektu.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Poznámky

##  <a name="read"></a>  CAtlFile::Read

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

*pBuffer*  
Ukazatel do vyrovnávací paměti, která bude přijímat data načtená ze souboru.

*nBufSize*  
Velikost vyrovnávací paměti v bajtech.

*nBytesRead*  
Počet přečtených bajtů.

*pOverlapped*  
Překryté struktury. Zobrazit *lpOverlapped* v [ReadFile](/windows/desktop/api/fileapi/nf-fileapi-readfile) v sadě Windows SDK.

*pfnCompletionRoutine*  
Dokončení rutiny. Zobrazit *lpCompletionRoutine* v [readfileex spuštěná](/windows/desktop/api/fileapi/nf-fileapi-readfileex) v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

První tři formuláře volání [ReadFile](/windows/desktop/api/fileapi/nf-fileapi-readfile), poslední [readfileex spuštěná](/windows/desktop/api/fileapi/nf-fileapi-readfileex) číst data ze souboru. Použití [CAtlFile::Seek](#seek) přesunout ukazatel souboru.

##  <a name="seek"></a>  CAtlFile::Seek

Voláním této metody lze přesunout ukazatel na soubor souboru.

```
HRESULT Seek(
    LONGLONG nOffset,
    DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>Parametry

*nOffset*  
Posun od počátečního bodu *dwFrom*.

*dwFrom*  
Počáteční bod (FILE_BEGIN, FILE_CURRENT nebo FILE_END).

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volání [funkce SetFilePointer](/windows/desktop/api/fileapi/nf-fileapi-setfilepointer) přesunout ukazatel souboru.

##  <a name="setsize"></a>  CAtlFile::SetSize

Voláním této metody lze nastavit velikost souboru.

```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>Parametry

*nNewLen*  
Novou velikost souboru v bajtech.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volání [funkce SetFilePointer](/windows/desktop/api/fileapi/nf-fileapi-setfilepointer) a [funkce SetEndOfFile](/windows/desktop/api/fileapi/nf-fileapi-setendoffile) nastavit velikost souboru. Při návratu je ukazatel na soubor umístěn na konci souboru.

##  <a name="unlockrange"></a>  CAtlFile::UnlockRange

Volejte tuto metodu za účelem odemknout oblasti souboru.

```
HRESULT UnlockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>Parametry

*nPos –*  
Pozice v souboru, ve kterém chcete spustit odemknout.

*nCount*  
Délka rozsahu bajtů k odemknutí.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volání [UnlockFile](/windows/desktop/api/fileapi/nf-fileapi-unlockfile) k odemknutí oblasti souboru.

##  <a name="write"></a>  CAtlFile::Write

Volání této metody zapsat data do souboru začínající na pozici ukazatele souboru.

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

*pBuffer*  
Vyrovnávací paměť obsahující data, která mají být zapsána do souboru.

*nBufSize*  
Počet bajtů, které mají být přeneseny z vyrovnávací paměti.

*pOverlapped*  
Překryté struktury. Zobrazit *lpOverlapped* v [WriteFile](/windows/desktop/api/fileapi/nf-fileapi-writefile) v sadě Windows SDK.

*pfnCompletionRoutine*  
Dokončení rutiny. Zobrazit *lpCompletionRoutine* v [writefileex spuštěná](/windows/desktop/api/fileapi/nf-fileapi-writefileex) v sadě Windows SDK.

*pnBytesWritten*  
Zapsaných bajtů.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

První tři formuláře volání [WriteFile](/windows/desktop/api/fileapi/nf-fileapi-writefile), poslední volání [writefileex spuštěná](/windows/desktop/api/fileapi/nf-fileapi-writefileex) k zápisu dat do souboru. Použití [CAtlFile::Seek](#seek) přesunout ukazatel souboru.

## <a name="see-also"></a>Viz také

[Výběr ukázky](../../visual-cpp-samples.md)   
[Přehled tříd](../../atl/atl-class-overview.md)   
[CHandle – třída](../../atl/reference/chandle-class.md)
