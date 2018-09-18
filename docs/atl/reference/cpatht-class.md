---
title: Cpatht – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CPathT class
ms.assetid: eba4137d-1fd2-4b44-a2e1-0944db64df3c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d95a8f6b28b638b65191bc04ad094cc128f7b247
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46080308"
---
# <a name="cpatht-class"></a>Cpatht – třída

Tato třída reprezentuje cestu.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <typename StringType>
class CPathT
```

#### <a name="parameters"></a>Parametry

*StringType*<br/>
Třídy ATL/MFC řetězec určený pro danou cestu (viz [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)).

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|[CPathT::PCXSTR](#pcxstr)|Typ konstanty typu řetězec.|
|[CPathT::PXSTR](#pxstr)|Typ řetězec.|
|[CPathT::XCHAR](#xchar)|Typ znaku.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CPathT::CPathT](#cpatht)|Konstruktor pro danou cestu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CPathT::AddBackslash](#addbackslash)|Volejte tuto metodu za účelem přidání zpětné lomítko na konci řetězce vytvořit správnou syntaxi pro cestu.|
|[CPathT::AddExtension](#addextension)|Volání této metody můžete přidat příponu souboru na cestu.|
|[CPathT::Append](#append)|Voláním této metody lze připojit řetězec aktuální cestě.|
|[CPathT::BuildRoot](#buildroot)|Volejte tuto metodu za účelem vytvoření kořenovou cestu z jednotky dané číslo.|
|[CPathT::Canonicalize](#canonicalize)|Voláním této metody lze převést cestu na kanonický tvar.|
|[CPathT::Combine](#combine)|Voláním této metody lze zřetězit řetězec představující název adresáře a řetězec představující název cesty souboru do jedné cesty.|
|[CPathT::CommonPrefix](#commonprefix)|Volejte tuto metodu za účelem určení, zda zadaná cesta sdílejí běžnou předponu s cestou k aktuální.|
|[CPathT::CompactPath](#compactpath)|Voláním této metody lze zkrátit cestu k souboru tak, aby odpovídaly šířka v pixelech dané nahrazením součásti cesty se třemi tečkami.|
|[CPathT::CompactPathEx](#compactpathex)|Voláním této metody lze zkrátit cestě přizpůsobena daný počet znaků tak, že nahradíte součásti cesty se třemi tečkami.|
|[CPathT::FileExists](#fileexists)|Volejte tuto metodu ke kontrole, jestli existuje soubor na tento název cesty.|
|[CPathT::FindExtension](#findextension)|Volání této metody pro hledání pozice přípona souboru v této cestě.|
|[CPathT::FindFileName](#findfilename)|Volání této metody pro hledání pozice názvu souboru v této cestě.|
|[CPathT::GetDriveNumber](#getdrivenumber)|Voláním této metody lze vyhledat cestu pro písmeno jednotky v rozsahu od "A" až "Z" a vrátí odpovídající číslo jednotky.|
|[CPathT::GetExtension](#getextension)|Volejte tuto metodu za účelem získání příponu souboru z cesty.|
|[CPathT::IsDirectory](#isdirectory)|Volejte tuto metodu ke kontrole, jestli je cesta platný adresář.|
|[CPathT::IsFileSpec](#isfilespec)|Volání této metody k vyhledání cesty pro cestu oddělovací znaky (například ":" nebo "\\"). Pokud neexistují žádné cesty oddělovací znaky k dispozici, cesta se považuje za cestu specifikace souboru.|
|[CPathT::IsPrefix](#isprefix)|Voláním této metody lze zjistit, zda cesta obsahuje platnou předponu typu předávány *pszPrefix*.|
|[CPathT::IsRelative](#isrelative)|Volejte tuto metodu za účelem určení, zda je cesta relativní.|
|[CPathT::IsRoot](#isroot)|Volejte tuto metodu za účelem určení, zda cesta je kořenový adresář.|
|[CPathT::IsSameRoot](#issameroot)|Volejte tuto metodu za účelem určení, zda má jinou cestu kořenovou součást a společné s aktuální cestě.|
|[CPathT::IsUNC](#isunc)|Volat tuto metodu za účelem určení, zda je cesta platná cesta UNC (universal naming convention) k serveru a sdílet.|
|[CPathT::IsUNCServer](#isuncserver)|Volání této metody Určuje, jestli je cesta pro server pouze pro platnou cestu UNC (universal naming convention).|
|[CPathT::IsUNCServerShare](#isuncservershare)|Volejte tuto metodu za účelem určení, zda je cesta platná cesta UNC (universal naming convention) sdílené složky \\ \  *server*\ *sdílet*.|
|[CPathT::MakePretty](#makepretty)|Volání této metody k převodu cesty na všechna malá písmena poskytnout cestu jednotný vzhled.|
|[CPathT::MatchSpec](#matchspec)|Volání této metody do cesty pro řetězec obsahující typ shody zástupných znaků pro hledání.|
|[CPathT::QuoteSpaces](#quotespaces)|Volejte tuto metodu za účelem cesty uzavřete do uvozovek, pokud obsahuje mezery.|
|[CPathT::RelativePathTo](#relativepathto)|Volejte tuto metodu za účelem vytvoření relativní cesta z jednoho souboru nebo složky do jiné.|
|[CPathT::RemoveArgs](#removeargs)|Volejte tuto metodu za účelem odebrání žádných argumentů příkazového řádku z cesty.|
|[CPathT::RemoveBackslash](#removebackslash)|Volejte tuto metodu za účelem odebrání zpětné lomítko na konci cesty.|
|[CPathT::RemoveBlanks](#removeblanks)|Volejte tuto metodu za účelem odebere všechny úvodní a koncové mezery v cestě.|
|[CPathT::RemoveExtension](#removeextension)|Volejte tuto metodu za účelem odebrání přípony souboru z cesty, pokud existuje.|
|[CPathT::RemoveFileSpec](#removefilespec)|Volejte tuto metodu za účelem odstranění na konci názvu souboru a zpětné lomítko z cesty, pokud je má.|
|[CPathT::RenameExtension](#renameextension)|Voláním této metody lze nahradit příponu názvu souboru v cestě k nové rozšíření. Pokud název souboru neobsahuje příponu, rozšíření bude připojen na konec řetězce.|
|[CPathT::SkipRoot](#skiproot)|Voláním této metody lze analyzovat cestu, ignoruje se písmeno jednotky nebo části cesty UNC nebo sdílené složky serveru.|
|[CPathT::StripPath](#strippath)|Voláním této metody lze odebrat část cesty plně kvalifikovanou cestu a název souboru.|
|[CPathT::StripToRoot](#striptoroot)|Voláním této metody lze odebrat všechny části cesty s výjimkou kořenové informace.|
|[CPathT::UnquoteSpaces](#unquotespaces)|Voláním této metody lze odebrat uvozovky ze začátku a konce cesty.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CPathT::operator const StringType &](#operator_const_stringtype_amp)|Tento operátor umožňuje objekt, který má zacházet jako řetězec.|
|[CPathT::operator CPathT::PCXSTR](#operator_cpatht__pcxstr)|Tento operátor umožňuje objekt, který má zacházet jako řetězec.|
|[CPathT::operator StringType &](#operator_stringtype)|Tento operátor umožňuje objekt, který má zacházet jako řetězec.|
|[CPathT::operator +=](#operator_add_eq)|Tento operátor přidá řetězec do cesty.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CPathT::m_strPath](#m_strpath)|Cesta.|

## <a name="remarks"></a>Poznámky

`CPath`, `CPathA`, a `CPathW` jsou instancemi `CPathT` definovaná následujícím způsobem:

`typedef CPathT< CString > CPath;`

`typedef CPathT< CStringA > CPathA;`

`typedef CPathT< CStringW > CPathW;`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlpath.h

##  <a name="addbackslash"></a>  CPathT::AddBackslash

Volejte tuto metodu za účelem přidání zpětné lomítko na konci řetězce vytvořit správnou syntaxi pro cestu. Pokud cesta již obsahuje lomítkem, přidá se neobsahuje zpětné lomítko.

```
void AddBackslash();
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathAddBackSlash](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddbackslasha).

