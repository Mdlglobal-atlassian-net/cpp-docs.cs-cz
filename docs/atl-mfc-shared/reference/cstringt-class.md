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
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418207"
---
# <a name="cstringt-class"></a>CStringt – třída

Tato třída reprezentuje objekt `CStringT`.

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

- **char** (pro řetězce znaků ANSI).

- **wchar_t** (pro řetězce znaků Unicode).

- TCHAR (pro řetězce znaků ANSI a Unicode).

*StringTraits*<br/>
Určuje, zda třída String potřebuje podporu knihovny jazyka C run-time (CRT) a kde jsou umístěny prostředky řetězců. Může být jedna z následujících akcí:

- **StrTraitATL < wchar_t** &#124; **char** &#124; **TCHAR, ChTraitsCRT < wchar_t** &#124; **char** &#124; **TCHAR > >**

   Třída vyžaduje podporu CRT a hledá řetězce prostředků v modulu určeném parametrem `m_hInstResource` (člen třídy modulu aplikace).

- **StrTraitATL < wchar_t** &#124; **char** &#124; **TCHAR, ChTraitsOS < wchar_t** &#124; **char** &#124; **TCHAR > >**

   Třída nevyžaduje podporu CRT a hledá řetězce prostředků v modulu určeném parametrem `m_hInstResource` (člen třídy modulu aplikace).

- **StrTraitMFC < wchar_t** &#124; **char** &#124; **TCHAR, ChTraitsCRT < wchar_t** &#124; **char** &#124; **TCHAR > >**

   Třída vyžaduje podporu CRT a hledá řetězce prostředků pomocí standardního vyhledávacího algoritmu MFC.

