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
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491449"
---
# <a name="csimplestringt-class"></a>CSimpleStringT – třída

Tato třída reprezentuje `CSimpleStringT` objekt.

## <a name="syntax"></a>Syntaxe

```
template <typename BaseType>
class CSimpleStringT
```

### <a name="parameters"></a>Parametry

*BaseType*<br/>
Typ znaku řetězcové třídy. Může být jedna z následujících akcí:

- **znak** (pro řetězce znaků ANSI).

- **wchar_t** (pro řetězce znaků Unicode).

- TCHAR (pro řetězce znaků ANSI a Unicode).

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Name|Popis|
|----------|-----------------|
|[CSimpleStringT::P CXSTR](#pcxstr)|Ukazatel na konstantní řetězec.|
|[CSimpleStringT::P XSTR](#pxstr)|Ukazatel na řetězec.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CSimpleStringT::CSimpleStringT](#ctor)|Sestaví `CSimpleStringT` objekty různými způsoby.|
|[CSimpleStringT::~CSimpleStringT](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CSimpleStringT:: Append](#append)|Připojí objekt k existujícímu `CSimpleStringT`objektu. `CSimpleStringT`|
|[CSimpleStringT::AppendChar](#appendchar)|Připojí znak k existujícímu `CSimpleStringT` objektu.|
|[CSimpleStringT::CopyChars](#copychars)|Zkopíruje znak nebo znaky do jiného řetězce.|
|[CSimpleStringT::CopyCharsOverlapped](#copycharsoverlapped)|Zkopíruje znak nebo znaky do jiného řetězce, ve kterém se překrývají vyrovnávací paměti.|
|[CSimpleStringT:: Empty](#empty)|Vynutí, aby měl řetězec nulovou délku.|
|[CSimpleStringT::FreeExtra](#freeextra)|Uvolní všechny nadbytečné paměti dříve přidělené objektem řetězce.|
|[CSimpleStringT::GetAllocLength](#getalloclength)|Načte přidělenou délku `CSimpleStringT` objektu.|
|[CSimpleStringT::GetAt](#getat)|Vrátí znak na dané pozici.|
|[CSimpleStringT::GetBuffer](#getbuffer)|Vrátí ukazatel na znaky v `CSimpleStringT`.|
|[CSimpleStringT::GetBufferSetLength](#getbuffersetlength)|Vrátí ukazatel na znaky v a `CSimpleStringT`zkrácení na zadanou délku.|
|[CSimpleStringT:: GetLength](#getlength)|Vrátí počet znaků v `CSimpleStringT` objektu.|
|[CSimpleStringT::GetManager](#getmanager)|Načte správce `CSimpleStringT` paměti objektu.|
|[CSimpleStringT:: GetString](#getstring)|Načte řetězec znaků.|
|[CSimpleStringT::IsEmpty](#isempty)|Testuje, zda `CSimpleStringT` objekt neobsahuje žádné znaky.|
|[CSimpleStringT::LockBuffer](#lockbuffer)|Zakáže počítání odkazů a chrání řetězec ve vyrovnávací paměti.|
|[CSimpleStringT::P znovu přidělit](#preallocate)|Přidělí konkrétní velikost paměti pro vyrovnávací paměť znaků.|
|[CSimpleStringT::ReleaseBuffer](#releasebuffer)|Uvolňuje kontrolu nad vyrovnávací pamětí `GetBuffer`vrácenou.|
|[CSimpleStringT::ReleaseBufferSetLength](#releasebuffersetlength)|Uvolňuje kontrolu nad vyrovnávací pamětí `GetBuffer`vrácenou.|
|[CSimpleStringT::SetAt](#setat)|Nastaví znak na dané pozici.|
|[CSimpleStringT::SetManager](#setmanager)|Nastaví správce `CSimpleStringT` paměti objektu.|
|[CSimpleStringT:: SetString](#setstring)|Nastaví řetězec `CSimpleStringT` objektu.|
|[CSimpleStringT::StringLength](#stringlength)|Vrátí počet znaků v zadaném řetězci.|
|[CSimpleStringT:: zkrátit](#truncate)|Zkrátí řetězec na zadanou délku.|
|[CSimpleStringT::UnlockBuffer](#unlockbuffer)|Povoluje počítání odkazů a uvolňuje řetězec ve vyrovnávací paměti.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CSimpleStringT:: operator PCXSTR](#operator_pcxstr)|Přímo přistupuje ke znakům uloženým `CSimpleStringT` v objektu jako řetězec ve stylu jazyka C.|
|[CSimpleStringT:: operator\[\]](#operator_at)|Vrátí znak na dané pozici – nahrazení operátoru pro `GetAt`.|
|[CSimpleStringT:: operator + =](#operator_add_eq)|Zřetězí nový řetězec na konec existujícího řetězce.|
|[CSimpleStringT:: operator =](#operator_eq)|Přiřadí novou hodnotu `CSimpleStringT` objektu.|

### <a name="remarks"></a>Poznámky

`CSimpleStringT`je základní třídou pro různé třídy řetězců podporované jazykem Visual C++. Poskytuje minimální podporu pro správu paměti objektu String a základní manipulaci s vyrovnávací pamětí. Další informace o rozšířených objektech řetězců naleznete v tématu [Třída CStringT](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlsimpstr. h

## <a name="append"></a>CSimpleStringT:: Append

Připojí objekt k existujícímu `CSimpleStringT`objektu. `CSimpleStringT`

### <a name="syntax"></a>Syntaxe

```
void Append(const CSimpleStringT& strSrc);
void Append(PCXSTR pszSrc, int nLength);
void Append(PCXSTR pszSrc);
```

#### <a name="parameters"></a>Parametry

*strSrc*<br/>
`CSimpleStringT` Objekt, který má být přidán.

*pszSrc*<br/>
Ukazatel na řetězec obsahující znaky, které mají být připojeny.

*nLength*<br/>
Počet znaků, které se mají připojit.

### <a name="remarks"></a>Poznámky

Voláním této metody připojíte existující `CSimpleStringT` objekt k jinému `CSimpleStringT` objektu.

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

Připojí znak k existujícímu `CSimpleStringT` objektu.

### <a name="syntax"></a>Syntaxe

```
void AppendChar(XCHAR ch);
```

#### <a name="parameters"></a>Parametry

*ch*<br/>
Znak, který se má připojit

### <a name="remarks"></a>Poznámky

Voláním této funkce připojíte zadaný znak ke konci existujícího `CSimpleStringT` objektu.

##  <a name="copychars"></a>CSimpleStringT::CopyChars

Zkopíruje znak nebo znaky do `CSimpleStringT` objektu.

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

Zkopíruje znak nebo znaky do `CSimpleStringT` objektu.

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

Voláním této metody zkopírujte znaky z *pchSrc* do řetězce *pchDest* . Na rozdíl `CopyChars`od `CopyCharsOverlapped` , poskytuje bezpečnou metodu kopírování ze znakových vyrovnávacích pamětí, které mohou být překryty.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CSimpleStringT:: CopyChars](#copychars)nebo zdrojový kód pro `CSimpleStringT::SetString` (umístěný v atlsimpstr. h).

##  <a name="ctor"></a>CSimpleStringT::CSimpleStringT

`CSimpleStringT` Vytvoří objekt.

### <a name="syntax"></a>Syntaxe

```
CSimpleStringT(const XCHAR* pchSrc, int nLength, IAtlStringMgr* pStringMgr);
CSimpleStringT(PCXSTR pszSrc, IAtlStringMgr* pStringMgr);
CSimpleStringT(const CSimpleStringT& strSrc);
explicit CSimpleStringT(IAtlStringMgr* pStringMgr) throw();
```

#### <a name="parameters"></a>Parametry

*strSrc*<br/>
Existující `CSimpleStringT` objekt, který má být zkopírován do `CSimpleStringT` tohoto objektu.

*pchSrc*<br/>
Ukazatel na pole znaků délky *nLength*, bez hodnoty null.

*pszSrc*<br/>
Řetězec zakončený hodnotou null, který má být zkopírován `CSimpleStringT` do tohoto objektu.

*nLength*<br/>
Počet znaků v `pch`.

*pStringMgr*<br/>
Ukazatel na správce `CSimpleStringT` paměti objektu. Další informace o `IAtlStringMgr` správě paměti pro `CSimpleStringT`najdete v tématu [Správa paměti a CString](../memory-management-with-cstringt.md).

### <a name="remarks"></a>Poznámky

Vytvořte nový `CSimpleStringT` objekt. Vzhledem k tomu, že konstruktory kopírují vstupní data do nového přiděleného úložiště, může to mít za následek výjimky paměti.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::CSimpleStringT` pomocí **definice typedef** `CSimpleString`ATL. `CSimpleString`je běžně používaná specializace šablony `CSimpleStringT`třídy.

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

Nastaví tento `CSimpleStringT` objekt prázdný řetězec a uvolní paměť v případě potřeby.

### <a name="syntax"></a>Syntaxe

```
void Empty() throw();
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [řetězce: Vymazání](../cstring-exception-cleanup.md)výjimky CString

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

Načte přidělenou délku `CSimpleStringT` objektu.

### <a name="syntax"></a>Syntaxe

```
int GetAllocLength() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Počet znaků přidělených pro tento objekt.

### <a name="remarks"></a>Poznámky

Voláním této metody určíte počet znaků přidělených pro tento `CSimpleStringT` objekt. Příklad volání této funkce naleznete v tématu [FreeExtra](#freeextra) .

##  <a name="getat"></a>CSimpleStringT::GetAt

Vrátí jeden znak z `CSimpleStringT` objektu.

### <a name="syntax"></a>Syntaxe

```
XCHAR GetAt(int iChar) const;
```

#### <a name="parameters"></a>Parametry

*iChar*<br/>
Index založený na nule znaku v `CSimpleStringT` objektu. Parametr *ICHAR* musí být větší nebo roven 0 a menší než hodnota vrácená funkcí [GetLength](#getlength). V opačném případě bude vygenerována výjimka. `GetAt`

### <a name="return-value"></a>Návratová hodnota

Objekt `XCHAR` , který obsahuje znak na zadané pozici v řetězci.

### <a name="remarks"></a>Poznámky

Voláním této metody vrátíte jeden znak určený parametrem *ICHAR*. Přetížený operátor dolního indexu ( **[]** ) je vhodným aliasem pro `GetAt`. Ukončovací znak null je adresovatelný bez generování výjimky pomocí `GetAt`. Nepočítá se ale podle `GetLength`a vrácená hodnota je 0.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít `CSimpleStringT::GetAt`.

```cpp
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(s.GetAt(2) == _T('c'));
```

##  <a name="getbuffer"></a>CSimpleStringT:: GetBuffer

Vrátí ukazatel na vnitřní vyrovnávací paměť znaků pro `CSimpleStringT` objekt.

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

`PXSTR` Ukazatel na vyrovnávací paměť znaků objektu (se zakončením hodnoty null).

### <a name="remarks"></a>Poznámky

Voláním této metody vrátíte obsah `CSimpleStringT` vyrovnávací paměti objektu. Vrácený `PXSTR` není konstanta, takže umožňuje přímou `CSimpleStringT` úpravu obsahu.

Použijete `GetBuffer` -li ukazatel vrácený pro změnu obsahu řetězce, je nutné volat [ReleaseBuffer](#releasebuffer) před použitím jakýchkoli jiných `CSimpleStringT` metod členů.

Adresa vrácená funkcí `GetBuffer` pravděpodobně není platná po volání metody, `ReleaseBuffer` protože `CSimpleStringT` další `CSimpleStringT` operace mohou způsobit opětovné přidělení vyrovnávací paměti. Pokud neměníte délku `CSimpleStringT`, vyrovnávací paměť se znovu nepřiřazuje.

Paměť vyrovnávací paměti je automaticky uvolněna při `CSimpleStringT` zničení objektu.

Pokud sledujete délku řetězce sami, neměli byste připojit ukončovací znak null. Je však nutné zadat konečnou délku řetězce při uvolnění vyrovnávací paměti pomocí `ReleaseBuffer`. Pokud připojíte ukončující znak null, měli byste pro tuto délku předat-1 (výchozí). `ReleaseBuffer`pak určuje délku vyrovnávací paměti.

Pokud není dostatek paměti pro splnění `GetBuffer` požadavku, tato metoda vyvolá CMemoryException *.

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

Vrací ukazatel na vnitřní vyrovnávací paměť znaků pro `CSimpleStringT` objekt, zkrácení nebo zvětšování délky, pokud je to nutné, aby přesně odpovídala délce zadané v *nLength*.

### <a name="syntax"></a>Syntaxe

```
PXSTR GetBufferSetLength(int nLength);
```

#### <a name="parameters"></a>Parametry

*nLength*<br/>
Přesná velikost `CSimpleStringT` vyrovnávací paměti znaků v znacích.

### <a name="return-value"></a>Návratová hodnota

`PXSTR` Ukazatel na vyrovnávací paměť znaků objektu (se zakončením hodnoty null).

### <a name="remarks"></a>Poznámky

Voláním této metody načtete zadanou délku vnitřní vyrovnávací paměti `CSimpleStringT` objektu. Vrácený `PXSTR` ukazatel není const , takže `CSimpleStringT` umožňuje přímou úpravu obsahu.

Použijete-li ukazatel vrácený funkcí [GetBufferSetLength](#getbuffersetlength) ke změně obsahu řetězce, zavolejte `ReleaseBuffer` na aktualizovat vnitřní stav `CsimpleStringT` předtím, než použijete jiné `CSimpleStringT` metody.

Adresa vrácená funkcí `GetBufferSetLength` pravděpodobně není platná po volání metody, `ReleaseBuffer` protože `CSimpleStringT` další `CSimpleStringT` operace mohou způsobit opětovné přidělení vyrovnávací paměti. Pokud neměníte délku `CSimpleStringT`, vyrovnávací paměť se znovu nepřiřazuje.

Paměť vyrovnávací paměti je automaticky uvolněna při `CSimpleStringT` zničení objektu.

Pokud sledujete délku řetězce sami, nepřipojujte ukončující znak null. Konečnou délku řetězce je nutné zadat při uvolnění vyrovnávací paměti pomocí `ReleaseBuffer`. Pokud připojíte ukončující `ReleaseBuffer`znak null při volání, Pass-1 (výchozí) pro délku do `ReleaseBuffer`a `ReleaseBuffer` `strlen` provede ve vyrovnávací paměti pro určení jeho délky.

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

Vrátí počet znaků v `CSimpleStringT` objektu.

### <a name="syntax"></a>Syntaxe

```
int GetLength() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Počet znaků v řetězci.

### <a name="remarks"></a>Poznámky

Voláním této metody vrátíte počet znaků v objektu. Počet nezahrnuje ukončovací znak null.

U vícebajtových znakových sad (MBCS `GetLength` ) počítá každý 8bitový znak; to znamená, že vedoucí a koncový bajt v jednom vícebajtovém znaku se počítají jako dva bajty. Příklad volání této funkce naleznete v tématu [FreeExtra](#freeextra) .

##  <a name="getmanager"></a>CSimpleStringT:: GetManager

Načte správce `CSimpleStringT` paměti objektu.

### <a name="syntax"></a>Syntaxe

```
IAtlStringMgr* GetManager() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na správce paměti pro `CSimpleStringT` objekt.

### <a name="remarks"></a>Poznámky

Voláním této metody načtete správce paměti používaný `CSimpleStringT` objektem. Další informace o správcích paměti a objektech řetězců najdete v tématu [Správa paměti a CString](../memory-management-with-cstringt.md).

##  <a name="getstring"></a>CSimpleStringT:: GetString

Načte řetězec znaků.

### <a name="syntax"></a>Syntaxe

```
PCXSTR GetString() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na řetězec znaků zakončený hodnotou null.

### <a name="remarks"></a>Poznámky

Voláním této metody načtete řetězec znaků přidružený `CSimpleStringT` k objektu.

> [!NOTE]
>  Vrácený `PCXSTR` ukazatel je **const** a `CSimpleStringT` nepovoluje přímou úpravu obsahu.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::GetString`.

```cpp
CSimpleString str(pMgr);
str += _T("Cup soccer is best!");
_tprintf_s(_T("%s"), str.GetString());
```

##  <a name="isempty"></a>CSimpleStringT::-Empty

`CSimpleStringT` Testuje objekt pro prázdnou podmínku.

### <a name="syntax"></a>Syntaxe

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, `CSimpleStringT` Pokud má objekt nulovou délku; v opačném případě false.

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

Ukazatel na `CSimpleStringT` objekt nebo řetězec zakončený hodnotou null.

### <a name="remarks"></a>Poznámky

Voláním této metody zamknete vyrovnávací paměť `CSimpleStringT` objektu. Voláním `LockBuffer`vytvoříte kopii řetězce s-1 pro počet odkazů. Pokud je hodnota počtu odkazů-1, řetězec ve vyrovnávací paměti je považován za uzamčený stav. V uzamčeném stavu je řetězec chráněn dvěma způsoby:

- Žádný jiný řetězec nemůže získat odkaz na data v uzamčeném řetězci, a to i v případě, že je tento řetězec přiřazen k uzamknutému řetězci.

- Uzamčený řetězec nikdy neodkazuje na jiný řetězec, a to i v případě, že je tento jiný řetězec zkopírován do uzamčeného řetězce.

Uzamčením řetězce ve vyrovnávací paměti zajistíte, že exkluzivní blokování řetězce ve vyrovnávací paměti zůstane beze změny.

Po dokončení s `LockBuffer`voláním volejte [UnlockBuffer](#unlockbuffer) pro resetování počtu odkazů na 1.

> [!NOTE]
>  Pokud voláte GetBuffer na uzamčené vyrovnávací paměti a nastavíte [](#getbuffer) `GetBuffer` parametr `nMinBufferLength` tak, aby byl větší než délka aktuální vyrovnávací paměti, dojde ke ztrátě zámku vyrovnávací paměti. Takové volání `GetBuffer` zničí aktuální vyrovnávací paměť, nahradí je vyrovnávací pamětí požadované velikosti a obnoví počet odkazů na nulu.

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
>  Operátor dolního indexu ( **[]** ) můžete použít k získání hodnoty znaku v `CSimpleStringT`, ale nelze jej použít ke změně hodnoty znaku v. `CSimpleStringT`

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::operator []`.

```cpp
CSimpleString s(_T("abc"), pMgr);
ASSERT(s[1] == _T('b'));
```

## <a name="operator_at"></a>CSimpleStringT:: operator\[\]

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
>  Operátor dolního indexu ( **[]** ) můžete použít k získání hodnoty znaku v `CSimpleStringT`, ale nelze jej použít ke změně hodnoty znaku v. `CSimpleStringT`

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
Ukazatel na existující `CSimpleStringT` objekt.

*ch*<br/>
Znak, který má být přidán.

### <a name="remarks"></a>Poznámky

Operátor přijímá jiný `CSimpleStringT` objekt nebo znak. Všimněte si, že výjimky paměti mohou nastat vždy, když použijete tento operátor zřetězení, protože pro znaky přidané do tohoto `CSimpleStringT` objektu může být přiděleno nové úložiště.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::operator +=`.

```cpp
CSimpleString str(_T("abc"), pMgr);
ASSERT(_tcscmp((str += _T("def")), _T("abcdef")) == 0);
```

##  <a name="operator_eq"></a>CSimpleStringT:: operator =

Přiřadí novou hodnotu `CSimpleStringT` objektu.

### <a name="syntax"></a>Syntaxe

```
CSimpleStringT& operator =(PCXSTR pszSrc);
CSimpleStringT& operator =(const CSimpleStringT& strSrc);
```

#### <a name="parameters"></a>Parametry

*pszSrc*<br/>
Ukazatel na řetězec zakončený hodnotou null.

*strSrc*<br/>
Ukazatel na existující `CSimpleStringT` objekt.

### <a name="remarks"></a>Poznámky

Pokud je cílový řetězec (levá strana) již dostatečně velký pro ukládání nových dat, není provedeno žádné nové přidělení paměti. Všimněte si, že výjimky paměti mohou nastat vždy, když použijete operátor přiřazení, protože nové úložiště je často přiděleno pro uložení výsledného `CSimpleStringT` objektu.

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

Přímo přistupuje ke znakům uloženým `CSimpleStringT` v objektu jako řetězec ve stylu jazyka C.

### <a name="syntax"></a>Syntaxe

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Znakový ukazatel na data řetězce.

### <a name="remarks"></a>Poznámky

Nejsou kopírovány žádné znaky; Vrátí se jenom ukazatel. Buďte opatrní s tímto operátorem. Změníte- `CString` li objekt poté, co jste získali ukazatel na znak, můžete způsobit přerozdělení paměti, která neověřuje ukazatel.

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

Přidělí určité množství bajtů `CSimpleStringT` objektu.

### <a name="syntax"></a>Syntaxe

```
void Preallocate( int nLength);
```

#### <a name="parameters"></a>Parametry

*nLength*<br/>
Přesná velikost `CSimpleStringT` vyrovnávací paměti znaků v znacích.

### <a name="remarks"></a>Poznámky

Zavolejte tuto metodu pro přidělení konkrétní velikosti `CSimpleStringT` vyrovnávací paměti objektu.

`CSimpleStringT`generuje výjimku STATUS_NO_MEMORY, pokud není schopna přidělit prostor pro vyrovnávací paměť znaků. Ve výchozím nastavení se přidělování paměti provádí funkcemi `HeapAlloc` rozhraní Win32 API nebo. `HeapReAlloc`

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

Uvolní kontrolu vyrovnávací paměti přidělené getbufferem. [](#getbuffer)

### <a name="syntax"></a>Syntaxe

```
void ReleaseBuffer(int nNewLength = -1);
```

#### <a name="parameters"></a>Parametry

*nNewLength*<br/>
Nová délka řetězce ve znacích, která nepočítá ukončovací znak null. Pokud je řetězec ukončen hodnotou null, výchozí hodnota-1 nastaví `CSimpleStringT` velikost na aktuální délku řetězce.

### <a name="remarks"></a>Poznámky

Zavolejte tuto metodu pro opětovné přidělení nebo uvolnění vyrovnávací paměti objektu String. Pokud víte, že řetězec ve vyrovnávací paměti má ukončenou hodnotu null, můžete vynechat argument *nNewLength* . Pokud váš řetězec není ukončený hodnotou null, zadejte jeho délku pomocí *nNewLength* . Adresa vrácená funkcí GetBuffer je neplatná po volání [](#getbuffer) `ReleaseBuffer` nebo jakékoli jiné `CSimpleStringT` operaci.

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

Uvolní kontrolu vyrovnávací paměti přidělené getbufferem. [](#getbuffer)

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

Nastaví jeden znak z `CSimpleStringT` objektu.

### <a name="syntax"></a>Syntaxe

```
void SetAt(int iChar, XCHAR ch);
```

#### <a name="parameters"></a>Parametry

*iChar*<br/>
Index založený na nule znaku v `CSimpleStringT` objektu. Parametr *ICHAR* musí být větší nebo roven 0 a menší než hodnota vrácená funkcí [GetLength](#getlength).

*ch*<br/>
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

Určuje správce `CSimpleStringT` paměti objektu.

### <a name="syntax"></a>Syntaxe

```
void SetManager(IAtlStringMgr* pStringMgr);
```

#### <a name="parameters"></a>Parametry

*pStringMgr*<br/>
Ukazatel na nového správce paměti.

### <a name="remarks"></a>Poznámky

Zavolejte tuto metodu pro určení nového správce paměti používaného `CSimpleStringT` objektem. Další informace o správcích paměti a objektech řetězců najdete v tématu [Správa paměti a CString](../memory-management-with-cstringt.md).

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::SetManager`.

```cpp
CSimpleString s(pMgr);
s.SetManager(pCustomMgr);
```

##  <a name="setstring"></a>CSimpleStringT:: SetString

Nastaví řetězec `CSimpleStringT` objektu.

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

Zkopírujte řetězec do `CSimpleStringT` objektu. `SetString`přepíše data staršího řetězce ve vyrovnávací paměti.

Obě verze `SetString` kontrolují, zda je *pszSrc* ukazatel s hodnotou null, a pokud je, vyvolejte chybu E_INVALIDARG.

Verze `SetString` s jedním parametrem očekává, že *pszSrc* odkazuje na řetězec zakončený hodnotou null.

Verze `SetString` dvou parametrů také očekává, že *pszSrc* je řetězec zakončený hodnotou null. Používá *nLength* jako délku řetězce, pokud nenalezne ukončovací znak null jako první.

Verze `SetString` dvou parametrů také kontroluje, zda *pszSrc* odkazuje na umístění v aktuální vyrovnávací paměti v `CSimpleStringT`. V tomto speciálním případě `SetString` používá funkce kopírování paměti, která nepřepisuje řetězcová data při kopírování řetězcových dat zpět do její vyrovnávací paměti.

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
>  Tato akce nemá vliv na přidělenou délku vyrovnávací paměti. Chcete-li snížit nebo zvýšit aktuální vyrovnávací paměť, přečtěte si téma [FreeExtra](#freeextra) a předalokace. [](#preallocate)

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

Odemkne vyrovnávací paměť `CSimpleStringT` objektu.

### <a name="syntax"></a>Syntaxe

```
void UnlockBuffer() throw();
```

### <a name="remarks"></a>Poznámky

Voláním této metody resetujete počet odkazů řetězce na 1.

Destruktor automaticky volá `UnlockBuffer` , aby se zajistilo, že vyrovnávací paměť není uzamčena při volání destruktoru. `CSimpleStringT` Příklad této metody naleznete v tématu [LockBuffer](#lockbuffer).

##  <a name="dtor"></a>CSimpleStringT:: ~ CSimpleStringT

`CSimpleStringT` Odstraní objekt.

### <a name="syntax"></a>Syntaxe

```
~CSimpleStringT() throw();
```

### <a name="remarks"></a>Poznámky

Zavolejte tuto metodu pro zničení `CSimpleStringT` objektu.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Sdílené třídy ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
