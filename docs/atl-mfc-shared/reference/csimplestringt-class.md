---
title: Csimplestringt – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- shared classes, CSimpleStringT
- strings [C++], ATL class
- CSimpleStringT class
ms.assetid: 15814fcb-5b8f-4425-a97e-3b61fc9b48d8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 326fdd3d4d5e8f19408adc7300c97523b37d942e
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50078931"
---
# <a name="csimplestringt-class"></a>Csimplestringt – třída

Tato třída reprezentuje `CSimpleStringT` objektu.

## <a name="syntax"></a>Syntaxe

```
template <typename BaseType>
class CSimpleStringT
```

### <a name="parameters"></a>Parametry

*BaseType*<br/>
Znakový typ třída string. Může být jedna z následujících akcí:

- **Char** (pro řetězce znaků ANSI).

- **wchar_t** (pro řetězce znaků Unicode).

- TCHAR (pro řetězce znaků ANSI a Unicode).

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|[CSimpleStringT::PCXSTR](#pcxstr)|Ukazatel na konstanty typu řetězec.|
|[CSimpleStringT::PXSTR](#pxstr)|Ukazatel na řetězec.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CSimpleStringT::CSimpleStringT](#ctor)|Vytvoří `CSimpleStringT` objekty různými způsoby.|
|[Csimplestringt –:: ~ csimplestringt –](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CSimpleStringT::Append](#append)|Připojí `CSimpleStringT` objektu do existujícího `CSimpleStringT` objektu.|
|[CSimpleStringT::AppendChar](#appendchar)|Přidá znak do existujícího `CSimpleStringT` objektu.|
|[CSimpleStringT::CopyChars](#copychars)|Zkopíruje znak nebo znaky do jiného řetězce.|
|[CSimpleStringT::CopyCharsOverlapped](#copycharsoverlapped)|Zkopíruje znak nebo znaky do jiného řetězce, ve které se překrývají vyrovnávací paměti.|
|[CSimpleStringT::Empty](#empty)|Způsobí, že řetězec má nulovou délku.|
|[CSimpleStringT::FreeExtra](#freeextra)|Uvolní všechny další paměť přidělenou dříve metodou na objekt řetězce.|
|[CSimpleStringT::GetAllocLength](#getalloclength)|Načte přidělené délku `CSimpleStringT` objektu.|
|[CSimpleStringT::GetAt](#getat)|Vrátí znak na dané pozici.|
|[CSimpleStringT::GetBuffer](#getbuffer)|Vrací ukazatel na znaky v `CSimpleStringT`.|
|[CSimpleStringT::GetBufferSetLength](#getbuffersetlength)|Vrací ukazatel na znaky v `CSimpleStringT`, zkrátí se na zadanou délku.|
|[CSimpleStringT::GetLength](#getlength)|Vrátí počet znaků `CSimpleStringT` objektu.|
|[CSimpleStringT::GetManager](#getmanager)|Získá správce paměti `CSimpleStringT` objektu.|
|[CSimpleStringT::GetString](#getstring)|Načte řetězec znaků|
|[CSimpleStringT::IsEmpty](#isempty)|Testy, jestli `CSimpleStringT` objekt neobsahuje žádné znaky.|
|[CSimpleStringT::LockBuffer](#lockbuffer)|Zakáže počítání odkazů a chrání data řetězec ve vyrovnávací paměti.|
|[CSimpleStringT::Preallocate](#preallocate)|Určitou velikostí paměti přidělí vyrovnávací paměti pro znaky.|
|[CSimpleStringT::ReleaseBuffer](#releasebuffer)|Verze ovládacího prvku vyrovnávací paměti pro vrácený `GetBuffer`.|
|[CSimpleStringT::ReleaseBufferSetLength](#releasebuffersetlength)|Verze ovládacího prvku vyrovnávací paměti pro vrácený `GetBuffer`.|
|[CSimpleStringT::SetAt](#setat)|Nastaví znak na dané pozici.|
|[CSimpleStringT::SetManager](#setmanager)|Nastaví správce paměti `CSimpleStringT` objektu.|
|[CSimpleStringT::SetString](#setstring)|Nastaví řetězec `CSimpleStringT` objektu.|
|[CSimpleStringT::StringLength](#stringlength)|Vrátí počet znaků v zadaném řetězci.|
|[CSimpleStringT::Truncate](#truncate)|Zkrátí řetězec, který má zadané délky.|
|[CSimpleStringT::UnlockBuffer](#unlockbuffer)|Umožňuje počítání odkazů a uvolní řetězec ve vyrovnávací paměti.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CSimpleStringT::operator PCXSTR](#operator_pcxstr)|Přímý přístup k znaků uložených v `CSimpleStringT` objektu jako řetězec stylu C.|
|[CSimpleStringT::operator\[\]](#operator_at)|Vrátí znak na dané pozici – operátor nahrazení pro `GetAt`.|
|[CSimpleStringT::operator +=](#operator_add_eq)|Zřetězí nový řetězec na konci existujícího řetězce.|
|[CSimpleStringT::operator =](#operator_eq)|Přiřadí novou hodnotu `CSimpleStringT` objektu.|

### <a name="remarks"></a>Poznámky

`CSimpleStringT` je základní třídou pro různé třídy řetězec podporované jazykem Visual C++. Poskytuje minimální podporu pro správu paměti objektu řetězce a manipulaci s základní vyrovnávací paměti. Pokročilejší řetězcových objektů, naleznete v tématu [cstringt – třída](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlsimpstr.h

## <a name="append"></a> CSimpleStringT::Append

Připojí `CSimpleStringT` objektu do existujícího `CSimpleStringT` objektu.

### <a name="syntax"></a>Syntaxe

```
void Append(const CSimpleStringT& strSrc);
void Append(PCXSTR pszSrc, int nLength);
void Append(PCXSTR pszSrc);
```

#### <a name="parameters"></a>Parametry

*strSrc*<br/>
`CSimpleStringT` Objektů, které se mají připojit.

*pszSrc*<br/>
Ukazatel na řetězec obsahující znaky, které se mají připojit.

*nLength*<br/>
Počet znaků k připojení.

### <a name="remarks"></a>Poznámky

Voláním této metody lze připojit existující `CSimpleStringT` objektu na jiný `CSimpleStringT` objektu.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::Append`.

```cpp
CSimpleString str1(pMgr), str2(pMgr);
str1.SetString(_T("Soccer is"));
str2.SetString(_T(" an elegant game"));
str1.Append(str2);
ASSERT(_tcscmp(str1, _T("Soccer is an elegant game")) == 0);
```

##  <a name="appendchar"></a> CSimpleStringT::AppendChar

Přidá znak do existujícího `CSimpleStringT` objektu.

### <a name="syntax"></a>Syntaxe

```
void AppendChar(XCHAR ch);
```

#### <a name="parameters"></a>Parametry

*ch*<br/>
Znak, který má být připojen

### <a name="remarks"></a>Poznámky

Voláním této funkce připojení zadaný znak na konci existujícího `CSimpleStringT` objektu.

##  <a name="copychars"></a> CSimpleStringT::CopyChars

Zkopíruje znak nebo znaky `CSimpleStringT` objektu.

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
Ukazatel na řetězec obsahující znaky, které se mají zkopírovat.

*nChars*<br/>
Počet *pchSrc* znaků, které mají být zkopírovány.

### <a name="remarks"></a>Poznámky

Volejte tuto metodu za účelem kopírování znaků z *pchSrc* k *pchDest* řetězec.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::CopyChars`.

```cpp
CSimpleString str(_T("xxxxxxxxxxxxxxxxxxx"), 20, pMgr);
TCHAR* pszSrc = _T("Hello world!");
_tprintf_s(_T("%s\n"), str);
str.CopyChars(str.GetBuffer(), pszSrc, 12);
_tprintf_s(_T("%s\n"), str);
```

##  <a name="copycharsoverlapped"></a>  CSimpleStringT::CopyCharsOverlapped

Zkopíruje znak nebo znaky `CSimpleStringT` objektu.

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
Ukazatel na řetězec obsahující znaky, které se mají zkopírovat.

*nChars*<br/>
Počet *pchSrc* znaků, které mají být zkopírovány.

### <a name="remarks"></a>Poznámky

Volejte tuto metodu za účelem kopírování znaků z *pchSrc* k *pchDest* řetězec. Na rozdíl od `CopyChars`, `CopyCharsOverlapped` způsobem bezpečné kopírování z vyrovnávací paměti znaků, které může být překrývajících se.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CSimpleStringT::CopyChars](#copychars), nebo zdrojový kód pro `CSimpleStringT::SetString` (nachází se ve atlsimpstr.h).

##  <a name="ctor"></a>  CSimpleStringT::CSimpleStringT

Vytvoří `CSimpleStringT` objektu.

### <a name="syntax"></a>Syntaxe

```
CSimpleStringT(const XCHAR* pchSrc, int nLength, IAtlStringMgr* pStringMgr);
CSimpleStringT(PCXSTR pszSrc, IAtlStringMgr* pStringMgr);
CSimpleStringT(const CSimpleStringT& strSrc);
explicit CSimpleStringT(IAtlStringMgr* pStringMgr) throw();
```

#### <a name="parameters"></a>Parametry

*strSrc*<br/>
Existující `CSimpleStringT` objektu, které se mají zkopírovat do tohoto `CSimpleStringT` objektu.

*pchSrc*<br/>
Ukazatel na pole znaků o délce *nLength*, není null byl ukončen.

*pszSrc*<br/>
Řetězec zakončený hodnotou null ke zkopírování do tohoto `CSimpleStringT` objektu.

*nLength*<br/>
Počet znaků v `pch`.

*pStringMgr*<br/>
Ukazatel na správce paměti `CSimpleStringT` objektu. Další informace o `IAtlStringMgr` a správa paměti pro `CSimpleStringT`, naleznete v tématu [Správa paměti a CStringT](../memory-management-with-cstringt.md).

### <a name="remarks"></a>Poznámky

Vytvořit nový `CSimpleStringT` objektu. Protože se konstruktory kopírují do nového úložiště přidělené vstupních dat, může způsobit výjimky paměti.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::CSimpleStringT` s použitím knihovny ATL **typedef** `CSimpleString`. `CSimpleString` je běžně používaný specializace šablony třídy `CSimpleStringT`.

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

##  <a name="empty"></a>  CSimpleStringT::Empty

To kvůli tomu `CSimpleStringT` objekt prázdný řetězec a uvolní paměť podle potřeby.

### <a name="syntax"></a>Syntaxe

```
void Empty() throw();
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [řetězce: CString – čištění výjimek](../cstring-exception-cleanup.md).

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::Empty`.

```cpp
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```

##  <a name="freeextra"></a>  CSimpleStringT::FreeExtra

Uvolní všechny další paměť přidělenou dříve metodou řetězce, ale už je nepotřebujete.

### <a name="syntax"></a>Syntaxe

```
void FreeExtra();
```

### <a name="remarks"></a>Poznámky

To by měla snížit režii paměti používané na objekt řetězce. Metoda znovu alokuje vyrovnávací paměť pro přesnou délku vrácený [GetLength](#getlength).

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

Výstup z tohoto příkladu vypadá takto:

```Output
Alloc length is 1031, String length is 1024
Alloc length is 1031, String length is 15
Alloc length is 15, String length is 15
```

##  <a name="getalloclength"></a>  CSimpleStringT::GetAllocLength

Načte přidělené délku `CSimpleStringT` objektu.

### <a name="syntax"></a>Syntaxe

```
int GetAllocLength() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Počet znaků přidělených pro tento objekt.

### <a name="remarks"></a>Poznámky

Volejte tuto metodu za účelem určení počtu znaků přidělené to `CSimpleStringT` objektu. Zobrazit [FreeExtra](#freeextra) příklad volání této funkce.

##  <a name="getat"></a>  CSimpleStringT::GetAt

Vrátí jeden znak od `CSimpleStringT` objektu.

### <a name="syntax"></a>Syntaxe

```
XCHAR GetAt(int iChar) const;
```

#### <a name="parameters"></a>Parametry

*iChar*<br/>
Z nuly vycházející index znaku v `CSimpleStringT` objektu. *IChar* parametr musí být větší než nebo rovna 0 a menší než hodnota vrácená [GetLength](#getlength). V opačném případě `GetAt` vygeneruje výjimku.

### <a name="return-value"></a>Návratová hodnota

`XCHAR` , Která obsahuje znak na zadané pozici v řetězci.

### <a name="remarks"></a>Poznámky

Voláním této metody vrátí jeden znak určený *iChar*. Přetížená dolního indexu (**[]**) operátor je vhodné alias pro `GetAt`. Ukončovací znak null je adresovatelné bez generování událostí výjimky pomocí `GetAt`. Však není spočítaných podle `GetLength`, a vrácená hodnota je 0.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat `CSimpleStringT::GetAt`.

```cpp
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(s.GetAt(2) == _T('c'));
```

##  <a name="getbuffer"></a>  CSimpleStringT::GetBuffer

Vrací ukazatel na znak vnitřní vyrovnávací paměti pro `CSimpleStringT` objektu.

### <a name="syntax"></a>Syntaxe

```
PXSTR GetBuffer(int nMinBufferLength);
PXSTR GetBuffer();
```

#### <a name="parameters"></a>Parametry

*nMinBufferLength*<br/>
Minimální počet znaků, které mohou obsahovat vyrovnávací paměti pro znaky. Tato hodnota nezahrnuje místo pro ukončovacího znaku null.

Pokud *nMinBufferLength* je větší než délka aktuální vyrovnávací paměti, `GetBuffer` odstraní aktuální vyrovnávací paměti, nahradí jej do vyrovnávací paměti požadované velikosti a resetuje počet odkazů objektu na hodnotu nula. Pokud jste dříve označované jako [LockBuffer](#lockbuffer) na této vyrovnávací paměti, ztratíte uzamčení vyrovnávací paměti.

### <a name="return-value"></a>Návratová hodnota

`PXSTR` Ukazatel do vyrovnávací paměti objektu znak (zakončený hodnotou null).

### <a name="remarks"></a>Poznámky

Voláním této metody vrátí obsah vyrovnávací paměti `CSimpleStringT` objektu. Vrácený `PXSTR` není konstantní a proto povoluje přímých úprav `CSimpleStringT` obsah.

Pokud použijete ukazatele vrácené `GetBuffer` Změna obsahu řetězce, musí volat [ReleaseBuffer](#releasebuffer) před použitím kteréhokoli jiného `CSimpleStringT` člen metody.

Adresu vrácenou funkcí `GetBuffer` nemusí být platný po volání `ReleaseBuffer` protože další `CSimpleStringT` operace může způsobit, že `CSimpleStringT` znovu přidělit vyrovnávací paměť. Vyrovnávací paměť není nevyčerpané, pokud nezměníte délka `CSimpleStringT`.

Vyrovnávací paměti je automaticky uvolněn, kdy `CSimpleStringT` objekt zničen.

Pokud budete udržovat přehled o délce řetězce sami, by neměla připojí ukončující znak null. Ale musíte zadat délku posledním řetězci uvedené při uvolnění vyrovnávací paměť hodnotou `ReleaseBuffer`. Pokud připojíte ukončujícího znaku null, je třeba předat hodnotu -1 (výchozí) pro délku. `ReleaseBuffer` poté určí velikost vyrovnávací paměti.

Pokud není dostatek paměti k uspokojení `GetBuffer` žádosti, tato metoda vyvolá cmemoryexception – *.

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

##  <a name="getbuffersetlength"></a>  CSimpleStringT::GetBufferSetLength

Vrací ukazatel na znak vnitřní vyrovnávací paměti pro `CSimpleStringT` objektu, zkracování nebo jeho délka se v případě potřeby tak, aby přesně odpovídaly délka zadaná v rozšiřující *nLength*.

### <a name="syntax"></a>Syntaxe

```
PXSTR GetBufferSetLength(int nLength);
```

#### <a name="parameters"></a>Parametry

*nLength*<br/>
Přesnou velikost `CSimpleStringT` vyrovnávací paměti pro znaky ve znacích.

### <a name="return-value"></a>Návratová hodnota

A `PXSTR` ukazatel do vyrovnávací paměti objektu znak (zakončený hodnotou null).

### <a name="remarks"></a>Poznámky

Voláním této metody lze načíst zadané délky vnitřní vyrovnávací paměť `CSimpleStringT` objektu. Vrácený `PXSTR` ukazatel není **const** a tím umožňuje přímých úprav `CSimpleStringT` obsah.

Pokud použijete ukazatele vrácené [GetBufferSetLength](#getbuffersetlength) Změna obsahu řetězce, volání `ReleaseBuffer` aktualizovat vnitřní stav `CsimpleStringT` před použitím kteréhokoli jiného `CSimpleStringT` metody.

Adresu vrácenou funkcí `GetBufferSetLength` nemusí být platný po volání `ReleaseBuffer` protože další `CSimpleStringT` operace může způsobit, že `CSimpleStringT` znovu přidělit vyrovnávací paměť. Vyrovnávací paměť není přiřazen, pokud nezměníte délka `CSimpleStringT`.

Vyrovnávací paměti je automaticky uvolněn, kdy `CSimpleStringT` objekt zničen.

Pokud budete udržovat přehled o délce řetězce sami, nepřipojujte ukončujícího znaku null. Po uvolnění vyrovnávací paměti s použitím je nutné zadat délku řetězce konečné `ReleaseBuffer`. Pokud připojíte ukončujícího znaku null při volání `ReleaseBuffer`, předejte hodnotu -1 (výchozí) pro délku `ReleaseBuffer`, a `ReleaseBuffer` provede `strlen` pro vyrovnávací paměť k určení jeho délka.

Další informace o počítání odkazů najdete v následujících článcích:

- [Správa životnosti objektu prostřednictvím počítání odkazů](/windows/desktop/com/managing-object-lifetimes-through-reference-counting) ve Windows SDK.

- [Implementace počítání odkazů](/windows/desktop/com/implementing-reference-counting) ve Windows SDK.

- [Pravidla pro správu počty odkazů](/windows/desktop/com/rules-for-managing-reference-counts) ve Windows SDK.

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

##  <a name="getlength"></a>  CSimpleStringT::GetLength

Vrátí počet znaků `CSimpleStringT` objektu.

### <a name="syntax"></a>Syntaxe

```
int GetLength() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Počet znaků v řetězci.

### <a name="remarks"></a>Poznámky

Voláním této metody vrátí počet znaků v objektu. Počet nezahrnuje ukončovací znak null.

Pro vícebajtové znakové sady (MBCS) `GetLength` počty jednotlivých 8bitové znak; to znamená vedoucí a bajt v jeden vícebajtový znak se počítají jako dva bajty. Zobrazit [FreeExtra](#freeextra) příklad volání této funkce.

##  <a name="getmanager"></a>  CSimpleStringT::GetManager

Získá správce paměti `CSimpleStringT` objektu.

### <a name="syntax"></a>Syntaxe

```
IAtlStringMgr* GetManager() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na správce paměti pro `CSimpleStringT` objektu.

### <a name="remarks"></a>Poznámky

Voláním této metody lze načíst paměti správce používá `CSimpleStringT` objektu. Další informace o nástroje pro správu paměti a řetězcových objektů najdete v tématu [Správa paměti a CStringT](../memory-management-with-cstringt.md).

##  <a name="getstring"></a>  CSimpleStringT::GetString

Načte řetězec znaků.

### <a name="syntax"></a>Syntaxe

```
PCXSTR GetString() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na řetězec znaků zakončené znakem null.

### <a name="remarks"></a>Poznámky

Voláním této metody lze načíst řetězec znaků, které jsou přidružené k `CSimpleStringT` objektu.

> [!NOTE]
>  Vrácený `PCXSTR` ukazatel **const** a neumožňuje přímou úpravu `CSimpleStringT` obsah.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::GetString`.

```cpp
CSimpleString str(pMgr);
str += _T("Cup soccer is best!");
_tprintf_s(_T("%s"), str.GetString());
```

##  <a name="isempty"></a>  CSimpleStringT::IsEmpty

Testy `CSimpleStringT` objekt pro prázdný stav.

### <a name="syntax"></a>Syntaxe

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí TRUE, pokud `CSimpleStringT` objekt má 0 délky; jinak hodnota FALSE.

### <a name="remarks"></a>Poznámky

Voláním této metody lze zjistit, zda objekt obsahuje prázdný řetězec.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::IsEmpty`.

```cpp
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```

##  <a name="lockbuffer"></a>  CSimpleStringT::LockBuffer

Zakáže počítání odkazů a chrání data řetězec ve vyrovnávací paměti.

### <a name="syntax"></a>Syntaxe

```
PXSTR LockBuffer();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel `CSimpleStringT` objektu nebo řetězec zakončený hodnotou null.

### <a name="remarks"></a>Poznámky

Voláním této metody k uzamčení vyrovnávací paměti s `CSimpleStringT` objektu. Voláním `LockBuffer`, vytvořte kopii řetězec a hodnotou -1 pro počet odkazů. Pokud hodnotu počtu odkazů je -1, řetězec ve vyrovnávací paměti se považuje za "" zamknuté. Řetězec je v uzamčeném stavu, chráněn dvěma způsoby:

- Žádný řetězec lze získat odkaz na data v uzamčeném řetězec i v případě, že tento řetězec je přiřazená uzamčené řetězec.

- Uzamčené řetězec nikdy odkazuje jiný řetězec, i v případě, že tento řetězec je zkopírován do uzamčené řetězec.

Podle řetězce ve vyrovnávací paměti, je zajistit výhradní blokování vyrovnávací paměti řetězce zůstane zachován beze změny.

Po dokončení se `LockBuffer`, volání [UnlockBuffer](#unlockbuffer) resetovat počet odkazů na hodnotu 1.

> [!NOTE]
>  Při volání [getbuffer –](#getbuffer) na uzamčeném vyrovnávací paměti a můžete nastavit `GetBuffer` parametr `nMinBufferLength` na hodnotu větší než délka vyrovnávací paměti pro aktuální, dojde ke ztrátě uzamčení vyrovnávací paměti. Volání do `GetBuffer` odstraní aktuální vyrovnávací paměti, nahradí jej do vyrovnávací paměti požadované velikosti a resetuje počet odkazů na nulu.

Další informace o počítání odkazů najdete v následujících článcích:

- [Správa životnosti objektu prostřednictvím počítání odkazů](/windows/desktop/com/managing-object-lifetimes-through-reference-counting) ve Windows SDK

- [Implementace počítání odkazů](/windows/desktop/com/implementing-reference-counting) ve Windows SDK

- [Pravidla pro správu počty odkazů](/windows/desktop/com/rules-for-managing-reference-counts) ve Windows SDK

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

##  <a name="operator_at"></a>  CSimpleStringT::operator\[\]

Voláním této funkce pro přístup k jeden znak pole znaků.

### <a name="syntax"></a>Syntaxe

```
XCHAR operator[](int iChar) const;
```

#### <a name="parameters"></a>Parametry

*iChar*<br/>
Z nuly vycházející index znaku v řetězci.

### <a name="remarks"></a>Poznámky

Přetížená dolního indexu (**[]**) operátor vrátí znak určený index založený na nule v *iChar*. Tento operátor je vhodné náhradou za [GetAt](#getat) členskou funkci.

> [!NOTE]
>  Můžete použít dolního indexu (**[]**) operátor má být získána hodnota znaku v `CSimpleStringT`, ale nelze jej použít ke změně hodnoty znaku v `CSimpleStringT`.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::operator []`.

```cpp
CSimpleString s(_T("abc"), pMgr);
ASSERT(s[1] == _T('b'));
```

## <a name="operator_at"></a>  CSimpleStringT::operator \[\]

Voláním této funkce pro přístup k jeden znak pole znaků.

### <a name="syntax"></a>Syntaxe

```
XCHAR operator[](int iChar) const;
```

### <a name="parameters"></a>Parametry

*iChar*<br/>
Z nuly vycházející index znaku v řetězci.

### <a name="remarks"></a>Poznámky

Přetížená dolního indexu (**[]**) operátor vrátí znak určený index založený na nule v *iChar*. Tento operátor je vhodné náhradou za [GetAt](#getat) členskou funkci.

> [!NOTE]
>  Můžete použít dolního indexu (**[]**) operátor má být získána hodnota znaku v `CSimpleStringT`, ale nelze jej použít ke změně hodnoty znaku v `CSimpleStringT`.

##  <a name="operator_add_eq"></a>  CSimpleStringT::operator +=

Připojí nový řetězec nebo znak na konci existujícího řetězce.

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
Ukazatel na existující `CSimpleStringT` objektu.

*ch*<br/>
Znak, který má být připojen.

### <a name="remarks"></a>Poznámky

Operátor, který přijímá Další `CSimpleStringT` objektu nebo znak. Všimněte si, že paměť výjimky může dojít při každém použití tohoto operátoru pro zřetězení, protože může být přiděleno nové úložiště pro znaky, které jsou přidány do tohoto `CSimpleStringT` objektu.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::operator +=`.

```cpp
CSimpleString str(_T("abc"), pMgr);
ASSERT(_tcscmp((str += _T("def")), _T("abcdef")) == 0);
```

##  <a name="operator_eq"></a>  CSimpleStringT::operator =

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
Ukazatel na existující `CSimpleStringT` objektu.

### <a name="remarks"></a>Poznámky

Pokud cílový řetězec (levá strana) je již dostatečně velký pro uložení nových dat, se neprovádí žádné nové přidělení paměti. Všimněte si, že paměť výjimky může dojít při každém použití operátoru přiřazení, protože často přiděleno nové úložiště pro uložení výsledný `CSimpleStringT` objektu.

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

##  <a name="operator_pcxstr"></a>  CSimpleStringT::operator PCXSTR

Přímý přístup k znaků uložených v `CSimpleStringT` objektu jako řetězec stylu C.

### <a name="syntax"></a>Syntaxe

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel znaku řetězec data.

### <a name="remarks"></a>Poznámky

Žádné znaky jsou zkopírovány; je vrácen pouze ukazatel. Pozor na tento operátor. Pokud změníte `CString` objektu po získání ukazatel znaku, může způsobit realokace paměti, která zruší platnost ukazatel.

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

##  <a name="pcxstr"></a>  CSimpleStringT::PCXSTR

Ukazatel na konstanty typu řetězec.

### <a name="syntax"></a>Syntaxe

```
typedef ChTraitsBase< BaseType >::PCXSTR PCXSTR;
```

##  <a name="preallocate"></a>  CSimpleStringT::Preallocate

Přidělí konkrétní velikost pro bajtů `CSimpleStringT` objektu.

### <a name="syntax"></a>Syntaxe

```
void Preallocate( int nLength);
```

#### <a name="parameters"></a>Parametry

*nLength*<br/>
Přesnou velikost `CSimpleStringT` vyrovnávací paměti pro znaky ve znacích.

### <a name="remarks"></a>Poznámky

Volejte tuto metodu za účelem přidělení velikosti vyrovnávací paměti specifické pro `CSimpleStringT` objektu.

`CSimpleStringT` generuje STATUS_NO_MEMORY výjimku, pokud se nepovedlo se přidělit prostor pro vyrovnávací paměti pro znaky. Ve výchozím nastavení, přidělení paměti se provádí pomocí funkce rozhraní WIN32 API `HeapAlloc` nebo `HeapReAlloc`.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::Preallocate`.

```cpp
CSimpleString str(pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
str.Preallocate(100);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
```

##  <a name="pxstr"></a>  CSimpleStringT::PXSTR

Ukazatel na řetězec.

### <a name="syntax"></a>Syntaxe

```
typedef ChTraitsBase< BaseType >::PXSTR PXSTR;
```

##  <a name="releasebuffer"></a>  CSimpleStringT::ReleaseBuffer

Uvolní kontrolu nad vyrovnávací paměť přidělaná [getbuffer –](#getbuffer).

### <a name="syntax"></a>Syntaxe

```
void ReleaseBuffer(int nNewLength = -1);
```

#### <a name="parameters"></a>Parametry

*nNewLength*<br/>
Nové délku řetězce ve znacích, výčtu nebudou započteny ukončovacího znaku null. Pokud řetězec má hodnotu null, byla ukončena,-1, výchozí hodnota nastaví `CSimpleStringT` velikost aktuální délka řetězce.

### <a name="remarks"></a>Poznámky

Volejte tuto metodu za účelem přerozdělit nebo uvolnit vyrovnávací paměť na objekt řetězce. Pokud víte, že řetězec ve vyrovnávací paměti je null byl ukončen, můžete vynechat *nNewLength* argument. Pokud váš řetězec nemá hodnotu null, byla ukončena, použijte *nNewLength* k určení jeho délky. Adresu vrácenou funkcí [getbuffer –](#getbuffer) neplatí po volání `ReleaseBuffer` nebo jakékoli jiné `CSimpleStringT` operace.

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

##  <a name="releasebuffersetlength"></a>  CSimpleStringT::ReleaseBufferSetLength

Uvolní kontrolu nad vyrovnávací paměť přidělaná [getbuffer –](#getbuffer).

### <a name="syntax"></a>Syntaxe

```
void ReleaseBufferSetLength(int nNewLength);
```

#### <a name="parameters"></a>Parametry

*nNewLength*<br/>
Délka řetězce se vydávají

### <a name="remarks"></a>Poznámky

Tato funkce je funkčně podobný [ReleaseBuffer](#releasebuffer) s tím rozdílem, že musí být předán platnou délku pro objekt řetězce.

##  <a name="setat"></a>  CSimpleStringT::SetAt

Nastaví jeden znak od `CSimpleStringT` objektu.

### <a name="syntax"></a>Syntaxe

```
void SetAt(int iChar, XCHAR ch);
```

#### <a name="parameters"></a>Parametry

*iChar*<br/>
Z nuly vycházející index znaku v `CSimpleStringT` objektu. *IChar* parametr musí být větší než nebo rovna 0 a menší než hodnota vrácená [GetLength](#getlength).

*ch*<br/>
Nový znak.

### <a name="remarks"></a>Poznámky

Volejte tuto metodu přepsat znaku na *iChar*. Tato metoda nebude zvětšit řetězec, pokud *iChar* přesahuje hranice existujícího řetězce.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::SetAt`.

```cpp
CSimpleString s(_T("abcdef"), pMgr);
s.SetAt(1, _T('a'));
ASSERT(_tcscmp(s, _T("aacdef")) == 0);
```

##  <a name="setmanager"></a>  CSimpleStringT::SetManager

Určuje správce paměti `CSimpleStringT` objektu.

### <a name="syntax"></a>Syntaxe

```
void SetManager(IAtlStringMgr* pStringMgr);
```

#### <a name="parameters"></a>Parametry

*pStringMgr*<br/>
Ukazatel na nového správce paměti.

### <a name="remarks"></a>Poznámky

Voláním této metody lze zadat nové paměti správce používá `CSimpleStringT` objektu. Další informace o nástroje pro správu paměti a řetězcových objektů najdete v tématu [Správa paměti a CStringT](../memory-management-with-cstringt.md).

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::SetManager`.

```cpp
CSimpleString s(pMgr);
s.SetManager(pCustomMgr);
```

##  <a name="setstring"></a>  CSimpleStringT::SetString

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

Zkopírujte řetězec do `CSimpleStringT` objektu. `SetString` přepíše starší řetězce data ve vyrovnávací paměti.

Obě verze `SetString` zkontrolujte, zda *pszSrc* je ukazatel s hodnotou null a pokud se jedná, vyvolá chybu E_INVALIDARG.

Jeden parametr verzi `SetString` očekává, že *pszSrc* tak, aby odkazoval na řetězec zakončený hodnotou null.

Parametr dvě verze `SetString` také očekává, že *pszSrc* na řetězec zakončený hodnotou null. Používá *nLength* jako délku řetězce Pokud nejprve nalezne ukončovacího znaku null.

Parametr dvě verze `SetString` také zkontroluje, jestli *pszSrc* odkazuje na umístění v aktuální vyrovnávací paměti v `CSimpleStringT`. V tomto případě speciální `SetString` používá funkci kopírování paměti, která nepřepisuje data řetězce podle zkopíruje řetězcová data zpět do vyrovnávací paměti.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::SetString`.

```cpp
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(_tcscmp(s, _T("abcdef")) == 0);
s.SetString(_T("Soccer"), 6);
ASSERT(_tcscmp(s, _T("Soccer")) == 0);
```

##  <a name="stringlength"></a>  CSimpleStringT::StringLength

Vrátí počet znaků v zadaném řetězci.

### <a name="syntax"></a>Syntaxe

```
ATL_NOINLINE static int StringLength(PCXSTR psz) throw();
```

#### <a name="parameters"></a>Parametry

*psz*<br/>
Ukazatel na řetězec zakončený hodnotou null.

### <a name="return-value"></a>Návratová hodnota

Počet znaků v *psz*; výčtu nebudou započteny ukončovacího znaku null.

### <a name="remarks"></a>Poznámky

Voláním této metody lze načíst počet znaků v řetězci, na které odkazuje *psz*.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití `CSimpleStringT::StringLength`.

```cpp
ASSERT(CSimpleString::StringLength(_T("soccer")) == 6);
```

##  <a name="truncate"></a>  CSimpleStringT::Truncate

Ořízne na novou délku řetězce.

### <a name="syntax"></a>Syntaxe

```
void Truncate(int nNewLength);
```

#### <a name="parameters"></a>Parametry

*nNewLength*<br/>
Nové délku řetězce.

### <a name="remarks"></a>Poznámky

Voláním této metody lze zkrátit obsah řetězce na novou délku.

> [!NOTE]
>  Toto neovlivňuje přidělené délka vyrovnávací paměti. Snížit nebo zvýšit aktuální vyrovnávací paměti, naleznete v tématu [FreeExtra](#freeextra) a [Preallocate](#preallocate).

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

##  <a name="unlockbuffer"></a>  CSimpleStringT::UnlockBuffer

Odemkne vyrovnávací paměti s `CSimpleStringT` objektu.

### <a name="syntax"></a>Syntaxe

```
void UnlockBuffer() throw();
```

### <a name="remarks"></a>Poznámky

Volejte tuto metodu za účelem resetování počet odkazů řetězce na hodnotu 1.

`CSimpleStringT` Destruktor automaticky volá `UnlockBuffer` zajistit, že vyrovnávací paměť není uzamčen při volání destruktoru. Příklad této metody, naleznete v tématu [LockBuffer](#lockbuffer).

##  <a name="dtor"></a>  Csimplestringt –:: ~ csimplestringt –

Odstraní `CSimpleStringT` objektu.

### <a name="syntax"></a>Syntaxe

```
~CSimpleStringT() throw();
```

### <a name="remarks"></a>Poznámky

Voláním této metody lze zničit `CSimpleStringT` objektu.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Sdílené třídy ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)