---
title: Třída CAtlTemporaryFile
ms.date: 11/04/2016
f1_keywords:
- CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile::CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile::Close
- ATLFILE/ATL::CAtlTemporaryFile::Create
- ATLFILE/ATL::CAtlTemporaryFile::Flush
- ATLFILE/ATL::CAtlTemporaryFile::GetPosition
- ATLFILE/ATL::CAtlTemporaryFile::GetSize
- ATLFILE/ATL::CAtlTemporaryFile::HandsOff
- ATLFILE/ATL::CAtlTemporaryFile::HandsOn
- ATLFILE/ATL::CAtlTemporaryFile::LockRange
- ATLFILE/ATL::CAtlTemporaryFile::Read
- ATLFILE/ATL::CAtlTemporaryFile::Seek
- ATLFILE/ATL::CAtlTemporaryFile::SetSize
- ATLFILE/ATL::CAtlTemporaryFile::TempFileName
- ATLFILE/ATL::CAtlTemporaryFile::UnlockRange
- ATLFILE/ATL::CAtlTemporaryFile::Write
helpviewer_keywords:
- CAtlTemporaryFile class
ms.assetid: 05f0f2a5-94f6-4594-8dae-b114292ff5f9
ms.openlocfilehash: 605e4bcbe7208b18d8d1a50507e8e142a93bde5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321311"
---
# <a name="catltemporaryfile-class"></a>Třída CAtlTemporaryFile

