---
title: CStringT – třída
ms.date: 03/27/2019
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
helpviewer_keywords:
- strings [C++], in ATL
- shared classes, CStringT
- CStringT class
ms.assetid: 7cacc59c-425f-40f1-8f5b-6db921318ec9
ms.openlocfilehash: 8fcce4c426cd99785d34dc080f238cc78cdfee36
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746711"
---
# <a name="cstringt-class"></a>CStringT – třída

Tato třída `CStringT` představuje objekt.

## <a name="syntax"></a>Syntaxe

```
template<typename BaseType, class StringTraits>
class CStringT :
    public CSimpleStringT<BaseType,
        _CSTRING_IMPL_::_MFCDLLTraitsCheck<BaseType, StringTraits>::c_bIsMFCDLLTraits>
```

#### <a name="parameters"></a>Parametry

*BaseType*<br/>
Typ znaku třídy řetězce. Může to být jedna z následujících možností:

- **char** (pro řetězce znaků ANSI).

- **wchar_t** (pro řetězce znaků Unicode).

- TCHAR (pro řetězce znaků ANSI i Unicode).

*StringTraits*<br/>
Určuje, zda třída řetězce potřebuje podporu knihovny C Run-Time (CRT) a kde jsou umístěny prostředky řetězce. Může to být jedna z následujících možností:

- **StrTraitATL< wchar_t** &#124; **char** &#124; **TCHAR, ChTraitsCRT< wchar_t** &#124; **char** &#124; **TCHAR > >**

   Třída vyžaduje podporu CRT a vyhledá v modulu `m_hInstResource` určeném (člen třídy modulu aplikace) řetězce prostředků.

- **StrTraitATL< wchar_t<** &#124; **char** &#124; **TCHAR, ChTraitsOS< wchar_t** &#124; **char** &#124; **TCHAR > >**

   Třída nevyžaduje podporu CRT a vyhledá v modulu určeném `m_hInstResource` (člen třídy modulu aplikace) hledá řetězce prostředků.

- **StrTraitMFC< wchar_t** &#124; **char** &#124; **TCHAR, ChTraitsCRT< wchar_t** &#124; **char** &#124; **TCHAR > >**

   Třída vyžaduje podporu CRT a vyhledává řetězce prostředků pomocí standardního algoritmu vyhledávání knihovny MFC.

