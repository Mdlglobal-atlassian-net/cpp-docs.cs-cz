---
title: Třída CPathT
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
ms.openlocfilehash: c10b854ae5c2d7167a067675b1391be24b6a8122
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746592"
---
# <a name="cpatht-class"></a>Třída CPathT

Tato třída představuje cestu.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <typename StringType>
class CPathT
```

#### <a name="parameters"></a>Parametry

*Typ řetězce*<br/>
Třída řetězce ATL/MFC, která má být pro cestu používána (viz [CStringT).](../../atl-mfc-shared/reference/cstringt-class.md)

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

|Název|Popis|
|----------|-----------------|
|[CPathT::PCXSTR](#pcxstr)|Konstantní typ řetězce.|
|[CPathT::PXSTR](#pxstr)|Typ řetězce.|
|[CPathT::XCHAR](#xchar)|Typ znaku.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[Cpatht::CPatht](#cpatht)|Konstruktor pro cestu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CPathT::AddBackslash](#addbackslash)|Volání této metody přidat zpětné lomítko na konec řetězce vytvořit správnou syntaxi pro cestu.|
|[CPatht::AddExtension](#addextension)|Volání této metody přidat příponu souboru na cestu.|
|[CPathT::Připojit](#append)|Volání této metody připojit řetězec k aktuální cestě.|
|[CPatht::Buildroot](#buildroot)|Volání této metody k vytvoření kořenové cesty z daného čísla jednotky.|
|[CPathT::Kanoián](#canonicalize)|Volání této metody převést cestu do kanonického formuláře.|
|[CPatht::Kombinovat](#combine)|Volání této metody zřetězit řetězec představující název adresáře a řetězec představující název cesty souboru do jedné cesty.|
|[CPathT::CommonPrefix](#commonprefix)|Volání této metody k určení, zda zadaná cesta sdílí společnou předponu s aktuální cestou.|
|[CPathT::CompactPath](#compactpath)|Volání této metody zkrátit cestu souboru, aby se vešly do dané šířky obrazových bodů nahrazením součástí cesty s elipsy.|
|[CPathT::CompactPathEx](#compactpathex)|Volání této metody zkrátit cestu k souboru, aby se vešly do daného počtu znaků nahrazením součásti cesty s elipsy.|
|[CPathT::FileExists](#fileexists)|Volání této metody ke kontrole, zda soubor v tomto názvu cesty existuje.|
|[CPatht::FindExtension](#findextension)|Volání této metody najít pozici přípony souboru v rámci cesty.|
|[CPatht::FindFileName](#findfilename)|Volání této metody najít pozici názvu souboru v rámci cesty.|
|[CPatht::GetDriveNumber](#getdrivenumber)|Volání této metody hledat cestu pro písmeno jednotky v rozsahu 'A' na 'Z' a vrátit odpovídající číslo jednotky.|
|[CPatht::GetExtension](#getextension)|Volání této metody získat příponu souboru z cesty.|
|[CPatht::IsDirectory](#isdirectory)|Volání této metody ke kontrole, zda cesta je platný adresář.|
|[CPatht::isfilespec](#isfilespec)|Voláním této metody vyhledejte cestu pro všechny znaky vymezující\\cestu (například ::' nebo ' ). Pokud nejsou k dispozici žádné znaky vymezující cestu, cesta se považuje za cestu specifikace souboru.|
|[CPathT::Předpoklady isprefixu](#isprefix)|Volání této metody k určení, zda cesta obsahuje platnou předponu typu předané *pszPrefix*.|
|[CPatht::Jerelativní](#isrelative)|Volání této metody k určení, pokud je relativní cesta.|
|[CPatht::Kořenová_kořenová_je](#isroot)|Volání této metody k určení, zda cesta je kořenový adresář.|
|[CPatht::IsSameRoot](#issameroot)|Volání této metody k určení, zda má jiná cesta společnou kořenovou součást s aktuální cestou.|
|[CPathT::IsUNC](#isunc)|Volání této metody k určení, zda cesta je platná UNC (univerzální konvence pojmenování) cesta pro server a sdílené položky.|
|[CPatht::IsUNCServer](#isuncserver)|Volání této metody k určení, zda cesta je platná UNC (univerzální konvence názvů) cesta pouze pro server.|
|[CPatht::IsUNCServerShare](#isuncservershare)|Volání této metody k určení, zda cesta je platná UNC \\ \ (univerzální konvence pojmenování) sdílené cesty,*sdílené správě* *serveru*\ .|
|[Cpatht::MakePretty](#makepretty)|Volání této metody převést cestu na všechny znaky malá písmena, aby cesta konzistentní vzhled.|
|[CPatht::MatchSpec](#matchspec)|Volání této metody hledat cestu pro řetězec obsahující typ shody se zástupnými symboly.|
|[CPathT::Mezery mezi nabídkami](#quotespaces)|Volání této metody uzavřít cestu do uvozovek, pokud obsahuje mezery.|
|[CPathT::RelativePathTo](#relativepathto)|Volání této metody k vytvoření relativní cestu z jednoho souboru nebo složky do jiného.|
|[CPathT::RemoveArgs](#removeargs)|Volání této metody odebrat všechny argumenty příkazového řádku z cesty.|
|[CPathT::RemoveBackslash](#removebackslash)|Volání této metody odebrat koncové zpětné lomítko z cesty.|
|[CPathT::RemoveBlanks](#removeblanks)|Volání této metody odebrat všechny úvodní a koncové mezery z cesty.|
|[CPatht::RemoveExtension](#removeextension)|Volání této metody odebrat příponu souboru z cesty, pokud existuje.|
|[CPatht::RemoveFileSpec](#removefilespec)|Volání této metody odebrat název koncového souboru a zpětné lomítko z cesty, pokud je má.|
|[CPathT::Přejmenovatrozšíření](#renameextension)|Volání této metody nahradit příponu názvu souboru v cestě s novou příponou. Pokud název souboru neobsahuje příponu, bude přípona připojena ke konci řetězce.|
|[CPatht::Přeskočení kořenů](#skiproot)|Volání této metody analyzovat cestu, ignoruje písmeno jednotky nebo UNC server/sdílet cesty částí.|
|[CPathT::Strippath](#strippath)|Volání této metody odebrat část cesty plně kvalifikovanou cestu a název souboru.|
|[CPatht::Striptoroot](#striptoroot)|Volání této metody odebrat všechny části cesty s výjimkou kořenové informace.|
|[CPathT::UnquoteSpaces](#unquotespaces)|Volání této metody odebrat uvozovky z začátku a konce cesty.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CPathT::operátor const StringType &](#operator_const_stringtype_amp)|Tento operátor umožňuje objekt, který má být zpracován jako řetězec.|
|[CPathT::operátor CPathT::PCXSTR](#operator_cpatht__pcxstr)|Tento operátor umožňuje objekt, který má být zpracován jako řetězec.|
|[CPathT::&typu StringType operátora](#operator_stringtype_amp)|Tento operátor umožňuje objekt, který má být zpracován jako řetězec.|
|[CPathT::operátor +=](#operator_add_eq)|Tento operátor připojí řetězec k cestě.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CPathT::m_strPath](#m_strpath)|Cesta.|

## <a name="remarks"></a>Poznámky

`CPath`, `CPathA`a `CPathW` jsou konkretizace `CPathT` definované takto:

`typedef CPathT< CString > CPath;`

`typedef CPathT< CStringA > CPathA;`

`typedef CPathT< CStringW > CPathW;`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlpath.h

## <a name="cpathtaddbackslash"></a><a name="addbackslash"></a>CPathT::AddBackslash

Volání této metody přidat zpětné lomítko na konec řetězce vytvořit správnou syntaxi pro cestu. Pokud cesta již má koncové zpětné lomítko, nebude přidáno žádné zpětné lomítko.

```cpp
void AddBackslash();
```

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [PathAddBackSlash](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw).

## <a name="cpathtaddextension"></a><a name="addextension"></a>CPatht::AddExtension

Volání této metody přidat příponu souboru na cestu.

```
BOOL AddExtension(PCXSTR pszExtension);
```

### <a name="parameters"></a>Parametry

*pszRozšíření*<br/>
Přípona souboru přidat.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [PathAddExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw).

## <a name="cpathtappend"></a><a name="append"></a>CPathT::Připojit

Volání této metody připojit řetězec k aktuální cestě.

```
BOOL Append(PCXSTR pszMore);
```

### <a name="parameters"></a>Parametry

*pszVíce*<br/>
Řetězec připojit.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw).

## <a name="cpathtbuildroot"></a><a name="buildroot"></a>CPatht::Buildroot

Volání této metody k vytvoření kořenové cesty z daného čísla jednotky.

```cpp
void BuildRoot(int iDrive);
```

### <a name="parameters"></a>Parametry

*Idrive*<br/>
Číslo jednotky (0 je A:, 1 je B:, a tak dále).

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw).

## <a name="cpathtcanonicalize"></a><a name="canonicalize"></a>CPathT::Kanoián

Volání této metody převést cestu do kanonického formuláře.

```cpp
void Canonicalize();
```

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [PathCanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew).

## <a name="cpathtcombine"></a><a name="combine"></a>CPatht::Kombinovat

Volání této metody zřetězit řetězec představující název adresáře a řetězec představující název cesty souboru do jedné cesty.

```cpp
void Combine(PCXSTR pszDir, PCXSTR  pszFile);
```

### <a name="parameters"></a>Parametry

*pszDir*<br/>
Cesta k adresáři.

*pszFile*<br/>
Cesta k souboru.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [PathCombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew).

## <a name="cpathtcommonprefix"></a><a name="commonprefix"></a>CPathT::CommonPrefix

Volání této metody k určení, zda zadaná cesta sdílí společnou předponu s aktuální cestou.

```
CPathT<StringType> CommonPrefix(PCXSTR pszOther);
```

### <a name="parameters"></a>Parametry

*pszOstatní*<br/>
Cesta k porovnání s aktuální.

### <a name="return-value"></a>Návratová hodnota

Vrátí běžnou předponu.

### <a name="remarks"></a>Poznámky

Předpona je jedním z těchto\\\\typů: "C: ", ".", "..", "..", ".. \\\\". Další informace naleznete v tématu [PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw).

## <a name="cpathtcompactpath"></a><a name="compactpath"></a>CPathT::CompactPath

Volání této metody zkrátit cestu souboru, aby se vešly do dané šířky obrazových bodů nahrazením součástí cesty s elipsy.

```
BOOL CompactPath(HDC hDC, UINT nWidth);
```

### <a name="parameters"></a>Parametry

*Hdc*<br/>
Kontext zařízení používaný pro metriky písma.

*nŠířka*<br/>
Šířka v pixelech, že řetězec bude nucen zapadnout.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw).

## <a name="cpathtcompactpathex"></a><a name="compactpathex"></a>CPathT::CompactPathEx

Volání této metody zkrátit cestu k souboru, aby se vešly do daného počtu znaků nahrazením součásti cesty s elipsy.

```
BOOL CompactPathEx(UINT nMaxChars, DWORD dwFlags = 0);
```

### <a name="parameters"></a>Parametry

*nMaxChars*<br/>
Maximální počet znaků, které mají být obsaženy v novém řetězci, včetně ukončujícího znaku NULL.

*dwFlags*<br/>
Vyhrazeno.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw).

## <a name="cpathtcpatht"></a><a name="cpatht"></a>Cpatht::CPatht

Konstruktor

```
CPathT(PCXSTR pszPath);
CPathT(const CPathT<StringType>& path);
CPathT() throw();
```

### <a name="parameters"></a>Parametry

*pszPath*<br/>
Ukazatel na řetězec cesty.

*Cestu*<br/>
Řetězec cesty.

## <a name="cpathtfileexists"></a><a name="fileexists"></a>CPathT::FileExists

Volání této metody ke kontrole, zda soubor v tomto názvu cesty existuje.

```
BOOL FileExists() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud soubor existuje, jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw).

