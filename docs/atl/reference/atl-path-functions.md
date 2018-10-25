---
title: Funkce cest ATL | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ATL, path
f1_keywords:
- ATLPATH/ATL::ATLPath::AddBackslash
- ATLPATH/ATL::ATLPath::AddExtension
- ATLPATH/ATL::ATLPath::Append
- ATLPATH/ATL::ATLPath::BuildRoot
- ATLPATH/ATL::ATLPath::Canonicalize
- ATLPATH/ATL::ATLPath::Combine
- ATLPATH/ATL::ATLPath::CommonPrefix
- ATLPATH/ATL::ATLPath::CompactPath
- ATLPATH/ATL::ATLPath::CompactPathEx
- ATLPATH/ATL::ATLPath::FileExists
- ATLPATH/ATL::ATLPath::FindExtension
- ATLPATH/ATL::ATLPath::FindFileName
- ATLPATH/ATL::ATLPath::GetDriveNumber
- ATLPATH/ATL::ATLPath::IsDirectory
- ATLPATH/ATL::ATLPath::IsFileSpec
- ATLPATH/ATL::ATLPath::IsPrefix
- ATLPATH/ATL::ATLPath::IsRelative
- ATLPATH/ATL::ATLPath::IsRoot
- ATLPATH/ATL::ATLPath::IsSameRoot
- ATLPATH/ATL::ATLPath::IsUNC
- ATLPATH/ATL::ATLPath::IsUNCServer
- ATLPATH/ATL::ATLPath::IsUNCServerShare
- ATLPATH/ATL::ATLPath::MakePretty
- ATLPATH/ATL::ATLPath::MatchSpec
- ATLPATH/ATL::ATLPath::QuoteSpaces
- ATLPATH/ATL::ATLPath::RelativePathTo
- ATLPATH/ATL::ATLPath::RemoveArgs
- ATLPATH/ATL::ATLPath::RemoveBackslash
- ATLPATH/ATL::ATLPath::RemoveBlanks
- ATLPATH/ATL::ATLPath::RemoveExtension
- ATLPATH/ATL::ATLPath::RemoveFileSpec
- ATLPATH/ATL::ATLPath::RenameExtension
- ATLPATH/ATL::ATLPath::SkipRoot
- ATLPATH/ATL::ATLPath::StripPath
- ATLPATH/ATL::ATLPath::StripToRoot
- ATLPATH/ATL::ATLPath::UnquoteSpaces
ms.assetid: d1ec2b8d-7ec7-43ea-90dd-0a740d2a742b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cdb658b179e3e3488b070203ad7f0909610d4fd8
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50054641"
---
# <a name="atl-path-functions"></a>Funkce cest ATL

Knihovna ATL poskytuje třídu ATLPath pro manipulaci s cesty ve formě [cpatht –](cpatht-class.md). Tento kód lze nalézt v atlpath.h.

### <a name="related-classes"></a>Související třídy

|||
|-|-|
|[CPathT – třída](cpatht-class.md)|Tato třída reprezentuje cestu.|

### <a name="related-typedefs"></a>Související – definice TypeDef

|||
|-|-|
|`CPath`|Specializace [cpatht –](cpatht-class.md) pomocí `CString`.|
|`CPathA`|Specializace [cpatht –](cpatht-class.md) pomocí `CStringA`.|
|`CPathW`|Specializace [cpatht –](cpatht-class.md) pomocí `CStringW`.|

### <a name="functions"></a>Funkce