- **StrTraitMFC < wchar_t** &#124; **char** &#124; **TCHAR, ChTraitsOS < wchar_t** &#124; **char** &#124; **TCHAR > >**

   Třída nevyžaduje podporu CRT a hledá řetězce prostředků pomocí standardního vyhledávacího algoritmu MFC.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CStringt:: CStringt](#cstringt)|Sestaví objekt `CStringT` různými způsoby.|
|[CStringt:: ~ CStringt](#_dtorcstringt)|Odstraní objekt `CStringT`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CStringt:: AllocSysString](#allocsysstring)|Přidělí datový objekt BSTR z `CStringT` dat.|
|[CStringt:: AnsiToOem](#ansitooem)|Provede místní převod ze znakové sady ANSI na znakovou sadu OEM.|
|[CStringt:: AppendFormat](#appendformat)|Připojí formátovaná data k existujícímu objektu `CStringT`.|
|[CStringt:: COLLATE](#collate)|Porovná dva řetězce (rozlišuje velká a malá písmena, používá informace specifické pro národní prostředí).|
|[CStringt:: CollateNoCase](#collatenocase)|Porovná dva řetězce (nerozlišuje velikost písmen, používá informace specifické pro národní prostředí).|
|[CStringt:: Compare](#compare)|Porovná dva řetězce (rozlišuje velká a malá písmena).|
|[CStringt:: CompareNoCase](#comparenocase)|Porovná dva řetězce (nerozlišuje velikost písmen).|
|[CStringt::D dstranit](#delete)|Odstraní znak nebo znaky z řetězce.|
|[CStringt:: Find](#find)|Vyhledá znak nebo podřetězec uvnitř většího řetězce.|
|[CStringt:: FindOneOf](#findoneof)|Vyhledá první shodný znak ze sady.|
|[CStringt:: Format](#format)|Zformátuje řetězec jako `sprintf`.|
|[CStringt:: FormatMessage](#formatmessage)|Formátuje řetězec zprávy.|
|[CStringt:: FormatMessageV](#formatmessagev)|Formátuje řetězec zprávy pomocí seznamu argumentů proměnných.|
|[CStringt:: FormatV](#formatv)|Zformátuje řetězec pomocí seznamu proměnných argumentů.|
|[CStringt:: GetEnvironmentVariable](#getenvironmentvariable)|Nastaví řetězec na hodnotu zadané proměnné prostředí.|
|[CStringt:: INSERT](#insert)|Vloží jeden znak nebo podřetězec na daný index v rámci řetězce.|
|[CStringt:: Left](#left)|Extrahuje levou část řetězce.|
|[CStringt:: LoadString](#loadstring)|Načte existující `CStringT` objekt z prostředku Windows.|
|[CStringt:: MakeLower](#makelower)|Převede všechny znaky v tomto řetězci na malá písmena.|
|[CStringt:: MakeReverse](#makereverse)|Obrátí řetězec.|
|[CStringt:: MakeUpper](#makeupper)|Převede všechny znaky v tomto řetězci na velká písmena.|
|[CStringt:: Mid](#mid)|Extrahuje střední část řetězce.|
|[CStringt:: OemToAnsi](#oemtoansi)|Provede místní převod ze znakové sady OEM na znakovou sadu ANSI.|
|[CStringt:: Remove](#remove)|Odebere označené znaky z řetězce.|
|[CStringt:: Replace](#replace)|Nahradí označené znaky dalšími znaky.|
|[CStringt:: ReverseFind](#reversefind)|Najde znak uvnitř většího řetězce; začíná od konce.|
|[CStringt:: Right](#right)|Extrahuje pravou část řetězce.|
|[CStringt:: SetSysString](#setsysstring)|Nastaví existující objekt BSTR daty z objektu `CStringT`.|
|[CStringt:: SpanExcluding](#spanexcluding)|Extrahuje znaky z řetězce počínaje prvním znakem, který není v sadě znaků identifikovaných pomocí `pszCharSet`.|
|[CStringt:: SpanIncluding](#spanincluding)|Extrahuje podřetězec, který obsahuje pouze znaky v sadě.|
|[CStringt:: tokenizovat](#tokenize)|Extrahuje zadané tokeny do cílového řetězce.|
|[CStringt:: Trim](#trim)|Ořízne všechny úvodní a koncové prázdné znaky z řetězce.|
|[CStringt:: TrimLeft](#trimleft)|Ořízne z řetězce úvodní prázdné znaky.|
|[CStringt:: TrimRight](#trimright)|Ořízne v řetězci koncové prázdné znaky.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[CStringt:: operator =](#operator_eq)|Přiřadí novou hodnotu objektu `CStringT`.|
|[CStringt:: operator +](#operator_add)|Zřetězí dva řetězce nebo znak a řetězec.|
|[CStringt:: operator + =](#operator_add_eq)|Zřetězí nový řetězec na konec existujícího řetězce.|
|[CStringt:: operator = =](#operator_eq_eq)|Určuje, zda jsou dva řetězce logicky stejné.|
|[CStringt:: operator! =](#operator_neq)|Určuje, zda jsou dva řetězce logicky neshodné.|
|[CStringt:: operator &lt;](#operator_lt)|Určuje, zda je řetězec na levé straně operátoru menší než řetězec na pravé straně.|
|[CStringt:: operator &gt;](#operator_gt)|Určuje, zda je řetězec na levé straně operátoru větší než řetězec na pravé straně.|
|[CStringt:: operator &lt;=](#operator_lt_eq)|Určuje, zda je řetězec na levé straně operátoru menší než nebo roven řetězci na pravé straně.|
|[CStringt:: operator &gt;=](#operator_gt_eq)|Určuje, zda je řetězec na levé straně operátoru větší než nebo roven řetězci na pravé straně.|

## <a name="remarks"></a>Poznámky

`CStringT` dědí z [třídy CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md). Pokročilé funkce, jako je například manipulace se znaky, řazení a hledání, jsou implementovány pomocí `CStringT`.

> [!NOTE]
> objekty `CStringT` jsou schopny vyvolávání výjimek. K tomu dochází, když `CStringT` objekt z jakéhokoli důvodu vyčerpá z paměti.

Objekt `CStringT` se skládá ze sekvence znaků s proměnlivou délkou. `CStringT` poskytuje funkce a operátory pomocí syntaxe, která je podobná syntaxi Basic. Operátory zřetězení a porovnávání, společně s zjednodušenou správou paměti, usnadňují použití objektů `CStringT` více než běžnými znakovými poli.

> [!NOTE]
>  I když je možné vytvořit `CStringT` instance, které obsahují vložené znaky null, doporučujeme proti ní. Volání metod a operátorů na `CStringT` objekty, které obsahují vložené znaky null, mohou způsobit neočekávané výsledky.

Pomocí různých kombinací parametrů `BaseType` a `StringTraits` mohou objekty `CStringT` být v následujících typech, které byly předdefinovány knihovnou ATL.

Při použití v aplikaci ATL:

`CString`, `CStringA`a `CStringW` jsou exportovány z knihovny MFC DLL (MFC90. DLL), nikdy z knihoven DLL uživatele. To se provádí, aby se zabránilo násobení `CStringT` definování.

> [!NOTE]
>  Pokud váš kód obsahuje alternativní řešení pro chyby linkeru, které jsou popsány v tématu [Export třídy řetězců pomocí CStringT](../../atl-mfc-shared/exporting-string-classes-using-cstringt.md), měli byste tento kód odebrat. Už není zapotřebí.

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

Následující typy řetězců jsou k dispozici v projektech, kde ATL_CSTRING_NO_CRT není definován:

|CStringt – typ|Deklarace|
|-------------------|-----------------|
|`CAtlStringA`|Řetězec typu znaku ANSI s podporou CRT.|
|`CAtlStringW`|Řetězec typu znaku Unicode s podporou CRT.|
|`CAtlString`|Typy znaků ANSI i Unicode s podporou CRT.|

`CString` objekty mají také následující vlastnosti:

- `CStringT` objekty mohou růst v důsledku operací zřetězení.

- objekty `CStringT` sledují "sémantika hodnoty". Objekt `CStringT` můžete představit jako skutečný řetězec, nikoli jako ukazatel na řetězec.

- Pro argumenty funkce `PCXSTR` lze volně dosadit `CStringT` objekty.

- Vlastní Správa paměti pro vyrovnávací paměti řetězců. Další informace najdete v tématu [Správa paměti a CString](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="cstringt-predefined-types"></a>Předdefinované typy CStringt

Vzhledem k tomu, že `CStringT` používá argument šablony pro definování typu znaku (buď [wchar_t](../../c-runtime-library/standard-types.md) nebo [char](../../c-runtime-library/standard-types.md)), typy parametrů metody mohou být složité v časech. Pro zjednodušení tohoto problému je definována sada předdefinovaných typů, která se používá v celé `CStringT` třídy. V následující tabulce jsou uvedeny různé typy:

|Název|Popis|
|----------|-----------------|
|`XCHAR`|Jeden znak (buď **wchar_t** , nebo **znak**) se stejným typem znaku jako objekt `CStringT`.|
|`YCHAR`|Jeden znak (buď **wchar_t** , nebo **znak**) s typem opačného znaku jako objekt `CStringT`.|
|`PXSTR`|Ukazatel na řetězec znaků (buď **wchar_t** , nebo **znak**) se stejným typem znaků jako objekt `CStringT`.|
|`PYSTR`|Ukazatel na řetězec znaků (buď **wchar_t** , nebo **znak**) s typem opačného znaku jako objekt `CStringT`.|
|`PCXSTR`|Ukazatel na řetězec **konstantního** znaku (buď **wchar_t** , nebo **znak**) se stejným typem znaků jako objekt `CStringT`.|
|`PCYSTR`|Ukazatel na řetězec **konstantního** znaku (buď **wchar_t** , nebo **znak**) s typem opačného znaku jako objekt `CStringT`.|

> [!NOTE]
>  Kód, který dříve používal nedokumentované metody `CString` (například `AssignCopy`), musí být nahrazen kódem, který používá následující dokumentované metody `CStringT` (například `GetBuffer` nebo `ReleaseBuffer`). Tyto metody jsou zděděné z `CSimpleStringT`.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)

`CStringT`

## <a name="requirements"></a>Požadavky

|Hlavička|Použít pro|
|------------|-------------|
|CStringT. h|Řetězcové objekty pouze MFC|
|atlstr.h|Objekty řetězce bez knihovny MFC|

##  <a name="allocsysstring"></a>CStringt:: AllocSysString

Přidělí řetězec kompatibilní s automatizací typu BSTR a zkopíruje obsah objektu `CStringT` do něj, včetně ukončujícího znaku null.

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

Převede všechny znaky z tohoto `CStringT` objektu ze znakové sady ANSI na znakovou sadu OEM.

```
void AnsiToOem();
```

### <a name="remarks"></a>Poznámky

Funkce není k dispozici, pokud je definována _UNICODE.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#106](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_2.cpp)]

##  <a name="appendformat"></a>CStringt:: AppendFormat

Připojí formátovaná data k existujícímu objektu `CStringT`.

```
void __cdecl AppendFormat(PCXSTR pszFormat, [, argument] ...);
void __cdecl AppendFormat(UINT nFormatID, [, argument] ...);
```

### <a name="parameters"></a>Parametry

*pszFormat*<br/>
Řetězec řízení formátu.

*nFormatID*<br/>
Identifikátor prostředku řetězce, který obsahuje řetězec řízení formátu.

*Argument*<br/>
Volitelné argumenty

### <a name="remarks"></a>Poznámky

Tato funkce formátuje a připojuje řadu znaků a hodnot v `CStringT`. Každý volitelný argument (pokud existuje) je převeden a připojen podle odpovídající specifikace formátu v *pszFormat* nebo z prostředku řetězce identifikovaného parametrem *nFormatID*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#107](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_3.cpp)]

##  <a name="collate"></a>CStringt:: COLLATE

Porovná dva řetězce pomocí funkce obecného textu `_tcscoll`.

```
int Collate(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Druhý řetězec použitý pro porovnání.

### <a name="return-value"></a>Návratová hodnota

Nula, pokud jsou řetězce identické, < 0, pokud je tento objekt `CStringT` menší než *PSZ*, nebo > 0, pokud je tento objekt `CStringT` větší než *PSZ*.

### <a name="remarks"></a>Poznámky

Funkce obecného textu `_tcscoll`, která je definována v TCHAR. H, mapuje buď `strcoll`, `wcscoll`nebo `_mbscoll`, v závislosti na znakové sadě definované v době kompilace. Každá funkce provádí porovnání řetězců s rozlišováním velkých a malých písmen podle znakové stránky, která se právě používá. Další informace najdete v tématu [strcoll –, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md).

##  <a name="collatenocase"></a>CStringt:: CollateNoCase

Porovná dva řetězce pomocí funkce obecného textu `_tcscoll`.

```
int CollateNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Druhý řetězec použitý pro porovnání.

### <a name="return-value"></a>Návratová hodnota

Nula, pokud jsou řetězce identické (ignorování velkých a malých písmen), < 0, pokud je tento objekt `CStringT` menší než *PSZ* (ignorování velkých a malých písmen), nebo > 0, pokud je tento objekt `CStringT` větší než *PSZ* (ignorování velkých a malých písmen).

### <a name="remarks"></a>Poznámky

Funkce obecného textu `_tcscoll`, která je definována v TCHAR. H, mapuje buď `stricoll`, `wcsicoll`nebo `_mbsicoll`, v závislosti na znakové sadě definované v době kompilace. Každá funkce provede porovnání řetězců bez rozlišování velkých a malých písmen, podle znakové stránky, která se právě používá. Další informace najdete v tématu [strcoll –, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md).

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

Nula, pokud jsou řetězce identické, < 0, pokud je tento objekt `CStringT` menší než *PSZ*, nebo > 0, pokud je tento objekt `CStringT` větší než *PSZ*.

### <a name="remarks"></a>Poznámky

Funkce obecného textu `_tcscmp`, která je definována v TCHAR. H, mapuje buď `strcmp`, `wcscmp`nebo `_mbscmp`, v závislosti na znakové sadě definované v době kompilace. Každá funkce provádí porovnání řetězců s rozlišováním velkých a malých písmen a není ovlivněno národním prostředím. Další informace najdete v tématu [strcmp, wcscmp, _mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md).

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

Nula, pokud jsou řetězce identické (ignorování velkých a malých písmen), < 0, pokud je tento objekt `CStringT` menší než *PSZ* (ignorování velkých a malých písmen), nebo > 0, pokud je tento objekt `CStringT` větší než *PSZ* (ignorování velkých a malých písmen).

### <a name="remarks"></a>Poznámky

Funkce obecného textu `_tcsicmp`, která je definována v TCHAR. H se mapuje buď na `_stricmp`, `_wcsicmp` nebo `_mbsicmp`, v závislosti na znakové sadě definované v době kompilace. Každá funkce provede porovnání řetězců bez rozlišování velkých a malých písmen. Porovnání závisí na LC_CTYPE aspektu národního prostředí, ale ne LC_COLLATE. Další informace najdete v tématu [_stricmp, _wcsicmp, _mbsicmp _stricmp_l, _wcsicmp_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)_mbsicmp_l.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#111](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_6.cpp)]

##  <a name="cstringt"></a>CStringt:: CStringt

Vytvoří objekt `CStringT`.

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

*PCH*<br/>
Ukazatel na pole znaků s délkou *nLength*, ne zakončené znakem null.

*nLength*<br/>
Počet znaků v souboru *PCH*.

*Zvolte*<br/>
Jeden znak.

*pszSrc*<br/>
Řetězec zakončený hodnotou null bude zkopírován do tohoto objektu `CStringT`.

*pStringMgr*<br/>
Ukazatel na správce paměti pro objekt `CStringT`. Další informace o správě `IAtlStringMgr` a paměti pro `CStringT`najdete v tématu [Správa paměti pomocí CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

*strSrc*<br/>
Existující objekt `CStringT`, který se má zkopírovat do tohoto objektu `CStringT` Další informace o `CThisString` a `CThisSimpleString`najdete v části poznámky.

*varSrc*<br/>
Objekt variant, který má být zkopírován do tohoto objektu `CStringT`.

*BaseType*<br/>
Typ znaku řetězcové třídy. Může být jedna z následujících akcí:

**char** (pro řetězce znaků ANSI).

**wchar_t** (pro řetězce znaků Unicode).

TCHAR (pro řetězce znaků ANSI a Unicode).

*bMFCDLL*<br/>
Logická hodnota, která určuje, zda se jedná o projekt knihovny MFC DLL (TRUE) nebo ne (FALSE).

*SystemString*<br/>
Musí být `System::String`a projekt musí být zkompilován pomocí parametrem/CLR.

*pString*<br/>
Popisovač pro objekt `CStringT`.

### <a name="remarks"></a>Poznámky

Vzhledem k tomu, že konstruktory kopírují vstupní data do nového přiděleného úložiště, měli byste si být vědomi, že by mohlo dojít k výjimkám paměti. Všimněte si, že některé z těchto konstruktorů fungují jako funkce pro převod. To vám umožňuje nahradit například LPTSTR, kde se očekává objekt `CStringT`.

- `CStringT`(`LPCSTR` `lpsz`): sestaví `CStringT` Unicode z řetězce ANSI. Tento konstruktor lze také použít k načtení prostředku řetězce, jak je znázorněno v následujícím příkladu.

- `CStringT(` `LPCWSTR` `lpsz`): sestaví `CStringT` z řetězce Unicode.

- `CStringT`(`const unsigned char*` `psz`): umožňuje vytvořit `CStringT` z ukazatele na **nepodepsaný znak**.

> [!NOTE]
>  Definujte makro _CSTRING_DISABLE_NARROW_WIDE_CONVERSION pro vypnutí implicitního převodu řetězce mezi řetězci ANSI a Unicode. Makro vyloučí z kompilačních konstruktorů, které podporují převod.

Všimněte si, že parametr *strSrc* může být buď objekt `CStringT` nebo `CThisSimpleString`. Pro `CStringT`použijte jednu z jeho výchozích instancí (`CString`, `CStringA`nebo `CStringW`); pro `CThisSimpleString`použijte **Tento** ukazatel. `CThisSimpleString` deklaruje instanci [třídy CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md), která je menší řetězcové třídy s menší integrovanou funkcí než `CStringT`ou třídou.

Operátor přetížení `CSimpleStringT<>&()` vytvoří objekt `CStringT` z deklarace `CSimpleStringT`.

> [!NOTE]
>  I když je možné vytvořit `CStringT` instance, které obsahují vložené znaky null, doporučujeme proti ní. Volání metod a operátorů na `CStringT` objekty, které obsahují vložené znaky null, mohou způsobit neočekávané výsledky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#112](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_7.cpp)]

##  <a name="_dtorcstringt"></a>CStringt:: ~ CStringt

Odstraní objekt `CStringT`.

```
~CStringT() throw();
```

### <a name="remarks"></a>Poznámky

Odstraní objekt `CStringT`.

##  <a name="delete"></a>CStringt::D dstranit

Odstraní znak nebo znaky z řetězce začínajícího znakem na daném indexu.

```
int Delete(int iIndex, int nCount = 1);
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
Index založený na nule prvního znaku v objektu `CStringT`, který se má odstranit.

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

*-zahájení*<br/>
Index znaku v řetězci, ve kterém má být zahájeno hledání, nebo 0, aby bylo možné začít od začátku.

*Zvolte*<br/>
Jeden znak, který chcete vyhledat.

### <a name="return-value"></a>Návratová hodnota

Index založený na nule prvního znaku v tomto objektu `CStringT`, který se shoduje s požadovaným podřetězcem nebo znaky; -1, pokud nebyl nalezen dílčí řetězec nebo znak.

### <a name="remarks"></a>Poznámky

Funkce je přetížena, aby přijímala jednotlivé znaky (podobně jako funkce modulu runtime `strchr`) a řetězce (podobně jako `strstr`).

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

Zapisuje formátovaná data do `CStringT` stejným způsobem, jakým [sprintf_s](../../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md) formátuje data do pole znaků ve stylu jazyka C.

```
void __cdecl Format(UINT nFormatID, [, argument]...);
void __cdecl Format(PCXSTR pszFormat,  [, argument] ...);
```

### <a name="parameters"></a>Parametry

*nFormatID*<br/>
Identifikátor prostředku řetězce, který obsahuje řetězec řízení formátu.

*pszFormat*<br/>
Řetězec řízení formátu.

*Argument*<br/>
Volitelné argumenty

### <a name="remarks"></a>Poznámky

Tato funkce formátuje a ukládá řadu znaků a hodnot v `CStringT`. Každý volitelný argument (pokud existuje) je převeden a výstup podle odpovídající specifikace formátu v *pszFormat* nebo z prostředku řetězce identifikovaného parametrem *nFormatID*.

Volání se nezdaří, pokud je samotný objekt String nabídnut jako parametr pro `Format`. Například následující kód způsobí nepředvídatelné výsledky:

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

*Argument*<br/>
Volitelné argumenty

### <a name="remarks"></a>Poznámky

Funkce vyžaduje jako vstup definici zprávy. Definice zprávy je určena *pszFormat* nebo z prostředku řetězce identifikovaného pomocí *nFormatID*. Funkce zkopíruje formátovaný text zprávy do objektu `CStringT` a v případě potřeby zpracovává všechny vložené sekvence vložení.

> [!NOTE]
> `FormatMessage` se pokusí přidělit systémovou paměť pro nově formátovaný řetězec. Pokud tento pokus neproběhne úspěšně, dojde k automatickému vyvolání výjimky paměti.

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
Odkazuje na řetězec řízení formátu. Bude prohledáván pro odpovídající vložení a formátování. Formátovací řetězec je podobný běhovým řetězcům formátu `printf`ve stylu, s výjimkou umožňuje vložení parametrů v libovolném pořadí.

*pArgList*<br/>
Ukazatel na seznam argumentů.

### <a name="remarks"></a>Poznámky

Funkce vyžaduje jako vstup definici zprávy určenou funkcí *pszFormat*. Funkce zkopíruje formátovaný text zprávy a seznam argumentů do objektu `CStringT` a v případě potřeby zpracovává všechny vložené sekvence vložení.

> [!NOTE]
> `FormatMessageV` volá [CStringT:: FormatMessage](#formatmessage), která se pokusí přidělit systémovou paměť pro nově formátovaný řetězec. Pokud tento pokus neproběhne úspěšně, dojde k automatickému vyvolání výjimky paměti.

Další informace najdete v Windows SDK funkci Windows [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) .

##  <a name="formatv"></a>CStringt:: FormatV

Formátuje řetězec zprávy pomocí seznamu argumentů proměnných.

```
void FormatV(PCXSTR pszFormat, va_list args);
```

### <a name="parameters"></a>Parametry

*pszFormat*<br/>
Odkazuje na řetězec řízení formátu. Bude prohledáván pro odpovídající vložení a formátování. Formátovací řetězec je podobný běhovým řetězcům formátu `printf`ve stylu, s výjimkou umožňuje vložení parametrů v libovolném pořadí.

*argumentů*<br/>
Ukazatel na seznam argumentů.

### <a name="remarks"></a>Poznámky

Zapíše formátovaný řetězec a seznam proměnných argumentů do řetězce `CStringT` stejným způsobem, jakým `vsprintf_s` formátuje data do pole znaků ve stylu jazyka C.

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

*Zvolte*<br/>
Znak, který má být vložen.

### <a name="return-value"></a>Návratová hodnota

Délka změněného řetězce.

### <a name="remarks"></a>Poznámky

Parametr *iIndex* identifikuje první znak, který bude přesunut, aby uvolnil místo pro daný znak nebo podřetězec. Pokud je *nIndex* nula, vložení proběhne před celým řetězcem. Pokud je *nIndex* větší než délka řetězce, funkce bude zřetězit aktuální řetězec a nový materiál poskytnutý buď *ch* , nebo *PSZ*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#122](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_17.cpp)]

##  <a name="left"></a>CStringt:: Left

Extrahuje zcela *nCount* znaky z tohoto objektu `CStringT` a vrátí kopii extrahované podřetězce.

```
CStringT Left(int nCount) const;
```

### <a name="parameters"></a>Parametry

*nCount*<br/>
Počet znaků, které mají být extrahovány z tohoto objektu `CStringT`.

### <a name="return-value"></a>Návratová hodnota

Objekt `CStringT`, který obsahuje kopii zadaného rozsahu znaků. Vrácený objekt `CStringT` může být prázdný.

### <a name="remarks"></a>Poznámky

Pokud *nCount* překračuje délku řetězce, bude extrahován celý řetězec. `Left` je podobná funkci Basic `Left`.

Pro vícebajtové znakové sady (MBCS) *nCount* zachází s každou 8bitové sekvencí jako znak, takže *nCount* vrátí počet vícebajtových znaků vynásobený dvěma.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#123](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_18.cpp)]

##  <a name="loadstring"></a>CStringt:: LoadString

Přečte prostředek řetězce Windows identifikovaný *NID*do existujícího objektu `CStringT`.

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

Převede objekt `CStringT` na malý řetězec.

```
CStringT& MakeLower();
```

### <a name="return-value"></a>Návratová hodnota

Výsledný řetězec malými písmeny.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#125](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_20.cpp)]

##  <a name="makereverse"></a>CStringt:: MakeReverse

Obrátí pořadí znaků v objektu `CStringT`.

```
CStringT& MakeReverse();
```

### <a name="return-value"></a>Návratová hodnota

Výsledný stornovaný řetězec.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#126](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_21.cpp)]

##  <a name="makeupper"></a>CStringt:: MakeUpper

Převede objekt `CStringT` na řetězec na velká písmena.

```
CStringT& MakeUpper();
```

### <a name="return-value"></a>Návratová hodnota

Výsledný řetězec na velká písmena.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#127](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_22.cpp)]

##  <a name="mid"></a>CStringt:: Mid

Extrahuje podřetězec délky *nCount* znaků z tohoto objektu `CStringT` od pozice *iFirst* (počítáno od nuly).

```
CStringT Mid(int iFirst, int nCount) const;
CStringT Mid(int iFirst) const;
```

### <a name="parameters"></a>Parametry

*iFirst*<br/>
Index založený na nule prvního znaku v tomto objektu `CStringT`, který má být zahrnut do extrahovaný podřetězec.

*nCount*<br/>
Počet znaků, které mají být extrahovány z tohoto objektu `CStringT`. Pokud tento parametr není zadán, je extrahován zbytek řetězce.

### <a name="return-value"></a>Návratová hodnota

Objekt `CStringT`, který obsahuje kopii zadaného rozsahu znaků. Počítejte s tím, že vrácený objekt `CStringT` může být prázdný.

### <a name="remarks"></a>Poznámky

Funkce vrátí kopii extrahované podřetězce. `Mid` je podobná základní funkci Mid (s výjimkou toho, že indexy na úrovni Basic jsou založené na jednom).

Pro vícebajtové znakové sady (MBCS) *nCount* odkazuje na každý 8bitový znak; To znamená, že vedoucí a koncový bajt v jednom vícebajtovém znaku se počítají jako dva znaky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#128](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_23.cpp)]

##  <a name="oemtoansi"></a>CStringt:: OemToAnsi

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
`CStringT`, který se má přiřadit k tomuto řetězci.

*str*<br/>
Odkaz na objekt `CThisSimpleString`.

*bMFCDLL*<br/>
Logická hodnota určující, zda se jedná o projekt knihovny MFC DLL, nebo ne.

*BaseType*<br/>
Základní typ řetězce.

*var*<br/>
Objekt typu variant, který se má přiřadit k tomuto řetězci.

*Zvolte*<br/>
Znak ANSI nebo Unicode, který se má přiřadit k řetězci.

*pszSrc*<br/>
Ukazatel na původní přiřazený řetězec.

### <a name="remarks"></a>Poznámky

Operátor přiřazení akceptuje další objekt `CStringT`, znakový ukazatel nebo jeden znak. Počítejte s tím, že výjimky paměti mohou nastat vždy, když použijete tento operátor, protože může být přiděleno nové úložiště.

Informace o `CThisSimpleString`naleznete v části poznámky v [CStringT:: CStringT](#cstringt).

> [!NOTE]
> I když je možné vytvořit `CStringT` instance, které obsahují vložené znaky null, doporučujeme proti ní. Volání metod a operátorů na `CStringT` objekty, které obsahují vložené znaky null, mohou způsobit neočekávané výsledky.

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

*CH1*<br/>
Znak ANSI nebo Unicode, který má být zřetězen s řetězcem.

*CH2*<br/>
Znak ANSI nebo Unicode, který má být zřetězen s řetězcem.

*str1*<br/>
`CStringT` zřetězení s řetězcem nebo znakem.

*str2*<br/>
`CStringT` zřetězení s řetězcem nebo znakem.

*psz1*<br/>
Ukazatel na řetězec zakončený hodnotou null, který má být zřetězen s řetězcem nebo znakem.

*psz2*<br/>
Ukazatel na řetězec, který má být zřetězen s řetězcem nebo znakem.

### <a name="remarks"></a>Poznámky

Existuje sedm forem přetížení funkce `CStringT::operator+`. První verze zřetězí dva existující `CStringT` objekty. Následující dva zřetězení `CStringT` objekt a řetězec zakončený hodnotou null. Další dva zřetězení `CStringT` objektu a znaku ANSI. Poslední dva zřetězení `CStringT` objektu a znaku Unicode.

> [!NOTE]
>  I když je možné vytvořit `CStringT` instance, které obsahují vložené znaky null, doporučujeme proti ní. Volání metod a operátorů na `CStringT` objekty, které obsahují vložené znaky null, mohou způsobit neočekávané výsledky.

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
Odkaz na objekt `CThisSimpleString`.

*bMFCDLL*<br/>
Logická hodnota určující, zda se jedná o projekt knihovny MFC DLL, nebo ne.

*BaseType*<br/>
Základní typ řetězce.

*var*<br/>
Objekt variant, který se má zřetězit k tomuto řetězci.

*Zvolte*<br/>
Znak ANSI nebo Unicode, který má být zřetězen s řetězcem.

*pszSrc*<br/>
Ukazatel na řetězec, který se zřetězí.

*strSrc*<br/>
`CStringT`, který se má zřetězit k tomuto řetězci.

### <a name="remarks"></a>Poznámky

Operátor přijímá jiný objekt `CStringT`, znakový ukazatel nebo jeden znak. Je třeba si uvědomit, že výjimky paměti mohou nastat vždy, když použijete tento operátor zřetězení, protože nové úložiště lze přidělit pro znaky přidané do tohoto objektu `CStringT`.

Informace o `CThisSimpleString`naleznete v části poznámky v [CStringT:: CStringT](#cstringt).

> [!NOTE]
>  I když je možné vytvořit `CStringT` instance, které obsahují vložené znaky null, doporučujeme proti ní. Volání metod a operátorů na `CStringT` objekty, které obsahují vložené znaky null, mohou způsobit neočekávané výsledky.

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

*CH1*<br/>
Znak ANSI nebo Unicode pro porovnání.

*CH2*<br/>
Znak ANSI nebo Unicode pro porovnání.

*str1*<br/>
`CStringT` pro porovnání.

*str2*<br/>
`CStringT` pro porovnání.

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

*CH1*<br/>
Znak ANSI nebo Unicode, který má být zřetězen s řetězcem.

*CH2*<br/>
Znak ANSI nebo Unicode, který má být zřetězen s řetězcem.

*str1*<br/>
`CStringT` pro porovnání.

*str2*<br/>
`CStringT` pro porovnání.

*psz1*<br/>
Ukazatel na řetězec zakončený hodnotou null pro porovnání.

*psz2*<br/>
Ukazatel na řetězec zakončený hodnotou null pro porovnání.

### <a name="remarks"></a>Poznámky

Testuje, zda se řetězec nebo znak na levé straně nerovná řetězci nebo znaku na pravé straně.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#143](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_27.cpp)]

##  <a name="operator_lt"></a>CStringt:: operator &lt;

Určuje, zda je řetězec na levé straně operátoru menší než řetězec na pravé straně.

```
friend bool operator<(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parametry

*str1*<br/>
`CStringT` pro porovnání.

*str2*<br/>
`CStringT` pro porovnání.

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

##  <a name="operator_gt"></a>CStringt:: operator &gt;

Určuje, zda je řetězec na levé straně operátoru větší než řetězec na pravé straně.

```
friend bool operator>(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parametry

*str1*<br/>
`CStringT` pro porovnání.

*str2*<br/>
`CStringT` pro porovnání.

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

##  <a name="operator_lt_eq"></a>CStringt:: operator &lt;=

Určuje, zda je řetězec na levé straně operátoru menší než nebo roven řetězci na pravé straně.

```
friend bool operator<=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parametry

*str1*<br/>
`CStringT` pro porovnání.

*str2*<br/>
`CStringT` pro porovnání.

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

##  <a name="operator_gt_eq"></a>CStringt:: operator &gt;=

Určuje, zda je řetězec na levé straně operátoru větší než nebo roven řetězci na pravé straně.

```
friend bool operator>=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parametry

*str1*<br/>
`CStringT` pro porovnání.

*str2*<br/>
`CStringT` pro porovnání.

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

Existují dvě verze `Replace`. První verze nahrazuje jednu nebo více kopií podřetězce pomocí jiného podřetězce. Oba podřetězce jsou zakončené znakem null. Druhá verze nahrazuje jednu nebo více kopií znaku pomocí jiného znaku. Obě verze pracují s daty znaků uloženými v `CStringT`.

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

`Replace` může změnit délku řetězce, protože *pszNew* a *pszOld* nemusí mít stejnou délku a několik kopií starého podřetězce lze změnit na nový. Funkce provádí shodu rozlišující velká a malá písmena.

Příklady instancí `CStringT` jsou `CString`, `CStringA`a `CStringW`.

Pro `CStringA``Replace` pracuje se znaky ANSI nebo vícebajtových znaků (MBCS). V případě `CStringW``Replace` pracuje s velkým množstvím znaků.

Pro `CString`je v době kompilace vybraný znakový datový typ, a to na základě toho, jestli jsou definované konstanty v následující tabulce.

|Definovaná konstanta|Znakový datový typ|
|----------------------|-------------------------|
|_UNICODE|Široké znaky|
|_MBCS|Dvoubajtové znaky|
|Ani jedno|Jednobajtové znaky|
|Obojí|Nedefinováno|

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#200](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_33.cpp)]

##  <a name="reversefind"></a>CStringt:: ReverseFind

Vyhledá tento objekt `CStringT` pro poslední shodu znaku.

```
int ReverseFind(XCHAR ch) const throw();
```

### <a name="parameters"></a>Parametry

*Zvolte*<br/>
Znak, který chcete vyhledat.

### <a name="return-value"></a>Návratová hodnota

Index založený na nule posledního znaku v tomto objektu `CStringT`, který odpovídá požadovanému znaku, nebo-1, pokud znak nebyl nalezen.

### <a name="remarks"></a>Poznámky

Funkce je podobná `strrchr`běhové funkci.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#130](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_34.cpp)]

##  <a name="right"></a>CStringt:: Right

Extrahuje poslední (tj.) *nCount* znaky z tohoto objektu `CStringT` a vrátí kopii extrahované podřetězce.

```
CStringT Right(int nCount) const;
```

### <a name="parameters"></a>Parametry

*nCount*<br/>
Počet znaků, které mají být extrahovány z tohoto objektu `CStringT`.

### <a name="return-value"></a>Návratová hodnota

Objekt `CStringT`, který obsahuje kopii zadaného rozsahu znaků. Počítejte s tím, že vrácený objekt `CStringT` může být prázdný.

### <a name="remarks"></a>Poznámky

Pokud *nCount* překračuje délku řetězce, bude extrahován celý řetězec. `Right` je podobná funkci Basic `Right` (s výjimkou toho, že indexy na úrovni Basic jsou založené na nule).

Pro vícebajtové znakové sady (MBCS) *nCount* odkazuje na každý 8bitový znak; To znamená, že vedoucí a koncový bajt v jednom vícebajtovém znaku se počítají jako dva znaky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#131](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_35.cpp)]

##  <a name="setsysstring"></a>CStringt:: SetSysString

Znovu přidělí objekt BSTR, na který odkazuje *pbstr* , a zkopíruje do něj obsah objektu `CStringT`, včetně znaku null.

```
BSTR SetSysString(BSTR* pbstr) const;
```

### <a name="parameters"></a>Parametry

*pbstr*<br/>
Ukazatel na řetězec znaků.

### <a name="return-value"></a>Návratová hodnota

Nový řetězec.

### <a name="remarks"></a>Poznámky

V závislosti na obsahu `CStringT`ho objektu se může změnit hodnota BSTR, na kterou odkazuje *pbstr* . Funkce vyvolá `CMemoryException`, pokud existuje nedostatek paměti.

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

Podřetězec obsahující znaky v řetězci, které nejsou v *pszCharSet*počínaje prvním znakem v řetězci a končí prvním znakem nalezeným v řetězci, který je také v *pszCharSet* (tj. počínaje prvním znakem v řetězci a až s výjimkou prvního znaku v řetězci, který je nalezen *pszCharSet*). Vrátí celý řetězec, pokud v *pszCharSet* není žádný znak v řetězci.

### <a name="remarks"></a>Poznámky

`SpanExcluding` extrahuje a vrátí všechny znaky předcházející prvnímu výskytu znaku z *pszCharSet* (jinými slovy znak z *pszCharSet* a všechny znaky, které následují v řetězci, se nevrátí). Pokud v řetězci není nalezen žádný znak z *pszCharSet* , pak `SpanExcluding` vrátí celý řetězec.

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

Podřetězec, který obsahuje znaky v řetězci, které jsou v *pszCharSet*, počínaje prvním znakem v řetězci a končící při nalezení znaku v řetězci, který není v *pszCharSet*. `SpanIncluding` vrátí prázdný podřetězec, pokud první znak v řetězci není v zadané sadě.

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

*-zahájení*<br/>
Index založený na nule pro zahájení hledání.

### <a name="return-value"></a>Návratová hodnota

Objekt `CStringT` obsahující aktuální hodnotu tokenu.

### <a name="remarks"></a>Poznámky

Funkce `Tokenize` vyhledá další token v cílovém řetězci. Sada znaků v *pszTokens* určuje možné oddělovače tokenu, který se má najít. Při každém volání `Tokenize` funkce *začíná na začátku,* přeskočí úvodní oddělovače a vrátí objekt `CStringT` obsahující aktuální token, což je řetězec znaků až k dalšímu znaku oddělovače. Hodnota parametru- *Start* je aktualizována tak, aby byla pozice za koncovým znakem oddělovače, nebo-1, pokud bylo dosaženo konce řetězce. Další tokeny mohou být rozděleny ze zbytku cílového řetězce řadou volání `Tokenize`, pomocí parametru- *Start* pro udržení přehledu o tom, kde v řetězci je další token čten. Pokud nejsou k dispozici žádné další tokeny, funkce vrátí prázdný řetězec a příkaz set- *Start* bude nastaven na hodnotu-1.

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
Ukazatel na řetězec obsahující cílové znaky, které mají být oříznuty. Všechny úvodní a koncové výskyty znaků v *pszTarget* budou oříznuty z objektu `CStringT`.

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
Ukazatel na řetězec obsahující cílové znaky, které mají být oříznuty. Všechny úvodní výskyty znaků v *pszTarget* budou oříznuty z objektu `CStringT`.

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
Ukazatel na řetězec obsahující cílové znaky, které mají být oříznuty. Všechny koncové výskyty znaků v *pszTarget* budou oříznuty z objektu `CStringT`.

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt `CStringT`, který obsahuje oříznutý řetězec.

### <a name="remarks"></a>Poznámky

Odebere koncové výskyty jednoho z následujících:

- Znak určený parametrem *chTarget*.

- Všechny znaky nalezené v řetězci určeném parametrem *pszTargets*.

- Typy.

Verze `CStringT& TrimRight(XCHAR chTarget)` přijímá jeden parametr znaku a odstraní všechny kopie tohoto znaku z konce `CStringT` řetězcových dat. Začíná na konci řetězce a funguje směrem dopředu. Zastaví se, když najde jiný znak nebo když `CSTringT` vyčerpá znaková data.

Verze `CStringT& TrimRight(PCXSTR pszTargets)` přijímá řetězec zakončený hodnotou null, který obsahuje všechny různé znaky, které chcete vyhledat. Odebere všechny kopie těchto znaků v objektu `CStringT`. Začíná na konci řetězce a funguje směrem dopředu. Zastaví se, když najde znak, který není v cílovém řetězci, nebo když `CStringT` vyčerpá znaková data. Nepokusí se najít celý cílový řetězec na podřetězec na konci `CStringT`.

Verze `CStringT& TrimRight()` nepožaduje žádné parametry. Ořízne všechny koncové prázdné znaky z konce `CStringT` řetězce. Prázdné znaky mohou být zalomení řádků, mezery nebo tabulátory.

-

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#138](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_42.cpp)]

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Sdílené třídy ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)<br/>
[CSimpleStringT – třída](../../atl-mfc-shared/reference/csimplestringt-class.md)
