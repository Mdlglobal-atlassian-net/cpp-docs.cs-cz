---
title: CPathT – třída
ms.date: 03/27/2019
f1_keywords:
- CPathT
- ATLPATH/ATL::CPathT
- ATLPATH/ATL::CPathT::PCXSTR
- ATLPATH/ATL::CPathT::PXSTR
- ATLPATH/ATL::CPathT::XCHAR
- ATLPATH/ATL::CPathT::CPathT
- ATLPATH/ATL::CPathT::AddBackslash
- ATLPATH/ATL::CPathT::AddExtension
- ATLPATH/ATL::CPathT::Append
- ATLPATH/ATL::CPathT::BuildRoot
- ATLPATH/ATL::CPathT::Canonicalize
- ATLPATH/ATL::CPathT::Combine
- ATLPATH/ATL::CPathT::CommonPrefix
- ATLPATH/ATL::CPathT::CompactPath
- ATLPATH/ATL::CPathT::CompactPathEx
- ATLPATH/ATL::CPathT::FileExists
- ATLPATH/ATL::CPathT::FindExtension
- ATLPATH/ATL::CPathT::FindFileName
- ATLPATH/ATL::CPathT::GetDriveNumber
- ATLPATH/ATL::CPathT::GetExtension
- ATLPATH/ATL::CPathT::IsDirectory
- ATLPATH/ATL::CPathT::IsFileSpec
- ATLPATH/ATL::CPathT::IsPrefix
- ATLPATH/ATL::CPathT::IsRelative
- ATLPATH/ATL::CPathT::IsRoot
- ATLPATH/ATL::CPathT::IsSameRoot
- ATLPATH/ATL::CPathT::IsUNC
- ATLPATH/ATL::CPathT::IsUNCServer
- ATLPATH/ATL::CPathT::IsUNCServerShare
- ATLPATH/ATL::CPathT::MakePretty
- ATLPATH/ATL::CPathT::MatchSpec
- ATLPATH/ATL::CPathT::QuoteSpaces
- ATLPATH/ATL::CPathT::RelativePathTo
- ATLPATH/ATL::CPathT::RemoveArgs
- ATLPATH/ATL::CPathT::RemoveBackslash
- ATLPATH/ATL::CPathT::RemoveBlanks
- ATLPATH/ATL::CPathT::RemoveExtension
- ATLPATH/ATL::CPathT::RemoveFileSpec
- ATLPATH/ATL::CPathT::RenameExtension
- ATLPATH/ATL::CPathT::SkipRoot
- ATLPATH/ATL::CPathT::StripPath
- ATLPATH/ATL::CPathT::StripToRoot
- ATLPATH/ATL::CPathT::UnquoteSpaces
- ATLPATH/ATL::CPathT::m_strPath
helpviewer_keywords:
- CPathT class
ms.assetid: eba4137d-1fd2-4b44-a2e1-0944db64df3c
ms.openlocfilehash: ba1c831d772deef34449d17adc2c8e7a6f90eaef
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "69496621"
---
# <a name="cpatht-class"></a>CPathT – třída

Tato třída reprezentuje cestu.