##  <a name="addextension"></a>  CPathT::AddExtension

Volání této metody můžete přidat příponu souboru na cestu.

```
BOOL AddExtension(PCXSTR pszExtension);
```

### <a name="parameters"></a>Parametry

*pszExtension*<br/>
Přípona souboru, který chcete přidat.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathAddExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddextensiona).

##  <a name="append"></a>  CPathT::Append

Voláním této metody lze připojit řetězec aktuální cestě.

```
BOOL Append(PCXSTR pszMore);
```

### <a name="parameters"></a>Parametry

*pszMore*<br/>
Řetězec, který chcete připojit.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathAppend](/windows/desktop/api/shlwapi/nf-shlwapi-pathappenda).

##  <a name="buildroot"></a>  CPathT::BuildRoot

Volejte tuto metodu za účelem vytvoření kořenovou cestu z jednotky dané číslo.

```
void BuildRoot(int iDrive);
```

### <a name="parameters"></a>Parametry

*iDrive*<br/>
Číslo jednotku (A: je 0, 1 je b a tak dále).

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathBuildRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathbuildroota).

##  <a name="canonicalize"></a>  CPathT::Canonicalize

Voláním této metody lze převést cestu na kanonický tvar.

```
void Canonicalize();
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathCanonicalize](/windows/desktop/api/shlwapi/nf-shlwapi-pathcanonicalizea).

##  <a name="combine"></a>  CPathT::Combine

Voláním této metody lze zřetězit řetězec představující název adresáře a řetězec představující název cesty souboru do jedné cesty.

```
void Combine(PCXSTR pszDir, PCXSTR  pszFile);
```

### <a name="parameters"></a>Parametry

*pszDir*<br/>
Cesta k adresáři.

*pszFile*<br/>
Cesta k souboru.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathCombine](/windows/desktop/api/shlwapi/nf-shlwapi-pathcombinea).

##  <a name="commonprefix"></a>  CPathT::CommonPrefix

Volejte tuto metodu za účelem určení, zda zadaná cesta sdílejí běžnou předponu s cestou k aktuální.

```
CPathT<StringType> CommonPrefix(PCXSTR pszOther);
```

### <a name="parameters"></a>Parametry

*pszOther*<br/>
Cesta, která má být porovnán s aktuální.

### <a name="return-value"></a>Návratová hodnota

Vrátí běžnou předponu.

### <a name="remarks"></a>Poznámky

Předpona je jedním z těchto typů: "C:\\\\",".","..",".. \\\\". Další informace najdete v tématu [PathCommonPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathcommonprefixa).

##  <a name="compactpath"></a>  CPathT::CompactPath

Voláním této metody lze zkrátit cestu k souboru tak, aby odpovídaly šířka v pixelech dané nahrazením součásti cesty se třemi tečkami.

```
BOOL CompactPath(HDC hDC, UINT nWidth);
```

### <a name="parameters"></a>Parametry

*hDC*<br/>
Kontext zařízení pro metriky písma

*nWidth*<br/>
Šířka v pixelech, které řetězec bude muset přizpůsobit.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathCompactPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpatha).

##  <a name="compactpathex"></a>  CPathT::CompactPathEx

Voláním této metody lze zkrátit cestě přizpůsobena daný počet znaků tak, že nahradíte součásti cesty se třemi tečkami.

```
BOOL CompactPathEx(UINT nMaxChars, DWORD dwFlags = 0);
```

### <a name="parameters"></a>Parametry

*nMaxChars*<br/>
Maximální počet znaků, které mají být součástí nového řetězce, včetně ukončujícího znaku NULL.

*dwFlags*<br/>
Vyhrazená.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathCompactPathEx](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpathexa).

##  <a name="cpatht"></a>  CPathT::CPathT

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
Řetězec cesty.

##  <a name="fileexists"></a>  CPathT::FileExists

Volejte tuto metodu ke kontrole, jestli existuje soubor na tento název cesty.

```
BOOL FileExists() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud soubor existuje, FALSE v opačném případě.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathFileExists](/windows/desktop/api/shlwapi/nf-shlwapi-pathfileexistsa).

