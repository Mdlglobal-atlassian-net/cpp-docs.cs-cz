---
title: CAtlTemporaryFile – třída
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
ms.openlocfilehash: d6a7a61d1886a264f8575e8d7325d6639d21338d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497704"
---
# <a name="catltemporaryfile-class"></a>CAtlTemporaryFile – třída

Tato třída poskytuje metody pro vytvoření a použití dočasného souboru.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CAtlTemporaryFile
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)|Konstruktor|
|[CAtlTemporaryFile::~CAtlTemporaryFile](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CAtlTemporaryFile:: Close](#close)|Voláním této metody zavřete dočasný soubor a buď odstraňte jeho obsah, nebo ho uložte pod zadaným názvem souboru.|
|[CAtlTemporaryFile:: Create](#create)|Voláním této metody vytvoříte dočasný soubor.|
|[CAtlTemporaryFile:: flush](#flush)|Voláním této metody vynutíte zápis všech dat zbývajících do vyrovnávací paměti souborů do dočasného souboru.|
|[CAtlTemporaryFile:: GetPosition](#getposition)|Zavolejte tuto metodu pro získání aktuálního umístění ukazatele na soubor.|
|[CAtlTemporaryFile:: GetSize](#getsize)|Voláním této metody získáte velikost dočasného souboru v bajtech.|
|[CAtlTemporaryFile::HandsOff](#handsoff)|Zavolejte tuto metodu pro zrušení přidružení souboru `CAtlTemporaryFile` k objektu.|
|[CAtlTemporaryFile::HandsOn](#handson)|Voláním této metody otevřete existující dočasný soubor a umístěte ukazatel na konec souboru.|
|[CAtlTemporaryFile::LockRange](#lockrange)|Voláním této metody zamknete oblast v souboru, abyste zabránili ostatním procesům v přístupu k ní.|
|[CAtlTemporaryFile:: Read](#read)|Zavolejte tuto metodu pro čtení dat z dočasného souboru počínaje pozicí určenou ukazatelem souboru.|
|[CAtlTemporaryFile:: Seek](#seek)|Voláním této metody přesunete ukazatel souboru do dočasného souboru.|
|[CAtlTemporaryFile:: SetSize](#setsize)|Voláním této metody nastavíte velikost dočasného souboru.|
|[CAtlTemporaryFile::TempFileName](#tempfilename)|Voláním této metody vrátíte název dočasného souboru.|
|[CAtlTemporaryFile::UnlockRange](#unlockrange)|Voláním této metody odemknete oblast dočasného souboru.|
|[CAtlTemporaryFile:: Write](#write)|Voláním této metody zapíšete data do dočasného souboru, který začíná na pozici označené ukazatelem souboru.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CAtlTemporaryFile:: operator – popisovač](#operator_handle)|Vrátí popisovač pro dočasný soubor.|

## <a name="remarks"></a>Poznámky

`CAtlTemporaryFile`umožňuje snadno vytvořit a použít dočasný soubor. Soubor je automaticky pojmenován, otevřen, zavřen a odstraněn. Pokud je obsah souboru po zavření souboru vyžadován, může být uložen do nového souboru se zadaným názvem.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlfile. h

## <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile).

##  <a name="catltemporaryfile"></a>CAtlTemporaryFile::CAtlTemporaryFile

Konstruktor

```
CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>Poznámky

Soubor není ve skutečnosti otevřen, dokud není provedeno volání [CAtlTemporaryFile:: Create](#create).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#73](../../atl/codesnippet/cpp/catltemporaryfile-class_1.cpp)]

##  <a name="dtor"></a>CAtlTemporaryFile:: ~ CAtlTemporaryFile

Destruktor.

```
~CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>Poznámky

Destruktor volá [CAtlTemporaryFile:: Close](#close).

##  <a name="close"></a>CAtlTemporaryFile:: Close

Voláním této metody zavřete dočasný soubor a buď odstraňte jeho obsah, nebo ho uložte pod zadaným názvem souboru.

```
HRESULT Close(LPCTSTR szNewName = NULL) throw();
```

### <a name="parameters"></a>Parametry

*szNewName*<br/>
Název nového souboru, do kterého se uloží obsah dočasného souboru. Pokud má argument hodnotu NULL, obsah dočasného souboru se odstraní.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile).

##  <a name="create"></a>CAtlTemporaryFile:: Create

Voláním této metody vytvoříte dočasný soubor.

```
HRESULT Create(LPCTSTR pszDir = NULL, DWORD dwDesiredAccess = GENERIC_WRITE) throw();
```

### <a name="parameters"></a>Parametry

*pszDir*<br/>
Cesta k dočasnému souboru Pokud má hodnotu NULL, bude volána [GetTempPath](/windows/win32/api/fileapi/nf-fileapi-gettemppathw) k přiřazení cesty.

*dwDesiredAccess*<br/>
Požadovaný přístup. Viz *dwDesiredAccess* v [CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew) v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile).

##  <a name="flush"></a>CAtlTemporaryFile:: flush

Voláním této metody vynutíte zápis všech dat zbývajících do vyrovnávací paměti souborů do dočasného souboru.

```
HRESULT Flush() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Podobný jako [CAtlTemporaryFile:: HandsOff](#handsoff), s tím rozdílem, že soubor není uzavřený.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile).

##  <a name="getposition"></a>CAtlTemporaryFile:: GetPosition

Zavolejte tuto metodu pro získání aktuálního umístění ukazatele na soubor.

```
HRESULT GetPosition(ULONGLONG& nPos) const throw();
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Pozice v bajtech.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Chcete-li změnit umístění ukazatele na soubor, použijte [CAtlTemporaryFile:: Seek](#seek).

##  <a name="getsize"></a>CAtlTemporaryFile:: GetSize

Voláním této metody získáte velikost dočasného souboru v bajtech.

```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>Parametry

*nLen*<br/>
Počet bajtů v souboru.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="handsoff"></a>CAtlTemporaryFile::HandsOff

Zavolejte tuto metodu pro zrušení přidružení souboru `CAtlTemporaryFile` k objektu.

```
HRESULT HandsOff() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

`HandsOff`a [CAtlTemporaryFile:: HandsOn](#handson) slouží k zrušení přidružení souboru k objektu a v případě potřeby jej znovu připojit. `HandsOff`vynutí zápis všech dat zbývajících do vyrovnávací paměti souborů do dočasného souboru a potom soubor zavřete. Pokud chcete soubor zavřít a odstranit trvale, nebo pokud chcete zavřít a zachovat obsah souboru s daným názvem, použijte [CAtlTemporaryFile:: Close](#close).

##  <a name="handson"></a>CAtlTemporaryFile::HandsOn

Voláním této metody otevřete existující dočasný soubor a umístěte ukazatel na konec souboru.

```
HRESULT HandsOn() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

[CAtlTemporaryFile:: HandsOff](#handsoff) a `HandsOn` slouží k zrušení přidružení souboru k objektu a v případě potřeby jej znovu připojit.

##  <a name="lockrange"></a>CAtlTemporaryFile::LockRange

Voláním této metody zamknete oblast v dočasném souboru, abyste zabránili ostatním procesům v přístupu k ní.

```
HRESULT LockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Pozice v souboru, kde má zámek začínat.

*nCount*<br/>
Délka rozsahu bajtů, který má být uzamčen.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Uzamykání bajtů v souboru brání v přístupu k těmto bajtům jiným procesům. Můžete uzamknout více než jednu oblast souboru, ale nejsou povoleny žádné překrývající se oblasti. Chcete-li úspěšně odemknout oblast, použijte [CAtlTemporaryFile:: UnlockRange](#unlockrange)a zajistěte, aby rozsah bajtů odpovídal přesně oblasti, která byla dříve uzamčena. `LockRange`neslučuje sousední oblasti; Pokud se dvě uzamčené oblasti sousedí, je nutné je všechny samostatně odemknout.

##  <a name="operator_handle"></a>CAtlTemporaryFile:: operator – popisovač

Vrátí popisovač pro dočasný soubor.

```
operator HANDLE() throw();
```

##  <a name="read"></a>CAtlTemporaryFile:: Read

Zavolejte tuto metodu pro čtení dat z dočasného souboru počínaje pozicí určenou ukazatelem souboru.

```
HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    DWORD& nBytesRead) throw();
```

### <a name="parameters"></a>Parametry

*pBuffer*<br/>
Ukazatel na vyrovnávací paměť, která bude přijímat data načtená ze souboru.

*nBufSize*<br/>
Velikost vyrovnávací paměti v bajtech.

*nBytesRead*<br/>
Počet přečtených bajtů.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volá [CAtlFile:: Read](../../atl/reference/catlfile-class.md#read). Chcete-li změnit umístění ukazatele na soubor, zavolejte [CAtlTemporaryFile:: Seek](#seek).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile).

##  <a name="seek"></a>CAtlTemporaryFile:: Seek

Voláním této metody přesunete ukazatel souboru do dočasného souboru.

```
HRESULT Seek(LONGLONG nOffset, DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>Parametry

*nOffset*<br/>
Posun v bajtech od počátečního bodu zadaného hodnotou *dwFrom.*

*dwFrom*<br/>
Výchozí bod (FILE_BEGIN, FILE_CURRENT nebo FILE_END).

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volá [CAtlFile:: Seek](../../atl/reference/catlfile-class.md#seek). Chcete-li získat aktuální pozici ukazatele souboru, zavolejte [CAtlTemporaryFile:: GetPosition](#getposition).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile).

##  <a name="setsize"></a>CAtlTemporaryFile:: SetSize

Voláním této metody nastavíte velikost dočasného souboru.

```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>Parametry

*nNewLen*<br/>
Nová délka souboru v bajtech

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volá [CAtlFile:: SetSize](../../atl/reference/catlfile-class.md#setsize). Při návratu je ukazatel na soubor umístěný na konci souboru.

##  <a name="tempfilename"></a>CAtlTemporaryFile::TempFileName

Voláním této metody vrátíte název dočasného souboru.

```
LPCTSTR TempFileName() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí LPCTSTR ukazující na název souboru.

### <a name="remarks"></a>Poznámky

Název souboru je vygenerován v [CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile) s voláním funkce [GetTempFile](/windows/win32/api/fileapi/nf-fileapi-gettempfilenamew)Windows SDK. Přípona souboru bude pro dočasný soubor vždy "TFR".

##  <a name="unlockrange"></a>CAtlTemporaryFile::UnlockRange

Voláním této metody odemknete oblast dočasného souboru.

```
HRESULT UnlockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Pozice v souboru, kde má začít odemčení.

*nCount*<br/>
Délka rozsahu bajtů, který má být odemčen.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volá [CAtlFile:: UnlockRange](../../atl/reference/catlfile-class.md#unlockrange).

##  <a name="write"></a>CAtlTemporaryFile:: Write

Voláním této metody zapíšete data do dočasného souboru, který začíná na pozici označené ukazatelem souboru.

```
HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    DWORD* pnBytesWritten = NULL) throw();
```

### <a name="parameters"></a>Parametry

*pBuffer*<br/>
Vyrovnávací paměť obsahující data, která mají být zapsána do souboru.

*nBufSize*<br/>
Počet bajtů, které mají být přeneseny z vyrovnávací paměti.

*pnBytesWritten*<br/>
Počet zapsaných bajtů.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volá [CAtlFile:: Write](../../atl/reference/catlfile-class.md#write).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile).

## <a name="see-also"></a>Viz také:

[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[CAtlFile – třída](../../atl/reference/catlfile-class.md)