## <a name="cpathtfindextension"></a><a name="findextension"></a>CPatht::FindExtension

Volání této metody najít pozici přípony souboru v rámci cesty.

```
int FindExtension() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí pozici "." před rozšíření. Pokud není nalezeno žádné rozšíření, vrátí -1.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [PathFindExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw).

## <a name="cpathtfindfilename"></a><a name="findfilename"></a>CPatht::FindFileName

Volání této metody najít pozici názvu souboru v rámci cesty.

```
int FindFileName() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí pozici názvu souboru. Pokud není nalezen žádný název souboru, vrátí -1.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew).

## <a name="cpathtgetdrivenumber"></a><a name="getdrivenumber"></a>CPatht::GetDriveNumber

Volání této metody hledat cestu pro písmeno jednotky v rozsahu 'A' na 'Z' a vrátit odpovídající číslo jednotky.

```
int GetDriveNumber() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí číslo jednotky jako celé číslo od 0 do 25 (odpovídající "A" až 'Z'), pokud má cesta písmeno jednotky, nebo -1 jinak.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw).

## <a name="cpathtgetextension"></a><a name="getextension"></a>CPatht::GetExtension

Volání této metody získat příponu souboru z cesty.

```
StringType GetExtension() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí příponu souboru.

## <a name="cpathtisdirectory"></a><a name="isdirectory"></a>CPatht::IsDirectory