##  <a name="findextension"></a>  CPathT::FindExtension

Volání této metody pro hledání pozice přípona souboru v této cestě.

```
int FindExtension() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí pozici "." předcházející rozšíření. Pokud se žádná rozšíření nenajde, vrátí hodnotu -1.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathFindExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindextensiona).

##  <a name="findfilename"></a>  CPathT::FindFileName

Volání této metody pro hledání pozice názvu souboru v této cestě.

```
int FindFileName() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí pozici názvu souboru. Pokud není nalezen žádný název souboru, vrátí hodnotu -1.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea).

##  <a name="getdrivenumber"></a>  CPathT::GetDriveNumber

Voláním této metody lze vyhledat cestu pro písmeno jednotky v rozsahu od "A" až "Z" a vrátí odpovídající číslo jednotky.

```
int GetDriveNumber() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrací číslo jednotky jako celé číslo od 0 do 25 (odpovídá "A" až "Z"), pokud cesta obsahuje písmeno jednotky nebo -1, jinak.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathGetDriveNumber](/windows/desktop/api/shlwapi/nf-shlwapi-pathgetdrivenumbera).

##  <a name="getextension"></a>  CPathT::GetExtension

Volejte tuto metodu za účelem získání příponu souboru z cesty.

```
StringType GetExtension() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí příponu souboru.

