---
title: Cstringt – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/18/2018
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
ms.openlocfilehash: f2d31d24007da1ec279e9c9762158b549e83d114
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49809119"
---
# <a name="cstringt-class"></a>Cstringt – třída

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

*BaseType*<br/>
Znakový typ třída string. Může být jedna z následujících akcí:

- **Char** (pro řetězce znaků ANSI).

- **wchar_t** (pro řetězce znaků Unicode).

- TCHAR (pro řetězce znaků ANSI a Unicode).

*StringTraits*<br/>
Určuje, zda třída string, potřebuje podpora knihovny Run-Time C (CRT) a kde jsou umístěny prostředky řetězců. Může být jedna z následujících akcí:

- **StrTraitATL < wchar_t** &#124; `char` &#124; **TCHAR, ChTraitsCRT < wchar_t** &#124; `char` &#124; **TCHAR >>**

   Třída vyžaduje podporu CRT a vyhledá zdrojové řetězce v modul specifikovaný údajem `m_hInstResource` (člen třídy modulu aplikace).

- **StrTraitATL < wchar_t** &#124; `char` &#124; **TCHAR, ChTraitsOS < wchar_t** &#124; `char` &#124; **TCHAR >>**

   Třída nevyžaduje CRT podpory a vyhledá zdrojové řetězce v modul specifikovaný údajem `m_hInstResource` (člen třídy modulu aplikace).

- **StrTraitMFC < wchar_t** &#124; `char` &#124; **TCHAR, ChTraitsCRT < wchar_t** &#124; `char` &#124; **TCHAR >>**

   Třída vyžaduje podporu CRT a vyhledá zdrojové řetězce pomocí standardní vyhledávacího algoritmu knihovny MFC.