Volání této metody ke kontrole, zda cesta je platný adresář.

```
BOOL IsDirectory() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí nenulovou hodnotu (16), pokud je cesta adresář, FALSE jinak.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [PathIsDirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw).

## <a name="cpathtisfilespec"></a><a name="isfilespec"></a>CPatht::isfilespec

Voláním této metody vyhledejte cestu pro všechny znaky vymezující\\cestu (například ::' nebo ' ). Pokud nejsou k dispozici žádné znaky vymezující cestu, cesta se považuje za cestu specifikace souboru.

```
BOOL IsFileSpec() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud v cestě nejsou žádné znaky vymezující cestu, nebo NEPRAVDA, pokud existují znaky vymezující cestu.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw).

## <a name="cpathtisprefix"></a><a name="isprefix"></a>CPathT::Předpoklady isprefixu

Volání této metody k určení, zda cesta obsahuje platnou předponu typu předané *pszPrefix*.

```
BOOL IsPrefix(PCXSTR pszPrefix) const;
```

### <a name="parameters"></a>Parametry

*pszPrefix*<br/>
Předpona, pro kterou chcete hledat. Předpona je jedním z těchto\\\\typů: "C: ", ".", "..", "..", ".. \\\\".

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud cesta obsahuje předponu, jinak nepravdivá.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw).

