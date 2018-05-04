---
title: Třída CStringT | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CStringT
- ATLSTR/ATL::CStringT
- ATLSTR/ATL::CStringT::CStringT
- ATLSTR/ATL::CStringT::AllocSysString
- ATLSTR/ATL::CStringT::AnsiToOem
- ATLSTR/ATL::CStringT::AppendFormat
- ATLSTR/ATL::CStringT::Collate
- ATLSTR/ATL::CStringT::CollateNoCase
- ATLSTR/ATL::CStringT::Compare
- ATLSTR/ATL::CStringT::CompareNoCase
- ATLSTR/ATL::CStringT::Delete
- ATLSTR/ATL::CStringT::Find
- ATLSTR/ATL::CStringT::FindOneOf
- ATLSTR/ATL::CStringT::Format
- ATLSTR/ATL::CStringT::FormatMessage
- ATLSTR/ATL::CStringT::FormatMessageV
- ATLSTR/ATL::CStringT::FormatV
- ATLSTR/ATL::CStringT::GetEnvironmentVariable
- ATLSTR/ATL::CStringT::Insert
- ATLSTR/ATL::CStringT::Left
- ATLSTR/ATL::CStringT::LoadString
- ATLSTR/ATL::CStringT::MakeLower
- ATLSTR/ATL::CStringT::MakeReverse
- ATLSTR/ATL::CStringT::MakeUpper
- ATLSTR/ATL::CStringT::Mid
- ATLSTR/ATL::CStringT::OemToAnsi
- ATLSTR/ATL::CStringT::Remove
- ATLSTR/ATL::CStringT::Replace
- ATLSTR/ATL::CStringT::ReverseFind
- ATLSTR/ATL::CStringT::Right
- ATLSTR/ATL::CStringT::SetSysString
- ATLSTR/ATL::CStringT::SpanExcluding
- ATLSTR/ATL::CStringT::SpanIncluding
- ATLSTR/ATL::CStringT::Tokenize
- ATLSTR/ATL::CStringT::Trim
- ATLSTR/ATL::CStringT::TrimLeft
- ATLSTR/ATL::CStringT::TrimRight
- CSTRINGT/CStringT
- CSTRINGT/CStringT::CStringT
- CSTRINGT/CStringT::AllocSysString
- CSTRINGT/CStringT::AnsiToOem
- CSTRINGT/CStringT::AppendFormat
- CSTRINGT/CStringT::Collate
- CSTRINGT/CStringT::CollateNoCase
- CSTRINGT/CStringT::Compare
- CSTRINGT/CStringT::CompareNoCase
- CSTRINGT/CStringT::Delete
- CSTRINGT/CStringT::Find
- CSTRINGT/CStringT::FindOneOf
- CSTRINGT/CStringT::Format
- CSTRINGT/CStringT::FormatMessage
- CSTRINGT/CStringT::FormatMessageV
- CSTRINGT/CStringT::FormatV
- CSTRINGT/CStringT::GetEnvironmentVariable
- CSTRINGT/CStringT::Insert
- CSTRINGT/CStringT::Left
- CSTRINGT/CStringT::LoadString
- CSTRINGT/CStringT::MakeLower
- CSTRINGT/CStringT::MakeReverse
- CSTRINGT/CStringT::MakeUpper
- CSTRINGT/CStringT::Mid
- CSTRINGT/CStringT::OemToAnsi
- CSTRINGT/CStringT::Remove
- CSTRINGT/CStringT::Replace
- CSTRINGT/CStringT::ReverseFind
- CSTRINGT/CStringT::Right
- CSTRINGT/CStringT::SetSysString
- CSTRINGT/CStringT::SpanExcluding
- CSTRINGT/CStringT::SpanIncluding
- CSTRINGT/CStringT::Tokenize
- CSTRINGT/CStringT::Trim
- CSTRINGT/CStringT::TrimLeft
- CSTRINGT/CStringT::TrimRight
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], in ATL
- shared classes, CStringT
- CStringT class
ms.assetid: 7cacc59c-425f-40f1-8f5b-6db921318ec9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2f8a66f87b3c4a2c6712a1db93f97361a25b6955
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="cstringt-class"></a>CStringT – třída
Tato třída reprezentuje `CStringT` objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
 
template<typename BaseType, class StringTraits>  
class CStringT :   
public CSimpleStringT<BaseType,
                      _CSTRING_IMPL_::_MFCDLLTraitsCheck<BaseType, StringTraits>
                      ::c_bIsMFCDLLTraits>  
 