|||
|-|-|
|[ATLPath::AddBackslash](#addbackslash)|Tato funkce je přetížená obálka pro [PathAddBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddbackslasha).|
|[ATLPath::AddExtension](#addextension)|Tato funkce je přetížená obálka pro [PathAddExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddextensiona).|
|[ATLPath::Append](#append)|Tato funkce je přetížená obálka pro [PathAppend](/windows/desktop/api/shlwapi/nf-shlwapi-pathappenda).|
|[ATLPath::BuildRoot](#buildroot)|Tato funkce je přetížená obálka pro [PathBuildRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathbuildroota).|
|[ATLPath::Canonicalize](#canonicalize)|Tato funkce je přetížená obálka pro [PathCanonicalize](/windows/desktop/api/shlwapi/nf-shlwapi-pathcanonicalizea).|
|[ATLPath::Combine](#combine)|Tato funkce je přetížená obálka pro [PathCombine](/windows/desktop/api/shlwapi/nf-shlwapi-pathcombinea).|
|[ATLPath::CommonPrefix](#commonprefix)|Tato funkce je přetížená obálka pro [PathCommonPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathcommonprefixa).|
|[ATLPath::CompactPath](#compactpath)|Tato funkce je přetížená obálka pro [PathCompactPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpatha).|
|[ATLPath::CompactPathEx](#compactpathex)|Tato funkce je přetížená obálka pro [PathCompactPathEx](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpathexa).|
|[ATLPath::FileExists](#fileexists)|Tato funkce je přetížená obálka pro [PathFileExists](/windows/desktop/api/shlwapi/nf-shlwapi-pathfileexistsa).|
|[ATLPath::FindExtension](#findextension)|Tato funkce je přetížená obálka pro [PathFindExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindextensiona).|
|[ATLPath::FindFileName](#findfilename)|Tato funkce je přetížená obálka pro [PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea).|
|[ATLPath::GetDriveNumber](#getdrivenumber)|Tato funkce je přetížená obálka pro [PathGetDriveNumber](/windows/desktop/api/shlwapi/nf-shlwapi-pathgetdrivenumbera).|
|[ATLPath::IsDirectory](#isdirectory)|Tato funkce je přetížená obálka pro [PathIsDirectory](/windows/desktop/api/shlwapi/nf-shlwapi-pathisdirectorya).|
|[ATLPath::IsFileSpec](#isfilespec)|Tato funkce je přetížená obálka pro [PathIsFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathisfilespeca).|
|[ATLPath::IsPrefix](#isprefix)|Tato funkce je přetížená obálka pro [PathIsPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathisprefixa).|
|[ATLPath::IsRelative](#isrelative)|Tato funkce je přetížená obálka pro [PathIsRelative](/windows/desktop/api/shlwapi/nf-shlwapi-pathisrelativea).|
|[ATLPath::IsRoot](#isroot)|Tato funkce je přetížená obálka pro [PathIsRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathisroota).|
|[ATLPath::IsSameRoot](#issameroot)|Tato funkce je přetížená obálka pro [PathIsSameRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathissameroota).|
|[ATLPath::IsUNC](#isunc)|Tato funkce je přetížená obálka pro [PathIsUNC](/windows/desktop/api/shlwapi/nf-shlwapi-pathisunca).|
|[ATLPath::IsUNCServer](#isuncserver)|Tato funkce je přetížená obálka pro [PathIsUNCServer](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncservera).|
|[ATLPath::IsUNCServerShare](#isuncservershare)|Tato funkce je přetížená obálka pro [PathIsUNCServerShare](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncserversharea).|
|[ATLPath::MakePretty](#makepretty)|Tato funkce je přetížená obálka pro [PathMakePretty](/windows/desktop/api/shlwapi/nf-shlwapi-pathmakeprettya).|
|[ATLPath::MatchSpec](#matchspec)|Tato funkce je přetížená obálka pro [PathMatchSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathmatchspeca).|
|[ATLPath::QuoteSpaces](#quotespaces)|Tato funkce je přetížená obálka pro [PathQuoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathquotespacesa).|
|[ATLPath::RelativePathTo](#relativepathto)|Tato funkce je přetížená obálka pro [PathRelativePathTo](/windows/desktop/api/shlwapi/nf-shlwapi-pathrelativepathtoa).|
|[ATLPath::RemoveArgs](#removeargs)|Tato funkce je přetížená obálka pro [PathRemoveArgs](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveargsa).|
|[ATLPath::RemoveBackslash](#removebackslash)|Tato funkce je přetížená obálka pro [PathRemoveBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovebackslasha).|
|[ATLPath::RemoveBlanks](#removeblanks)|Tato funkce je přetížená obálka pro [PathRemoveBlanks](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveblanksa).|
|[ATLPath::RemoveExtension](#removeextension)|Tato funkce je přetížená obálka pro [PathRemoveExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveextensiona).|
|[ATLPath::RemoveFileSpec](#removefilespec)|Tato funkce je přetížená obálka pro [PathRemoveFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovefilespeca).|
|[ATLPath::RenameExtension](#renameextension)|Tato funkce je přetížená obálka pro [PathRenameExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathrenameextensiona).|
|[ATLPath::SkipRoot](#skiproot)|Tato funkce je přetížená obálka pro [PathSkipRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathskiproota).|
|[ATLPath::StripPath](#strippath)|Tato funkce je přetížená obálka pro [PathStripPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathstrippatha).|
|[ATLPath::StripToRoot](#striptoroot)|Tato funkce je přetížená obálka pro [PathStripToRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathstriptoroota).|
|[ATLPath::UnquoteSpaces](#unquotespaces)|Tato funkce je přetížená obálka pro [PathUnquoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathunquotespacesa).|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlpath.h

## <a name="addbackslash"></a> ATLPath::AddBackSlash

Tato funkce je přetížená obálka pro [PathAddBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddbackslasha).

### <a name="syntax"></a>Syntaxe

```
inline char* AddBackslash(char* pszPath);
inline wchar_t* AddBackslash(wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Zobrazit [PathAddBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddbackslasha) podrobnosti.

## <a name="addextension"></a> ATLPath::AddExtension

Tato funkce je přetížená obálka pro [PathAddExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddextensiona).

### <a name="syntax"></a>Syntaxe

```
inline BOOL AddExtension(char* pszPath, const char* pszExtension);
inline BOOL AddExtension(wchar_t* pszPath, const wchar_t* pszExtension);
```

### <a name="remarks"></a>Poznámky

Zobrazit [PathAddExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddextensiona) podrobnosti.

## <a name="append"></a> ATLPath::Append

Tato funkce je přetížená obálka pro [PathAppend](/windows/desktop/api/shlwapi/nf-shlwapi-pathappenda).

### <a name="syntax"></a>Syntaxe

```
inline BOOL Append(char* pszPath, const char* pszMore);
inline BOOL Append(wchar_t* pszPath, const wchar_t* pszMore);
```

### <a name="remarks"></a>Poznámky

Zobrazit [PathAppend](/windows/desktop/api/shlwapi/nf-shlwapi-pathappenda) podrobnosti.

## <a name="buildroot"></a> ATLPath::BuildRoot

Tato funkce je přetížená obálka pro [PathBuildRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathbuildroota).

### <a name="syntax"></a>Syntaxe

```
inline char* BuildRoot(char* pszPath, int iDrive);
inline wchar_t* BuildRoot(wchar_t* pszPath, int iDrive);
```

### <a name="remarks"></a>Poznámky

Zobrazit [PathBuildRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathbuildroota) podrobnosti.

## <a name="canonicalize"></a> ATLPath::Canonicalize

Tato funkce je přetížená obálka pro [PathCanonicalize](/windows/desktop/api/shlwapi/nf-shlwapi-pathcanonicalizea).

### <a name="syntax"></a>Syntaxe

```
inline BOOL Canonicalize(char* pszDest, const char* pszSrc);
inline BOOL Canonicalize(wchar_t* pszDest, const wchar_t* pszSrc);
```

### <a name="remarks"></a>Poznámky

Zobrazit [PathCanonicalize](/windows/desktop/api/shlwapi/nf-shlwapi-pathcanonicalizea) podrobnosti.

## <a name="combine"></a> ATLPath::Combine

Tato funkce je přetížená obálka pro [PathCombine](/windows/desktop/api/shlwapi/nf-shlwapi-pathcombinea).

### <a name="syntax"></a>Syntaxe

```
inline char* Combine(
   char* pszDest,
   const char* pszDir,
   const char* pszFile
);

inline wchar_t* Combine(
   wchar_t* pszDest,
   const wchar_t* pszDir,
   const wchar_t* pszFile);
```

### <a name="remarks"></a>Poznámky

Podrobnosti najdete v části PathCombine.

## <a name="commonprefix"></a> ATLPath::CommonPrefix

Tato funkce je přetížená obálka pro [PathCommonPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathcommonprefixa).

### <a name="syntax"></a>Syntaxe

```
inline int CommonPrefix(
   const char* pszFile1,
   const char* pszFile2,
   char* pszDest);

inline int CommonPrefix(
   const wchar_t* pszFile1,
   const wchar_t* pszFile2,
   wchar_t* pszDest);
```

### <a name="remarks"></a>Poznámky

Zobrazit [PathCommonPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathcommonprefixa) podrobnosti.

## <a name="compactpath"></a> ATLPath::CompactPath

Tato funkce je přetížená obálka pro [PathCompactPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpatha).

### <a name="syntax"></a>Syntaxe

```
inline BOOL CompactPath(
   HDC hDC,
   char* pszPath,
   UINT dx);

inline BOOL CompactPath(
   HDC hDC,
   wchar_t* pszPath,
   UINT dx);
```

### <a name="remarks"></a>Poznámky

Zobrazit [PathCompactPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpatha) podrobnosti.

## <a name="compactpathex"></a> ATLPath::CompactPathEx

Tato funkce je přetížená obálka pro [PathCompactPathEx](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpathexa).

### <a name="syntax"></a>Syntaxe

```
inline BOOL CompactPathEx(
   char* pszDest,
   const char* pszSrc,
   UINT nMaxChars,
   DWORD dwFlags);

inline BOOL CompactPathEx(
   wchar_t* pszDest,
   const wchar_t* pszSrc,
   UINT nMaxChars,
   DWORD dwFlags);
```

### <a name="remarks"></a>Poznámky

Zobrazit [PathCompactPathEx](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpathexa) podrobnosti.

## <a name="fileexists"></a> ATLPath::FileExists

Tato funkce je přetížená obálka pro [PathFileExists](/windows/desktop/api/shlwapi/nf-shlwapi-pathfileexistsa).

### <a name="syntax"></a>Syntaxe

```
inline BOOL FileExists(const char* pszPath);
inline BOOL FileExists(const wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Zobrazit [PathFileExists](/windows/desktop/api/shlwapi/nf-shlwapi-pathfileexistsa) podrobnosti.

## <a name="findextension"></a> ATLPath::FindExtension

Tato funkce je přetížená obálka pro [PathFindExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindextensiona).

### <a name="syntax"></a>Syntaxe

```
inline char* FindExtension(const char* pszPath);
inline wchar_t* FindExtension(const wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Zobrazit [PathFindExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindextensiona) podrobnosti.

## <a name="findfilename"></a> ATLPath::FindFileName

Tato funkce je přetížená obálka pro [PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea).

### <a name="syntax"></a>Syntaxe

```
inline char* FindFileName(const char* pszPath);
inline wchar_t* FindFileName(const wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Zobrazit [PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea) podrobnosti.

## <a name="getdrivenumber"></a> ATLPath::GetDriveNumber

Tato funkce je přetížená obálka pro [PathGetDriveNumber](/windows/desktop/api/shlwapi/nf-shlwapi-pathgetdrivenumbera).

### <a name="syntax"></a>Syntaxe

```
inline int GetDriveNumber(const char* pszPath);
inline int GetDriveNumber(const wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Zobrazit [PathGetDriveNumber](/windows/desktop/api/shlwapi/nf-shlwapi-pathgetdrivenumbera) podrobnosti.

## <a name="isdirectory"></a>  ATLPath::IsDirectory

Tato funkce je přetížená obálka pro [PathIsDirectory](/windows/desktop/api/shlwapi/nf-shlwapi-pathisdirectorya).

```
inline BOOL IsDirectory(const char* pszPath);
inline BOOL IsDirectory(const wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Podrobnosti najdete v části PathIsDirectory.

## <a name="isfilespec"></a> ATLPath::IsFileSpec

Tato funkce je přetížená obálka pro [PathIsFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathisfilespeca).

### <a name="syntax"></a>Syntaxe

```
inline BOOL IsFileSpec(const char* pszPath);
inline BOOL IsFileSpec(const wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Zobrazit [PathIsFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathisfilespeca) podrobnosti.

## <a name="isprefix"></a> ATLPath::IsPrefix

Tato funkce je přetížená obálka pro [PathIsPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathisprefixa).

### <a name="syntax"></a>Syntaxe

```
inline BOOL IsPrefix(const char* pszPrefix, const char* pszPath);
inline BOOL IsPrefix(const wchar_t* pszPrefix, const wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Zobrazit [PathIsPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathisprefixa) podrobnosti.

## <a name="isrelative"></a> ATLPath::IsRelative

Tato funkce je přetížená obálka pro [PathIsRelative](/windows/desktop/api/shlwapi/nf-shlwapi-pathisrelativea).

### <a name="syntax"></a>Syntaxe

```
inline BOOL IsRelative(const char* pszPath);
inline BOOL IsRelative(const wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Zobrazit [PathIsRelative](/windows/desktop/api/shlwapi/nf-shlwapi-pathisrelativea) podrobnosti.

## <a name="isroot"></a> ATLPath::IsRoot

Tato funkce je přetížená obálka pro [PathIsRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathisroota).

### <a name="syntax"></a>Syntaxe

```
inline BOOL IsRoot(const char* pszPath);
inline BOOL IsRoot(const wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Zobrazit [PathIsRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathisroota) podrobnosti.

## <a name="issameroot"></a> ATLPath::IsSameRoot

Tato funkce je přetížená obálka pro [PathIsSameRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathissameroota).

### <a name="syntax"></a>Syntaxe

```
inline BOOL IsSameRoot(const char* pszPath1, const char* pszPath2);
inline BOOL IsSameRoot(const wchar_t* pszPath1, const wchar_t* pszPath2);
```

### <a name="remarks"></a>Poznámky

Zobrazit [PathIsSameRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathissameroota) podrobnosti.

## <a name="isunc"></a> ATLPath::IsUNC

Tato funkce je přetížená obálka pro [PathIsUNC](/windows/desktop/api/shlwapi/nf-shlwapi-pathisunca).

### <a name="syntax"></a>Syntaxe

```
inline BOOL IsUNC(const char* pszPath);
inline BOOL IsUNC(const wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Zobrazit [PathIsUNC](/windows/desktop/api/shlwapi/nf-shlwapi-pathisunca) podrobnosti.

## <a name="isuncserver"></a> ATLPath::IsUNCServer

Tato funkce je přetížená obálka pro [PathIsUNCServer](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncservera).

### <a name="syntax"></a>Syntaxe

```
inline BOOL IsUNCServer(const char* pszPath);
inline BOOL IsUNCServer(const wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Zobrazit [PathIsUNCServer](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncservera) podrobnosti.

## <a name="isuncservershare"></a> ATLPath::IsUNCServerShare

Tato funkce je přetížená obálka pro [PathIsUNCServerShare](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncserversharea).

### <a name="syntax"></a>Syntaxe

```
inline BOOL IsUNCServerShare(const char* pszPath);
inline BOOL IsUNCServerShare(const wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Zobrazit [PathIsUNCServerShare](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncserversharea) podrobnosti.

## <a name="makepretty"></a> ATLPath::MakePretty

Tato funkce je přetížená obálka pro [PathMakePretty](/windows/desktop/api/shlwapi/nf-shlwapi-pathmakeprettya).

### <a name="syntax"></a>Syntaxe

```
inline BOOL MakePretty(char* pszPath);
inline BOOL MakePretty(wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Zobrazit [PathMakePretty](/windows/desktop/api/shlwapi/nf-shlwapi-pathmakeprettya) podrobnosti.

## <a name="matchspec"></a> ATLPath::MatchSpec

Tato funkce je přetížená obálka pro [PathMatchSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathmatchspeca).

### <a name="syntax"></a>Syntaxe

```
inline BOOL MatchSpec(const char* pszPath, const char* pszSpec);
inline BOOL MatchSpec(const wchar_t* pszPath, const wchar_t* pszSpec);
```

### <a name="remarks"></a>Poznámky

Zobrazit [PathMatchSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathmatchspeca) podrobnosti.

## <a name="quotespaces"></a> ATLPath::QuoteSpaces

Tato funkce je přetížená obálka pro [PathQuoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathquotespacesa).

### <a name="syntax"></a>Syntaxe

```
inline void QuoteSpaces(char* pszPath);
inline void QuoteSpaces(wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Zobrazit [PathQuoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathquotespacesa) podrobnosti.

## <a name="relativepathto"></a> ATLPath::RelativePathTo

Tato funkce je přetížená obálka pro [PathRelativePathTo](/windows/desktop/api/shlwapi/nf-shlwapi-pathrelativepathtoa).

### <a name="syntax"></a>Syntaxe

```
inline BOOL RelativePathTo(
   char* pszPath,
   const char* pszFrom,
   DWORD dwAttrFrom,
   const char* pszTo,
   DWORD dwAttrTo);

inline BOOL RelativePathTo(
   wchar_t* pszPath,
   const wchar_t* pszFrom,
   DWORD dwAttrFrom,
   const wchar_t* pszTo,
   DWORD dwAttrTo);
```

### <a name="remarks"></a>Poznámky

Zobrazit [PathRelativePathTo](/windows/desktop/api/shlwapi/nf-shlwapi-pathrelativepathtoa) podrobnosti.

## <a name="removeargs"></a> ATLPath::RemoveArgs

Tato funkce je přetížená obálka pro [PathRemoveArgs](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveargsa).

### <a name="syntax"></a>Syntaxe

```
inline void RemoveArgs(char* pszPath);
inline void RemoveArgs(wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Zobrazit [PathRemoveArgs](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveargsa) podrobnosti.

## <a name="removebackslash"></a> ATLPath::RemoveBackslash

Tato funkce je přetížená obálka pro [PathRemoveBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovebackslasha).

### <a name="syntax"></a>Syntaxe

```
inline char* RemoveBackslash(char* pszPath);
inline wchar_t* RemoveBackslash(wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Zobrazit [PathRemoveBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovebackslasha) podrobnosti.

## <a name="removeblanks"></a> ATLPath::RemoveBlanks

Tato funkce je přetížená obálka pro [PathRemoveBlanks](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveblanksa).

### <a name="syntax"></a>Syntaxe

```
inline void RemoveBlanks(char* pszPath);
inline void RemoveBlanks(wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Zobrazit [PathRemoveBlanks](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveblanksa) podrobnosti.

## <a name="removeextension"></a> ATLPath::RemoveExtension

Tato funkce je přetížená obálka pro [PathRemoveExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveextensiona).

### <a name="syntax"></a>Syntaxe

```
inline void RemoveExtension(char* pszPath);
inline void RemoveExtension(wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Zobrazit [PathRemoveExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveextensiona) podrobnosti.

## <a name="removefilespec"></a> ATLPath::RemoveFileSpec

Tato funkce je přetížená obálka pro [PathRemoveFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovefilespeca).

### <a name="syntax"></a>Syntaxe

```
inline BOOL RemoveFileSpec(char* pszPath);
inline BOOL RemoveFileSpec(wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Zobrazit [PathRemoveFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovefilespeca) podrobnosti.

## <a name="renameextension"></a> ATLPath::RenameExtension

Tato funkce je přetížená obálka pro [PathRenameExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathrenameextensiona).

### <a name="syntax"></a>Syntaxe

```
inline BOOL RenameExtension(char* pszPath, const char* pszExt);
inline BOOL RenameExtension(wchar_t* pszPath, const wchar_t* pszExt);
```

### <a name="remarks"></a>Poznámky

Zobrazit [PathRenameExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathrenameextensiona) podrobnosti.

## <a name="skiproot"></a> ATLPath::SkipRoot

Tato funkce je přetížená obálka pro [PathSkipRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathskiproota).

### <a name="syntax"></a>Syntaxe

```
inline char* SkipRoot(const char* pszPath);
inline wchar_t* SkipRoot(const wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Zobrazit [PathSkipRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathskiproota) podrobnosti.

## <a name="strippath"></a> ATLPath::StripPath

Tato funkce je přetížená obálka pro [PathStripPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathstrippatha).

### <a name="syntax"></a>Syntaxe

```
inline void StripPath(char* pszPath);
inline void StripPath(wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Zobrazit [PathStripPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathstrippatha) podrobnosti.

## <a name="striptoroot"></a> ATLPath::StripToRoot

Tato funkce je přetížená obálka pro [PathStripToRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathstriptoroota).

### <a name="syntax"></a>Syntaxe

```
inline BOOL StripToRoot(char* pszPath);
inline BOOL StripToRoot(wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Zobrazit [PathStripToRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathstriptoroota) podrobnosti.

## <a name="unquotespaces"></a> ATLPath::UnquoteSpaces

Tato funkce je přetížená obálka pro [PathUnquoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathunquotespacesa).

### <a name="syntax"></a>Syntaxe

```
inline void UnquoteSpaces(char* pszPath);
inline void UnquoteSpaces(wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Zobrazit [PathUnquoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathunquotespacesa) podrobnosti.