## <a name="cpathtisrelative"></a><a name="isrelative"></a>CPatht::Jerelativní

Volání této metody k určení, pokud je relativní cesta.

```
BOOL IsRelative() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je cesta relativní, nebo nepravda, pokud je absolutní.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [PathIsRelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew).

## <a name="cpathtisroot"></a><a name="isroot"></a>CPatht::Kořenová_kořenová_je

Volání této metody k určení, zda cesta je kořenový adresář.

```
BOOL IsRoot() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je cesta kořenovou nebo nepravdivou jinak.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw).

## <a name="cpathtissameroot"></a><a name="issameroot"></a>CPatht::IsSameRoot

Volání této metody k určení, zda má jiná cesta společnou kořenovou součást s aktuální cestou.

```
BOOL IsSameRoot(PCXSTR pszOther) const;
```

### <a name="parameters"></a>Parametry

*pszOstatní*<br/>
Druhá cesta.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud mají oba řetězce stejnou kořenovou součást, jinak hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw).

## <a name="cpathtisunc"></a><a name="isunc"></a>CPathT::IsUNC

Volání této metody k určení, zda cesta je platná UNC (univerzální konvence pojmenování) cesta pro server a sdílené položky.

```
BOOL IsUNC() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je cesta platnou cestou UNC, jinak nepravdivá.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw).

## <a name="cpathtisuncserver"></a><a name="isuncserver"></a>CPatht::IsUNCServer

Volání této metody k určení, zda cesta je platná UNC (univerzální konvence názvů) cesta pouze pro server.

```
BOOL IsUNCServer() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je řetězec platnou cestou UNC pouze pro server (bez názvu sdílené složky) nebo JINAK NEPRAVDA.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw).

