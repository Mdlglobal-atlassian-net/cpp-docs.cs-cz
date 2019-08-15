---
title: CStringt – třída
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
ms.openlocfilehash: a411ed54a73a0dee49ebbd9ccacbd7c6f8e69ca5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491643"
---
# <a name="cstringt-class"></a>CStringt – třída

Tato třída reprezentuje `CStringT` objekt.

## <a name="syntax"></a>Syntaxe

```
template<typename BaseType, class StringTraits>
class CStringT :
    public CSimpleStringT<BaseType,
        _CSTRING_IMPL_::_MFCDLLTraitsCheck<BaseType, StringTraits>::c_bIsMFCDLLTraits>
```

#### <a name="parameters"></a>Parametry

*BaseType*<br/>
Typ znaku řetězcové třídy. Může být jedna z následujících akcí:

- **znak** (pro řetězce znaků ANSI).

- **wchar_t** (pro řetězce znaků Unicode).

- TCHAR (pro řetězce znaků ANSI a Unicode).

*StringTraits*<br/>
Určuje, zda třída String potřebuje podporu knihovny jazyka C run-time (CRT) a kde jsou umístěny prostředky řetězců. Může být jedna z následujících akcí:

- **StrTraitATL < wchar_t** &#124; char &#124; **TCHAR, ChTraitsCRT < wchar_t** &#124; **char** &#124; **> >**

   Třída vyžaduje podporu CRT a hledá řetězce prostředků v modulu určeném `m_hInstResource` (členem třídy modulu aplikace).

- **StrTraitATL < wchar_t** &#124; char &#124; **TCHAR, ChTraitsOS < wchar_t** &#124; **char** &#124; **> >**

   Třída nevyžaduje podporu CRT a hledá řetězce prostředků v modulu určeném `m_hInstResource` (členem třídy modulu aplikace).

- **StrTraitMFC < wchar_t** &#124; char &#124; **TCHAR, ChTraitsCRT < wchar_t** &#124; **char** &#124; **> >**

   Třída vyžaduje podporu CRT a hledá řetězce prostředků pomocí standardního vyhledávacího algoritmu MFC.