- **StrTraitMFC < wchar_t** &#124; `char` &#124; **TCHAR, ChTraitsOS < wchar_t** &#124; `char` &#124; **TCHAR >>**

   Třída nevyžaduje CRT podpory a vyhledá zdrojové řetězce pomocí standardní vyhledávacího algoritmu knihovny MFC.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CStringT::CStringT](#cstringt)|Vytvoří `CStringT` objekt různými způsoby.|
|[CStringT:: ~ CStringT](#_dtorcstringt)|Odstraní `CStringT` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CStringT::AllocSysString](#allocsysstring)|Přidělí BSTR z `CStringT` data.|
|[CStringT::AnsiToOem](#ansitooem)|Provede konverzi na místě ze ANSI znakovou sadu na znakové sady OEM.|
|[CStringT::AppendFormat](#appendformat)|Připojí formátovaná data do existujícího `CStringT` objektu.|
|[CStringT::Collate](#collate)|Porovná dva řetězce (velká a malá písmena, používá informace specifické pro národní prostředí).|
|[CStringT::CollateNoCase](#collatenocase)|Porovná dva řetězce (malá a velká písmena, používá informace specifické pro národní prostředí).|
|[CStringT::Compare](#compare)|Porovná dva řetězce (rozlišuje velikost písmen).|
|[CStringT::CompareNoCase](#comparenocase)|Porovná dva řetězce (malých písmen).|
|[CStringT::Delete](#delete)|Odstraní znak nebo znaky z řetězce.|
|[CStringT::Find](#find)|Vyhledá nebo podřetězec ve větším řetězci.|
|[CStringT::FindOneOf](#findoneof)|Najde první odpovídající znak ze sady.|
|[CStringT::Format](#format)|Formáty řetězce jako `sprintf` nepodporuje.|
|[CStringT::FormatMessage](#formatmessage)|Formátuje řetězec zprávy.|
|[CStringT::FormatMessageV](#formatmessagev)|Formáty řetězce zprávy pomocí Proměnný seznam argumentů.|
|[CStringT::FormatV](#formatv)|Formáty řetězce, pomocí seznamu proměnných, argumentů.|
|[CStringT::GetEnvironmentVariable](#getenvironmentvariable)|Nastaví řetězec na hodnotu proměnné zadaného prostředí.|
|[CStringT::Insert](#insert)|Vloží znak nebo podřetězec v daném indexu v rámci řetězce.|
|[CStringT::Left](#left)|Extrahuje levou část řetězce.|
|[CStringT::LoadString](#loadstring)|Načte existující `CStringT` objekt z prostředků Windows.|
|[CStringT::MakeLower](#makelower)|Převede všechny znaky v tomto řetězci na malá písmena.|
|[CStringT::MakeReverse](#makereverse)|Vrátí řetězec.|
|[CStringT::MakeUpper](#makeupper)|Převede všechny znaky v tomto řetězci na velká písmena.|
|[CStringT::Mid](#mid)|Extrahuje prostřední část řetězce.|
|[CStringT::OemToAnsi](#oemtoansi)|Provede konverzi na místě od výrobce OEM znakové sadě znakovou sadu ANSI.|
|[CStringT::Remove](#remove)|Odstraní uvedené znaků z řetězce.|
|[CStringT::Replace](#replace)|Nahradí uvedené znaků s jinými znaky.|
|[CStringT::ReverseFind](#reversefind)|Vyhledá znaků ve větším řetězci; začíná od konce.|
|[CStringT::Right](#right)|Extrahuje pravou část řetězce.|
|[CStringT::SetSysString](#setsysstring)|Nastaví existující objekt BSTR s daty z `CStringT` objektu.|
|[CStringT::SpanExcluding](#spanexcluding)|Extrahuje znaky z řetězce, počínaje první znaky, které nejsou v sadě znaků identifikovaný `pszCharSet`.|
|[CStringT::SpanIncluding](#spanincluding)|Extrahuje podřetězec, který obsahuje pouze znaky v objektu set.|
|[CStringT::Tokenize](#tokenize)|Extrahuje zadaný tokeny v cílovém řetězci.|
|[CStringT::Trim](#trim)|Ořízne všechny úvodní a koncové prázdné znaky z řetězce.|
|[CStringT::TrimLeft](#trimleft)|Ořízne počáteční prázdné znaky z řetězce.|
|[CStringT::TrimRight](#trimright)|Ořízne koncové prázdné znaky z řetězce.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor =](#operator_eq)|Přiřadí novou hodnotu `CStringT` objektu.|
|[CStringT::operator +](#operator_add)|Spojuje dva řetězce nebo řetězce a znak.|
|[CStringT::operator +=](#operator_add_eq)|Zřetězí nový řetězec na konci existujícího řetězce.|
|[CStringT::operator ==](#operator_eq_eq)|Určuje, jestli jsou dva řetězce logicky stejné.|
|[CStringT::operator! =](#operator_neq)|Určuje, jestli dva řetězce jsou logicky nejsou stejné.|
|[CStringT::operator &lt;](#operator_lt)|Určuje, zda je řetězec na levé straně operátoru menší než do řetězce na pravé straně.|
|[CStringT::operator &gt;](#operator_gt)|Určuje, zda je řetězec na levé straně operátoru větší než řetězec na pravé straně.|
|[CStringT::operator &lt;=](#operator_lt_eq)|Určuje, zda řetězec na levé straně operátoru menší než nebo rovno řetězci na pravé straně.|
|[CStringT::operator &gt;=](#operator_gt_eq)|Určuje, zda je řetězec na levé straně operátoru větší než nebo rovno řetězci na pravé straně.|

## <a name="remarks"></a>Poznámky

`CStringT` dědí z [csimplestringt – třída](../../atl-mfc-shared/reference/csimplestringt-class.md). Pokročilé funkce, jako je znak manipulaci, řazení a vyhledávání, implementují `CStringT`.

> [!NOTE]
> `CStringT` objekty jsou schopny vyvolat výjimky. K tomu dojde při `CStringT` objekt nedostatek paměti z jakéhokoli důvodu.

A `CStringT` objekt obsahuje proměnlivou délkou posloupnost znaků. `CStringT` poskytuje funkce a operátory pomocí syntaxe podobné Basic. Zřetězení a operátory porovnání, společně s Správa zjednodušené paměti `CStringT` objekty, které jsou jednodušší než pole běžný znak.

> [!NOTE]
>  I když je možné vytvořit `CStringT` instancí, které obsahují vložené znaky null, doporučujeme před ním. Při volání metody a operátory na `CStringT` objektů, které obsahují vložené znaky null může způsobit nežádoucí výsledky.

S použitím různých kombinací `BaseType` a `StringTraits` parametry, `CStringT` můžou pocházet v následujících typů, které jsou předem definoval knihovny ATL – objekty.

Při použití v aplikaci knihovny ATL:

`CString`, `CStringA`, a `CStringW` byly exportovány z knihovny MFC DLL (MFC90. Knihovny DLL), nikdy od uživatele knihovny DLL. To se provádí, aby se zabránilo `CStringT` z je definovaná víckrát.

> [!NOTE]
>  Pokud váš kód obsahuje alternativní řešení pro chyby, která je popsána v [export řetězec třídy pomocí CStringT](../../atl-mfc-shared/exporting-string-classes-using-cstringt.md), měli byste odebrat tento kód. Už je nepotřebujete.

Následující typy řetězců jsou dostupné v rámci aplikace založené na knihovně MFC:

|Cstringt – typ|Deklarace|
|-------------------|-----------------|
|`CStringA`|Znak ANSI zadejte řetězec s podporou CRT.|
|`CStringW`|Znak Unicode zadejte řetězec s podporou CRT.|
|`CString`|ANSI a Unicode typy znaků s podporou CRT.|

Následující typy řetězců jsou k dispozici v projektech, kde je definován ATL_CSTRING_NO_CRT:

|Cstringt – typ|Deklarace|
|-------------------|-----------------|
|`CAtlStringA`|Znak ANSI zadejte řetězec bez podpory CRT.|
|`CAtlStringW`|Znak Unicode zadejte řetězec bez podpory CRT.|
|`CAtlString`|ANSI a Unicode typy znaků bez podpory CRT.|

Následující typy řetězců jsou k dispozici v projektech, kde není definován ATL_CSTRING_NO_CRT:

|Cstringt – typ|Deklarace|
|-------------------|-----------------|
|`CAtlStringA`|Znak ANSI zadejte řetězec s podporou CRT.|
|`CAtlStringW`|Znak Unicode zadejte řetězec s podporou CRT.|
|`CAtlString`|ANSI a Unicode typy znaků s podporou CRT.|

`CString` objekty také mají následující vlastnosti:

- `CStringT` objekty můžou jako výsledek operace sřetězení růst.

- `CStringT` objekty podle "hodnota sémantiky." Představte si, že `CStringT` objektu jako vytvoření skutečného řetězce, nikoli jako ukazatel na řetězec.

- Můžete volně nahradit `CStringT` objekty pro `PCXSTR` argumenty funkce.

- Správa vlastní paměti pro řetězec vyrovnávací paměti. Další informace najdete v tématu [Správa paměti a CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="cstringt-predefined-types"></a>Cstringt – předdefinované typy

Protože `CStringT` používá argument šablony pro definování tyto typy znaků (buď [wchar_t](../../c-runtime-library/standard-types.md) nebo [char](../../c-runtime-library/standard-types.md)) podporovány typy parametrů metody mohou být složité čas od času. Pro zjednodušení tento problém, sada předdefinovaných typů definovaná a použitá v průběhu `CStringT` třídy. V následující tabulce jsou uvedeny různé typy:

|Název|Popis|
|----------|-----------------|
|`XCHAR`|Jeden znak (buď **wchar_t** nebo **char**) se stejným typem znak jako `CStringT` objektu.|
|`YCHAR`|Jeden znak (buď **wchar_t** nebo **char**) s opačný typ znaku, jako `CStringT` objektu.|
|`PXSTR`|Ukazatel na řetězec znaků (buď **wchar_t** nebo **char**) se stejným typem znak jako `CStringT` objektu.|
|`PYSTR`|Ukazatel na řetězec znaků (buď **wchar_t** nebo **char**) s opačný typ znaku, jako `CStringT` objektu.|
|`PCXSTR`|Ukazatel **const** řetězec znaků, ale (buď **wchar_t** nebo **char**) se stejným typem znak jako `CStringT` objektu.|
|`PCYSTR`|Ukazatel na **const** řetězec znaků (buď **wchar_t** nebo **char**) s opačný typ znaku, jako `CStringT` objektu.|

> [!NOTE]
>  Kód, který dřív používal nedokumentované metody `CString` (například `AssignCopy`) nutné vyměnit za kód, který používá tyto metody zdokumentovaných `CStringT` (jako `GetBuffer` nebo `ReleaseBuffer`). Tyto metody jsou zděděny ze `CSimpleStringT`.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Csimplestringt –](../../atl-mfc-shared/reference/csimplestringt-class.md)

`CStringT`

## <a name="requirements"></a>Požadavky

|Záhlaví|Použití pro|
|------------|-------------|
|cstringt.h|Objekty řetězec pouze knihovny MFC|
|atlstr.h|Non-MFC řetězcových objektů|

##  <a name="allocsysstring"></a>  CStringT::AllocSysString

Přiděluje řetězci automatizace kompatibilního typu BSTR a kopíruje obsah `CStringT` do objektu, včetně ukončujícího znaku null.

```
BSTR AllocSysString() const;  
```

### <a name="return-value"></a>Návratová hodnota

Nově přidělenou řetězec.

### <a name="remarks"></a>Poznámky

V aplikacích MFC [cmemoryexception – třída](../../mfc/reference/cmemoryexception-class.md) je vyvolána, pokud existuje dostatek paměti. V aplikacích knihovny ATL [catlexception –](../../atl/reference/catlexception-class.md) je vyvolána výjimka. Tato funkce se obvykle používá k vrácení řetězce pro automatizaci.

Obecně Pokud se tento řetězec je předán do funkce modelu COM jako [in] vyžaduje parametr, pak by se volajícím uvolnit řetězec. To můžete udělat pomocí [SysFreeString](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-sysfreestring), jak je popsáno v sadě Windows SDK. Další informace najdete v tématu [Allocating a uvolňování paměti pro BSTR](../../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md).

Další informace o funkcích přidělení OLE ve Windows najdete v tématu [SysAllocString](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-sysallocstring) v sadě Windows SDK.  


### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CStringT::AllocSysString`.

[!code-cpp[NVC_ATLMFC_Utilities#105](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_1.cpp)]

##  <a name="ansitooem"></a>  CStringT::AnsiToOem

Převede všechny znaky v tomto `CStringT` objekt z ANSI znakovou sadu na znakové sady OEM.

```
void AnsiToOem();
```

### <a name="remarks"></a>Poznámky

Funkce není k dispozici, pokud je _UNICODE definováno.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#106](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_2.cpp)]

##  <a name="appendformat"></a>  CStringT::AppendFormat

Připojí formátovaná data do existujícího `CStringT` objektu.

```
void __cdecl AppendFormat(PCXSTR pszFormat, [, argument] ...);
void __cdecl AppendFormat(UINT nFormatID, [, argument] ...);
```

### <a name="parameters"></a>Parametry

*pszFormat*<br/>
Řetězec řízení formátu.

*nFormatID*<br/>
Identifikátor prostředku řetězců obsahující řetězec řízení formátu.

*Argument*<br/>
Volitelné argumenty

### <a name="remarks"></a>Poznámky

Tato funkce formátuje a připojí řadu znaků a hodnot v `CStringT`. Jednotlivé volitelné argumenty (pokud existuje) je převeden a připojí podle odpovídající specifikace formátu v *pszFormat* nebo z řetězce prostředku označeném identifikátorem *nFormatID*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#107](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_3.cpp)]

##  <a name="collate"></a>  CStringT::Collate

Porovná dva řetězce pomocí funkce obecného textu `_tcscoll`.

```
int Collate(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Další řetězec použitý pro porovnání.

### <a name="return-value"></a>Návratová hodnota

Nula v případě, že jsou řetězce identické, < 0, pokud tento `CStringT` objekt je menší než *psz*, nebo > 0, pokud tento `CStringT` objekt je větší než *psz*.

### <a name="remarks"></a>Poznámky

Obecná textová funkce `_tcscoll`, který je definován v TCHAR. H, odpovídá buď `strcoll`, `wcscoll`, nebo `_mbscoll`, v závislosti na znakové sady, který je definován v době kompilace. Každá funkce provádí velká a malá písmena porovnání řetězců podle kódové stránky, aktuálně používá. Další informace najdete v tématu [strcoll – wcscoll –, _mbscoll –, _strcoll_l –, _wcscoll_l –, _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md).

##  <a name="collatenocase"></a>  CStringT::CollateNoCase

Porovná dva řetězce pomocí funkce obecného textu `_tcscoll`.

```
int CollateNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Další řetězec použitý pro porovnání.

### <a name="return-value"></a>Návratová hodnota

Nula, pokud jsou řetězce identické (bez rozlišování případů), < 0, pokud tento `CStringT` objekt je menší než *psz* (bez rozlišování případů), nebo > 0, pokud tento `CStringT` objekt je větší než *psz* (bez rozlišování případů).

### <a name="remarks"></a>Poznámky

Obecná textová funkce `_tcscoll`, který je definován v TCHAR. H, odpovídá buď `stricoll`, `wcsicoll`, nebo `_mbsicoll`, v závislosti na znakové sady, který je definován v době kompilace. Každá funkce provádí porovnávání řetězců, podle kódové stránky, aktuálně používán. Další informace najdete v tématu [strcoll – wcscoll –, _mbscoll –, _strcoll_l –, _wcscoll_l –, _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#109](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_4.cpp)]

##  <a name="compare"></a>  CStringT::Compare

Porovná dva řetězce (rozlišuje velikost písmen).

```
int Compare(PCXSTR psz) const; 
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Další řetězec použitý pro porovnání.

### <a name="return-value"></a>Návratová hodnota

Nula v případě, že jsou řetězce identické, < 0, pokud tento `CStringT` objekt je menší než *psz*, nebo > 0, pokud tento `CStringT` objekt je větší než *psz*.

### <a name="remarks"></a>Poznámky

Obecná textová funkce `_tcscmp`, který je definován v TCHAR. H, odpovídá buď `strcmp`, `wcscmp`, nebo `_mbscmp`, v závislosti na znakové sady, který je definován v době kompilace. Každá funkce provádí porovnání řetězců velká a malá písmena a není ovlivněná národním prostředím. Další informace najdete v tématu [strcmp – wcscmp –, _mbscmp –](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md).

Pokud řetězec obsahuje vložené znaky null, pro účely porovnání řetězce se považuje za zkrácen na první vložený znak null.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CStringT::Compare`.

[!code-cpp[NVC_ATLMFC_Utilities#110](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_5.cpp)]

##  <a name="comparenocase"></a>  CStringT::CompareNoCase

Porovná dva řetězce (malých písmen).

```
int CompareNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Další řetězec použitý pro porovnání.

### <a name="return-value"></a>Návratová hodnota

Nula, pokud jsou řetězce identické (bez rozlišování případů), < 0, pokud tento `CStringT` objekt je menší než *psz* (bez rozlišování případů), nebo > 0, pokud tento `CStringT` objekt je větší než *psz* (bez rozlišování případů).

### <a name="remarks"></a>Poznámky

Obecná textová funkce `_tcsicmp`, který je definován v TCHAR. H, odpovídá buď `_stricmp`, `_wcsicmp` nebo `_mbsicmp`, v závislosti na znakové sady, který je definován v době kompilace. Každá funkce provádí porovnávání řetězců. Porovnání závisí na LC_CTYPE aspekt národní prostředí, ale ne LC_COLLATE. Další informace najdete v tématu [_stricmp – _wcsicmp –, _mbsicmp –, _stricmp_l –, _wcsicmp_l –, _mbsicmp_l –](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md).

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

*pch*<br/>
Ukazatel na pole znaků o délce *nLength*, nejsou zakončené znakem null.

*nLength*<br/>
Počet znaků v *pch*.

*ch*<br/>
Jeden znak.

*pszSrc*<br/>
Řetězec zakončený hodnotou null ke zkopírování do tohoto `CStringT` objektu.

*pStringMgr*<br/>
Ukazatel na správce paměti pro `CStringT` objektu. Další informace o `IAtlStringMgr` a správa paměti pro `CStringT`, naleznete v tématu [Správa paměti pomocí CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

*strSrc*<br/>
Existující `CStringT` objektu, které se mají zkopírovat do tohoto `CStringT` objektu. Další informace o `CThisString` a `CThisSimpleString`, naleznete v části poznámky.

*varSrc*<br/>
Varianty objektu, které se mají zkopírovat do tohoto `CStringT` objektu.

*BaseType*<br/>
Znakový typ třída string. Může být jedna z následujících akcí:

**Char** (pro řetězce znaků ANSI).

**wchar_t** (pro řetězce znaků Unicode).

TCHAR (pro řetězce znaků ANSI a Unicode).

*bMFCDLL*<br/>
Logická hodnota, která určuje, zda je projekt knihovny MFC DLL (pravda) nebo ne (FALSE).

*SystemString*<br/>
Musí být `System::String`, a projekt musí být kompilována s parametrem/CLR.

*pString*<br/>
Popisovač `CStringT` objektu.

### <a name="remarks"></a>Poznámky

Protože se konstruktory kopírují do nového úložiště přidělené vstupních dat, je třeba si uvědomit, tato paměť, může způsobit výjimky. Všimněte si, že některé z těchto konstruktorů fungovat jako funkce pro převod. Díky tomu můžete nahradit, například LPTSTR kde `CStringT` byl očekáván objekt.

- `CStringT`( `LPCSTR` `lpsz` ): Vytvoří Unicode `CStringT` z řetězce ANSI. Můžete také použít tento konstruktor se načíst prostředek řetězce, jak je znázorněno v následujícím příkladu.

- `CStringT(` `LPCWSTR` `lpsz` ): Konstrukce `CStringT` z řetězce Unicode.

- `CStringT`( `const unsigned char*` `psz` ): Umožňuje vytvářet `CStringT` z ukazatele na **unsigned char**.

> [!NOTE]
>  Definujte makro _CSTRING_DISABLE_NARROW_WIDE_CONVERSION vypnout řetězec implicitní převod mezi řetězce ANSI a Unicode. Makro se vyloučí z kompilace konstruktory, které podporují převod.

Všimněte si, že *strSrc* parametr může být buď `CStringT` nebo `CThisSimpleString` objektu. Pro `CStringT`, použijte jeden z jeho výchozí instancí (`CString`, `CStringA`, nebo `CStringW`); pro `CThisSimpleString`, použití **to** ukazatele. `CThisSimpleString` deklaruje instanci [csimplestringt – třída](../../atl-mfc-shared/reference/csimplestringt-class.md), což je menší třídu řetězec s míň vestavěnou funkci než `CStringT` třídy.

Přetižte operátor `CSimpleStringT<>&()` sestaví `CStringT` objektu z `CSimpleStringT` deklarace.

> [!NOTE]
>  I když je možné vytvořit `CStringT` instancí, které obsahují vložené znaky null, doporučujeme před ním. Při volání metody a operátory na `CStringT` objektů, které obsahují vložené znaky null může způsobit nežádoucí výsledky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#112](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_7.cpp)]

##  <a name="_dtorcstringt"></a>  CStringT:: ~ CStringT

Odstraní `CStringT` objektu.

```
~CStringT() throw();
```

### <a name="remarks"></a>Poznámky

Odstraní `CStringT` objektu.

##  <a name="delete"></a>  CStringT::Delete

Odstraní znak nebo znaky z řetězce, počínaje znak na daném indexu.

```
int Delete(int iIndex, int nCount = 1);
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
Z nuly vycházející index prvního znaku v `CStringT` objekt odstranit.

*nCount*<br/>
Počet znaků, které mají být odebrány.

### <a name="return-value"></a>Návratová hodnota

Délka změněný řetězec.

### <a name="remarks"></a>Poznámky

Pokud *nCount* je delší, než řetězec a zbytek řetězce se odeberou.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#113](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_8.cpp)]

```Output  
Before: Soccer is best,
    but hockey is quicker!  
After: Soccer best,
    but hockey is quicker!  
```

##  <a name="find"></a>  CStringT::Find

Vyhledá první shoda znak nebo podřetězec tento řetězec.

```
int Find(PCXSTR pszSub, int iStart=0) const throw();
int Find(XCHAR ch, int iStart=0) const throw();
```

### <a name="parameters"></a>Parametry

*pszSub*<br/>
Podřetězec hledaný.

*iStart*<br/>
Index znaku v řetězci zahájíte hledání s použitím nebo 0 pro začít od začátku.

*ch*<br/>
Jeden znak pro hledání.

### <a name="return-value"></a>Návratová hodnota

Z nuly vycházející index prvního znaku v tomto `CStringT` objekt, který odpovídá požadovaný dílčí řetězec nebo znaky; -1, pokud nebyl nalezen dílčí řetězec nebo znak.

### <a name="remarks"></a>Poznámky

Funkce je přetížená tak, aby přijímal i jednotlivé znaky (podobné funkci run-time `strchr`) a řetězce (podobně jako `strstr`).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#114](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_9.cpp)]

##  <a name="findoneof"></a>  CStringT::FindOneOf

Prohledá tento řetězec prvního znaku, který odpovídá libovolnému znaku součástí *pszCharSet*.

```
int FindOneOf(PCXSTR pszCharSet) const throw();
```

### <a name="parameters"></a>Parametry

*pszCharSet*<br/>
Řetězec obsahující znaky pro porovnání.

### <a name="return-value"></a>Návratová hodnota

Z nuly vycházející index prvního znaku v tomto řetězci, které jsou uvedené taky v *pszCharSet*; -1, pokud není nalezena žádná shoda.

### <a name="remarks"></a>Poznámky

Vyhledá první výskyt některý ze znaků v *pszCharSet*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#115](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_10.cpp)]

##  <a name="format"></a>  CStringT::Format

Zapisuje formátovaná data do `CStringT` ve stejném způsobu, jakým [sprintf_s –](../../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md) formáty dat do pole stylu C znaků.

```
void __cdecl Format(UINT nFormatID, [, argument]...);
void __cdecl Format(PCXSTR pszFormat,  [, argument] ...);
```

### <a name="parameters"></a>Parametry

*nFormatID*<br/>
Identifikátor prostředku řetězců obsahující řetězec řízení formátu.

*pszFormat*<br/>
Řetězec řízení formátu.

*Argument*<br/>
Volitelné argumenty

### <a name="remarks"></a>Poznámky

Tato funkce formátuje a ukládá řadu znaků a hodnot v `CStringT`. Jednotlivé volitelné argumenty (pokud existuje) je převeden a uložen podle odpovídající specifikace formátu v *pszFormat* nebo z řetězce prostředku označeném identifikátorem *nFormatID*.

Volání selže, pokud samotného objektu řetězce se nabízí jako parametr `Format`. Například následující kód způsobí nepředvídatelné výsledky:

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

*nFormatID*<br/>
Identifikátor prostředku řetězce, který obsahuje text neformátovaný zprávy.

*pszFormat*<br/>
Odkazuje na řetězec řízení formátu. Bude vyhledávat vloží a ve formátu odpovídajícím způsobem. Formátovací řetězec je podobný funkci run-time *printf*– styl řetězce formátu, s výjimkou umožňuje parametry, které má být vložen v libovolném pořadí.

*Argument*<br/>
Volitelné argumenty

### <a name="remarks"></a>Poznámky

Funkce vyžaduje definici zprávy jako vstup. Je určeno definicí zpráv *pszFormat* nebo z řetězce prostředku označeném identifikátorem *nFormatID*. Funkce zkopíruje text formátovaná zpráva `CStringT` objektu, zpracování některé vložené vložit pořadí, pokud o to požádá.

> [!NOTE]
> `FormatMessage` pokusy o přidělení paměti systému pro nově formátovaný řetězec. Pokud tento pokus selže, je automaticky vyvolána výjimka paměti.

Každý insert musí mít odpovídající parametr následující *pszFormat* nebo *nFormatID* parametru. V textu zprávy se podporují několik řídicí sekvence pro dynamicky formátování zprávy. Další informace najdete v článku Windows [FormatMessage](/windows/desktop/api/winbase/nf-winbase-formatmessage) funkce v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#118](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_13.cpp)]

##  <a name="formatmessagev"></a>  CStringT::FormatMessageV

Formáty řetězce zprávy pomocí Proměnný seznam argumentů.

```
void FormatMessageV(PCXSTR pszFormat, va_list* pArgList);
```

### <a name="parameters"></a>Parametry

*pszFormat*<br/>
Odkazuje na řetězec řízení formátu. Bude vyhledávat vloží a ve formátu odpovídajícím způsobem. Formátovací řetězec je podobný funkci run-time `printf`– styl řetězce formátu, s výjimkou umožňuje parametry, které má být vložen v libovolném pořadí.

*pArgList*<br/>
Ukazatel na seznam argumentů.

### <a name="remarks"></a>Poznámky

Funkce vyžaduje definici zprávy jako vstup, určené *pszFormat*. Funkce zkopíruje formátovaného textu a proměnných seznam argumentů, které mají `CStringT` objektu, zpracování některé vložené vložit pořadí, pokud o to požádá.

> [!NOTE]
> `FormatMessageV` volání [CStringT::FormatMessage](#formatmessage), která se pokusí přidělení paměti systému pro nově formátovaný řetězec. Pokud tento pokus selže, je automaticky vyvolána výjimka paměti.

Další informace najdete v článku Windows [FormatMessage](/windows/desktop/api/winbase/nf-winbase-formatmessage) funkce v sadě Windows SDK.

##  <a name="formatv"></a>  CStringT::FormatV

Formáty řetězce zprávy pomocí Proměnný seznam argumentů.

```
void FormatV(PCXSTR pszFormat, va_list args);
```

### <a name="parameters"></a>Parametry

*pszFormat*<br/>
Odkazuje na řetězec řízení formátu. Bude vyhledávat vloží a ve formátu odpovídajícím způsobem. Formátovací řetězec je podobný funkci run-time `printf`– styl řetězce formátu, s výjimkou umožňuje parametry, které má být vložen v libovolném pořadí.

*argumenty*<br/>
Ukazatel na seznam argumentů.

### <a name="remarks"></a>Poznámky

Zapíše formátovaný řetězec a seznam argumentů proměnné `CStringT` řetězec ve stejném způsobu, jakým `vsprintf_s` formáty dat do pole stylu C znaků.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#119](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_14.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#120](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_15.cpp)]

##  <a name="getenvironmentvariable"></a>  CStringT::GetEnvironmentVariable

Nastaví řetězec na hodnotu proměnné zadaného prostředí.

```
BOOL GetEnvironmentVariable(PCXSTR pszVar);
```

### <a name="parameters"></a>Parametry

*pszVar*<br/>
Ukazatel na řetězec zakončený hodnotou null, který určuje proměnnou prostředí.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Načte hodnotu zadanou proměnnou z bloku prostředí volajícího procesu. Hodnota je ve formě řetězec znaků zakončené znakem null.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#121](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_16.cpp)]

##  <a name="insert"></a>  CStringT::Insert

Vloží znak nebo podřetězec v daném indexu v rámci řetězce.

```
int Insert(int iIndex, PCXSTR psz);
int Insert(int iIndex, XCHAR ch);
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
Index znak, před kterým bude vložení proběhnout.

*psz*<br/>
Ukazatel na dílčí řetězec, který má být vložen.

*ch*<br/>
Znak, který má být vložen.

### <a name="return-value"></a>Návratová hodnota

Délka změněný řetězec.

### <a name="remarks"></a>Poznámky

*IIndex* parametr identifikuje prvního znaku, který bude přesunuta do místa pro tento znak nebo podřetězec. Pokud *nIndex* je nula, dojde k vložení před celý řetězec. Pokud *nIndex* je vyšší než délka řetězce, funkce bude zřetězit řetězec k dispozici a nový materiál k dispozici buď *ch* nebo *psz*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#122](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_17.cpp)]

##  <a name="left"></a>  CStringT::Left

Extrahuje *nCount* znaky z tohoto `CStringT` objekt a vrátí kopii extrahovaného podřetězce.

```
CStringT Left(int nCount) const; 
```

### <a name="parameters"></a>Parametry

*nCount*<br/>
Počet znaků k extrakci z tohoto `CStringT` objektu.

### <a name="return-value"></a>Návratová hodnota

A `CStringT` objekt, který obsahuje kopii zadaného rozsahu znaků. Vrácený `CStringT` objekt může být prázdný.

### <a name="remarks"></a>Poznámky

Pokud *nCount* překračuje délku řetězce a pak je extrahován celý řetězec. `Left` se podobá základní `Left` funkce.

Pro vícebajtové znakové sady (MBCS) *nCount* zpracuje každou 8bitovou posloupnost jako znak, tak, aby *nCount* vrátí počet znaků vynásobený dvěma.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#123](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_18.cpp)]

##  <a name="loadstring"></a>  CStringT::LoadString

Načte prostředek řetězce Windows identifikovaný *nID*, do existujícího `CStringT` objektu.

```
BOOL LoadString(HINSTANCE hInstance, UINT nID, WORD wLanguageID);
BOOL LoadString(HINSTANCE hInstance, UINT nID);
BOOL LoadString(UINT nID);
```

### <a name="parameters"></a>Parametry

*hInstance*<br/>
Popisovač instance modulu.

*nID*<br/>
ID Windows řetězec prostředku.

*wLanguageID*<br/>
Jazyk prostředku řetězců.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud zatížení prostředků byla úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Načte prostředek řetězce (*nID*) ze zadaného modulu (*hInstance*) pomocí zadaného jazyka (*wLanguage*).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#124](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_19.cpp)]

##  <a name="makelower"></a>  CStringT::MakeLower

Převede `CStringT` objekt na řetězec, malá písmena.

```
CStringT& MakeLower();
```

### <a name="return-value"></a>Návratová hodnota

Výsledný řetězec, malá písmena.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#125](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_20.cpp)]

##  <a name="makereverse"></a>  CStringT::MakeReverse

Obrátí pořadí znaků ve `CStringT` objektu.

```
CStringT& MakeReverse();
```

### <a name="return-value"></a>Návratová hodnota

Výsledná vrátit řetězec.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#126](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_21.cpp)]

##  <a name="makeupper"></a>  CStringT::MakeUpper

Převede `CStringT` objekt na řetězec, velká písmena.

```
CStringT& MakeUpper();
```

### <a name="return-value"></a>Návratová hodnota

Výsledný řetězec, velká písmena.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#127](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_22.cpp)]

##  <a name="mid"></a>  CStringT::Mid

Extrahuje podřetězec délky *nCount* znaky z tohoto `CStringT` počínaje pozice *iFirst* (počítáno od nuly).

```
CStringT Mid(int iFirst, int nCount) const;
CStringT Mid(int iFirst) const; 
```

### <a name="parameters"></a>Parametry

*iFirst*<br/>
Z nuly vycházející index prvního znaku v tomto `CStringT` objekt, který má být součástí extrahovaného podřetězce.

*nCount*<br/>
Počet znaků k extrakci z tohoto `CStringT` objektu. Pokud tento parametr není zadán, je extrahován zbývající část řetězce.

### <a name="return-value"></a>Návratová hodnota

A `CStringT` objekt, který obsahuje kopii zadaného rozsahu znaků. Všimněte si, že vrácené `CStringT` objekt může být prázdný.

### <a name="remarks"></a>Poznámky

Vrátí kopii extrahovaného podřetězce. `Mid` je podobný funkce základní Mid (s tím rozdílem, že indexy v Basic jsou základem 1).

Pro vícebajtové znakové sady (MBCS) *nCount* odkazuje na každý 8bitový znak; to znamená vedoucí a bajt v jeden vícebajtový znak se počítají jako dva znaky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#128](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_23.cpp)]

##  <a name="oemtoansi"></a>  CStringT::OemToAnsi

Převede všechny znaky v tomto `CStringT` objekt od výrobce OEM znakové sadě znakovou sadu ANSI.

```
void OemToAnsi();
```

### <a name="remarks"></a>Poznámky

Tato funkce není k dispozici, pokud je _UNICODE definováno.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CStringT::AnsiToOem](#ansitooem).

##  <a name="operator_add"></a>  CStringT::operator +

Spojuje dva řetězce nebo řetězce a znak.

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

*CH1*<br/>
ANSI nebo Unicode znak pro řetězení s řetězcem.

*CH2*<br/>
ANSI nebo Unicode znak pro řetězení s řetězcem.

*Str1*<br/>
A `CStringT` zřetězit s řetězec nebo znak.

*řetězci Str2*<br/>
A `CStringT` zřetězit s řetězec nebo znak.

*psz1*<br/>
Ukazatel na řetězec zakončený hodnotou null pro řetězení s řetězec nebo znak.

*psz2*<br/>
Ukazatel na řetězec zřetězit s řetězec nebo znak.

### <a name="remarks"></a>Poznámky

Existují formy sedm přetížení `CStringT::operator+` funkce. První verze zřetězí dva existující `CStringT` objekty. Další dvě concatenate `CStringT` objekt a řetězec zakončený hodnotou null. Další dvě concatenate `CStringT` objektu a znak ANSI. Poslední dva concatenate `CStringT` objektu a znak Unicode.

> [!NOTE]
>  I když je možné vytvořit `CStringT` instancí, které obsahují vložené znaky null, doporučujeme před ním. Při volání metody a operátory na `CStringT` objektů, které obsahují vložené znaky null může způsobit nežádoucí výsledky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#140](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_24.cpp)]

##  <a name="operator_add_eq"></a>  CStringT::operator +=

Připojí znaky na konec řetězce.

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

str  
Odkaz na `CThisSimpleString` objektu.

*bMFCDLL*<br/>
Logická hodnota určující, zda je projekt knihovny MFC DLL, nebo ne.

*BaseType*<br/>
Základní typ řetězec.

*var*<br/>
Varianty objekt ke zřetězení tento řetězec.

*ch*<br/>
ANSI nebo Unicode znak pro řetězení s řetězcem.

*pszSrc*<br/>
Ukazatel na původní řetězec jsou zřetězeny.

*strSrc*<br/>
A `CStringT` ke zřetězení tento řetězec.

### <a name="remarks"></a>Poznámky

Operátor, který přijímá Další `CStringT` objekt, ukazatel znaku nebo jeden znak. Je třeba si uvědomit, tato paměť, může dojít k výjimkám, při každém použití tohoto operátoru pro zřetězení, protože může být přiděleno nové úložiště pro znaky, které jsou přidány do tohoto `CStringT` objektu.

Informace o `CThisSimpleString`, najdete v části poznámky [CStringT::CStringT](#cstringt).

> [!NOTE]
>  I když je možné vytvořit `CStringT` instancí, které obsahují vložené znaky null, doporučujeme před ním. Při volání metody a operátory na `CStringT` objektů, které obsahují vložené znaky null může způsobit nežádoucí výsledky.

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

*CH1*<br/>
ANSI nebo Unicode znak pro porovnání.

*CH2*<br/>
ANSI nebo Unicode znak pro porovnání.

*Str1*<br/>
A `CStringT` pro porovnání.

*řetězci Str2*<br/>
A `CStringT` pro porovnání.

*psz1*<br/>
Ukazatel na řetězec zakončený hodnotou null pro srovnání.

*psz2*<br/>
Ukazatel na řetězec zakončený hodnotou null pro srovnání.

### <a name="remarks"></a>Poznámky

Testuje, jestli řetězec nebo znak na levé straně je rovna řetězec nebo znak na pravé straně a vrátí hodnotu TRUE nebo FALSE odpovídajícím způsobem.

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

*CH1*<br/>
ANSI nebo Unicode znak pro řetězení s řetězcem.

*CH2*<br/>
ANSI nebo Unicode znak pro řetězení s řetězcem.

*Str1*<br/>
A `CStringT` pro porovnání.

*řetězci Str2*<br/>
A `CStringT` pro porovnání.

*psz1*<br/>
Ukazatel na řetězec zakončený hodnotou null pro srovnání.

*psz2*<br/>
Ukazatel na řetězec zakončený hodnotou null pro srovnání.

### <a name="remarks"></a>Poznámky

Testuje, zda je řetězec nebo znak na levé straně není roven řetězec nebo znak na pravé straně.

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

*Str1*<br/>
A `CStringT` pro porovnání.

*řetězci Str2*<br/>
A `CStringT` pro porovnání.

*psz1*<br/>
Ukazatel na řetězec zakončený hodnotou null pro srovnání.

*psz2*<br/>
Ukazatel na řetězec zakončený hodnotou null pro srovnání.

### <a name="remarks"></a>Poznámky

Lexicographical porovnání znak po znaku do řetězce:

- Najde odpovídající dva znaky nerovnost a výsledek jejich porovnání se provede jako výsledek porovnání řetězců.

- Vyhledá žádný nerovnosti, ale jeden řetězec obsahuje více znaků, než druhý a kratší řetězec považuje za menší než řetězec delší dobu.

- Vyhledá žádný nerovnosti a zjistí, že řetězce mají stejný počet znaků, a proto jsou řetězce shodné.

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

*Str1*<br/>
A `CStringT` pro porovnání.

*řetězci Str2*<br/>
A `CStringT` pro porovnání.

*psz1*<br/>
Ukazatel na řetězec zakončený hodnotou null pro srovnání.

*psz2*<br/>
Ukazatel na řetězec zakončený hodnotou null pro srovnání.

### <a name="remarks"></a>Poznámky

Lexicographical porovnání znak po znaku do řetězce:

- Najde odpovídající dva znaky nerovnost a výsledek jejich porovnání se provede jako výsledek porovnání řetězců.

- Vyhledá žádný nerovnosti, ale jeden řetězec obsahuje více znaků, než druhý a kratší řetězec považuje za menší než řetězec delší dobu.

- Vyhledá žádný nerovnosti a zjistí, že řetězce mají stejný počet znaků, takže jsou řetězce shodné.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#145](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_29.cpp)]

##  <a name="operator_lt_eq"></a>  CStringT::operator &lt;=

Určuje, zda je řetězec na levé straně operátoru menší než nebo rovno řetězci na pravé straně.

```
friend bool operator<=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parametry

*Str1*<br/>
A `CStringT` pro porovnání.

*řetězci Str2*<br/>
A `CStringT` pro porovnání.

*psz1*<br/>
Ukazatel na řetězec zakončený hodnotou null pro srovnání.

*psz2*<br/>
Ukazatel na řetězec zakončený hodnotou null pro srovnání.

### <a name="remarks"></a>Poznámky

Lexicographical porovnání znak po znaku do řetězce:

- Najde odpovídající dva znaky nerovnost a výsledek jejich porovnání se provede jako výsledek porovnání řetězců.

- Vyhledá žádný nerovnosti, ale jeden řetězec obsahuje více znaků, než druhý a kratší řetězec považuje za menší než řetězec delší dobu.

- Vyhledá žádný nerovnosti a zjistí, že řetězce mají stejný počet znaků, takže jsou řetězce shodné.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#146](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_30.cpp)]

##  <a name="operator_gt_eq"></a>  CStringT::operator &gt;=

Určuje, zda je řetězec na levé straně operátoru větší než nebo rovno řetězci na pravé straně.

```
friend bool operator>=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parametry

*Str1*<br/>
A `CStringT` pro porovnání.

*řetězci Str2*<br/>
A `CStringT` pro porovnání.

*psz1*<br/>
Ukazatel na řetězec k porovnání.

*psz2*<br/>
Ukazatel na řetězec k porovnání.

### <a name="remarks"></a>Poznámky

Lexicographical porovnání znak po znaku do řetězce:

- Najde odpovídající dva znaky nerovnost a výsledek jejich porovnání se provede jako výsledek porovnání řetězců.

- Vyhledá žádný nerovnosti, ale jeden řetězec obsahuje více znaků, než druhý a kratší řetězec považuje za menší než řetězec delší dobu.

- Vyhledá žádný nerovnosti a zjistí, že řetězce mají stejný počet znaků, takže jsou řetězce shodné.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#147](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_31.cpp)]

##  <a name="remove"></a>  CStringT::Remove

Odebere všechny výskyty zadaný znak z řetězce.

```
int Remove(XCHAR chRemove);
```

### <a name="parameters"></a>Parametry

*chRemove*<br/>
Znak, který má být odebrán z řetězce.

### <a name="return-value"></a>Návratová hodnota

Počet znaků z řetězce. Nula v případě řetězec se nezmění.

### <a name="remarks"></a>Poznámky

Porovnávání znaku rozlišuje velká a malá písmena.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#129](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_32.cpp)]

##  <a name="replace"></a>  CStringT::Replace

Existují dvě verze `Replace`. První verze nahradí jeden nebo více kopií podřetězce pomocí jiného dílčí řetězec. Obě podřetězce jsou si zakončený hodnotou null. Druhá verze nahradí jeden nebo více kopií znak pomocí další znak. Obě verze pracovat s daty znak uložené v `CStringT`.

```
int Replace(PCXSTR pszOld, PCXSTR pszNew);
int Replace(XCHAR chOld, XCHAR chNew);
```

### <a name="parameters"></a>Parametry

*pszOld*<br/>
Ukazatel na řetězec zakončený hodnotou null bude nahrazen *pszNew*.

*pszNew*<br/>
Ukazatel na řetězec zakončený hodnotou null, který nahrazuje *pszOld*.

*chOld*<br/>
Znak, který má být nahrazen *chNew*.

*chNew*<br/>
Znak nahrazení *chOld*.

### <a name="return-value"></a>Návratová hodnota

Vrátí počet nahrazená instancí znak nebo podřetězec nebo nula, pokud není změněná řetězec.

### <a name="remarks"></a>Poznámky

`Replace` Délka řetězce může změnit, protože *pszNew* a *pszOld* nemusíte mít stejnou délku a několik kopií staré podřetězce lze změnit na novou. Funkce provádí velká a malá písmena rozlišovat.

Příklady `CStringT` instance jsou `CString`, `CStringA`, a `CStringW`.

Pro `CStringA`, `Replace` funguje s ANSI nebo vícebajtových znaků (MBCS). Pro `CStringW`, `Replace` funguje s širokých znaků.

Pro `CString`, datový typ znak se určí v době kompilace, o tom, jestli jsou definované konstanty v následující tabulce.

|Definované – konstanta|Znak typu dat|
|----------------------|-------------------------|
|_UNICODE|Široké znaky|
|_MBCS|Vícebajtové znaky|
|Ani|Jednobajtové znaky|
|Obojí|Nedefinovaný|

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#200](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_33.cpp)]

##  <a name="reversefind"></a>  CStringT::ReverseFind

Vyhledá to `CStringT` objekt pro poslední výskyty znaku.

```
int ReverseFind(XCHAR ch) const throw();
```

### <a name="parameters"></a>Parametry

*ch*<br/>
Znak, který chcete vyhledat.

### <a name="return-value"></a>Návratová hodnota

Index založený na nule poslední znak v tomto `CStringT` objekt, který odpovídá požadované znak nebo -1, pokud znak, který nebyl nalezen.

### <a name="remarks"></a>Poznámky

Funkce je podobný funkci run-time `strrchr`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#130](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_34.cpp)]

##  <a name="right"></a>  CStringT::Right

Extrahuje posledních (to znamená úplně vpravo) *nCount* znaky z tohoto `CStringT` objekt a vrátí kopii extrahovaného podřetězce.

```
CStringT Right(int nCount) const; 
```

### <a name="parameters"></a>Parametry

*nCount*<br/>
Počet znaků k extrakci z tohoto `CStringT` objektu.

### <a name="return-value"></a>Návratová hodnota

A `CStringT` objekt, který obsahuje kopii zadaného rozsahu znaků. Všimněte si, že vrácené `CStringT` objekt může být prázdný.

### <a name="remarks"></a>Poznámky

Pokud *nCount* překračuje délku řetězce a pak je extrahován celý řetězec. `Right` se podobá základní `Right` funkci (s tím rozdílem, že indexy v Basic jsou počítány od nuly).

Pro vícebajtové znakové sady (MBCS) *nCount* odkazuje na každý 8bitový znak; to znamená vedoucí a bajt v jeden vícebajtový znak se počítají jako dva znaky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#131](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_35.cpp)]

##  <a name="setsysstring"></a>  CStringT::SetSysString

Znovu alokuje BSTR, na které odkazuje *pbstr* a kopíruje obsah `CStringT` do objektu, včetně znaku NULL.

```
BSTR SetSysString(BSTR* pbstr) const; 
```

### <a name="parameters"></a>Parametry

*pbstr*<br/>
Ukazatel na řetězec znaků.

### <a name="return-value"></a>Návratová hodnota

Nový řetězec.

### <a name="remarks"></a>Poznámky

V závislosti na obsah `CStringT` objektu, hodnota BSTR odkazuje *pbstr* můžete změnit. Funkce vyvolá `CMemoryException` pokud existuje dostatek paměti.

Tato funkce se obvykle používá Chcete-li změnit hodnotu řetězce, které jsou předány podle odkazu pro automatizaci.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#132](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_36.cpp)]

##  <a name="spanexcluding"></a>  CStringT::SpanExcluding

Extrahuje znaky z řetězce, počínaje první znaky, které nejsou v sadě znaků identifikovaný *pszCharSet*.

```
CStringT SpanExcluding(PCXSTR pszCharSet) const; 
```

### <a name="parameters"></a>Parametry

*pszCharSet*<br/>
Řetězec je interpretován jako sadu znaků.

### <a name="return-value"></a>Návratová hodnota

Podřetězce, který obsahuje znaky v řetězci, které nejsou v *pszCharSet*, počínaje první znak v řetězci a končící na první znak v řetězci, které jsou uvedené taky v nalezen *pszCharSet* (to znamená, počínaje první znak v řetězci a až s výjimkou prvního znaku v řetězci, který se nachází *pszCharSet*). Vrátí celý řetězec, pokud žádný znak v *pszCharSet* se nachází v řetězci.

### <a name="remarks"></a>Poznámky

`SpanExcluding` extrahuje a vrátí všechny znaky, které předchází první výskyt znaku z *pszCharSet* (jinými slovy, znak z *pszCharSet* a nejsou všechny znaky v řetězci, Vrátí). Pokud žádný znak z *pszCharSet* se nachází v řetězci, pak `SpanExcluding` vrátí celý řetězec.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#133](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_37.cpp)]

##  <a name="spanincluding"></a>  CStringT::SpanIncluding

Extrahuje znaky z řetězce, počínaje prvního znaku, které jsou v sadě znaků identifikovaný *pszCharSet*.

```
CStringT SpanIncluding(PCXSTR pszCharSet) const; 
```

### <a name="parameters"></a>Parametry

*pszCharSet*<br/>
Řetězec je interpretován jako sadu znaků.

### <a name="return-value"></a>Návratová hodnota

Podřetězce, který obsahuje znaky v řetězci, které jsou v *pszCharSet*, počínaje první znak v řetězci a končí při nalezení znaku v řetězci, který není součástí *pszCharSet*. `SpanIncluding` nejsou-li první znak v řetězci v zadané sadě, vrátí prázdný dílčí řetězec.

### <a name="remarks"></a>Poznámky

Nejsou-li první znak řetězce ve znakové sadě pak `SpanIncluding` vrátí prázdný řetězec. V opačném případě vrátí posloupnosti po sobě jdoucích znaků, které jsou v sadě.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#134](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_38.cpp)]

##  <a name="tokenize"></a>  CStringT::Tokenize

Vyhledá další token v cílovém řetězci

```
CStringT Tokenize(PCXSTR pszTokens, int& iStart) const; 
```

### <a name="parameters"></a>Parametry

*pszTokens*<br/>
Řetězec obsahující token oddělovače. Pořadí oddělovačů tyto není důležité.

*iStart*<br/>
Index založený na nule zahájíte hledání.

### <a name="return-value"></a>Návratová hodnota

A `CStringT` objekt, který obsahuje aktuální hodnota tokenu.

### <a name="remarks"></a>Poznámky

`Tokenize` Funkce vyhledá další token v cílovém řetězci. Sady znaků v *pszTokens* Určuje možné oddělovače tokenu, která se má najít. Pro každé volání `Tokenize` funkci začíná *iStart*, přeskočí úvodní oddělovače a vrátí `CStringT` objekt, který obsahuje aktuální token, který je řetězec znaků až do další znak oddělovače. Hodnota *iStart* je aktualizován, aby se do pozice za poslední znak oddělovače nebo -1, pokud bylo dosaženo konce řetězce. Další tokeny lze zjistit ze zbytku parametru cílový řetězec pomocí posloupnosti volání `Tokenize`s použitím *iStart* ke sledování umístění v řetězci je další token ke čtení. Pokud neexistují žádné další tokeny funkce vrátí prázdný řetězec a *iStart* bude nastavena na hodnotu -1.

Na rozdíl od CRT tokenizovat funkce, jako je [strtok_s – _strtok_s_l –, wcstok_s –, _wcstok_s_l –, _mbstok_s –, _mbstok_s_l –](../../c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md), `Tokenize` neupravuje cílový řetězec.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#135](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_39.cpp)]

### <a name="remarks"></a>Poznámky

Výstup z tohoto příkladu vypadá takto:

```Output
Resulting Token: First
Resulting Token: Second
Resulting Token: Third
```

##  <a name="trim"></a>  CStringT::Trim

Ořízne počáteční a koncové znaky z řetězce.

```
CStringT& Trim(XCHAR chTarget);
CStringT& Trim(PCXSTR pszTargets);
CStringT& Trim();
```

### <a name="parameters"></a>Parametry

*chTarget*<br/>
Cíl znak, který má být oříznut.

*pszTargets*<br/>
Ukazatel na řetězec obsahující znaky cíl, které mají být oříznut. Všechny úvodní a koncové výskyty znaků v *pszTarget* bude oříznut z `CStringT` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí řetězec oříznutý.

### <a name="remarks"></a>Poznámky

Odebere všechny úvodní a koncové výskytů jedné z následujících akcí:

- Znak určený *chTarget*.

- Všechny znaky v řetězci určené nalezen *pszTargets*.

- Prázdné znaky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#136](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_40.cpp)]

### <a name="remarks"></a>Poznámky

Výstup z tohoto příkladu vypadá takto:

```Output
Before: "******Soccer is best, but liquor is quicker!!!!!"
After : "Soccer is best, but liquor is quicker"
```

##  <a name="trimleft"></a>  CStringT::TrimLeft

Ořízne počáteční znaky z řetězce.

```
CStringT& TrimLeft(XCHAR chTarget);
CStringT& TrimLeft(PCXSTR pszTargets);
CStringT& TrimLeft();
```

### <a name="parameters"></a>Parametry

*chTarget*<br/>
Cíl znak, který má být oříznut.

*pszTargets*<br/>
Ukazatel na řetězec obsahující znaky cíl, které mají být oříznut. Všechny úvodní výskyty znaků v *pszTarget* bude oříznut z `CStringT` objektu.

### <a name="return-value"></a>Návratová hodnota

Výsledný řetězec, který oříznutý.

### <a name="remarks"></a>Poznámky

Odebere všechny úvodní a koncové výskytů jedné z následujících akcí:

- Znak určený *chTarget*.

- Všechny znaky v řetězci určené nalezen *pszTargets*.

- Prázdné znaky.

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

*chTarget*<br/>
Cíl znak, který má být oříznut.

*pszTargets*<br/>
Ukazatel na řetězec obsahující znaky cíl, které mají být oříznut. Všechny výskyty znaků v koncové *pszTarget* bude oříznut z `CStringT` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí `CStringT` objekt, který obsahuje zkrácená řetězcová.

### <a name="remarks"></a>Poznámky

Odebere koncové výskytů jedné z následujících akcí:

- Znak určený *chTarget*.

- Všechny znaky v řetězci určené nalezen *pszTargets*.

- Prázdné znaky.

`CStringT& TrimRight(XCHAR chTarget)` Verze přijímá jeden parametr znaku a odebere všechny kopie této znaků z konce `CStringT` data řetězce. Začíná od konce řetězce a funguje směrem dopředu. Zastaví, pokud se najde jiný znak, nebo když `CSTringT` vyčerpá znaková data.

`CStringT& TrimRight(PCXSTR pszTargets)` Verze přijímá řetězec zakončený hodnotou null, který obsahuje všechny různých znaků k vyhledání. Odebere všechny kopie těchto znaků `CStringT` objektu. Začíná na konci řetězce a funguje směrem dopředu. Zastaví při nalezení znaku, který není v cílovém řetězci, nebo když `CStringT` vyčerpá znaková data. Tak, aby odpovídaly celý cílový řetězec, který má dílčí řetězec na konci nepokusí `CStringT`.

`CStringT& TrimRight()` Verze nevyžaduje žádné parametry. Ořízne všechny mezery na konci od konce `CStringT` řetězec. Prázdné znaky může být konce řádků, mezery nebo tabulátory.

-

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#138](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_42.cpp)]

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Sdílené třídy ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)<br/>
[CSimpleStringT – třída](../../atl-mfc-shared/reference/csimplestringt-class.md)