```  
  
#### <a name="parameters"></a>Parametry  
 `BaseType`  
 Tyto typy znaků třídy string. Může být jedna z následujících akcí:  
  
- `char` (pro znakových řetězců v kódu ANSI).  
  
- `wchar_t` (pro znakových řetězců v kódu Unicode).  
  
- **Tchar –** (pro ANSI a Unicode řetězce znaků).  
  
 `StringTraits`  
 Určuje, zda třída řetězec potřebuje podpora knihoven C Run-Time (CRT) a kde jsou umístěné řetězcové prostředky. Může být jedna z následujících akcí:  
  
- **StrTraitATL < wchar_t** &#124; `char` &#124; **TCHAR –, ChTraitsCRT < wchar_t** &#124; `char` &#124; **Tchar – >>**  
  
     Třída vyžaduje CRT – podpora a hledá řetězce prostředků v modulu určeného `m_hInstResource` (členem třídy modulu aplikace).  
  
- **StrTraitATL < wchar_t** &#124; `char` &#124; **TCHAR –, ChTraitsOS < wchar_t** &#124; `char` &#124; **Tchar – >>**  
  
     Třída nevyžaduje CRT – podpora a hledá řetězce prostředků v modulu určeného `m_hInstResource` (členem třídy modulu aplikace).  
  
- **StrTraitMFC < wchar_t** &#124; `char` &#124; **TCHAR –, ChTraitsCRT < wchar_t** &#124; `char` &#124; **Tchar – >>**  
  
     Třída vyžaduje CRT – podpora a hledá řetězce prostředků pomocí standardní vyhledávací algoritmus MFC.  
  
- **StrTraitMFC < wchar_t** &#124; `char` &#124; **TCHAR –, ChTraitsOS < wchar_t** &#124; `char` &#124; **Tchar – >>**  
  
     Třída nevyžaduje CRT – podpora a hledá řetězce prostředků pomocí standardní vyhledávací algoritmus MFC.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CStringT::CStringT](#cstringt)|Vytvoří `CStringT` objekt různými způsoby.|  
|[CStringT:: ~ CStringT](#_dtorcstringt)|Zničí `CStringT` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CStringT::AllocSysString](#allocsysstring)|Přiděluje `BSTR` z `CStringT` data.|  
|[CStringT::AnsiToOem](#ansitooem)|Usnadňuje konverzi na místě z znakovou sadu pro výrobce OEM znakovou sadu ANSI.|  
|[CStringT::AppendFormat](#appendformat)|Připojí formátovaných dat do existujícího `CStringT` objektu.|  
|[CStringT::Collate](#collate)|Porovnává dva řetězce (velká a malá písmena, používá informace specifické pro národní prostředí).|  
|[CStringT::CollateNoCase](#collatenocase)|Porovnává dva řetězce (nerozlišují, používá informace specifické pro národní prostředí).|  
|[CStringT::Compare](#compare)|Porovnává dva řetězce (malá a velká písmena).|  
|[CStringT::CompareNoCase](#comparenocase)|Porovnává dva řetězce (rozlišování malých a velkých písmen).|  
|[CStringT::Delete](#delete)|Odstraní znaky v řetězci.|  
|[CStringT::Find](#find)|Vyhledá znak nebo substring uvnitř řetězců.|  
|[CStringT::FindOneOf](#findoneof)|Vyhledá první odpovídající znak ze sady.|  
|[CStringT::Format](#format)|Formáty řetězec jako `sprintf` nepodporuje.|  
|[CStringT::FormatMessage](#formatmessage)|Formátuje řetězec zprávy.|  
|[CStringT::FormatMessageV](#formatmessagev)|Formátuje řetězec zprávy pomocí seznam argumentů s proměnnou.|  
|[CStringT::FormatV](#formatv)|Formátuje řetězec pomocí proměnné seznam argumentů.|  
|[CStringT::GetEnvironmentVariable](#getenvironmentvariable)|Nastaví na hodnotu proměnné prostředí zadaný řetězec.|  
|[CStringT::Insert](#insert)|Vloží jeden znak nebo dílčí řetězec daného indexu v rámci řetězce.|  
|[CStringT::Left](#left)|Extrahuje levé části řetězec.|  
|[CStringT::LoadString](#loadstring)|Načte existující `CStringT` objekt z prostředků Windows.|  
|[CStringT::MakeLower](#makelower)|Převede všechny znaky v tohoto řetězce na malá písmena.|  
|[CStringT::MakeReverse](#makereverse)|Obrátí řetězec.|  
|[CStringT::MakeUpper](#makeupper)|Převede všechny znaky v tohoto řetězce na velká písmena.|  
|[CStringT::Mid](#mid)|Extrahuje střední část řetězce.|  
|[CStringT::OemToAnsi](#oemtoansi)|Usnadňuje konverzi na místě od výrobce OEM znaku nastavit na znakovou sadu ANSI.|  
|[CStringT::Remove](#remove)|Odebere uvedené znaků z řetězce.|  
|[CStringT::Replace](#replace)|Nahradí uvedené znaky s jinými znaky.|  
|[CStringT::ReverseFind](#reversefind)|Vyhledá znak uvnitř větší řetězec; spustí od konce.|  
|[CStringT::Right](#right)|Extrahuje pravou část řetězec.|  
|[CStringT::SetSysString](#setsysstring)|Nastaví na existující `BSTR` objektu s použitím dat z `CStringT` objektu.|  
|[CStringT::SpanExcluding](#spanexcluding)|Extrahuje znaky z řetězce od prvního znaku, které nejsou v sadě znaků identifikovaný `pszCharSet`.|  
|[CStringT::SpanIncluding](#spanincluding)|Extrahuje dílčí řetězec, který obsahuje pouze znaky v sadě.|  
|[CStringT::Tokenize](#tokenize)|Extrahuje zadat tokeny v řetězci cíl.|  
|[CStringT::Trim](#trim)|Ořízne všechny úvodní a koncové znaky prázdných znaků z řetězce.|  
|[CStringT::TrimLeft](#trimleft)|Ořízne úvodní prázdné znaky z řetězce.|  
|[CStringT::TrimRight](#trimright)|Ořízne koncové znaky prázdných znaků z řetězce.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operátor =](#operator_eq)|Přiřadí novou hodnotu k `CStringT` objektu.|  
|[CStringT::operator +](#operator_add)|Zřetězí dva řetězce nebo řetězce a znak.|  
|[CStringT::operator +=](#operator_add_eq)|Zřetězí nového řetězce na konec existující řetězec.|  
|[CStringT::operator ==](#operator_eq_eq)|Určuje, jestli jsou logicky stejné dva řetězce.|  
|[CStringT::operator! =](#operator_neq)|Určuje, jestli dva řetězce jsou logicky nejsou stejné.|  
|[CStringT::operator &lt;](#operator_lt)|Určuje, zda řetězec na levé straně operátoru menší než na řetězec na pravé straně.|  
|[CStringT::operator &gt;](#operator_gt)|Určuje, zda řetězec na levé straně operátoru větší než řetězec na pravé straně.|  
|[CStringT::operator &lt;=](#operator_lt_eq)|Určuje, zda řetězec na levé straně operátoru menší než nebo rovna hodnotě řetězec na pravé straně.|  
|[CStringT::operator &gt;=](#operator_gt_eq)|Určuje, zda řetězec na levé straně operátoru větší než nebo rovna hodnotě řetězec na pravé straně.|  
  
## <a name="remarks"></a>Poznámky  
 `CStringT` dědí z [CSimpleStringT třída](../../atl-mfc-shared/reference/csimplestringt-class.md). Pokročilé funkce, jako je znak manipulaci, řazení a hledání, jsou implementované `CStringT`.  
  
> [!NOTE]
> `CStringT` objekty jsou schopná využívat vyvolávání výjimek. K tomu dojde při `CStringT` objektu spouští nedostatek paměti z jakéhokoli důvodu.  
  
 A `CStringT` objekt obsahuje proměnlivou délkou posloupnost znaků. `CStringT` poskytuje funkce a operátory pomocí syntaxe podobná Basic. Zřetězení a relační operátory, společně s Správa zjednodušené paměti, zkontrolujte `CStringT` objektů jednodušší než obyčejnou znaková pole.  
  
> [!NOTE]
>  I když je možné vytvořit `CStringT` instancí, které obsahují vložených znaky null, nedoporučujeme ji. Volání metody a operátory na `CStringT` objekty, které obsahují vložené znaky null může vést k neočekávaným výsledkům.  
  
 Pomocí různých kombinací `BaseType` a `StringTraits` parametry, `CStringT` objekty můžete přijde v následující typy, které jsou předem definoval knihovny ATL.  
  
 Pokud se používá v aplikaci ATL:  
  
 `CString`, `CStringA`, a `CStringW` byly exportovány z MFC DLL (MFC90. Knihovny DLL), nikdy od uživatele knihovny DLL. Děje se tak aby se zabránilo `CStringT` z násobkem definovaný.  
  
> [!NOTE]
>  Pokud váš kód obsahuje alternativní řešení pro chybami linkeru, která je popsána v [Linking Errors When You Import CString-Derived třídy "(Q309801)](https://support.microsoft.com/help/309801/you-may-receive-an-lnk2019-error-message-when-you-build-a-visual-c-200), byste měli odebrat tento kód. Se už nepotřebuje.  
  
 Následující typy řetězce jsou k dispozici v rámci aplikace založené na MFC:  
  
|Typ CStringT|Deklarace|  
|-------------------|-----------------|  
|`CStringA`|Znak ANSI zadejte řetězec s CRT – podpora.|  
|`CStringW`|Znak Unicode zadejte řetězec s CRT – podpora.|  
|`CString`|ANSI a Unicode typy znaků s CRT – podpora.|  
  
 Následující řetězec typy jsou k dispozici v projekty kde **ATL_CSTRING_NO_CRT** je definována:  
  
|Typ CStringT|Deklarace|  
|-------------------|-----------------|  
|**CAtlStringA**|Znak ANSI zadejte řetězec bez CRT – podpora.|  
|**CAtlStringW**|Znak Unicode zadejte řetězec bez CRT – podpora.|  
|**CAtlString**|ANSI a Unicode znakové typy bez CRT – podpora.|  
  
 Následující řetězec typy jsou k dispozici v projekty kde **ATL_CSTRING_NO_CRT** není definován:  
  
|Typ CStringT|Deklarace|  
|-------------------|-----------------|  
|**CAtlStringA**|Znak ANSI zadejte řetězec s CRT – podpora.|  
|**CAtlStringW**|Znak Unicode zadejte řetězec s CRT – podpora.|  
|**CAtlString**|ANSI a Unicode typy znaků s CRT – podpora.|  
  
 `CString` objekty také mít následující vlastnosti:  
  
- `CStringT` v důsledku operace sřetězení můžou růst objekty.  
  
- `CStringT` objekty podle "hodnota sémantiku." Představte si, že `CStringT` objekt jako řetězec skutečného, ne jako ukazatel na řetězec.  
  
-   Můžete volně nahradit `CStringT` objekty pro `PCXSTR` argumenty funkce.  
  
-   Správa vlastní paměti pro řetězec vyrovnávací paměti. Další informace najdete v tématu [Správa paměti a CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
## <a name="cstringt-predefined-types"></a>CStringT předdefinované typy  
 Protože `CStringT` používá šablonu argumentu zadat tyto typy znaků (buď [wchar_t](../../c-runtime-library/standard-types.md) nebo [char](../../c-runtime-library/standard-types.md)) nepodporuje typy parametrů metoda může být složité v některých případech. Pro zjednodušení tento problém, je definovaný a použít v celé sadu předdefinovaných typů `CStringT` třídy. Následující tabulka uvádí různé typy:  
  
|Název|Popis|  
|----------|-----------------|  
|`XCHAR`|Jeden znak (buď `wchar_t` nebo `char`) se stejným typem znak jako `CStringT` objektu.|  
|**YCHAR**|Jeden znak (buď `wchar_t` nebo `char`) s opačným typy znaků, jako `CStringT` objektu.|  
|`PXSTR`|Ukazatel na řetězec znaků (buď `wchar_t` nebo `char`) se stejným typem znak jako `CStringT` objektu.|  
|**PYSTR**|Ukazatel na řetězec znaků (buď `wchar_t` nebo `char`) s opačným typy znaků, jako `CStringT` objektu.|  
|`PCXSTR`|Ukazatel na **const** řetězec znaků (buď `wchar_t` nebo `char`) se stejným typem znak jako `CStringT` objektu.|  
|**PCYSTR**|Ukazatel na **const** řetězec znaků (buď `wchar_t` nebo `char`) s opačným typy znaků, jako `CStringT` objektu.|  
  
> [!NOTE]
>  Kód, který dřív používal nedokumentovanými metody `CString` (například **AssignCopy**) s kódem, který používá tyto metody zdokumentovaných se musí nahradit `CStringT` (například `GetBuffer` nebo `ReleaseBuffer`). Tyto metody se dědí z `CSimpleStringT`.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)  
  
 `CStringT`  
  
## <a name="requirements"></a>Požadavky  
  
|Záhlaví|Použít pro|  
|------------|-------------|  
|cstringt.h|Objekty řetězec pouze pro MFC|  
|atlstr.h|Objekty řetězce bez knihovny MFC|  
  
##  <a name="allocsysstring"></a>  CStringT::AllocSysString  
 Přiděluje řetězec kompatibilního s automatizací typu `BSTR` a zkopíruje obsah `CStringT` objektu do ní, včetně ukončující znak hodnoty null.  
  
```  
BSTR AllocSysString() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nově přidělených řetězec.  
  
