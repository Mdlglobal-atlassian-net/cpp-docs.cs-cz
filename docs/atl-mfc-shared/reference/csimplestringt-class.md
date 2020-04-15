---
title: CSimpleStringT – třída
ms.date: 10/18/2018
f1_keywords:
- CSimpleStringT
- ATLSIMPSTR/ATL::CSimpleStringT
- ATLSIMPSTR/ATL::CSimpleStringT::PCXSTR
- ATLSIMPSTR/ATL::CSimpleStringT::PXSTR
- ATLSIMPSTR/ATL::CSimpleStringT::CSimpleStringT
- ATLSIMPSTR/ATL::CSimpleStringT::Append
- ATLSIMPSTR/ATL::CSimpleStringT::AppendChar
- ATLSIMPSTR/ATL::CSimpleStringT::CopyChars
- ATLSIMPSTR/ATL::CSimpleStringT::CopyCharsOverlapped
- ATLSIMPSTR/ATL::CSimpleStringT::Empty
- ATLSIMPSTR/ATL::CSimpleStringT::FreeExtra
- ATLSIMPSTR/ATL::CSimpleStringT::GetAllocLength
- ATLSIMPSTR/ATL::CSimpleStringT::GetAt
- ATLSIMPSTR/ATL::CSimpleStringT::GetBuffer
- ATLSIMPSTR/ATL::CSimpleStringT::GetBufferSetLength
- ATLSIMPSTR/ATL::CSimpleStringT::GetLength
- ATLSIMPSTR/ATL::CSimpleStringT::GetManager
- ATLSIMPSTR/ATL::CSimpleStringT::GetString
- ATLSIMPSTR/ATL::CSimpleStringT::IsEmpty
- ATLSIMPSTR/ATL::CSimpleStringT::LockBuffer
- ATLSIMPSTR/ATL::CSimpleStringT::Preallocate
- ATLSIMPSTR/ATL::CSimpleStringT::ReleaseBuffer
- ATLSIMPSTR/ATL::CSimpleStringT::ReleaseBufferSetLength
- ATLSIMPSTR/ATL::CSimpleStringT::SetAt
- ATLSIMPSTR/ATL::CSimpleStringT::SetManager
- ATLSIMPSTR/ATL::CSimpleStringT::SetString
- ATLSIMPSTR/ATL::CSimpleStringT::StringLength
- ATLSIMPSTR/ATL::CSimpleStringT::Truncate
- ATLSIMPSTR/ATL::CSimpleStringT::UnlockBuffer
helpviewer_keywords:
- shared classes, CSimpleStringT
- strings [C++], ATL class
- CSimpleStringT class
ms.assetid: 15814fcb-5b8f-4425-a97e-3b61fc9b48d8
ms.openlocfilehash: dce33289699b9e7b7484d1feb6335476f93dee9b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317690"
---
# <a name="csimplestringt-class"></a>CSimpleStringT – třída

Tato třída `CSimpleStringT` představuje objekt.

## <a name="syntax"></a>Syntaxe

```
template <typename BaseType>
class CSimpleStringT
```

### <a name="parameters"></a>Parametry

*BaseType*<br/>
Typ znaku třídy řetězce. Může to být jedna z následujících možností:

- **char** (pro řetězce znaků ANSI).

- **wchar_t** (pro řetězce znaků Unicode).

- TCHAR (pro řetězce znaků ANSI i Unicode).

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

