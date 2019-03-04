---
title: CComBSTR – třída
ms.date: 11/04/2016
f1_keywords:
- CComBSTR
- ATLBASE/ATL::CComBSTR
- ATLBASE/ATL::CComBSTR::CComBSTR
- ATLBASE/ATL::CComBSTR::Append
- ATLBASE/ATL::CComBSTR::AppendBSTR
- ATLBASE/ATL::CComBSTR::AppendBytes
- ATLBASE/ATL::CComBSTR::ArrayToBSTR
- ATLBASE/ATL::CComBSTR::AssignBSTR
- ATLBASE/ATL::CComBSTR::Attach
- ATLBASE/ATL::CComBSTR::BSTRToArray
- ATLBASE/ATL::CComBSTR::ByteLength
- ATLBASE/ATL::CComBSTR::Copy
- ATLBASE/ATL::CComBSTR::CopyTo
- ATLBASE/ATL::CComBSTR::Detach
- ATLBASE/ATL::CComBSTR::Empty
- ATLBASE/ATL::CComBSTR::Length
- ATLBASE/ATL::CComBSTR::LoadString
- ATLBASE/ATL::CComBSTR::ReadFromStream
- ATLBASE/ATL::CComBSTR::ToLower
- ATLBASE/ATL::CComBSTR::ToUpper
- ATLBASE/ATL::CComBSTR::WriteToStream
- ATLBASE/ATL::CComBSTR::m_str
helpviewer_keywords:
- BSTRs, wrapper
- CComBSTR class
- CComBSTR
ms.assetid: 8fea1879-a05e-47a5-a803-8dec60eaa534
ms.openlocfilehash: 48447b9e6a211927d8e729dd761d2e14ecd89615
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57282354"
---
# <a name="ccombstr-class"></a>CComBSTR – třída

Tato třída představuje obálku pro [BSTR](/previous-versions/windows/desktop/automat/bstr)s.

## <a name="syntax"></a>Syntaxe