### <a name="remarks"></a>Poznámky  
 V aplikacích MFC [CMemoryException třída](../../mfc/reference/cmemoryexception-class.md) je vyvolána, pokud existuje nedostatek paměti. V aplikacích ATL [CAtlException](../../atl/reference/catlexception-class.md) je vyvolána výjimka. Tato funkce se obvykle používá k vrácení řetězce pro automatizaci.  
  

 Běžně Pokud se tento řetězec je předaný funkci COM jako [in] parametr a potom to vyžaduje volající uvolnit řetězec. To můžete provést pomocí [SysFreeString](https://msdn.microsoft.com/library/windows/desktop/ms221481.aspx), jak je popsáno v sadě Windows SDK. Další informace najdete v tématu [Allocating a uvolňování paměti pro BSTR](../../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md).  
  
 Další informace o funkcích přidělení OLE ve Windows najdete v tématu [SysAllocString](https://msdn.microsoft.com/library/windows/desktop/ms221458.aspx) ve Windows SDK.  

  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje použití `CStringT::AllocSysString`.  
  
 [!code-cpp[NVC_ATLMFC_Utilities#105](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_1.cpp)]  
  
##  <a name="ansitooem"></a>  CStringT::AnsiToOem  
 Převede všechny znaky v tomto `CStringT` objekt z znakovou sadu pro výrobce OEM znakovou sadu ANSI.  
  
```  
void AnsiToOem();
```  
  
### <a name="remarks"></a>Poznámky  
 Funkce není k dispozici Pokud `_UNICODE` je definována.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#106](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_2.cpp)]  
  
##  <a name="appendformat"></a>  CStringT::AppendFormat  
 Připojí formátovaných dat do existujícího `CStringT` objektu.  
  
```  
void __cdecl AppendFormat(PCXSTR pszFormat, [, argument] ...);
void __cdecl AppendFormat(UINT nFormatID, [, argument] ...);
```  
  
### <a name="parameters"></a>Parametry  
 `pszFormat`  
 Řetězec formátu control.  
  
 `nFormatID`  
 Identifikátor prostředku řetězec, který obsahuje řetězec formát ovládacího prvku.  
  
 `argument`  
 Volitelné argumenty  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce naformátuje a připojí řady znaků a hodnot v `CStringT`. Všechny volitelné argumenty (pokud existuje) je převeden a připojí podle odpovídající specifikaci formátu v `pszFormat` nebo z prostředků řetězec identifikovaný `nFormatID`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#107](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_3.cpp)]  
  
##  <a name="collate"></a>  CStringT::Collate  
 Porovnává dva řetězce, pomocí funkce obecného textu `_tcscoll`.  
  
```  
int Collate(PCXSTR psz) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `psz`  
 Ostatní řetězec použitý pro porovnání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nula. Pokud jsou řetězce identické, < 0, pokud `CStringT` objekt je menší než `psz`, nebo > 0, pokud `CStringT` objektu je větší než `psz`.  
  
### <a name="remarks"></a>Poznámky  
 Funkce obecného textu `_tcscoll`, která je definována v Tchar –. H, se mapuje na buď `strcoll`, `wcscoll`, nebo `_mbscoll`, v závislosti na znakovou sadu, která je definována v době kompilace. Jednotlivé funkce provádí malá a velká písmena porovnání řetězců podle znakové stránky aktuálně používá. Další informace najdete v tématu [strcoll –, wcscoll –, _mbscoll –, _strcoll_l –, _wcscoll_l –, _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md).  
  
##  <a name="collatenocase"></a>  CStringT::CollateNoCase  
 Porovnává dva řetězce, pomocí funkce obecného textu `_tcscoll`.  
  
```  
int CollateNoCase(PCXSTR psz) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `psz`  
 Ostatní řetězec použitý pro porovnání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nula, pokud jsou řetězce identické (bude ignorována případ), < 0, pokud `CStringT` objekt je menší než `psz` (ignorována případ), nebo > 0, pokud `CStringT` objektu je větší než `psz` (ignorována případ).  
  
### <a name="remarks"></a>Poznámky  
 Funkce obecného textu `_tcscoll`, která je definována v Tchar –. H, se mapuje na buď `stricoll`, `wcsicoll`, nebo `_mbsicoll`, v závislosti na znakovou sadu, která je definována v době kompilace. Jednotlivé funkce provádí velká a malá písmena porovnání řetězců, podle znakové stránky aktuálně používán. Další informace najdete v tématu [strcoll –, wcscoll –, _mbscoll –, _strcoll_l –, _wcscoll_l –, _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#109](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_4.cpp)]  
  
##  <a name="compare"></a>  CStringT::Compare  
 Porovnává dva řetězce (malá a velká písmena).  
  
```  
int Compare(PCXSTR psz) const; 
```  
  
### <a name="parameters"></a>Parametry  
 `psz`  
 Ostatní řetězec použitý pro porovnání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nula. Pokud jsou řetězce identické, < 0, pokud `CStringT` objekt je menší než `psz`, nebo > 0, pokud `CStringT` objektu je větší než `psz`.  
  
### <a name="remarks"></a>Poznámky  
 Funkce obecného textu `_tcscmp`, která je definována v Tchar –. H, se mapuje na buď `strcmp`, `wcscmp`, nebo `_mbscmp`, v závislosti na znakovou sadu, která je definována v době kompilace. Jednotlivé funkce provede malá a velká písmena porovnání řetězce a nemá vliv národního prostředí. Další informace najdete v tématu [strcmp – wcscmp –, _mbscmp –](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md).  
  
 Pokud řetězec obsahuje vložené hodnoty Null, pro účely porovnání řetězce se považuje být zkráceno na první embedded znak hodnoty null.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje použití `CStringT::Compare`.  
  
 [!code-cpp[NVC_ATLMFC_Utilities#110](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_5.cpp)]  
  
##  <a name="comparenocase"></a>  CStringT::CompareNoCase  
 Porovnává dva řetězce (rozlišování malých a velkých písmen).  
  
```  
int CompareNoCase(PCXSTR psz) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `psz`  
 Ostatní řetězec použitý pro porovnání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nula, pokud jsou řetězce identické (ignorována případ), < 0, pokud tato `CStringT` objekt je menší než `psz` (ignorována případ), nebo > 0, pokud tato `CStringT` objektu je větší než `psz` (ignorována případ).  
  
### <a name="remarks"></a>Poznámky  
 Funkce obecného textu `_tcsicmp`, která je definována v Tchar –. H, se mapuje na buď `_stricmp`, `_wcsicmp` nebo `_mbsicmp`, v závislosti na znakovou sadu, která je definována v době kompilace. Jednotlivé funkce provede porovnávání řetězců. Porovnání závisí na `LC_CTYPE` aspekt národní prostředí, ale ne `LC_COLLATE`. Další informace najdete v tématu [_stricmp –, _wcsicmp –, _mbsicmp –, _stricmp_l –, _wcsicmp_l –, _mbsicmp_l –](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#111](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_6.cpp)]  
  
##  <a name="cstringt"></a>  CStringT::CStringT  
 Vytvoří `CStringT` objektu.  
  
```  
CStringT() throw() :   
    CThisSimpleString(StringTraits::GetDefaultManager());
 
explicit CStringT(IAtlStringMgr* pStringMgr) throw() :   
    CThisSimpleString( pStringMgr); 

CStringT(const VARIANT& varSrc);
 
CStringT(const VARIANT& varSrc, IAtlStringMgr* pStringMgr);
 
CStringT(const CStringT& strSrc) :   
    CThisSimpleString( strSrc);

 operator CSimpleStringT<
                    BaseType, 
                    !_CSTRING_IMPL_::_MFCDLLTraitsCheck<BaseType, StringTraits>
                    :: c_bIsMFCDLLTraits> &()  
 
template <bool bMFCDLL>  
CStringT(const CSimpleStringT<BaseType, bMFCDLL>& strSrc) :   
    CThisSimpleString( strSrc);
 
template <class SystemString>  
CStringT(SystemString^ pString) :   
    CThisSimpleString( StringTraits::GetDefaultManager());
 
CStringT(const XCHAR* pszSrc) :   
    CThisSimpleString( StringTraits::GetDefaultManager());
 
CSTRING_EXPLICIT CStringT(const YCHAR* pszSrc) :   
    CThisSimpleString( StringTraits::GetDefaultManager());
 
CStringT(LPCSTR pszSrc, IAtlStringMgr* pStringMgr) :   
    CThisSimpleString( pStringMgr);
 
CStringT(LPCWSTR pszSrc, IAtlStringMgr* pStringMgr) :   
    CThisSimpleString( pStringMgr);
 
CSTRING_EXPLICIT CStringT(const unsigned char* pszSrc) :   
    CThisSimpleString( StringTraits::GetDefaultManager());
 
/*CSTRING_EXPLICIT*/ CStringT(char* pszSrc) :   
    CThisSimpleString( StringTraits::GetDefaultManager());
 
CSTRING_EXPLICIT CStringT(unsigned char* pszSrc) :   
    CThisSimpleString( StringTraits::GetDefaultManager());
 
CSTRING_EXPLICIT CStringT(wchar_t* pszSrc) :   
    CThisSimpleString( StringTraits::GetDefaultManager());
 
CStringT(const unsigned char* pszSrc, IAtlStringMgr* pStringMgr) :   
    CThisSimpleString( pStringMgr);
 
CSTRING_EXPLICIT CStringT(char ch, int nLength = 1) :   
    CThisSimpleString( StringTraits::GetDefaultManager());
 
CSTRING_EXPLICIT CStringT(wchar_t ch, int nLength = 1) :   
    CThisSimpleString( StringTraits::GetDefaultManager());
 
CStringT(const XCHAR* pch, int nLength) :   
    CThisSimpleString( pch, nLength, StringTraits::GetDefaultManager());
 
CStringT(const YCHAR* pch, int nLength) :   
    CThisSimpleString( StringTraits::GetDefaultManager());
 
CStringT(const XCHAR* pch, int nLength, AtlStringMgr* pStringMgr) :   
    CThisSimpleString( pch, nLength, pStringMgr);
 
CStringT(const YCHAR* pch, int nLength, IAtlStringMgr* pStringMgr) :   
    CThisSimpleString( pStringMgr);
```  
  
### <a name="parameters"></a>Parametry  
 `pch`  
 Ukazatel na pole znaků délky `nLength`, není ukončené hodnotou null.  
  
 `nLength`  
 Počet znaků v `pch`.  
  
 `ch`  
 Jeden znak.  
  
 `pszSrc`  
 Řetězce ukončené hodnotou null zkopírovat do této `CStringT` objektu.  
  
 `pStringMgr`  
 Ukazatel na správce paměti pro `CStringT` objektu. Další informace o `IAtlStringMgr` a správa paměti pro `CStringT`, najdete v části [Správa paměti s CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
 `strSrc`  
 Existující `CStringT` objekt, který se má zkopírovat do této `CStringT` objektu. Další informace o `CThisString` a `CThisSimpleString`, naleznete v části poznámky.  
  
 `varSrc`  
 Objekt variant zkopírovat do této `CStringT` objektu.  
  
 `BaseType`  
 Tyto typy znaků třídy string. Může být jedna z následujících akcí:  
  
 `char` (pro znakových řetězců v kódu ANSI).  
  
 `wchar_t` (pro znakových řetězců v kódu Unicode).  
  
 `TCHAR` (pro ANSI a Unicode řetězce znaků).  
  
 `bMFCDLL`  
 Logická hodnota, která určuje, zda je projektu knihovny MFC DLL (TRUE) nebo ne (FALSE).  
  
 `SystemString`  
 Musí být `System::String`, a musí být zkompilovány projektu s volbou/CLR.  
  
 `pString`  
 Popisovač pro `CStringT` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Protože konstruktorů zkopírovat do nového úložiště přidělené vstupních dat, je třeba si uvědomit, že paměť, může způsobit výjimky. Všimněte si, že některé z těchto konstruktorů fungovat jako funkce pro převod. To umožňuje nahradit, například `LPTSTR` kde `CStringT` je byl očekáván objekt.  
  
- `CStringT`( `LPCSTR` `lpsz` ): Vytvoří typu Unicode `CStringT` z řetězce ANSI. Tento konstruktor můžete také načíst řetězec prostředků, jak je znázorněno v následujícím příkladu.  
  
- `CStringT(` `LPCWSTR` `lpsz` ): Vytvoří `CStringT` z řetězec znaků Unicode.  
  
- `CStringT`( `const unsigned char*` `psz` ): Umožňuje vytvořit `CStringT` z ukazatel na `unsigned char`.  
  
> [!NOTE]
>  Definování **_CSTRING_DISABLE_NARROW_WIDE_CONVERSION** makro vypnout řetězec implicitní převod mezi [!INCLUDE[vcpransi](../../atl-mfc-shared/reference/includes/vcpransi_md.md)] a [!INCLUDE[TLA#tla_unicode](../../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)] řetězce. Makro vyloučí z kompilace konstruktory, které podporují převod.  
  
 Všimněte si, že `strSrc` parametr může být buď `CStringT` nebo `CThisSimpleString` objektu. Pro `CStringT`, použijte jednu z jeho výchozí konkretizací ( `CString`, `CStringA`, nebo `CStringW`); pro `CThisSimpleString`, používat `this` ukazatel. `CThisSimpleString` deklaruje instanci [CSimpleStringT třída](../../atl-mfc-shared/reference/csimplestringt-class.md), která je menší třída řetězec s méně integrovanou funkci než `CStringT` – třída.  
  
 Přetížení operátoru `CSimpleStringT<>&()` vytvoří `CStringT` objektu z `CSimpleStringT` deklarace.  
  
> [!NOTE]
>  I když je možné vytvořit `CStringT` instancí, které obsahují vložených znaky null, nedoporučujeme ji. Volání metody a operátory na `CStringT` objekty, které obsahují vložené znaky null může vést k neočekávaným výsledkům.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#112](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_7.cpp)]  
  
##  <a name="_dtorcstringt"></a>  CStringT:: ~ CStringT  
 Zničí `CStringT` objektu.  
  
```  
~CStringT() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Zničí `CStringT` objektu.  
  
##  <a name="delete"></a>  CStringT::Delete  
 Odstraní znak nebo znaků z řetězce začínající znakem daným indexem.  
  
```  
int Delete(int iIndex, int nCount = 1);
```  
  
### <a name="parameters"></a>Parametry  
 `iIndex`  
 Index prvního znaku v založený na nule `CStringT` objekt k odstranění.  
  
 `nCount`  
 Počet znaků, který má být odebrána.  
  
### <a name="return-value"></a>Návratová hodnota  
 Délka řetězce změněné.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `nCount` je delší, než se odeberou řetězec zbytek řetězce.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#113](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_8.cpp)]  
  
```Output  
Before: Soccer is best,
    but hockey is quicker!  
After: Soccer best,
    but hockey is quicker!  
```  
  
##  <a name="find"></a>  CStringT::Find  
 Tento řetězec hledá na první shodu znaku nebo dílčí řetězec.  
  
```  
int Find(PCXSTR pszSub, int iStart=0) const throw();
int Find(XCHAR ch, int iStart=0) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pszSub`  
 Dílčí řetězec pro vyhledávání.  
  
 `iStart`  
 Index znaku v řetězci k zahájení hledání se nebo 0, chcete-li začít od začátku.  
  
 `ch`  
 Jeden znak pro vyhledávání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index prvního znaku v tomto založený na nule `CStringT` objekt, který odpovídá požadovaný substring nebo znaků; -1, pokud nebyl nalezen dílčí řetězec nebo znak.  
  
### <a name="remarks"></a>Poznámky  
 Funkce je přetížena tak, aby přijímal obou jednotlivé znaky (podobně jako funkce běhové `strchr`) a řetězce (podobně jako `strstr`).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#114](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_9.cpp)]  
  
##  <a name="findoneof"></a>  CStringT::FindOneOf  
 Vyhledá tento řetězec prvního znaku, který odpovídá jakémukoliv znaku obsažené v `pszCharSet`.  
  
```  
int FindOneOf(PCXSTR pszCharSet) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pszCharSet`  
 Řetězec obsahující znaky k porovnání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index prvního znaku v tomto řetězci, který je k dispozici také v založený na nule `pszCharSet`; -1, pokud není nalezena žádná shoda.  
  
### <a name="remarks"></a>Poznámky  
 Najde první výskyt některý ze znaků v `pszCharSet`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#115](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_10.cpp)]  
  
##  <a name="format"></a>  CStringT::Format  
 Zápisy formátovaných dat do `CStringT` stejným způsobem [sprintf_s –](../../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md) formáty dat do pole znaků stylu jazyka C.  
  
```  
void __cdecl Format(UINT nFormatID, [, argument]...);
void __cdecl Format(PCXSTR pszFormat,  [, argument] ...);
```  
  
### <a name="parameters"></a>Parametry  
 `nFormatID`  
 Identifikátor prostředku řetězec, který obsahuje řetězec formát ovládacího prvku.  
  
 `pszFormat`  
 Řetězec formátu control.  
  
 `argument`  
 Volitelné argumenty  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce naformátuje a ukládá řady znaků a hodnot v `CStringT`. Všechny volitelné argumenty (pokud existuje) je převeden a výstup podle odpovídající specifikaci formátu v `pszFormat` nebo z prostředků řetězec identifikovaný `nFormatID`.  
  
 Volání se nezdaří, pokud samotného objektu řetězec je poskytován jako parametr, který se `Format`. Například následující kód bude způsobit nepředvídatelné výsledky:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#116](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_11.cpp)]  
  
 Další informace najdete v tématu [syntaxe specifikace formátu: funkce printf a wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#117](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_12.cpp)]  
  
##  <a name="formatmessage"></a>  CStringT::FormatMessage  
 Formátuje řetězec zprávy.  
  
```  
void __cdecl FormatMessage(UINT nFormatID, [, argument]...);
void __cdecl FormatMessage(PCXSTR pszFormat, [, argument]...);
```  
  
### <a name="parameters"></a>Parametry  
 `nFormatID`  
 Identifikátor prostředku řetězec obsahující text neformátovaný zprávy.  
  
 `pszFormat`  
 Odkazuje na řetězec formátu control. Bude hledat vložení a formátu odpovídajícím způsobem. Řetězec formátu je podobná spuštění funkce `printf`-formátování řetězce formátu, s výjimkou umožňuje parametrů má být vložen v libovolném pořadí.  
  
 `argument`  
 Volitelné argumenty  
  
### <a name="remarks"></a>Poznámky  
 Funkce vyžaduje definice zprávy jako vstup. Definice zprávy je dáno `pszFormat` nebo z prostředků řetězec identifikovaný `nFormatID`. Funkce zkopíruje formátovaná zpráva text, který má `CStringT` objekt, zpracování žádné vložených vložit pořadí, pokud požadovaný.  
  
> [!NOTE]
> `FormatMessage` pokusí se přidělit paměť systému pro nově formátovaný řetězec. Pokud tento pokus selže, je automaticky vyvolána výjimka paměti.  
  
 Každý příkaz insert musí mít odpovídající parametr následující `pszFormat` nebo `nFormatID` parametr. V rámci text zprávy se podporují několik řídicí sekvence pro dynamicky formátování zprávy. Další informace najdete v tématu Windows [FormatMessage](http://msdn.microsoft.com/library/windows/desktop/ms679351) funkce ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#118](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_13.cpp)]  
  
##  <a name="formatmessagev"></a>  CStringT::FormatMessageV  
 Formátuje řetězec zprávy pomocí seznam argumentů s proměnnou.  
  
```  
void FormatMessageV(PCXSTR pszFormat, va_list* pArgList);
```  
  
### <a name="parameters"></a>Parametry  
 `pszFormat`  
 Odkazuje na řetězec formátu control. Bude hledat vložení a formátu odpovídajícím způsobem. Řetězec formátu je podobná spuštění funkce `printf`-formátování řetězce formátu, s výjimkou umožňuje parametrů má být vložen v libovolném pořadí.  
  
 `pArgList`  
 Ukazatel na seznam argumentů.  
  
### <a name="remarks"></a>Poznámky  
 Funkce vyžaduje definice zprávy jako vstup, dáno `pszFormat`. Funkce zkopíruje text formátovaná zpráva a seznam argumentů pro proměnné `CStringT` objekt, zpracování žádné vložených vložit pořadí, pokud požadovaný.  
  
> [!NOTE]
> `FormatMessageV` volání [CStringT::FormatMessage](#formatmessage), která se pokusí přidělit paměť systému pro nově formátovaný řetězec. Pokud tento pokus selže, je automaticky vyvolána výjimka paměti.  
  
 Další informace najdete v tématu Windows [FormatMessage](http://msdn.microsoft.com/library/windows/desktop/ms679351) funkce ve Windows SDK.  
  
##  <a name="formatv"></a>  CStringT::FormatV  
 Formátuje řetězec zprávy pomocí seznam argumentů s proměnnou.  
  
```  
void FormatV(PCXSTR pszFormat, va_list args);
```  
  
### <a name="parameters"></a>Parametry  
 `pszFormat`  
 Odkazuje na řetězec formátu control. Bude hledat vložení a formátu odpovídajícím způsobem. Řetězec formátu je podobná spuštění funkce `printf`-formátování řetězce formátu, s výjimkou umožňuje parametrů má být vložen v libovolném pořadí.  
  
 `args`  
 Ukazatel na seznam argumentů.  
  
### <a name="remarks"></a>Poznámky  
 Zapíše formátovaný řetězec a proměnné seznam argumentů pro `CStringT` řetězec stejným způsobem `vsprintf_s` formáty dat do pole znaků stylu jazyka C.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#119](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_14.cpp)]  
  
 [!code-cpp[NVC_ATLMFC_Utilities#120](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_15.cpp)]  
  
##  <a name="getenvironmentvariable"></a>  CStringT::GetEnvironmentVariable  
 Nastaví na hodnotu proměnné prostředí zadaný řetězec.  
  
```  
BOOL GetEnvironmentVariable(PCXSTR pszVar);
```  
  
### <a name="parameters"></a>Parametry  
 `pszVar`  
 Ukazatel na řetězec ukončené hodnotou null, který určuje proměnnou prostředí.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Načte hodnotu zadanou proměnnou z prostředí bloku volajícího procesu. Hodnota je ve formě řetězec znaků ukončený hodnotou null.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#121](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_16.cpp)]  
  
##  <a name="insert"></a>  CStringT::Insert  
 Vloží jeden znak nebo dílčí řetězec daného indexu v rámci řetězce.  
  
```  
int Insert(int iIndex, PCXSTR psz);
int Insert(int iIndex, XCHAR ch);
```  
  
### <a name="parameters"></a>Parametry  
 `iIndex`  
 Index znak, před kterou bude vložení probíhat.  
  
 `psz`  
 Ukazatel na dílčí řetězec, který má být vložen.  
  
 `ch`  
 Znak, který má být vložen.  
  
### <a name="return-value"></a>Návratová hodnota  
 Délka řetězce změněné.  
  
### <a name="remarks"></a>Poznámky  
 `iIndex` Parametr identifikuje prvního znaku, který bude přesunut do uvolnil prostor pro znak nebo dílčí řetězec. Pokud `nIndex` rovná nule, dojde k vložení před celý řetězec. Pokud `nIndex` je vyšší než délka řetězce, funkce bude řetězení přítomen řetězec a nové materiály poskytované buď `ch` nebo `psz`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#122](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_17.cpp)]  
  
##  <a name="left"></a>  CStringT::Left  
 Extrahuje levou krajní `nCount` znaky z tohoto `CStringT` objektu a vrátí kopii extrahované dílčí řetězec.  
  
```  
CStringT Left(int nCount) const; 
```  
  
### <a name="parameters"></a>Parametry  
 `nCount`  
 Počet znaků k extrakci z tohoto `CStringT` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CStringT` objekt, který obsahuje kopii zadaný rozsah znaků. Vrácený `CStringT` objekt může být prázdný.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `nCount` překračuje délku řetězce a pak je extrahován celý řetězec. `Left` je podobná základní `Left` funkce.  
  
 Pro vícebajtové znakové sady (MBCS), `nCount` považuje pořadí jednotlivých 8bitové jako znak, tak, aby `nCount` vrátí počet vícebajtové znaky vynásobit dvěma.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#123](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_18.cpp)]  
  
##  <a name="loadstring"></a>  CStringT::LoadString  
 Načte prostředek řetězce Windows identifikovaný `nID`, do existující `CStringT` objektu.  
  
```  
BOOL LoadString(HINSTANCE hInstance, UINT nID, WORD wLanguageID);
BOOL LoadString(HINSTANCE hInstance, UINT nID);
BOOL LoadString(UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `hInstance`  
 Popisovač pro instanci modulu.  
  
 `nID`  
 Windows řetězec prostředku.  
  
 `wLanguageID`  
 Jazyk řetězec prostředku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud zatížení prostředků byla úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Načte prostředek řetězce ( `nID`) z zadaný modul ( `hInstance`) v daném jazyce ( `wLanguage`).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#124](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_19.cpp)]  
  
##  <a name="makelower"></a>  CStringT::MakeLower  
 Převede `CStringT` objekt na řetězec malá písmena.  
  
```  
CStringT& MakeLower();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výsledný řetězec, malá písmena.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#125](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_20.cpp)]  
  
##  <a name="makereverse"></a>  CStringT::MakeReverse  
 Obrátí pořadí znaků v `CStringT` objektu.  
  
```  
CStringT& MakeReverse();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výsledná vrátit zpět na řetězec.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#126](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_21.cpp)]  
  
##  <a name="makeupper"></a>  CStringT::MakeUpper  
 Převede `CStringT` objekt na řetězec velká písmena.  
  
```  
CStringT& MakeUpper();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výsledný řetězec velká písmena.  
  
### <a name="remarks"></a>Poznámky  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#127](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_22.cpp)]  
  
##  <a name="mid"></a>  CStringT::Mid  
 Extrahuje dílčí řetězec o délce `nCount` znaky z tohoto `CStringT` objekt, začínající na pozici `iFirst` (počítáno od nuly).  
  
```  
CStringT Mid(int iFirst, int nCount) const;
CStringT Mid(int iFirst) const; 
```  
  
### <a name="parameters"></a>Parametry  
 `iFirst`  
 Index prvního znaku v tomto založený na nule `CStringT` objekt, který má být součástí extrahované dílčí řetězec.  
  
 `nCount`  
 Počet znaků k extrakci z tohoto `CStringT` objektu. Pokud není tento parametr zadán, je zbytek řetězec extrahován.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CStringT` objekt, který obsahuje kopii zadaný rozsah znaků. Všimněte si, že vrácený `CStringT` objekt může být prázdný.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí kopii extrahované dílčí řetězec. `Mid` je podobná funkce základní Mid (kromě toho, že indexy v Basic jsou základem jedna).  
  
 Pro vícebajtových znakových sad (MBCS), `nCount` odkazuje na všech bajtů 8bitové znak; to znamená, realizace a záznam v jednom vícebajtových znaků, se počítají jako dva znaky.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#128](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_23.cpp)]  
  
##  <a name="oemtoansi"></a>  CStringT::OemToAnsi  
 Převede všechny znaky v tomto `CStringT` objekt z OEM znakovou sadu pro znakovou sadu ANSI.  
  
```  
void OemToAnsi();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce není k dispozici Pokud `_UNICODE` je definována.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CStringT::AnsiToOem](#ansitooem).  
  
##  <a name="operator_add"></a>  CStringT::operator +  
 Zřetězí dva řetězce nebo řetězce a znak.  
  
```  
friend CStringT operator+(const CStringT& str1, const CStringT& str2);
friend CStringT operator+(const CStringT& str1, PCXSTR psz2);
friend CStringT operator+(PCXSTR psz1, const CStringT& str2,);
friend CStringT operator+(char ch1, const CStringT& str2,);
friend CStringT operator+(const CStringT& str1, char ch2);
friend CStringT operator+(const CStringT& str1, wchar_t ch2);
friend CStringT operator+(wchar_t ch1, const CStringT& str2,);
```  
  
### <a name="parameters"></a>Parametry  
 `ch1`  
 ANSI nebo Unicode znak ke zřetězení řetězcem.  
  
 `ch2`  
 ANSI nebo Unicode znak ke zřetězení řetězcem.  
  
 `str1`  
 A `CStringT` ke zřetězení s řetězec nebo znak.  
  
 `str2`  
 A `CStringT` ke zřetězení s řetězec nebo znak.  
  
 `psz1`  
 Ukazatel na řetězce ukončené hodnotou null ke zřetězení s řetězec nebo znak.  
  
 `psz2`  
 Ukazatel na řetězec tak, aby řetězení s řetězec nebo znak.  
  
### <a name="remarks"></a>Poznámky  
 Jsou formy sedm přetížení `CStringT::operator+` funkce. První verze zřetězí dvě existující `CStringT` objekty. Další dva zřetězení `CStringT` objekt a řetězce ukončené hodnotou null. Další dva zřetězení `CStringT` objekt a znak ANSI. Poslední dva zřetězení `CStringT` objekt a znak Unicode.  
  
> [!NOTE]
>  I když je možné vytvořit `CStringT` instancí, které obsahují vložených znaky null, nedoporučujeme ji. Volání metody a operátory na `CStringT` objekty, které obsahují vložené znaky null může vést k neočekávaným výsledkům.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#140](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_24.cpp)]  
  
##  <a name="operator_add_eq"></a>  CStringT::operator +=  
 Zřetězí znaků do konce řetězce.  
  
```  
CStringT& operator+=(const CThisSimpleString& str);

template<bool bMFCDLL>  
CStringT& operator+=(const const CSimpleStringT<BaseType, bMFCDLL>& str);

template<int t_nSize>  
CStringT& operator+=(const CStaticString<XCHAR, t_nSize>& strSrc);
CStringT& operator+=(PCXSTR pszSrc);
CStringT& operator+=(PCYSTR pszSrc);
CStringT& operator+=(char ch);
CStringT& operator+=(unsigned char ch);
CStringT& operator+=(wchar_t ch);
CStringT& operator+=(const VARIANT& var);
```  
  
### <a name="parameters"></a>Parametry  
 str –  
 Odkaz na `CThisSimpleString` objektu.  
  
 `bMFCDLL`  
 Logická hodnota určuje, zda je projektu knihovny MFC DLL nebo ne.  
  
 `BaseType`  
 Základní typ řetězec.  
  
 `var`  
 Variant objekt ke zřetězení tento řetězec.  
  
 `ch`  
 ANSI nebo Unicode znak ke zřetězení řetězcem.  
  
 `pszSrc`  
 Ukazatel na původní řetězec je zřetězen.  
  
 `strSrc`  
 A `CStringT` ke zřetězení tento řetězec.  
  
### <a name="remarks"></a>Poznámky  
 Operátor přijímá jiné `CStringT` objektu, ukazatel znak nebo jeden znak. Mějte na paměti, že výjimky dochází vždy, když použijete tento operátor řetězení, protože nové úložiště může být přidělen znaky, které jsou přidány do tohoto `CStringT` objektu.  
  
 Informace o `CThisSimpleString`, najdete v části poznámky [CStringT::CStringT](#cstringt).  
  
> [!NOTE]
>  I když je možné vytvořit `CStringT` instancí, které obsahují vložených znaky null, nedoporučujeme ji. Volání metody a operátory na `CStringT` objekty, které obsahují vložené znaky null může vést k neočekávaným výsledkům.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#141](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_25.cpp)]  
  
##  <a name="operator_eq_eq"></a>  CStringT::operator ==  
 Určuje, zda jsou dva řetězce logicky stejné.  
  
```  
friend bool operator==(const CStringT& str1, const CStringT& str2) throw();
friend bool operator==(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator==(const CStringT& str1, PCYSTR psz2) throw();
friend bool operator==(const CStringT& str1, XCHAR ch2) throw();
friend bool operator==(PCXSTR psz1, const CStringT& str2) throw();
friend bool operator==(PCYSTR psz1, const CStringT& str2,) throw();
friend bool operator==(XCHAR ch1, const CStringT& str2,) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `ch1`  
 ANSI nebo Unicode znak pro porovnání.  
  
 `ch2`  
 ANSI nebo Unicode znak pro porovnání.  
  
 `str1`  
 A `CStringT` pro porovnání.  
  
 `str2`  
 A `CStringT` pro porovnání.  
  
 `psz1`  
 Ukazatel na řetězce ukončené hodnotou null pro porovnání.  
  
 `psz2`  
 Ukazatel na řetězce ukončené hodnotou null pro porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Ověřuje, zda řetězec nebo znak na levé straně se rovná řetězec nebo znak na pravé straně a vrátí hodnotu TRUE nebo FALSE odpovídajícím způsobem.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#142](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_26.cpp)]  
  
##  <a name="operator_neq"></a>  CStringT::operator! =  
 Určuje, zda dva řetězce jsou logicky nejsou stejné.  
  
```  
friend bool operator!=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator!=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator!=(const CStringT& str1, PCYSTR psz2) throw();
friend bool operator!=(const CStringT& str1, XCHAR ch2) throw();
friend bool operator!=(PCXSTR psz1, const CStringT& str2) throw();
friend bool operator!=(PCYSTR psz1, const CStringT& str2,) throw();
friend bool operator!=(XCHAR ch1, const CStringT& str2,) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `ch1`  
 ANSI nebo Unicode znak ke zřetězení řetězcem.  
  
 `ch2`  
 ANSI nebo Unicode znak ke zřetězení řetězcem.  
  
 `str1`  
 A `CStringT` pro porovnání.  
  
 `str2`  
 A `CStringT` pro porovnání.  
  
 `psz1`  
 Ukazatel na řetězce ukončené hodnotou null pro porovnání.  
  
 `psz2`  
 Ukazatel na řetězce ukončené hodnotou null pro porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Testy, pokud řetězec nebo znak na levé straně není rovno řetězec nebo znak na pravé straně.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#143](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_27.cpp)]  
  
##  <a name="operator_lt"></a>  CStringT::operator &lt;  
 Určuje, zda je řetězec na levé straně operátoru menší než řetězec na pravé straně.  
  
```  
friend bool operator<(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<(PCXSTR psz1, const CStringT& str2) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `str1`  
 A `CStringT` pro porovnání.  
  
 `str2`  
 A `CStringT` pro porovnání.  
  
 `psz1`  
 Ukazatel na řetězce ukončené hodnotou null pro porovnání.  
  
 `psz2`  
 Ukazatel na řetězce ukončené hodnotou null pro porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Lexicographical porovnání mezi řetězce, dokud znak znak:  
  
-   Nerovné najde odpovídající dva znaky a výsledek jejich porovnání se provede na základě porovnání mezi řetězce.  
  
-   Najde žádné nerovnosti, ale jeden řetězec obsahuje více znaků, než dalších a kratší řetězec, který je považován za méně než delší řetězec.  
  
-   Najde žádné nerovnosti a najde řetězce mít stejný počet znaků, a proto řetězce jsou stejné.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#144](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_28.cpp)]  
  
##  <a name="operator_gt"></a>  CStringT::operator &gt;  
 Určuje, zda je řetězec na levé straně operátoru větší než řetězec na pravé straně.  
  
```  
friend bool operator>(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>(PCXSTR psz1, const CStringT& str2) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `str1`  
 A `CStringT` pro porovnání.  
  
 `str2`  
 A `CStringT` pro porovnání.  
  
 `psz1`  
 Ukazatel na řetězce ukončené hodnotou null pro porovnání.  
  
 `psz2`  
 Ukazatel na řetězce ukončené hodnotou null pro porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Lexicographical porovnání mezi řetězce, dokud znak znak:  
  
-   Nerovné najde odpovídající dva znaky a výsledek jejich porovnání se provede na základě porovnání mezi řetězce.  
  
-   Najde žádné nerovnosti, ale jeden řetězec obsahuje více znaků, než dalších a kratší řetězec, který je považován za méně než delší řetězec.  
  
-   Najde žádné nerovnosti a najde, že řetězce mají stejný počet znaků, takže řetězce jsou stejné.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#145](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_29.cpp)]  
  
##  <a name="operator_lt_eq"></a>  CStringT::operator &lt;=  
 Určuje, zda je řetězec na levé straně operátoru menší než nebo rovna hodnotě řetězec na pravé straně.  
  
```  
friend bool operator<=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<=(PCXSTR psz1, const CStringT& str2) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `str1`  
 A `CStringT` pro porovnání.  
  
 `str2`  
 A `CStringT` pro porovnání.  
  
 `psz1`  
 Ukazatel na řetězce ukončené hodnotou null pro porovnání.  
  
 `psz2`  
 Ukazatel na řetězce ukončené hodnotou null pro porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Lexicographical porovnání mezi řetězce, dokud znak znak:  
  
-   Nerovné najde odpovídající dva znaky a výsledek jejich porovnání se provede na základě porovnání mezi řetězce.  
  
-   Najde žádné nerovnosti, ale jeden řetězec obsahuje více znaků, než dalších a kratší řetězec, který je považován za méně než delší řetězec.  
  
-   Najde žádné nerovnosti a najde, že řetězce mají stejný počet znaků, takže řetězce jsou stejné.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#146](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_30.cpp)]  
  
##  <a name="operator_gt_eq"></a>  CStringT::operator &gt;=  
 Určuje, zda řetězec na levé straně operátoru je větší než nebo rovna hodnotě řetězec na pravé straně.  
  
```  
friend bool operator>=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>=(PCXSTR psz1, const CStringT& str2) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `str1`  
 A `CStringT` pro porovnání.  
  
 `str2`  
 A `CStringT` pro porovnání.  
  
 `psz1`  
 Ukazatel na řetězec k porovnání.  
  
 `psz2`  
 Ukazatel na řetězec k porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Lexicographical porovnání mezi řetězce, dokud znak znak:  
  
-   Nerovné najde odpovídající dva znaky a výsledek jejich porovnání se provede na základě porovnání mezi řetězce.  
  
-   Najde žádné nerovnosti, ale jeden řetězec obsahuje více znaků, než dalších a kratší řetězec, který je považován za méně než delší řetězec.  
  
-   Najde žádné nerovnosti a najde, že řetězce mají stejný počet znaků, takže řetězce jsou stejné.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#147](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_31.cpp)]  
  
##  <a name="remove"></a>  CStringT::Remove  
 Odebere všechny výskyty zadaný znak z řetězce.  
  
```  
int Remove(XCHAR chRemove);
```  
  
### <a name="parameters"></a>Parametry  
 `chRemove`  
 Znak, který má být odebrána z řetězce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet znaků z řetězce odebrána. Hodnotu řetězce se nezmění.  
  
### <a name="remarks"></a>Poznámky  
 Porovnávání znaku se rozlišují malá a velká písmena.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#129](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_32.cpp)]  
  
##  <a name="replace"></a>  CStringT::Replace  
 Existují dvě verze `Replace`. První verze nahradí jednu nebo více kopií podřetězce pomocí jiné dílčí řetězec. Obě dílčích řetězců jsou ukončené hodnotou null. Druhá verze nahradí jednu nebo více kopií znaku pomocí jiné znak. Obě verze pracovat textová data uložená v `CStringT`.  
  
```  
int Replace(PCXSTR pszOld, PCXSTR pszNew);
int Replace(XCHAR chOld, XCHAR chNew);
```  
  
### <a name="parameters"></a>Parametry  
 `pszOld`  
 Ukazatel na řetězce ukončené hodnotou null budou nahrazeny `pszNew`.  
  
 `pszNew`  
 Ukazatel na řetězce ukončené hodnotou null, který nahrazuje `pszOld`.  
  
 `chOld`  
 Znak, který má být nahrazen `chNew`.  
  
 `chNew`  
 Znak nahrazení `chOld`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet nahrazené instancí znak nebo dílčí řetězec nebo nula, pokud se nezměnil řetězec.  
  
### <a name="remarks"></a>Poznámky  
 `Replace` Délka řetězce můžete změnit, protože `pszNew` a `pszOld` nemusíte mít stejnou délku a několik kopií původního dílčí řetězec můžete změnit tak, aby novým. Funkce provede malá a velká písmena shody.  
  
 Příklady `CStringT` instance jsou `CString`, `CStringA`, a `CStringW`.  
  
 Pro `CStringA`, `Replace` funguje s ANSI nebo vícebajtové znaky (MBCS). Pro `CStringW`, `Replace` pracuje s široké znaky.  
  
 Pro `CString`, znak dat je vybrán při kompilaci, založené na tom, jestli jsou definované konstanty v následující tabulce.  
  
|Definované konstantě|Znak datový typ|  
|----------------------|-------------------------|  
|`_UNICODE`|Široké znaky|  
|`_MBCS`|Vícebajtové znaky|  
|Ani|Jednobajtové znaky|  
|Obě|Nedefinovaná|  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#200](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_33.cpp)]  
  
##  <a name="reversefind"></a>  CStringT::ReverseFind  
 Vyhledá to `CStringT` objekt pro poslední shodu znaku.  
  
```  
int ReverseFind(XCHAR ch) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `ch`  
 Znak, který se má hledat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index založený na nule z poslední znak v tomto `CStringT` objekt, který odpovídá požadovaný znak nebo -1, pokud není nalezen znak.  
  
### <a name="remarks"></a>Poznámky  
 Funkce je podobná spuštění funkce `strrchr`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#130](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_34.cpp)]  
  
##  <a name="right"></a>  CStringT::Right  
 Extrahuje poslední (který je nejvíce vpravo) `nCount` znaky z tohoto `CStringT` objektu a vrátí kopii extrahované dílčí řetězec.  
  
```  
CStringT Right(int nCount) const; 
```  
  
### <a name="parameters"></a>Parametry  
 `nCount`  
 Počet znaků k extrakci z tohoto `CStringT` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CStringT` objekt, který obsahuje kopii zadaný rozsah znaků. Všimněte si, že vrácený `CStringT` objekt nesmí být prázdné.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `nCount` překračuje délku řetězce a pak je extrahován celý řetězec. `Right` je podobná základní `Right` funkce (s výjimkou toho, že indexy v Basic jsou od nuly).  
  
 Pro vícebajtových znakových sad (MBCS), `nCount` odkazuje na všech bajtů 8bitové znak; to znamená, realizace a záznam v jednom vícebajtových znaků, se počítají jako dva znaky.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#131](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_35.cpp)]  
  
##  <a name="setsysstring"></a>  CStringT::SetSysString  
 Přidělí `BSTR` na kterou odkazuje `pbstr` a zkopíruje obsah `CStringT` objektu do ní, včetně `NULL` znak.  
  
```  
BSTR SetSysString(BSTR* pbstr) const; 
```  
  
### <a name="parameters"></a>Parametry  
 `pbstr`  
 Ukazatel na řetězec znaků.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nový řetězec.  
  
### <a name="remarks"></a>Poznámky  
 V závislosti na obsah `CStringT` objektu, hodnota `BSTR` odkazuje `pbstr` můžete změnit. Funkce vyvolá `CMemoryException` pokud existuje nedostatek paměti.  
  
 Tato funkce se obvykle používá ke změně hodnoty řetězce předaná odkaz pro automatizaci.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#132](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_36.cpp)]  
  
##  <a name="spanexcluding"></a>  CStringT::SpanExcluding  
 Extrahuje znaky z řetězce od prvního znaku, které nejsou v sadě znaků identifikovaný `pszCharSet`.  
  
```  
CStringT SpanExcluding(PCXSTR pszCharSet) const; 
```  
  
### <a name="parameters"></a>Parametry  
 `pszCharSet`  
 Řetězec interpretovat jako sadu znaků.  
  
### <a name="return-value"></a>Návratová hodnota  
 Dílčí řetězec, který obsahuje znaky v řetězci, které nejsou v `pszCharSet`, počínaje první znak v řetězci a konče první znak v řetězec, který je k dispozici také v nalezen `pszCharSet` (to znamená, počínaje první znak argumentu řetězec a až do, ale s výjimkou prvního znaku v řetězci, který je nalezen `pszCharSet`). Vrátí celý řetězec, pokud žádné znak v `pszCharSet` nachází v řetězci.  
  
### <a name="remarks"></a>Poznámky  
 `SpanExcluding` extrahuje a vrátí všechny znaky předcházející první výskyt znak z `pszCharSet` (jinými slovy, znak z `pszCharSet` a nebudou zobrazeny všechny znaky v řetězci). Pokud žádné znak z `pszCharSet` se nachází v řetězci potom `SpanExcluding` vrátí celý řetězec.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#133](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_37.cpp)]  
  
##  <a name="spanincluding"></a>  CStringT::SpanIncluding  
 Extrahuje znaky z řetězce od prvního znaku, které jsou v sadě znaků identifikovaný `pszCharSet`.  
  
```  
CStringT SpanIncluding(PCXSTR pszCharSet) const; 
```  
  
### <a name="parameters"></a>Parametry  
 `pszCharSet`  
 Řetězec interpretovat jako sadu znaků.  
  
### <a name="return-value"></a>Návratová hodnota  
 Dílčí řetězec, který obsahuje znaky v řetězci, které jsou v `pszCharSet`, počínaje první znak v řetězci a končí, když se najde znak v řetězci, který není součástí `pszCharSet`. `SpanIncluding` Vrátí prázdný dílčí řetězec, pokud první znak v řetězci se nenachází v zadané sadě.  
  
### <a name="remarks"></a>Poznámky  
 Pokud první znak řetězce, který není ve znakové sadě pak `SpanIncluding` vrátí prázdný řetězec. V opačném případě vrátí posloupnosti po sobě jdoucích znaků, které jsou v sadě.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#134](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_38.cpp)]  
  
##  <a name="tokenize"></a>  CStringT::Tokenize  
 Vyhledá na další token v řetězci cíl  
  
```  
CStringT Tokenize(PCXSTR pszTokens, int& iStart) const; 
```  
  
### <a name="parameters"></a>Parametry  
 `pszTokens`  
 Řetězec obsahující tokenu oddělovače. Pořadí těchto oddělovače není důležité.  
  
 `iStart`  
 Index založený na nule hledání začněte.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CStringT` objekt obsahující aktuální hodnota tokenu.  
  
### <a name="remarks"></a>Poznámky  
 `Tokenize` Funkce najde v řetězci cíl na další token. Sadu znaků `pszTokens` Určuje možné oddělovače token, který má být nalezena. Při každém volání `Tokenize` funkce začíná na `iStart`, přeskočí úvodní oddělovače a vrátí `CStringT` objekt obsahující aktuální token, který je řetězec znaků až další znak oddělovače. Hodnota `iStart` se aktualizuje na pozici následující ukončovací znak oddělovač nebo -1, pokud byl dosažen konec řetězec. Další tokeny, lze zjistit mimo zbytek cílový řetězec řadou volání `Tokenize`pomocí `iStart` ke sledování kde v řetězci na další token je možné načíst. Pokud nejsou žádné další tokeny funkce vrátí prázdný řetězec a `iStart` bude nastavena na hodnotu -1.  
  
 Na rozdíl od CRT tokenizaci funkce jako [strtok_s –, _strtok_s_l –, wcstok_s –, _wcstok_s_l –, _mbstok_s –, _mbstok_s_l –](../../c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md), `Tokenize` nedojde ke změně cílový řetězec.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#135](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_39.cpp)]  
  
### <a name="remarks"></a>Poznámky  
 Výstup z tohoto příkladu je následující:  
  
 `Resulting Token: First`  
  
 `Resulting Token: Second`  
  
 `Resulting Token: Third`  
  
##  <a name="trim"></a>  CStringT::Trim  
 Ořízne počátečních a koncových znaků z řetězce.  
  
```  
CStringT& Trim(XCHAR chTarget);
CStringT& Trim(PCXSTR pszTargets);
CStringT& Trim();
```  
  
### <a name="parameters"></a>Parametry  
 `chTarget`  
 Znak cíl, který má být oříznut.  
  
 `pszTargets`  
 Ukazatel na řetězec obsahující znaky cíl, které mají být oříznut. Všechny úvodní a koncové znaky v `pszTarget` se ořízne z `CStringT` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí řetězec oříznutý.  
  
### <a name="remarks"></a>Poznámky  
 Odebere všechny úvodní a koncové výskyty jednu z těchto možností:  
  
-   Znak určeného `chTarget.`  
  
-   Všechny znaky v řetězci určeného nalezena `pszTargets.`  
  
-   Prázdné znaky.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#136](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_40.cpp)]  
  
### <a name="remarks"></a>Poznámky  
 Výstup z tohoto příkladu je následující:  
  
 `Before: "******Soccer is best, but liquor is quicker!!!!!"`  
  
 `After : "Soccer is best, but liquor is quicker"`  
  
##  <a name="trimleft"></a>  CStringT::TrimLeft  
 Ořízne úvodní znaků z řetězce.  
  
```  
CStringT& TrimLeft(XCHAR chTarget);
CStringT& TrimLeft(PCXSTR pszTargets);
CStringT& TrimLeft();
```  
  
### <a name="parameters"></a>Parametry  
 `chTarget`  
 Znak cíl, který má být oříznut.  
  
 `pszTargets`  
 Ukazatel na řetězec obsahující znaky cíl, které mají být oříznut. Všechny výskyty úvodní znaků `pszTarget` se ořízne z `CStringT` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výsledná oříznut řetězec.  
  
### <a name="remarks"></a>Poznámky  
 Odebere všechny úvodní a koncové výskyty jednu z těchto možností:  
  
-   Znak určeného `chTarget.`  
  
-   Všechny znaky v řetězci určeného nalezena `pszTargets.`  
  
-   Prázdné znaky.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#137](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_41.cpp)]  
  
##  <a name="trimright"></a>  CStringT::TrimRight  
 Ořízne koncových znaků z řetězce.  
  
```  
CStringT& TrimRight(XCHAR chTarget);
CStringT& TrimRight(PCXSTR pszTargets);
CStringT& TrimRight();
```  
  
### <a name="parameters"></a>Parametry  
 `chTarget`  
 Znak cíl, který má být oříznut.  
  
 `pszTargets`  
 Ukazatel na řetězec obsahující znaky cíl, které mají být oříznut. Všechny koncové znaky v `pszTarget` se ořízne z `CStringT` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `CStringT` objekt, který obsahuje oříznutý řetězec.  
  
### <a name="remarks"></a>Poznámky  
 Odebere koncové výskyty jednu z následujících:  
  
-   Znak určeného `chTarget.`  
  
-   Všechny znaky v řetězci určeného nalezena `pszTargets.`  
  
-   Prázdné znaky.  
  
 `CStringT& TrimRight(XCHAR chTarget)` Verze přijímá jeden parametr znaku a odebere všechny kopie této znaků z konce `CStringT` řetězcová data. Začne od konce řetězce a funguje směrem dopředu. Zastaví, pokud se najde jiný znak nebo pokud `CSTringT` dojde textová data.  
  
 `CStringT& TrimRight(PCXSTR pszTargets)` Verze přijímá ukončené hodnotou null řetězec, který obsahuje všechny jiné znaky pro vyhledávání. Odebere všechny kopie těchto znaků `CStringT` objektu. Začne na konci řetězce a funguje směrem dopředu. Zastaví, pokud najde znak, který se nenachází v cílový řetězec, nebo když `CStringT` dojde textová data. Nepokusí tak, aby odpovídaly celý cílový řetězec, který má dílčí řetězec na konci `CStringT`.  
  
 `CStringT& TrimRight()` Verze nevyžaduje žádné parametry. Se ořízne žádné koncové znaky prázdných znaků z konce `CStringT` řetězec. Prázdné znaky mohou být karty, mezery nebo zalomením řádku.  
  
-  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#138](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_42.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [ATL a MFC sdílené třídy](../../atl-mfc-shared/atl-mfc-shared-classes.md)   
 [CSimpleStringT – třída](../../atl-mfc-shared/reference/csimplestringt-class.md)


