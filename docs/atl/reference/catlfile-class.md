---
title: CAtlFile – třída
ms.date: 11/04/2016
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
helpviewer_keywords:
- CAtlFile class
ms.assetid: 93ed160b-af2a-448c-9cbe-e5fa46c199bb
ms.openlocfilehash: 83a0a89bf6e2e21be33cf8c6003228111eff5394
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168108"
---
# <a name="catlfile-class"></a>CAtlFile – třída

Tato třída poskytuje tenké obálky kolem rozhraní API pro zpracování souborů systému Windows.

> [!IMPORTANT]
> Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
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
|[CAtlFile:: Create](#create)|Voláním této metody vytvoříte nebo otevřete soubor.|
|[CAtlFile:: flush](#flush)|Voláním této metody vymažete vyrovnávací paměti pro daný soubor a způsobí, že všechna data uložená do vyrovnávací paměti budou zapsána do souboru.|
|[CAtlFile:: funkce GetOverlappedResult](#getoverlappedresult)|Voláním této metody získáte výsledky překrývající operace v souboru.|
|[CAtlFile:: GetPosition](#getposition)|Voláním této metody získá aktuální pozice ukazatele na soubor ze souboru.|
|[CAtlFile:: GetSize](#getsize)|Voláním této metody získáte velikost souboru v bajtech.|
|[CAtlFile::LockRange](#lockrange)|Voláním této metody zamknete oblast v souboru, abyste zabránili ostatním procesům v přístupu k ní.|
|[CAtlFile:: Read](#read)|Voláním této metody načtete data ze souboru, který začíná na pozici označené ukazatelem souboru.|
|[CAtlFile:: Seek](#seek)|Voláním této metody přesunete ukazatel souboru souboru.|
|[CAtlFile:: SetSize](#setsize)|Voláním této metody nastavíte velikost souboru.|
|[CAtlFile::UnlockRange](#unlockrange)|Zavolejte tuto metodu pro odemčení oblasti souboru.|
|[CAtlFile:: Write](#write)|Voláním této metody zapíšete data do souboru počínaje pozicí určenou ukazatelem souboru.|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CAtlFile:: m_pTM](#m_ptm)|Ukazatel na `CAtlTransactionManager` objekt|

## <a name="remarks"></a>Poznámky

Tuto třídu použijte, když jsou potřeby zpracování souborů relativně jednoduché, ale vyžaduje se více abstrakcí, než je vyžadováno rozhraní API systému Windows, aniž by to mělo zahrnovat závislosti MFC.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CHandle](../../atl/reference/chandle-class.md)

`CAtlFile`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlfile. h

## <a name="catlfilecatlfile"></a><a name="catlfile"></a>CAtlFile::CAtlFile

Konstruktor

```cpp
CAtlFile() throw();
CAtlFile(CAtlTransactionManager* pTM = NULL) throw();
CAtlFile(CAtlFile& file) throw();
explicit CAtlFile(HANDLE hFile) throw();
```

### <a name="parameters"></a>Parametry

*souborů*<br/>
Objekt souboru.

*hFile*<br/>
Popisovač souboru.

*pTM*<br/>
Ukazatel na objekt CAtlTransactionManager

### <a name="remarks"></a>Poznámky

Kopírovací konstruktor převádí vlastnictví popisovače souboru z původního `CAtlFile` objektu na nově vytvořený objekt.

## <a name="catlfilecreate"></a><a name="create"></a>CAtlFile:: Create

Voláním této metody vytvoříte nebo otevřete soubor.

```cpp
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

*szFilename*<br/>
Název souboru

*dwDesiredAccess*<br/>
Požadovaný přístup. Viz *dwDesiredAccess* v [CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew) v Windows SDK.

*dwShareMode*<br/>
Režim sdílení. Viz *dwShareMode* v `CreateFile`.

*dwCreationDisposition*<br/>
Dispozice při vytváření. Viz *dwCreationDisposition* v `CreateFile`.

*dwFlagsAndAttributes*<br/>
Příznaky a atributy. Viz *dwFlagsAndAttributes* v `CreateFile`.

*lpsa*<br/>
Atributy zabezpečení Viz *lpSecurityAttributes* v `CreateFile`.

*hTemplateFile*<br/>
Soubor šablony. Viz *hTemplateFile* v `CreateFile`.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volá [CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew) pro vytvoření nebo otevření souboru.

## <a name="catlfileflush"></a><a name="flush"></a>CAtlFile:: flush

Voláním této metody vymažete vyrovnávací paměti pro daný soubor a způsobí, že všechna data uložená do vyrovnávací paměti budou zapsána do souboru.

```cpp
HRESULT Flush() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Zavolá [FlushFileBuffers](/windows/win32/api/fileapi/nf-fileapi-flushfilebuffers) k vyprázdnění dat do vyrovnávací paměti do souboru.

## <a name="catlfilegetoverlappedresult"></a><a name="getoverlappedresult"></a>CAtlFile:: funkce GetOverlappedResult

Voláním této metody získáte výsledky překrývající operace v souboru.

```cpp
HRESULT GetOverlappedResult(
    LPOVERLAPPED pOverlapped,
    DWORD& dwBytesTransferred,
    BOOL bWait) throw();
```

### <a name="parameters"></a>Parametry

*pOverlapped*<br/>
Překrytá struktura. Viz *lpOverlapped* v [funkce GetOverlappedResult](/windows/win32/api/ioapiset/nf-ioapiset-getoverlappedresult) ve Windows SDK.

*dwBytesTransferred*<br/>
Přenesené bajty. Viz *lpNumberOfBytesTransferred* v `GetOverlappedResult`.

*bWait*<br/>
Možnost čekání. Viz *bWait* v `GetOverlappedResult`.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volá [funkce GetOverlappedResult](/windows/win32/api/ioapiset/nf-ioapiset-getoverlappedresult) k získání výsledků překrývající se operace v souboru.

## <a name="catlfilegetposition"></a><a name="getposition"></a>CAtlFile:: GetPosition

Zavolejte tuto metodu pro získání aktuálního umístění ukazatele na soubor.

```cpp
HRESULT GetPosition(ULONGLONG& nPos) const throw();
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Pozice v bajtech.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volá [funkce SetFilePointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer) k získání aktuálního umístění ukazatele na soubor.

## <a name="catlfilegetsize"></a><a name="getsize"></a>CAtlFile:: GetSize

Voláním této metody získáte velikost souboru v bajtech.

```cpp
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>Parametry

*nLen*<br/>
Počet bajtů v souboru.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volá [funkce GetFileSize](/windows/win32/api/fileapi/nf-fileapi-getfilesize) , aby získala velikost souboru v bajtech.

## <a name="catlfilelockrange"></a><a name="lockrange"></a>CAtlFile::LockRange

Voláním této metody zamknete oblast v souboru, abyste zabránili ostatním procesům v přístupu k ní.

```cpp
HRESULT LockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Pozice v souboru, kde má zámek začínat.

*nCount*<br/>
Délka rozsahu bajtů, který má být uzamčen.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volá [LockFile](/windows/win32/api/fileapi/nf-fileapi-lockfile) k uzamknutí oblasti v souboru. Uzamykání bajtů v souboru brání v přístupu k těmto bajtům jiným procesům. Můžete uzamknout více než jednu oblast souboru, ale nejsou povoleny žádné překrývající se oblasti. Když odemknete oblast pomocí [CAtlFile:: UnlockRange](#unlockrange), musí rozsah bajtů přesně odpovídat oblasti, která byla dříve uzamčena. `LockRange`neslučuje sousední oblasti; Pokud se dvě uzamčené oblasti sousedí, je nutné je všechny samostatně odemknout.

## <a name="catlfilem_ptm"></a><a name="m_ptm"></a>CAtlFile:: m_pTM

Ukazatel na `CAtlTransactionManager` objekt.

```cpp
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Poznámky

## <a name="catlfileread"></a><a name="read"></a>CAtlFile:: Read

Voláním této metody načtete data ze souboru, který začíná na pozici označené ukazatelem souboru.

```cpp
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

*pBuffer*<br/>
Ukazatel na vyrovnávací paměť, která bude přijímat data načtená ze souboru.

*nBufSize*<br/>
Velikost vyrovnávací paměti v bajtech.

*nBytesRead*<br/>
Počet přečtených bajtů.

*pOverlapped*<br/>
Překrytá struktura. Viz *lpOverlapped* v funkci [ReadFile](/windows/win32/api/fileapi/nf-fileapi-readfile) v Windows SDK.

*pfnCompletionRoutine*<br/>
Rutina dokončení. Viz *lpCompletionRoutine* v [ReadFileEx](/windows/win32/api/fileapi/nf-fileapi-readfileex) ve Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

První tři formuláře volají funkci [ReadFile](/windows/win32/api/fileapi/nf-fileapi-readfile), poslední [ReadFileEx](/windows/win32/api/fileapi/nf-fileapi-readfileex) ke čtení dat ze souboru. Použijte [CAtlFile:: Seek](#seek) pro přesunutí ukazatele na soubor.

## <a name="catlfileseek"></a><a name="seek"></a>CAtlFile:: Seek

Voláním této metody přesunete ukazatel souboru souboru.

```cpp
HRESULT Seek(
    LONGLONG nOffset,
    DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>Parametry

*nOffset*<br/>
Posun od počátečního bodu, který je dán hodnotou *dwFrom*.

*dwFrom*<br/>
Výchozí bod (FILE_BEGIN, FILE_CURRENT nebo FILE_END).

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volá [funkce SetFilePointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer) , aby se přesunul ukazatel na soubor.

## <a name="catlfilesetsize"></a><a name="setsize"></a>CAtlFile:: SetSize

Voláním této metody nastavíte velikost souboru.

```cpp
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>Parametry

*nNewLen*<br/>
Nová délka souboru v bajtech

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Zavolá [funkce SetFilePointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer) a [funkce SetEndOfFile](/windows/win32/api/fileapi/nf-fileapi-setendoffile) , aby se nastavila velikost souboru. Při návratu je ukazatel na soubor umístěný na konci souboru.

## <a name="catlfileunlockrange"></a><a name="unlockrange"></a>CAtlFile::UnlockRange

Zavolejte tuto metodu pro odemčení oblasti souboru.

```cpp
HRESULT UnlockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Pozice v souboru, kde má začít odemčení.

*nCount*<br/>
Délka rozsahu bajtů, který má být odemčen.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volá [UnlockFile](/windows/win32/api/fileapi/nf-fileapi-unlockfile) k odemknutí oblasti souboru.

## <a name="catlfilewrite"></a><a name="write"></a>CAtlFile:: Write

Voláním této metody zapíšete data do souboru počínaje pozicí určenou ukazatelem souboru.

```cpp
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

*pBuffer*<br/>
Vyrovnávací paměť obsahující data, která mají být zapsána do souboru.

*nBufSize*<br/>
Počet bajtů, které mají být přeneseny z vyrovnávací paměti.

*pOverlapped*<br/>
Překrytá struktura. Viz *lpOverlapped* v [WriteFile](/windows/win32/api/fileapi/nf-fileapi-writefile) v Windows SDK.

*pfnCompletionRoutine*<br/>
Rutina dokončení. Viz *lpCompletionRoutine* v [WriteFileEx](/windows/win32/api/fileapi/nf-fileapi-writefileex) ve Windows SDK.

*pnBytesWritten*<br/>
Zapsané bajty.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

První tři formuláře volají metodu [WriteFile](/windows/win32/api/fileapi/nf-fileapi-writefile)a poslední volá [WriteFileEx](/windows/win32/api/fileapi/nf-fileapi-writefileex) k zápisu dat do souboru. Použijte [CAtlFile:: Seek](#seek) pro přesunutí ukazatele na soubor.

## <a name="see-also"></a>Viz také

[Ukázka běžícího textu](../../overview/visual-cpp-samples.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[CHandle – třída](../../atl/reference/chandle-class.md)
