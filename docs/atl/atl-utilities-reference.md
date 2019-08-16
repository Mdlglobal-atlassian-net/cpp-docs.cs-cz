---
title: Referenční dokumentace k nástrojům ATL
ms.date: 11/04/2016
ms.assetid: dd8a2888-34f4-461e-9bf4-834218f9b95b
ms.openlocfilehash: 6c1481929f832e6f810ce46773f328f278b503fa
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491704"
---
# <a name="atl-utilities-reference"></a>Referenční dokumentace k nástrojům ATL

ATL poskytuje kód pro manipulaci s cestami a adresami URL ve formě [CPathT](../atl/reference/cpatht-class.md) a [kudrlinkou](../atl/reference/curl-class.md). Ve svých aplikacích lze použít fond vláken [CThreadPool](../atl/reference/cthreadpool-class.md). Tento kód najdete v atlpath. h a atlutil. h.

### <a name="classes"></a>Třídy

|||
|-|-|
|[CPathT – třída](../atl/reference/cpatht-class.md)|Tato třída reprezentuje cestu.|
|[CDebugReportHook – třída](../atl/reference/cdebugreporthook-class.md)|Tato třída slouží k posílání ladicích sestav do pojmenovaného kanálu.|
|[CNonStatelessWorker – třída](../atl/reference/cnonstatelessworker-class.md)|Přijímá požadavky z fondu vláken a předává je do objektu pracovního procesu, který je vytvořen a zničen na každém požadavku.|
|[CNoWorkerThread – třída](../atl/reference/cnoworkerthread-class.md)|Tuto třídu použijte jako argument pro `MonitorClass` parametr šablony pro ukládání tříd do mezipaměti, pokud chcete zakázat údržbu dynamické mezipaměti.|
|[CThreadPool – třída](../atl/reference/cthreadpool-class.md)|Tato třída poskytuje fond pracovních vláken, která zpracovávají frontu pracovních položek.|
|[CUrl – třída](../atl/reference/curl-class.md)|Tato třída představuje adresu URL. Umožňuje manipulaci s každým prvkem adresy URL nezávisle na tom, zda analyzuje existující řetězec adresy URL nebo vytváří řetězec od začátku.|
|[CWorkerThread – třída](../atl/reference/cworkerthread-class.md)|Tato třída vytvoří pracovní vlákno nebo použije existující, počká na jeden nebo více popisovačů objektů jádra a spustí zadanou klientskou funkci, pokud je jeden z popisovačů signalizována.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[CPath](../atl/reference/atl-typedefs.md#cpath)|Specializace [CPathT](../atl/reference/cpatht-class.md) s využitím `CString`.|
|[CPathA](../atl/reference/atl-typedefs.md#cpatha)|Specializace [CPathT](../atl/reference/cpatht-class.md) s využitím `CStringA`.|
|[CPathW](../atl/reference/atl-typedefs.md#cpathw)|Specializace [CPathT](../atl/reference/cpatht-class.md) s využitím `CStringW`.|
|[ATL_URL_PORT](../atl/reference/atl-typedefs.md#atl_url_port)|Typ použitý oblým [](../atl/reference/curl-class.md) pro zadání čísla portu.|

### <a name="enums"></a>Výčty

|||
|-|-|
|[ATL_URL_SCHEME](../atl/reference/atl-url-scheme-enum.md)|Členové tohoto výčtu poskytují konstanty pro schémata srozumitelná pomocí metody [kudrlinkou](../atl/reference/curl-class.md).|

### <a name="functions"></a>Funkce

|||
|-|-|
|[AtlCanonicalizeUrl](../atl/reference/atl-http-utility-functions.md#atlcanonicalizeurl)|Voláním této funkce převedete adresu URL na kanonický tvar, přičemž problematické znaky a mezery se převedou na řídicí sekvence.|
|[AtlCombineUrl](../atl/reference/atl-http-utility-functions.md#atlcombineurl)|Voláním této funkce zkombinujete základní a relativní adresu URL do jedné kanonické adresy URL.|
|[AtlEscapeUrl](../atl/reference/atl-http-utility-functions.md#atlescapeurl)|Voláním této funkce převedete všechny problematické znaky na řídicí sekvence.|
|[AtlGetDefaultUrlPort](../atl/reference/atl-http-utility-functions.md#atlgetdefaulturlport)|Voláním této funkce získáte výchozí číslo portu přidružené ke konkrétnímu protokolu sítě Internet nebo schématu.|
|[AtlHexValue](../atl/reference/atl-text-encoding-functions.md#atlhexvalue)|Voláním této funkce získáte číselnou hodnotu šestnáctkové číslice.|
|[AtlIsUnsafeUrlChar](../atl/reference/atl-http-utility-functions.md#atlisunsafeurlchar)|Voláním této funkce zjistíte, zda lze znak bezpečně použít v adrese URL.|
|[AtlUnescapeUrl](../atl/reference/atl-http-utility-functions.md#atlunescapeurl)|Voláním této funkce převedete řídicí znaky zpět na jejich původní hodnoty.|
|[SystemTimeToHttpDate](../atl/reference/atl-http-utility-functions.md#systemtimetohttpdate)|Voláním této funkce převedete systémový čas na řetězec ve formátu vhodném pro použití v hlavičkách protokolu HTTP.|

|[ATLPath::AddBackslash](../atl/reference/atl-path-functions.md#addbackslash)| Tato funkce je přetížená obálka pro [PathAddBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddbackslasha
). | |[ ATLPath::AddExtension](../atl/reference/atl-path-functions.md#addextension)| Tato funkce je přetížená obálka pro [PathAddExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw). | |[ ATLPath::Append](../atl/reference/atl-path-functions.md#append)| Tato funkce je přetížená obálka pro [PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw). | |[ ATLPath::BuildRoot](../atl/reference/atl-path-functions.md#buildroot)| Tato funkce je přetížená obálka pro [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw). | |[ ATLPath::Canonicalize](../atl/reference/atl-path-functions.md#canonicalize)| Tato funkce je přetížená obálka pro [PathCanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew). | |[ ATLPath::Combine](../atl/reference/atl-path-functions.md#combine)| Tato funkce je přetížená obálka pro [PathCombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew). | |[ ATLPath::CommonPrefix](../atl/reference/atl-path-functions.md#commonprefix)| Tato funkce je přetížená obálka pro [PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw). | |[ ATLPath::CompactPath](../atl/reference/atl-path-functions.md#compactpath)| Tato funkce je přetížená obálka pro [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw). | |[ ATLPath::CompactPathEx](../atl/reference/atl-path-functions.md#compactpathex)| Tato funkce je přetížená obálka pro [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw). | |[ ATLPath::FileExists](../atl/reference/atl-path-functions.md#fileexists)| Tato funkce je přetížená obálka pro [PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw). | |[ ATLPath::FindExtension](../atl/reference/atl-path-functions.md#findextension)| Tato funkce je přetížená obálka pro [PathFindExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw). | |[ ATLPath::FindFileName](../atl/reference/atl-path-functions.md#findfilename)| Tato funkce je přetížená obálka pro [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew). | |[ ATLPath::GetDriveNumber](../atl/reference/atl-path-functions.md#getdrivenumber)| Tato funkce je přetížená obálka pro [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw). | |[ ATLPath::IsDirectory](../atl/reference/atl-path-functions.md#isdirectory)| Tato funkce je přetížená obálka pro [PathIsDirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw). | |[ ATLPath::IsFileSpec](../atl/reference/atl-path-functions.md#isfilespec)| Tato funkce je přetížená obálka pro [PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw). | |[ ATLPath::IsPrefix](../atl/reference/atl-path-functions.md#isprefix)| Tato funkce je přetížená obálka pro [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw). | |[ ATLPath::IsRelative](../atl/reference/atl-path-functions.md#isrelative)| Tato funkce je přetížená obálka pro [PathIsRelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew). | |[ ATLPath::IsRoot](../atl/reference/atl-path-functions.md#isroot)| Tato funkce je přetížená obálka pro [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw). | |[ ATLPath::IsSameRoot](../atl/reference/atl-path-functions.md#issameroot)| Tato funkce je přetížená obálka pro [PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw). | |[ ATLPath::IsUNC](../atl/reference/atl-path-functions.md#isunc)| Tato funkce je přetížená obálka pro [PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw). | |[ ATLPath::IsUNCServer](../atl/reference/atl-path-functions.md#isuncserver)| Tato funkce je přetížená obálka pro [PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw). | |[ ATLPath::IsUNCServerShare](../atl/reference/atl-path-functions.md#isuncservershare)| Tato funkce je přetížená obálka pro [PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew).| |[ATLPath::MakePretty](../atl/reference/atl-path-functions.md#makepretty)|This function is an overloaded wrapper for [PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw).| |[ATLPath::MatchSpec](../atl/reference/atl-path-functions.md#matchspec)|This function is an overloaded wrapper for [PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw).| |[ATLPath::QuoteSpaces](../atl/reference/atl-path-functions.md#quotespaces)|This function is an overloaded wrapper for [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw).| |[ATLPath::RelativePathTo](../atl/reference/atl-path-functions.md#relativepathto)|This function is an overloaded wrapper for [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow).| |[ATLPath::RemoveArgs](../atl/reference/atl-path-functions.md#removeargs)|This function is an overloaded wrapper for [PathRemoveArgs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw).| |[ATLPath::RemoveBackslash](../atl/reference/atl-path-functions.md#removebackslash)|This function is an overloaded wrapper for [PathRemoveBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw).| |[ATLPath::RemoveBlanks](../atl/reference/atl-path-functions.md#removeblanks)|This function is an overloaded wrapper for [PathRemoveBlanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw).| |[ATLPath::RemoveExtension](../atl/reference/atl-path-functions.md#removeextension)|This function is an overloaded wrapper for [PathRemoveExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw).| |[ATLPath::RemoveFileSpec](../atl/reference/atl-path-functions.md#removefilespec)|This function is an overloaded wrapper for [PathRemoveFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw).| |[ATLPath::RenameExtension](../atl/reference/atl-path-functions.md#renameextension)|This function is an overloaded wrapper for [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw).| |[ATLPath::SkipRoot](../atl/reference/atl-path-functions.md#skiproot)|This function is an overloaded wrapper for [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw).| |[ATLPath::StripPath](../atl/reference/atl-path-functions.md#strippath)|This function is an overloaded wrapper for [PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw).| |[ATLPath::StripToRoot](../atl/reference/atl-path-functions.md#striptoroot)|This function is an overloaded wrapper for [PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw).| |[ATLPath::UnquoteSpaces](../atl/reference/atl-path-functions.md#unquotespaces)|This function is an overloaded wrapper for [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw).|

## <a name="see-also"></a>Viz také:

[Charakteristiky](../atl/active-template-library-atl-concepts.md)<br/>
[Desktopové komponenty ATL objektů COM](../atl/atl-com-desktop-components.md)