> [!IMPORTANT]
> Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <typename StringType>
class CPathT
```

#### <a name="parameters"></a>Parametry

*StringType*<br/>
Třída řetězců ATL/MFC, která se má použít pro cestu (viz [CStringT](../../atl-mfc-shared/reference/cstringt-class.md))

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Name|Popis|
|----------|-----------------|
|[CPathT::PCXSTR](#pcxstr)|Typ konstantního řetězce.|
|[CPathT::PXSTR](#pxstr)|Typ String.|
|[CPathT::XCHAR](#xchar)|Typ znaku.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CPathT::CPathT](#cpatht)|Konstruktor pro cestu|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CPathT::AddBackslash](#addbackslash)|Voláním této metody přidáte zpětné lomítko na konec řetězce pro vytvoření správné syntaxe pro cestu.|
|[CPathT::AddExtension](#addextension)|Voláním této metody přidáte příponu souboru do cesty.|
|[CPathT:: Append](#append)|Voláním této metody připojíte řetězec k aktuální cestě.|
|[CPathT::BuildRoot](#buildroot)|Voláním této metody vytvoříte kořenovou cestu z daného čísla jednotky.|
|[CPathT::Canonicalize](#canonicalize)|Voláním této metody převedete cestu na kanonický tvar.|
|[CPathT::Combine](#combine)|Voláním této metody zřetězí řetězec představující název adresáře a řetězec představující název cesty k souboru na jednu cestu.|
|[CPathT::CommonPrefix](#commonprefix)|Voláním této metody určíte, zda zadaná cesta sdílí společnou předponu s aktuální cestou.|
|[CPathT::CompactPath](#compactpath)|Zavolejte tuto metodu, chcete-li zkrátit cestu k souboru tak, aby odpovídala dané šířce v pixelech tím, že nahradíte součásti cesty třemi tečkami.|
|[CPathT::CompactPathEx](#compactpathex)|Zavolejte tuto metodu, chcete-li zkrátit cestu k souboru tak, aby odpovídala zadanému počtu znaků, a to tak, že nahradíte součásti cesty třemi tečkami.|
|[CPathT:: existuje](#fileexists)|Voláním této metody zkontrolujete, zda soubor s tímto názvem cesty existuje.|
|[CPathT::FindExtension](#findextension)|Voláním této metody zjistíte pozici přípony souboru v cestě.|
|[CPathT::FindFileName](#findfilename)|Voláním této metody zjistíte pozici názvu souboru v cestě.|
|[CPathT::GetDriveNumber](#getdrivenumber)|Voláním této metody prohledáte cestu k písmenu jednotky v rozsahu od "A" do "Z" a vrátíte odpovídající číslo jednotky.|
|[CPathT::GetExtension](#getextension)|Voláním této metody Získá příponu souboru z cesty.|
|[CPathT::IsDirectory](#isdirectory)|Voláním této metody zkontrolujete, zda je cesta platným adresářem.|
|[CPathT::IsFileSpec](#isfilespec)|Voláním této metody můžete vyhledat cestu pro všechny znaky oddělujecích cesty (například ': ' nebo '\\'). Pokud nejsou k dispozici žádné znaky oddělovače cest, je cesta považována za cestu specifikace souboru.|
|[CPathT::IsPrefix](#isprefix)|Voláním této metody určíte, zda cesta obsahuje platnou předponu typu předaného *pszPrefix*.|
|[CPathT::IsRelative](#isrelative)|Voláním této metody určíte, zda je cesta relativní.|
|[CPathT::IsRoot](#isroot)|Voláním této metody určíte, zda je cesta kořenem adresáře.|
|[CPathT::IsSameRoot](#issameroot)|Voláním této metody určíte, zda má jiná cesta společnou kořenovou komponentu s aktuální cestou.|
|[CPathT::IsUNC](#isunc)|Voláním této metody určíte, zda je cesta platnou cestou UNC (Universal Naming Convention) pro server a sdílenou složku.|
|[CPathT::IsUNCServer](#isuncserver)|Voláním této metody určíte, zda je cesta platnou cestou UNC (Universal Naming Convention) pro server.|
|[CPathT::IsUNCServerShare](#isuncservershare)|Voláním této metody určíte, zda je cesta platnou cestou UNC (Universal Naming Convention), \\ \ *sdílenou složkou* *serveru*\ .|
|[CPathT::MakePretty](#makepretty)|Voláním této metody převedete cestu na všechna malá písmena, aby cesta poskytovala konzistentní vzhled.|
|[CPathT::MatchSpec](#matchspec)|Zavolejte tuto metodu pro hledání řetězce obsahujícího typ shody se zástupnými znaky.|
|[CPathT::QuoteSpaces](#quotespaces)|Voláním této metody uzavřete cestu do uvozovek, pokud obsahuje mezery.|
|[CPathT::RelativePathTo](#relativepathto)|Voláním této metody vytvoříte relativní cestu z jednoho souboru nebo složky do jiné.|
|[CPathT::RemoveArgs](#removeargs)|Voláním této metody odeberte jakékoli argumenty příkazového řádku z cesty.|
|[CPathT::RemoveBackslash](#removebackslash)|Zavolejte tuto metodu pro odebrání koncového zpětného lomítka z cesty.|
|[CPathT::RemoveBlanks](#removeblanks)|Voláním této metody odeberete všechny úvodní a koncové mezery z cesty.|
|[CPathT::RemoveExtension](#removeextension)|Voláním této metody odeberete příponu souboru z cesty, pokud existuje.|
|[CPathT::RemoveFileSpec](#removefilespec)|Zavolejte tuto metodu pro odebrání koncového názvu souboru a zpětného lomítka z cesty, pokud je obsahuje.|
|[CPathT::RenameExtension](#renameextension)|Voláním této metody Nahraďte příponu názvu souboru v cestě novým rozšířením. Pokud název souboru neobsahuje příponu, bude rozšíření připojeno ke konci řetězce.|
|[CPathT::SkipRoot](#skiproot)|Voláním této metody rozložíte cestu, ignorování písmen jednotek nebo serveru UNC nebo částí cesty pro sdílení.|
|[CPathT::StripPath](#strippath)|Voláním této metody odeberete část cesty s plně kvalifikovanou cestou a názvem souboru.|
|[CPathT::StripToRoot](#striptoroot)|Voláním této metody odeberete všechny části cesty s výjimkou kořenových informací.|
|[CPathT::UnquoteSpaces](#unquotespaces)|Voláním této metody odeberete uvozovky ze začátku a konce cesty.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CPathT:: operator const StringType &](#operator_const_stringtype_amp)|Tento operátor umožňuje objektu pracovat jako řetězec.|
|[CPathT:: operator CPathT::P CXSTR](#operator_cpatht__pcxstr)|Tento operátor umožňuje objektu pracovat jako řetězec.|
|[CPathT:: operator StringType &](#operator_stringtype_amp)|Tento operátor umožňuje objektu pracovat jako řetězec.|
|[CPathT:: operator + =](#operator_add_eq)|Tento operátor připojí řetězec k cestě.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CPathT::m_strPath](#m_strpath)|Cesta.|

## <a name="remarks"></a>Poznámky

`CPath`, `CPathA`a `CPathW` jsou instancemi, které `CPathT` jsou definovány takto:

`typedef CPathT< CString > CPath;`

`typedef CPathT< CStringA > CPathA;`

`typedef CPathT< CStringW > CPathW;`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlpath. h

##  <a name="addbackslash"></a>CPathT::AddBackslash

Voláním této metody přidáte zpětné lomítko na konec řetězce pro vytvoření správné syntaxe pro cestu. Pokud cesta již obsahuje koncové zpětné lomítko, nebude přidáno žádné zpětné lomítko.

```
void AddBackslash();
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathAddBackSlash](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw).