|Name (Název)|Popis|
|----------|-----------------|
|[CSimpleStringT::PCXSTR](#pcxstr)|Ukazatel na konstantní řetězec.|
|[CSimpleStringT::PXSTR](#pxstr)|Ukazatel na řetězec.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CSimpleStringT::CSimpleStringT](#ctor)|Vytváří `CSimpleStringT` objekty různými způsoby.|
|[CSimpleStringT::~CSimpleStringT](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CSimpleStringT::Připojit](#append)|Připojí `CSimpleStringT` objekt k existujícímu `CSimpleStringT` objektu.|
|[CSimpleStringT::AppendChar](#appendchar)|Připojí znak k existujícímu `CSimpleStringT` objektu.|
|[CSimpleStringT::CopyChars](#copychars)|Zkopíruje znak nebo znaky do jiného řetězce.|
|[CSimpleStringT::CopyCharsOverlapped](#copycharsoverlapped)|Zkopíruje znak nebo znaky do jiného řetězce, ve kterém se vyrovnávací paměti překrývají.|
|[CSimpleStringT::Prázdný](#empty)|Vynutí, aby řetězec měl délku nula.|
|[CSimpleStringT::FreeExtra](#freeextra)|Uvolní všechny další paměti dříve přidělené objektu řetězce.|
|[CSimpleStringT::GetAllocLength](#getalloclength)|Načte přidělenou délku `CSimpleStringT` objektu.|
|[CSimpleStringt::Getat](#getat)|Vrátí znak na dané pozici.|
|[CSimpleStringT::GetBuffer](#getbuffer)|Vrátí ukazatel na znaky `CSimpleStringT`v .|
|[CSimpleStringT::GetBufferSetLength](#getbuffersetlength)|Vrátí ukazatel na znaky `CSimpleStringT`v , zkrácení na zadanou délku.|
|[CSimpleStringT::GetLength](#getlength)|Vrátí počet znaků v `CSimpleStringT` objektu.|
|[CSimpleStringT::GetManager](#getmanager)|Načte správce paměti `CSimpleStringT` objektu.|
|[CSimpleStringT::GetString](#getstring)|Načte řetězec znaků.|
|[CSimpleStringT::Jeprázdný](#isempty)|Testuje, `CSimpleStringT` zda objekt neobsahuje žádné znaky.|
|[CSimpleStringT::Lockbuffer](#lockbuffer)|Zakáže počítání odkazů a chrání řetězec ve vyrovnávací paměti.|
|[CSimpleStringT::Preallocate](#preallocate)|Přiděluje určité množství paměti pro vyrovnávací paměť znaků.|
|[CSimpleStringT::Uvolnění vyrovnávací paměti](#releasebuffer)|Uvolní řízení vyrovnávací paměti `GetBuffer`vrácené .|
|[CSimpleStringT::UvolněníbufferSetLength](#releasebuffersetlength)|Uvolní řízení vyrovnávací paměti `GetBuffer`vrácené .|
|[CSimpleStringT::Setat](#setat)|Nastaví znak na dané pozici.|
|[CSimpleStringT::SetManager](#setmanager)|Nastaví správce paměti `CSimpleStringT` objektu.|
|[CSimpleStringT::SetString](#setstring)|Nastaví řetězec `CSimpleStringT` objektu.|
|[CSimpleStringT::Délka řetězce](#stringlength)|Vrátí počet znaků v zadaném řetězci.|
|[CSimpleStringT::Zkrátit](#truncate)|Zkrátí řetězec na zadanou délku.|
|[CSimpleStringT::Odemknout vyrovnávací paměť](#unlockbuffer)|Povolí počítání odkazů a uvolní řetězec ve vyrovnávací paměti.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CSimpleStringT::operátor PCXSTR](#operator_pcxstr)|Přímo přistupuje `CSimpleStringT` k znakům uloženým v objektu jako řetězec ve stylu C.|
|[CSimpleStringT::operátor\[\]](#operator_at)|Vrátí znak na dané pozici – `GetAt`substituce operátora pro .|
|[CSimpleStringT::operátor +=](#operator_add_eq)|Zřetězí nový řetězec na konec existujícího řetězce.|
|[CSimpleStringT::operátor =](#operator_eq)|Přiřadí objektu novou `CSimpleStringT` hodnotu.|

### <a name="remarks"></a>Poznámky

`CSimpleStringT`je základní třída pro různé třídy řetězců podporované visual c++. Poskytuje minimální podporu pro správu paměti objektu řetězce a základní manipulaci vyrovnávací paměti. Další pokročilé objekty řetězce naleznete v tématu [CStringT Class](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlsimpstr.h

## <a name="csimplestringtappend"></a><a name="append"></a>CSimpleStringT::Připojit

Připojí `CSimpleStringT` objekt k existujícímu `CSimpleStringT` objektu.

### <a name="syntax"></a>Syntaxe

```
void Append(const CSimpleStringT& strSrc);
void Append(PCXSTR pszSrc, int nLength);
void Append(PCXSTR pszSrc);
```

#### <a name="parameters"></a>Parametry

*strSrc*<br/>
Objekt, `CSimpleStringT` který má být připojen.

*pszSrc*<br/>
Ukazatel na řetězec obsahující znaky, které mají být připojeny.

*nDélka*<br/>
Počet znaků připojit.

### <a name="remarks"></a>Poznámky

Volání této metody připojit `CSimpleStringT` existující objekt `CSimpleStringT` k jinému objektu.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::Append`.

```cpp
CSimpleString str1(pMgr), str2(pMgr);
str1.SetString(_T("Soccer is"));
str2.SetString(_T(" an elegant game"));
str1.Append(str2);
ASSERT(_tcscmp(str1, _T("Soccer is an elegant game")) == 0);
```

## <a name="csimplestringtappendchar"></a><a name="appendchar"></a>CSimpleStringT::AppendChar

Připojí znak k existujícímu `CSimpleStringT` objektu.

### <a name="syntax"></a>Syntaxe

```
void AppendChar(XCHAR ch);
```

#### <a name="parameters"></a>Parametry

*Ch*<br/>
Znak, který má být připojen

### <a name="remarks"></a>Poznámky

Volání této funkce připojit zadaný znak na `CSimpleStringT` konec existujícího objektu.

## <a name="csimplestringtcopychars"></a><a name="copychars"></a>CSimpleStringT::CopyChars

Zkopíruje znak nebo `CSimpleStringT` znaky do objektu.

### <a name="syntax"></a>Syntaxe

```
static void CopyChars(
    XCHAR* pchDest,
    const XCHAR* pchSrc,
    int nChars) throw();
```

#### <a name="parameters"></a>Parametry

*pchDest*<br/>
Ukazatel na řetězec znaku.

*pchSrc řekl:*<br/>
Ukazatel na řetězec obsahující znaky, které mají být zkopírovány.

*nChars*<br/>
Počet *znaků pchSrc,* které mají být zkopírovány.

### <a name="remarks"></a>Poznámky

Volání této metody ke kopírování znaků z *pchSrc* do *řetězce pchDest.*

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::CopyChars`.

```cpp
CSimpleString str(_T("xxxxxxxxxxxxxxxxxxx"), 20, pMgr);
TCHAR* pszSrc = _T("Hello world!");
_tprintf_s(_T("%s\n"), str);
str.CopyChars(str.GetBuffer(), pszSrc, 12);
_tprintf_s(_T("%s\n"), str);
```

## <a name="csimplestringtcopycharsoverlapped"></a><a name="copycharsoverlapped"></a>CSimpleStringT::CopyCharsOverlapped

Zkopíruje znak nebo `CSimpleStringT` znaky do objektu.

### <a name="syntax"></a>Syntaxe

```
static void CopyCharsOverlapped(
    XCHAR* pchDest,
    const XCHAR* pchSrc,
    int nChars) throw();
```

#### <a name="parameters"></a>Parametry

*pchDest*<br/>
Ukazatel na řetězec znaku.

*pchSrc řekl:*<br/>
Ukazatel na řetězec obsahující znaky, které mají být zkopírovány.

*nChars*<br/>
Počet *znaků pchSrc,* které mají být zkopírovány.

### <a name="remarks"></a>Poznámky

Volání této metody ke kopírování znaků z *pchSrc* do *řetězce pchDest.* Na `CopyChars` `CopyCharsOverlapped` rozdíl od , poskytuje bezpečnou metodu pro kopírování z vyrovnávacích pamětí znaků, které mohou být překryty.

### <a name="example"></a>Příklad

Viz příklad [csimplestringt::CopyChars](#copychars)nebo zdrojový kód `CSimpleStringT::SetString` pro (nachází se v atlsimpstr.h).

## <a name="csimplestringtcsimplestringt"></a><a name="ctor"></a>CSimpleStringT::CSimpleStringT

Vytvoří `CSimpleStringT` objekt.

### <a name="syntax"></a>Syntaxe

```
CSimpleStringT(const XCHAR* pchSrc, int nLength, IAtlStringMgr* pStringMgr);
CSimpleStringT(PCXSTR pszSrc, IAtlStringMgr* pStringMgr);
CSimpleStringT(const CSimpleStringT& strSrc);
explicit CSimpleStringT(IAtlStringMgr* pStringMgr) throw();
```

#### <a name="parameters"></a>Parametry

*strSrc*<br/>
Existující `CSimpleStringT` objekt, který má `CSimpleStringT` být do tohoto objektu zkopírován.

*pchSrc řekl:*<br/>
Ukazatel na pole znaků délky *nLength*, není null ukončen.

*pszSrc*<br/>
Řetězec s ukončeným hodnotou null, `CSimpleStringT` který má být zkopírován do tohoto objektu.

*nDélka*<br/>
Počet znaků v . `pch`

*pStringMgr*<br/>
Ukazatel na správce paměti `CSimpleStringT` objektu. Další informace `IAtlStringMgr` o správě `CSimpleStringT`paměti pro , naleznete v [tématu Správa paměti a CStringT](../memory-management-with-cstringt.md).

### <a name="remarks"></a>Poznámky

Vytvořte `CSimpleStringT` nový objekt. Vzhledem k tomu, že konstruktory zkopírují vstupní data do nového přidělenéúložiště, může dojít k výjimkám paměti.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::CSimpleStringT` pomocí **atl typedef** `CSimpleString`. `CSimpleString`je běžně používaná specializace šablony `CSimpleStringT`třídy .

```cpp
CSimpleString s1(pMgr);
// Empty string
CSimpleString s2(_T("cat"), pMgr);
// From a C string literal

CSimpleString s3(s2);
// Copy constructor
CSimpleString s4(s2 + _T(" ") + s3);

// From a string expression
CSimpleString s5(_T("xxxxxx"), 6, pMgr);
// s5 = "xxxxxx"
```

## <a name="csimplestringtempty"></a><a name="empty"></a>CSimpleStringT::Prázdný

Vytvoří `CSimpleStringT` tento objekt prázdný řetězec a uvolní paměť podle potřeby.

### <a name="syntax"></a>Syntaxe

```
void Empty() throw();
```

### <a name="remarks"></a>Poznámky

Další informace naleznete [v tématu Strings: CString Exception Cleanup](../cstring-exception-cleanup.md).

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::Empty`.

```cpp
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```

## <a name="csimplestringtfreeextra"></a><a name="freeextra"></a>CSimpleStringT::FreeExtra

Uvolní všechny další paměti dříve přidělené řetězcem, ale již není potřeba.

### <a name="syntax"></a>Syntaxe

```
void FreeExtra();
```

### <a name="remarks"></a>Poznámky

To by mělo snížit nároky na paměť spotřebované objektem řetězce. Metoda přerozdělí vyrovnávací paměť na přesnou délku vrácenou [GetLength](#getlength).

### <a name="example"></a>Příklad

```cpp
CAtlString basestr;
IAtlStringMgr* pMgr;

pMgr= basestr.GetManager();
ASSERT(pMgr != NULL);

// Create a CSimpleString with 28 characters
CSimpleString str(_T("Many sports are fun to play."), 28, pMgr);
_tprintf_s(_T("Alloc length is %d, String length is %d\n"),
   str.GetAllocLength(), str.GetLength());

// Assigning a smaller string won't cause CSimpleString to free its
// memory, because it assumes the string will grow again anyway.
str = _T("Soccer is best!");
_tprintf_s(_T("Alloc length is %d, String length is %d\n"),
   str.GetAllocLength(), str.GetLength());

// This call forces CSimpleString to release the extra
// memory it doesn't need.
str.FreeExtra();
_tprintf_s(_T("Alloc length is %d, String length is %d\n"),
   str.GetAllocLength(), str.GetLength());
```

### <a name="remarks"></a>Poznámky

Výstup z tohoto příkladu je následující:

```Output
Alloc length is 1031, String length is 1024
Alloc length is 1031, String length is 15
Alloc length is 15, String length is 15
```

## <a name="csimplestringtgetalloclength"></a><a name="getalloclength"></a>CSimpleStringT::GetAllocLength

Načte přidělenou délku `CSimpleStringT` objektu.

### <a name="syntax"></a>Syntaxe

```
int GetAllocLength() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Počet znaků přidělených pro tento objekt.

### <a name="remarks"></a>Poznámky

Volání této metody k určení počtu znaků `CSimpleStringT` přidělených pro tento objekt. Viz [FreeExtra](#freeextra) příklad volání této funkce.

## <a name="csimplestringtgetat"></a><a name="getat"></a>CSimpleStringt::Getat

Vrátí jeden znak `CSimpleStringT` z objektu.

### <a name="syntax"></a>Syntaxe

```
XCHAR GetAt(int iChar) const;
```

#### <a name="parameters"></a>Parametry

*iChar*<br/>
Nulový index znaku v `CSimpleStringT` objektu. Parametr *iChar* musí být větší nebo roven 0 a menší než hodnota vrácená [getlength](#getlength). V `GetAt` opačném případě vygeneruje výjimku.

### <a name="return-value"></a>Návratová hodnota

A, `XCHAR` který obsahuje znak na zadané pozici v řetězci.

### <a name="remarks"></a>Poznámky

Volání této metody vrátit jeden znak určený *iChar*. Přetížený dolní index (**[]**) operátor `GetAt`je vhodný alias pro . Zakončení null je adresovatelné bez `GetAt`generování výjimky pomocí . Však není počítáno `GetLength`podle a vrácená hodnota je 0.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak `CSimpleStringT::GetAt`používat .

```cpp
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(s.GetAt(2) == _T('c'));
```

## <a name="csimplestringtgetbuffer"></a><a name="getbuffer"></a>CSimpleStringT::GetBuffer

Vrátí ukazatel na vnitřní znak `CSimpleStringT` vyrovnávací paměti pro objekt.

### <a name="syntax"></a>Syntaxe

```
PXSTR GetBuffer(int nMinBufferLength);
PXSTR GetBuffer();
```

#### <a name="parameters"></a>Parametry

*nMinBufferLength*<br/>
Minimální počet znaků, které může obsahovat vyrovnávací paměť znaků. Tato hodnota nezahrnuje místo pro zakončení null.

Pokud *nMinBufferLength* je větší než délka `GetBuffer` aktuální vyrovnávací paměti, zničí aktuální vyrovnávací paměti, nahradí ji vyrovnávací paměť požadované velikosti a obnoví počet odkazů na objekt na nulu. Pokud jste dříve volal [lockbuffer](#lockbuffer) na této vyrovnávací paměti, ztratíte zámek vyrovnávací paměti.

### <a name="return-value"></a>Návratová hodnota

Ukazatel `PXSTR` na vyrovnávací paměť znaku objektu (null ukončeno).

### <a name="remarks"></a>Poznámky

Volání této metody vrátit vyrovnávací `CSimpleStringT` obsah objektu. Vrácená `PXSTR` není konstanta, a proto `CSimpleStringT` umožňuje přímou úpravu obsahu.

Pokud použijete ukazatel `GetBuffer` vrácený změnit obsah řetězce, musíte volat [ReleaseBuffer](#releasebuffer) před použitím jakékoli jiné `CSimpleStringT` metody člena.

Adresa vrácená `GetBuffer` od nemusí být platná `ReleaseBuffer` po `CSimpleStringT` volání, `CSimpleStringT` protože další operace mohou způsobit přerozdělení vyrovnávací paměti. Vyrovnávací paměť není přerozdělena, pokud nezměníte `CSimpleStringT`délku .

Vyrovnávací paměť je automaticky `CSimpleStringT` uvolněna při zničení objektu.

Pokud budete sledovat délku řetězce sami, neměli byste připojit ukončující prázdný znak. Je však nutné zadat konečnou délku řetězce `ReleaseBuffer`při uvolnění vyrovnávací paměti s . Pokud připojíte ukončující znak null, měli byste předat -1 (výchozí) pro délku. `ReleaseBuffer`pak určuje délku vyrovnávací paměti.

Pokud není dostatek paměti `GetBuffer` pro splnění požadavku, tato metoda vyvolá CMemoryException*.

### <a name="example"></a>Příklad

```cpp
CSimpleString s(_T("abcd"), pMgr);
LPTSTR pBuffer = s.GetBuffer(10);
int sizeOfBuffer = s.GetAllocLength();

// Directly access CSimpleString buffer
_tcscpy_s(pBuffer, sizeOfBuffer, _T("Hello"));
ASSERT(_tcscmp(s, _T("Hello")) == 0);
s.ReleaseBuffer();
```

## <a name="csimplestringtgetbuffersetlength"></a><a name="getbuffersetlength"></a>CSimpleStringT::GetBufferSetLength

Vrátí ukazatel na vnitřní znak `CSimpleStringT` vyrovnávací paměti pro objekt, zkrácení nebo zvýšení jeho délky v případě potřeby přesně tak, aby přesně odpovídala délce zadané v *nLength*.

### <a name="syntax"></a>Syntaxe

```
PXSTR GetBufferSetLength(int nLength);
```

#### <a name="parameters"></a>Parametry

*nDélka*<br/>
Přesná velikost `CSimpleStringT` vyrovnávací paměti znaků ve znacích.

### <a name="return-value"></a>Návratová hodnota

Ukazatel `PXSTR` na vyrovnávací paměť znaku objektu (null ukončeno).

### <a name="remarks"></a>Poznámky

Volání této metody načíst zadanou délku `CSimpleStringT` vnitřní vyrovnávací paměti objektu. Vrácený `PXSTR` ukazatel není **const** a proto `CSimpleStringT` umožňuje přímou úpravu obsahu.

Pokud použijete ukazatel vrácený [GetBufferSetLength](#getbuffersetlength) ke změně `ReleaseBuffer` obsahu řetězce, `CsimpleStringT` volání aktualizovat vnitřní `CSimpleStringT` stav před použitím jiných metod.

Adresa vrácená `GetBufferSetLength` od nemusí být platná `ReleaseBuffer` po `CSimpleStringT` volání, `CSimpleStringT` protože další operace mohou způsobit přerozdělení vyrovnávací paměti. Vyrovnávací paměť není znovu přiřazena, pokud nezměníte délku `CSimpleStringT`.

Vyrovnávací paměť je automaticky `CSimpleStringT` uvolněna při zničení objektu.

Pokud budete sledovat délku řetězce sami, nepřipojujte ukončující znak null. Při uvolnění vyrovnávací paměti pomocí `ReleaseBuffer`aplikace je nutné určit konečnou délku řetězce. Pokud při `ReleaseBuffer`volání připojíte ukončující znak null , předaj te `ReleaseBuffer`-1 (výchozí) pro délku do aplikace a `ReleaseBuffer` provedete `strlen` vyrovnávací paměť, která určí jeho délku.

Další informace o počítání odkazů naleznete v následujících článcích:

- [Správa životnosti objektů prostřednictvím počítání odkazů](/windows/win32/com/managing-object-lifetimes-through-reference-counting) v sadě Windows SDK.

- [Implementace počítání odkazů](/windows/win32/com/implementing-reference-counting) v sadě Windows SDK.

- [Pravidla pro správu počty odkazů](/windows/win32/com/rules-for-managing-reference-counts) v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::GetBufferSetLength`.

```cpp
CSimpleString str(pMgr);
LPTSTR pstr = str.GetBufferSetLength(3);
pstr[0] = _T('C');
pstr[1] = _T('u');
pstr[2] = _T('p');

// No need for trailing zero or call to ReleaseBuffer()
// because GetBufferSetLength() set it for us.

str += _T(" soccer is best!");
ASSERT(_tcscmp(str, _T("Cup soccer is best!")) == 0);
```

## <a name="csimplestringtgetlength"></a><a name="getlength"></a>CSimpleStringT::GetLength

Vrátí počet znaků v `CSimpleStringT` objektu.

### <a name="syntax"></a>Syntaxe

```
int GetLength() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Počet znaků v řetězci.

### <a name="remarks"></a>Poznámky

Volání této metody vrátit počet znaků v objektu. Počet neobsahuje zakončení null.

U vícebajtových znakových sad `GetLength` (MBCS) počítá každý 8bitový znak; to znamená, že úvodní bajt a bajt stopy v jednom vícebajtovém znaku se počítají jako dva bajty. Viz [FreeExtra](#freeextra) příklad volání této funkce.

## <a name="csimplestringtgetmanager"></a><a name="getmanager"></a>CSimpleStringT::GetManager

Načte správce paměti `CSimpleStringT` objektu.

### <a name="syntax"></a>Syntaxe

```
IAtlStringMgr* GetManager() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na správce paměti `CSimpleStringT` pro objekt.

### <a name="remarks"></a>Poznámky

Volání této metody načíst správce `CSimpleStringT` paměti používá objekt. Další informace o správci paměti a objekty řetězce naleznete v [tématu Správa paměti a CStringT](../memory-management-with-cstringt.md).

## <a name="csimplestringtgetstring"></a><a name="getstring"></a>CSimpleStringT::GetString

Načte řetězec znaků.

### <a name="syntax"></a>Syntaxe

```
PCXSTR GetString() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na řetězec znaků ukončený nulou.

### <a name="remarks"></a>Poznámky

Volání této metody načíst řetězec `CSimpleStringT` znaků přidružené k objektu.

> [!NOTE]
> Vrácený `PCXSTR` ukazatel je **const** a neumožňuje přímé změny `CSimpleStringT` obsahu.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::GetString`.

```cpp
CSimpleString str(pMgr);
str += _T("Cup soccer is best!");
_tprintf_s(_T("%s"), str.GetString());
```

## <a name="csimplestringtisempty"></a><a name="isempty"></a>CSimpleStringT::Jeprázdný

Testuje `CSimpleStringT` objekt pro prázdnou podmínku.

### <a name="syntax"></a>Syntaxe

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu `CSimpleStringT` PRAVDA, pokud má objekt 0 délku; jinak FALSE.

### <a name="remarks"></a>Poznámky

Volání této metody k určení, pokud objekt obsahuje prázdný řetězec.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::IsEmpty`.

```cpp
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```

## <a name="csimplestringtlockbuffer"></a><a name="lockbuffer"></a>CSimpleStringT::Lockbuffer

Zakáže počítání odkazů a chrání řetězec ve vyrovnávací paměti.

### <a name="syntax"></a>Syntaxe

```
PXSTR LockBuffer();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CSimpleStringT` objekt nebo řetězec s nulovým ukončením.

### <a name="remarks"></a>Poznámky

Volání této metody zamknout `CSimpleStringT` vyrovnávací paměť objektu. Voláním `LockBuffer`vytvoříte kopii řetězce s -1 pro počet odkazů. Pokud je hodnota počtu odkazů -1, řetězec ve vyrovnávací paměti je považován za ve stavu "uzamčeno". V uzamčeném stavu je řetězec chráněn dvěma způsoby:

- Žádný jiný řetězec nemůže získat odkaz na data v uzamčeném řetězci, i když je tento řetězec přiřazen k uzamčenému řetězci.

- Uzamčený řetězec nikdy nebude odkazovat na jiný řetězec, i když je tento jiný řetězec zkopírován do uzamčeného řetězce.

Uzamčením řetězce ve vyrovnávací paměti zajistíte, že výhradní blokování řetězce ve vyrovnávací paměti zůstane beze změny.

Po dokončení s `LockBuffer`, volání [UnlockBuffer](#unlockbuffer) obnovit počet odkazů na 1.

> [!NOTE]
> Pokud zavoláte [GetBuffer](#getbuffer) na uzamčenou `GetBuffer` vyrovnávací `nMinBufferLength` paměť a nastavíte parametr na větší než délka aktuální vyrovnávací paměti, ztratíte zámek vyrovnávací paměti. Takové volání `GetBuffer` zničí aktuální vyrovnávací paměť, nahradí ji vyrovnávací pamětí požadované velikosti a obnoví počet odkazů na nulu.

Další informace o počítání odkazů naleznete v následujících článcích:

- [Správa životnosti objektů prostřednictvím počítání odkazů](/windows/win32/com/managing-object-lifetimes-through-reference-counting) v sadě Windows SDK

- [Implementace počítání odkazů](/windows/win32/com/implementing-reference-counting) v sadě Windows SDK

- [Pravidla pro správu počty odkazů](/windows/win32/com/rules-for-managing-reference-counts) v sadě Windows SDK

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::LockBuffer`.

```cpp
CSimpleString str(_T("Hello"), pMgr);
TCHAR ch;

str.LockBuffer();
ch = str.GetAt(2);
_tprintf_s(_T("%c"), ch);
str.UnlockBuffer();
```

## <a name="csimplestringtoperator"></a><a name="operator_at"></a>CSimpleStringT::operátor\[\]

Volání této funkce pro přístup k jeden znak pole znaků.

### <a name="syntax"></a>Syntaxe

```
XCHAR operator[](int iChar) const;
```

#### <a name="parameters"></a>Parametry

*iChar*<br/>
Nulový index znaku v řetězci.

### <a name="remarks"></a>Poznámky

Operátor přetížený dolní index (**[]** vrátí jeden znak určený indexem založeným na nule v *iChar*. Tento operátor je vhodnou náhradou za člennou funkci [GetAt.](#getat)

> [!NOTE]
> Pomocí operátoru dolníindex (**[]**) můžete získat hodnotu znaku `CSimpleStringT`v aplikaci , ale nelze `CSimpleStringT`jej použít ke změně hodnoty znaku v .

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::operator []`.

```cpp
CSimpleString s(_T("abc"), pMgr);
ASSERT(s[1] == _T('b'));
```

## <a name="csimplestringtoperator-"></a><a name="operator_at"></a>CSimpleStringT::operátor\[\]

Volání této funkce pro přístup k jeden znak pole znaků.

### <a name="syntax"></a>Syntaxe

```
XCHAR operator[](int iChar) const;
```

### <a name="parameters"></a>Parametry

*iChar*<br/>
Nulový index znaku v řetězci.

### <a name="remarks"></a>Poznámky

Operátor přetížený dolní index (**[]** vrátí jeden znak určený indexem založeným na nule v *iChar*. Tento operátor je vhodnou náhradou za člennou funkci [GetAt.](#getat)

> [!NOTE]
> Pomocí operátoru dolníindex (**[]**) můžete získat hodnotu znaku `CSimpleStringT`v aplikaci , ale nelze `CSimpleStringT`jej použít ke změně hodnoty znaku v .

## <a name="csimplestringtoperator-"></a><a name="operator_add_eq"></a>CSimpleStringT::operátor +=

Připojí nový řetězec nebo znak na konec existujícího řetězce.

### <a name="syntax"></a>Syntaxe

```
CSimpleStringT& operator +=(PCXSTR pszSrc);
CSimpleStringT& operator +=(const CSimpleStringT& strSrc);
template<int t_nSize>
CSimpleStringT& operator+=(const CStaticString< XCHAR, t_nSize >& strSrc);
CSimpleStringT& operator +=(char ch);
CSimpleStringT& operator +=(unsigned char ch);
CSimpleStringT& operator +=(wchar_t ch);
```

#### <a name="parameters"></a>Parametry

*pszSrc*<br/>
Ukazatel na řetězec ukončený nulou.

*strSrc*<br/>
Ukazatel na existující `CSimpleStringT` objekt.

*Ch*<br/>
Znak, který má být připojen.

### <a name="remarks"></a>Poznámky

Operátor přijme jiný `CSimpleStringT` objekt nebo znak. Všimněte si, že výjimky paměti může dojít při každém použití tohoto operátoru `CSimpleStringT` zřetězení, protože nové úložiště může být přiděleno pro znaky přidané do tohoto objektu.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::operator +=`.

```cpp
CSimpleString str(_T("abc"), pMgr);
ASSERT(_tcscmp((str += _T("def")), _T("abcdef")) == 0);
```

## <a name="csimplestringtoperator-"></a><a name="operator_eq"></a>CSimpleStringT::operátor =

Přiřadí objektu novou `CSimpleStringT` hodnotu.

### <a name="syntax"></a>Syntaxe

```
CSimpleStringT& operator =(PCXSTR pszSrc);
CSimpleStringT& operator =(const CSimpleStringT& strSrc);
```

#### <a name="parameters"></a>Parametry

*pszSrc*<br/>
Ukazatel na řetězec ukončený nulou.

*strSrc*<br/>
Ukazatel na existující `CSimpleStringT` objekt.

### <a name="remarks"></a>Poznámky

Pokud cílový řetězec (levá strana) je již dostatečně velký pro uložení nových dat, není provedeno žádné nové přidělení paměti. Všimněte si, že výjimky paměti může dojít při každém použití operátoru `CSimpleStringT` přiřazení, protože nové úložiště je často přidělena držet výsledný objekt.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::operator =`.

```cpp
CSimpleString s1(pMgr), s2(pMgr);
// Empty CSimpleStringT objects

s1 = _T("cat");
// s1 = "cat"
ASSERT(_tcscmp(s1, _T("cat")) == 0);

s2 = s1;               // s1 and s2 each = "cat"
ASSERT(_tcscmp(s2, _T("cat")) == 0);

s1 = _T("the ") + s1;
// Or expressions
ASSERT(_tcscmp(s1, _T("the cat")) == 0);

s1 = _T("x");
// Or just individual characters
ASSERT(_tcscmp(s1, _T("x")) == 0);
```

## <a name="csimplestringtoperator-pcxstr"></a><a name="operator_pcxstr"></a>CSimpleStringT::operátor PCXSTR

Přímo přistupuje `CSimpleStringT` k znakům uloženým v objektu jako řetězec ve stylu C.

### <a name="syntax"></a>Syntaxe

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel znaku na data řetězce.

### <a name="remarks"></a>Poznámky

Nejsou zkopírovány žádné znaky; je vrácen pouze ukazatel. Buďte opatrní s tímto operátorem. Pokud změníte `CString` objekt poté, co jste získali ukazatel znaku, může způsobit přerozdělení paměti, která zruší platnost ukazatele.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::operator PCXSTR`.

```cpp
// If the prototype of a function is known to the compiler,
// the PCXSTR cast operator may be invoked implicitly.

CSimpleString strSports(L"Soccer is Best!", pMgr);
WCHAR sz[1024];

wcscpy_s(sz, strSports);

// If the prototype isn't known or is a va_arg prototype,
// you must invoke the cast operator explicitly. For example,
// the va_arg part of a call to swprintf_s() needs the cast:

swprintf_s(sz, 1024, L"I think that %s!\n", (PCWSTR)strSports);

// While the format parameter is known to be an PCXSTR and
// therefore doesn't need the cast:

swprintf_s(sz, 1024, strSports);

// Note that some situations are ambiguous. This line will
// put the address of the strSports object to stdout:

wcout << strSports;

// while this line will put the content of the string out:

wcout << (PCWSTR)strSports;
```

## <a name="csimplestringtpcxstr"></a><a name="pcxstr"></a>CSimpleStringT::PCXSTR

Ukazatel na konstantní řetězec.

### <a name="syntax"></a>Syntaxe

```
typedef ChTraitsBase< BaseType >::PCXSTR PCXSTR;
```

## <a name="csimplestringtpreallocate"></a><a name="preallocate"></a>CSimpleStringT::Preallocate

Přidělí určité množství bajtů `CSimpleStringT` pro objekt.

### <a name="syntax"></a>Syntaxe

```
void Preallocate( int nLength);
```

#### <a name="parameters"></a>Parametry

*nDélka*<br/>
Přesná velikost `CSimpleStringT` vyrovnávací paměti znaků ve znacích.

### <a name="remarks"></a>Poznámky

Volání této metody přidělit konkrétní `CSimpleStringT` velikost vyrovnávací paměti pro objekt.

`CSimpleStringT`generuje výjimku STATUS_NO_MEMORY, pokud není schopen přidělit místo pro vyrovnávací paměť znaků. Ve výchozím nastavení je přidělování paměti prováděno funkcemi `HeapAlloc` rozhraní API WIN32 nebo `HeapReAlloc`.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::Preallocate`.

```cpp
CSimpleString str(pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
str.Preallocate(100);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
```

## <a name="csimplestringtpxstr"></a><a name="pxstr"></a>CSimpleStringT::PXSTR

Ukazatel na řetězec.

### <a name="syntax"></a>Syntaxe

```
typedef ChTraitsBase< BaseType >::PXSTR PXSTR;
```

## <a name="csimplestringtreleasebuffer"></a><a name="releasebuffer"></a>CSimpleStringT::Uvolnění vyrovnávací paměti

Uvolní řízení vyrovnávací paměti přidělené [GetBuffer](#getbuffer).

### <a name="syntax"></a>Syntaxe

```
void ReleaseBuffer(int nNewLength = -1);
```

#### <a name="parameters"></a>Parametry

*nNová délka*<br/>
Nová délka řetězce ve znacích, nepočítaje zakončení null. Pokud je řetězec ukončen, výchozí hodnota -1 `CSimpleStringT` nastaví velikost na aktuální délku řetězce.

### <a name="remarks"></a>Poznámky

Volání této metody přerozdělit nebo uvolnit vyrovnávací paměť objektu řetězce. Pokud víte, že řetězec ve vyrovnávací paměti je null ukončen, můžete vynechat *nNewLength* argument. Pokud váš řetězec není null ukončen, použijte *nNewLength* určit jeho délku. Adresa vrácená [GetBuffer](#getbuffer) je neplatná `ReleaseBuffer` po `CSimpleStringT` volání nebo jiné operace.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::ReleaseBuffer`.

```cpp
const int bufferSize = 1024;
CSimpleString s(_T("abc"), pMgr);
LPTSTR p = s.GetBuffer(bufferSize);
_tcscpy_s(p, bufferSize, _T("abc"));

// use the buffer directly
ASSERT(s.GetLength() == 3);

// String length = 3
s.ReleaseBuffer();

// Surplus memory released, p is now invalid.
ASSERT(s.GetLength() == 3);

// Length still 3
```

## <a name="csimplestringtreleasebuffersetlength"></a><a name="releasebuffersetlength"></a>CSimpleStringT::UvolněníbufferSetLength

Uvolní řízení vyrovnávací paměti přidělené [GetBuffer](#getbuffer).

### <a name="syntax"></a>Syntaxe

```
void ReleaseBufferSetLength(int nNewLength);
```

#### <a name="parameters"></a>Parametry

*nNová délka*<br/>
Délka uvolněného řetězce

### <a name="remarks"></a>Poznámky

Tato funkce je funkčně podobná [ReleaseBuffer](#releasebuffer) s tím rozdílem, že musí být předána platná délka objektu řetězce.

## <a name="csimplestringtsetat"></a><a name="setat"></a>CSimpleStringT::Setat

Nastaví jeden znak `CSimpleStringT` z objektu.

### <a name="syntax"></a>Syntaxe

```
void SetAt(int iChar, XCHAR ch);
```

#### <a name="parameters"></a>Parametry

*iChar*<br/>
Nulový index znaku v `CSimpleStringT` objektu. Parametr *iChar* musí být větší nebo roven 0 a menší než hodnota vrácená [getlength](#getlength).

*Ch*<br/>
Nová postava.

### <a name="remarks"></a>Poznámky

Volání této metody přepsat znak umístěný na *iChar*. Tato metoda nezvětší řetězec, pokud *iChar* překročí hranice existujícího řetězce.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::SetAt`.

```cpp
CSimpleString s(_T("abcdef"), pMgr);
s.SetAt(1, _T('a'));
ASSERT(_tcscmp(s, _T("aacdef")) == 0);
```

## <a name="csimplestringtsetmanager"></a><a name="setmanager"></a>CSimpleStringT::SetManager

Určuje správce paměti objektu. `CSimpleStringT`

### <a name="syntax"></a>Syntaxe

```
void SetManager(IAtlStringMgr* pStringMgr);
```

#### <a name="parameters"></a>Parametry

*pStringMgr*<br/>
Ukazatel na nový správce paměti.

### <a name="remarks"></a>Poznámky

Volání této metody určit nový správce `CSimpleStringT` paměti používá objekt. Další informace o správci paměti a objekty řetězce naleznete v [tématu Správa paměti a CStringT](../memory-management-with-cstringt.md).

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::SetManager`.

```cpp
CSimpleString s(pMgr);
s.SetManager(pCustomMgr);
```

## <a name="csimplestringtsetstring"></a><a name="setstring"></a>CSimpleStringT::SetString

Nastaví řetězec `CSimpleStringT` objektu.

### <a name="syntax"></a>Syntaxe

```
void SetString(PCXSTR pszSrc, int nLength);
void SetString(PCXSTR pszSrc);
```

#### <a name="parameters"></a>Parametry

*pszSrc*<br/>
Ukazatel na řetězec ukončený nulou.

*nDélka*<br/>
Počet znaků v *pszSrc*.

### <a name="remarks"></a>Poznámky

Zkopírujte řetězec `CSimpleStringT` do objektu. `SetString`přepíše starší řetězcová data ve vyrovnávací paměti.

Obě verze `SetString` zkontrolujte, zda *pszSrc* je nulový ukazatel, a pokud ano, vyvolat E_INVALIDARG chybu.

Jednoparametrová verze `SetString` očekává, že *pszSrc* přejde na řetězec s ukončeným hodnotou null.

Dvouparametrová verze `SetString` také očekává, že *pszSrc* bude řetězec s nulovým ukončeným. Používá *nLength* jako délku řetězce, pokud nejprve nenarazí na zakončení null.

Dvouparametrová verze `SetString` také kontroluje, zda *pszSrc* odkazuje na `CSimpleStringT`umístění v aktuální vyrovnávací paměti v . V tomto zvláštním `SetString` případě používá funkci kopírování paměti, která nepřepíše data řetězce, protože zkopíruje data řetězce zpět do vyrovnávací paměti.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::SetString`.

```cpp
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(_tcscmp(s, _T("abcdef")) == 0);
s.SetString(_T("Soccer"), 6);
ASSERT(_tcscmp(s, _T("Soccer")) == 0);
```

## <a name="csimplestringtstringlength"></a><a name="stringlength"></a>CSimpleStringT::Délka řetězce

Vrátí počet znaků v zadaném řetězci.

### <a name="syntax"></a>Syntaxe

```
ATL_NOINLINE static int StringLength(PCXSTR psz) throw();
```

#### <a name="parameters"></a>Parametry

*psz*<br/>
Ukazatel na řetězec ukončený nulou.

### <a name="return-value"></a>Návratová hodnota

Počet znaků v *psz*; nepočítám zakončení null.

### <a name="remarks"></a>Poznámky

Volání této metody načíst počet znaků v řetězci ukázal *psz*.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::StringLength`.

```cpp
ASSERT(CSimpleString::StringLength(_T("soccer")) == 6);
```

## <a name="csimplestringttruncate"></a><a name="truncate"></a>CSimpleStringT::Zkrátit

Zkrátí řetězec na novou délku.

### <a name="syntax"></a>Syntaxe

```
void Truncate(int nNewLength);
```

#### <a name="parameters"></a>Parametry

*nNová délka*<br/>
Nová délka řetězce.

### <a name="remarks"></a>Poznámky

Volání této metody zkrátit obsah řetězce na novou délku.

> [!NOTE]
> To nemá vliv na přidělenou délku vyrovnávací paměti. Chcete-li snížit nebo zvýšit aktuální vyrovnávací paměti, naleznete v [tématu FreeExtra](#freeextra) a [Preallocate](#preallocate).

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::Truncate`.

```cpp
CSimpleString str(_T("abcdefghi"), pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetLength());
_tprintf_s(_T("Contents: %s\n"), str);
str.Truncate(4);
_tprintf_s(_T("Allocated length: %d\n"), str.GetLength());
_tprintf_s(_T("Contents: %s\n"), str);
```

## <a name="csimplestringtunlockbuffer"></a><a name="unlockbuffer"></a>CSimpleStringT::Odemknout vyrovnávací paměť

Odemkne vyrovnávací `CSimpleStringT` paměť objektu.

### <a name="syntax"></a>Syntaxe

```
void UnlockBuffer() throw();
```

### <a name="remarks"></a>Poznámky

Volání této metody obnovit počet odkazů řetězce na 1.

`CSimpleStringT` Destruktor automaticky `UnlockBuffer` volá, aby zajistil, že vyrovnávací paměť není uzamčena při volání destruktoru. Příklad této metody naleznete v tématu [LockBuffer](#lockbuffer).

## <a name="csimplestringtcsimplestringt"></a><a name="dtor"></a>CSimpleStringT::~CSimpleStringT

Zničí `CSimpleStringT` objekt.

### <a name="syntax"></a>Syntaxe

```
~CSimpleStringT() throw();
```

### <a name="remarks"></a>Poznámky

Volání této metody `CSimpleStringT` zničit objekt.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Sdílené třídy KNIHOVNY ATL/Knihovny MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