##  <a name="isdirectory"></a>  CPathT::IsDirectory

Volejte tuto metodu ke kontrole, jestli je cesta platný adresář.

```
BOOL IsDirectory() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrací nenulovou hodnotu (16), pokud cesta je adresář, FALSE v opačném případě.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathIsDirectory](/windows/desktop/api/shlwapi/nf-shlwapi-pathisdirectorya).

##  <a name="isfilespec"></a>  CPathT::IsFileSpec

Volání této metody k vyhledání cesty pro cestu oddělovací znaky (například ":" nebo "\\"). Pokud neexistují žádné cesty oddělovací znaky k dispozici, cesta se považuje za cestu specifikace souboru.

```
BOOL IsFileSpec() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud neexistují žádné cesty oddělovací znaky v této cestě, nebo hodnotu FALSE, pokud existuje cesta oddělovací znaky.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathIsFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathisfilespeca).

##  <a name="isprefix"></a>  CPathT::IsPrefix

Voláním této metody lze zjistit, zda cesta obsahuje platnou předponu typu předávány *pszPrefix*.

```
BOOL IsPrefix(PCXSTR pszPrefix) const;
```

### <a name="parameters"></a>Parametry

*pszPrefix*<br/>
Předpona, který chcete vyhledat. Předpona je jedním z těchto typů: "C:\\\\",".","..",".. \\\\".

### <a name="return-value"></a>Návratová hodnota

Pokud cesta obsahuje předponu, nebo FALSE, v opačném případě vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathIsPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathisprefixa).

##  <a name="isrelative"></a>  CPathT::IsRelative

Volejte tuto metodu za účelem určení, zda je cesta relativní.

```
BOOL IsRelative() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud cesta je relativní, nebo hodnotu NEPRAVDA, pokud je absolutní.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathIsRelative](/windows/desktop/api/shlwapi/nf-shlwapi-pathisrelativea).

##  <a name="isroot"></a>  CPathT::IsRoot

Volejte tuto metodu za účelem určení, zda cesta je kořenový adresář.

```
BOOL IsRoot() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud se cesta kořenové nebo hodnotu FALSE v opačném případě vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathIsRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathisroota).

##  <a name="issameroot"></a>  CPathT::IsSameRoot

Volejte tuto metodu za účelem určení, zda má jinou cestu kořenovou součást a společné s aktuální cestě.

```
BOOL IsSameRoot(PCXSTR pszOther) const;
```

### <a name="parameters"></a>Parametry

*pszOther*<br/>
Jiné cesty.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud oba řetězce mají stejnou kořenovou součást, nebo FALSE, jinak.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathIsSameRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathissameroota).

##  <a name="isunc"></a>  CPathT::IsUNC

Volat tuto metodu za účelem určení, zda je cesta platná cesta UNC (universal naming convention) k serveru a sdílet.

