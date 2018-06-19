---
title: Funkce knihovny ATL cesta | Microsoft Docs
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
ms.openlocfilehash: 38286d169591dd55f7a2618332b6f5d5c9c86719
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366533"
---
# <a name="atl-path-functions"></a>Funkce cesta knihovny ATL

ATL poskytuje třídu ATLPath pro manipulaci s cesty ve formě [CPathT](cpatht-class.md). Tento kód lze nalézt v atlpath.h.  
  
### <a name="related-classes"></a>Související třídy  
  
|||  
|-|-|  
|[CPathT – třída](cpatht-class.md)|Tato třída reprezentuje cestu.|  

### <a name="related-typedefs"></a>Související – definice TypeDef  
  
|||  
|-|-|  
|`CPath`|Specializace z [CPathT](cpatht-class.md) pomocí `CString`.|  
|`CPathA`|Specializace z [CPathT](cpatht-class.md) pomocí `CStringA`.|  
|`CPathW`|Specializace z [CPathT](cpatht-class.md) pomocí `CStringW`.|  
  
### <a name="functions"></a>Funkce  
  
|||  
|-|-|  
|[ATLPath::AddBackslash](#addbackslash)|Tato funkce je přetížené obálku pro [PathAddBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773561).|  
|[ATLPath::AddExtension](#addextension)|Tato funkce je přetížené obálku pro [PathAddExtension](http://msdn.microsoft.com/library/windows/desktop/bb773563).|  
|[ATLPath::Append](#append)|Tato funkce je přetížené obálku pro [PathAppend](http://msdn.microsoft.com/library/windows/desktop/bb773565).|  
|[ATLPath::BuildRoot](#buildroot)|Tato funkce je přetížené obálku pro [PathBuildRoot](http://msdn.microsoft.com/library/windows/desktop/bb773567).|  
|[ATLPath::Canonicalize](#canonicalize)|Tato funkce je přetížené obálku pro [PathCanonicalize](http://msdn.microsoft.com/library/windows/desktop/bb773569).|  
|[ATLPath::Combine](#combine)|Tato funkce je přetížené obálku pro [PathCombine](http://msdn.microsoft.com/library/windows/desktop/bb773571).|  
|[ATLPath::CommonPrefix](#commonprefix)|Tato funkce je přetížené obálku pro [PathCommonPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773574).|  
|[ATLPath::CompactPath](#compactpath)|Tato funkce je přetížené obálku pro [PathCompactPath](http://msdn.microsoft.com/library/windows/desktop/bb773575).|  
|[ATLPath::CompactPathEx](#compactpathex)|Tato funkce je přetížené obálku pro [PathCompactPathEx](http://msdn.microsoft.com/library/windows/desktop/bb773578).|  
|[ATLPath::FileExists](#fileexists)|Tato funkce je přetížené obálku pro [PathFileExists](http://msdn.microsoft.com/library/windows/desktop/bb773584).|  
|[ATLPath::FindExtension](#findextension)|Tato funkce je přetížené obálku pro [PathFindExtension](http://msdn.microsoft.com/library/windows/desktop/bb773587).|  
|[ATLPath::FindFileName](#findfilename)|Tato funkce je přetížené obálku pro [PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589).|  
|[ATLPath::GetDriveNumber](#getdrivenumber)|Tato funkce je přetížené obálku pro [PathGetDriveNumber](http://msdn.microsoft.com/library/windows/desktop/bb773612).|  
|[ATLPath::IsDirectory](#isdirectory)|Tato funkce je přetížené obálku pro [PathIsDirectory](http://msdn.microsoft.com/library/windows/desktop/bb773621).|  
|[ATLPath::IsFileSpec](#isfilespec)|Tato funkce je přetížené obálku pro [PathIsFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773627).|  
|[ATLPath::IsPrefix](#isprefix)|Tato funkce je přetížené obálku pro [PathIsPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773650).|  
|[ATLPath::IsRelative](#isrelative)|Tato funkce je přetížené obálku pro [PathIsRelative](http://msdn.microsoft.com/library/windows/desktop/bb773660).|  
|[ATLPath::IsRoot](#isroot)|Tato funkce je přetížené obálku pro [PathIsRoot](http://msdn.microsoft.com/library/windows/desktop/bb773674).|  
|[ATLPath::IsSameRoot](#issameroot)|Tato funkce je přetížené obálku pro [PathIsSameRoot](http://msdn.microsoft.com/library/windows/desktop/bb773687).|  
|[ATLPath::IsUNC](#isunc)|Tato funkce je přetížené obálku pro [PathIsUNC](http://msdn.microsoft.com/library/windows/desktop/bb773712).|  
|[ATLPath::IsUNCServer](#isuncserver)|Tato funkce je přetížené obálku pro [PathIsUNCServer](http://msdn.microsoft.com/library/windows/desktop/bb773722).|  
|[ATLPath::IsUNCServerShare](#isuncservershare)|Tato funkce je přetížené obálku pro [PathIsUNCServerShare](http://msdn.microsoft.com/library/windows/desktop/bb773723).|  
|[ATLPath::MakePretty](#makepretty)|Tato funkce je přetížené obálku pro [PathMakePretty](http://msdn.microsoft.com/library/windows/desktop/bb773725).|  
|[ATLPath::MatchSpec](#matchspec)|Tato funkce je přetížené obálku pro [PathMatchSpec](http://msdn.microsoft.com/library/windows/desktop/bb773727).|  
|[ATLPath::QuoteSpaces](#quotespaces)|Tato funkce je přetížené obálku pro [PathQuoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773739).|  
|[ATLPath::RelativePathTo](#relativepathto)|Tato funkce je přetížené obálku pro [PathRelativePathTo](http://msdn.microsoft.com/library/windows/desktop/bb773740).|  
|[ATLPath::RemoveArgs](#removeargs)|Tato funkce je přetížené obálku pro [PathRemoveArgs](http://msdn.microsoft.com/library/windows/desktop/bb773742).|  
|[ATLPath::RemoveBackslash](#removebackslash)|Tato funkce je přetížené obálku pro [PathRemoveBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773743).|  
|[ATLPath::RemoveBlanks](#removeblanks)|Tato funkce je přetížené obálku pro [PathRemoveBlanks](http://msdn.microsoft.com/library/windows/desktop/bb773745).|  
|[ATLPath::RemoveExtension](#removeextension)|Tato funkce je přetížené obálku pro [PathRemoveExtension](http://msdn.microsoft.com/library/windows/desktop/bb773746).|  
|[ATLPath::RemoveFileSpec](#removefilespec)|Tato funkce je přetížené obálku pro [PathRemoveFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773748).|  
|[ATLPath::RenameExtension](#renameextension)|Tato funkce je přetížené obálku pro [PathRenameExtension](http://msdn.microsoft.com/library/windows/desktop/bb773749).|  
|[ATLPath::SkipRoot](#skiproot)|Tato funkce je přetížené obálku pro [PathSkipRoot](http://msdn.microsoft.com/library/windows/desktop/bb773754).|  
|[ATLPath::StripPath](#strippath)|Tato funkce je přetížené obálku pro [PathStripPath](http://msdn.microsoft.com/library/windows/desktop/bb773756).|  
|[ATLPath::StripToRoot](#striptoroot)|Tato funkce je přetížené obálku pro [PathStripToRoot](http://msdn.microsoft.com/library/windows/desktop/bb773757).|  
|[ATLPath::UnquoteSpaces](#unquotespaces)|Tato funkce je přetížené obálku pro [PathUnquoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773763).|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlpath.h  

## <a name="addbackslash"></a> ATLPath::AddBackSlash

Tato funkce je přetížené obálku pro [PathAddBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773561).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline char* AddBackslash(char* pszPath);  
inline wchar_t* AddBackslash(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [PathAddBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773561) podrobnosti.  
  
 
  

## <a name="addextension"></a> ATLPath::AddExtension
 Tato funkce je přetížené obálku pro [PathAddExtension](http://msdn.microsoft.com/library/windows/desktop/bb773563).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline BOOL AddExtension(char* pszPath, const char* pszExtension);  
inline BOOL AddExtension(wchar_t* pszPath, const wchar_t* pszExtension);  
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [PathAddExtension](http://msdn.microsoft.com/library/windows/desktop/bb773563) podrobnosti. 
  
## <a name="append"></a> ATLPath::Append
 Tato funkce je přetížené obálku pro [PathAppend](http://msdn.microsoft.com/library/windows/desktop/bb773565).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline BOOL Append(char* pszPath, const char* pszMore);  
inline BOOL Append(wchar_t* pszPath, const wchar_t* pszMore);  
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [PathAppend](http://msdn.microsoft.com/library/windows/desktop/bb773565) podrobnosti.  
  
 
  

## <a name="buildroot"></a> ATLPath::BuildRoot
 Tato funkce je přetížené obálku pro [PathBuildRoot](http://msdn.microsoft.com/library/windows/desktop/bb773567).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline char* BuildRoot(char* pszPath, int iDrive);  
inline wchar_t* BuildRoot(wchar_t* pszPath, int iDrive);  
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [PathBuildRoot](http://msdn.microsoft.com/library/windows/desktop/bb773567) podrobnosti.  
  
 
  

## <a name="canonicalize"></a> ATLPath::Canonicalize
 Tato funkce je přetížené obálku pro [PathCanonicalize](http://msdn.microsoft.com/library/windows/desktop/bb773569).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline BOOL Canonicalize(char* pszDest, const char* pszSrc);  
inline BOOL Canonicalize(wchar_t* pszDest, const wchar_t* pszSrc);  
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [PathCanonicalize](http://msdn.microsoft.com/library/windows/desktop/bb773569) podrobnosti.  
  
 
  

## <a name="combine"></a> ATLPath::Combine 
Tato funkce je přetížené obálku pro [PathCombine](https://msdn.microsoft.com/en-us/library/windows/desktop/bb773571).  

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
Podrobnosti najdete v PathCombine.


## <a name="commonprefix"></a> ATLPath::CommonPrefix
 Tato funkce je přetížené obálku pro [PathCommonPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773574).  
  
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
 V tématu [PathCommonPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773574) podrobnosti.  
  
 
  

## <a name="compactpath"></a> ATLPath::CompactPath
 Tato funkce je přetížené obálku pro [PathCompactPath](http://msdn.microsoft.com/library/windows/desktop/bb773575).  
  
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
 V tématu [PathCompactPath](http://msdn.microsoft.com/library/windows/desktop/bb773575) podrobnosti.  
  
 
  

## <a name="compactpathex"></a> ATLPath::CompactPathEx
 Tato funkce je přetížené obálku pro [PathCompactPathEx](http://msdn.microsoft.com/library/windows/desktop/bb773578).  
  
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
 V tématu [PathCompactPathEx](http://msdn.microsoft.com/library/windows/desktop/bb773578) podrobnosti.  
  
 
  

## <a name="fileexists"></a> ATLPath::FileExists
 Tato funkce je přetížené obálku pro [PathFileExists](http://msdn.microsoft.com/library/windows/desktop/bb773584).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline BOOL FileExists(const char* pszPath);  
inline BOOL FileExists(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [PathFileExists](http://msdn.microsoft.com/library/windows/desktop/bb773584) podrobnosti.  
  
 
  

## <a name="findextension"></a> ATLPath::FindExtension
 Tato funkce je přetížené obálku pro [PathFindExtension](http://msdn.microsoft.com/library/windows/desktop/bb773587).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline char* FindExtension(const char* pszPath);  
inline wchar_t* FindExtension(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [PathFindExtension](http://msdn.microsoft.com/library/windows/desktop/bb773587) podrobnosti.  
  
 
  

## <a name="findfilename"></a> ATLPath::FindFileName
 Tato funkce je přetížené obálku pro [PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline char* FindFileName(const char* pszPath);  
inline wchar_t* FindFileName(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589) podrobnosti.  
  
 
  

## <a name="getdrivenumber"></a> ATLPath::GetDriveNumber  
 Tato funkce je přetížené obálku pro [PathGetDriveNumber](http://msdn.microsoft.com/library/windows/desktop/bb773612).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline int GetDriveNumber(const char* pszPath);  
inline int GetDriveNumber(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [PathGetDriveNumber](http://msdn.microsoft.com/library/windows/desktop/bb773612) podrobnosti.  
  
 


## <a name="isdirectory"></a>  ATLPath::IsDirectory 
Tato funkce je přetížené obálku pro [PathIsDirectory](https://msdn.microsoft.com/en-us/library/windows/desktop/bb773621).

```  
inline BOOL IsDirectory(const char* pszPath);
inline BOOL IsDirectory(const wchar_t* pszPath);
```  
### <a name="remarks"></a>Poznámky
Podrobnosti najdete v PathIsDirectory.  

## <a name="isfilespec"></a> ATLPath::IsFileSpec
 Tato funkce je přetížené obálku pro [PathIsFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773627).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline BOOL IsFileSpec(const char* pszPath);  
inline BOOL IsFileSpec(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [PathIsFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773627) podrobnosti.  
  
 
  

## <a name="isprefix"></a> ATLPath::IsPrefix
 Tato funkce je přetížené obálku pro [PathIsPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773650).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline BOOL IsPrefix(const char* pszPrefix, const char* pszPath);  
inline BOOL IsPrefix(const wchar_t* pszPrefix, const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [PathIsPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773650) podrobnosti.  
  
 
  

## <a name="isrelative"></a> ATLPath::IsRelative
 Tato funkce je přetížené obálku pro [PathIsRelative](http://msdn.microsoft.com/library/windows/desktop/bb773660).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline BOOL IsRelative(const char* pszPath);  
inline BOOL IsRelative(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [PathIsRelative](http://msdn.microsoft.com/library/windows/desktop/bb773660) podrobnosti.  
  
 
  

## <a name="isroot"></a> ATLPath::IsRoot
 Tato funkce je přetížené obálku pro [PathIsRoot](http://msdn.microsoft.com/library/windows/desktop/bb773674).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline BOOL IsRoot(const char* pszPath);  
inline BOOL IsRoot(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [PathIsRoot](http://msdn.microsoft.com/library/windows/desktop/bb773674) podrobnosti.  
  
 
  

## <a name="issameroot"></a> ATLPath::IsSameRoot
 Tato funkce je přetížené obálku pro [PathIsSameRoot](http://msdn.microsoft.com/library/windows/desktop/bb773687).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline BOOL IsSameRoot(const char* pszPath1, const char* pszPath2);  
inline BOOL IsSameRoot(const wchar_t* pszPath1, const wchar_t* pszPath2);  
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [PathIsSameRoot](http://msdn.microsoft.com/library/windows/desktop/bb773687) podrobnosti.  
  
 
  

## <a name="isunc"></a> ATLPath::IsUNC
 Tato funkce je přetížené obálku pro [PathIsUNC](http://msdn.microsoft.com/library/windows/desktop/bb773712).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline BOOL IsUNC(const char* pszPath);  
inline BOOL IsUNC(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [PathIsUNC](http://msdn.microsoft.com/library/windows/desktop/bb773712) podrobnosti.  
  
 
  

## <a name="isuncserver"></a> ATLPath::IsUNCServer
 Tato funkce je přetížené obálku pro [PathIsUNCServer](http://msdn.microsoft.com/library/windows/desktop/bb773722).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline BOOL IsUNCServer(const char* pszPath);  
inline BOOL IsUNCServer(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [PathIsUNCServer](http://msdn.microsoft.com/library/windows/desktop/bb773722) podrobnosti.  
  
 
  

## <a name="isuncservershare"></a> ATLPath::IsUNCServerShare
 Tato funkce je přetížené obálku pro [PathIsUNCServerShare](http://msdn.microsoft.com/library/windows/desktop/bb773723).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline BOOL IsUNCServerShare(const char* pszPath);  
inline BOOL IsUNCServerShare(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [PathIsUNCServerShare](http://msdn.microsoft.com/library/windows/desktop/bb773723) podrobnosti.  
  
 
  

## <a name="makepretty"></a> ATLPath::MakePretty
 Tato funkce je přetížené obálku pro [PathMakePretty](http://msdn.microsoft.com/library/windows/desktop/bb773725).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline BOOL MakePretty(char* pszPath);  
inline BOOL MakePretty(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [PathMakePretty](http://msdn.microsoft.com/library/windows/desktop/bb773725) podrobnosti.  
  
 
  

## <a name="matchspec"></a> ATLPath::MatchSpec  
 Tato funkce je přetížené obálku pro [PathMatchSpec](http://msdn.microsoft.com/library/windows/desktop/bb773727).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline BOOL MatchSpec(const char* pszPath, const char* pszSpec);  
inline BOOL MatchSpec(const wchar_t* pszPath, const wchar_t* pszSpec);  
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [PathMatchSpec](http://msdn.microsoft.com/library/windows/desktop/bb773727) podrobnosti.  
  
 
  

## <a name="quotespaces"></a> ATLPath::QuoteSpaces  
 Tato funkce je přetížené obálku pro [PathQuoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773739).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline void QuoteSpaces(char* pszPath);  
inline void QuoteSpaces(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [PathQuoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773739) podrobnosti.  
  
 
  

## <a name="relativepathto"></a> ATLPath::RelativePathTo
 Tato funkce je přetížené obálku pro [PathRelativePathTo](http://msdn.microsoft.com/library/windows/desktop/bb773740).  
  
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
 V tématu [PathRelativePathTo](http://msdn.microsoft.com/library/windows/desktop/bb773740) podrobnosti.  
  
 
  

## <a name="removeargs"></a> ATLPath::RemoveArgs  
 Tato funkce je přetížené obálku pro [PathRemoveArgs](http://msdn.microsoft.com/library/windows/desktop/bb773742).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline void RemoveArgs(char* pszPath);  
inline void RemoveArgs(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [PathRemoveArgs](http://msdn.microsoft.com/library/windows/desktop/bb773742) podrobnosti.  
  
 
  

## <a name="removebackslash"></a> ATLPath::RemoveBackslash
 Tato funkce je přetížené obálku pro [PathRemoveBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773743).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline char* RemoveBackslash(char* pszPath);  
inline wchar_t* RemoveBackslash(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [PathRemoveBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773743) podrobnosti.  
  
 
  

## <a name="removeblanks"></a> ATLPath::RemoveBlanks
 Tato funkce je přetížené obálku pro [PathRemoveBlanks](http://msdn.microsoft.com/library/windows/desktop/bb773745).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline void RemoveBlanks(char* pszPath);  
inline void RemoveBlanks(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [PathRemoveBlanks](http://msdn.microsoft.com/library/windows/desktop/bb773745) podrobnosti.  
  
 
  

## <a name="removeextension"></a> ATLPath::RemoveExtension
 Tato funkce je přetížené obálku pro [PathRemoveExtension](http://msdn.microsoft.com/library/windows/desktop/bb773746).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline void RemoveExtension(char* pszPath);  
inline void RemoveExtension(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [PathRemoveExtension](http://msdn.microsoft.com/library/windows/desktop/bb773746) podrobnosti.  
  
 
  

## <a name="removefilespec"></a> ATLPath::RemoveFileSpec
 Tato funkce je přetížené obálku pro [PathRemoveFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773748).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline BOOL RemoveFileSpec(char* pszPath);  
inline BOOL RemoveFileSpec(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [PathRemoveFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773748) podrobnosti.  
  
 
  

## <a name="renameextension"></a> ATLPath::RenameExtension
 Tato funkce je přetížené obálku pro [PathRenameExtension](http://msdn.microsoft.com/library/windows/desktop/bb773749).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline BOOL RenameExtension(char* pszPath, const char* pszExt);  
inline BOOL RenameExtension(wchar_t* pszPath, const wchar_t* pszExt);  
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [PathRenameExtension](http://msdn.microsoft.com/library/windows/desktop/bb773749) podrobnosti.  
  
 
  

## <a name="skiproot"></a> ATLPath::SkipRoot
 Tato funkce je přetížené obálku pro [PathSkipRoot](http://msdn.microsoft.com/library/windows/desktop/bb773754).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline char* SkipRoot(const char* pszPath);  
inline wchar_t* SkipRoot(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [PathSkipRoot](http://msdn.microsoft.com/library/windows/desktop/bb773754) podrobnosti.  
  
 
  

## <a name="strippath"></a> ATLPath::StripPath
 Tato funkce je přetížené obálku pro [PathStripPath](http://msdn.microsoft.com/library/windows/desktop/bb773756).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline void StripPath(char* pszPath);  
inline void StripPath(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [PathStripPath](http://msdn.microsoft.com/library/windows/desktop/bb773756) podrobnosti.  
  
 
  


## <a name="striptoroot"></a> ATLPath::StripToRoot
 Tato funkce je přetížené obálku pro [PathStripToRoot](http://msdn.microsoft.com/library/windows/desktop/bb773757).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline BOOL StripToRoot(char* pszPath);  
inline BOOL StripToRoot(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [PathStripToRoot](http://msdn.microsoft.com/library/windows/desktop/bb773757) podrobnosti.  
  
 
  

## <a name="unquotespaces"></a> ATLPath::UnquoteSpaces
 Tato funkce je přetížené obálku pro [PathUnquoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773763).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline void UnquoteSpaces(char* pszPath);  
inline void UnquoteSpaces(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [PathUnquoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773763) podrobnosti.  
  
 
  
 