##  <a name="addextension"></a>CPathT::AddExtension

Voláním této metody přidáte příponu souboru do cesty.

```
BOOL AddExtension(PCXSTR pszExtension);
```

### <a name="parameters"></a>Parametry

*pszExtension*<br/>
Přípona souboru, která se má přidat

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathAddExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw).

##  <a name="append"></a>CPathT:: Append

Voláním této metody připojíte řetězec k aktuální cestě.

```
BOOL Append(PCXSTR pszMore);
```

### <a name="parameters"></a>Parametry

*pszMore*<br/>
Řetězec, který se má připojit.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw).

##  <a name="buildroot"></a>CPathT:: BuildRoot

Voláním této metody vytvoříte kořenovou cestu z daného čísla jednotky.

```
void BuildRoot(int iDrive);
```

### <a name="parameters"></a>Parametry

*iDrive*<br/>
Číslo jednotky (0 je:, 1 je B: a tak dále).

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw).

##  <a name="canonicalize"></a>CPathT:: kanonického tvaru

Voláním této metody převedete cestu na kanonický tvar.

```
void Canonicalize();
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathCanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew).

##  <a name="combine"></a>CPathT:: kombinovat

Voláním této metody zřetězí řetězec představující název adresáře a řetězec představující název cesty k souboru na jednu cestu.

```
void Combine(PCXSTR pszDir, PCXSTR  pszFile);
```

### <a name="parameters"></a>Parametry

*pszDir*<br/>
Cesta k adresáři.

*pszFile*<br/>
Cesta k souboru.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathCombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew).

##  <a name="commonprefix"></a>CPathT::CommonPrefix

Voláním této metody určíte, zda zadaná cesta sdílí společnou předponu s aktuální cestou.

```
CPathT<StringType> CommonPrefix(PCXSTR pszOther);
```

### <a name="parameters"></a>Parametry

*pszOther*<br/>
Cesta, která se má porovnat s aktuálním.

### <a name="return-value"></a>Návratová hodnota

Vrátí společnou předponu.

### <a name="remarks"></a>Poznámky

Předpona je jedním z těchto typů: "C:\\\\", ".", "..", "..", ".. \\\\". Další informace najdete v tématu [PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw).

##  <a name="compactpath"></a>  CPathT::CompactPath

Zavolejte tuto metodu, chcete-li zkrátit cestu k souboru tak, aby odpovídala dané šířce v pixelech tím, že nahradíte součásti cesty třemi tečkami.

```
BOOL CompactPath(HDC hDC, UINT nWidth);
```

### <a name="parameters"></a>Parametry

*hDC*<br/>
Kontext zařízení používaný pro metriky písma.

*nWidth*<br/>
Šířka (v pixelech), do které se má řetězec vejít

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw).

##  <a name="compactpathex"></a>CPathT::CompactPathEx

Zavolejte tuto metodu, chcete-li zkrátit cestu k souboru tak, aby odpovídala zadanému počtu znaků, a to tak, že nahradíte součásti cesty třemi tečkami.

```
BOOL CompactPathEx(UINT nMaxChars, DWORD dwFlags = 0);
```

### <a name="parameters"></a>Parametry

*nMaxChars*<br/>
Maximální počet znaků, které mají být obsaženy v novém řetězci, včetně ukončujícího znaku NULL.

*dwFlags*<br/>
Rezervovaný.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw).

##  <a name="cpatht"></a>CPathT::CPathT

Konstruktor

```
CPathT(PCXSTR pszPath);
CPathT(const CPathT<StringType>& path);
CPathT() throw();
```

### <a name="parameters"></a>Parametry

*pszPath*<br/>
Ukazatel na řetězec cesty.

*Cesta*<br/>
Řetězec cesty

##  <a name="fileexists"></a>CPathT:: existuje

Voláním této metody zkontrolujete, zda soubor s tímto názvem cesty existuje.

```
BOOL FileExists() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud soubor existuje, jinak FALSE.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw).