```
BOOL IsUNC() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud je cesta platná cesta UNC, nebo hodnotu FALSE v opačném případě vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathIsUNC](/windows/desktop/api/shlwapi/nf-shlwapi-pathisunca).

##  <a name="isuncserver"></a>  CPathT::IsUNCServer

Volání této metody Určuje, jestli je cesta pro server pouze pro platnou cestu UNC (universal naming convention).

```
BOOL IsUNCServer() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud řetězec je jinak platnou cestu UNC pouze server (bez názvu sdílené složky) nebo FALSE.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathIsUNCServer](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncservera).

##  <a name="isuncservershare"></a>  CPathT::IsUNCServerShare

Volejte tuto metodu za účelem určení, zda je cesta platná cesta UNC (universal naming convention) sdílené složky \\ \  *server*\ *sdílet*.

```
BOOL IsUNCServerShare() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud se cesta ve formátu \\ \  *server*\ *sdílet*, nebo hodnotu NEPRAVDA, jinak.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathIsUNCServerShare](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncserversharea).

##  <a name="m_strpath"></a>  CPathT::m_strPath

Cesta.

```
StringType m_strPath;
```

### <a name="remarks"></a>Poznámky

`StringType` je parametr šablony `CPathT`.

##  <a name="makepretty"></a>  CPathT::MakePretty

Volání této metody k převodu cesty na všechna malá písmena poskytnout cestu jednotný vzhled.

```
BOOL MakePretty();
```

### <a name="return-value"></a>Návratová hodnota

V opačném případě vrátí hodnotu TRUE, pokud byl převeden cestu, nebo FALSE.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathMakePretty](/windows/desktop/api/shlwapi/nf-shlwapi-pathmakeprettya).

##  <a name="matchspec"></a>  CPathT::MatchSpec

Volání této metody do cesty pro řetězec obsahující typ shody zástupných znaků pro hledání.

```
BOOL MatchSpec(PCXSTR pszSpec) const;
```

### <a name="parameters"></a>Parametry

*pszSpec*<br/>
Ukazatel na řetězec zakončený hodnotou null typu souboru, který chcete vyhledat. Například chcete otestovat, jestli soubor v aktuální cestě je soubor dokumentu *pszSpec* musí být nastavená na "* .doc".

### <a name="return-value"></a>Návratová hodnota

V opačném případě vrátí hodnotu TRUE, pokud řetězec odpovídá nebo hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathMatchSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathmatchspeca).

##  <a name="operator_add_eq"></a>  CPathT::operator +=

Tento operátor přidá řetězec do cesty.

```
CPathT<StringType>& operator+=(PCXSTR pszMore);
```

### <a name="parameters"></a>Parametry

*pszMore*<br/>
Řetězec, který chcete připojit.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovanou cestu.

##  <a name="operator_const_stringtype_amp"></a>  CPathT::operator const StringType &amp;

Tento operátor umožňuje objekt, který má zacházet jako řetězec.

```
operatorconst StringType&() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí řetězec představující aktuální cestu spravovaných tímto objektem.

##  <a name="operator_cpatht__pcxstr"></a>  CPathT::operator CPathT::PCXSTR

Tento operátor umožňuje objekt, který má zacházet jako řetězec.

```
operatorPCXSTR() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí řetězec představující aktuální cestu spravovaných tímto objektem.

##  <a name="operator_stringtype__amp"></a>  CPathT::operator StringType &amp;

Tento operátor umožňuje objekt, který má zacházet jako řetězec.

```
operatorStringType&() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí řetězec představující aktuální cestu spravovaných tímto objektem.

##  <a name="pcxstr"></a>  CPathT::PCXSTR

Typ konstanty typu řetězec.

```
typedef StringType::PCXSTR PCXSTR;
```

### <a name="remarks"></a>Poznámky

`StringType` je parametr šablony `CPathT`.

##  <a name="pxstr"></a>  CPathT::PXSTR

Typ řetězec.

```
typedef StringType::PXSTR PXSTR;
```

### <a name="remarks"></a>Poznámky

`StringType` je parametr šablony `CPathT`.

##  <a name="quotespaces"></a>  CPathT::QuoteSpaces

Volejte tuto metodu za účelem cesty uzavřete do uvozovek, pokud obsahuje mezery.

