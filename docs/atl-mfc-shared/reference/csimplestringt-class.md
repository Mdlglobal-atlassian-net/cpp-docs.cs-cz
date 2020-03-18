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
ms.openlocfilehash: c033346b7a687a1c6778ad23e30ee0e73c787ad8
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418193"
---
# <a name="csimplestringt-class"></a>CSimpleStringT – třída

Tato třída reprezentuje objekt `CSimpleStringT`.

## <a name="syntax"></a>Syntaxe

```
template <typename BaseType>
class CSimpleStringT
```

### <a name="parameters"></a>Parametry

*BaseType*<br/>
Typ znaku řetězcové třídy. Může být jedna z následujících akcí:

- **char** (pro řetězce znaků ANSI).

- **wchar_t** (pro řetězce znaků Unicode).

- TCHAR (pro řetězce znaků ANSI a Unicode).

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Název|Popis|
|----------|-----------------|
|[CSimpleStringT::P CXSTR](#pcxstr)|Ukazatel na konstantní řetězec.|
|[CSimpleStringT::P XSTR](#pxstr)|Ukazatel na řetězec.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CSimpleStringT::CSimpleStringT](#ctor)|Sestavuje `CSimpleStringT` objekty různými způsoby.|
|[CSimpleStringT:: ~ CSimpleStringT](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CSimpleStringT:: Append](#append)|Připojí objekt `CSimpleStringT` k existujícímu objektu `CSimpleStringT`.|
|[CSimpleStringT::AppendChar](#appendchar)|Připojí znak k existujícímu objektu `CSimpleStringT`.|
|[CSimpleStringT::CopyChars](#copychars)|Zkopíruje znak nebo znaky do jiného řetězce.|
|[CSimpleStringT::CopyCharsOverlapped](#copycharsoverlapped)|Zkopíruje znak nebo znaky do jiného řetězce, ve kterém se překrývají vyrovnávací paměti.|
|[CSimpleStringT:: Empty](#empty)|Vynutí, aby měl řetězec nulovou délku.|
|[CSimpleStringT::FreeExtra](#freeextra)|Uvolní všechny nadbytečné paměti dříve přidělené objektem řetězce.|
|[CSimpleStringT::GetAllocLength](#getalloclength)|Načte přidělenou délku objektu `CSimpleStringT`.|
|[CSimpleStringT::GetAt](#getat)|Vrátí znak na dané pozici.|
|[CSimpleStringT:: GetBuffer](#getbuffer)|Vrátí ukazatel na znaky ve `CSimpleStringT`.|
|[CSimpleStringT::GetBufferSetLength](#getbuffersetlength)|Vrátí ukazatel na znaky ve `CSimpleStringT`, zkrácení na zadanou délku.|
|[CSimpleStringT:: GetLength](#getlength)|Vrátí počet znaků v objektu `CSimpleStringT`.|
|[CSimpleStringT:: GetManager](#getmanager)|Načte správce paměti objektu `CSimpleStringT`.|
|[CSimpleStringT:: GetString](#getstring)|Načte řetězec znaků.|
|[CSimpleStringT::-Empty](#isempty)|Testuje, zda objekt `CSimpleStringT` neobsahuje žádné znaky.|
|[CSimpleStringT::LockBuffer](#lockbuffer)|Zakáže počítání odkazů a chrání řetězec ve vyrovnávací paměti.|
|[CSimpleStringT::P znovu přidělit](#preallocate)|Přidělí konkrétní velikost paměti pro vyrovnávací paměť znaků.|
|[CSimpleStringT::ReleaseBuffer](#releasebuffer)|Uvolní kontrolu vyrovnávací paměti vrácené `GetBuffer`.|
|[CSimpleStringT::ReleaseBufferSetLength](#releasebuffersetlength)|Uvolní kontrolu vyrovnávací paměti vrácené `GetBuffer`.|
|[CSimpleStringT::SetAt](#setat)|Nastaví znak na dané pozici.|
|[CSimpleStringT::SetManager](#setmanager)|Nastaví správce paměti objektu `CSimpleStringT`.|
|[CSimpleStringT:: SetString](#setstring)|Nastaví řetězec objektu `CSimpleStringT`.|
|[CSimpleStringT::StringLength](#stringlength)|Vrátí počet znaků v zadaném řetězci.|
|[CSimpleStringT:: zkrátit](#truncate)|Zkrátí řetězec na zadanou délku.|
|[CSimpleStringT::UnlockBuffer](#unlockbuffer)|Povoluje počítání odkazů a uvolňuje řetězec ve vyrovnávací paměti.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CSimpleStringT:: operator PCXSTR](#operator_pcxstr)|Přímo přistupuje ke znakům uloženým v objektu `CSimpleStringT` jako řetězec ve stylu jazyka C.|
|[CSimpleStringT:: operator\[\]](#operator_at)|Vrátí znak na dané pozici – nahrazení operátoru pro `GetAt`.|
|[CSimpleStringT:: operator + =](#operator_add_eq)|Zřetězí nový řetězec na konec existujícího řetězce.|
|[CSimpleStringT:: operator =](#operator_eq)|Přiřadí novou hodnotu objektu `CSimpleStringT`.|

### <a name="remarks"></a>Poznámky

`CSimpleStringT` je základní třídou pro různé řetězcové třídy podporované jazykem Visual C++. Poskytuje minimální podporu pro správu paměti objektu String a základní manipulaci s vyrovnávací pamětí. Další informace o rozšířených objektech řetězců naleznete v tématu [Třída CStringT](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlsimpstr. h

## <a name="append"></a>CSimpleStringT:: Append

Připojí objekt `CSimpleStringT` k existujícímu objektu `CSimpleStringT`.

### <a name="syntax"></a>Syntaxe

```
void Append(const CSimpleStringT& strSrc);
void Append(PCXSTR pszSrc, int nLength);
void Append(PCXSTR pszSrc);
```

#### <a name="parameters"></a>Parametry

*strSrc*<br/>
Objekt `CSimpleStringT`, který se má připojit.

*pszSrc*<br/>
Ukazatel na řetězec obsahující znaky, které mají být připojeny.

*nLength*<br/>
Počet znaků, které se mají připojit.

### <a name="remarks"></a>Poznámky

Voláním této metody připojíte existující objekt `CSimpleStringT` k jinému objektu `CSimpleStringT`.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::Append`.

```cpp
CSimpleString str1(pMgr), str2(pMgr);
str1.SetString(_T("Soccer is"));
str2.SetString(_T(" an elegant game"));
str1.Append(str2);
ASSERT(_tcscmp(str1, _T("Soccer is an elegant game")) == 0);
```

##  <a name="appendchar"></a>CSimpleStringT::AppendChar

Připojí znak k existujícímu objektu `CSimpleStringT`.

### <a name="syntax"></a>Syntaxe

```
void AppendChar(XCHAR ch);
```

#### <a name="parameters"></a>Parametry

*Zvolte*<br/>
Znak, který se má připojit

### <a name="remarks"></a>Poznámky

Voláním této funkce připojíte zadaný znak ke konci existujícího objektu `CSimpleStringT`.

##  <a name="copychars"></a>CSimpleStringT::CopyChars

Zkopíruje znak nebo znaky do objektu `CSimpleStringT`.

### <a name="syntax"></a>Syntaxe

```
static void CopyChars(
    XCHAR* pchDest,
    const XCHAR* pchSrc,
    int nChars) throw();
```

#### <a name="parameters"></a>Parametry

*pchDest*<br/>
Ukazatel na řetězec znaků.

*pchSrc*<br/>
Ukazatel na řetězec obsahující znaky, které mají být zkopírovány.

*nChar*<br/>
Počet *pchSrc* znaků, které se mají zkopírovat

### <a name="remarks"></a>Poznámky

Voláním této metody zkopírujte znaky z *pchSrc* do řetězce *pchDest* .

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::CopyChars`.

```cpp
CSimpleString str(_T("xxxxxxxxxxxxxxxxxxx"), 20, pMgr);
TCHAR* pszSrc = _T("Hello world!");
_tprintf_s(_T("%s\n"), str);
str.CopyChars(str.GetBuffer(), pszSrc, 12);
_tprintf_s(_T("%s\n"), str);
```

##  <a name="copycharsoverlapped"></a>CSimpleStringT::CopyCharsOverlapped

Zkopíruje znak nebo znaky do objektu `CSimpleStringT`.

### <a name="syntax"></a>Syntaxe

```
static void CopyCharsOverlapped(
    XCHAR* pchDest,
    const XCHAR* pchSrc,
    int nChars) throw();
```

#### <a name="parameters"></a>Parametry

*pchDest*<br/>
Ukazatel na řetězec znaků.

*pchSrc*<br/>
Ukazatel na řetězec obsahující znaky, které mají být zkopírovány.

*nChar*<br/>
Počet *pchSrc* znaků, které se mají zkopírovat

### <a name="remarks"></a>Poznámky

Voláním této metody zkopírujte znaky z *pchSrc* do řetězce *pchDest* . Na rozdíl od `CopyChars``CopyCharsOverlapped` poskytuje bezpečnou metodu kopírování ze znakových vyrovnávacích pamětí, které mohou být překryty.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CSimpleStringT:: CopyChars](#copychars)nebo zdrojový kód pro `CSimpleStringT::SetString` (nachází se v atlsimpstr. h).

##  <a name="ctor"></a>CSimpleStringT::CSimpleStringT

Vytvoří objekt `CSimpleStringT`.

### <a name="syntax"></a>Syntaxe

```
CSimpleStringT(const XCHAR* pchSrc, int nLength, IAtlStringMgr* pStringMgr);
CSimpleStringT(PCXSTR pszSrc, IAtlStringMgr* pStringMgr);
CSimpleStringT(const CSimpleStringT& strSrc);
explicit CSimpleStringT(IAtlStringMgr* pStringMgr) throw();
```

#### <a name="parameters"></a>Parametry

*strSrc*<br/>
Existující objekt `CSimpleStringT`, který se má zkopírovat do tohoto objektu `CSimpleStringT`

*pchSrc*<br/>
Ukazatel na pole znaků délky *nLength*, bez hodnoty null.

*pszSrc*<br/>
Řetězec zakončený hodnotou null bude zkopírován do tohoto objektu `CSimpleStringT`.

*nLength*<br/>
Počet znaků v `pch`.

*pStringMgr*<br/>
Ukazatel na správce paměti objektu `CSimpleStringT`. Další informace o správě `IAtlStringMgr` a paměti pro `CSimpleStringT`najdete v tématu [Správa paměti a CString](../memory-management-with-cstringt.md).

### <a name="remarks"></a>Poznámky

Vytvořte nový objekt `CSimpleStringT`. Vzhledem k tomu, že konstruktory kopírují vstupní data do nového přiděleného úložiště, může to mít za následek výjimky paměti.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::CSimpleStringT` pomocí `CSimpleString`**typedef** ATL. `CSimpleString` je běžně používaná specializace šablony třídy `CSimpleStringT`.

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

##  <a name="empty"></a>CSimpleStringT:: Empty

Nastaví objekt `CSimpleStringT` prázdný řetězec a uvolní paměť podle potřeby.

### <a name="syntax"></a>Syntaxe

```
void Empty() throw();
```

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [řetězce: CString Exception Cleanup](../cstring-exception-cleanup.md).

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::Empty`.

```cpp
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```

##  <a name="freeextra"></a>CSimpleStringT::FreeExtra

Uvolní všechny nadbytečné paměti dříve přidělené řetězcem, ale už se nepotřebují.

### <a name="syntax"></a>Syntaxe

```
void FreeExtra();
```

### <a name="remarks"></a>Poznámky

To by mělo snížit nároky na paměť spotřebující objektem řetězce. Metoda znovu přidělí vyrovnávací paměť na přesnou délku vrácenou funkcí [GetLength](#getlength).

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

##  <a name="getalloclength"></a>CSimpleStringT::GetAllocLength

Načte přidělenou délku objektu `CSimpleStringT`.

### <a name="syntax"></a>Syntaxe

```
int GetAllocLength() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Počet znaků přidělených pro tento objekt.

### <a name="remarks"></a>Poznámky

Voláním této metody určíte počet znaků přidělených pro tento objekt `CSimpleStringT`. Příklad volání této funkce naleznete v tématu [FreeExtra](#freeextra) .

##  <a name="getat"></a>CSimpleStringT::GetAt

Vrátí jeden znak z objektu `CSimpleStringT`.

### <a name="syntax"></a>Syntaxe

```
XCHAR GetAt(int iChar) const;
```

#### <a name="parameters"></a>Parametry

*iChar*<br/>
Index založený na nule znaku v objektu `CSimpleStringT`. Parametr *ICHAR* musí být větší nebo roven 0 a menší než hodnota vrácená funkcí [GetLength](#getlength). V opačném případě `GetAt` vyvolá výjimku.

### <a name="return-value"></a>Návratová hodnota

`XCHAR`, který obsahuje znak na zadané pozici v řetězci.

### <a name="remarks"></a>Poznámky

Voláním této metody vrátíte jeden znak určený parametrem *ICHAR*. Přetížený operátor dolního indexu ( **[]** ) je vhodným aliasem pro `GetAt`. Ukončovací znak null je adresovatelný bez generování výjimky pomocí `GetAt`. Nepočítá se však podle `GetLength`a vrácená hodnota je 0.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít `CSimpleStringT::GetAt`.

```cpp
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(s.GetAt(2) == _T('c'));
```

##  <a name="getbuffer"></a>CSimpleStringT:: GetBuffer

Vrátí ukazatel na vnitřní vyrovnávací paměť znaků pro objekt `CSimpleStringT`.

### <a name="syntax"></a>Syntaxe

```
PXSTR GetBuffer(int nMinBufferLength);
PXSTR GetBuffer();
```

#### <a name="parameters"></a>Parametry

*nMinBufferLength*<br/>
Minimální počet znaků, které může uložit znaková vyrovnávací paměť. Tato hodnota nezahrnuje místo pro ukončovací znak null.

Pokud je *nMinBufferLength* větší než délka aktuální vyrovnávací paměti, `GetBuffer` zničí aktuální vyrovnávací paměť, nahradí ji vyrovnávací pamětí požadované velikosti a obnoví počet odkazů na objekt nula. Pokud jste v této vyrovnávací paměti dříve volali [LockBuffer](#lockbuffer) , ztratíte zámek vyrovnávací paměti.

### <a name="return-value"></a>Návratová hodnota

`PXSTR` ukazatel na vyrovnávací paměť znaku zakončeného hodnotou null.

### <a name="remarks"></a>Poznámky

Voláním této metody vrátíte obsah vyrovnávací paměti objektu `CSimpleStringT`. Vrácený `PXSTR` není konstanta, takže umožňuje přímou úpravu `CSimpleStringT` obsahu.

Použijete-li ukazatel vrácený `GetBuffer` ke změně obsahu řetězce, je nutné volat [ReleaseBuffer](#releasebuffer) před použitím jakýchkoli jiných metod členů `CSimpleStringT`.

Adresa vrácená `GetBuffer` nemusí být po volání `ReleaseBuffer` platná, protože další `CSimpleStringT` operace mohou způsobit opětovné přidělení `CSimpleStringT` vyrovnávací paměti. Pokud neměníte délku `CSimpleStringT`, vyrovnávací paměť se znovu nepřiřazuje.

Paměť vyrovnávací paměti je automaticky uvolněna při zničení objektu `CSimpleStringT`.

Pokud sledujete délku řetězce sami, neměli byste připojit ukončovací znak null. Při uvolnění vyrovnávací paměti pomocí `ReleaseBuffer`je však nutné zadat konečnou délku řetězce. Pokud připojíte ukončující znak null, měli byste pro tuto délku předat-1 (výchozí). `ReleaseBuffer` pak určí délku vyrovnávací paměti.

Pokud není k dispozici dostatek paměti pro splnění požadavku `GetBuffer`, tato metoda vyvolá výjimku CMemoryException *.

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

##  <a name="getbuffersetlength"></a>CSimpleStringT::GetBufferSetLength

Vrací ukazatel na vnitřní vyrovnávací paměť znaků pro objekt `CSimpleStringT`, zkracování nebo zvětšování délky, pokud je to nutné, aby přesně odpovídala délce zadané v *nLength*.

### <a name="syntax"></a>Syntaxe

```
PXSTR GetBufferSetLength(int nLength);
```

#### <a name="parameters"></a>Parametry

*nLength*<br/>
Přesná velikost vyrovnávací paměti pro `CSimpleStringT` znaků.

### <a name="return-value"></a>Návratová hodnota

`PXSTR` ukazatel na vyrovnávací paměť znaku zakončeného hodnotou null.

### <a name="remarks"></a>Poznámky

Voláním této metody načtete zadanou délku vnitřní vyrovnávací paměti objektu `CSimpleStringT`. Vrácený ukazatel `PXSTR` není **const** , takže umožňuje přímou úpravu `CSimpleStringT` obsahu.

Použijete-li ukazatel vrácený funkcí [GetBufferSetLength](#getbuffersetlength) ke změně obsahu řetězce, zavolejte `ReleaseBuffer` a aktualizujte tak vnitřní stav `CsimpleStringT` předtím, než použijete jiné `CSimpleStringT` metody.

Adresa vrácená `GetBufferSetLength` nemusí být po volání `ReleaseBuffer` platná, protože další `CSimpleStringT` operace mohou způsobit opětovné přidělení `CSimpleStringT` vyrovnávací paměti. Pokud neměníte délku `CSimpleStringT`, vyrovnávací paměť se znovu nepřiřazuje.

Paměť vyrovnávací paměti je automaticky uvolněna při zničení objektu `CSimpleStringT`.

Pokud sledujete délku řetězce sami, nepřipojujte ukončující znak null. Konečnou délku řetězce je nutné zadat při uvolnění vyrovnávací paměti pomocí `ReleaseBuffer`. Pokud připojíte ukončující znak null při volání `ReleaseBuffer`, Pass-1 (výchozí) pro délku `ReleaseBuffer`a `ReleaseBuffer` provede `strlen` ve vyrovnávací paměti za účelem určení jeho délky.

Další informace o počítání odkazů najdete v následujících článcích:

- [Správa životnosti objektů prostřednictvím počítání odkazů](/windows/win32/com/managing-object-lifetimes-through-reference-counting) v Windows SDK.

- [Implementace počítání odkazů](/windows/win32/com/implementing-reference-counting) v Windows SDK.

- [Pravidla pro správu počtů odkazů](/windows/win32/com/rules-for-managing-reference-counts) v Windows SDK.

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

##  <a name="getlength"></a>CSimpleStringT:: GetLength

Vrátí počet znaků v objektu `CSimpleStringT`.

### <a name="syntax"></a>Syntaxe

```
int GetLength() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Počet znaků v řetězci.

### <a name="remarks"></a>Poznámky

Voláním této metody vrátíte počet znaků v objektu. Počet nezahrnuje ukončovací znak null.

U vícebajtových znakových sad (MBCS) `GetLength` počítá každý 8bitový znak; To znamená, že vedoucí a koncový bajt v jednom vícebajtovém znaku se počítají jako dva bajty. Příklad volání této funkce naleznete v tématu [FreeExtra](#freeextra) .

##  <a name="getmanager"></a>CSimpleStringT:: GetManager

Načte správce paměti objektu `CSimpleStringT`.

### <a name="syntax"></a>Syntaxe

```
IAtlStringMgr* GetManager() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na správce paměti pro objekt `CSimpleStringT`.

### <a name="remarks"></a>Poznámky

Voláním této metody načtete správce paměti používaný objektem `CSimpleStringT`. Další informace o správcích paměti a objektech řetězců najdete v tématu [Správa paměti a CString](../memory-management-with-cstringt.md).

##  <a name="getstring"></a>CSimpleStringT:: GetString

Načte řetězec znaků.

### <a name="syntax"></a>Syntaxe

```
PCXSTR GetString() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na řetězec znaků zakončený hodnotou null.

### <a name="remarks"></a>Poznámky

Voláním této metody načtete řetězec znaků přidružený k objektu `CSimpleStringT`.

> [!NOTE]
>  Vrácený ukazatel `PCXSTR` je **const** a neumožňuje přímou úpravu obsahu `CSimpleStringT`.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::GetString`.

```cpp
CSimpleString str(pMgr);
str += _T("Cup soccer is best!");
_tprintf_s(_T("%s"), str.GetString());
```

##  <a name="isempty"></a>CSimpleStringT::-Empty

Testuje objekt `CSimpleStringT` pro prázdnou podmínku.

### <a name="syntax"></a>Syntaxe

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud má objekt `CSimpleStringT` 0 délky; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Voláním této metody určíte, zda objekt obsahuje prázdný řetězec.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::IsEmpty`.

```cpp
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```

##  <a name="lockbuffer"></a>CSimpleStringT::LockBuffer

Zakáže počítání odkazů a chrání řetězec ve vyrovnávací paměti.

### <a name="syntax"></a>Syntaxe

```
PXSTR LockBuffer();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt `CSimpleStringT` nebo řetězec zakončený hodnotou null.

### <a name="remarks"></a>Poznámky

Voláním této metody zamknete vyrovnávací paměť objektu `CSimpleStringT`. Voláním `LockBuffer`vytvoříte kopii řetězce s-1 pro počet odkazů. Pokud je hodnota počtu odkazů-1, řetězec ve vyrovnávací paměti je považován za uzamčený stav. V uzamčeném stavu je řetězec chráněn dvěma způsoby:

- Žádný jiný řetězec nemůže získat odkaz na data v uzamčeném řetězci, a to i v případě, že je tento řetězec přiřazen k uzamknutému řetězci.

- Uzamčený řetězec nikdy neodkazuje na jiný řetězec, a to i v případě, že je tento jiný řetězec zkopírován do uzamčeného řetězce.

Uzamčením řetězce ve vyrovnávací paměti zajistíte, že exkluzivní blokování řetězce ve vyrovnávací paměti zůstane beze změny.

Po dokončení práce s `LockBuffer`zavolejte [UnlockBuffer](#unlockbuffer) pro resetování počtu odkazů na 1.

> [!NOTE]
>  Pokud voláte [GetBuffer](#getbuffer) na uzamčené vyrovnávací paměti a nastavíte parametr `GetBuffer` `nMinBufferLength` na hodnotu větší než délka aktuální vyrovnávací paměti, dojde ke ztrátě zámku vyrovnávací paměti. Takové volání `GetBuffer` zničí aktuální vyrovnávací paměť, nahradí ji vyrovnávací pamětí požadované velikosti a obnoví počet odkazů na nulu.

Další informace o počítání odkazů najdete v následujících článcích:

- [Správa životnosti objektů prostřednictvím počítání odkazů](/windows/win32/com/managing-object-lifetimes-through-reference-counting) v Windows SDK

- [Implementace počítání odkazů](/windows/win32/com/implementing-reference-counting) v Windows SDK

- [Pravidla pro správu počtů odkazů](/windows/win32/com/rules-for-managing-reference-counts) v Windows SDK

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

##  <a name="operator_at"></a>CSimpleStringT:: operator\[\]

Voláním této funkce získáte přístup k jednomu znaku pole znaků.

### <a name="syntax"></a>Syntaxe

```
XCHAR operator[](int iChar) const;
```

#### <a name="parameters"></a>Parametry

*iChar*<br/>
Index založený na nule znaku v řetězci.

### <a name="remarks"></a>Poznámky

Operátor přetíženého dolního indexu ( **[]** ) vrací jeden znak určený indexem založeným na nule v *ICHAR*. Tento operátor je pohodlný náhrada za členskou funkci [GetAt](#getat) .

> [!NOTE]
>  Pomocí operátoru dolního indexu ( **[]** ) lze získat hodnotu znaku v `CSimpleStringT`, ale nelze jej použít ke změně hodnoty znaku v `CSimpleStringT`.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::operator []`.

```cpp
CSimpleString s(_T("abc"), pMgr);
ASSERT(s[1] == _T('b'));
```

## <a name="operator_at"></a>CSimpleStringT:: operator \[\]

Voláním této funkce získáte přístup k jednomu znaku pole znaků.

### <a name="syntax"></a>Syntaxe

```
XCHAR operator[](int iChar) const;
```

### <a name="parameters"></a>Parametry

*iChar*<br/>
Index založený na nule znaku v řetězci.

### <a name="remarks"></a>Poznámky

Operátor přetíženého dolního indexu ( **[]** ) vrací jeden znak určený indexem založeným na nule v *ICHAR*. Tento operátor je pohodlný náhrada za členskou funkci [GetAt](#getat) .

> [!NOTE]
>  Pomocí operátoru dolního indexu ( **[]** ) lze získat hodnotu znaku v `CSimpleStringT`, ale nelze jej použít ke změně hodnoty znaku v `CSimpleStringT`.

##  <a name="operator_add_eq"></a>CSimpleStringT:: operator + =

Spojí nový řetězec nebo znak na konec stávajícího řetězce.

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
Ukazatel na řetězec zakončený hodnotou null.

*strSrc*<br/>
Ukazatel na existující objekt `CSimpleStringT`.

*Zvolte*<br/>
Znak, který má být přidán.

### <a name="remarks"></a>Poznámky

Operátor přijímá jiný objekt `CSimpleStringT` nebo znak. Všimněte si, že výjimky paměti mohou nastat vždy, když použijete tento operátor zřetězení, protože pro znaky přidané do tohoto objektu `CSimpleStringT` může být přiděleno nové úložiště.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::operator +=`.

```cpp
CSimpleString str(_T("abc"), pMgr);
ASSERT(_tcscmp((str += _T("def")), _T("abcdef")) == 0);
```

##  <a name="operator_eq"></a>CSimpleStringT:: operator =

Přiřadí novou hodnotu objektu `CSimpleStringT`.

### <a name="syntax"></a>Syntaxe

```
CSimpleStringT& operator =(PCXSTR pszSrc);
CSimpleStringT& operator =(const CSimpleStringT& strSrc);
```

#### <a name="parameters"></a>Parametry

*pszSrc*<br/>
Ukazatel na řetězec zakončený hodnotou null.

*strSrc*<br/>
Ukazatel na existující objekt `CSimpleStringT`.

### <a name="remarks"></a>Poznámky

Pokud je cílový řetězec (levá strana) již dostatečně velký pro ukládání nových dat, není provedeno žádné nové přidělení paměti. Všimněte si, že výjimky paměti mohou nastat vždy, když použijete operátor přiřazení, protože nové úložiště je často přiděleno pro uchování výsledné `CSimpleStringT` objektu.

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

##  <a name="operator_pcxstr"></a>CSimpleStringT:: operator PCXSTR

Přímo přistupuje ke znakům uloženým v objektu `CSimpleStringT` jako řetězec ve stylu jazyka C.

### <a name="syntax"></a>Syntaxe

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Znakový ukazatel na data řetězce.

### <a name="remarks"></a>Poznámky

Nejsou kopírovány žádné znaky; Vrátí se jenom ukazatel. Buďte opatrní s tímto operátorem. Změníte-li `CString` objekt poté, co jste získali ukazatel na znak, můžete způsobit přerozdělení paměti, která neověřuje ukazatel.

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

##  <a name="pcxstr"></a>CSimpleStringT::P CXSTR

Ukazatel na konstantní řetězec.

### <a name="syntax"></a>Syntaxe

```
typedef ChTraitsBase< BaseType >::PCXSTR PCXSTR;
```

##  <a name="preallocate"></a>CSimpleStringT::P znovu přidělit

Přidělí konkrétní velikost bajtů pro objekt `CSimpleStringT`.

### <a name="syntax"></a>Syntaxe

```
void Preallocate( int nLength);
```

#### <a name="parameters"></a>Parametry

*nLength*<br/>
Přesná velikost vyrovnávací paměti pro `CSimpleStringT` znaků.

### <a name="remarks"></a>Poznámky

Zavolejte tuto metodu pro přidělení konkrétní velikosti vyrovnávací paměti pro objekt `CSimpleStringT`.

`CSimpleStringT` generuje výjimku STATUS_NO_MEMORY, pokud není schopen přidělit prostor pro vyrovnávací paměť znaků. Ve výchozím nastavení jsou přidělení paměti prováděna funkcemi rozhraní WIN32 API `HeapAlloc` nebo `HeapReAlloc`.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::Preallocate`.

```cpp
CSimpleString str(pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
str.Preallocate(100);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
```

##  <a name="pxstr"></a>CSimpleStringT::P XSTR

Ukazatel na řetězec.

### <a name="syntax"></a>Syntaxe

```
typedef ChTraitsBase< BaseType >::PXSTR PXSTR;
```

##  <a name="releasebuffer"></a>CSimpleStringT::ReleaseBuffer

Uvolní kontrolu vyrovnávací paměti přidělené [Getbufferem](#getbuffer).

### <a name="syntax"></a>Syntaxe

```
void ReleaseBuffer(int nNewLength = -1);
```

#### <a name="parameters"></a>Parametry

*nNewLength*<br/>
Nová délka řetězce ve znacích, která nepočítá ukončovací znak null. Pokud je řetězec ukončen hodnotou null, výchozí hodnota-1 nastaví velikost `CSimpleStringT` na aktuální délku řetězce.

### <a name="remarks"></a>Poznámky

Zavolejte tuto metodu pro opětovné přidělení nebo uvolnění vyrovnávací paměti objektu String. Pokud víte, že řetězec ve vyrovnávací paměti má ukončenou hodnotu null, můžete vynechat argument *nNewLength* . Pokud váš řetězec není ukončený hodnotou null, zadejte jeho délku pomocí *nNewLength* . Adresa vrácená funkcí [GetBuffer](#getbuffer) je po volání `ReleaseBuffer` nebo jakékoli jiné operace `CSimpleStringT` neplatná.

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

##  <a name="releasebuffersetlength"></a>CSimpleStringT::ReleaseBufferSetLength

Uvolní kontrolu vyrovnávací paměti přidělené [Getbufferem](#getbuffer).

### <a name="syntax"></a>Syntaxe

```
void ReleaseBufferSetLength(int nNewLength);
```

#### <a name="parameters"></a>Parametry

*nNewLength*<br/>
Délka vydávaného řetězce

### <a name="remarks"></a>Poznámky

Tato funkce je funkčně podobná [ReleaseBuffer](#releasebuffer) s tím rozdílem, že musí být předána platná délka řetězcového objektu.

##  <a name="setat"></a>CSimpleStringT::SetAt

Nastaví jeden znak z objektu `CSimpleStringT`.

### <a name="syntax"></a>Syntaxe

```
void SetAt(int iChar, XCHAR ch);
```

#### <a name="parameters"></a>Parametry

*iChar*<br/>
Index založený na nule znaku v objektu `CSimpleStringT`. Parametr *ICHAR* musí být větší nebo roven 0 a menší než hodnota vrácená funkcí [GetLength](#getlength).

*Zvolte*<br/>
Nový znak.

### <a name="remarks"></a>Poznámky

Voláním této metody můžete přepsat znak umístěný v *ICHAR*. Tato metoda nezvětšuje řetězec, pokud *ICHAR* překročí hranice stávajícího řetězce.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::SetAt`.

```cpp
CSimpleString s(_T("abcdef"), pMgr);
s.SetAt(1, _T('a'));
ASSERT(_tcscmp(s, _T("aacdef")) == 0);
```

##  <a name="setmanager"></a>CSimpleStringT::SetManager

Určuje správce paměti objektu `CSimpleStringT`.

### <a name="syntax"></a>Syntaxe

```
void SetManager(IAtlStringMgr* pStringMgr);
```

#### <a name="parameters"></a>Parametry

*pStringMgr*<br/>
Ukazatel na nového správce paměti.

### <a name="remarks"></a>Poznámky

Zavolejte tuto metodu pro určení nového správce paměti používaného objektem `CSimpleStringT`. Další informace o správcích paměti a objektech řetězců najdete v tématu [Správa paměti a CString](../memory-management-with-cstringt.md).

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::SetManager`.

```cpp
CSimpleString s(pMgr);
s.SetManager(pCustomMgr);
```

##  <a name="setstring"></a>CSimpleStringT:: SetString

Nastaví řetězec objektu `CSimpleStringT`.

### <a name="syntax"></a>Syntaxe

```
void SetString(PCXSTR pszSrc, int nLength);
void SetString(PCXSTR pszSrc);
```

#### <a name="parameters"></a>Parametry

*pszSrc*<br/>
Ukazatel na řetězec zakončený hodnotou null.

*nLength*<br/>
Počet znaků v *pszSrc*.

### <a name="remarks"></a>Poznámky

Zkopírujte řetězec do objektu `CSimpleStringT`. `SetString` přepíše data staršího řetězce ve vyrovnávací paměti.

Obě verze `SetString` zkontrolují, zda je *pszSrc* ukazatel s hodnotou null, a pokud je, vyvolejte chybu E_INVALIDARG.

Verze `SetString` s jedním parametrem očekává, že *pszSrc* odkazuje na řetězec zakončený hodnotou null.

Verze dvou parametrů `SetString` také očekává, že *pszSrc* je řetězec zakončený hodnotou null. Používá *nLength* jako délku řetězce, pokud nenalezne ukončovací znak null jako první.

Verze dvou parametrů `SetString` také kontroluje, zda *pszSrc* odkazuje na umístění v aktuální vyrovnávací paměti v `CSimpleStringT`. V tomto zvláštním případě `SetString` používá funkci kopírování paměti, která nepřepisuje data řetězce, protože kopíruje data řetězců zpátky do její vyrovnávací paměti.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::SetString`.

```cpp
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(_tcscmp(s, _T("abcdef")) == 0);
s.SetString(_T("Soccer"), 6);
ASSERT(_tcscmp(s, _T("Soccer")) == 0);
```

##  <a name="stringlength"></a>CSimpleStringT::StringLength

Vrátí počet znaků v zadaném řetězci.

### <a name="syntax"></a>Syntaxe

```
ATL_NOINLINE static int StringLength(PCXSTR psz) throw();
```

#### <a name="parameters"></a>Parametry

*psz*<br/>
Ukazatel na řetězec zakončený hodnotou null.

### <a name="return-value"></a>Návratová hodnota

Počet znaků v *PSZ*; nepočítá ukončovací znak null.

### <a name="remarks"></a>Poznámky

Voláním této metody načtete počet znaků v řetězci, na které ukazuje *PSZ*.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::StringLength`.

```cpp
ASSERT(CSimpleString::StringLength(_T("soccer")) == 6);
```

##  <a name="truncate"></a>CSimpleStringT:: zkrátit

Zkrátí řetězec na novou délku.

### <a name="syntax"></a>Syntaxe

```
void Truncate(int nNewLength);
```

#### <a name="parameters"></a>Parametry

*nNewLength*<br/>
Nová délka řetězce.

### <a name="remarks"></a>Poznámky

Zavolejte tuto metodu, chcete-li zkrátit obsah řetězce na novou délku.

> [!NOTE]
>  Tato akce nemá vliv na přidělenou délku vyrovnávací paměti. Chcete-li snížit nebo zvýšit aktuální vyrovnávací paměť, přečtěte si téma [FreeExtra](#freeextra) a [předalokace](#preallocate).

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

##  <a name="unlockbuffer"></a>CSimpleStringT::UnlockBuffer

Odemkne vyrovnávací paměť objektu `CSimpleStringT`.

### <a name="syntax"></a>Syntaxe

```
void UnlockBuffer() throw();
```

### <a name="remarks"></a>Poznámky

Voláním této metody resetujete počet odkazů řetězce na 1.

Destruktor `CSimpleStringT` automaticky volá `UnlockBuffer`, aby se zajistilo, že při volání destruktoru není vyrovnávací paměť uzamčena. Příklad této metody naleznete v tématu [LockBuffer](#lockbuffer).

##  <a name="dtor"></a>CSimpleStringT:: ~ CSimpleStringT

Odstraní objekt `CSimpleStringT`.

### <a name="syntax"></a>Syntaxe

```
~CSimpleStringT() throw();
```

### <a name="remarks"></a>Poznámky

Chcete-li zničit objekt `CSimpleStringT`, zavolejte tuto metodu.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Sdílené třídy ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
