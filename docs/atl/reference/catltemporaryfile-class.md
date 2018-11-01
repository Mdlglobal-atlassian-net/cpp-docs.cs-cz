---
title: Catltemporaryfile – třída
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
ms.openlocfilehash: f440476db3618c24f0fd1cfbfe028c959517a607
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50642267"
---
# <a name="catltemporaryfile-class"></a>Catltemporaryfile – třída

Tato třída poskytuje metody pro vytváření a používání dočasný soubor.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CAtlTemporaryFile
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)|Konstruktor|
|[Catltemporaryfile –:: ~ catltemporaryfile –](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAtlTemporaryFile::Close](#close)|Voláním této metody lze dočasný soubor zavřít a buď odstraňte její obsah nebo si je uložte pod názvem zadaného souboru.|
|[CAtlTemporaryFile::Create](#create)|Voláním této metody lze vytvořit dočasný soubor.|
|[CAtlTemporaryFile::Flush](#flush)|Voláním této metody lze vynutit žádná data zbývajících ve vyrovnávací paměti souboru k zápisu do dočasného souboru.|
|[CAtlTemporaryFile::GetPosition](#getposition)|Voláním této metody k získání aktuální ukazatel pozice v souboru.|
|[CAtlTemporaryFile::GetSize](#getsize)|Volejte tuto metodu za účelem získání velikost v bajtech dočasný soubor.|
|[CAtlTemporaryFile::HandsOff](#handsoff)|Volejte tuto metodu za účelem zrušte přidružení souboru `CAtlTemporaryFile` objektu.|
|[CAtlTemporaryFile::HandsOn](#handson)|Volejte tuto metodu za účelem otevření existujícího souboru dočasné a umístěte kurzor na konec souboru.|
|[CAtlTemporaryFile::LockRange](#lockrange)|Volejte tuto metodu za účelem uzamčení oblasti v souboru, který má bránit dalším procesům v přístupu k nim.|
|[CAtlTemporaryFile::Read](#read)|Volejte tuto metodu za účelem čtení dat z dočasného souboru začínající na pozici ukazatele souboru.|
|[CAtlTemporaryFile::Seek](#seek)|Voláním této metody lze přesunout ukazatel souboru dočasný soubor.|
|[CAtlTemporaryFile::SetSize](#setsize)|Voláním této metody lze nastavit velikost dočasného souboru.|
|[CAtlTemporaryFile::TempFileName](#tempfilename)|Voláním této metody vrátí název dočasného souboru.|
|[CAtlTemporaryFile::UnlockRange](#unlockrange)|Volání této metody k odemknutí oblast dočasný soubor.|
|[CAtlTemporaryFile::Write](#write)|Volání této metody zapsat data do dočasného souboru začínající na pozici ukazatele souboru.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CAtlTemporaryFile::operator POPISOVAČ](#operator_handle)|Vrátí popisovač do dočasného souboru.|

## <a name="remarks"></a>Poznámky

`CAtlTemporaryFile` umožňuje snadno vytvořit a použít dočasný soubor. Soubor je automaticky s názvem, otevřít, uzavřen a odstraněn. Pokud obsah souboru vyžaduje zavření souboru, mohou být uloženy do nového souboru se zadaným názvem.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlfile.h

## <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

##  <a name="catltemporaryfile"></a>  CAtlTemporaryFile::CAtlTemporaryFile

Konstruktor

```
CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>Poznámky

Soubor není otevřen ve skutečnosti, dokud je provedeno volání [CAtlTemporaryFile::Create](#create).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#73](../../atl/codesnippet/cpp/catltemporaryfile-class_1.cpp)]

##  <a name="dtor"></a>  Catltemporaryfile –:: ~ catltemporaryfile –

Destruktor.

```
~CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>Poznámky

Volání destruktoru [CAtlTemporaryFile::Close](#close).

##  <a name="close"></a>  CAtlTemporaryFile::Close

Voláním této metody lze dočasný soubor zavřít a buď odstraňte její obsah nebo si je uložte pod názvem zadaného souboru.

```
HRESULT Close(LPCTSTR szNewName = NULL) throw();
```

### <a name="parameters"></a>Parametry

*szNewName*<br/>
Název pro nový soubor pro uložení obsahu dočasný soubor v. Pokud tento argument je NULL, odstraní se obsah bude dočasný soubor.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

##  <a name="create"></a>  CAtlTemporaryFile::Create

Voláním této metody lze vytvořit dočasný soubor.

```
HRESULT Create(LPCTSTR pszDir = NULL, DWORD dwDesiredAccess = GENERIC_WRITE) throw();
```

### <a name="parameters"></a>Parametry

*pszDir*<br/>
Cesta pro dočasný soubor. Pokud je hodnota NULL, [GetTempPath](/windows/desktop/api/fileapi/nf-fileapi-gettemppatha) bude volána k přiřazení cesty.

*dwDesiredAccess*<br/>
Požadovaný přístup. Zobrazit *dwDesiredAccess* v [CreateFile](/windows/desktop/api/fileapi/nf-fileapi-createfilea) v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

##  <a name="flush"></a>  CAtlTemporaryFile::Flush

Voláním této metody lze vynutit žádná data zbývajících ve vyrovnávací paměti souboru k zápisu do dočasného souboru.

```
HRESULT Flush() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Podobně jako [CAtlTemporaryFile::HandsOff](#handsoff), s tím rozdílem, že soubor není uzavřený.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

##  <a name="getposition"></a>  CAtlTemporaryFile::GetPosition

Voláním této metody k získání aktuální ukazatel pozice v souboru.

```
HRESULT GetPosition(ULONGLONG& nPos) const throw();
```

### <a name="parameters"></a>Parametry

*nPos –*<br/>
Pozice v bajtech.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Ke změně pozice ukazatel souboru, použijte [CAtlTemporaryFile::Seek](#seek).

##  <a name="getsize"></a>  CAtlTemporaryFile::GetSize

Volejte tuto metodu za účelem získání velikost v bajtech dočasný soubor.

```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>Parametry

*nLen*<br/>
Počet bajtů v souboru.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="handsoff"></a>  CAtlTemporaryFile::HandsOff

Volejte tuto metodu za účelem zrušte přidružení souboru `CAtlTemporaryFile` objektu.

```
HRESULT HandsOff() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

`HandsOff` a [CAtlTemporaryFile::HandsOn](#handson) se používají k zrušte přidružení souboru z objektu a znovu připojit v případě potřeby. `HandsOff` se vynutí žádná data zbývajících ve vyrovnávací paměti souboru k zápisu do dočasného souboru a poté zavřete soubor. Pokud chcete zavřít a trvale odstranit soubor, nebo pokud chcete zavřít a zachovat obsah souboru s daným názvem, použijte [CAtlTemporaryFile::Close](#close).

##  <a name="handson"></a>  CAtlTemporaryFile::HandsOn

Volejte tuto metodu za účelem otevření existujícího souboru dočasné a umístěte kurzor na konec souboru.

```
HRESULT HandsOn() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

[CAtlTemporaryFile::HandsOff](#handsoff) a `HandsOn` se používají k zrušte přidružení souboru z objektu a znovu připojit v případě potřeby.

##  <a name="lockrange"></a>  CAtlTemporaryFile::LockRange

Volejte tuto metodu za účelem uzamčení oblasti do dočasného souboru, aby se zabránilo jiné procesy v přístupu k nim.

```
HRESULT LockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>Parametry

*nPos –*<br/>
Pozice v souboru, ve kterém chcete spustit zámek.

*nCount*<br/>
Délka rozsahu bajtů uzamčení.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Zamykací bajty v souboru brání v přístupu k těmto bajtů s jinými procesy. Můžeš více než jedné oblasti souboru, ale žádné překrývající se oblasti jsou povoleny. Chcete-li úspěšně odemknout oblasti, použijte [CAtlTemporaryFile::UnlockRange](#unlockrange), zajištění rozsah bajtů přesně odpovídá oblasti, která dříve byla uzamčena. `LockRange` nesloučí sousední oblasti; Pokud jsou dvě oblasti uzamčené vedle sebe, musí každý odemknout samostatně.

##  <a name="operator_handle"></a>  CAtlTemporaryFile::operator POPISOVAČ

Vrátí popisovač do dočasného souboru.

```
operator HANDLE() throw();
```

##  <a name="read"></a>  CAtlTemporaryFile::Read

Volejte tuto metodu za účelem čtení dat z dočasného souboru začínající na pozici ukazatele souboru.

```
HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    DWORD& nBytesRead) throw();
```

### <a name="parameters"></a>Parametry

*pBuffer*<br/>
Ukazatel do vyrovnávací paměti, která bude přijímat data načtená ze souboru.

*nBufSize*<br/>
Velikost vyrovnávací paměti v bajtech.

*nBytesRead*<br/>
Počet přečtených bajtů.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volání [CAtlFile::Read](../../atl/reference/catlfile-class.md#read). Chcete-li změnit umístění ukazatel souboru, zavolejte [CAtlTemporaryFile::Seek](#seek).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

##  <a name="seek"></a>  CAtlTemporaryFile::Seek

Voláním této metody lze přesunout ukazatel souboru dočasný soubor.

```
HRESULT Seek(LONGLONG nOffset, DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>Parametry

*nOffset*<br/>
Posun v bajtech od počátečního bodu *dwFrom.*

*dwFrom*<br/>
Počáteční bod (FILE_BEGIN, FILE_CURRENT nebo FILE_END).

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volání [CAtlFile::Seek](../../atl/reference/catlfile-class.md#seek). Chcete-li získat aktuální ukazatel pozice v souboru, zavolejte [CAtlTemporaryFile::GetPosition](#getposition).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

##  <a name="setsize"></a>  CAtlTemporaryFile::SetSize

Voláním této metody lze nastavit velikost dočasného souboru.

```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>Parametry

*nNewLen*<br/>
Novou velikost souboru v bajtech.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volání [CAtlFile::SetSize](../../atl/reference/catlfile-class.md#setsize). Při návratu je ukazatel na soubor umístěn na konci souboru.

##  <a name="tempfilename"></a>  CAtlTemporaryFile::TempFileName

Voláním této metody vrátí název dočasného souboru.

```
LPCTSTR TempFileName() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí LPCTSTR odkazující na název souboru.

### <a name="remarks"></a>Poznámky

Název souboru generuje v [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile) voláním [GetTempFile](/windows/desktop/api/fileapi/nf-fileapi-gettempfilenamea)funkce sady Windows SDK. Přípona souboru bude vždy "TFR" pro dočasný soubor.

##  <a name="unlockrange"></a>  CAtlTemporaryFile::UnlockRange

Volání této metody k odemknutí oblast dočasný soubor.

```
HRESULT UnlockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>Parametry

*nPos –*<br/>
Pozice v souboru, ve kterém chcete spustit odemknout.

*nCount*<br/>
Délka rozsahu bajtů k odemknutí.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Volání [CAtlFile::UnlockRange](../../atl/reference/catlfile-class.md#unlockrange).

##  <a name="write"></a>  CAtlTemporaryFile::Write

Volání této metody zapsat data do dočasného souboru začínající na pozici ukazatele souboru.

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

Volání [CAtlFile::Write](../../atl/reference/catlfile-class.md#write).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="see-also"></a>Viz také

[Přehled tříd](../../atl/atl-class-overview.md)<br/>
[CAtlFile – třída](../../atl/reference/catlfile-class.md)
