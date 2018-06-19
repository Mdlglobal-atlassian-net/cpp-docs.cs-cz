---
title: Třída CPathT | Microsoft Docs
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
ms.openlocfilehash: 37f669ddc7912f45222d52f10311ff70110e170f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366377"
---
# <a name="cpatht-class"></a>CPathT – třída
Tato třída reprezentuje cestu.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <typename StringType>
class CPathT
```  
  
#### <a name="parameters"></a>Parametry  
 `StringType`  
 Třídy ATL a MFC řetězec použité pro cestu (viz [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)).  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|[CPathT::PCXSTR](#pcxstr)|Konstantní řetězec typu.|  
|[CPathT::PXSTR](#pxstr)|Typ string.|  
|[CPathT::XCHAR](#xchar)|Typy znaků.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CPathT::CPathT](#cpatht)|Konstruktor pro cestu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CPathT::AddBackslash](#addbackslash)|Voláním této metody lze přidat do konce řetězce k vytvoření správnou syntaxi pro cestu k zpětné lomítko.|  
|[CPathT::AddExtension](#addextension)|Voláním této metody lze přidat příponu souboru do cesty.|  
|[CPathT::Append](#append)|Volejte tuto metodu za účelem připojení k aktuální cestě řetězec.|  
|[CPathT::BuildRoot](#buildroot)|Volejte tuto metodu za účelem vytvoření kořenovou cestu z mnoha dané jednotce.|  
|[CPathT::Canonicalize](#canonicalize)|Voláním této metody lze převést cestu na kanonický tvar.|  
|[CPathT::Combine](#combine)|Volejte tuto metodu za účelem řetězení řetězec představující název adresáře a řetězec představující název cesty souboru do jedné cesty.|  
|[CPathT::CommonPrefix](#commonprefix)|Volejte tuto metodu za účelem určení, zda zadaná cesta sdílí společné předponu s aktuální cestě.|  
|[CPathT::CompactPath](#compactpath)|Volejte tuto metodu za účelem zkrácení cestu k souboru nevejde se do dané pixelů šířka nahrazením komponenty cesty se třemi tečkami.|  
|[CPathT::CompactPathEx](#compactpathex)|Volejte tuto metodu za účelem zkrácení cestu k souboru, aby vyhovovaly limitu zadaný počet znaků nahrazením komponenty cesty se třemi tečkami.|  
|[CPathT::FileExists](#fileexists)|Voláním této metody zkontrolujte, zda existuje soubor v tento název cesty.|  
|[CPathT::FindExtension](#findextension)|Voláním této metody lze najít pozici přípona souboru v cestě.|  
|[CPathT::FindFileName](#findfilename)|Voláním této metody lze najít pozici názvu souboru v cestě.|  
|[CPathT::GetDriveNumber](#getdrivenumber)|Volejte tuto metodu Hledat v cestě pro písmeno jednotky v rozsahu od 'A' do 'Z' a vrátíte se příslušné číslo jednotky.|  
|[CPathT::GetExtension](#getextension)|Volejte tuto metodu za účelem získání příponu souboru z cesty.|  
|[CPathT::IsDirectory](#isdirectory)|Voláním této metody zkontrolujte, zda je cesta platný adresář.|  
|[CPathT::IsFileSpec](#isfilespec)|Volat tuto metodu za účelem Hledat v cestě pro znaky omezující cestu (například ':' nebo '\\'). Pokud neexistují žádné cesty omezující znaky přítomen, cesta se považuje za cestu k souboru specifikace.|  
|[CPathT::IsPrefix](#isprefix)|Voláním této metody lze zjistit, zda cesta obsahuje platnou předponu typu předaná `pszPrefix`.|  
|[CPathT::IsRelative](#isrelative)|Volejte tuto metodu za účelem určení, zda je relativní cesta.|  
|[CPathT::IsRoot](#isroot)|Volejte tuto metodu za účelem určení, zda je cesta kořenové adresáře.|  
|[CPathT::IsSameRoot](#issameroot)|Voláním této metody lze určit, zda má jiné cesty běžné součást kořenové s aktuální cestě.|  
|[CPathT::IsUNC](#isunc)|Voláním této metody lze určit, zda je cesta platná cesta UNC (universal naming convention) k serveru a sdílet.|  
|[CPathT::IsUNCServer](#isuncserver)|Voláním této metody lze určit, zda je cesta platná cesta UNC (universal naming convention) k pouze server.|  
|[CPathT::IsUNCServerShare](#isuncservershare)|Voláním této metody lze určit, zda je cesta platnou cestu sdílené složky UNC (universal naming convention), \\ \  *server*\ *sdílet*.|  
|[CPathT::MakePretty](#makepretty)|Voláním této metody lze převést cestu na cestu poskytnout jednotný vzhled všech malá písmena.|  
|[CPathT::MatchSpec](#matchspec)|Volejte tuto metodu za účelem Hledat v cestě pro řetězec obsahující shodný typ zástupný znak.|  
|[CPathT::QuoteSpaces](#quotespaces)|Volejte tuto metodu za účelem vložte cestu do uvozovek, pokud obsahuje žádné mezery.|  
|[CPathT::RelativePathTo](#relativepathto)|Voláním této metody lze vytvořit na relativní cestu z jeden soubor nebo složku.|  
|[CPathT::RemoveArgs](#removeargs)|Volejte tuto metodu za účelem odebrání žádných argumentů příkazového řádku z cesty.|  
|[CPathT::RemoveBackslash](#removebackslash)|Volejte tuto metodu za účelem odebrání cesta koncové lomítko.|  
|[CPathT::RemoveBlanks](#removeblanks)|Voláním této metody lze odebrat všechny úvodní a koncové mezery z cesty.|  
|[CPathT::RemoveExtension](#removeextension)|Volejte tuto metodu za účelem odstranění příponu souboru z cesty, pokud existuje.|  
|[CPathT::RemoveFileSpec](#removefilespec)|Volejte tuto metodu za účelem odstranění koncové název souboru a jeho zpětné lomítko z cesty, pokud je má.|  
|[CPathT::RenameExtension](#renameextension)|Voláním této metody lze nahradit příponu názvu souboru v cestě k nové rozšíření. Pokud název souboru neobsahuje rozšíření, rozšíření bude připojen na konec řetězec.|  
|[CPathT::SkipRoot](#skiproot)|Voláním této metody lze analyzovat cestu, písmeno jednotky nebo části cesty UNC sdílená složka serveru nebo je ignorována.|  
|[CPathT::StripPath](#strippath)|Voláním této metody lze odebrat část adresy obsahující cestu plně kvalifikovanou cestu a název souboru.|  
|[CPathT::StripToRoot](#striptoroot)|Voláním této metody lze odebrat všechny části cesty s výjimkou kořenové informace.|  
|[CPathT::UnquoteSpaces](#unquotespaces)|Volejte tuto metodu za účelem odebrání začátek a konec cesty uvozovky.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CPathT::operator const StringType &](#operator_const_stringtype_amp)|Tento operátor umožňuje objekt, který má být zpracovány jako řetězec.|  
|[CPathT::operator CPathT::PCXSTR](#operator_cpatht__pcxstr)|Tento operátor umožňuje objekt, který má být zpracovány jako řetězec.|  
|[CPathT::operator StringType &](#operator_stringtype)|Tento operátor umožňuje objekt, který má být zpracovány jako řetězec.|  
|[CPathT::operator +=](#operator_add_eq)|Tento operátor přidá řetězec do cesty.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CPathT::m_strPath](#m_strpath)|Cesta.|  
  
## <a name="remarks"></a>Poznámky  
 `CPath`, `CPathA`, a `CPathW` jsou instancemi `CPathT` definovány takto:  
  
 `typedef CPathT< CString > CPath;`  
  
 `typedef CPathT< CStringA > CPathA;`  
  
 `typedef CPathT< CStringW > CPathW;`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlpath.h  
  
##  <a name="addbackslash"></a>  CPathT::AddBackslash  
 Voláním této metody lze přidat do konce řetězce k vytvoření správnou syntaxi pro cestu k zpětné lomítko. Pokud cesta již koncové zpětné lomítko, bude přidán neobsahuje zpětné lomítko.  
  
```
void AddBackslash();
```  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [PathAddBackSlash](http://msdn.microsoft.com/library/windows/desktop/bb773561).  
  
##  <a name="addextension"></a>  CPathT::AddExtension  
 Voláním této metody lze přidat příponu souboru do cesty.  
  
```
BOOL AddExtension(PCXSTR pszExtension);
```  
  
### <a name="parameters"></a>Parametry  
 `pszExtension`  
 Přípona souboru, který chcete přidat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, v případě úspěchu FALSE při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [PathAddExtension](http://msdn.microsoft.com/library/windows/desktop/bb773563).  
  
##  <a name="append"></a>  CPathT::Append  
 Volejte tuto metodu za účelem připojení k aktuální cestě řetězec.  
  
```
BOOL Append(PCXSTR pszMore);
```  
  
### <a name="parameters"></a>Parametry  
 `pszMore`  
 Řetězec, který se má připojit.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, v případě úspěchu FALSE při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [PathAppend](http://msdn.microsoft.com/library/windows/desktop/bb773565).  
  
##  <a name="buildroot"></a>  CPathT::BuildRoot  
 Volejte tuto metodu za účelem vytvoření kořenovou cestu z mnoha dané jednotce.  
  
```
void BuildRoot(int iDrive);
```  
  
### <a name="parameters"></a>Parametry  
 *iDrive*  
 Číslo jednotku (A: je 0, 1 je B: a tak dále).  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [PathBuildRoot](http://msdn.microsoft.com/library/windows/desktop/bb773567).  
  
##  <a name="canonicalize"></a>  CPathT::Canonicalize  
 Voláním této metody lze převést cestu na kanonický tvar.  
  
```
void Canonicalize();
```  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [PathCanonicalize](http://msdn.microsoft.com/library/windows/desktop/bb773569).  
  
##  <a name="combine"></a>  CPathT::Combine  
 Volejte tuto metodu za účelem řetězení řetězec představující název adresáře a řetězec představující název cesty souboru do jedné cesty.  
  
```
void Combine(PCXSTR pszDir, PCXSTR  pszFile);
```  
  
### <a name="parameters"></a>Parametry  
 `pszDir`  
 Cesta k adresáři.  
  
 *pszFile*  
 Cesta k souboru.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [PathCombine](http://msdn.microsoft.com/library/windows/desktop/bb773571).  
  
##  <a name="commonprefix"></a>  CPathT::CommonPrefix  
 Volejte tuto metodu za účelem určení, zda zadaná cesta sdílí společné předponu s aktuální cestě.  
  
```
CPathT<StringType> CommonPrefix(PCXSTR pszOther);
```  
  
### <a name="parameters"></a>Parametry  
 `pszOther`  
 Cesta k porovnání s aktuálním klíčem.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí běžné předponu.  
  
### <a name="remarks"></a>Poznámky  
 Předpona je jedním z těchto typů: "C:\\\\",".","...",".. \\\\". Další informace najdete v tématu [PathCommonPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773574).  
  
##  <a name="compactpath"></a>  CPathT::CompactPath  
 Volejte tuto metodu za účelem zkrácení cestu k souboru nevejde se do dané pixelů šířka nahrazením komponenty cesty se třemi tečkami.  
  
```
BOOL CompactPath(HDC hDC, UINT nWidth);
```  
  
### <a name="parameters"></a>Parametry  
 `hDC`  
 Kontext zařízení používá pro metriky písma.  
  
 `nWidth`  
 Šířku v pixelech, kterou řetězec se vynutí, aby se vešla do.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, v případě úspěchu FALSE při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [PathCompactPath](http://msdn.microsoft.com/library/windows/desktop/bb773575).  
  
##  <a name="compactpathex"></a>  CPathT::CompactPathEx  
 Volejte tuto metodu za účelem zkrácení cestu k souboru, aby vyhovovaly limitu zadaný počet znaků nahrazením komponenty cesty se třemi tečkami.  
  
```
BOOL CompactPathEx(UINT nMaxChars, DWORD dwFlags = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `nMaxChars`  
 Maximální počet znaků, který má být součástí nového řetězce, včetně ukončující znak hodnoty NULL.  
  
 `dwFlags`  
 Vyhrazena.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, v případě úspěchu FALSE při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [PathCompactPathEx](http://msdn.microsoft.com/library/windows/desktop/bb773578).  
  
##  <a name="cpatht"></a>  CPathT::CPathT  
 Konstruktor  
  
```
CPathT(PCXSTR pszPath);
CPathT(const CPathT<StringType>& path);
CPathT() throw();
```  
  
### <a name="parameters"></a>Parametry  
 *pszPath*  
 Ukazatel na řetězec cesty.  
  
 *Cesta*  
 Řetězec cesty.  
  
##  <a name="fileexists"></a>  CPathT::FileExists  
 Voláním této metody zkontrolujte, zda existuje soubor v tento název cesty.  
  
```
BOOL FileExists() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, pokud soubor existuje, FALSE jinak.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [PathFileExists](http://msdn.microsoft.com/library/windows/desktop/bb773584).  
  
##  <a name="findextension"></a>  CPathT::FindExtension  
 Voláním této metody lze najít pozici přípona souboru v cestě.  
  
```
int FindExtension() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí pozici "." předcházející rozšíření. Pokud se nenajde žádný rozšíření, vrátí hodnotu -1.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [PathFindExtension](http://msdn.microsoft.com/library/windows/desktop/bb773587).  
  
##  <a name="findfilename"></a>  CPathT::FindFileName  
 Voláním této metody lze najít pozici názvu souboru v cestě.  
  
```
int FindFileName() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí pozici název souboru. Pokud se nenajde žádný název souboru, vrátí hodnotu -1.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589).  
  
##  <a name="getdrivenumber"></a>  CPathT::GetDriveNumber  
 Volejte tuto metodu Hledat v cestě pro písmeno jednotky v rozsahu od 'A' do 'Z' a vrátíte se příslušné číslo jednotky.  
  
```
int GetDriveNumber() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací číslo jednotky jako celé číslo od 0 do 25 (až "Z" odpovídající "A"), pokud cesta obsahuje jinak písmeno jednotky nebo -1.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [PathGetDriveNumber](http://msdn.microsoft.com/library/windows/desktop/bb773612).  
  
##  <a name="getextension"></a>  CPathT::GetExtension  
 Volejte tuto metodu za účelem získání příponu souboru z cesty.  
  
```
StringType GetExtension() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí příponu souboru.  
  
##  <a name="isdirectory"></a>  CPathT::IsDirectory  
 Voláním této metody zkontrolujte, zda je cesta platný adresář.  
  
```
BOOL IsDirectory() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací hodnotu nula (16), pokud je cesta k adresáři, `FALSE` jinak.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [PathIsDirectory](http://msdn.microsoft.com/library/windows/desktop/bb773621).  
  
##  <a name="isfilespec"></a>  CPathT::IsFileSpec  
 Volat tuto metodu za účelem Hledat v cestě pro znaky omezující cestu (například ':' nebo '\\'). Pokud neexistují žádné cesty omezující znaky přítomen, cesta se považuje za cestu k souboru specifikace.  
  
```
BOOL IsFileSpec() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací hodnotu TRUE, pokud nejsou žádné omezující cesta znaky v cestě, nebo hodnotu NEPRAVDA, pokud cesta omezující znaky.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [PathIsFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773627).  
  
##  <a name="isprefix"></a>  CPathT::IsPrefix  
 Voláním této metody lze zjistit, zda cesta obsahuje platnou předponu typu předaná `pszPrefix`.  
  
```
BOOL IsPrefix(PCXSTR pszPrefix) const;
```  
  
### <a name="parameters"></a>Parametry  
 `pszPrefix`  
 Předpona, pro které chcete vyhledat. Předpona je jedním z těchto typů: "C:\\\\",".","...",".. \\\\".  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, pokud cesta obsahuje jinak předpony, nebo hodnotu FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [PathIsPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773650).  
  
##  <a name="isrelative"></a>  CPathT::IsRelative  
 Volejte tuto metodu za účelem určení, zda je relativní cesta.  
  
```
BOOL IsRelative() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, pokud cesta relativní, nebo hodnotu NEPRAVDA, pokud je absolutní.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [PathIsRelative](http://msdn.microsoft.com/library/windows/desktop/bb773660).  
  
##  <a name="isroot"></a>  CPathT::IsRoot  
 Volejte tuto metodu za účelem určení, zda je cesta kořenové adresáře.  
  
```
BOOL IsRoot() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud cesta je jinak kořenové nebo hodnotu NEPRAVDA, vrátí hodnotu TRUE.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [PathIsRoot](http://msdn.microsoft.com/library/windows/desktop/bb773674).  
  
##  <a name="issameroot"></a>  CPathT::IsSameRoot  
 Voláním této metody lze určit, zda má jiné cesty běžné součást kořenové s aktuální cestě.  
  
```
BOOL IsSameRoot(PCXSTR pszOther) const;
```  
  
### <a name="parameters"></a>Parametry  
 `pszOther`  
 Jiné cesty.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, pokud mají oba řetězce stejné kořenové komponenty, nebo hodnotu NEPRAVDA jinak.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [PathIsSameRoot](http://msdn.microsoft.com/library/windows/desktop/bb773687).  
  
##  <a name="isunc"></a>  CPathT::IsUNC  
 Voláním této metody lze určit, zda je cesta platná cesta UNC (universal naming convention) k serveru a sdílet.  
  
```
BOOL IsUNC() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, pokud je cesta platná cesta UNC, nebo hodnotu FALSE jinak.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [PathIsUNC](http://msdn.microsoft.com/library/windows/desktop/bb773712).  
  
##  <a name="isuncserver"></a>  CPathT::IsUNCServer  
 Voláním této metody lze určit, zda je cesta platná cesta UNC (universal naming convention) k pouze server.  
  
```
BOOL IsUNCServer() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, pokud řetězec je jinak platná cesta UNC pro server pouze (žádný název sdílené složky) nebo FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [PathIsUNCServer](http://msdn.microsoft.com/library/windows/desktop/bb773722).  
  
##  <a name="isuncservershare"></a>  CPathT::IsUNCServerShare  
 Voláním této metody lze určit, zda je cesta platnou cestu sdílené složky UNC (universal naming convention), \\ \  *server*\ *sdílet*.  
  
```
BOOL IsUNCServerShare() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, pokud je cesta ve formátu \\ \  *server*\ *sdílet*, nebo hodnotu NEPRAVDA, jinak hodnota.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [PathIsUNCServerShare](http://msdn.microsoft.com/library/windows/desktop/bb773723).  
  
##  <a name="m_strpath"></a>  CPathT::m_strPath  
 Cesta.  
  
```
StringType m_strPath;
```  
  
### <a name="remarks"></a>Poznámky  
 `StringType` je parametr šablony k `CPathT`.  
  
##  <a name="makepretty"></a>  CPathT::MakePretty  
 Voláním této metody lze převést cestu na cestu poskytnout jednotný vzhled všech malá písmena.  
  
```
BOOL MakePretty();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 V opačném případě vrátí hodnotu TRUE, pokud byl převeden cestu, nebo hodnotu FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [PathMakePretty](http://msdn.microsoft.com/library/windows/desktop/bb773725).  
  
##  <a name="matchspec"></a>  CPathT::MatchSpec  
 Volejte tuto metodu za účelem Hledat v cestě pro řetězec obsahující shodný typ zástupný znak.  
  
```
BOOL MatchSpec(PCXSTR pszSpec) const;
```  
  
### <a name="parameters"></a>Parametry  
 `pszSpec`  
 Ukazatel na řetězce ukončené hodnotou null se typ souboru, pro které chcete vyhledat. Chcete-li otestovat, zda je soubor v aktuální cestě souboru DOC, třeba `pszSpec` musí být nastavena na "* .doc".  
  
### <a name="return-value"></a>Návratová hodnota  
 V opačném případě vrátí hodnotu TRUE, pokud řetězec odpovídá nebo FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [PathMatchSpec](http://msdn.microsoft.com/library/windows/desktop/bb773727).  
  
##  <a name="operator_add_eq"></a>  CPathT::operator +=  
 Tento operátor přidá řetězec do cesty.  
  
```
CPathT<StringType>& operator+=(PCXSTR pszMore);
```  
  
### <a name="parameters"></a>Parametry  
 `pszMore`  
 Řetězec, který se má připojit.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací aktualizované cestu.  
  
##  <a name="operator_const_stringtype_amp"></a>  CPathT::operator const StringType &amp;  
 Tento operátor umožňuje objekt, který má být zpracovány jako řetězec.  
  
```
 operatorconst StringType&() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací řetězec představující aktuální cestě spravuje tento objekt.  
  
##  <a name="operator_cpatht__pcxstr"></a>  CPathT::operator CPathT::PCXSTR  
 Tento operátor umožňuje objekt, který má být zpracovány jako řetězec.  
  
```
 operatorPCXSTR() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací řetězec představující aktuální cestě spravuje tento objekt.  
  
##  <a name="operator_stringtype__amp"></a>  CPathT::operator StringType &amp;  
 Tento operátor umožňuje objekt, který má být zpracovány jako řetězec.  
  
```
 operatorStringType&() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací řetězec představující aktuální cestě spravuje tento objekt.  
  
##  <a name="pcxstr"></a>  CPathT::PCXSTR  
 Konstantní řetězec typu.  
  
```
typedef StringType::PCXSTR PCXSTR;
```  
  
### <a name="remarks"></a>Poznámky  
 `StringType` je parametr šablony k `CPathT`.  
  
##  <a name="pxstr"></a>  CPathT::PXSTR  
 Typ string.  
  
```
typedef StringType::PXSTR PXSTR;
```  
  
### <a name="remarks"></a>Poznámky  
 `StringType` je parametr šablony k `CPathT`.  
  
##  <a name="quotespaces"></a>  CPathT::QuoteSpaces  
 Volejte tuto metodu za účelem vložte cestu do uvozovek, pokud obsahuje žádné mezery.  
  
```
void QuoteSpaces();
```  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [PathQuoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773739).  
  
##  <a name="relativepathto"></a>  CPathT::RelativePathTo  
 Voláním této metody lze vytvořit na relativní cestu z jeden soubor nebo složku.  
  
```
BOOL RelativePathTo(
    PCXSTR pszFrom,
    DWORD dwAttrFrom,
    PCXSTR pszTo,
    DWORD dwAttrTo);
```  
  
### <a name="parameters"></a>Parametry  
 `pszFrom`  
 Začátek relativní cesty.  
  
 *dwAttrFrom*  
 Atributy souboru `pszFrom`. Pokud tato hodnota obsahuje FILE_ATTRIBUTE_DIRECTORY, `pszFrom` je předpokládané být adresář, jinak hodnota `pszFrom` se předpokládá, že se soubor.  
  
 `pszTo`  
 Koncový bod relativní cesty.  
  
 *dwAttrTo*  
 Atributy souboru `pszTo`. Pokud tato hodnota obsahuje FILE_ATTRIBUTE_DIRECTORY, `pszTo` je předpokládané být adresář, jinak hodnota `pszTo` se předpokládá, že se soubor.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, v případě úspěchu FALSE při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [PathRelativePathTo](http://msdn.microsoft.com/library/windows/desktop/bb773740).  
  
##  <a name="removeargs"></a>  CPathT::RemoveArgs  
 Volejte tuto metodu za účelem odebrání žádných argumentů příkazového řádku z cesty.  
  
```
void RemoveArgs();
```  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [PathRemoveArgs](http://msdn.microsoft.com/library/windows/desktop/bb773742).  
  
##  <a name="removebackslash"></a>  CPathT::RemoveBackslash  
 Volejte tuto metodu za účelem odebrání cesta koncové lomítko.  
  
```
void RemoveBackslash();
```  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [PathRemoveBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773743).  
  
##  <a name="removeblanks"></a>  CPathT::RemoveBlanks  
 Voláním této metody lze odebrat všechny úvodní a koncové mezery z cesty.  
  
```
void RemoveBlanks();
```  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [PathRemoveBlanks](http://msdn.microsoft.com/library/windows/desktop/bb773745).  
  
##  <a name="removeextension"></a>  CPathT::RemoveExtension  
 Volejte tuto metodu za účelem odstranění příponu souboru z cesty, pokud existuje.  
  
```
void RemoveExtension();
```  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [PathRemoveExtension](http://msdn.microsoft.com/library/windows/desktop/bb773746).  
  
##  <a name="removefilespec"></a>  CPathT::RemoveFileSpec  
 Volejte tuto metodu za účelem odstranění koncové název souboru a jeho zpětné lomítko z cesty, pokud je má.  
  
```
BOOL RemoveFileSpec();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, v případě úspěchu FALSE při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [PathRemoveFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773748).  
  
##  <a name="renameextension"></a>  CPathT::RenameExtension  
 Voláním této metody lze nahradit příponu názvu souboru v cestě k nové rozšíření. Pokud název souboru neobsahuje rozšíření, rozšíření bude připojen na konec cesty.  
  
```
BOOL RenameExtension(PCXSTR pszExtension);
```  
  
### <a name="parameters"></a>Parametry  
 `pszExtension`  
 Novou příponu názvu souboru, před sebou "." znak.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, v případě úspěchu FALSE při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [PathRenameExtension](http://msdn.microsoft.com/library/windows/desktop/bb773749).  
  
##  <a name="skiproot"></a>  CPathT::SkipRoot  
 Voláním této metody lze analyzovat cestu, ignoruje písmeno jednotky nebo části cesty UNC (universal naming convention) nebo sdílené složky serveru.  
  
```
int SkipRoot() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí pozici začátku na dílčí cestu, která následuje kořenu (písmeno jednotky nebo serveru nebo sdílené složky UNC).  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [PathSkipRoot](http://msdn.microsoft.com/library/windows/desktop/bb773754).  
  
##  <a name="strippath"></a>  CPathT::StripPath  
 Voláním této metody lze odebrat část adresy obsahující cestu plně kvalifikovanou cestu a název souboru.  
  
```
void StripPath();
```  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [PathStripPath](http://msdn.microsoft.com/library/windows/desktop/bb773756).  
  
##  <a name="striptoroot"></a>  CPathT::StripToRoot  
 Voláním této metody lze odebrat všechny části cesty s výjimkou kořenové informace.  
  
```
BOOL StripToRoot();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, pokud platné písmeno jednotky byl nalezen v cestě, nebo hodnotu NEPRAVDA jinak.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [PathStripToRoot](http://msdn.microsoft.com/library/windows/desktop/bb773757).  
  
##  <a name="unquotespaces"></a>  CPathT::UnquoteSpaces  
 Volejte tuto metodu za účelem odebrání začátek a konec cesty uvozovky.  
  
```
void UnquoteSpaces();
```  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [PathUnquoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773763).  
  
##  <a name="xchar"></a>  CPathT::XCHAR  
 Typy znaků.  
  
```
typedef StringType::XCHAR XCHAR;
```  
  
### <a name="remarks"></a>Poznámky  
 `StringType` je parametr šablony k `CPathT`.  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../atl/reference/atl-classes.md)   
 [CStringT – třída](../../atl-mfc-shared/reference/cstringt-class.md)