```
class CComBSTR
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CComBSTR::CComBSTR](#ccombstr)|Konstruktor|
|[CComBSTR::~CComBSTR](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComBSTR::Append](#append)|Přidá řetězec do `m_str`.|
|[CComBSTR::AppendBSTR](#appendbstr)|Připojí k BSTR `m_str`.|
|[CComBSTR::AppendBytes](#appendbytes)|Přidá zadaný počet bajtů, které mají `m_str`.|
|[CComBSTR::ArrayToBSTR](#arraytobstr)|Vytvoří BSTR z první znak každého prvku v safearray a připojí ho k `CComBSTR` objektu.|
|[CComBSTR::AssignBSTR](#assignbstr)|Přiřadí BSTR k `m_str`.|
|[CComBSTR::Attach](#attach)|Připojí k BSTR `CComBSTR` objektu.|
|[CComBSTR::BSTRToArray](#bstrtoarray)|Vytvoří jednorozměrný safearray založený na nule, kde každý prvek pole je znak z `CComBSTR` objektu.|
|[CComBSTR::ByteLength](#bytelength)|Vrátí délku objektu `m_str` v bajtech.|
|[CComBSTR::Copy](#copy)|Vrátí kopii objektu `m_str`.|
|[CComBSTR::CopyTo](#copyto)|Vrátí kopii objektu `m_str` prostřednictvím **[out]** parametr|
|[CComBSTR::Detach](#detach)|Odpojí `m_str` z `CComBSTR` objektu.|
|[CComBSTR::Empty](#empty)|Uvolní `m_str`.|
|[CComBSTR::Length](#length)|Vrátí délku objektu `m_str`.|
|[CComBSTR::LoadString](#loadstring)|Načte prostředek řetězce.|
|[CComBSTR::ReadFromStream](#readfromstream)|Načte objekt BSTR z datového proudu.|
|[CComBSTR::ToLower](#tolower)|Převede řetězec na malá písmena.|
|[CComBSTR::ToUpper](#toupper)|Převede řetězec na velká písmena.|
|[CComBSTR::WriteToStream](#writetostream)|Uloží `m_str` do datového proudu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CComBSTR::operator BSTR](#operator_bstr)|Přetypování `CComBSTR` objekt BSTR.|
|[CComBSTR::operator!](#operator_not)|Vrátí hodnotu PRAVDA nebo NEPRAVDA v závislosti na tom, zda `m_str`má hodnotu NULL.|
|[CComBSTR::operator! =](#operator_neq)|Porovná `CComBSTR` s řetězcem.|
|[CComBSTR::operator &](#operator_amp)|Vrátí adresu `m_str`.|
|[CComBSTR::operator +=](#operator_add_eq)|Připojí `CComBSTR` objektu.|
|[CComBSTR::operator <](#operator_lt)|Porovná `CComBSTR` s řetězcem.|
|[CComBSTR::operator =](#operator_eq)|Přiřadí hodnotu k `m_str`.|
|[CComBSTR::operator ==](#operator_eq_eq)|Porovná `CComBSTR` s řetězcem.|
|[CComBSTR::operator >](#operator_gt)|Porovná `CComBSTR` s řetězcem.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CComBSTR::m_str](#m_str)|Obsahuje BSTR přidružené `CComBSTR` objektu.|

## <a name="remarks"></a>Poznámky

`CComBSTR` Třídy tvoří obálku pro datových typů BSTR, které jsou s předponou délku řetězce. Délka se ukládá jako celé číslo v umístění v paměti před data v řetězci.

A [BSTR](/previous-versions/windows/desktop/automat/bstr) je zakončený hodnotou null po poslední znak počítá ale může také obsahovat vložený do řetězce znaky s hodnotou null. Délka řetězce se určuje podle počtu znaků, nikoli první znak null.

> [!NOTE]
>  `CComBSTR` Třídy nabízí celou řadu členů (konstruktorů, operátory přiřazení a porovnání operátory), které přijímají řetězce ANSI nebo Unicode jako argumenty. ANSI verze těchto funkcí jsou míň efektivní než jejich protějšky v kódování Unicode, protože dočasných řetězců v kódu Unicode jsou často vytvořili interně. Z důvodu efektivity použijte Unicode verze, kde je to možné.

> [!NOTE]
>  Kvůli implementovány v aplikaci Visual Studio .NET vyhledávací Vylepšená chování kódu, jako `bstr = L"String2" + bstr;`, které mohou mít zkompilovat v předchozích verzích by měla být implementována místo jako `bstr = CStringW(L"String2") + bstr`.

Seznam upozornění při použití `CComBSTR`, naleznete v tématu [programování pomocí třídy CComBSTR](../../atl/programming-with-ccombstr-atl.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

##  <a name="append"></a>  CComBSTR::Append

Buď připojí *lpsz* nebo člen BSTR *bstrSrc* k [m_str](#m_str).

```
HRESULT Append(const CComBSTR& bstrSrc) throw();
HRESULT Append(wchar_t ch) throw();
HRESULT Append(char ch) throw();
HRESULT Append(LPCOLESTR lpsz) throw();
HRESULT Append(LPCSTR lpsz) throw();
HRESULT Append(LPCOLESTR lpsz, int nLen) throw();
```

### <a name="parameters"></a>Parametry

*bstrSrc*<br/>
[in] A `CComBSTR` objektu, který chcete připojit.

*ch*<br/>
[in] Znak pro připojení.

*lpsz*<br/>
[in] Ukončit nulou znak řetězec pro připojení. Řetězec s kódováním Unicode lze předat prostřednictvím přetížení LPCOLESTR nebo řetězec ANSI prostřednictvím LPCSTR verze.

*nLen*<br/>
[in] Počet znaků od *lpsz* připojit.

### <a name="return-value"></a>Návratová hodnota

S_OK na úspěch, nebo všechny standardní hodnota HRESULT chyby.

### <a name="remarks"></a>Poznámky

Řetězec ANSI se převést do kódování Unicode, než se připojí.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#32](../../atl/codesnippet/cpp/ccombstr-class_1.cpp)]

##  <a name="appendbstr"></a>  CComBSTR::AppendBSTR

Připojí zadaný BSTR k [m_str](#m_str).

```
HRESULT AppendBSTR(BSTR p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
[in] BSTR má připojit.

### <a name="return-value"></a>Návratová hodnota

S_OK na úspěch, nebo všechny standardní hodnota HRESULT chyby.

### <a name="remarks"></a>Poznámky

V této metodě nepředávejte běžné širokoznaký řetězec. Kompilátor nemůže zachytávat chyby a spustit, když dojde k chybám.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#33](../../atl/codesnippet/cpp/ccombstr-class_2.cpp)]

##  <a name="appendbytes"></a>  CComBSTR::AppendBytes

Přidá zadaný počet bajtů, které mají [m_str](#m_str) bez převodu.

```
HRESULT AppendBytes(const char* lpsz, int nLen) throw();
```

### <a name="parameters"></a>Parametry

*lpsz*<br/>
[in] Ukazatel na pole bajtů pro připojení.

*p*<br/>
[in] Počet bajtů, které mají připojit.

### <a name="return-value"></a>Návratová hodnota

S_OK na úspěch, nebo všechny standardní hodnota HRESULT chyby.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#34](../../atl/codesnippet/cpp/ccombstr-class_3.cpp)]

##  <a name="arraytobstr"></a>  CComBSTR::ArrayToBSTR

Uvolní všechny existující řetězce uchovávat v datovém typu `CComBSTR` objekt, vytvoří BSTR z první znak každého prvku v safearray a připojí ho k `CComBSTR` objektu.

```
HRESULT ArrayToBSTR(const SAFEARRAY* pSrc) throw();
```

### <a name="parameters"></a>Parametry

*pSrc*<br/>
[in] Safearray obsahující prvků, které slouží k vytvoření řetězce.

### <a name="return-value"></a>Návratová hodnota

S_OK na úspěch, nebo všechny standardní hodnota HRESULT chyby.

##  <a name="assignbstr"></a>  CComBSTR::AssignBSTR

Přiřadí BSTR k [m_str](#m_str).

```
HRESULT AssignBSTR(const BSTR bstrSrc) throw();
```

### <a name="parameters"></a>Parametry

*bstrSrc*<br/>
[in] BSTR přiřadit aktuální `CComBSTR` objektu.

### <a name="return-value"></a>Návratová hodnota

S_OK na úspěch, nebo všechny standardní hodnota HRESULT chyby.

##  <a name="attach"></a>  CComBSTR::Attach

Připojí k BSTR `CComBSTR` objektu tak, že nastavíte [m_str](#m_str) člen *src*.

```
void Attach(BSTR src) throw();
```

### <a name="parameters"></a>Parametry

*src*<br/>
[in] BSTR pro připojení k objektu.

### <a name="remarks"></a>Poznámky

V této metodě nepředávejte běžné širokoznaký řetězec. Kompilátor nemůže zachytávat chyby a spustit, když dojde k chybám.

> [!NOTE]
>  Tato metoda se uplatnit, pokud `m_str` je jiná než NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]

##  <a name="bstrtoarray"></a>  CComBSTR::BSTRToArray

Vytvoří jednorozměrný safearray založený na nule, kde každý prvek pole je znak z `CComBSTR` objektu.

```
HRESULT BSTRToArray(LPSAFEARRAY* ppArray) throw();
```

### <a name="parameters"></a>Parametry

*ppArray*<br/>
[out] Ukazatel na pole safearray používají k uložení výsledků této funkce.

### <a name="return-value"></a>Návratová hodnota

S_OK na úspěch, nebo všechny standardní hodnota HRESULT chyby.

##  <a name="bytelength"></a>  CComBSTR::ByteLength

Vrátí počet bajtů v `m_str`, s výjimkou ukončujícího znaku null.

```
unsigned int ByteLength() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Délka [m_str](#m_str) člena v bajtech.

### <a name="remarks"></a>Poznámky

Vrátí hodnotu 0, pokud `m_str` má hodnotu NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#36](../../atl/codesnippet/cpp/ccombstr-class_5.cpp)]

##  <a name="ccombstr"></a>  CComBSTR::CComBSTR

Konstruktor Výchozí konstruktor sady [m_str](#m_str) člena na hodnotu NULL.

```
CComBSTR() throw();
CComBSTR(const CComBSTR& src);
CComBSTR(REFGUID  guid);
CComBSTR(int nSize);
CComBSTR(int nSize, LPCOLESTR sz);
CComBSTR(int nSize, LPCSTR sz);
CComBSTR(LPCOLESTR pSrc);
CComBSTR(LPCSTR pSrc);
CComBSTR(CComBSTR&& src) throw(); // (Visual Studio 2017)
```

### <a name="parameters"></a>Parametry

*nSize*<br/>
[in] Počet znaků pro kopírování z *sz* nebo počáteční velikost ve znacích `CComBSTR`.

*sz*<br/>
[in] Řetězec zkopírujte. Verze Unicode určuje LPCOLESTR; verze ANSI určuje LPCSTR.

*pSrc*<br/>
[in] Řetězec zkopírujte. Verze Unicode určuje LPCOLESTR; verze ANSI určuje LPCSTR.

*src*<br/>
[in] A `CComBSTR` objektu.

*identifikátor GUID*<br/>
[in] Odkaz na `GUID` struktury.

### <a name="remarks"></a>Poznámky

Nastaví konstruktor kopie `m_str` kopii BSTR členem *src*. `REFGUID` Konstruktor převede na řetězec pomocí identifikátoru GUID `StringFromGUID2` a výsledek je uložen.

Druhá sada konstruktorů `m_str` na kopii zadaného řetězce. Pokud předáte hodnotu *nSize*, pak pouze *nSize* znaky budou zkopírovány, za nímž následuje ukončujícího znaku null.

`CComBSTR` podporuje přesunutí sémantiky. Můžete použít konstruktor přesunu (konstruktor, který bere odkaz rvalue (`&&`) Chcete-li vytvořit nový objekt, který používá stejné podkladová data, protože původní objekt můžete předat jako argument, bez režie kopírování objektu.

Destruktor uvolní řetězce odkazované `m_str`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#37](../../atl/codesnippet/cpp/ccombstr-class_6.cpp)]

##  <a name="dtor"></a>  CComBSTR:: ~ CComBSTR

Destruktor.

```
~CComBSTR();
```

### <a name="remarks"></a>Poznámky

Destruktor uvolní řetězce odkazované `m_str`.

##  <a name="copy"></a>  CComBSTR::Copy

Přiděluje a vrátí kopii objektu `m_str`.

```
BSTR Copy() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Kopie [m_str](#m_str) člena. Pokud `m_str` má hodnotu NULL, vrátí hodnotu NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#38](../../atl/codesnippet/cpp/ccombstr-class_7.cpp)]

##  <a name="copyto"></a>  CComBSTR::CopyTo

Přiděluje a vrátí kopii objektu [m_str](#m_str) prostřednictvím parametru.

```
HRESULT CopyTo(BSTR* pbstr) throw();

HRESULT CopyTo(VARIANT* pvarDest) throw();
```

### <a name="parameters"></a>Parametry

*pbstr*<br/>
[out] Adresa BSTR, ve kterých se mají vrátit řetězec přidělených touto metodou.

*pvarDest*<br/>
[out] Adresa hodnotu typu VARIANT, ve kterých se mají vrátit řetězec přidělených touto metodou.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnotu HRESULT označující úspěch nebo neúspěch kopie.

### <a name="remarks"></a>Poznámky

Po volání této metody, varianty odkazované *pvarDest* typu VT_BSTR.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#39](../../atl/codesnippet/cpp/ccombstr-class_8.cpp)]

##  <a name="detach"></a>  CComBSTR::Detach

Odpojí [m_str](#m_str) z `CComBSTR` objekt a nastaví `m_str` na hodnotu NULL.

```
BSTR Detach() throw();
```

### <a name="return-value"></a>Návratová hodnota

Přidružené BSTR `CComBSTR` objektu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#40](../../atl/codesnippet/cpp/ccombstr-class_9.cpp)]

##  <a name="empty"></a>  CComBSTR::Empty

Uvolňuje [m_str](#m_str) člena.

```
void Empty() throw();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#41](../../atl/codesnippet/cpp/ccombstr-class_10.cpp)]

##  <a name="length"></a>  CComBSTR::Length

Vrátí počet znaků v `m_str`, s výjimkou ukončujícího znaku null.

```
unsigned int Length() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Délka [m_str](#m_str) člena.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#42](../../atl/codesnippet/cpp/ccombstr-class_11.cpp)]

##  <a name="loadstring"></a>  CComBSTR::LoadString

Načte řetězec prostředku zadaného parametrem *nID* a ukládá ho do tohoto objektu.

```
bool LoadString(HINSTANCE hInst, UINT nID) throw();
bool LoadString(UINT nID) throw();
```

### <a name="parameters"></a>Parametry

Zobrazit [LoadString](/windows/desktop/api/winuser/nf-winuser-loadstringa) ve Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je řetězec úspěšně načten. v opačném případě vrátí hodnotu FALSE.

### <a name="remarks"></a>Poznámky

První funkce načte prostředek z modulu identifikovaný prostřednictvím *hInst* parametru. Druhá funkce načte z modulu prostředků přidružené k prostředku [ccommodule –](../../atl/reference/ccommodule-class.md)-odvozené objekt použitý v tomto projektu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#43](../../atl/codesnippet/cpp/ccombstr-class_12.cpp)]

##  <a name="m_str"></a>  CComBSTR::m_str

Obsahuje BSTR přidružené `CComBSTR` objektu.

```
BSTR m_str;
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#49](../../atl/codesnippet/cpp/ccombstr-class_13.cpp)]

##  <a name="operator_bstr"></a>  CComBSTR::operator BSTR

Přetypování `CComBSTR` objekt BSTR.

```
operator BSTR() const throw();
```

### <a name="remarks"></a>Poznámky

Umožňuje předat `CComBSTR` objektů funkcí, které mají **[in] BSTR** parametry.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CComBSTR::m_str](#m_str).

##  <a name="operator_not"></a>  CComBSTR::operator!

Kontroluje, zda řetězec BSTR má hodnotu NULL.

```
bool operator!() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí TRUE, pokud [m_str](#m_str) člena je NULL; v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tento operátor zkontroluje pouze pro hodnotu NULL, ne pro prázdný řetězec.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]

##  <a name="operator_neq"></a>  CComBSTR::operator! =

Vrátí logickou opakem [operátor ==](#operator_eq_eq).

```
bool operator!= (const CComBSTR& bstrSrc) const throw();
bool operator!= (LPCOLESTR pszSrc) const;
bool operator!= (LPCSTR pszSrc) const;
bool operator!= (int nNull) const throw();
```

### <a name="parameters"></a>Parametry

*bstrSrc*<br/>
[in] A `CComBSTR` objektu.

*pszSrc*<br/>
[in] Řetězec zakončený nula.

*nNull*<br/>
[in] Musí mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Vrátí TRUE, pokud položka, který se porovnává se nerovná `CComBSTR` objektu; jinak vrátí FALSE.

### <a name="remarks"></a>Poznámky

`CComBSTR`s jsou porovnány pomocí textu v kontextu uživatele výchozí národní prostředí. Poslední relační operátor pouze porovnává obsažený řetězec s hodnotou NULL.

##  <a name="operator_amp"></a>  CComBSTR::operator &amp;

Vrátí adresu BSTR uložené v [m_str](#m_str) člena.

```
BSTR* operator&() throw();
```

### <a name="remarks"></a>Poznámky

`CComBstr operator &` speciální kontrolního výrazu k němu má přidružené k identifikaci nevracení paměti. Program bude assert, kdy `m_str` člen je inicializovaný. Byl vytvořen tohoto kontrolního výrazu k identifikaci situací, kdy používá programátor `& operator` přiřadí novou hodnotu do `m_str` člen, aniž by bylo uvolněno první přidělení `m_str`. Pokud `m_str` rovná NULL, program se předpokládá, že m_str nepřidělil se ještě. V takovém případě nebude uplatňovat program.

Tento kontrolní výraz není standardně povolená. Definujte ATL_CCOMBSTR_ADDRESS_OF_ASSERT povolit tento kontrolní výraz.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#46](../../atl/codesnippet/cpp/ccombstr-class_14.cpp)]

[!code-cpp[NVC_ATL_Utilities#47](../../atl/codesnippet/cpp/ccombstr-class_15.cpp)]

##  <a name="operator_add_eq"></a>  CComBSTR::operator +=

Přidá řetězec do `CComBSTR` objektu.

```
CComBSTR& operator+= (const CComBSTR& bstrSrc);
CComBSTR& operator+= (const LPCOLESTR pszSrc);
```

### <a name="parameters"></a>Parametry

*bstrSrc*<br/>
[in] A `CComBSTR` objektu, který chcete připojit.

*pszSrc*<br/>
[in] Ukončit nulou řetězec pro připojení.

### <a name="remarks"></a>Poznámky

`CComBSTR`s jsou porovnány pomocí textu v kontextu uživatele výchozí národní prostředí. Provádí se porovnání LPCOLESTR pomocí `memcmp` na nezpracovaných dat v každém řetězci. Porovnání LPCSTR provádí stejně jako po dočasné Unicode kopie *pszSrc* se vytvořil. Poslední relační operátor pouze porovnává obsažený řetězec s hodnotou NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#48](../../atl/codesnippet/cpp/ccombstr-class_16.cpp)]

##  <a name="operator_lt"></a>  CComBSTR::operator &lt;

Porovná `CComBSTR` s řetězcem.

```
bool operator<(const CComBSTR& bstrSrc) const throw();
bool operator<(LPCOLESTR pszSrc) const throw();
bool operator<(LPCSTR pszSrc) const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je položka, který se porovnává menší než `CComBSTR` objektu; jinak vrátí FALSE.

### <a name="remarks"></a>Poznámky

Porovnání se provádí pomocí výchozí národní prostředí uživatele.

##  <a name="operator_eq"></a>  CComBSTR::operator =

Nastaví [m_str](#m_str) člena na kopii *pSrc* nebo kopii BSTR členem *src*. Operátor přiřazení přesunu přesune `src` bez kopírování.

```
CComBSTR& operator= (const CComBSTR& src);
CComBSTR& operator= (LPCOLESTR pSrc);
CComBSTR& operator= (LPCSTR pSrc);
CComBSTR& operator= (CComBSTR&& src) throw(); // (Visual Studio 2017)
```

### <a name="remarks"></a>Poznámky

*PSrc* parametr určuje buď LPCOLESTR pro verze Unicode nebo LPCSTR ANSI verze.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CComBSTR::Copy](#copy).

##  <a name="operator_eq_eq"></a>  CComBSTR::operator ==

Porovná `CComBSTR` s řetězcem. `CComBSTR`s jsou porovnány pomocí textu v kontextu uživatele výchozí národní prostředí.

```
bool operator== (const CComBSTR& bstrSrc) const throw();
bool operator== (LPCOLESTR pszSrc) const;
bool operator== (LPCSTR pszSrc) const;
bool operator== (int nNull) const throw();
```

### <a name="parameters"></a>Parametry

*bstrSrc*<br/>
[in] A `CComBSTR` objektu.

*pszSrc*<br/>
[in] Řetězec zakončený nula.

*nNull*<br/>
[in] Musí mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Vrátí TRUE, pokud položka, který se porovnává se rovná `CComBSTR` objektu; jinak vrátí FALSE.

### <a name="remarks"></a>Poznámky

Poslední relační operátor pouze porovnává obsažený řetězec s hodnotou NULL.

##  <a name="operator_gt"></a>  CComBSTR::operator &gt;

Porovná `CComBSTR` s řetězcem.

```
bool operator>(const CComBSTR& bstrSrc) const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je větší než položky, který se porovnává `CComBSTR` objektu; jinak vrátí FALSE.

### <a name="remarks"></a>Poznámky

Porovnání se provádí pomocí výchozí národní prostředí uživatele.

##  <a name="readfromstream"></a>  CComBSTR::ReadFromStream

Nastaví [m_str](#m_str) člen BSTR obsaženy v určený datový proud.

```
HRESULT ReadFromStream(IStream* pStream) throw();
```

### <a name="parameters"></a>Parametry

*pStream*<br/>
[in] Ukazatel [IStream](/windows/desktop/api/objidl/nn-objidl-istream) rozhraní v datovém proudu, který obsahuje data.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

`ReadToStream` vyžaduje obsah datového proudu na aktuální pozici, aby byly kompatibilní s formátem data zapsaná voláním [WriteToStream](#writetostream).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#44](../../atl/codesnippet/cpp/ccombstr-class_17.cpp)]

##  <a name="tolower"></a>  CComBSTR::ToLower

Převede obsažený řetězec na malá písmena.

```
HRESULT ToLower() throw();
```

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Zobrazit `CharLowerBuff` Další informace o tom, jak se provádí převod.

##  <a name="toupper"></a>  CComBSTR::ToUpper

Převede obsažený řetězec na velká písmena.

```
HRESULT ToUpper() throw();
```

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Zobrazit `CharUpperBuff` Další informace o tom, jak se provádí převod.

##  <a name="writetostream"></a>  CComBSTR::WriteToStream

Uloží [m_str](#m_str) člen do datového proudu.

```
HRESULT WriteToStream(IStream* pStream) throw();
```

### <a name="parameters"></a>Parametry

*pStream*<br/>
[in] Ukazatel [IStream](/windows/desktop/api/objidl/nn-objidl-istream) rozhraní na datovém proudu.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Můžete znovu vytvořit BSTR z obsahu pomocí datového proudu [ReadFromStream](#readfromstream) funkce.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#45](../../atl/codesnippet/cpp/ccombstr-class_18.cpp)]

## <a name="see-also"></a>Viz také:

[Přehled tříd](../../atl/atl-class-overview.md)<br/>
[ATL a MFC – makra převodu řetězců](string-conversion-macros.md)