##  <a name="findextension"></a>CPathT::FindExtension

Voláním této metody zjistíte pozici přípony souboru v cestě.

```
int FindExtension() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí pozici "." před rozšířením. Pokud není nalezeno žádné rozšíření, vrátí hodnotu-1.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathFindExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw).

##  <a name="findfilename"></a>CPathT::FindFileName

Voláním této metody zjistíte pozici názvu souboru v cestě.

```
int FindFileName() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí pozici názvu souboru. Pokud se nenalezne žádný název souboru, vrátí hodnotu-1.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew).

##  <a name="getdrivenumber"></a>CPathT::GetDriveNumber

Voláním této metody prohledáte cestu k písmenu jednotky v rozsahu od "A" do "Z" a vrátíte odpovídající číslo jednotky.

```
int GetDriveNumber() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí číslo jednotky jako celé číslo od 0 do 25 (odpovídající "A" až "Z"), pokud má cesta písmeno jednotky nebo-1 jinak.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw).

##  <a name="getextension"></a>CPathT:: GetExtension

Voláním této metody Získá příponu souboru z cesty.

```
StringType GetExtension() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí příponu souboru.

##  <a name="isdirectory"></a>CPathT::-adresář

Voláním této metody zkontrolujete, zda je cesta platným adresářem.

```
BOOL IsDirectory() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí nenulovou hodnotu (16), pokud je cesta adresářem, jinak FALSE.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathIsDirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw).

##  <a name="isfilespec"></a>  CPathT::IsFileSpec

Voláním této metody můžete vyhledat cestu pro všechny znaky oddělujecích cesty (například ': ' nebo '\\'). Pokud nejsou k dispozici žádné znaky oddělovače cest, je cesta považována za cestu specifikace souboru.

```
BOOL IsFileSpec() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud v cestě nejsou žádné znaky oddělovače cest, nebo FALSE, pokud existují znaky odkladu cest.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw).

##  <a name="isprefix"></a>CPathT::-prefix

Voláním této metody určíte, zda cesta obsahuje platnou předponu typu předaného *pszPrefix*.

```
BOOL IsPrefix(PCXSTR pszPrefix) const;
```

### <a name="parameters"></a>Parametry

*pszPrefix*<br/>
Předpona, kterou chcete vyhledat. Předpona je jedním z těchto typů: "C:\\\\", ".", "..", "..", ".. \\\\".

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud cesta obsahuje předponu, nebo v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw).

##  <a name="isrelative"></a>CPathT::-relativní

Voláním této metody určíte, zda je cesta relativní.