Tato třída poskytuje metody pro vytvoření a použití dočasného souboru.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CAtlTemporaryFile
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)|Konstruktor|
|[CAtlTemporaryFile::~CAtlTemporaryFile](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CAtlTemporaryFile::Zavřít](#close)|Volání této metody zavřít dočasný soubor a odstranit jeho obsah nebo uložit pod zadaný název souboru.|
|[CAtlTemporaryFile::Vytvořit](#create)|Volání této metody k vytvoření dočasného souboru.|
|[CAtlTemporaryFile::Flush](#flush)|Volání této metody vynutit všechna data zbývající ve vyrovnávací paměti souboru, které mají být zapsány do dočasného souboru.|
|[CAtlTemporaryFile::GetPosition](#getposition)|Volání této metody získat aktuální pozici ukazatele souboru.|
|[CAtlTemporaryFile::GetSize](#getsize)|Volání této metody získat velikost v bajtů dočasného souboru.|
|[CAtlTemporaryFile::HandsOff](#handsoff)|Volání této metody zrušit přidružení souboru od objektu. `CAtlTemporaryFile`|
|[CAtlTemporaryFile::HandsOn](#handson)|Volání této metody otevřít existující dočasný soubor a umístit ukazatel na konci souboru.|
|[CAtlTemporaryFile::LockRange](#lockrange)|Volání této metody uzamknout oblast v souboru zabránit jiným procesům v přístupu k němu.|
|[CAtlTemporaryFile::Číst](#read)|Volání této metody ke čtení dat z dočasného souboru začíná na pozici označené ukazatelem souboru.|
|[CAtlTemporaryFile::Hledat](#seek)|Volání této metody přesunout ukazatel souboru dočasného souboru.|
|[CAtlTemporaryFile::SetSize](#setsize)|Volání této metody nastavit velikost dočasného souboru.|
|[CAtlTemporaryFile::TempFileName](#tempfilename)|Volání této metody vrátit název dočasného souboru.|
|[CAtlTemporaryFile::UnlockRange](#unlockrange)|Volání této metody odemknout oblast dočasného souboru.|
|[CAtlTemporaryFile::Zápis](#write)|Volání této metody pro zápis dat do dočasného souboru začíná na pozici označené ukazatelem souboru.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CAtlTemporaryFile::POPISOVAČ operátora](#operator_handle)|Vrátí popisovač dočasného souboru.|

## <a name="remarks"></a>Poznámky

`CAtlTemporaryFile`usnadňuje vytvoření a použití dočasného souboru. Soubor je automaticky pojmenován, otevřen, uzavřen a odstraněn. Pokud je obsah souboru vyžadován po zavření souboru, lze jej uložit do nového souboru se zadaným názvem.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlfile.h

## <a name="example"></a>Příklad

Viz příklad [catltemporaryfile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfilecatltemporaryfile"></a><a name="catltemporaryfile"></a>CAtlTemporaryFile::CAtlTemporaryFile

Konstruktor

```
CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>Poznámky

Soubor není ve skutečnosti otevřen, dokud není provedeno volání [CAtlTemporaryFile::Create](#create).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#73](../../atl/codesnippet/cpp/catltemporaryfile-class_1.cpp)]

## <a name="catltemporaryfilecatltemporaryfile"></a><a name="dtor"></a>CAtlTemporaryFile::~CAtlTemporaryFile

Destruktor.

```
~CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>Poznámky

Destruktor volá [CAtlTemporaryFile::Close](#close).

## <a name="catltemporaryfileclose"></a><a name="close"></a>CAtlTemporaryFile::Zavřít

Volání této metody zavřít dočasný soubor a odstranit jeho obsah nebo uložit pod zadaný název souboru.

```
HRESULT Close(LPCTSTR szNewName = NULL) throw();
```

### <a name="parameters"></a>Parametry

*szNewName*<br/>
Název nového souboru pro uložení obsahu dočasného souboru. Pokud je tento argument NULL, obsah dočasného souboru jsou odstraněny.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="example"></a>Příklad

Viz příklad [catltemporaryfile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfilecreate"></a><a name="create"></a>CAtlTemporaryFile::Vytvořit

Volání této metody k vytvoření dočasného souboru.

```
HRESULT Create(LPCTSTR pszDir = NULL, DWORD dwDesiredAccess = GENERIC_WRITE) throw();
```

### <a name="parameters"></a>Parametry

*pszDir*<br/>
Cesta pro dočasný soubor. Pokud je to NULL, [GetTempPath](/windows/win32/api/fileapi/nf-fileapi-gettemppathw) bude volána přiřadit cestu.

*dwDesiredAccess*<br/>
Požadovaný přístup. Viz *dwDesiredAccess* v [CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew) v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="example"></a>Příklad

Viz příklad [catltemporaryfile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfileflush"></a><a name="flush"></a>CAtlTemporaryFile::Flush

Volání této metody vynutit všechna data zbývající ve vyrovnávací paměti souboru, které mají být zapsány do dočasného souboru.

```
HRESULT Flush() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Podobně jako [CAtlTemporaryFile::HandsOff](#handsoff), s tím rozdílem, že soubor není uzavřen.

### <a name="example"></a>Příklad

Viz příklad [catltemporaryfile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfilegetposition"></a><a name="getposition"></a>CAtlTemporaryFile::GetPosition

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

Chcete-li změnit polohu ukazatele souboru, použijte [CAtlTemporaryFile::Seek](#seek).

## <a name="catltemporaryfilegetsize"></a><a name="getsize"></a>CAtlTemporaryFile::GetSize

Volání této metody získat velikost v bajtů dočasného souboru.

```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>Parametry

*nLen*<br/>
Počet bajtů v souboru.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="catltemporaryfilehandsoff"></a><a name="handsoff"></a>CAtlTemporaryFile::HandsOff

Volání této metody zrušit přidružení souboru od objektu. `CAtlTemporaryFile`

```
HRESULT HandsOff() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

`HandsOff`a [CAtlTemporaryFile::HandsOn](#handson) se používají k zrušení přidružení souboru k objektu a v případě potřeby jej znovu připojit. `HandsOff`vynutí všechna data zbývající ve vyrovnávací paměti souboru, která mají být zapsána do dočasného souboru, a potom soubor zavřete. Pokud chcete soubor zavřít a odstranit trvale nebo chcete zavřít a zachovat obsah souboru s daným názvem, použijte [CAtlTemporaryFile::Close](#close).

## <a name="catltemporaryfilehandson"></a><a name="handson"></a>CAtlTemporaryFile::HandsOn

Volání této metody otevřít existující dočasný soubor a umístit ukazatel na konci souboru.

```
HRESULT HandsOn() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

[CAtlTemporaryFile::HandsOff](#handsoff) `HandsOn` a slouží k zrušení přidružení souboru k objektu a v případě potřeby jej znovu připojit.

## <a name="catltemporaryfilelockrange"></a><a name="lockrange"></a>CAtlTemporaryFile::LockRange

Volání této metody uzamknout oblast v dočasném souboru zabránit jiným procesům v přístupu k němu.

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

Zamykání bajtů v souboru zabraňuje přístupu k těmto bajtům jinými procesy. Můžete zamknout více než jednu oblast souboru, ale nejsou povoleny žádné překrývající se oblasti. Chcete-li úspěšně odemknout oblast, použijte [CAtlTemporaryFile::UnlockRange](#unlockrange), zajištění rozsahu bajtů přesně odpovídá oblasti, která byla dříve uzamčena. `LockRange`neslučuje sousední oblasti; Pokud jsou dvě uzamčené oblasti sousedící, musíte je odemknout samostatně.

## <a name="catltemporaryfileoperator-handle"></a><a name="operator_handle"></a>CAtlTemporaryFile::POPISOVAČ operátora

Vrátí popisovač dočasného souboru.

```
operator HANDLE() throw();
```

## <a name="catltemporaryfileread"></a><a name="read"></a>CAtlTemporaryFile::Číst

Volání této metody ke čtení dat z dočasného souboru začíná na pozici označené ukazatelem souboru.

```
HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    DWORD& nBytesRead) throw();
```

### <a name="parameters"></a>Parametry

*pVyrovnávací paměť*<br/>
Ukazatel na vyrovnávací paměť, která obdrží data přečtená ze souboru.

*nBufVelikost*<br/>
Velikost vyrovnávací paměti v bajtů.

*nBajtyČíst*<br/>
Počet přečtených bajtů.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volání [CAtlFile::Číst](../../atl/reference/catlfile-class.md#read). Chcete-li změnit polohu ukazatele souboru, zavolejte [CAtlTemporaryFile::Seek](#seek).

### <a name="example"></a>Příklad

Viz příklad [catltemporaryfile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfileseek"></a><a name="seek"></a>CAtlTemporaryFile::Hledat

Volání této metody přesunout ukazatel souboru dočasného souboru.

```
HRESULT Seek(LONGLONG nOffset, DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>Parametry

*nOffset*<br/>
Posun v bajtů z počátečního bodu dané *dwFrom.*

*dwFrom*<br/>
Výchozí bod (FILE_BEGIN, FILE_CURRENT nebo FILE_END).

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volání [CAtlFile::Seek](../../atl/reference/catlfile-class.md#seek). Chcete-li získat aktuální pozici ukazatele souboru, zavolejte [CAtlTemporaryFile::GetPosition](#getposition).

### <a name="example"></a>Příklad

Viz příklad [catltemporaryfile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfilesetsize"></a><a name="setsize"></a>CAtlTemporaryFile::SetSize

Volání této metody nastavit velikost dočasného souboru.

```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>Parametry

*nNewLen*<br/>
Nová délka souboru v bajtů.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volá [CAtlFile::SetSize](../../atl/reference/catlfile-class.md#setsize). Při návratu je ukazatel souboru umístěn na konci souboru.

## <a name="catltemporaryfiletempfilename"></a><a name="tempfilename"></a>CAtlTemporaryFile::TempFileName

Volání této metody vrátit název dočasného souboru.

```
LPCTSTR TempFileName() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí lPCTSTR ukazující na název souboru.

### <a name="remarks"></a>Poznámky

Název souboru je generován v [catltemporaryfile::CAtlTemporaryFile](#catltemporaryfile) s voláním funkce [GetTempFile](/windows/win32/api/fileapi/nf-fileapi-gettempfilenamew)Windows SDK. Přípona souboru bude vždy "TFR" pro dočasný soubor.

## <a name="catltemporaryfileunlockrange"></a><a name="unlockrange"></a>CAtlTemporaryFile::UnlockRange

Volání této metody odemknout oblast dočasného souboru.

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

Volá [CAtlFile::UnlockRange](../../atl/reference/catlfile-class.md#unlockrange).

## <a name="catltemporaryfilewrite"></a><a name="write"></a>CAtlTemporaryFile::Zápis

Volání této metody pro zápis dat do dočasného souboru začíná na pozici označené ukazatelem souboru.

```
HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    DWORD* pnBytesWritten = NULL) throw();
```

### <a name="parameters"></a>Parametry

*pVyrovnávací paměť*<br/>
Vyrovnávací paměť obsahující data, která mají být zapsána do souboru.

*nBufVelikost*<br/>
Počet bajtů, které mají být přeneseny z vyrovnávací paměti.

*pnBytesWritten*<br/>
Počet zapsaných bajtů.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volání [CAtlFile::Write](../../atl/reference/catlfile-class.md#write).

### <a name="example"></a>Příklad

Viz příklad [catltemporaryfile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Třída CAtlFile](../../atl/reference/catlfile-class.md)