## <a name="cpathtisuncservershare"></a><a name="isuncservershare"></a>CPatht::IsUNCServerShare

Volání této metody k určení, zda cesta je platná UNC \\ \ (univerzální konvence pojmenování) sdílené cesty,*sdílené správě* *serveru*\ .

```
BOOL IsUNCServerShare() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud \\ \ je cesta ve*sdílené složce* *serveru*\ formuláře , jinak nepravdivá.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew).

## <a name="cpathtm_strpath"></a><a name="m_strpath"></a>CPathT::m_strPath

Cesta.

```
StringType m_strPath;
```

### <a name="remarks"></a>Poznámky

`StringType`je parametr šablony `CPathT`.

## <a name="cpathtmakepretty"></a><a name="makepretty"></a>Cpatht::MakePretty

Volání této metody převést cestu na všechny znaky malá písmena, aby cesta konzistentní vzhled.

```
BOOL MakePretty();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud byla cesta převedena, jinak nepravdivá.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw).

## <a name="cpathtmatchspec"></a><a name="matchspec"></a>CPatht::MatchSpec

Volání této metody hledat cestu pro řetězec obsahující typ shody se zástupnými symboly.

```
BOOL MatchSpec(PCXSTR pszSpec) const;
```

### <a name="parameters"></a>Parametry

*pszSpec*<br/>
Ukazatel na řetězec s nulovým ukončením s typem souboru, pro který chcete hledat. Chcete-li například otestovat, zda je soubor na aktuální cestě soubor DOC, *pszSpec* by měl být nastaven na "*.doc".

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud se řetězec shoduje, jinak nepravda.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw).

## <a name="cpathtoperator-"></a><a name="operator_add_eq"></a>CPathT::operátor +=

Tento operátor připojí řetězec k cestě.

```
CPathT<StringType>& operator+=(PCXSTR pszMore);
```

### <a name="parameters"></a>Parametry

*pszVíce*<br/>
Řetězec připojit.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovanou cestu.

## <a name="cpathtoperator-const-stringtype-amp"></a><a name="operator_const_stringtype_amp"></a>CPathT::operátor const StringType&amp;

Tento operátor umožňuje objekt, který má být zpracován jako řetězec.

```
operator const StringType&() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí řetězec představující aktuální cestu spravovanou tímto objektem.

## <a name="cpathtoperator-cpathtpcxstr"></a><a name="operator_cpatht__pcxstr"></a>CPathT::operátor CPathT::PCXSTR

Tento operátor umožňuje objekt, který má být zpracován jako řetězec.

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí řetězec představující aktuální cestu spravovanou tímto objektem.

## <a name="cpathtoperator-stringtype-amp"></a><a name="operator_stringtype_amp"></a>CPathT::operátor StringType&amp;

Tento operátor umožňuje objekt, který má být zpracován jako řetězec.

```
operator StringType&() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí řetězec představující aktuální cestu spravovanou tímto objektem.

## <a name="cpathtpcxstr"></a><a name="pcxstr"></a>CPathT::PCXSTR

Konstantní typ řetězce.

```
typedef StringType::PCXSTR PCXSTR;
```

### <a name="remarks"></a>Poznámky

`StringType`je parametr šablony `CPathT`.

## <a name="cpathtpxstr"></a><a name="pxstr"></a>CPathT::PXSTR

Typ řetězce.

```
typedef StringType::PXSTR PXSTR;
```

### <a name="remarks"></a>Poznámky

`StringType`je parametr šablony `CPathT`.

## <a name="cpathtquotespaces"></a><a name="quotespaces"></a>CPathT::Mezery mezi nabídkami

Volání této metody uzavřít cestu do uvozovek, pokud obsahuje mezery.

```cpp
void QuoteSpaces();
```

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw).

## <a name="cpathtrelativepathto"></a><a name="relativepathto"></a>CPathT::RelativePathTo