```
void QuoteSpaces();
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathQuoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathquotespacesa).

##  <a name="relativepathto"></a>  CPathT::RelativePathTo

Volejte tuto metodu za účelem vytvoření relativní cesta z jednoho souboru nebo složky do jiné.

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
Atributy souboru *pszFrom*. Pokud tato hodnota obsahuje FILE_ATTRIBUTE_DIRECTORY, *pszFrom* se předpokládá, že bude adresář; v opačném případě *pszFrom* předpokládá, že je možné do souboru.

*pszTo*<br/>
Koncový bod relativní cesty.

*dwAttrTo*<br/>
Atributy souboru *pszTo*. Pokud tato hodnota obsahuje FILE_ATTRIBUTE_DIRECTORY, *pszTo* se předpokládá, že bude adresář; v opačném případě *pszTo* předpokládá, že je možné do souboru.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathRelativePathTo](/windows/desktop/api/shlwapi/nf-shlwapi-pathrelativepathtoa).

##  <a name="removeargs"></a>  CPathT::RemoveArgs

Volejte tuto metodu za účelem odebrání žádných argumentů příkazového řádku z cesty.

```
void RemoveArgs();
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathRemoveArgs](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveargsa).

##  <a name="removebackslash"></a>  CPathT::RemoveBackslash

Volejte tuto metodu za účelem odebrání zpětné lomítko na konci cesty.

```
void RemoveBackslash();
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathRemoveBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovebackslasha).

##  <a name="removeblanks"></a>  CPathT::RemoveBlanks

Volejte tuto metodu za účelem odebere všechny úvodní a koncové mezery v cestě.

```
void RemoveBlanks();
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathRemoveBlanks](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveblanksa).

##  <a name="removeextension"></a>  CPathT::RemoveExtension

Volejte tuto metodu za účelem odebrání přípony souboru z cesty, pokud existuje.

```
void RemoveExtension();
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathRemoveExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveextensiona).

##  <a name="removefilespec"></a>  CPathT::RemoveFileSpec

Volejte tuto metodu za účelem odstranění na konci názvu souboru a zpětné lomítko z cesty, pokud je má.

```
BOOL RemoveFileSpec();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathRemoveFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovefilespeca).

##  <a name="renameextension"></a>  CPathT::RenameExtension

Voláním této metody lze nahradit příponu názvu souboru v cestě k nové rozšíření. Pokud název souboru neobsahuje příponu, rozšíření bude připojen na konec cesty.

```
BOOL RenameExtension(PCXSTR pszExtension);
```

### <a name="parameters"></a>Parametry

*pszExtension*<br/>
Předchází novou příponu názvu souboru "." znaku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathRenameExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathrenameextensiona).

##  <a name="skiproot"></a>  CPathT::SkipRoot

Voláním této metody lze analyzovat cestu, písmeno jednotky nebo části cesty UNC (universal naming convention) sdílené složky serveru/se ignoruje.

```
int SkipRoot() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí pozici začátku podřízená cesta v, který následuje root (písmeno jednotky nebo serveru/sdílené složky UNC).

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathSkipRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathskiproota).

##  <a name="strippath"></a>  CPathT::StripPath

Voláním této metody lze odebrat část cesty plně kvalifikovanou cestu a název souboru.

```
void StripPath();
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathStripPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathstrippatha).

##  <a name="striptoroot"></a>  CPathT::StripToRoot

Voláním této metody lze odebrat všechny části cesty s výjimkou kořenové informace.

```
BOOL StripToRoot();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud platné písmeno jednotky byl nalezen v cestě, nebo hodnotu NEPRAVDA jinak.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathStripToRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathstriptoroota).

##  <a name="unquotespaces"></a>  CPathT::UnquoteSpaces

Voláním této metody lze odebrat uvozovky ze začátku a konce cesty.

```
void UnquoteSpaces();
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [PathUnquoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathunquotespacesa).

##  <a name="xchar"></a>  CPathT::XCHAR

Typ znaku.

```
typedef StringType::XCHAR XCHAR;
```

### <a name="remarks"></a>Poznámky

`StringType` je parametr šablony `CPathT`.

## <a name="see-also"></a>Viz také

[Třídy](../../atl/reference/atl-classes.md)<br/>
[CStringT – třída](../../atl-mfc-shared/reference/cstringt-class.md)