---
title: Referenční dokumentace k nástrojům ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: dd8a2888-34f4-461e-9bf4-834218f9b95b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9b802d8764dda321e2e313f793f4f2e4745dbcc7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="atl-utilities-reference"></a>Referenční dokumentace k nástrojům ATL
ATL obsahuje kód pro manipulaci s cesty a adresy URL ve formě [CPathT](../atl/reference/cpatht-class.md) a [CUrl](../atl/reference/curl-class.md). Fondu vláken, [CThreadPool](../atl/reference/cthreadpool-class.md), můžete použít ve svých aplikacích. Tento kód lze nalézt v atlpath.h a atlutil.h.  
  
### <a name="classes"></a>Třídy  
  
|||  
|-|-|  
|[CPathT – třída](../atl/reference/cpatht-class.md)|Tato třída reprezentuje cestu.|  
|[CDebugReportHook – třída](../atl/reference/cdebugreporthook-class.md)|Tato třída slouží k ladění sestavy poslat pojmenovaný kanál.|  
|[CNonStatelessWorker – třída](../atl/reference/cnonstatelessworker-class.md)|Přijímá požadavky od fondu vláken a předává je na objekt pracovního procesu, který je vytvořen a zničen v každé žádosti.|  
|[CNoWorkerThread – třída](../atl/reference/cnoworkerthread-class.md)|Tato třída slouží jako argument pro `MonitorClass` parametr šablony do mezipaměti tříd, pokud chcete zakázat dynamické mezipaměti údržby.|  
|[CThreadPool – třída](../atl/reference/cthreadpool-class.md)|Tato třída poskytuje fond pracovních vláken, které zpracovávají fronty pracovních položek.|  
|[CUrl – třída](../atl/reference/curl-class.md)|Tato třída představuje adresu URL. Umožňuje pracovat s každý prvek adresy URL nezávisle na ostatních, zda analýza stávající adresy URL řetězec nebo vytváření řetězec od začátku.|  
|[CWorkerThread – třída](../atl/reference/cworkerthread-class.md)|Tato třída vytvoří pracovní vlákno nebo používá existující, čeká na jeden nebo více objektů obslužných rutin jádra a provede funkci zadaného klienta, když se jeden z obslužné rutiny pro zpracování signalizace.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[CPath](../atl/reference/atl-typedefs.md#cpath)|Specializace z [CPathT](../atl/reference/cpatht-class.md) pomocí `CString`.|  
|[CPathA](../atl/reference/atl-typedefs.md#cpatha)|Specializace z [CPathT](../atl/reference/cpatht-class.md) pomocí `CStringA`.|  
|[CPathW](../atl/reference/atl-typedefs.md#cpathw)|Specializace z [CPathT](../atl/reference/cpatht-class.md) pomocí `CStringW`.|  
|[ATL_URL_PORT](../atl/reference/atl-typedefs.md#atl_url_port)|Typ používaný [CUrl](../atl/reference/curl-class.md) pro zadání číslo portu.|  
  
### <a name="enums"></a>Výčty  
  
|||  
|-|-|  
|[ATL_URL_SCHEME](../atl/reference/atl-url-scheme-enum.md)|Tento výčet členů zadejte konstanty pro schémata rozumí [CUrl](../atl/reference/curl-class.md).|  
  
### <a name="functions"></a>Funkce  
  
|||  
|-|-|  
|[AtlCanonicalizeUrl](../atl/reference/atl-http-utility-functions.md#atlcanonicalizeurl)|Voláním této funkce převedete adresu URL na kanonický tvar, přičemž problematické znaky a mezery se převedou na řídicí sekvence.|  
|[AtlCombineUrl](../atl/reference/atl-http-utility-functions.md#atlcombineurl)|Voláním této funkce zkombinujete základní a relativní adresu URL do jedné kanonické adresy URL.|  
|[AtlEscapeUrl](../atl/reference/atl-http-utility-functions.md#atlescapeurl)|Voláním této funkce převedete všechny problematické znaky na řídicí sekvence.|  
|[AtlGetDefaultUrlPort](../atl/reference/atl-http-utility-functions.md#atlgetdefaulturlport)|Volání této funkce se získat výchozí číslo portu přidružené k určité protokolu IP nebo schéma.|  
|[AtlHexValue](../atl/reference/atl-text-encoding-functions.md#atlhexvalue)|Voláním této funkce získáte číselnou hodnotu šestnáctkové číslice.|  
|[AtlIsUnsafeUrlChar](../atl/reference/atl-http-utility-functions.md#atlisunsafeurlchar)|Voláním této funkce zjistíte, zda lze znak bezpečně použít v adrese URL.|  
|[AtlUnescapeUrl](../atl/reference/atl-http-utility-functions.md#atlunescapeurl)|Voláním této funkce převedete řídicí znaky zpět na jejich původní hodnoty.|  
|[SystemTimeToHttpDate](../atl/reference/atl-http-utility-functions.md#systemtimetohttpdate)|Voláním této funkce převedete systémový čas na řetězec ve formátu vhodném pro použití v hlavičkách protokolu HTTP.|  

|[ATLPath::AddBackslash](../atl/reference/atl-path-functions.md#addbackslash)| Tato funkce je přetížené obálku pro [PathAddBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773561). |  
|[ATLPath::AddExtension](../atl/reference/atl-path-functions.md#addextension)| Tato funkce je přetížené obálku pro [PathAddExtension](http://msdn.microsoft.com/library/windows/desktop/bb773563). |  
|[ATLPath::Append](../atl/reference/atl-path-functions.md#append)| Tato funkce je přetížené obálku pro [PathAppend](http://msdn.microsoft.com/library/windows/desktop/bb773565). |  
|[ATLPath::BuildRoot](../atl/reference/atl-path-functions.md#buildroot)| Tato funkce je přetížené obálku pro [PathBuildRoot](http://msdn.microsoft.com/library/windows/desktop/bb773567). |  
|[ATLPath::Canonicalize](../atl/reference/atl-path-functions.md#canonicalize)| Tato funkce je přetížené obálku pro [PathCanonicalize](http://msdn.microsoft.com/library/windows/desktop/bb773569). |  
|[ATLPath::Combine](../atl/reference/atl-path-functions.md#combine)| Tato funkce je přetížené obálku pro [PathCombine](http://msdn.microsoft.com/library/windows/desktop/bb773571). |  
|[ATLPath::CommonPrefix](../atl/reference/atl-path-functions.md#commonprefix)| Tato funkce je přetížené obálku pro [PathCommonPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773574). |  
|[ATLPath::CompactPath](../atl/reference/atl-path-functions.md#compactpath)| Tato funkce je přetížené obálku pro [PathCompactPath](http://msdn.microsoft.com/library/windows/desktop/bb773575). |  
|[ATLPath::CompactPathEx](../atl/reference/atl-path-functions.md#compactpathex)| Tato funkce je přetížené obálku pro [PathCompactPathEx](http://msdn.microsoft.com/library/windows/desktop/bb773578). |  
|[ATLPath::FileExists](../atl/reference/atl-path-functions.md#fileexists)| Tato funkce je přetížené obálku pro [PathFileExists](http://msdn.microsoft.com/library/windows/desktop/bb773584). |  
|[ATLPath::FindExtension](../atl/reference/atl-path-functions.md#findextension)| Tato funkce je přetížené obálku pro [PathFindExtension](http://msdn.microsoft.com/library/windows/desktop/bb773587). |  
|[ATLPath::FindFileName](../atl/reference/atl-path-functions.md#findfilename)| Tato funkce je přetížené obálku pro [PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589). |  
|[ATLPath::GetDriveNumber](../atl/reference/atl-path-functions.md#getdrivenumber)| Tato funkce je přetížené obálku pro [PathGetDriveNumber](http://msdn.microsoft.com/library/windows/desktop/bb773612). |  
|[ATLPath::IsDirectory](../atl/reference/atl-path-functions.md#isdirectory)| Tato funkce je přetížené obálku pro [PathIsDirectory](http://msdn.microsoft.com/library/windows/desktop/bb773621). |  
|[ATLPath::IsFileSpec](../atl/reference/atl-path-functions.md#isfilespec)| Tato funkce je přetížené obálku pro [PathIsFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773627). |  
|[ATLPath::IsPrefix](../atl/reference/atl-path-functions.md#isprefix)| Tato funkce je přetížené obálku pro [PathIsPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773650). |  
|[ATLPath::IsRelative](../atl/reference/atl-path-functions.md#isrelative)| Tato funkce je přetížené obálku pro [PathIsRelative](http://msdn.microsoft.com/library/windows/desktop/bb773660). |  
|[ATLPath::IsRoot](../atl/reference/atl-path-functions.md#isroot)| Tato funkce je přetížené obálku pro [PathIsRoot](http://msdn.microsoft.com/library/windows/desktop/bb773674). |  
|[ATLPath::IsSameRoot](../atl/reference/atl-path-functions.md#issameroot)| Tato funkce je přetížené obálku pro [PathIsSameRoot](http://msdn.microsoft.com/library/windows/desktop/bb773687). |  
|[ATLPath::IsUNC](../atl/reference/atl-path-functions.md#isunc)| Tato funkce je přetížené obálku pro [PathIsUNC](http://msdn.microsoft.com/library/windows/desktop/bb773712). |  
|[ATLPath::IsUNCServer](../atl/reference/atl-path-functions.md#isuncserver)| Tato funkce je přetížené obálku pro [PathIsUNCServer](http://msdn.microsoft.com/library/windows/desktop/bb773722). |  
|[ATLPath::IsUNCServerShare](../atl/reference/atl-path-functions.md#isuncservershare)| Tato funkce je přetížené obálku pro [PathIsUNCServerShare](http://msdn.microsoft.com/library/windows/desktop/bb773723). |  
|[ATLPath::MakePretty](../atl/reference/atl-path-functions.md#makepretty)| Tato funkce je přetížené obálku pro [PathMakePretty](http://msdn.microsoft.com/library/windows/desktop/bb773725). |  
|[ATLPath::MatchSpec](../atl/reference/atl-path-functions.md#matchspec)| Tato funkce je přetížené obálku pro [PathMatchSpec](http://msdn.microsoft.com/library/windows/desktop/bb773727). |  
|[ATLPath::QuoteSpaces](../atl/reference/atl-path-functions.md#quotespaces)| Tato funkce je přetížené obálku pro [PathQuoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773739). |  
|[ATLPath::RelativePathTo](../atl/reference/atl-path-functions.md#relativepathto)| Tato funkce je přetížené obálku pro [PathRelativePathTo](http://msdn.microsoft.com/library/windows/desktop/bb773740). |  
|[ATLPath::RemoveArgs](../atl/reference/atl-path-functions.md#removeargs)| Tato funkce je přetížené obálku pro [PathRemoveArgs](http://msdn.microsoft.com/library/windows/desktop/bb773742). |  
|[ATLPath::RemoveBackslash](../atl/reference/atl-path-functions.md#removebackslash)| Tato funkce je přetížené obálku pro [PathRemoveBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773743). |  
|[ATLPath::RemoveBlanks](../atl/reference/atl-path-functions.md#removeblanks)| Tato funkce je přetížené obálku pro [PathRemoveBlanks](http://msdn.microsoft.com/library/windows/desktop/bb773745). |  
|[ATLPath::RemoveExtension](../atl/reference/atl-path-functions.md#removeextension)| Tato funkce je přetížené obálku pro [PathRemoveExtension](http://msdn.microsoft.com/library/windows/desktop/bb773746). |  
|[ATLPath::RemoveFileSpec](../atl/reference/atl-path-functions.md#removefilespec)| Tato funkce je přetížené obálku pro [PathRemoveFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773748). |  
|[ATLPath::RenameExtension](../atl/reference/atl-path-functions.md#renameextension)| Tato funkce je přetížené obálku pro [PathRenameExtension](http://msdn.microsoft.com/library/windows/desktop/bb773749). |  
|[ATLPath::SkipRoot](../atl/reference/atl-path-functions.md#skiproot)| Tato funkce je přetížené obálku pro [PathSkipRoot](http://msdn.microsoft.com/library/windows/desktop/bb773754). |  
|[ATLPath::StripPath](../atl/reference/atl-path-functions.md#strippath)| Tato funkce je přetížené obálku pro [PathStripPath](http://msdn.microsoft.com/library/windows/desktop/bb773756). |  
|[ATLPath::StripToRoot](../atl/reference/atl-path-functions.md#striptoroot)| Tato funkce je přetížené obálku pro [PathStripToRoot](http://msdn.microsoft.com/library/windows/desktop/bb773757). |  
|[ATLPath::UnquoteSpaces](../atl/reference/atl-path-functions.md#unquotespaces)| Tato funkce je přetížené obálku pro [PathUnquoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773763). |  
  

## <a name="see-also"></a>Viz také  
 [Koncepty](../atl/active-template-library-atl-concepts.md)   
 [Desktopové komponenty ATL objektů COM](../atl/atl-com-desktop-components.md)