Volání této metody k vytvoření relativní cestu z jednoho souboru nebo složky do jiného.

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
File atributy *pszFrom*. Pokud tato hodnota obsahuje FILE_ATTRIBUTE_DIRECTORY, *pszFrom* se předpokládá, že je adresář; jinak *pszFrom* se předpokládá, že soubor.

*pszTo*<br/>
Koncový bod relativní cesty.

*dwAttrTo*<br/>
File atributy *pszTo*. Pokud tato hodnota obsahuje FILE_ATTRIBUTE_DIRECTORY, *pszTo* se předpokládá, že je adresář; jinak *pszTo* se předpokládá, že je soubor.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow).

## <a name="cpathtremoveargs"></a><a name="removeargs"></a>CPathT::RemoveArgs

Volání této metody odebrat všechny argumenty příkazového řádku z cesty.

```cpp
void RemoveArgs();
```

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [PathRemoveArgs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw).

## <a name="cpathtremovebackslash"></a><a name="removebackslash"></a>CPathT::RemoveBackslash

Volání této metody odebrat koncové zpětné lomítko z cesty.

```cpp
void RemoveBackslash();
```

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [PathRemoveBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw).

## <a name="cpathtremoveblanks"></a><a name="removeblanks"></a>CPathT::RemoveBlanks

Volání této metody odebrat všechny úvodní a koncové mezery z cesty.

```cpp
void RemoveBlanks();
```

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [PathRemoveBlanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw).

## <a name="cpathtremoveextension"></a><a name="removeextension"></a>CPatht::RemoveExtension

Volání této metody odebrat příponu souboru z cesty, pokud existuje.

```cpp
void RemoveExtension();
```

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [PathRemoveExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw).

## <a name="cpathtremovefilespec"></a><a name="removefilespec"></a>CPatht::RemoveFileSpec

Volání této metody odebrat název koncového souboru a zpětné lomítko z cesty, pokud je má.

```
BOOL RemoveFileSpec();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

Další informace naleznete v [tématu PathRemoveFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw).

## <a name="cpathtrenameextension"></a><a name="renameextension"></a>CPathT::Přejmenovatrozšíření

Volání této metody nahradit příponu názvu souboru v cestě s novou příponou. Pokud název souboru neobsahuje příponu, bude přípona připojena ke konci cesty.

```
BOOL RenameExtension(PCXSTR pszExtension);
```

### <a name="parameters"></a>Parametry

*pszRozšíření*<br/>
Nová přípona názvu souboru, předchází znak "." .

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw).

## <a name="cpathtskiproot"></a><a name="skiproot"></a>CPatht::Přeskočení kořenů

Volání této metody analyzovat cestu, ignoruje písmeno jednotky nebo UNC (univerzální konvence pojmenování) server nebo sdílet části cesty.

```
int SkipRoot() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí pozici začátku podcesty, která následuje za kořenem (písmeno jednotky nebo server/sdílená složka UNC).

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw).

## <a name="cpathtstrippath"></a><a name="strippath"></a>CPathT::Strippath

Volání této metody odebrat část cesty plně kvalifikovanou cestu a název souboru.

```cpp
void StripPath();
```

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw).

## <a name="cpathtstriptoroot"></a><a name="striptoroot"></a>CPatht::Striptoroot

Volání této metody odebrat všechny části cesty s výjimkou kořenové informace.

```
BOOL StripToRoot();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud bylo v cestě nalezeno platné písmeno jednotky, jinak nepravda.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw).

## <a name="cpathtunquotespaces"></a><a name="unquotespaces"></a>CPathT::UnquoteSpaces

Volání této metody odebrat uvozovky z začátku a konce cesty.

```cpp
void UnquoteSpaces();
```

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw).

## <a name="cpathtxchar"></a><a name="xchar"></a>CPathT::XCHAR

Typ znaku.

```
typedef StringType::XCHAR XCHAR;
```

### <a name="remarks"></a>Poznámky

`StringType`je parametr šablony `CPathT`.

## <a name="see-also"></a>Viz také

[Třídy](../../atl/reference/atl-classes.md)<br/>
[CStringT – třída](../../atl-mfc-shared/reference/cstringt-class.md)