- **StrTraitMFC < wchar_t** &#124; char &#124; **TCHAR, ChTraitsOS < wchar_t** &#124; **char** &#124; **> >**

   Třída nevyžaduje podporu CRT a hledá řetězce prostředků pomocí standardního vyhledávacího algoritmu MFC.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CStringT::CStringT](#cstringt)|Sestaví `CStringT` objekt různými způsoby.|
|[CStringT::~CStringT](#_dtorcstringt)|`CStringT` Odstraní objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CStringT::AllocSysString](#allocsysstring)|Přidělí datový objekt BSTR `CStringT` z dat.|
|[CStringT::AnsiToOem](#ansitooem)|Provede místní převod ze znakové sady ANSI na znakovou sadu OEM.|
|[CStringT::AppendFormat](#appendformat)|Připojí formátovaná data k existujícímu `CStringT` objektu.|
|[CStringt:: COLLATE](#collate)|Porovná dva řetězce (rozlišuje velká a malá písmena, používá informace specifické pro národní prostředí).|
|[CStringT::CollateNoCase](#collatenocase)|Porovná dva řetězce (nerozlišuje velikost písmen, používá informace specifické pro národní prostředí).|
|[CStringt:: Compare](#compare)|Porovná dva řetězce (rozlišuje velká a malá písmena).|
|[CStringT::CompareNoCase](#comparenocase)|Porovná dva řetězce (nerozlišuje velikost písmen).|
|[CStringT::Delete](#delete)|Odstraní znak nebo znaky z řetězce.|
|[CStringt:: Find](#find)|Vyhledá znak nebo podřetězec uvnitř většího řetězce.|
|[CStringT::FindOneOf](#findoneof)|Vyhledá první shodný znak ze sady.|
|[CStringT::Format](#format)|Zformátuje řetězec jako `sprintf` .|
|[CStringT::FormatMessage](#formatmessage)|Formátuje řetězec zprávy.|
|[CStringT::FormatMessageV](#formatmessagev)|Formátuje řetězec zprávy pomocí seznamu argumentů proměnných.|
|[CStringT::FormatV](#formatv)|Zformátuje řetězec pomocí seznamu proměnných argumentů.|
|[CStringT::GetEnvironmentVariable](#getenvironmentvariable)|Nastaví řetězec na hodnotu zadané proměnné prostředí.|
|[CStringt:: INSERT](#insert)|Vloží jeden znak nebo podřetězec na daný index v rámci řetězce.|
|[CStringt:: Left](#left)|Extrahuje levou část řetězce.|
|[CStringT::LoadString](#loadstring)|Načte existující `CStringT` objekt z prostředku Windows.|
|[CStringT::MakeLower](#makelower)|Převede všechny znaky v tomto řetězci na malá písmena.|
|[CStringT::MakeReverse](#makereverse)|Obrátí řetězec.|
|[CStringT::MakeUpper](#makeupper)|Převede všechny znaky v tomto řetězci na velká písmena.|
|[CStringT::Mid](#mid)|Extrahuje střední část řetězce.|
|[CStringT::OemToAnsi](#oemtoansi)|Provede místní převod ze znakové sady OEM na znakovou sadu ANSI.|
|[CStringt:: Remove](#remove)|Odebere označené znaky z řetězce.|
|[CStringt:: Replace](#replace)|Nahradí označené znaky dalšími znaky.|
|[CStringt:: ReverseFind](#reversefind)|Najde znak uvnitř většího řetězce; začíná od konce.|
|[CStringt:: Right](#right)|Extrahuje pravou část řetězce.|
|[CStringT::SetSysString](#setsysstring)|Nastaví existující objekt BSTR daty z `CStringT` objektu.|
|[CStringt:: SpanExcluding](#spanexcluding)|Extrahuje znaky z řetězce počínaje prvním znakem, který není v sadě znaků identifikovaných `pszCharSet`.|
|[CStringt:: SpanIncluding](#spanincluding)|Extrahuje podřetězec, který obsahuje pouze znaky v sadě.|
|[CStringt:: tokenizovat](#tokenize)|Extrahuje zadané tokeny do cílového řetězce.|
|[CStringT::Trim](#trim)|Ořízne všechny úvodní a koncové prázdné znaky z řetězce.|
|[CStringt:: TrimLeft](#trimleft)|Ořízne z řetězce úvodní prázdné znaky.|
|[CStringt:: TrimRight](#trimright)|Ořízne v řetězci koncové prázdné znaky.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[CStringt:: operator =](#operator_eq)|Přiřadí novou hodnotu `CStringT` objektu.|
|[CStringt:: operator +](#operator_add)|Zřetězí dva řetězce nebo znak a řetězec.|
|[CStringt:: operator + =](#operator_add_eq)|Zřetězí nový řetězec na konec existujícího řetězce.|
|[CStringt:: operator = =](#operator_eq_eq)|Určuje, zda jsou dva řetězce logicky stejné.|
|[CStringt:: operator! =](#operator_neq)|Určuje, zda jsou dva řetězce logicky neshodné.|
|[CStringt:: – operátor&lt;](#operator_lt)|Určuje, zda je řetězec na levé straně operátoru menší než řetězec na pravé straně.|
|[CStringt:: – operátor&gt;](#operator_gt)|Určuje, zda je řetězec na levé straně operátoru větší než řetězec na pravé straně.|
|[CStringt:: – operátor&lt;=](#operator_lt_eq)|Určuje, zda je řetězec na levé straně operátoru menší než nebo roven řetězci na pravé straně.|
|[CStringt:: – operátor&gt;=](#operator_gt_eq)|Určuje, zda je řetězec na levé straně operátoru větší než nebo roven řetězci na pravé straně.|

## <a name="remarks"></a>Poznámky

`CStringT`dědí z [třídy CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md). Pokročilé funkce, jako je například manipulace se znaky, řazení a hledání, jsou implementovány nástrojem `CStringT`.

> [!NOTE]
> `CStringT`objekty jsou schopny vyvolávání výjimek. K tomu dochází, `CStringT` když z jakéhokoli důvodu dojde k vykonání objektu z nějaké paměti.

`CStringT` Objekt se skládá z sekvence znaků s proměnlivou délkou. `CStringT`poskytuje funkce a operátory pomocí syntaxe, která je podobná syntaxi Basic. Operátory zřetězení a porovnávání, společně s zjednodušenou správou paměti `CStringT` , usnadňují používání objektů než běžných polí znaků.

> [!NOTE]
>  I když je možné vytvořit `CStringT` instance, které obsahují vložené znaky null, doporučujeme proti ní. Volání metod a operátorů `CStringT` na objekty, které obsahují vložené znaky null, mohou způsobit neočekávané výsledky.

Pomocí různých kombinací `BaseType` parametrů `StringTraits` a mohou `CStringT` objekty přijít do následujících typů, které jsou předdefinovány knihovnou ATL.

Při použití v aplikaci ATL:

`CString`, `CStringA` a`CStringW` jsou exportovány z knihovny MFC DLL (MFC90. DLL), nikdy z knihoven DLL uživatele. To je provedeno, aby `CStringT` nedocházelo k násobení definování.

> [!NOTE]
>  Pokud váš kód obsahuje alternativní řešení pro chyby linkeru, které jsou popsány v tématu [Export třídy řetězců pomocí CStringT](../../atl-mfc-shared/exporting-string-classes-using-cstringt.md), měli byste tento kód odebrat. Už není potřeba.

V aplikacích založených na knihovně MFC jsou k dispozici následující typy řetězců:

|CStringt – typ|Deklarace|
|-------------------|-----------------|
|`CStringA`|Řetězec typu znaku ANSI s podporou CRT.|
|`CStringW`|Řetězec typu znaku Unicode s podporou CRT.|
|`CString`|Typy znaků ANSI i Unicode s podporou CRT.|

Následující typy řetězců jsou k dispozici v projektech, kde je definována ATL_CSTRING_NO_CRT:

|CStringt – typ|Deklarace|
|-------------------|-----------------|
|`CAtlStringA`|Řetězec typu znaků ANSI bez podpory CRT.|
|`CAtlStringW`|Řetězec typu znaku Unicode bez podpory CRT.|
|`CAtlString`|Typy znaků ANSI i Unicode bez podpory CRT.|

Následující typy řetězců jsou k dispozici v projektech, kde není definován ATL_CSTRING_NO_CRT:

|CStringt – typ|Deklarace|
|-------------------|-----------------|
|`CAtlStringA`|Řetězec typu znaku ANSI s podporou CRT.|
|`CAtlStringW`|Řetězec typu znaku Unicode s podporou CRT.|
|`CAtlString`|Typy znaků ANSI i Unicode s podporou CRT.|

`CString`objekty mají také následující vlastnosti:

- `CStringT`objekty mohou být růst v důsledku operací zřetězení.

- `CStringT`objekty následují jako "sémantika hodnoty". `CStringT` Objekt si můžete představit jako skutečný řetězec, nikoli jako ukazatel na řetězec.

- Můžete volně dosadit `CStringT` objekty pro `PCXSTR` argumenty funkce.

- Vlastní Správa paměti pro vyrovnávací paměti řetězců. Další informace najdete v tématu [Správa paměti a CString](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="cstringt-predefined-types"></a>Předdefinované typy CStringt

Vzhledem `CStringT` k tomu, že používá argument šablony pro definování typu znaku (buď [wchar_t](../../c-runtime-library/standard-types.md) nebo [char](../../c-runtime-library/standard-types.md)), typy parametrů metody mohou být složité v časech. Pro zjednodušení tohoto problému je definována sada předdefinovaných typů, která se používá v celé `CStringT` třídě. V následující tabulce jsou uvedeny různé typy:

|Name|Popis|
|----------|-----------------|
|`XCHAR`|Jeden znak (buď **wchar_t** nebo **char**) se stejným `CStringT` typem znaku jako objekt.|
|`YCHAR`|Jeden znak (buď **wchar_t** nebo **char**) s `CStringT` typem opačného znaku jako objekt.|
|`PXSTR`|Ukazatel na řetězec znaků (buď **wchar_t** , nebo **char**) se stejným `CStringT` typem znaku jako objekt.|
|`PYSTR`|Ukazatel na řetězec znaků (buď **wchar_t** , nebo **char**) s `CStringT` typem opačného znaku jako objekt.|
|`PCXSTR`|Ukazatel na řetězec **konstantního** znaku (buď **wchar_t** , nebo **char**) se `CStringT` stejným typem znaku jako objekt.|
|`PCYSTR`|Ukazatel na řetězec **konstantního** znaku (buď **wchar_t** , nebo **char**) s typem `CStringT` opačného znaku jako objekt.|

> [!NOTE]
>  Kód, který dříve používal nedokumentované metody `CString` ( `AssignCopy`například), musí být nahrazen kódem, který používá následující dokumentované `GetBuffer` metody `CStringT` (například nebo `ReleaseBuffer`). Tyto metody jsou zděděné `CSimpleStringT`z.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)

`CStringT`

## <a name="requirements"></a>Požadavky

|Záhlaví|Použít pro|
|------------|-------------|
|CStringT. h|Řetězcové objekty pouze MFC|
|atlstr.h|Objekty řetězce bez knihovny MFC|

##  <a name="allocsysstring"></a>CStringt:: AllocSysString

Přidělí řetězec kompatibilní s automatizací typu BSTR a zkopíruje do něj obsah `CStringT` objektu, včetně ukončujícího znaku null.

```
BSTR AllocSysString() const;
```

### <a name="return-value"></a>Návratová hodnota

Nově přidělený řetězec.

### <a name="remarks"></a>Poznámky

V programech MFC je vyvolána [Třída CMemoryException](../../mfc/reference/cmemoryexception-class.md) , pokud existuje nedostatek paměti. V programech ATL je vyvolána výjimka [CAtlException](../../atl/reference/catlexception-class.md) . Tato funkce se obvykle používá k vrácení řetězců pro automatizaci.

Obecně platí, že pokud je tento řetězec předán funkci modelu COM jako parametr [in], pak volající vyžaduje uvolnění řetězce. To lze provést pomocí [SysFreeString](/windows/win32/api/oleauto/nf-oleauto-sysfreestring), jak je popsáno v Windows SDK. Další informace naleznete v tématu [přidělování a uvolňování paměti pro BSTR](../../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md).

Další informace o funkcích alokace OLE v systému Windows naleznete v tématu [případě](/windows/win32/api/oleauto/nf-oleauto-sysallocstring) v Windows SDK.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CStringT::AllocSysString`.

[!code-cpp[NVC_ATLMFC_Utilities#105](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_1.cpp)]

##  <a name="ansitooem"></a>CStringt:: AnsiToOem

Převede všechny znaky v tomto `CStringT` objektu ze znakové sady ANSI na znakovou sadu OEM.

```
void AnsiToOem();
```

### <a name="remarks"></a>Poznámky

Funkce není k dispozici, pokud je definována _UNICODE.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#106](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_2.cpp)]

##  <a name="appendformat"></a>CStringt:: AppendFormat

Připojí formátovaná data k existujícímu `CStringT` objektu.

```
void __cdecl AppendFormat(PCXSTR pszFormat, [, argument] ...);
void __cdecl AppendFormat(UINT nFormatID, [, argument] ...);
```

### <a name="parameters"></a>Parametry

*pszFormat*<br/>
Řetězec řízení formátu.

*nFormatID*<br/>
Identifikátor prostředku řetězce, který obsahuje řetězec řízení formátu.

*argument*<br/>
Volitelné argumenty

### <a name="remarks"></a>Poznámky

Tato funkce formátuje a připojuje řadu znaků a hodnot v `CStringT`. Každý volitelný argument (pokud existuje) je převeden a připojen podle odpovídající specifikace formátu v *pszFormat* nebo z prostředku řetězce identifikovaného parametrem *nFormatID*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#107](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_3.cpp)]

##  <a name="collate"></a>CStringt:: COLLATE

Porovná dva řetězce pomocí funkce `_tcscoll`obecného textu.

```
int Collate(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Druhý řetězec použitý pro porovnání.

### <a name="return-value"></a>Návratová hodnota

Nula, pokud jsou řetězce identické, < 0, `CStringT` Pokud je tento objekt menší než *PSZ*, nebo > 0 `CStringT` , pokud je tento objekt větší než *PSZ*.

### <a name="remarks"></a>Poznámky

Funkce `_tcscoll`obecného textu, která je definována v Tchar. H, mapuje na buď `strcoll`, `wcscoll`nebo `_mbscoll`, v závislosti na znakové sadě definované v době kompilace. Každá funkce provádí porovnání řetězců s rozlišováním velkých a malých písmen podle znakové stránky, která se právě používá. Další informace najdete v tématu [strcoll –, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md).

##  <a name="collatenocase"></a>CStringt:: CollateNoCase

Porovná dva řetězce pomocí funkce `_tcscoll`obecného textu.

```
int CollateNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Druhý řetězec použitý pro porovnání.

### <a name="return-value"></a>Návratová hodnota

Nula, pokud jsou řetězce identické (ignorování velkých a malých písmen), `CStringT` < 0, pokud je tento objekt menší než *PSZ* (ignorování velkých a malých `CStringT` písmen), nebo > 0, pokud je tento objekt větší než *PSZ* (ignorování případu).

### <a name="remarks"></a>Poznámky

Funkce `_tcscoll`obecného textu, která je definována v Tchar. H, mapuje na buď `stricoll`, `wcsicoll`nebo `_mbsicoll`, v závislosti na znakové sadě definované v době kompilace. Každá funkce provede porovnání řetězců bez rozlišování velkých a malých písmen, podle znakové stránky, která se právě používá. Další informace najdete v tématu [strcoll –, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#109](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_4.cpp)]

##  <a name="compare"></a>CStringt:: Compare

Porovná dva řetězce (rozlišuje velká a malá písmena).

```
int Compare(PCXSTR psz) const;
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Druhý řetězec použitý pro porovnání.

### <a name="return-value"></a>Návratová hodnota

Nula, pokud jsou řetězce identické, < 0, `CStringT` Pokud je tento objekt menší než *PSZ*, nebo > 0 `CStringT` , pokud je tento objekt větší než *PSZ*.

### <a name="remarks"></a>Poznámky

Funkce `_tcscmp`obecného textu, která je definována v Tchar. H, mapuje na buď `strcmp`, `wcscmp`nebo `_mbscmp`, v závislosti na znakové sadě definované v době kompilace. Každá funkce provádí porovnání řetězců s rozlišováním velkých a malých písmen a není ovlivněno národním prostředím. Další informace najdete v tématu [strcmp, wcscmp, _mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md).

Pokud řetězec obsahuje vložené hodnoty null, pro účely porovnání je řetězec považován za zkrácený při prvním vloženém znaku null.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CStringT::Compare`.

[!code-cpp[NVC_ATLMFC_Utilities#110](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_5.cpp)]

##  <a name="comparenocase"></a>CStringt:: CompareNoCase

Porovná dva řetězce (nerozlišuje velikost písmen).

```
int CompareNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Druhý řetězec použitý pro porovnání.

### <a name="return-value"></a>Návratová hodnota

Nula, pokud jsou řetězce identické (ignorování velkých a malých písmen), `CStringT` < 0, pokud je tento objekt menší než *PSZ* (ignorování velkých a malých `CStringT` písmen), nebo > 0, pokud je tento objekt větší než *PSZ* (ignorování případu).

### <a name="remarks"></a>Poznámky

Funkce `_tcsicmp`obecného textu, která je definována v Tchar. H, mapuje na buď `_stricmp`, `_wcsicmp` nebo `_mbsicmp`, v závislosti na znakové sadě definované v době kompilace. Každá funkce provede porovnání řetězců bez rozlišování velkých a malých písmen. Porovnání závisí na aspektu LC_CTYPE národního prostředí, ale ne na LC_COLLATE. Další informace najdete v tématu [_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#111](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_6.cpp)]

##  <a name="cstringt"></a>CStringt:: CStringt

`CStringT` Vytvoří objekt.

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
Ukazatel na pole znaků s délkou *nLength*, ne zakončené znakem null.

*nLength*<br/>
Počet znaků v souboru *PCH*.

*ch*<br/>
Jeden znak.

*pszSrc*<br/>
Řetězec zakončený hodnotou null, který má být zkopírován `CStringT` do tohoto objektu.

*pStringMgr*<br/>
Ukazatel na správce paměti pro `CStringT` objekt. Další informace o `IAtlStringMgr` správě paměti pro `CStringT`najdete v tématu [Správa paměti pomocí CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

*strSrc*<br/>
Existující `CStringT` objekt, který má být zkopírován do `CStringT` tohoto objektu. Další informace o systémech `CThisString` a `CThisSimpleString`najdete v části poznámky.

*varSrc*<br/>
Objekt variant, který má být zkopírován do `CStringT` tohoto objektu.

*BaseType*<br/>
Typ znaku řetězcové třídy. Může být jedna z následujících akcí:

**znak** (pro řetězce znaků ANSI).

**wchar_t** (pro řetězce znaků Unicode).

TCHAR (pro řetězce znaků ANSI a Unicode).

*bMFCDLL*<br/>
Logická hodnota, která určuje, zda se jedná o projekt knihovny MFC DLL (TRUE) nebo ne (FALSE).

*SystemString*<br/>
Musí být `System::String`a projekt musí být kompilován pomocí parametrem/CLR.

*pString*<br/>
Popisovač pro `CStringT` objekt.

### <a name="remarks"></a>Poznámky

Vzhledem k tomu, že konstruktory kopírují vstupní data do nového přiděleného úložiště, měli byste si být vědomi, že by mohlo dojít k výjimkám paměti. Všimněte si, že některé z těchto konstruktorů fungují jako funkce pro převod. To vám umožňuje nahradit například LPTStr, kde `CStringT` se očekává objekt.

- `CStringT`( `LPCSTR` `lpsz` ): Vytvoří sadu Unicode `CStringT` z řetězce ANSI. Tento konstruktor lze také použít k načtení prostředku řetězce, jak je znázorněno v následujícím příkladu.

- `CStringT(` `LPCWSTR` `lpsz` ): Sestaví `CStringT` z řetězce Unicode.

- `CStringT`( `const unsigned char*` `psz` ): Umožňuje vytvořit `CStringT` z ukazatele na nepodepsaný **znak**.

> [!NOTE]
>  Definujte makro _CSTRING_DISABLE_NARROW_WIDE_CONVERSION pro vypnutí implicitního převodu řetězce mezi řetězci ANSI a Unicode. Makro vyloučí z kompilačních konstruktorů, které podporují převod.

Všimněte si, že parametr *strSrc* může být buď `CStringT` objekt `CThisSimpleString` , nebo. Pro `CStringT`použijte jednu z jeho výchozích instancí (`CString`, `CStringA`, nebo `CStringW`); pro `CThisSimpleString`použijte **Tento** ukazatel. `CThisSimpleString`deklaruje instanci [třídy CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md), která je menší řetězcové třídy s menší integrovanou funkcí než `CStringT` třídou.

Operátor `CSimpleStringT<>&()` přetížení vytvoří `CStringT` objekt z `CSimpleStringT` deklarace.

> [!NOTE]
>  I když je možné vytvořit `CStringT` instance, které obsahují vložené znaky null, doporučujeme proti ní. Volání metod a operátorů `CStringT` na objekty, které obsahují vložené znaky null, mohou způsobit neočekávané výsledky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#112](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_7.cpp)]

##  <a name="_dtorcstringt"></a>CStringt:: ~ CStringt

`CStringT` Odstraní objekt.

```
~CStringT() throw();
```

### <a name="remarks"></a>Poznámky

`CStringT` Odstraní objekt.

##  <a name="delete"></a>CStringt::D dstranit

Odstraní znak nebo znaky z řetězce začínajícího znakem na daném indexu.

```
int Delete(int iIndex, int nCount = 1);
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
Index založený na nule prvního znaku v `CStringT` objektu, který se má odstranit.

*nCount*<br/>
Počet znaků, které mají být odebrány.

### <a name="return-value"></a>Návratová hodnota

Délka změněného řetězce.

### <a name="remarks"></a>Poznámky

Pokud je *nCount* delší než řetězec, zbytek řetězce se odebere.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#113](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_8.cpp)]

```Output
Before: Soccer is best,
    but hockey is quicker!
After: Soccer best,
    but hockey is quicker!
```

##  <a name="find"></a>CStringt:: Find

Vyhledá v tomto řetězci první shodu znaku nebo podřetězce.

```
int Find(PCXSTR pszSub, int iStart=0) const throw();
int Find(XCHAR ch, int iStart=0) const throw();
```

### <a name="parameters"></a>Parametry

*pszSub*<br/>
Dílčí řetězec, který má být hledán.

*iStart*<br/>
Index znaku v řetězci, ve kterém má být zahájeno hledání, nebo 0, aby bylo možné začít od začátku.

*ch*<br/>
Jeden znak, který chcete vyhledat.

### <a name="return-value"></a>Návratová hodnota

Index založený na nule prvního znaku v tomto `CStringT` objektu, který odpovídá požadovanému podřetězci nebo znakům;-1, pokud nebyl nalezen dílčí řetězec nebo znak.

### <a name="remarks"></a>Poznámky

Funkce je přetížena, aby přijímala jednotlivé znaky (podobně jako funkce `strchr`běhu) a řetězce ( `strstr`podobně jako).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#114](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_9.cpp)]

##  <a name="findoneof"></a>CStringt:: FindOneOf

Vyhledá v tomto řetězci první znak, který odpovídá jakémukoli znaku obsaženému v *pszCharSet*.

```
int FindOneOf(PCXSTR pszCharSet) const throw();
```

### <a name="parameters"></a>Parametry

*pszCharSet*<br/>
Řetězec obsahující znaky pro spárování.

### <a name="return-value"></a>Návratová hodnota

Index založený na nule prvního znaku v tomto řetězci, který je také v *pszCharSet*; -1, pokud se neshoduje.

### <a name="remarks"></a>Poznámky

Vyhledá první výskyt všech znaků v *pszCharSet*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#115](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_10.cpp)]

##  <a name="format"></a>CStringt:: Format

Zapisuje naformátovaná `CStringT` data stejným způsobem, jako [sprintf_s](../../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md) formátuje data do pole znaků ve stylu jazyka C.

```
void __cdecl Format(UINT nFormatID, [, argument]...);
void __cdecl Format(PCXSTR pszFormat,  [, argument] ...);
```

### <a name="parameters"></a>Parametry

*nFormatID*<br/>
Identifikátor prostředku řetězce, který obsahuje řetězec řízení formátu.

*pszFormat*<br/>
Řetězec řízení formátu.

*argument*<br/>
Volitelné argumenty

### <a name="remarks"></a>Poznámky

Tato funkce formátuje a ukládá řadu znaků a hodnot v `CStringT`. Každý volitelný argument (pokud existuje) je převeden a výstup podle odpovídající specifikace formátu v *pszFormat* nebo z prostředku řetězce identifikovaného parametrem *nFormatID*.

Volání se nezdaří, pokud je samotný objekt String nabídnut jako parametr `Format`. Například následující kód způsobí nepředvídatelné výsledky:

[!code-cpp[NVC_ATLMFC_Utilities#116](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_11.cpp)]

Další informace najdete v tématu [syntaxe specifikace formátu: printf a wprintf Functions](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#117](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_12.cpp)]

##  <a name="formatmessage"></a>CStringt:: FormatMessage

Formátuje řetězec zprávy.

```
void __cdecl FormatMessage(UINT nFormatID, [, argument]...);
void __cdecl FormatMessage(PCXSTR pszFormat, [, argument]...);
```

### <a name="parameters"></a>Parametry

*nFormatID*<br/>
Identifikátor prostředku řetězce, který obsahuje text neformátované zprávy.

*pszFormat*<br/>
Odkazuje na řetězec řízení formátu. Bude prohledáván pro odpovídající vložení a formátování. Formátovací řetězec je podobný řetězci formátu *printf*běhových funkcí, s výjimkou umožňuje vložení parametrů v libovolném pořadí.

*argument*<br/>
Volitelné argumenty

### <a name="remarks"></a>Poznámky

Funkce vyžaduje jako vstup definici zprávy. Definice zprávy je určena *pszFormat* nebo z prostředku řetězce identifikovaného pomocí *nFormatID*. Funkce zkopíruje formátovaný text zprávy do `CStringT` objektu, přičemž při požadavku zpracovává všechny vložené sekvence vložení.

> [!NOTE]
> `FormatMessage`pokusí se přidělit systémovou paměť pro nově formátovaný řetězec. Pokud tento pokus neproběhne úspěšně, dojde k automatickému vyvolání výjimky paměti.

Každé vložení musí mít odpovídající parametr za parametrem *pszFormat* nebo *nFormatID* . V textu zprávy je několik řídicích sekvencí podporováno pro dynamické formátování zprávy. Další informace najdete v Windows SDK funkci Windows [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#118](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_13.cpp)]

##  <a name="formatmessagev"></a>CStringt:: FormatMessageV

Formátuje řetězec zprávy pomocí seznamu argumentů proměnných.

```
void FormatMessageV(PCXSTR pszFormat, va_list* pArgList);
```

### <a name="parameters"></a>Parametry

*pszFormat*<br/>
Odkazuje na řetězec řízení formátu. Bude prohledáván pro odpovídající vložení a formátování. Formátovací řetězec je podobný formátovacím řetězcům ve stylu `printf`běhu, s výjimkou umožňuje vložení parametrů v libovolném pořadí.

*pArgList*<br/>
Ukazatel na seznam argumentů.

### <a name="remarks"></a>Poznámky

Funkce vyžaduje jako vstup definici zprávy určenou funkcí *pszFormat*. Funkce zkopíruje text formátované zprávy a seznam argumentů s proměnnými do `CStringT` objektu a zpracovává všechny vložené sekvence vložení, pokud je to požadováno.

> [!NOTE]
> `FormatMessageV`volá [CStringT:: FormatMessage](#formatmessage), který se pokusí přidělit systémovou paměť pro nově formátovaný řetězec. Pokud tento pokus neproběhne úspěšně, dojde k automatickému vyvolání výjimky paměti.

Další informace najdete v Windows SDK funkci Windows [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) .

##  <a name="formatv"></a>CStringt:: FormatV

Formátuje řetězec zprávy pomocí seznamu argumentů proměnných.

```
void FormatV(PCXSTR pszFormat, va_list args);
```

### <a name="parameters"></a>Parametry

*pszFormat*<br/>
Odkazuje na řetězec řízení formátu. Bude prohledáván pro odpovídající vložení a formátování. Formátovací řetězec je podobný formátovacím řetězcům ve stylu `printf`běhu, s výjimkou umožňuje vložení parametrů v libovolném pořadí.

*argumentů*<br/>
Ukazatel na seznam argumentů.

### <a name="remarks"></a>Poznámky

Zapíše formátovaný řetězec a seznam proměnných argumentů do `CStringT` řetězce stejným způsobem, který `vsprintf_s` formátuje data do pole znaků ve stylu jazyka C.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#119](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_14.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#120](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_15.cpp)]

##  <a name="getenvironmentvariable"></a>CStringt:: GetEnvironmentVariable

Nastaví řetězec na hodnotu zadané proměnné prostředí.

```
BOOL GetEnvironmentVariable(PCXSTR pszVar);
```

### <a name="parameters"></a>Parametry

*pszVar*<br/>
Ukazatel na řetězec zakončený hodnotou null, který určuje proměnnou prostředí.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Načte hodnotu zadané proměnné z bloku prostředí volajícího procesu. Hodnota je ve formátu řetězce znaků zakončeného hodnotou null.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#121](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_16.cpp)]

##  <a name="insert"></a>CStringt:: INSERT

Vloží jeden znak nebo podřetězec na daný index v rámci řetězce.

```
int Insert(int iIndex, PCXSTR psz);
int Insert(int iIndex, XCHAR ch);
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
Index znaku, před kterým bude provedeno vkládání.

*psz*<br/>
Ukazatel na dílčí řetězec, který má být vložen.

*ch*<br/>
Znak, který má být vložen.

### <a name="return-value"></a>Návratová hodnota

Délka změněného řetězce.

### <a name="remarks"></a>Poznámky

Parametr *iIndex* identifikuje první znak, který bude přesunut, aby uvolnil místo pro daný znak nebo podřetězec. Pokud je *nIndex* nula, vložení proběhne před celým řetězcem. Pokud je *nIndex* větší než délka řetězce, funkce bude zřetězit aktuální řetězec a nový materiál poskytnutý buď *ch* , nebo *PSZ*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#122](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_17.cpp)]

##  <a name="left"></a>CStringt:: Left

Extrahuje z tohoto `CStringT` objektu zcela nCount znaky a vrátí kopii extrahované podřetězce.

```
CStringT Left(int nCount) const;
```

### <a name="parameters"></a>Parametry

*nCount*<br/>
Počet znaků, které mají být z tohoto `CStringT` objektu extrahovány.

### <a name="return-value"></a>Návratová hodnota

`CStringT` Objekt, který obsahuje kopii zadaného rozsahu znaků. Vrácený `CStringT` objekt může být prázdný.

### <a name="remarks"></a>Poznámky

Pokud *nCount* překračuje délku řetězce, bude extrahován celý řetězec. `Left`je podobný základní `Left` funkci.

Pro vícebajtové znakové sady (MBCS) *nCount* zachází s každou 8bitové sekvencí jako znak, takže *nCount* vrátí počet vícebajtových znaků vynásobený dvěma.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#123](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_18.cpp)]

##  <a name="loadstring"></a>CStringt:: LoadString

Přečte prostředek řetězce Windows identifikovaný *NID*do existujícího `CStringT` objektu.

```
BOOL LoadString(HINSTANCE hInstance, UINT nID, WORD wLanguageID);
BOOL LoadString(HINSTANCE hInstance, UINT nID);
BOOL LoadString(UINT nID);
```

### <a name="parameters"></a>Parametry

*hInstance*<br/>
Popisovač instance modulu.

*nID*<br/>
ID prostředku řetězce Windows

*wLanguageID*<br/>
Jazyk řetězcového prostředku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo zatížení prostředku úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Načte prostředek řetězce (*NID*) ze zadaného modulu (*HINSTANCE*) pomocí zadaného jazyka (*wLanguage*).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#124](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_19.cpp)]

##  <a name="makelower"></a>CStringt:: MakeLower

`CStringT` Převede objekt na malý řetězec.

```
CStringT& MakeLower();
```

### <a name="return-value"></a>Návratová hodnota

Výsledný řetězec malými písmeny.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#125](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_20.cpp)]

##  <a name="makereverse"></a>CStringt:: MakeReverse

Obrátí pořadí znaků v `CStringT` objektu.

```
CStringT& MakeReverse();
```

### <a name="return-value"></a>Návratová hodnota

Výsledný stornovaný řetězec.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#126](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_21.cpp)]

##  <a name="makeupper"></a>CStringt:: MakeUpper

`CStringT` Převede objekt na řetězec na velká písmena.

```
CStringT& MakeUpper();
```

### <a name="return-value"></a>Návratová hodnota

Výsledný řetězec na velká písmena.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#127](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_22.cpp)]

##  <a name="mid"></a>CStringt:: Mid

Extrahuje podřetězec délky *nCount* znaků od tohoto `CStringT` objektu počínaje pozicí *iFirst* (počítáno od nuly).

```
CStringT Mid(int iFirst, int nCount) const;
CStringT Mid(int iFirst) const;
```

### <a name="parameters"></a>Parametry

*iFirst*<br/>
Index založený na nule prvního znaku v tomto `CStringT` objektu, který má být zahrnut do extrahovaný podřetězec.

*nCount*<br/>
Počet znaků, které mají být z tohoto `CStringT` objektu extrahovány. Pokud tento parametr není zadán, je extrahován zbytek řetězce.

### <a name="return-value"></a>Návratová hodnota

`CStringT` Objekt, který obsahuje kopii zadaného rozsahu znaků. Všimněte si, že `CStringT` vrácený objekt může být prázdný.

### <a name="remarks"></a>Poznámky

Funkce vrátí kopii extrahované podřetězce. `Mid`je podobný základní funkci Mid (s výjimkou toho, že indexy jsou založeny na bázi Basic).

Pro vícebajtové znakové sady (MBCS) *nCount* odkazuje na každý 8bitový znak; To znamená, že vedoucí a koncový bajt v jednom vícebajtovém znaku se počítají jako dva znaky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#128](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_23.cpp)]

##  <a name="oemtoansi"></a>  CStringT::OemToAnsi

Převede všechny znaky v tomto `CStringT` objektu ze znakové sady OEM na znakovou sadu ANSI.

```
void OemToAnsi();
```

### <a name="remarks"></a>Poznámky

Tato funkce není k dispozici, pokud je definována _UNICODE.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CStringT:: AnsiToOem](#ansitooem).

##  <a name="operator_eq"></a>CStringt:: operator =

Přiřadí k řetězci novou hodnotu.

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
, Který se má přiřadit k tomuto řetězci. `CStringT`

*str*<br/>
Odkaz na `CThisSimpleString` objekt.

*bMFCDLL*<br/>
Logická hodnota určující, zda se jedná o projekt knihovny MFC DLL, nebo ne.

*BaseType*<br/>
Základní typ řetězce.

*var*<br/>
Objekt typu variant, který se má přiřadit k tomuto řetězci.

*ch*<br/>
Znak ANSI nebo Unicode, který se má přiřadit k řetězci.

*pszSrc*<br/>
Ukazatel na původní přiřazený řetězec.

### <a name="remarks"></a>Poznámky

Operátor přiřazení akceptuje jiný `CStringT` objekt, znakový ukazatel nebo jeden znak. Počítejte s tím, že výjimky paměti mohou nastat vždy, když použijete tento operátor, protože může být přiděleno nové úložiště.

Informace o `CThisSimpleString`naleznete v části poznámky v CStringT [:: CStringT](#cstringt).

> [!NOTE]
> I když je možné vytvořit `CStringT` instance, které obsahují vložené znaky null, doporučujeme proti ní. Volání metod a operátorů `CStringT` na objekty, které obsahují vložené znaky null, mohou způsobit neočekávané výsledky.

##  <a name="operator_add"></a>CStringt:: operator +

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
Znak ANSI nebo Unicode, který má být zřetězen s řetězcem.

*ch2*<br/>
Znak ANSI nebo Unicode, který má být zřetězen s řetězcem.

*str1*<br/>
`CStringT` Pro zřetězení s řetězcem nebo znakem.

*str2*<br/>
`CStringT` Pro zřetězení s řetězcem nebo znakem.

*psz1*<br/>
Ukazatel na řetězec zakončený hodnotou null, který má být zřetězen s řetězcem nebo znakem.

*psz2*<br/>
Ukazatel na řetězec, který má být zřetězen s řetězcem nebo znakem.

### <a name="remarks"></a>Poznámky

Je sedm forem `CStringT::operator+` přetížení funkce. První verze zřetězí dva existující `CStringT` objekty. Následující dva zřetězení `CStringT` objektu a řetězec zakončený hodnotou null. Další dva zřetězení `CStringT` objektu a znaku ANSI. Poslední dva zřetězení `CStringT` objektu a znaku Unicode.

> [!NOTE]
>  I když je možné vytvořit `CStringT` instance, které obsahují vložené znaky null, doporučujeme proti ní. Volání metod a operátorů `CStringT` na objekty, které obsahují vložené znaky null, mohou způsobit neočekávané výsledky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#140](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_24.cpp)]

##  <a name="operator_add_eq"></a>CStringt:: operator + =

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

*str*<br/>
Odkaz na `CThisSimpleString` objekt.

*bMFCDLL*<br/>
Logická hodnota určující, zda se jedná o projekt knihovny MFC DLL, nebo ne.

*BaseType*<br/>
Základní typ řetězce.

*var*<br/>
Objekt variant, který se má zřetězit k tomuto řetězci.

*ch*<br/>
Znak ANSI nebo Unicode, který má být zřetězen s řetězcem.

*pszSrc*<br/>
Ukazatel na řetězec, který se zřetězí.

*strSrc*<br/>
`CStringT` Pro zřetězení do tohoto řetězce.

### <a name="remarks"></a>Poznámky

Operátor přijímá jiný `CStringT` objekt, znakový ukazatel nebo jeden znak. Je třeba si uvědomit, že výjimky paměti mohou nastat vždy, když použijete tento operátor zřetězení, protože novému úložišti lze přidělit znaky `CStringT` přidané do tohoto objektu.

Informace o `CThisSimpleString`naleznete v části poznámky v CStringT [:: CStringT](#cstringt).

> [!NOTE]
>  I když je možné vytvořit `CStringT` instance, které obsahují vložené znaky null, doporučujeme proti ní. Volání metod a operátorů `CStringT` na objekty, které obsahují vložené znaky null, mohou způsobit neočekávané výsledky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#141](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_25.cpp)]

##  <a name="operator_eq_eq"></a>CStringt:: operator = =

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
`CStringT` Pro porovnání.

*str2*<br/>
`CStringT` Pro porovnání.

*psz1*<br/>
Ukazatel na řetězec zakončený hodnotou null pro porovnání.

*psz2*<br/>
Ukazatel na řetězec zakončený hodnotou null pro porovnání.

### <a name="remarks"></a>Poznámky

Testuje, zda je řetězec nebo znak na levé straně roven řetězci nebo znaku na pravé straně a vrátí hodnotu TRUE nebo FALSE odpovídajícím způsobem.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#142](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_26.cpp)]

##  <a name="operator_neq"></a>CStringt:: operator! =

Určuje, zda jsou dva řetězce logicky neshodné.

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
Znak ANSI nebo Unicode, který má být zřetězen s řetězcem.

*ch2*<br/>
Znak ANSI nebo Unicode, který má být zřetězen s řetězcem.

*str1*<br/>
`CStringT` Pro porovnání.

*str2*<br/>
`CStringT` Pro porovnání.

*psz1*<br/>
Ukazatel na řetězec zakončený hodnotou null pro porovnání.

*psz2*<br/>
Ukazatel na řetězec zakončený hodnotou null pro porovnání.

### <a name="remarks"></a>Poznámky

Testuje, zda se řetězec nebo znak na levé straně nerovná řetězci nebo znaku na pravé straně.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#143](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_27.cpp)]

##  <a name="operator_lt"></a>CStringt:: – operátor&lt;

Určuje, zda je řetězec na levé straně operátoru menší než řetězec na pravé straně.

```
friend bool operator<(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parametry

*str1*<br/>
`CStringT` Pro porovnání.

*str2*<br/>
`CStringT` Pro porovnání.

*psz1*<br/>
Ukazatel na řetězec zakončený hodnotou null pro porovnání.

*psz2*<br/>
Ukazatel na řetězec zakončený hodnotou null pro porovnání.

### <a name="remarks"></a>Poznámky

Lexicographical porovnávání mezi řetězci, znak po znaku až do:

- Najde dva odpovídající znaky, které nejsou stejné a výsledek jejich porovnání je výsledkem porovnání řetězců.

- Nenajde žádné nerovnosti, ale jeden řetězec má více znaků než druhý a kratší řetězec je považován za méně než delší řetězec.

- Nenajde žádné nerovnosti a zjistí, že řetězce mají stejný počet znaků, a proto jsou řetězce stejné.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#144](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_28.cpp)]

##  <a name="operator_gt"></a>CStringt:: – operátor&gt;

Určuje, zda je řetězec na levé straně operátoru větší než řetězec na pravé straně.

```
friend bool operator>(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parametry

*str1*<br/>
`CStringT` Pro porovnání.

*str2*<br/>
`CStringT` Pro porovnání.

*psz1*<br/>
Ukazatel na řetězec zakončený hodnotou null pro porovnání.

*psz2*<br/>
Ukazatel na řetězec zakončený hodnotou null pro porovnání.

### <a name="remarks"></a>Poznámky

Lexicographical porovnávání mezi řetězci, znak po znaku až do:

- Najde dva odpovídající znaky, které nejsou stejné a výsledek jejich porovnání je výsledkem porovnání řetězců.

- Nenajde žádné nerovnosti, ale jeden řetězec má více znaků než druhý a kratší řetězec je považován za méně než delší řetězec.

- Nenajde žádné nerovnosti a zjistí, že řetězce mají stejný počet znaků, takže jsou řetězce stejné.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#145](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_29.cpp)]

##  <a name="operator_lt_eq"></a>CStringt:: – operátor&lt;=

Určuje, zda je řetězec na levé straně operátoru menší než nebo roven řetězci na pravé straně.

```
friend bool operator<=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parametry

*str1*<br/>
`CStringT` Pro porovnání.

*str2*<br/>
`CStringT` Pro porovnání.

*psz1*<br/>
Ukazatel na řetězec zakončený hodnotou null pro porovnání.

*psz2*<br/>
Ukazatel na řetězec zakončený hodnotou null pro porovnání.

### <a name="remarks"></a>Poznámky

Lexicographical porovnávání mezi řetězci, znak po znaku až do:

- Najde dva odpovídající znaky, které nejsou stejné a výsledek jejich porovnání je výsledkem porovnání řetězců.

- Nenajde žádné nerovnosti, ale jeden řetězec má více znaků než druhý a kratší řetězec je považován za méně než delší řetězec.

- Nenajde žádné nerovnosti a zjistí, že řetězce mají stejný počet znaků, takže jsou řetězce stejné.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#146](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_30.cpp)]

##  <a name="operator_gt_eq"></a>CStringt:: – operátor&gt;=

Určuje, zda je řetězec na levé straně operátoru větší než nebo roven řetězci na pravé straně.

```
friend bool operator>=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parametry

*str1*<br/>
`CStringT` Pro porovnání.

*str2*<br/>
`CStringT` Pro porovnání.

*psz1*<br/>
Ukazatel na řetězec pro porovnání.

*psz2*<br/>
Ukazatel na řetězec pro porovnání.

### <a name="remarks"></a>Poznámky

Lexicographical porovnávání mezi řetězci, znak po znaku až do:

- Najde dva odpovídající znaky, které nejsou stejné a výsledek jejich porovnání je výsledkem porovnání řetězců.

- Nenajde žádné nerovnosti, ale jeden řetězec má více znaků než druhý a kratší řetězec je považován za méně než delší řetězec.

- Nenajde žádné nerovnosti a zjistí, že řetězce mají stejný počet znaků, takže jsou řetězce stejné.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#147](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_31.cpp)]

##  <a name="remove"></a>CStringt:: Remove

Odebere všechny výskyty zadaného znaku z řetězce.

```
int Remove(XCHAR chRemove);
```

### <a name="parameters"></a>Parametry

*chRemove*<br/>
Znak, který má být odebrán z řetězce.

### <a name="return-value"></a>Návratová hodnota

Počet znaků odebraných z řetězce. Nula, pokud se řetězec nemění.

### <a name="remarks"></a>Poznámky

Porovnávání znaku rozlišuje velká a malá písmena.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#129](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_32.cpp)]

##  <a name="replace"></a>CStringt:: Replace

Existují dvě verze systému `Replace`. První verze nahrazuje jednu nebo více kopií podřetězce pomocí jiného podřetězce. Oba podřetězce jsou zakončené znakem null. Druhá verze nahrazuje jednu nebo více kopií znaku pomocí jiného znaku. Obě verze pracují s daty znaků uloženými v `CStringT`.

```
int Replace(PCXSTR pszOld, PCXSTR pszNew);
int Replace(XCHAR chOld, XCHAR chNew);
```

### <a name="parameters"></a>Parametry

*pszOld*<br/>
Ukazatel na řetězec zakončený hodnotou null, který má být nahrazen hodnotou *pszNew*.

*pszNew*<br/>
Ukazatel na řetězec zakončený hodnotou null, který nahrazuje *pszOld*.

*chOld*<br/>
Znak, který má být nahrazen nástrojem *chNew*.

*chNew*<br/>
Znak nahrazující *chOld*

### <a name="return-value"></a>Návratová hodnota

Vrátí počet nahrazených instancí znaku nebo podřetězec nebo hodnotu nula, pokud se řetězec nemění.

### <a name="remarks"></a>Poznámky

`Replace`může změnit délku řetězce, protože *pszNew* a *pszOld* nemusí mít stejnou délku a několik kopií starého podřetězce lze změnit na nový. Funkce provádí shodu rozlišující velká a malá písmena.

Příklady instancí jsou `CString`, `CStringA`a. `CStringW` `CStringT`

Pro `CStringA`používásaduANSI nebovícebajtovýchznaků(MBCS).`Replace` Pro `CStringW`fungujesvelkým množstvímznaků.`Replace`

Pro `CString`je typ dat znaků vybrán v době kompilace na základě toho, zda jsou definovány konstanty v následující tabulce.

|Definovaná konstanta|Znakový datový typ|
|----------------------|-------------------------|
|_UNICODE|Široké znaky|
|_MBCS|Dvoubajtové znaky|
|Ani|Jednobajtové znaky|
|Obojí|Nedefinováno|

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#200](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_33.cpp)]

##  <a name="reversefind"></a>CStringt:: ReverseFind

Vyhledá `CStringT` v tomto objektu poslední shodu znaku.

```
int ReverseFind(XCHAR ch) const throw();
```

### <a name="parameters"></a>Parametry

*ch*<br/>
Znak, který chcete vyhledat.

### <a name="return-value"></a>Návratová hodnota

Index založený na nule posledního znaku v tomto `CStringT` objektu, který odpovídá požadovanému znaku, nebo-1, pokud znak nebyl nalezen.

### <a name="remarks"></a>Poznámky

Funkce je podobná funkci `strrchr`run-time.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#130](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_34.cpp)]

##  <a name="right"></a>CStringt:: Right

Extrahuje poslední (tj.) *nCount* znaky z tohoto `CStringT` objektu a vrátí kopii extrahované podřetězce.

```
CStringT Right(int nCount) const;
```

### <a name="parameters"></a>Parametry

*nCount*<br/>
Počet znaků, které mají být z tohoto `CStringT` objektu extrahovány.

### <a name="return-value"></a>Návratová hodnota

`CStringT` Objekt, který obsahuje kopii zadaného rozsahu znaků. Všimněte si, že `CStringT` vrácený objekt může být prázdný.

### <a name="remarks"></a>Poznámky

Pokud *nCount* překračuje délku řetězce, bude extrahován celý řetězec. `Right`se podobá funkci Basic `Right` (s výjimkou toho, že indexy v Basic jsou počítány od nuly).

Pro vícebajtové znakové sady (MBCS) *nCount* odkazuje na každý 8bitový znak; To znamená, že vedoucí a koncový bajt v jednom vícebajtovém znaku se počítají jako dva znaky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#131](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_35.cpp)]

##  <a name="setsysstring"></a>CStringt:: SetSysString

Znovu přidělí `CStringT` objekt BSTR, na který odkazuje *pbstr* , a zkopíruje do něj obsah objektu, včetně znaku null.

```
BSTR SetSysString(BSTR* pbstr) const;
```

### <a name="parameters"></a>Parametry

*pbstr*<br/>
Ukazatel na řetězec znaků.

### <a name="return-value"></a>Návratová hodnota

Nový řetězec.

### <a name="remarks"></a>Poznámky

V závislosti na obsahu `CStringT` objektu se může změnit hodnota BSTR, na kterou odkazuje *pbstr* . Funkce vyvolá výjimku, `CMemoryException` Pokud existuje nedostatek paměti.

Tato funkce se obvykle používá ke změně hodnoty řetězců předaných odkazem pro automatizaci.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#132](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_36.cpp)]

##  <a name="spanexcluding"></a>CStringt:: SpanExcluding

Extrahuje znaky z řetězce počínaje prvním znakem, který není v sadě znaků identifikovaných pomocí *pszCharSet*.

```
CStringT SpanExcluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>Parametry

*pszCharSet*<br/>
Řetězec, který je interpretován jako sada znaků.

### <a name="return-value"></a>Návratová hodnota

Podřetězec obsahující znaky v řetězci, které nejsou v *pszCharSet*počínaje prvním znakem v řetězci a končící prvním znakem nalezeným v řetězci, který je také v *pszCharSet* (tj. počínaje prvním znak v řetězci a až s výjimkou prvního znaku v řetězci, který je nalezen *pszCharSet*). Vrátí celý řetězec, pokud v *pszCharSet* není žádný znak v řetězci.

### <a name="remarks"></a>Poznámky

`SpanExcluding`extrahuje a vrátí všechny znaky předcházející prvnímu výskytu znaku z *pszCharSet* (jinými slovy znak z *pszCharSet* a všechny znaky, které následují v řetězci, nejsou vraceny). Pokud v řetězci není nalezen žádný znak z *pszCharSet* , pak `SpanExcluding` vrátí celý řetězec.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#133](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_37.cpp)]

##  <a name="spanincluding"></a>CStringt:: SpanIncluding

Extrahuje znaky z řetězce počínaje prvním znakem, které jsou v sadě znaků identifikované *pszCharSet*.

```
CStringT SpanIncluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>Parametry

*pszCharSet*<br/>
Řetězec, který je interpretován jako sada znaků.

### <a name="return-value"></a>Návratová hodnota

Podřetězec, který obsahuje znaky v řetězci, které jsou v *pszCharSet*, počínaje prvním znakem v řetězci a končící při nalezení znaku v řetězci, který není v *pszCharSet*. `SpanIncluding`Vrátí prázdný podřetězec, pokud první znak v řetězci není v zadané sadě.

### <a name="remarks"></a>Poznámky

Pokud první znak řetězce není v sadě znaků, pak `SpanIncluding` vrátí prázdný řetězec. V opačném případě vrátí posloupnost po sobě jdoucích znaků, které jsou v sadě.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#134](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_38.cpp)]

##  <a name="tokenize"></a>CStringt:: tokenizovat

Vyhledá další token v cílovém řetězci.

```
CStringT Tokenize(PCXSTR pszTokens, int& iStart) const;
```

### <a name="parameters"></a>Parametry

*pszTokens*<br/>
Řetězec obsahující oddělovače tokenů. Pořadí těchto oddělovačů není důležité.

*iStart*<br/>
Index založený na nule pro zahájení hledání.

### <a name="return-value"></a>Návratová hodnota

`CStringT` Objekt obsahující aktuální hodnotu tokenu.

### <a name="remarks"></a>Poznámky

`Tokenize` Funkce vyhledá další token v cílovém řetězci. Sada znaků v *pszTokens* určuje možné oddělovače tokenu, který se má najít. Při každém volání `Tokenize` funkce začíná na začátku,přeskočí úvodní oddělovače a vrátí `CStringT` objekt obsahující aktuální token, což je řetězec znaků až k dalšímu znaku oddělovače. Hodnota parametru- *Start* je aktualizována tak, aby byla pozice za koncovým znakem oddělovače, nebo-1, pokud bylo dosaženo konce řetězce. Další tokeny lze rozdělit ze zbytku cílového řetězce řadou volání na `Tokenize`, pomocí příkazového začátku pro udržení přehledu o tom, kde v řetězci je další token čten. Pokud nejsou k dispozici žádné další tokeny, funkce vrátí prázdný řetězec a příkaz set- *Start* bude nastaven na hodnotu-1.

Na rozdíl od funkcí CRT tokenizovat, jako je [strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l](../../c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md), `Tokenize` neupravuje cílový řetězec.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#135](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_39.cpp)]

### <a name="remarks"></a>Poznámky

Výstup z tohoto příkladu je následující:

```Output
Resulting Token: First
Resulting Token: Second
Resulting Token: Third
```

##  <a name="trim"></a>CStringt:: Trim

Ořízne úvodní a koncové znaky z řetězce.

```
CStringT& Trim(XCHAR chTarget);
CStringT& Trim(PCXSTR pszTargets);
CStringT& Trim();
```

### <a name="parameters"></a>Parametry

*chTarget*<br/>
Cílový znak, který má být oříznut.

*pszTargets*<br/>
Ukazatel na řetězec obsahující cílové znaky, které mají být oříznuty. Všechny úvodní a koncové výskyty znaků v *pszTarget* budou z `CStringT` objektu oříznuty.

### <a name="return-value"></a>Návratová hodnota

Vrátí oříznutý řetězec.

### <a name="remarks"></a>Poznámky

Odebere všechny úvodní a koncové výskyty jednoho z následujících:

- Znak určený parametrem *chTarget*.

- Všechny znaky nalezené v řetězci určeném parametrem *pszTargets*.

- Typy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#136](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_40.cpp)]

### <a name="remarks"></a>Poznámky

Výstup z tohoto příkladu je následující:

```Output
Before: "******Soccer is best, but liquor is quicker!!!!!"
After : "Soccer is best, but liquor is quicker"
```

##  <a name="trimleft"></a>CStringt:: TrimLeft

Ořízne úvodní znaky z řetězce.

```
CStringT& TrimLeft(XCHAR chTarget);
CStringT& TrimLeft(PCXSTR pszTargets);
CStringT& TrimLeft();
```

### <a name="parameters"></a>Parametry

*chTarget*<br/>
Cílový znak, který má být oříznut.

*pszTargets*<br/>
Ukazatel na řetězec obsahující cílové znaky, které mají být oříznuty. Všechny úvodní výskyty znaků v *pszTarget* budou z `CStringT` objektu oříznuty.

### <a name="return-value"></a>Návratová hodnota

Výsledný oříznutý řetězec.

### <a name="remarks"></a>Poznámky

Odebere všechny úvodní a koncové výskyty jednoho z následujících:

- Znak určený parametrem *chTarget*.

- Všechny znaky nalezené v řetězci určeném parametrem *pszTargets*.

- Typy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#137](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_41.cpp)]

##  <a name="trimright"></a>CStringt:: TrimRight

Ořízne koncové znaky z řetězce.

```
CStringT& TrimRight(XCHAR chTarget);
CStringT& TrimRight(PCXSTR pszTargets);
CStringT& TrimRight();
```

### <a name="parameters"></a>Parametry

*chTarget*<br/>
Cílový znak, který má být oříznut.

*pszTargets*<br/>
Ukazatel na řetězec obsahující cílové znaky, které mají být oříznuty. Všechny koncové výskyty znaků v *pszTarget* budou z `CStringT` objektu oříznuty.

### <a name="return-value"></a>Návratová hodnota

`CStringT` Vrátí objekt, který obsahuje oříznutý řetězec.

### <a name="remarks"></a>Poznámky

Odebere koncové výskyty jednoho z následujících:

- Znak určený parametrem *chTarget*.

- Všechny znaky nalezené v řetězci určeném parametrem *pszTargets*.

- Typy.

Verze přijímá jeden parametr znaku a odstraní všechny kopie daného znaku z `CStringT` konce řetězcových dat. `CStringT& TrimRight(XCHAR chTarget)` Začíná na konci řetězce a funguje směrem dopředu. Zastaví se, když najde jiný znak nebo když `CSTringT` vyčerpá znaková data.

`CStringT& TrimRight(PCXSTR pszTargets)` Verze přijímá řetězec zakončený hodnotou null, který obsahuje všechny různé znaky, které chcete vyhledat. Odebere všechny kopie těchto znaků v `CStringT` objektu. Začíná na konci řetězce a funguje směrem dopředu. Zastaví se, když najde znak, který není v cílovém řetězci, nebo při `CStringT` vyzkoušení znakových dat. Nepokusí se porovnat celý cílový řetězec s podřetězcem na konci `CStringT`.

`CStringT& TrimRight()` Verze nevyžaduje žádné parametry. Ořízne všechny koncové prázdné znaky z konce `CStringT` řetězce. Prázdné znaky mohou být zalomení řádků, mezery nebo tabulátory.

-

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#138](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_42.cpp)]

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Sdílené třídy ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)<br/>
[CSimpleStringT – třída](../../atl-mfc-shared/reference/csimplestringt-class.md)
