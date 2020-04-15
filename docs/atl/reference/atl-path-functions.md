---
title: Funkce cesty ATL
ms.date: 11/04/2016
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
ms.openlocfilehash: f3d8fa63e7fd20f8a0d6759fee8417b3fbc29486
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319221"
---
# <a name="atl-path-functions"></a>Funkce cesty ATL

ATL poskytuje třídu ATLPath pro manipulaci s cestami ve formě [CPathT](cpatht-class.md). Tento kód naleznete v atlpath.h.

### <a name="related-classes"></a>Související třídy

|||
|-|-|
|[Třída CPathT](cpatht-class.md)|Tato třída představuje cestu.|

### <a name="related-typedefs"></a>Související typedefs

|||
|-|-|
|`CPath`|Specializace [CPathT](cpatht-class.md) pomocí `CString`.|
|`CPathA`|Specializace [CPathT](cpatht-class.md) pomocí `CStringA`.|
|`CPathW`|Specializace [CPathT](cpatht-class.md) pomocí `CStringW`.|

### <a name="functions"></a>Functions

|||
|-|-|
|[ATLPath::AddBackslash](#addbackslash)|Tato funkce je přetížené obálky pro [PathAddBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw).|
|[ATLPath::AddExtension](#addextension)|Tato funkce je přetížené obálky pro [PathAddExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw).|
|[ATLPath::Připojit](#append)|Tato funkce je přetížené obálky pro [PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw).|
|[ATLPath::Kořenovou mocnina sestavení](#buildroot)|Tato funkce je přetížené obálky pro [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw).|
|[ATLPath::Kanoián](#canonicalize)|Tato funkce je přetížené obálky pro [PathCanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew).|
|[ATLPath::Kombinovat](#combine)|Tato funkce je přetížené obálky pro [PathCombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew).|
|[ATLPath::CommonPrefix](#commonprefix)|Tato funkce je přetížené obálky pro [PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw).|
|[ATLPath::CompactPath](#compactpath)|Tato funkce je přetížené obálky pro [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw).|
|[ATLPath::CompactPathEx](#compactpathex)|Tato funkce je přetížené obálky pro [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw).|
|[ATLPath::FileExists](#fileexists)|Tato funkce je přetížené obálky pro [PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw).|
|[ATLPath::FindExtension](#findextension)|Tato funkce je přetížené obálky pro [PathFindExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw).|
|[ATLPath::FindFileName](#findfilename)|Tato funkce je přetížené obálky pro [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew).|
|[ATLPath::GetDriveNumber](#getdrivenumber)|Tato funkce je přetížené obálky pro [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw).|
|[ATLPath::IsDirectory](#isdirectory)|Tato funkce je přetížené obálky pro [PathIsDirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw).|
|[ATLPath::IsFileSpec](#isfilespec)|Tato funkce je přetížené obálky pro [PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw).|
|[ATLPath::IsPrefix](#isprefix)|Tato funkce je přetížené obálky pro [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw).|
|[ATLPath::Jerelativní](#isrelative)|Tato funkce je přetížené obálky pro [PathIsRelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew).|
|[ATLPath::Kořenová_obec](#isroot)|Tato funkce je přetížené obálky pro [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw).|
|[ATLPath::IsSameRoot](#issameroot)|Tato funkce je přetížené obálky pro [PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw).|
|[ATLPath::IsUNC](#isunc)|Tato funkce je přetížené obálky pro [PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw).|
|[ATLPath::IsUNCServer](#isuncserver)|Tato funkce je přetížené obálky pro [PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw).|
|[ATLPath::IsUNCServerShare](#isuncservershare)|Tato funkce je přetížené obálky pro [PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew).|
|[ATLPath::MakePretty](#makepretty)|Tato funkce je přetížené obálky pro [PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw).|
|[ATLPath::MatchSpec](#matchspec)|Tato funkce je přetížené obálky pro [PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw).|
|[ATLPath::Mezery v uvozovkách](#quotespaces)|Tato funkce je přetížené obálky pro [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw).|
|[ATLPath::RelativePathTo](#relativepathto)|Tato funkce je přetížené obálky pro [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow).|
|[ATLPath::RemoveArgs](#removeargs)|Tato funkce je přetížené obálky pro [PathRemoveArgs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw).|
|[ATLPath::RemoveBackslash](#removebackslash)|Tato funkce je přetížené obálky pro [PathRemoveBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw).|
|[ATLPath::RemoveBlanks](#removeblanks)|Tato funkce je přetížené obálky pro [PathRemoveBlanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw).|
|[ATLPath::RemoveExtension](#removeextension)|Tato funkce je přetížené obálky pro [PathRemoveExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw).|
|[ATLPath::RemoveFileSpec](#removefilespec)|Tato funkce je přetížené obálky pro [PathRemoveFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw).|
|[ATLPath::Přejmenovatrozšíření](#renameextension)|Tato funkce je přetížené obálky pro [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw).|
|[ATLPath::Přeskočení kořenové adresáře](#skiproot)|Tato funkce je přetížené obálky pro [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw).|
|[ATLPath::Strippath](#strippath)|Tato funkce je přetížené obálky pro [PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw).|
|[ATLPath::StripToroot](#striptoroot)|Tato funkce je přetížené obálky pro [PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw).|
|[ATLPath::UnquoteSpaces](#unquotespaces)|Tato funkce je přetížené obálky pro [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw).|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlpath.h

## <a name="atlpathaddbackslash"></a><a name="addbackslash"></a>ATLPath::AddBackSlash

Tato funkce je přetížené obálky pro [PathAddBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw).

### <a name="syntax"></a>Syntaxe

```
inline char* AddBackslash(char* pszPath);
inline wchar_t* AddBackslash(wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Podrobnosti najdete v tématu [PathAddBackslash.](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw)

## <a name="atlpathaddextension"></a><a name="addextension"></a>ATLPath::AddExtension

Tato funkce je přetížené obálky pro [PathAddExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw).

### <a name="syntax"></a>Syntaxe

```
inline BOOL AddExtension(char* pszPath, const char* pszExtension);
inline BOOL AddExtension(wchar_t* pszPath, const wchar_t* pszExtension);
```

### <a name="remarks"></a>Poznámky

Podrobnosti najdete v [tématu PathAddExtension.](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw)

## <a name="atlpathappend"></a><a name="append"></a>ATLPath::Připojit

Tato funkce je přetížené obálky pro [PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw).

### <a name="syntax"></a>Syntaxe

```
inline BOOL Append(char* pszPath, const char* pszMore);
inline BOOL Append(wchar_t* pszPath, const wchar_t* pszMore);
```

### <a name="remarks"></a>Poznámky

Podrobnosti najdete v [tématu PathAppend.](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw)

## <a name="atlpathbuildroot"></a><a name="buildroot"></a>ATLPath::Kořenovou mocnina sestavení

Tato funkce je přetížené obálky pro [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw).

### <a name="syntax"></a>Syntaxe

```
inline char* BuildRoot(char* pszPath, int iDrive);
inline wchar_t* BuildRoot(wchar_t* pszPath, int iDrive);
```

### <a name="remarks"></a>Poznámky

Podrobnosti najdete v [tématu PathBuildRoot.](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw)

## <a name="atlpathcanonicalize"></a><a name="canonicalize"></a>ATLPath::Kanoián

Tato funkce je přetížené obálky pro [PathCanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew).

### <a name="syntax"></a>Syntaxe

```
inline BOOL Canonicalize(char* pszDest, const char* pszSrc);
inline BOOL Canonicalize(wchar_t* pszDest, const wchar_t* pszSrc);
```

### <a name="remarks"></a>Poznámky

Podrobnosti najdete v [tématu PathCanonicalize.](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew)

## <a name="atlpathcombine"></a><a name="combine"></a>ATLPath::Kombinovat

Tato funkce je přetížené obálky pro [PathCombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew).

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

Podrobnosti najdete v tématu PathCombine.

## <a name="atlpathcommonprefix"></a><a name="commonprefix"></a>ATLPath::CommonPrefix

Tato funkce je přetížené obálky pro [PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw).

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

Podrobnosti naleznete v tématu [PathCommonPrefix.](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw)

## <a name="atlpathcompactpath"></a><a name="compactpath"></a>ATLPath::CompactPath

Tato funkce je přetížené obálky pro [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw).

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

Podrobnosti najdete v [tématu PathCompactPath.](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw)

## <a name="atlpathcompactpathex"></a><a name="compactpathex"></a>ATLPath::CompactPathEx

Tato funkce je přetížené obálky pro [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw).

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

Podrobnosti najdete v [tématu PathCompactPathEx.](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw)

## <a name="atlpathfileexists"></a><a name="fileexists"></a>ATLPath::FileExists

Tato funkce je přetížené obálky pro [PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw).

### <a name="syntax"></a>Syntaxe

```
inline BOOL FileExists(const char* pszPath);
inline BOOL FileExists(const wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Podrobnosti naleznete v tématu [PathFileExists.](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw)

## <a name="atlpathfindextension"></a><a name="findextension"></a>ATLPath::FindExtension

Tato funkce je přetížené obálky pro [PathFindExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw).

### <a name="syntax"></a>Syntaxe

```
inline char* FindExtension(const char* pszPath);
inline wchar_t* FindExtension(const wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Podrobnosti najdete v [tématu PathFindExtension.](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw)

## <a name="atlpathfindfilename"></a><a name="findfilename"></a>ATLPath::FindFileName

Tato funkce je přetížené obálky pro [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew).

### <a name="syntax"></a>Syntaxe

```
inline char* FindFileName(const char* pszPath);
inline wchar_t* FindFileName(const wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Podrobnosti najdete v tématu [PathFindFileName.](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew)

## <a name="atlpathgetdrivenumber"></a><a name="getdrivenumber"></a>ATLPath::GetDriveNumber

Tato funkce je přetížené obálky pro [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw).

### <a name="syntax"></a>Syntaxe

```
inline int GetDriveNumber(const char* pszPath);
inline int GetDriveNumber(const wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Podrobnosti najdete v [tématu PathGetDriveNumber.](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw)

## <a name="atlpathisdirectory"></a><a name="isdirectory"></a>ATLPath::IsDirectory

Tato funkce je přetížené obálky pro [PathIsDirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw).

```
inline BOOL IsDirectory(const char* pszPath);
inline BOOL IsDirectory(const wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Podrobnosti naleznete v tématu PathIsDirectory.

## <a name="atlpathisfilespec"></a><a name="isfilespec"></a>ATLPath::IsFileSpec

Tato funkce je přetížené obálky pro [PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw).

### <a name="syntax"></a>Syntaxe

```
inline BOOL IsFileSpec(const char* pszPath);
inline BOOL IsFileSpec(const wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Podrobnosti naleznete v tématu [PathIsFileSpec.](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw)

## <a name="atlpathisprefix"></a><a name="isprefix"></a>ATLPath::IsPrefix

Tato funkce je přetížené obálky pro [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw).

### <a name="syntax"></a>Syntaxe

```
inline BOOL IsPrefix(const char* pszPrefix, const char* pszPath);
inline BOOL IsPrefix(const wchar_t* pszPrefix, const wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Podrobnosti naleznete v tématu [PathIsPrefix.](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw)

## <a name="atlpathisrelative"></a><a name="isrelative"></a>ATLPath::Jerelativní

Tato funkce je přetížené obálky pro [PathIsRelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew).

### <a name="syntax"></a>Syntaxe

```
inline BOOL IsRelative(const char* pszPath);
inline BOOL IsRelative(const wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Podrobnosti naleznete v [tématu PathIsRelative.](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew)

## <a name="atlpathisroot"></a><a name="isroot"></a>ATLPath::Kořenová_obec

Tato funkce je přetížené obálky pro [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw).

### <a name="syntax"></a>Syntaxe

```
inline BOOL IsRoot(const char* pszPath);
inline BOOL IsRoot(const wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Podrobnosti najdete v [tématu PathIsRoot.](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw)

## <a name="atlpathissameroot"></a><a name="issameroot"></a>ATLPath::IsSameRoot

Tato funkce je přetížené obálky pro [PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw).

### <a name="syntax"></a>Syntaxe

```
inline BOOL IsSameRoot(const char* pszPath1, const char* pszPath2);
inline BOOL IsSameRoot(const wchar_t* pszPath1, const wchar_t* pszPath2);
```

### <a name="remarks"></a>Poznámky

Podrobnosti najdete v [tématu PathIsSameRoot.](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw)

## <a name="atlpathisunc"></a><a name="isunc"></a>ATLPath::IsUNC

Tato funkce je přetížené obálky pro [PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw).

### <a name="syntax"></a>Syntaxe

```
inline BOOL IsUNC(const char* pszPath);
inline BOOL IsUNC(const wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Podrobnosti naleznete v tématu [PathIsUNC.](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw)

## <a name="atlpathisuncserver"></a><a name="isuncserver"></a>ATLPath::IsUNCServer

Tato funkce je přetížené obálky pro [PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw).

### <a name="syntax"></a>Syntaxe

```
inline BOOL IsUNCServer(const char* pszPath);
inline BOOL IsUNCServer(const wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Podrobnosti naleznete v tématu [PathIsUNCServer.](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw)

## <a name="atlpathisuncservershare"></a><a name="isuncservershare"></a>ATLPath::IsUNCServerShare

Tato funkce je přetížené obálky pro [PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew).

### <a name="syntax"></a>Syntaxe

```
inline BOOL IsUNCServerShare(const char* pszPath);
inline BOOL IsUNCServerShare(const wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Podrobnosti naleznete v tématu [PathIsUNCServerShare.](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew)

## <a name="atlpathmakepretty"></a><a name="makepretty"></a>ATLPath::MakePretty

Tato funkce je přetížené obálky pro [PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw).

### <a name="syntax"></a>Syntaxe

```
inline BOOL MakePretty(char* pszPath);
inline BOOL MakePretty(wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Podrobnosti najdete v [tématu PathMakePretty.](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw)

## <a name="atlpathmatchspec"></a><a name="matchspec"></a>ATLPath::MatchSpec

Tato funkce je přetížené obálky pro [PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw).

### <a name="syntax"></a>Syntaxe

```
inline BOOL MatchSpec(const char* pszPath, const char* pszSpec);
inline BOOL MatchSpec(const wchar_t* pszPath, const wchar_t* pszSpec);
```

### <a name="remarks"></a>Poznámky

Podrobnosti naleznete v tématu [PathMatchSpec.](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw)

## <a name="atlpathquotespaces"></a><a name="quotespaces"></a>ATLPath::Mezery v uvozovkách

Tato funkce je přetížené obálky pro [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw).

### <a name="syntax"></a>Syntaxe

```
inline void QuoteSpaces(char* pszPath);
inline void QuoteSpaces(wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Podrobnosti najdete v [tématu PathQuoteSpaces.](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw)

## <a name="atlpathrelativepathto"></a><a name="relativepathto"></a>ATLPath::RelativePathTo

Tato funkce je přetížené obálky pro [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow).

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

Podrobnosti naleznete v [tématu PathRelativePathTo.](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow)

## <a name="atlpathremoveargs"></a><a name="removeargs"></a>ATLPath::RemoveArgs

Tato funkce je přetížené obálky pro [PathRemoveArgs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw).

### <a name="syntax"></a>Syntaxe

```
inline void RemoveArgs(char* pszPath);
inline void RemoveArgs(wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Podrobnosti naleznete v tématu [PathRemoveArgs.](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw)

## <a name="atlpathremovebackslash"></a><a name="removebackslash"></a>ATLPath::RemoveBackslash

Tato funkce je přetížené obálky pro [PathRemoveBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw).

### <a name="syntax"></a>Syntaxe

```
inline char* RemoveBackslash(char* pszPath);
inline wchar_t* RemoveBackslash(wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Podrobnosti najdete v tématu [PathRemoveBackslash.](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw)

## <a name="atlpathremoveblanks"></a><a name="removeblanks"></a>ATLPath::RemoveBlanks

Tato funkce je přetížené obálky pro [PathRemoveBlanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw).

### <a name="syntax"></a>Syntaxe

```
inline void RemoveBlanks(char* pszPath);
inline void RemoveBlanks(wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Podrobnosti najdete v [tématu PathRemoveBlanks.](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw)

## <a name="atlpathremoveextension"></a><a name="removeextension"></a>ATLPath::RemoveExtension

Tato funkce je přetížené obálky pro [PathRemoveExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw).

### <a name="syntax"></a>Syntaxe

```
inline void RemoveExtension(char* pszPath);
inline void RemoveExtension(wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Podrobnosti najdete v [tématu PathRemoveExtension.](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw)

## <a name="atlpathremovefilespec"></a><a name="removefilespec"></a>ATLPath::RemoveFileSpec

Tato funkce je přetížené obálky pro [PathRemoveFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw).

### <a name="syntax"></a>Syntaxe

```
inline BOOL RemoveFileSpec(char* pszPath);
inline BOOL RemoveFileSpec(wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Podrobnosti najdete v [tématu PathRemoveFileSpec.](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw)

## <a name="atlpathrenameextension"></a><a name="renameextension"></a>ATLPath::Přejmenovatrozšíření

Tato funkce je přetížené obálky pro [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw).

### <a name="syntax"></a>Syntaxe

```
inline BOOL RenameExtension(char* pszPath, const char* pszExt);
inline BOOL RenameExtension(wchar_t* pszPath, const wchar_t* pszExt);
```

### <a name="remarks"></a>Poznámky

Podrobnosti najdete v [tématu PathRenameExtension.](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw)

## <a name="atlpathskiproot"></a><a name="skiproot"></a>ATLPath::Přeskočení kořenové adresáře

Tato funkce je přetížené obálky pro [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw).

### <a name="syntax"></a>Syntaxe

```
inline char* SkipRoot(const char* pszPath);
inline wchar_t* SkipRoot(const wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Podrobnosti najdete v [tématu PathSkipRoot.](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw)

## <a name="atlpathstrippath"></a><a name="strippath"></a>ATLPath::Strippath

Tato funkce je přetížené obálky pro [PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw).

### <a name="syntax"></a>Syntaxe

```
inline void StripPath(char* pszPath);
inline void StripPath(wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Podrobnosti najdete v [tématu PathStripPath.](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw)

## <a name="atlpathstriptoroot"></a><a name="striptoroot"></a>ATLPath::StripToroot

Tato funkce je přetížené obálky pro [PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw).

### <a name="syntax"></a>Syntaxe

```
inline BOOL StripToRoot(char* pszPath);
inline BOOL StripToRoot(wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Podrobnosti najdete v [tématu PathStripToRoot.](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw)

## <a name="atlpathunquotespaces"></a><a name="unquotespaces"></a>ATLPath::UnquoteSpaces

Tato funkce je přetížené obálky pro [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw).

### <a name="syntax"></a>Syntaxe

```
inline void UnquoteSpaces(char* pszPath);
inline void UnquoteSpaces(wchar_t* pszPath);
```

### <a name="remarks"></a>Poznámky

Podrobnosti najdete v [tématu PathUnquoteSpaces.](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw)
