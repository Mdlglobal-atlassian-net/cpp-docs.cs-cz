---
title: Třída CAtlFile
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
ms.openlocfilehash: 39f323874ccde5178722235b9beb34c2572407a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318968"
---
# <a name="catlfile-class"></a>Třída CAtlFile

Tato třída poskytuje tenký obálku kolem rozhraní API pro zpracování souborů systému Windows.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CAtlFile : public CHandle
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CAtlFile::CAtlFile](#catlfile)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CAtlFile::Vytvořit](#create)|Volání této metody k vytvoření nebo otevření souboru.|
|[CAtlFile::Vyprázdnění](#flush)|Volání této metody vymazat vyrovnávací paměti pro soubor a způsobit všechna data ve vyrovnávací paměti, které mají být zapsány do souboru.|
|[CAtlFile::GetOverlappedResult](#getoverlappedresult)|Volání této metody získat výsledky překrývající se operace v souboru.|
|[CAtlFile::GetPosition](#getposition)|Volání této metody získat aktuální pozici ukazatele souboru ze souboru.|
|[CAtlFile::GetSize](#getsize)|Volání této metody získat velikost v bajtů souboru.|
|[CAtlFile::LockRange](#lockrange)|Volání této metody uzamknout oblast v souboru zabránit jiným procesům v přístupu k němu.|
|[CAtlFile::Číst](#read)|Volání této metody ke čtení dat ze souboru začínající na pozici označené ukazatelem souboru.|
|[CAtlFile::Hledat](#seek)|Volání této metody přesunout ukazatel souboru.|
|[CAtlFile::SetSize](#setsize)|Volání této metody nastavit velikost souboru.|
|[CAtlFile::UnlockRange](#unlockrange)|Volání této metody odemknout oblast souboru.|
|[CAtlFile::Zápis](#write)|Volání této metody pro zápis dat do souboru začíná na pozici označené ukazatelem souboru.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Name (Název)|Popis|
|----------|-----------------|
|[CAtlFile::m_pTM](#m_ptm)|Ukazatel `CAtlTransactionManager` na objekt|

## <a name="remarks"></a>Poznámky

Tuto třídu použijte, pokud jsou potřeby zpracování souborů poměrně jednoduché, ale je vyžadováno více abstrakce, než poskytuje rozhraní API systému Windows, bez zahrnutí závislostí knihovny MFC.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CHandle](../../atl/reference/chandle-class.md)

`CAtlFile`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlfile.h

## <a name="catlfilecatlfile"></a><a name="catlfile"></a>CAtlFile::CAtlFile

Konstruktor

```
CAtlFile() throw();
CAtlFile(CAtlTransactionManager* pTM = NULL) throw();
CAtlFile(CAtlFile& file) throw();
explicit CAtlFile(HANDLE hFile) throw();
```

### <a name="parameters"></a>Parametry

*Soubor*<br/>
Objekt souboru.

*hSoubor*<br/>
Popisovač souboru.

*Ptm*<br/>
Ukazatel na objekt CAtlTransactionManager

### <a name="remarks"></a>Poznámky

Konstruktor kopie přenese vlastnictví popisovače `CAtlFile` souboru z původního objektu na nově vytvořený objekt.

## <a name="catlfilecreate"></a><a name="create"></a>CAtlFile::Vytvořit

Volání této metody k vytvoření nebo otevření souboru.

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

*szNázev_souboru*<br/>
Název souboru

*dwDesiredAccess*<br/>
Požadovaný přístup. Viz *dwDesiredAccess* v [CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew) v sadě Windows SDK.

*dwShareMode*<br/>
Režim sdílení. Viz *dwShareMode* v `CreateFile`.

*dwCreationDispozice*<br/>
Stvoření dispozice. Viz *dwCreationDisposition* in `CreateFile`.

*dwFlagsAndAttributes*<br/>
Příznaky a atributy. Viz *dwFlagsAndAttributes* v `CreateFile`.

*LPSA*<br/>
Atributy zabezpečení. Viz *lpSecurityAttributes* in `CreateFile`.

*hTemplateFile*<br/>
Soubor šablony. Viz *hTemplateFile* v `CreateFile`.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volání [CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew) vytvořit nebo otevřít soubor.

## <a name="catlfileflush"></a><a name="flush"></a>CAtlFile::Vyprázdnění

Volání této metody vymazat vyrovnávací paměti pro soubor a způsobit všechna data ve vyrovnávací paměti, které mají být zapsány do souboru.

```
HRESULT Flush() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volá [FlushFileBuffers vyprázdnění](/windows/win32/api/fileapi/nf-fileapi-flushfilebuffers) dat ve vyrovnávací paměti do souboru.

## <a name="catlfilegetoverlappedresult"></a><a name="getoverlappedresult"></a>CAtlFile::GetOverlappedResult

Volání této metody získat výsledky překrývající se operace v souboru.

```
HRESULT GetOverlappedResult(
    LPOVERLAPPED pOverlapped,
    DWORD& dwBytesTransferred,
    BOOL bWait) throw();
```

### <a name="parameters"></a>Parametry

*přeskakované*<br/>
Překrývající se struktura. Viz *lpOverlapped* in [GetOverlappedResult](/windows/win32/api/ioapiset/nf-ioapiset-getoverlappedresult) in the Windows SDK.

*dwBytesPřevedeno*<br/>
Přenesené bajty. Viz *lpNumberOfBytesTransferred* in `GetOverlappedResult`.

*bPočkejte*<br/>
Možnost čekání. Viz *bWait* in `GetOverlappedResult`.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volání [GetOverlappedResult](/windows/win32/api/ioapiset/nf-ioapiset-getoverlappedresult) získat výsledky překrývající se operace v souboru.

## <a name="catlfilegetposition"></a><a name="getposition"></a>CAtlFile::GetPosition

Volání této metody získat aktuální pozici ukazatele souboru.

```
HRESULT GetPosition(ULONGLONG& nPos) const throw();
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Pozice v bajtů.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volá [SetFilePointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer) získat aktuální pozici ukazatele souboru.

## <a name="catlfilegetsize"></a><a name="getsize"></a>CAtlFile::GetSize

Volání této metody získat velikost v bajtů souboru.

```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>Parametry

*nLen*<br/>
Počet bajtů v souboru.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volání [GetFileSize](/windows/win32/api/fileapi/nf-fileapi-getfilesize) získat velikost v bajtů souboru.

## <a name="catlfilelockrange"></a><a name="lockrange"></a>CAtlFile::LockRange

Volání této metody uzamknout oblast v souboru zabránit jiným procesům v přístupu k němu.

```
HRESULT LockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Pozice v souboru, kde by měl začít zámek.

*nCount*<br/>
Délka rozsahu bajtů, který má být uzamčen.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volá [LockFile](/windows/win32/api/fileapi/nf-fileapi-lockfile) zamknout oblast v souboru. Zamykání bajtů v souboru zabraňuje přístupu k těmto bajtům jinými procesy. Můžete zamknout více než jednu oblast souboru, ale nejsou povoleny žádné překrývající se oblasti. Při odemknutí oblasti pomocí [CAtlFile::UnlockRange](#unlockrange), rozsah bajtů musí přesně odpovídat oblasti, která byla dříve uzamčena. `LockRange`neslučuje sousední oblasti; Pokud jsou dvě uzamčené oblasti sousedící, musíte je odemknout samostatně.

## <a name="catlfilem_ptm"></a><a name="m_ptm"></a>CAtlFile::m_pTM

Ukazatel na `CAtlTransactionManager` objekt.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Poznámky

## <a name="catlfileread"></a><a name="read"></a>CAtlFile::Číst

Volání této metody ke čtení dat ze souboru začínající na pozici označené ukazatelem souboru.

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

*pVyrovnávací paměť*<br/>
Ukazatel na vyrovnávací paměť, která obdrží data přečtená ze souboru.

*nBufVelikost*<br/>
Velikost vyrovnávací paměti v bajtů.

*nBajtyČíst*<br/>
Počet přečtených bajtů.

*přeskakované*<br/>
Překrývající se struktura. Viz *lpOverlapped* in [ReadFile](/windows/win32/api/fileapi/nf-fileapi-readfile) v sadě Windows SDK.

*pfnCompletionRoutine*<br/>
Rutina dokončení. Viz *lpCompletionRoutine* v [ReadFileEx](/windows/win32/api/fileapi/nf-fileapi-readfileex) v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

První tři formuláře volají [ReadFile](/windows/win32/api/fileapi/nf-fileapi-readfile), poslední [ReadFileEx](/windows/win32/api/fileapi/nf-fileapi-readfileex) pro čtení dat ze souboru. Pomocí [catlfile::Seek](#seek) přesuňte ukazatel souboru.

## <a name="catlfileseek"></a><a name="seek"></a>CAtlFile::Hledat

Volání této metody přesunout ukazatel souboru.

```
HRESULT Seek(
    LONGLONG nOffset,
    DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>Parametry

*nOffset*<br/>
Posun od počátečního bodu dané *dwFrom*.

*dwFrom*<br/>
Výchozí bod (FILE_BEGIN, FILE_CURRENT nebo FILE_END).

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volá [SetFilePointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer) přesunout ukazatel souboru.

## <a name="catlfilesetsize"></a><a name="setsize"></a>CAtlFile::SetSize

Volání této metody nastavit velikost souboru.

```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>Parametry

*nNewLen*<br/>
Nová délka souboru v bajtů.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volá [SetFilePointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer) a [SetEndOfFile](/windows/win32/api/fileapi/nf-fileapi-setendoffile) nastavit velikost souboru. Při návratu je ukazatel souboru umístěn na konci souboru.

## <a name="catlfileunlockrange"></a><a name="unlockrange"></a>CAtlFile::UnlockRange

Volání této metody odemknout oblast souboru.

```
HRESULT UnlockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Pozice v souboru, kde by mělo začít odemknutí.

*nCount*<br/>
Délka rozsahu bajtů, který má být odemčen.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volání [UnlockFile](/windows/win32/api/fileapi/nf-fileapi-unlockfile) odemknout oblast souboru.

## <a name="catlfilewrite"></a><a name="write"></a>CAtlFile::Zápis

Volání této metody pro zápis dat do souboru začíná na pozici označené ukazatelem souboru.

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

*pVyrovnávací paměť*<br/>
Vyrovnávací paměť obsahující data, která mají být zapsána do souboru.

*nBufVelikost*<br/>
Počet bajtů, které mají být přeneseny z vyrovnávací paměti.

*přeskakované*<br/>
Překrývající se struktura. Viz *lpOverlapped* in [WriteFile](/windows/win32/api/fileapi/nf-fileapi-writefile) v sadě Windows SDK.

*pfnCompletionRoutine*<br/>
Rutina dokončení. Viz *lpCompletionRoutine* v [WriteFileEx](/windows/win32/api/fileapi/nf-fileapi-writefileex) v sadě Windows SDK.

*pnBytesWritten*<br/>
Napsané bajty.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

První tři formuláře volání [WriteFile](/windows/win32/api/fileapi/nf-fileapi-writefile), poslední volání [WriteFileEx](/windows/win32/api/fileapi/nf-fileapi-writefileex) zapisovat data do souboru. Pomocí [catlfile::Seek](#seek) přesuňte ukazatel souboru.

## <a name="see-also"></a>Viz také

[Vzorek výběru](../../overview/visual-cpp-samples.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Třída CHandle](../../atl/reference/chandle-class.md)