```
BOOL IsRelative() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je cesta relativní, nebo FALSE, pokud je absolutní.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathIsRelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew).

##  <a name="isroot"></a>  CPathT::IsRoot

Voláním této metody určíte, zda je cesta kořenem adresáře.

```
BOOL IsRoot() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je cesta kořenem, nebo v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw).

##  <a name="issameroot"></a>  CPathT::IsSameRoot

Voláním této metody určíte, zda má jiná cesta společnou kořenovou komponentu s aktuální cestou.

```
BOOL IsSameRoot(PCXSTR pszOther) const;
```

### <a name="parameters"></a>Parametry

*pszOther*<br/>
Druhá cesta.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud mají oba řetězce stejnou kořenovou komponentu, nebo jinak FALSE.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw).

##  <a name="isunc"></a>CPathT::IsUNC

Voláním této metody určíte, zda je cesta platnou cestou UNC (Universal Naming Convention) pro server a sdílenou složku.

```
BOOL IsUNC() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je cesta platnou cestou UNC, nebo v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw).

##  <a name="isuncserver"></a>  CPathT::IsUNCServer

Voláním této metody určíte, zda je cesta platnou cestou UNC (Universal Naming Convention) pro server.

```
BOOL IsUNCServer() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je řetězec platnou cestou UNC pouze pro server (žádný název sdílené složky), nebo jinak FALSE.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw).

##  <a name="isuncservershare"></a>  CPathT::IsUNCServerShare

Voláním této metody určíte, zda je cesta platnou cestou UNC (Universal Naming Convention), \\ \ *sdílenou složkou* *serveru*\ .

```
BOOL IsUNCServerShare() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je cesta ve \\ \ *sdílené složce* *serveru*\ , nebo v opačném případě false.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew).

##  <a name="m_strpath"></a>  CPathT::m_strPath

Cesta.

```
StringType m_strPath;
```

### <a name="remarks"></a>Poznámky

`StringType`je parametr šablony pro `CPathT`.

##  <a name="makepretty"></a>CPathT::MakePretty

Voláním této metody převedete cestu na všechna malá písmena, aby cesta poskytovala konzistentní vzhled.

```
BOOL MakePretty();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud byla cesta převedena, nebo v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw).

##  <a name="matchspec"></a>  CPathT::MatchSpec

Zavolejte tuto metodu pro hledání řetězce obsahujícího typ shody se zástupnými znaky.

```
BOOL MatchSpec(PCXSTR pszSpec) const;
```

### <a name="parameters"></a>Parametry

*pszSpec*<br/>
Ukazatel na řetězec zakončený hodnotou null s typem souboru, který chcete vyhledat. Chcete-li například otestovat, zda je soubor v aktuální cestě souborem DOC, *pszSpec* by měl být nastaven na "*. doc".

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud se řetězec shoduje, nebo jinak FALSE.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw).

##  <a name="operator_add_eq"></a>CPathT:: operator + =

Tento operátor připojí řetězec k cestě.

```
CPathT<StringType>& operator+=(PCXSTR pszMore);
```

### <a name="parameters"></a>Parametry

*pszMore*<br/>
Řetězec, který se má připojit.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovanou cestu.

##  <a name="operator_const_stringtype_amp"></a>CPathT:: operator const StringType&amp;

Tento operátor umožňuje objektu pracovat jako řetězec.

```
operator const StringType&() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí řetězec představující aktuální cestu spravovanou tímto objektem.

##  <a name="operator_cpatht__pcxstr"></a>CPathT:: operator CPathT::P CXSTR

Tento operátor umožňuje objektu pracovat jako řetězec.

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí řetězec představující aktuální cestu spravovanou tímto objektem.

##  <a name="operator_stringtype_amp"></a>CPathT:: operator StringType&amp;

Tento operátor umožňuje objektu pracovat jako řetězec.

```
operator StringType&() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí řetězec představující aktuální cestu spravovanou tímto objektem.

##  <a name="pcxstr"></a>CPathT::P CXSTR

Typ konstantního řetězce.

```
typedef StringType::PCXSTR PCXSTR;
```

### <a name="remarks"></a>Poznámky

`StringType`je parametr šablony pro `CPathT`.

##  <a name="pxstr"></a>CPathT::P XSTR

Typ String.

```
typedef StringType::PXSTR PXSTR;
```

### <a name="remarks"></a>Poznámky

`StringType`je parametr šablony pro `CPathT`.