- **StrTraitMFC< wchar_t** &#124; **char** &#124; **TCHAR, ChTraitsOS< wchar_t** &#124; **char** &#124; **TCHAR > >**

   Třída nevyžaduje podporu CRT a vyhledá v řetězecích prostředků pomocí standardního algoritmu vyhledávání knihovny MFC.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CStringT::CStringt](#cstringt)|Vytvoří `CStringT` objekt různými způsoby.|
|[CStringT::~CStringT](#_dtorcstringt)|Zničí `CStringT` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CStringT::AllocSysString](#allocsysstring)|Přiděluje BSTR z `CStringT` dat.|
|[CStringT::AnsiToOem](#ansitooem)|Provede převod na místě ze znakové sady ANSI na znakovou sadu OEM.|
|[CStringT::Připojitformát](#appendformat)|Připojí formátovaná data k `CStringT` existujícímu objektu.|
|[CStringT::Kompletovat](#collate)|Porovná dva řetězce (rozlišuje malá a velká písmena, používá informace specifické pro národní prostředí).|
|[CStringT::CollateNoCase](#collatenocase)|Porovná dva řetězce (malá a velká písmena, používá informace specifické pro národní prostředí).|
|[CStringT::Porovnat](#compare)|Porovná dva řetězce (malá a velká písmena).|
|[CStringT::PorovnáníNocase](#comparenocase)|Porovná dva řetězce (malá a velká písmena).|
|[CStringT::Delete](#delete)|Odstraní znak nebo znaky z řetězce.|
|[CStringT::Najít](#find)|Najde znak nebo podřetězec uvnitř větší řetězec.|
|[CStringt::Najít](#findoneof)|Najde první odpovídající znak ze sady.|
|[CStringT::Formát](#format)|Formátuje řetězec `sprintf` stejně jako řetězec.|
|[CStringT::Zpráva formátu](#formatmessage)|Formátuje řetězec zprávy.|
|[CStringT::FormatMessageV](#formatmessagev)|Formátuje řetězec zprávy pomocí seznamu argumentů proměnných.|
|[CStringT::FormatV](#formatv)|Zformátuje řetězec pomocí seznamu proměnných argumentů.|
|[CStringT::GetEnvironmentVariable](#getenvironmentvariable)|Nastaví řetězec na hodnotu zadané proměnné prostředí.|
|[CStringT::Vložit](#insert)|Vloží jeden znak nebo podřetězec na daný index v řetězci.|
|[CStringT::Vlevo](#left)|Extrahuje levou část řetězce.|
|[CStringT::Načíst řetězec](#loadstring)|Načte `CStringT` existující objekt z prostředku systému Windows.|
|[CStringT::MakeLower](#makelower)|Převede všechny znaky v tomto řetězci na malé znaky.|
|[CStringT::MakeReverse](#makereverse)|Obrátí řetězec.|
|[CStringt::MakeUpper](#makeupper)|Převede všechny znaky v tomto řetězci na velká písmena.|
|[CStringT::Střední](#mid)|Extrahuje střední část řetězce.|
|[CStringT::OemToAnsi](#oemtoansi)|Provede převod na místě ze znakové sady OEM na znakovou sadu ANSI.|
|[CStringT::Odebrat](#remove)|Odebere označené znaky z řetězce.|
|[CStringT::Nahradit](#replace)|Nahradí označené znaky jinými znaky.|
|[CStringT::Reverznífind](#reversefind)|Najde znak uvnitř větší hovna; začíná od konce.|
|[CStringT::Doprava](#right)|Extrahuje pravou část řetězce.|
|[CStringT::SetSysString](#setsysstring)|Nastaví existující objekt BSTR `CStringT` s daty z objektu.|
|[CStringT::SpanBez](#spanexcluding)|Extrahuje znaky z řetězce, počínaje prvním znakem, které nejsou `pszCharSet`v sadě znaků identifikovaných .|
|[CStringT::SpanIncluding](#spanincluding)|Extrahuje podřetězec, který obsahuje pouze znaky v sadě.|
|[CStringT::Tokenize](#tokenize)|Extrahuje zadané tokeny v cílovém řetězci.|
|[CStringT::Oříznutí](#trim)|Ořízne všechny úvodní a koncové znaky prázdného místa z řetězce.|
|[CStringT::Oříznutívlevo](#trimleft)|Ořízne počáteční znaky prázdného místa z řetězce.|
|[cstringt::TrimRight](#trimright)|Ořízne koncové znaky prázdného místa z řetězce.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[CStringT::operátor =](#operator_eq)|Přiřadí objektu novou `CStringT` hodnotu.|
|[CStringT::operátor +](#operator_add)|Zřetězí dva řetězce nebo znak a řetězec.|
|[CStringT::operátor +=](#operator_add_eq)|Zřetězí nový řetězec na konec existujícího řetězce.|
|[CStringT::operátor ==](#operator_eq_eq)|Určuje, zda jsou dva řetězce logicky stejné.|
|[CStringT::operátor !=](#operator_neq)|Určuje, zda dva řetězce nejsou logicky stejné.|
|[CStringT::operátor&lt;](#operator_lt)|Určuje, zda je řetězec na levé straně operátoru menší než řetězec na pravé straně.|
|[CStringT::operátor&gt;](#operator_gt)|Určuje, zda je řetězec na levé straně operátoru větší než řetězec na pravé straně.|
|[CStringT::operátor&lt;=](#operator_lt_eq)|Určuje, zda je řetězec na levé straně operátoru menší nebo roven řetězci na pravé straně.|
|[CStringT::operátor&gt;=](#operator_gt_eq)|Určuje, zda je řetězec na levé straně operátoru větší nebo roven řetězci na pravé straně.|

## <a name="remarks"></a>Poznámky

`CStringT`dědí z [csimplestringt třídy](../../atl-mfc-shared/reference/csimplestringt-class.md). Pokročilé funkce, jako je například manipulace s znaky, řazení a vyhledávání, jsou implementovány . `CStringT`

> [!NOTE]
> `CStringT`objekty jsou schopny vyvolat výjimky. K tomu dochází, `CStringT` když objekt vyčerpá paměť z jakéhokoli důvodu.

Objekt `CStringT` se skládá z posloupnosti znaků s proměnnou délkou. `CStringT`poskytuje funkce a operátory pomocí syntaxe podobné basic. Operátory zřetězení a porovnání spolu se `CStringT` zjednodušenou správou paměti usnadňují použití objektů než běžná pole znaků.

> [!NOTE]
> I když je `CStringT` možné vytvořit instance, které obsahují vložené prázdné znaky, doporučujeme proti němu. Volání metod a `CStringT` operátorů na objekty, které obsahují vložené prázdné znaky může způsobit nezamýšlené výsledky.

Pomocí různých kombinací `BaseType` a `StringTraits` parametry, `CStringT` objekty mohou přijít v následujících typech, které byly předdefinovány knihovny KNIHOVNY ATL.

Při použití v aplikaci ATL:

`CString`, `CStringA`a `CStringW` jsou exportovány z knihovny MFC DLL (MFC90. DLL), nikdy z uživatelských knihoven DLL. To se provádí, aby se zabránilo `CStringT` množení definovány.

> [!NOTE]
> Pokud váš kód obsahuje řešení pro chyby propojovacího zařízení, které je popsáno v [exportu tříd řetězce pomocí CStringT](../../atl-mfc-shared/exporting-string-classes-using-cstringt.md), měli byste tento kód odebrat. Už není zapotřebí.

V aplikacích založených na knihovně MFC jsou k dispozici následující typy řetězců:

|Typ CStringT|Deklarace|
|-------------------|-----------------|
|`CStringA`|Řetězec typu znaku ANSI s podporou CRT.|
|`CStringW`|Řetězec typu znaku Unicode s podporou CRT.|
|`CString`|Typy znaků ANSI a Unicode s podporou CRT.|

Následující typy řetězců jsou k dispozici v projektech, kde je definovánATL_CSTRING_NO_CRT

|Typ CStringT|Deklarace|
|-------------------|-----------------|
|`CAtlStringA`|Řetězec typu znaku ANSI bez podpory CRT.|
|`CAtlStringW`|Řetězec typu znaku Unicode bez podpory CRT.|
|`CAtlString`|Typy znaků ANSI a Unicode bez podpory CRT.|

Následující typy řetězců jsou k dispozici v projektech, kde není definována ATL_CSTRING_NO_CRT:

|Typ CStringT|Deklarace|
|-------------------|-----------------|
|`CAtlStringA`|Řetězec typu znaku ANSI s podporou CRT.|
|`CAtlStringW`|Řetězec typu znaku Unicode s podporou CRT.|
|`CAtlString`|Typy znaků ANSI a Unicode s podporou CRT.|

`CString`objekty mají také následující vlastnosti:

- `CStringT`objekty mohou růst v důsledku operací zřetězení.

- `CStringT`objekty následují za "hodnotou sémantiky". Představte `CStringT` si objekt jako skutečný řetězec, nikoli jako ukazatel na řetězec.

- Můžete volně nahradit `CStringT` objekty pro `PCXSTR` argumenty funkce.

- Vlastní správa paměti pro vyrovnávací paměti řetězce. Další informace naleznete v [tématu Memory Management a CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="cstringt-predefined-types"></a>Předdefinované typy CStringT

Protože `CStringT` používá argument šablony k definování typu znaku (wchar_t [nebo](../../c-runtime-library/standard-types.md) [znak](../../c-runtime-library/standard-types.md)) podporované, typy parametrů metody mohou být někdy složité. Pro zjednodušení tohoto problému je definována a používána `CStringT` v celé třídě sada předdefinovaných typů. V následující tabulce jsou uvedeny různé typy:

|Název|Popis|
|----------|-----------------|
|`XCHAR`|Jeden znak **(buď wchar_t** nebo **znak**) se `CStringT` stejným typem znaku jako objekt.|
|`YCHAR`|Jeden znak **(buď wchar_t** nebo **znak**) s `CStringT` opačným typem znaku jako objekt.|
|`PXSTR`|Ukazatel na řetězec znaku **(wchar_t** nebo **znak)** se `CStringT` stejným typem znaku jako objekt.|
|`PYSTR`|Ukazatel na řetězec znaku **(buď wchar_t** nebo **char)** `CStringT` s opačným typem znaku jako objekt.|
|`PCXSTR`|Ukazatel na řetězec **znaků const** **(buď wchar_t** nebo **char)** `CStringT` se stejným typem znaku jako objekt.|
|`PCYSTR`|Ukazatel na řetězec **znaku const** **(buď wchar_t** nebo **char)** s opačným typem znaku jako objekt. `CStringT`|

> [!NOTE]
> Kód, který dříve používal `CString` nedokumentované `AssignCopy`metody (například ) musí být nahrazen `CStringT` kódem, `GetBuffer` `ReleaseBuffer`který používá následující zdokumentované metody (například nebo ). Tyto metody jsou `CSimpleStringT`zděděny z .

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)

`CStringT`

## <a name="requirements"></a>Požadavky

|Hlavička|Použití pro|
|------------|-------------|
|cstringt.h|Objekty řetězce pouze knihovny MFC|
|atlstr.h|Objekty řetězce jiné než Knihovna MFC|

## <a name="cstringtallocsysstring"></a><a name="allocsysstring"></a>CStringT::AllocSysString

Přidělí řetězec kompatibilní s automatizací typu BSTR a `CStringT` zkopíruje do něj obsah objektu, včetně ukončujícího znaku null.

```
BSTR AllocSysString() const;
```

### <a name="return-value"></a>Návratová hodnota

Nově přidělený řetězec.

### <a name="remarks"></a>Poznámky

V programech knihovny MFC je vyvolána [třída CMemoryException,](../../mfc/reference/cmemoryexception-class.md) pokud neexistuje dostatek paměti. V programech ATL je vyvolána [catlexception.](../../atl/reference/catlexception-class.md) Tato funkce se obvykle používá k vrácení řetězců pro automatizaci.

Obvykle pokud tento řetězec je předán funkci COM jako parametr [in], pak to vyžaduje, aby volající uvolnit řetězec. To lze provést pomocí [sysFreeString](/windows/win32/api/oleauto/nf-oleauto-sysfreestring), jak je popsáno v sadě Windows SDK. Další informace naleznete [v tématu Přidělování a uvolnění paměti pro BSTR](../../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md).

Další informace o funkcích přidělení OLE v systému Windows naleznete v tématu [SysAllocString](/windows/win32/api/oleauto/nf-oleauto-sysallocstring) v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CStringT::AllocSysString`.

[!code-cpp[NVC_ATLMFC_Utilities#105](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_1.cpp)]

## <a name="cstringtansitooem"></a><a name="ansitooem"></a>CStringT::AnsiToOem

Převede všechny znaky `CStringT` v tomto objektu ze znakové sady ANSI na znakovou sadu OEM.

```cpp
void AnsiToOem();
```

### <a name="remarks"></a>Poznámky

Funkce není k dispozici, pokud je definována _UNICODE.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#106](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_2.cpp)]

## <a name="cstringtappendformat"></a><a name="appendformat"></a>CStringT::Připojitformát

Připojí formátovaná data k `CStringT` existujícímu objektu.

```cpp
void __cdecl AppendFormat(PCXSTR pszFormat, [, argument] ...);
void __cdecl AppendFormat(UINT nFormatID, [, argument] ...);
```

### <a name="parameters"></a>Parametry

*pszFormat*<br/>
Řetězec řízení formátu.

*nID formátu*<br/>
Identifikátor prostředku řetězce, který obsahuje řetězec řízení formátu.

*Argument*<br/>
Volitelné argumenty

### <a name="remarks"></a>Poznámky

Tato funkce formátuje a připojí řadu znaků `CStringT`a hodnot v . Každý volitelný argument (pokud existuje) je převeden a připojen podle odpovídající specifikace formátu v *pszFormat* nebo z prostředku řetězce identifikovaného *nFormatID*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#107](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_3.cpp)]

## <a name="cstringtcollate"></a><a name="collate"></a>CStringT::Kompletovat

Porovná dva řetězce pomocí funkce `_tcscoll`obecného textu .

```
int Collate(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Druhý řetězec použitý pro porovnání.

### <a name="return-value"></a>Návratová hodnota

Nula, pokud řetězce jsou identické, `CStringT` < 0, pokud tento objekt `CStringT` je menší než *psz*, nebo > 0, pokud tento objekt je větší než *psz*.

### <a name="remarks"></a>Poznámky

Funkce `_tcscoll`obecného textu , která je definována v TCHAR. H, mapuje `strcoll` `wcscoll`na `_mbscoll`buď , nebo , v závislosti na znakové sadě, která je definována v době kompilace. Každá funkce provádí porovnání řetězců rozlišujícímalá písmena podle aktuálně používáné znakové stránky. Další informace naleznete [v tématech strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md).

## <a name="cstringtcollatenocase"></a><a name="collatenocase"></a>CStringT::CollateNoCase

Porovná dva řetězce pomocí funkce `_tcscoll`obecného textu .

```
int CollateNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Druhý řetězec použitý pro porovnání.

### <a name="return-value"></a>Návratová hodnota

Nula, pokud řetězce jsou identické (ignorování `CStringT` případu), < 0, pokud tento objekt je `CStringT` menší než *psz* (ignorování případu), nebo > 0, pokud tento objekt je větší než *psz* (ignorování případu).

### <a name="remarks"></a>Poznámky

Funkce `_tcscoll`obecného textu , která je definována v TCHAR. H, mapuje `stricoll` `wcsicoll`na `_mbsicoll`buď , nebo , v závislosti na znakové sadě, která je definována v době kompilace. Každá funkce provádí porovnání řetězců bez rozlišování velkých a malých písmen podle aktuálně používáné znakové stránky. Další informace naleznete [v tématech strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#109](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_4.cpp)]

## <a name="cstringtcompare"></a><a name="compare"></a>CStringT::Porovnat

Porovná dva řetězce (malá a velká písmena).

```
int Compare(PCXSTR psz) const;
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Druhý řetězec použitý pro porovnání.

### <a name="return-value"></a>Návratová hodnota

Nula, pokud řetězce jsou identické, `CStringT` < 0, pokud tento objekt `CStringT` je menší než *psz*, nebo > 0, pokud tento objekt je větší než *psz*.

### <a name="remarks"></a>Poznámky

Funkce `_tcscmp`obecného textu , která je definována v TCHAR. H, mapuje `strcmp` `wcscmp`na `_mbscmp`buď , nebo , v závislosti na znakové sadě, která je definována v době kompilace. Každá funkce provádí porovnání řetězců rozlišující malá a velká písmena a není ovlivněna národním prostředím. Další informace naleznete [v tématu strcmp, wcscmp, _mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md).

Pokud řetězec obsahuje vložené nulls, pro účely porovnání řetězec je považován za zkrácený na první vložený znak null.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CStringT::Compare`.

[!code-cpp[NVC_ATLMFC_Utilities#110](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_5.cpp)]

## <a name="cstringtcomparenocase"></a><a name="comparenocase"></a>CStringT::PorovnáníNocase

Porovná dva řetězce (malá a velká písmena).

```
int CompareNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Druhý řetězec použitý pro porovnání.

### <a name="return-value"></a>Návratová hodnota

Nula, pokud řetězce jsou identické (ignorování `CStringT` případu), <0, pokud tento objekt je `CStringT` menší než *psz* (ignorování případu), nebo >0, pokud tento objekt je větší než *psz* (ignorování případu).

### <a name="remarks"></a>Poznámky

Funkce `_tcsicmp`obecného textu , která je definována v TCHAR. H, mapuje `_stricmp` `_wcsicmp` na `_mbsicmp`buď , nebo , v závislosti na znakové sady, která je definována v době kompilace. Každá funkce provádí porovnání řetězců bez rozlišování velkých a malých písmen. Porovnání závisí na LC_CTYPE aspektnárodní prostředí, ale není LC_COLLATE. Další informace naleznete [v tématu _stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#111](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_6.cpp)]

## <a name="cstringtcstringt"></a><a name="cstringt"></a>CStringT::CStringt

Vytvoří `CStringT` objekt.

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
Ukazatel na pole znaků délky *nLength*, není null ukončen.

*nDélka*<br/>
Počet znaků v *pch*.

*Ch*<br/>
Jeden znak.

*pszSrc*<br/>
Řetězec s ukončeným hodnotou null, `CStringT` který má být zkopírován do tohoto objektu.

*pStringMgr*<br/>
Ukazatel na správce paměti `CStringT` pro objekt. Další informace `IAtlStringMgr` o správě `CStringT`paměti a pro správu paměti naleznete v [tématu Správa paměti s cstringt](../../atl-mfc-shared/memory-management-with-cstringt.md).

*strSrc*<br/>
Existující `CStringT` objekt, který má `CStringT` být do tohoto objektu zkopírován. Další informace `CThisString` o `CThisSimpleString`a najdete v části Poznámky.

*varSrc*<br/>
Objekt varianty, který má `CStringT` být do tohoto objektu zkopírován.

*BaseType*<br/>
Typ znaku třídy řetězce. Může to být jedna z následujících možností:

**char** (pro řetězce znaků ANSI).

**wchar_t** (pro řetězce znaků Unicode).

TCHAR (pro řetězce znaků ANSI i Unicode).

*bMFCDLL*<br/>
Logická hodnota, která určuje, zda je projekt knihovnou MFC DLL (TRUE) nebo ne (FALSE).

*Řetězec systemstring*<br/>
Musí `System::String`být a projekt musí být zkompilován s /clr.

*pŘetězec*<br/>
Úchyt `CStringT` pro objekt.

### <a name="remarks"></a>Poznámky

Vzhledem k tomu, že konstruktory zkopírují vstupní data do nového přidělenéúložiště, měli byste si být vědomi, že mohou mít způsobit výjimky paměti. Všimněte si, že některé z těchto konstruktorů fungují jako funkce převodu. To umožňuje nahradit například LPTSTR, kde `CStringT` se očekává objekt.

- `CStringT`( `LPCSTR` `lpsz` ): Vytvoří unicode `CStringT` z řetězce ANSI. Tento konstruktor můžete také použít k načtení prostředku řetězce, jak je znázorněno v příkladu níže.

- `CStringT(`): Vytvoří `CStringT` řetězec z unicode. `LPCWSTR` `lpsz`

- `CStringT`( `const unsigned char*` `psz` ): Umožňuje vytvořit `CStringT` z ukazatele na **nepodepsané char**.

> [!NOTE]
> Definujte _CSTRING_DISABLE_NARROW_WIDE_CONVERSION makra, chcete-li vypnout implicitní převod řetězců mezi řetězci ANSI a Unicode. Makro vylučuje z kompilace konstruktory, které podporují převod.

Všimněte si, že *strSrc* parametr může být `CStringT` nebo objekt. `CThisSimpleString` Pro `CStringT`, použijte jeden z jeho`CString`výchozích instancí ( , `CStringA`, nebo `CStringW`); pro `CThisSimpleString`, použijte **tento** ukazatel. `CThisSimpleString`deklaruje instanci [třídy CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md), což je menší třída `CStringT` řetězce s méně vestavěnou funkcí než třída.

Operátor přetížení `CSimpleStringT<>&()` vytvoří `CStringT` objekt z `CSimpleStringT` deklarace.

> [!NOTE]
> I když je `CStringT` možné vytvořit instance, které obsahují vložené prázdné znaky, doporučujeme proti němu. Volání metod a `CStringT` operátorů na objekty, které obsahují vložené prázdné znaky může způsobit nezamýšlené výsledky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#112](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_7.cpp)]

## <a name="cstringtcstringt"></a><a name="_dtorcstringt"></a>CStringT::~CStringT

Zničí `CStringT` objekt.

```
~CStringT() throw();
```

### <a name="remarks"></a>Poznámky

Zničí `CStringT` objekt.

## <a name="cstringtdelete"></a><a name="delete"></a>CStringT::Delete

Odstraní znak nebo znaky z řetězce začínající znakem v daném indexu.

```
int Delete(int iIndex, int nCount = 1);
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
Index založený na nule prvního `CStringT` znaku v objektu, který chcete odstranit.

*nCount*<br/>
Počet znaků, které mají být odebrány.

### <a name="return-value"></a>Návratová hodnota

Délka změněného řetězce.

### <a name="remarks"></a>Poznámky

Pokud *nCount* je delší než řetězec, zbytek řetězce budou odebrány.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#113](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_8.cpp)]

```Output
Before: Soccer is best,
    but hockey is quicker!
After: Soccer best,
    but hockey is quicker!
```

## <a name="cstringtfind"></a><a name="find"></a>CStringT::Najít

Vyhledá v tomto řetězci první shodu znaku nebo podřetězce.

```
int Find(PCXSTR pszSub, int iStart=0) const throw();
int Find(XCHAR ch, int iStart=0) const throw();
```

### <a name="parameters"></a>Parametry

*pszSub*<br/>
Podřetězec, který chcete vyhledat.

*iStartovat*<br/>
Index znaku v řetězci začít hledání s nebo 0 začít od začátku.

*Ch*<br/>
Jeden znak, který chcete vyhledat.

### <a name="return-value"></a>Návratová hodnota

Nulový index prvního znaku `CStringT` v tomto objektu, který odpovídá požadovanému podřetězci nebo znakům; -1, pokud není nalezen podřetězec nebo znak.

### <a name="remarks"></a>Poznámky

Funkce je přetížena přijmout oba jednotlivé znaky (podobně `strchr`jako funkce run-time) a řetězce (podobně jako `strstr`).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#114](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_9.cpp)]

## <a name="cstringtfindoneof"></a><a name="findoneof"></a>CStringt::Najít

Vyhledá v tomto řetězci první znak, který odpovídá libovolnému znaku obsaženému v *souboru pszCharSet*.

```
int FindOneOf(PCXSTR pszCharSet) const throw();
```

### <a name="parameters"></a>Parametry

*pszCharSet*<br/>
Řetězec obsahující znaky pro porovnávání.

### <a name="return-value"></a>Návratová hodnota

Index založený na nule prvního znaku v tomto řetězci, který je také v *pszCharSet*; -1, pokud není shoda.

### <a name="remarks"></a>Poznámky

Vyhledá první výskyt některého ze znaků v *pszCharSet*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#115](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_10.cpp)]

## <a name="cstringtformat"></a><a name="format"></a>CStringT::Formát

Zapisuje `CStringT` formátovaná data stejným způsobem, jakým [sprintf_s](../../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md) formátuje data do znakového pole ve stylu C.

```cpp
void __cdecl Format(UINT nFormatID, [, argument]...);
void __cdecl Format(PCXSTR pszFormat,  [, argument] ...);
```

### <a name="parameters"></a>Parametry

*nID formátu*<br/>
Identifikátor prostředku řetězce, který obsahuje řetězec řízení formátu.

*pszFormat*<br/>
Řetězec řízení formátu.

*Argument*<br/>
Volitelné argumenty

### <a name="remarks"></a>Poznámky

Tato funkce formátuje a ukládá řadu znaků `CStringT`a hodnot v . Každý volitelný argument (pokud existuje) je převeden a výstup podle odpovídající specifikace formátu v *pszFormat* nebo z prostředku řetězce identifikované *nFormatID*.

Volání se nezdaří, pokud je samotný objekt `Format`řetězce nabízen jako parametr . Například následující kód způsobí nepředvídatelné výsledky:

[!code-cpp[NVC_ATLMFC_Utilities#116](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_11.cpp)]

Další informace naleznete [v tématu Syntaxe specifikace formátu: printf a wprintf Functions](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#117](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_12.cpp)]

## <a name="cstringtformatmessage"></a><a name="formatmessage"></a>CStringT::Zpráva formátu

Formátuje řetězec zprávy.

```cpp
void __cdecl FormatMessage(UINT nFormatID, [, argument]...);
void __cdecl FormatMessage(PCXSTR pszFormat, [, argument]...);
```

### <a name="parameters"></a>Parametry

*nID formátu*<br/>
Identifikátor prostředků řetězce, který obsahuje neformátovaný text zprávy.

*pszFormat*<br/>
Odkazuje na řetězec řízení formátu. Bude naskenován pro vložky a formátován odpovídajícím způsobem. Formátovací řetězec je podobný run-time funkce *printf*-style řetězce, s výjimkou umožňuje parametry, které mají být vloženy v libovolném pořadí.

*Argument*<br/>
Volitelné argumenty

### <a name="remarks"></a>Poznámky

Funkce vyžaduje jako vstup definici zprávy. Definice zprávy je určena *pszFormat* nebo z prostředku řetězce identifikovaného *nFormatID*. Funkce zkopíruje formátovaný text `CStringT` zprávy do objektu a na požádání zprovozní všechny vložené sekvence vložení.

> [!NOTE]
> `FormatMessage`pokusí se přidělit systémovou paměť pro nově formátovaný řetězec. Pokud se tento pokus nezdaří, je automaticky vyvolána výjimka paměti.

Každá vložení musí mít odpovídající parametr za parametrem *pszFormat* nebo *nFormatID.* V textu zprávy je podporováno několik sekvencí escape pro dynamické formátování zprávy. Další informace naleznete v aplikaci Windows [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#118](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_13.cpp)]

## <a name="cstringtformatmessagev"></a><a name="formatmessagev"></a>CStringT::FormatMessageV

Formátuje řetězec zprávy pomocí seznamu argumentů proměnných.

```cpp
void FormatMessageV(PCXSTR pszFormat, va_list* pArgList);
```

### <a name="parameters"></a>Parametry

*pszFormat*<br/>
Odkazuje na řetězec řízení formátu. Bude naskenován pro vložky a formátován odpovídajícím způsobem. Formátovací řetězec je podobný řetězce `printf`formátu funkce run-time- styl, s výjimkou umožňuje parametry, které mají být vloženy v libovolném pořadí.

*seznam pArglist*<br/>
Ukazatel na seznam argumentů.

### <a name="remarks"></a>Poznámky

Funkce vyžaduje definici zprávy jako vstup, určenou *pszFormat*. Funkce zkopíruje formátovaný text zprávy a seznam proměnných argumentů do objektu, `CStringT` zpracování všech vložených sekvencí vložení na požádání.

> [!NOTE]
> `FormatMessageV`volá [CStringT::FormatMessage](#formatmessage), který se pokusí přidělit systémovou paměť pro nově formátovaný řetězec. Pokud se tento pokus nezdaří, je automaticky vyvolána výjimka paměti.

Další informace naleznete v aplikaci Windows [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) v sadě Windows SDK.

## <a name="cstringtformatv"></a><a name="formatv"></a>CStringT::FormatV

Formátuje řetězec zprávy pomocí seznamu argumentů proměnných.

```cpp
void FormatV(PCXSTR pszFormat, va_list args);
```

### <a name="parameters"></a>Parametry

*pszFormat*<br/>
Odkazuje na řetězec řízení formátu. Bude naskenován pro vložky a formátován odpovídajícím způsobem. Formátovací řetězec je podobný řetězce `printf`formátu funkce run-time- styl, s výjimkou umožňuje parametry, které mají být vloženy v libovolném pořadí.

*Args*<br/>
Ukazatel na seznam argumentů.

### <a name="remarks"></a>Poznámky

Zapíše formátovaný řetězec a seznam proměnných `CStringT` argumentů do `vsprintf_s` řetězce stejným způsobem, jakým formátuje data do pole znaků ve stylu C.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#119](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_14.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#120](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_15.cpp)]

## <a name="cstringtgetenvironmentvariable"></a><a name="getenvironmentvariable"></a>CStringT::GetEnvironmentVariable

Nastaví řetězec na hodnotu zadané proměnné prostředí.

```
BOOL GetEnvironmentVariable(PCXSTR pszVar);
```

### <a name="parameters"></a>Parametry

*pszVar*<br/>
Ukazatel na řetězec s ukončeným hodnotou null, který určuje proměnnou prostředí.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Načte hodnotu zadané proměnné z bloku prostředí volajícího procesu. Hodnota je ve formě řetězce znaků ukončeného nulou.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#121](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_16.cpp)]

## <a name="cstringtinsert"></a><a name="insert"></a>CStringT::Vložit

Vloží jeden znak nebo podřetězec na daný index v řetězci.

```
int Insert(int iIndex, PCXSTR psz);
int Insert(int iIndex, XCHAR ch);
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
Index znaku, před kterým dojde k vložení.

*psz*<br/>
Ukazatel na podřetězec, který má být vložen.

*Ch*<br/>
Znak, který má být vložen.

### <a name="return-value"></a>Návratová hodnota

Délka změněného řetězce.

### <a name="remarks"></a>Poznámky

Parametr *iIndex* identifikuje první znak, který bude přesunut, aby se uvolnilo místo pro znak nebo podřetězec. Pokud *nIndex* je nula, vložení dojde před celý řetězec. Pokud *nIndex* je vyšší než délka řetězce, funkce zřetězí současný řetězec a nový materiál poskytnutý *buď ch* nebo *psz*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#122](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_17.cpp)]

## <a name="cstringtleft"></a><a name="left"></a>CStringT::Vlevo

Extrahuje znaky *nCount* nejvíce `CStringT` vlevo z tohoto objektu a vrátí kopii extrahovaného podřetězce.

```
CStringT Left(int nCount) const;
```

### <a name="parameters"></a>Parametry

*nCount*<br/>
Počet znaků extrahovat `CStringT` z tohoto objektu.

### <a name="return-value"></a>Návratová hodnota

Objekt, `CStringT` který obsahuje kopii zadaného rozsahu znaků. Vrácený `CStringT` objekt může být prázdný.

### <a name="remarks"></a>Poznámky

Pokud *nCount* překročí délku řetězce, pak je extrahován celý řetězec. `Left`je podobná funkci `Left` Basic.

Pro vícebajtové znakové sady (MBCS) *nCount* považuje každou 8bitovou sekvenci za znak, takže *nCount* vrátí počet vícebajtových znaků vynásobený dvěma.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#123](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_18.cpp)]

## <a name="cstringtloadstring"></a><a name="loadstring"></a>CStringT::Načíst řetězec

Přečte prostředek řetězce systému Windows, identifikovaný `CStringT` *nID*, do existujícího objektu.

```
BOOL LoadString(HINSTANCE hInstance, UINT nID, WORD wLanguageID);
BOOL LoadString(HINSTANCE hInstance, UINT nID);
BOOL LoadString(UINT nID);
```

### <a name="parameters"></a>Parametry

*hInstance*<br/>
Popisovač instance modulu.

*Nid*<br/>
ID řetězce systému Windows.

*wLanguageID*<br/>
Jazyk prostředků řetězce.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud bylo zatížení prostředku úspěšné; jinak 0.

### <a name="remarks"></a>Poznámky

Načte řetězec prostředku (*nID*) ze zadaného modulu (*hInstance*) pomocí zadaného jazyka (*wLanguage*).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#124](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_19.cpp)]

## <a name="cstringtmakelower"></a><a name="makelower"></a>CStringT::MakeLower

Převede `CStringT` objekt na řetězec s malou písmena.

```
CStringT& MakeLower();
```

### <a name="return-value"></a>Návratová hodnota

Výsledný řetězec s ložených písmen.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#125](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_20.cpp)]

## <a name="cstringtmakereverse"></a><a name="makereverse"></a>CStringT::MakeReverse

Obrátí pořadí znaků v objektu. `CStringT`

```
CStringT& MakeReverse();
```

### <a name="return-value"></a>Návratová hodnota

Výsledný obrácený řetězec.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#126](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_21.cpp)]

## <a name="cstringtmakeupper"></a><a name="makeupper"></a>CStringt::MakeUpper

Převede `CStringT` objekt na řetězec s velkými písmeny.

```
CStringT& MakeUpper();
```

### <a name="return-value"></a>Návratová hodnota

Výsledný řetězec velkých písmen.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#127](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_22.cpp)]

## <a name="cstringtmid"></a><a name="mid"></a>CStringT::Střední

Extrahuje podřetězec délky *nCount* znaky z tohoto `CStringT` objektu, počínaje pozice *iFirst* (na základě nuly).

```
CStringT Mid(int iFirst, int nCount) const;
CStringT Mid(int iFirst) const;
```

### <a name="parameters"></a>Parametry

*iPrvní*<br/>
Nula index první znak v `CStringT` tomto objektu, který má být zahrnut do extrahovaného podřetězce.

*nCount*<br/>
Počet znaků extrahovat `CStringT` z tohoto objektu. Pokud tento parametr není zadán, je extrahován zbytek řetězce.

### <a name="return-value"></a>Návratová hodnota

Objekt, `CStringT` který obsahuje kopii zadaného rozsahu znaků. Všimněte si, že vrácený `CStringT` objekt může být prázdný.

### <a name="remarks"></a>Poznámky

Funkce vrátí kopii extrahovaného podřetězce. `Mid`je podobná základní střední funkce (s tím rozdílem, že indexy v Basic jsou jednozaložené).

Pro vícebajtové znakové sady (MBCS) *nCount* odkazuje na každý 8bitový znak; to znamená, že úvodní bajt a bajt stopy v jednom vícebajtovém znaku se počítají jako dva znaky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#128](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_23.cpp)]

## <a name="cstringtoemtoansi"></a><a name="oemtoansi"></a>CStringT::OemToAnsi

Převede všechny znaky `CStringT` v tomto objektu ze znakové sady OEM na znakovou sadu ANSI.

```cpp
void OemToAnsi();
```

### <a name="remarks"></a>Poznámky

Tato funkce není k dispozici, pokud je definován_UNICODE.

### <a name="example"></a>Příklad

Viz příklad [cstringt::AnsiToOem](#ansitooem).

## <a name="cstringtoperator-"></a><a name="operator_eq"></a>CStringT::operátor =

Přiřadí řetězec novou hodnotu.

```
CStringT& operator=(const CStringT& strSrc);

template<bool bMFCDLL>
CStringT& operator=(const CSimpleStringT<BaseType, bMFCDLL>& str);

CStringT& operator=(PCXSTR pszSrc);
CStringT& operator=(PCYSTR pszSrc);
CStringT& operator=(const unsigned char* pszSrc);
CStringT& operator=(XCHAR ch);
CStringT& operator=(YCHAR ch);
CStringT& operator=(const VARIANT& var);
```

### <a name="parameters"></a>Parametry

*strSrc*<br/>
A `CStringT` přiřadit k tomuto řetězci.

*Str*<br/>
Odkaz na `CThisSimpleString` objekt.

*bMFCDLL*<br/>
Logická hodnota určující, zda je projekt knihovnou DLL knihovny MFC nebo ne.

*BaseType*<br/>
Typ základní řetězec.

*var*<br/>
Variantní objekt, který má být přiřazen tomuto řetězci.

*Ch*<br/>
Znak ANSI nebo Unicode přiřadit k řetězci.

*pszSrc*<br/>
Ukazatel na původní řetězec, který je přiřazen.

### <a name="remarks"></a>Poznámky

Operátor přiřazení přijme `CStringT` jiný objekt, ukazatel znaku nebo jeden znak. Měli byste si být vědomi toho, že výjimky paměti může dojít při každém použití tohoto operátoru, protože nové úložiště může být přiděleno.

Informace o `CThisSimpleString`tématu naleznete v části Poznámky [cstringt::CStringT](#cstringt).

> [!NOTE]
> I když je `CStringT` možné vytvořit instance, které obsahují vložené prázdné znaky, doporučujeme proti němu. Volání metod a `CStringT` operátorů na objekty, které obsahují vložené prázdné znaky může způsobit nezamýšlené výsledky.

## <a name="cstringtoperator-"></a><a name="operator_add"></a>CStringT::operátor +

Zřetězí dva řetězce nebo znak a řetězec.

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

*ch1*<br/>
Znak ANSI nebo Unicode, který se má zřetězit řetězcem.

*ch2*<br/>
Znak ANSI nebo Unicode, který se má zřetězit řetězcem.

*str1*<br/>
A `CStringT` zřetězit s řetězcem nebo znakem.

*str2*<br/>
A `CStringT` zřetězit s řetězcem nebo znakem.

*psz1*<br/>
Ukazatel na řetězec s ukončeným hodnotou null, který chcete zřetězit řetězcem nebo znakem.

*psz2*<br/>
Ukazatel na řetězec zřetězit s řetězcem nebo znakem.

### <a name="remarks"></a>Poznámky

Existuje sedm formy přetížení `CStringT::operator+` funkce. První verze zřetězí dva `CStringT` existující objekty. Další dva zřetězit `CStringT` objekt a řetězec s ukončeným hodnotou null. Další dva zřetězit `CStringT` objekt a znak ANSI. Poslední dva zřetězit `CStringT` objekt a znak Unicode.

> [!NOTE]
> I když je `CStringT` možné vytvořit instance, které obsahují vložené prázdné znaky, doporučujeme proti němu. Volání metod a `CStringT` operátorů na objekty, které obsahují vložené prázdné znaky může způsobit nezamýšlené výsledky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#140](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_24.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_add_eq"></a>CStringT::operátor +=

Zřetězí znaky na konec řetězce.

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

*Str*<br/>
Odkaz na `CThisSimpleString` objekt.

*bMFCDLL*<br/>
Logická hodnota určující, zda je projekt knihovnou DLL knihovny MFC nebo ne.

*BaseType*<br/>
Typ základní řetězec.

*var*<br/>
Variantní objekt zřetězit do tohoto řetězce.

*Ch*<br/>
Znak ANSI nebo Unicode, který se má zřetězit řetězcem.

*pszSrc*<br/>
Ukazatel na původní řetězec, který je zřetězen.

*strSrc*<br/>
A `CStringT` zřetězit k tomuto řetězci.

### <a name="remarks"></a>Poznámky

Operátor přijme jiný `CStringT` objekt, ukazatel znaku nebo jeden znak. Měli byste si být vědomi toho, že výjimky paměti může dojít při každém použití `CStringT` tohoto operátoru zřetězení, protože nové úložiště může být přiděleno pro znaky přidané do tohoto objektu.

Informace o `CThisSimpleString`tématu naleznete v části Poznámky [cstringt::CStringT](#cstringt).

> [!NOTE]
> I když je `CStringT` možné vytvořit instance, které obsahují vložené prázdné znaky, doporučujeme proti němu. Volání metod a `CStringT` operátorů na objekty, které obsahují vložené prázdné znaky může způsobit nezamýšlené výsledky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#141](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_25.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_eq_eq"></a>CStringT::operátor ==

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

*ch1*<br/>
Znak ANSI nebo Unicode pro porovnání.

*ch2*<br/>
Znak ANSI nebo Unicode pro porovnání.

*str1*<br/>
A `CStringT` pro srovnání.

*str2*<br/>
A `CStringT` pro srovnání.

*psz1*<br/>
Ukazatel na řetězec s ukončeným hodnotou null pro porovnání.

*psz2*<br/>
Ukazatel na řetězec s ukončeným hodnotou null pro porovnání.

### <a name="remarks"></a>Poznámky

Testuje, zda je řetězec nebo znak na levé straně roven řetězci nebo znaku na pravé straně, a odpovídajícím způsobem vrátí hodnotu PRAVDA nebo NEPRAVDA.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#142](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_26.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_neq"></a>CStringT::operátor !=

Určuje, zda dva řetězce nejsou logicky stejné.

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

*ch1*<br/>
Znak ANSI nebo Unicode, který se má zřetězit řetězcem.

*ch2*<br/>
Znak ANSI nebo Unicode, který se má zřetězit řetězcem.

*str1*<br/>
A `CStringT` pro srovnání.

*str2*<br/>
A `CStringT` pro srovnání.

*psz1*<br/>
Ukazatel na řetězec s ukončeným hodnotou null pro porovnání.

*psz2*<br/>
Ukazatel na řetězec s ukončeným hodnotou null pro porovnání.

### <a name="remarks"></a>Poznámky

Testy, pokud řetězec nebo znak na levé straně se nerovná řetězec nebo znak na pravé straně.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#143](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_27.cpp)]

## <a name="cstringtoperator-lt"></a><a name="operator_lt"></a>CStringT::operátor&lt;

Určuje, zda je řetězec na levé straně operátoru menší než řetězec na pravé straně.

```
friend bool operator<(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parametry

*str1*<br/>
A `CStringT` pro srovnání.

*str2*<br/>
A `CStringT` pro srovnání.

*psz1*<br/>
Ukazatel na řetězec s ukončeným hodnotou null pro porovnání.

*psz2*<br/>
Ukazatel na řetězec s ukončeným hodnotou null pro porovnání.

### <a name="remarks"></a>Poznámky

Lexikografické porovnání mezi řetězci, znak po znaku, dokud:

- Najde dva odpovídající znaky nerovné a výsledek jejich porovnání je přijata v důsledku porovnání mezi řetězci.

- Nenajde žádné nerovnosti, ale jeden řetězec má více znaků než druhý a kratší řetězec je považován za menší než delší řetězec.

- Nenajde žádné nerovnosti a zjistí, že řetězce mají stejný počet znaků, a proto řetězce jsou stejné.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#144](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_28.cpp)]

## <a name="cstringtoperator-gt"></a><a name="operator_gt"></a>CStringT::operátor&gt;

Určuje, zda je řetězec na levé straně operátoru větší než řetězec na pravé straně.

```
friend bool operator>(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parametry

*str1*<br/>
A `CStringT` pro srovnání.

*str2*<br/>
A `CStringT` pro srovnání.

*psz1*<br/>
Ukazatel na řetězec s ukončeným hodnotou null pro porovnání.

*psz2*<br/>
Ukazatel na řetězec s ukončeným hodnotou null pro porovnání.

### <a name="remarks"></a>Poznámky

Lexikografické porovnání mezi řetězci, znak po znaku, dokud:

- Najde dva odpovídající znaky nerovné a výsledek jejich porovnání je přijata v důsledku porovnání mezi řetězci.

- Nenajde žádné nerovnosti, ale jeden řetězec má více znaků než druhý a kratší řetězec je považován za menší než delší řetězec.

- Nenajde žádné nerovnosti a zjistí, že řetězce mají stejný počet znaků, takže řetězce jsou stejné.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#145](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_29.cpp)]

## <a name="cstringtoperator-lt"></a><a name="operator_lt_eq"></a>CStringT::operátor&lt;=

Určuje, zda je řetězec na levé straně operátoru menší nebo roven řetězci na pravé straně.

```
friend bool operator<=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parametry

*str1*<br/>
A `CStringT` pro srovnání.

*str2*<br/>
A `CStringT` pro srovnání.

*psz1*<br/>
Ukazatel na řetězec s ukončeným hodnotou null pro porovnání.

*psz2*<br/>
Ukazatel na řetězec s ukončeným hodnotou null pro porovnání.

### <a name="remarks"></a>Poznámky

Lexikografické porovnání mezi řetězci, znak po znaku, dokud:

- Najde dva odpovídající znaky nerovné a výsledek jejich porovnání je přijata v důsledku porovnání mezi řetězci.

- Nenajde žádné nerovnosti, ale jeden řetězec má více znaků než druhý a kratší řetězec je považován za menší než delší řetězec.

- Nenajde žádné nerovnosti a zjistí, že řetězce mají stejný počet znaků, takže řetězce jsou stejné.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#146](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_30.cpp)]

## <a name="cstringtoperator-gt"></a><a name="operator_gt_eq"></a>CStringT::operátor&gt;=

Určuje, zda je řetězec na levé straně operátoru větší nebo roven řetězci na pravé straně.

```
friend bool operator>=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parametry

*str1*<br/>
A `CStringT` pro srovnání.

*str2*<br/>
A `CStringT` pro srovnání.

*psz1*<br/>
Ukazatel na řetězec pro porovnání.

*psz2*<br/>
Ukazatel na řetězec pro porovnání.

### <a name="remarks"></a>Poznámky

Lexikografické porovnání mezi řetězci, znak po znaku, dokud:

- Najde dva odpovídající znaky nerovné a výsledek jejich porovnání je přijata v důsledku porovnání mezi řetězci.

- Nenajde žádné nerovnosti, ale jeden řetězec má více znaků než druhý a kratší řetězec je považován za menší než delší řetězec.

- Nenajde žádné nerovnosti a zjistí, že řetězce mají stejný počet znaků, takže řetězce jsou stejné.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#147](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_31.cpp)]

## <a name="cstringtremove"></a><a name="remove"></a>CStringT::Odebrat

Odebere všechny instance zadaného znaku z řetězce.

```
int Remove(XCHAR chRemove);
```

### <a name="parameters"></a>Parametry

*chOdebrat*<br/>
Znak, který má být odebrán z řetězce.

### <a name="return-value"></a>Návratová hodnota

Počet znaků odebraných z řetězce. Nula, pokud řetězec není změněn.

### <a name="remarks"></a>Poznámky

Porovnání znaku jsou rozlišována malá a velká písmena.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#129](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_32.cpp)]

## <a name="cstringtreplace"></a><a name="replace"></a>CStringT::Nahradit

Existují dvě verze `Replace`aplikace . První verze nahradí jednu nebo více kopií podřetězce pomocí jiného podřetězce. Oba podřetězce jsou ukončeny s nulou. Druhá verze nahradí jednu nebo více kopií znaku pomocí jiného znaku. Obě verze pracují s daty `CStringT`znaků uloženými v aplikaci .

```
int Replace(PCXSTR pszOld, PCXSTR pszNew);
int Replace(XCHAR chOld, XCHAR chNew);
```

### <a name="parameters"></a>Parametry

*pszOld*<br/>
Ukazatel na řetězec s ukončeným hodnotou null, který má být nahrazen *pszNew*.

*pszNový*<br/>
Ukazatel na řetězec ukončený nulou, který nahrazuje *pszOld*.

*chStarý*<br/>
Znak, který má být nahrazen *chNew*.

*chNovinka*<br/>
Znak nahrazující *chOld*.

### <a name="return-value"></a>Návratová hodnota

Vrátí počet nahrazených instancí znaku nebo podřetězce nebo nula, pokud se řetězec nezmění.

### <a name="remarks"></a>Poznámky

`Replace`můžete změnit délku řetězce, protože *pszNew* a *pszOld* nemusí být stejné délky, a několik kopií starého podřetězce lze změnit na nový. Funkce provádí shodu rozlišující malá a velká písmena.

Příklady `CStringT` instancí `CString` `CStringA`jsou `CStringW`, a .

Pro `CStringA` `Replace` , pracuje se znaky ANSI nebo vícebajtové (MBCS). Pro `CStringW` `Replace` , pracuje s širokými znaky.

Pro `CString`, znak datový typ je vybrán v době kompilace, na základě toho, zda jsou definovány konstanty v následující tabulce.

|Definovaná konstanta|Datový typ znaku|
|----------------------|-------------------------|
|_unicode|Široké znaky|
|_mbcs|Vícebajtové znaky|
|Ani jedno|Jednobajtové znaky|
|Obojí|Nedefinované|

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#200](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_33.cpp)]

## <a name="cstringtreversefind"></a><a name="reversefind"></a>CStringT::Reverznífind

Vyhledá tento `CStringT` objekt pro poslední shodu znaku.

```
int ReverseFind(XCHAR ch) const throw();
```

### <a name="parameters"></a>Parametry

*Ch*<br/>
Znak, který chcete vyhledat.

### <a name="return-value"></a>Návratová hodnota

Nulový index posledního znaku `CStringT` v tomto objektu, který odpovídá požadovanému znaku, nebo -1, pokud znak nebyl nalezen.

### <a name="remarks"></a>Poznámky

Funkce je podobná funkci `strrchr`run-time .

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#130](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_34.cpp)]

## <a name="cstringtright"></a><a name="right"></a>CStringT::Doprava

Extrahuje poslední (to znamená, že nejvíce `CStringT` vpravo) *nCount* znaky z tohoto objektu a vrátí kopii extrahovanépodstring.

```
CStringT Right(int nCount) const;
```

### <a name="parameters"></a>Parametry

*nCount*<br/>
Počet znaků extrahovat `CStringT` z tohoto objektu.

### <a name="return-value"></a>Návratová hodnota

Objekt, `CStringT` který obsahuje kopii zadaného rozsahu znaků. Všimněte si, že vrácený `CStringT` objekt může být prázdný.

### <a name="remarks"></a>Poznámky

Pokud *nCount* překročí délku řetězce, pak je extrahován celý řetězec. `Right`je podobná základní `Right` funkci (s tím rozdílem, že indexy v Basic jsou založeny na nule).

Pro vícebajtové znakové sady (MBCS) *nCount* odkazuje na každý 8bitový znak; to znamená, že úvodní bajt a bajt stopy v jednom vícebajtovém znaku se počítají jako dva znaky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#131](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_35.cpp)]

## <a name="cstringtsetsysstring"></a><a name="setsysstring"></a>CStringT::SetSysString

Přerozdělí BSTR, na který je odkazováno `CStringT` *pbstr,* a zkopíruje do něj obsah objektu, včetně znaku NULL.

```
BSTR SetSysString(BSTR* pbstr) const;
```

### <a name="parameters"></a>Parametry

*pbstr*<br/>
Ukazatel na řetězec znaku.

### <a name="return-value"></a>Návratová hodnota

Nový řetězec.

### <a name="remarks"></a>Poznámky

V závislosti na `CStringT` obsahu objektu může změnit hodnotu BSTR odkazuje *pbstr.* Funkce vyvolá pokud `CMemoryException` neexistuje dostatek paměti.

Tato funkce se obvykle používá ke změně hodnoty řetězců předaných odkazem pro automatizaci.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#132](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_36.cpp)]

## <a name="cstringtspanexcluding"></a><a name="spanexcluding"></a>CStringT::SpanBez

Extrahuje znaky z řetězce, počínaje prvním znakem, které nejsou v sadě znaků identifikovaných *pszCharSet*.

```
CStringT SpanExcluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>Parametry

*pszCharSet*<br/>
Řetězec interpretovaný jako sada znaků.

### <a name="return-value"></a>Návratová hodnota

Podřetězec, který obsahuje znaky v řetězci, které nejsou v *pszCharSet*, počínaje prvním znakem v řetězci a končící prvním znakem nalezeným v řetězci, který je také v *pszCharSet* (to znamená počínaje prvním znakem v řetězci a až po první znak v řetězci, který je nalezen *pszCharSet*). Vrátí celý řetězec, pokud je v řetězci nalezen žádný znak v *pszCharSet.*

### <a name="remarks"></a>Poznámky

`SpanExcluding`extrahuje a vrátí všechny znaky předcházející prvnímu výskytu znaku z *pszCharSet* (jinými slovy, znak z *pszCharSet* a všechny znaky následující v řetězci, nejsou vráceny). Pokud žádný znak z *pszCharSet* je `SpanExcluding` nalezen v řetězci, vrátí celý řetězec.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#133](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_37.cpp)]

## <a name="cstringtspanincluding"></a><a name="spanincluding"></a>CStringT::SpanIncluding

Extrahuje znaky z řetězce, počínaje prvním znakem, které jsou v sadě znaků identifikovaných *pszCharSet*.

```
CStringT SpanIncluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>Parametry

*pszCharSet*<br/>
Řetězec interpretovaný jako sada znaků.

### <a name="return-value"></a>Návratová hodnota

Podřetězec, který obsahuje znaky v řetězci, které jsou v *pszCharSet*, počínaje prvním znakem v řetězci a končící, když je nalezen znak v řetězci, který není v *pszCharSet*. `SpanIncluding`vrátí prázdný podřetězec, pokud první znak v řetězci není v zadané sadě.

### <a name="remarks"></a>Poznámky

Pokud první znak řetězce není v znakové `SpanIncluding` sadě, vrátí prázdný řetězec. V opačném případě vrátí posloupnost po sobě jdoucích znaků, které jsou v sadě.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#134](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_38.cpp)]

## <a name="cstringttokenize"></a><a name="tokenize"></a>CStringT::Tokenize

Najde další token v cílovém řetězci.

```
CStringT Tokenize(PCXSTR pszTokens, int& iStart) const;
```

### <a name="parameters"></a>Parametry

*pszTokeny*<br/>
Řetězec obsahující oddělovače tokenů. Pořadí těchto oddělovačů není důležité.

*iStartovat*<br/>
Index založený na nule pro zahájení hledání.

### <a name="return-value"></a>Návratová hodnota

Objekt `CStringT` obsahující aktuální hodnotu tokenu.

### <a name="remarks"></a>Poznámky

Funkce `Tokenize` najde další token v cílovém řetězci. Sada znaků v *pszTokens* určuje možné oddělovače tokenu, který má být nalezen. Při každém `Tokenize` volání funkce začíná na *iStart*, přeskočí úvodní `CStringT` oddělovače a vrátí objekt obsahující aktuální token, což je řetězec znaků až do dalšího znaku oddělovače. Hodnota *iStart* je aktualizována na pozici za koncovým znakem oddělovače nebo -1, pokud bylo dosaženo konce řetězce. Další tokeny mohou být rozděleny ze zbytku cílového `Tokenize`řetězce řadou volání do , pomocí *iStart* sledovat, kde v řetězci další token má být čten. Pokud nejsou k dispozici žádné další tokeny funkce vrátí prázdný řetězec a *iStart* bude nastavena na -1.

Na rozdíl od crt tokenize funkce [jako strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l](../../c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md), `Tokenize` nemění cílový řetězec.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#135](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_39.cpp)]

### <a name="remarks"></a>Poznámky

Výstup z tohoto příkladu je následující:

```Output
Resulting Token: First
Resulting Token: Second
Resulting Token: Third
```

## <a name="cstringttrim"></a><a name="trim"></a>CStringT::Oříznutí

Ořízne úvodní a koncové znaky z řetězce.

```
CStringT& Trim(XCHAR chTarget);
CStringT& Trim(PCXSTR pszTargets);
CStringT& Trim();
```

### <a name="parameters"></a>Parametry

*chCíl*<br/>
Cílový znak, který má být oříznut.

*pszCíle*<br/>
Ukazatel na řetězec obsahující cílové znaky, které mají být oříznuty. Všechny počáteční a koncové výskyty znaků v *pszTarget* budou `CStringT` oříznuty z objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí oříznutý řetězec.

### <a name="remarks"></a>Poznámky

Odstraní všechny hlavní a koncové výskyty jedné z následujících událostí:

- Znak určený *chTarget*.

- Všechny znaky nalezené v řetězci *určeném pszTargets*.

- Mezery.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#136](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_40.cpp)]

### <a name="remarks"></a>Poznámky

Výstup z tohoto příkladu je následující:

```Output
Before: "******Soccer is best, but liquor is quicker!!!!!"
After : "Soccer is best, but liquor is quicker"
```

## <a name="cstringttrimleft"></a><a name="trimleft"></a>CStringT::Oříznutívlevo

Ořízne úvodní znaky z řetězce.

```
CStringT& TrimLeft(XCHAR chTarget);
CStringT& TrimLeft(PCXSTR pszTargets);
CStringT& TrimLeft();
```

### <a name="parameters"></a>Parametry

*chCíl*<br/>
Cílový znak, který má být oříznut.

*pszCíle*<br/>
Ukazatel na řetězec obsahující cílové znaky, které mají být oříznuty. Všechny hlavní výskyty znaků v *pszTarget* budou `CStringT` oříznuty z objektu.

### <a name="return-value"></a>Návratová hodnota

Výsledný oříznutý řetězec.

### <a name="remarks"></a>Poznámky

Odstraní všechny hlavní a koncové výskyty jedné z následujících událostí:

- Znak určený *chTarget*.

- Všechny znaky nalezené v řetězci *určeném pszTargets*.

- Mezery.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#137](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_41.cpp)]

## <a name="cstringttrimright"></a><a name="trimright"></a>cstringt::TrimRight

Ořízne koncové znaky z řetězce.

```
CStringT& TrimRight(XCHAR chTarget);
CStringT& TrimRight(PCXSTR pszTargets);
CStringT& TrimRight();
```

### <a name="parameters"></a>Parametry

*chCíl*<br/>
Cílový znak, který má být oříznut.

*pszCíle*<br/>
Ukazatel na řetězec obsahující cílové znaky, které mají být oříznuty. Všechny koncové výskyty znaků v *pszTarget* budou oříznuty z objektu. `CStringT`

### <a name="return-value"></a>Návratová hodnota

Vrátí `CStringT` objekt, který obsahuje oříznutý řetězec.

### <a name="remarks"></a>Poznámky

Odstraní koncové výskyty jedné z následujících událostí:

- Znak určený *chTarget*.

- Všechny znaky nalezené v řetězci *určeném pszTargets*.

- Mezery.

Verze `CStringT& TrimRight(XCHAR chTarget)` přijme jeden parametr znaku a odebere všechny kopie `CStringT` tohoto znaku z konce dat řetězce. Začíná od konce řetězce a pracuje směrem dopředu. Zastaví se, když najde jiný `CSTringT` znak nebo když dojde k datům znaků.

Verze `CStringT& TrimRight(PCXSTR pszTargets)` přijímá řetězec s ukončeným hodnotou null, který obsahuje všechny různé znaky, které mají být vyhledány. Odebere všechny kopie těchto znaků `CStringT` v objektu. Začíná na konci řetězce a pracuje směrem dopředu. Zastaví se, když najde znak, který není v `CStringT` cílovém řetězci, nebo když dojde k datům znaků. Nepokouší se spárovat celý cílový řetězec s podřetězcem na konci . `CStringT`

Verze `CStringT& TrimRight()` nevyžaduje žádné parametry. Ořízne všechny koncové znaky prázdné ho `CStringT` od konce řetězce. Prázdné znaky mohou být zalomení řádků, mezery nebo karty.

-

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#138](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_42.cpp)]

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Sdílené třídy KNIHOVNY ATL/Knihovny MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)<br/>
[CSimpleStringT – třída](../../atl-mfc-shared/reference/csimplestringt-class.md)