##  <a name="quotespaces"></a>  CPathT::QuoteSpaces

Voláním této metody uzavřete cestu do uvozovek, pokud obsahuje mezery.

```
void QuoteSpaces();
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw).

##  <a name="relativepathto"></a>  CPathT::RelativePathTo

Voláním této metody vytvoříte relativní cestu z jednoho souboru nebo složky do jiné.

```
BOOL RelativePathTo(
    PCXSTR pszFrom,
    DWORD dwAttrFrom,
    PCXSTR pszTo,
    DWORD dwAttrTo);
```

### <a name="parameters"></a>Parametry

*pszFrom*<br/>
Začátek relativní cesty.

*dwAttrFrom*<br/>
Atributy souboru *pszFrom*. Pokud tato hodnota obsahuje FILE_ATTRIBUTE_DIRECTORY, předpokládá se, že *pszFrom* je adresář. v opačném případě se *pszFrom* předpokládá jako soubor.

*pszTo*<br/>
Koncový bod relativní cesty.

*dwAttrTo*<br/>
Atributy souboru *pszTo*. Pokud tato hodnota obsahuje FILE_ATTRIBUTE_DIRECTORY, předpokládá se, že *pszTo* je adresář. v opačném případě se *pszTo* předpokládá jako soubor.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow).

##  <a name="removeargs"></a>CPathT::RemoveArgs

Voláním této metody odeberte jakékoli argumenty příkazového řádku z cesty.

```
void RemoveArgs();
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathRemoveArgs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw).

##  <a name="removebackslash"></a>CPathT::RemoveBackslash

Zavolejte tuto metodu pro odebrání koncového zpětného lomítka z cesty.

```
void RemoveBackslash();
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathRemoveBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw).

##  <a name="removeblanks"></a>CPathT::RemoveBlanks

Voláním této metody odeberete všechny úvodní a koncové mezery z cesty.

```
void RemoveBlanks();
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathRemoveBlanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw).

##  <a name="removeextension"></a>CPathT::RemoveExtension

Voláním této metody odeberete příponu souboru z cesty, pokud existuje.

```
void RemoveExtension();
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathRemoveExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw).

##  <a name="removefilespec"></a>CPathT::RemoveFileSpec

Zavolejte tuto metodu pro odebrání koncového názvu souboru a zpětného lomítka z cesty, pokud je obsahuje.

```
BOOL RemoveFileSpec();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathRemoveFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw).

##  <a name="renameextension"></a>CPathT::RenameExtension

Voláním této metody Nahraďte příponu názvu souboru v cestě novým rozšířením. Pokud název souboru neobsahuje příponu, bude rozšíření připojeno ke konci cesty.

```
BOOL RenameExtension(PCXSTR pszExtension);
```

### <a name="parameters"></a>Parametry

*pszExtension*<br/>
Nová přípona názvu souboru předchází znaku ".".

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw).

##  <a name="skiproot"></a>CPathT::SkipRoot

Voláním této metody můžete analyzovat cestu, ignorovat písmeno jednotky nebo cestu UNC (Universal Naming Convention) serveru nebo sdílené cesty ke sdílené složce.

```
int SkipRoot() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí pozici začátku dílčí cesty, která následuje po kořenu (písmeno jednotky nebo Server nebo sdílenou složku UNC).

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw).

##  <a name="strippath"></a>  CPathT::StripPath

Voláním této metody odeberete část cesty s plně kvalifikovanou cestou a názvem souboru.

```
void StripPath();
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw).

##  <a name="striptoroot"></a>  CPathT::StripToRoot

Voláním této metody odeberete všechny části cesty s výjimkou kořenových informací.

```
BOOL StripToRoot();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud bylo v cestě Nalezeno platné písmeno jednotky, nebo v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw).

##  <a name="unquotespaces"></a>CPathT::UnquoteSpaces

Voláním této metody odeberete uvozovky ze začátku a konce cesty.

```
void UnquoteSpaces();
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw).

##  <a name="xchar"></a>CPathT::XCHAR

Typ znaku.

```
typedef StringType::XCHAR XCHAR;
```

### <a name="remarks"></a>Poznámky

`StringType`je parametr šablony pro `CPathT`.

## <a name="see-also"></a>Viz také:

[Třídy](../../atl/reference/atl-classes.md)<br/>
[CStringT – třída](../../atl-mfc-shared/reference/cstringt-class.md)
