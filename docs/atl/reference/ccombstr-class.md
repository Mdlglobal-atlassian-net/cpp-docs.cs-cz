---
title: Třída CComBSTR
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
ms.openlocfilehash: c1448a5638b263a87403edf0baca170f0f952e26
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748133"
---
# <a name="ccombstr-class"></a>Třída CComBSTR

Tato třída je obálka pro [BSTR](/previous-versions/windows/desktop/automat/bstr)s.

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
|[CComBSTR::Připojit](#append)|Připojí řetězec k `m_str`aplikaci .|
|[CComBSTR::AppendBSTR](#appendbstr)|Připojí BSTR k `m_str`aplikaci .|
|[CComBSTR::Připojit bajty](#appendbytes)|Připojí k aplikaci zadaný `m_str`počet bajtů.|
|[CComBSTR::ArrayToBSTR](#arraytobstr)|Vytvoří BSTR z prvního znaku každého prvku v safearray `CComBSTR` a připojí jej k objektu.|
|[CComBSTR::AssignBSTR](#assignbstr)|Přiřadí BSTR `m_str`společnosti .|
|[CComBSTR::Připojit](#attach)|Připojí BSTR k `CComBSTR` objektu.|
|[CComBSTR::BSTRToArray](#bstrtoarray)|Vytvoří jednorozměrné pole safearray založené na nule, kde každý `CComBSTR` prvek pole je znak z objektu.|
|[CComBSTR::Délka bajty](#bytelength)|Vrátí délku `m_str` v bajtů.|
|[CComBSTR::Kopírovat](#copy)|Vrátí kopii `m_str`souboru .|
|[CComBSTR::Copyto](#copyto)|Vrátí kopii `m_str` parametru **[out]**|
|[CComBSTR::Detach](#detach)|Odpojí `m_str` se `CComBSTR` od objektu.|
|[CComBSTR::Prázdné](#empty)|Osvobozuje `m_str`.|
|[CComBSTR::Délka](#length)|Vrátí délku `m_str`souboru .|
|[CComBSTR::Načítat](#loadstring)|Načte řetězec prostředku.|
|[CComBSTR::ReadFromStream](#readfromstream)|Načte bstr objekt z datového proudu.|
|[CComBSTR::ToLower](#tolower)|Převede řetězec na malá písmena.|
|[CComBSTR::Toupper](#toupper)|Převede řetězec na velká písmena.|
|[CComBSTR::WriteToStream](#writetostream)|Uloží `m_str` do datového proudu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CComBSTR::operátor BSTR](#operator_bstr)|Převrhne `CComBSTR` objekt bstr.|
|[CComBSTR::operátor !](#operator_not)|Vrátí hodnotu PRAVDA nebo `m_str`NEPRAVDA v závislosti na tom, zda je null.|
|[CComBSTR::operátor !=](#operator_neq)|Porovná řetězec. `CComBSTR`|
|[CComBSTR::&operátora](#operator_amp)|Vrátí adresu `m_str`.|
|[CComBSTR::operátor +=](#operator_add_eq)|Připojí k `CComBSTR` objektu.|
|[CComBSTR::<operátora](#operator_lt)|Porovná řetězec. `CComBSTR`|
|[CComBSTR::operátor =](#operator_eq)|Přiřadí hodnotu `m_str`společnosti .|
|[CComBSTR::operátor ==](#operator_eq_eq)|Porovná řetězec. `CComBSTR`|
|[CComBSTR::>operátora](#operator_gt)|Porovná řetězec. `CComBSTR`|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CComBSTR::m_str](#m_str)|Obsahuje BSTR přidružené `CComBSTR` k objektu.|

## <a name="remarks"></a>Poznámky

Třída `CComBSTR` je obálka pro BSTRs, které jsou řetězce s předponou délky. Délka je uložena jako celé číslo v umístění paměti předcházející datům v řetězci.

[BSTR](/previous-versions/windows/desktop/automat/bstr) je null ukončena po poslední spočítaný znak, ale může také obsahovat prázdné znaky vložené do řetězce. Délka řetězce je určena počtem znaků, nikoli prvním znakem null.

> [!NOTE]
> Třída `CComBSTR` poskytuje počet členů (konstruktory, operátory přiřazení a operátory porovnání), které berou řetězce ANSI nebo Unicode jako argumenty. Ansi verze těchto funkcí jsou méně efektivní než jejich protějšky Unicode, protože dočasné řetězce Unicode jsou často vytvářeny interně. Pro efektivitu použijte verze Unicode, kde je to možné.

> [!NOTE]
> Z důvodu vylepšené chování vyhledávání implementované v sadě `bstr = L"String2" + bstr;`Visual Studio .NET, kód jako například `bstr = CStringW(L"String2") + bstr`, které mohou být zkompilovány v předchozích verzích, by měly být místo toho implementovány jako .

Seznam upozornění při použití `CComBSTR`naleznete v [tématu Programování pomocí CComBSTR](../../atl/programming-with-ccombstr-atl.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="ccombstrappend"></a><a name="append"></a>CComBSTR::Připojit

Připojí *buď lpsz* nebo BSTR člen *bstrSrc* [m_str](#m_str).

```
HRESULT Append(const CComBSTR& bstrSrc) throw();
HRESULT Append(wchar_t ch) throw();
HRESULT Append(char ch) throw();
HRESULT Append(LPCOLESTR lpsz) throw();
HRESULT Append(LPCSTR lpsz) throw();
HRESULT Append(LPCOLESTR lpsz, int nLen) throw();
```

### <a name="parameters"></a>Parametry

*bstrSrc řekl:*<br/>
[v] Objekt `CComBSTR` připojit.

*Ch*<br/>
[v] Znak připojit.

*lpsz*<br/>
[v] Řetězec znaků s nulovým ukončením, který chcete připojit. Řetězec Unicode můžete předat prostřednictvím přetížení LPCOLESTR nebo řetězce ANSI prostřednictvím verze LPCSTR.

*nLen*<br/>
[v] Počet znaků z *lpsz* připojit.

### <a name="return-value"></a>Návratová hodnota

S_OK na úspěch, nebo standardní HRESULT chybová hodnota.

### <a name="remarks"></a>Poznámky

Řetězec ANSI bude před připojením převeden na kódování Unicode.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#32](../../atl/codesnippet/cpp/ccombstr-class_1.cpp)]

## <a name="ccombstrappendbstr"></a><a name="appendbstr"></a>CComBSTR::AppendBSTR

Připojí zadaný BSTR k [m_str](#m_str).

```
HRESULT AppendBSTR(BSTR p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
[v] BSTR připojit.

### <a name="return-value"></a>Návratová hodnota

S_OK na úspěch, nebo standardní HRESULT chybová hodnota.

### <a name="remarks"></a>Poznámky

Nepředávají běžné řetězec široký znak této metody. Kompilátor nemůže zachytit chybu a dojde k chybám běhu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#33](../../atl/codesnippet/cpp/ccombstr-class_2.cpp)]

## <a name="ccombstrappendbytes"></a><a name="appendbytes"></a>CComBSTR::Připojit bajty

Připojí zadaný počet bajtů k [m_str](#m_str) bez převodu.

```
HRESULT AppendBytes(const char* lpsz, int nLen) throw();
```

### <a name="parameters"></a>Parametry

*lpsz*<br/>
[v] Ukazatel na pole bajtů připojit.

*P*<br/>
[v] Počet bajtů připojit.

### <a name="return-value"></a>Návratová hodnota

S_OK na úspěch, nebo standardní HRESULT chybová hodnota.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#34](../../atl/codesnippet/cpp/ccombstr-class_3.cpp)]

## <a name="ccombstrarraytobstr"></a><a name="arraytobstr"></a>CComBSTR::ArrayToBSTR

Uvolní všechny existující řetězec `CComBSTR` uchvátí v objektu, pak vytvoří BSTR z prvního `CComBSTR` znaku každého prvku v safearray a připojí jej k objektu.

```
HRESULT ArrayToBSTR(const SAFEARRAY* pSrc) throw();
```

### <a name="parameters"></a>Parametry

*pSrc*<br/>
[v] Safearray obsahující prvky použité k vytvoření řetězce.

### <a name="return-value"></a>Návratová hodnota

S_OK na úspěch, nebo standardní HRESULT chybová hodnota.

## <a name="ccombstrassignbstr"></a><a name="assignbstr"></a>CComBSTR::AssignBSTR

Přiřadí bstr [m_str](#m_str).

```
HRESULT AssignBSTR(const BSTR bstrSrc) throw();
```

### <a name="parameters"></a>Parametry

*bstrSrc řekl:*<br/>
[v] BSTR přiřadit aktuální `CComBSTR` objekt.

### <a name="return-value"></a>Návratová hodnota

S_OK na úspěch, nebo standardní HRESULT chybová hodnota.

## <a name="ccombstrattach"></a><a name="attach"></a>CComBSTR::Připojit

Připojí BSTR k `CComBSTR` objektu nastavením [m_str](#m_str) člen *src*.

```cpp
void Attach(BSTR src) throw();
```

### <a name="parameters"></a>Parametry

*src*<br/>
[v] BSTR připojit k objektu.

### <a name="remarks"></a>Poznámky

Nepředávají běžné řetězec široký znak této metody. Kompilátor nemůže zachytit chybu a dojde k chybám běhu.

> [!NOTE]
> Tato metoda bude `m_str` uplatňovat, pokud je non- NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]

## <a name="ccombstrbstrtoarray"></a><a name="bstrtoarray"></a>CComBSTR::BSTRToArray

Vytvoří jednorozměrné pole safearray založené na nule, kde každý `CComBSTR` prvek pole je znak z objektu.

```
HRESULT BSTRToArray(LPSAFEARRAY* ppArray) throw();
```

### <a name="parameters"></a>Parametry

*ppArray*<br/>
[out] Ukazatel na safearray slouží k uložení výsledky funkce.

### <a name="return-value"></a>Návratová hodnota

S_OK na úspěch, nebo standardní HRESULT chybová hodnota.

## <a name="ccombstrbytelength"></a><a name="bytelength"></a>CComBSTR::Délka bajty

Vrátí počet bajtů `m_str`v , s výjimkou ukončujícího znaku null.

```
unsigned int ByteLength() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Délka [m_str](#m_str) člen v bajtů.

### <a name="remarks"></a>Poznámky

Vrátí hodnotu 0, pokud `m_str` je null.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#36](../../atl/codesnippet/cpp/ccombstr-class_5.cpp)]

## <a name="ccombstrccombstr"></a><a name="ccombstr"></a>CComBSTR::CComBSTR

Konstruktor Výchozí konstruktor nastaví [člen m_str](#m_str) na hodnotu NULL.

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

*nVelikost*<br/>
[v] Počet znaků, které chcete kopírovat z *sz* nebo `CComBSTR`počáteční velikost znaků pro .

*Sz*<br/>
[v] Řetězec ke kopírování. Verze Unicode určuje LPCOLESTR; verze ANSI určuje LPCSTR.

*pSrc*<br/>
[v] Řetězec ke kopírování. Verze Unicode určuje LPCOLESTR; verze ANSI určuje LPCSTR.

*src*<br/>
[v] Objekt. `CComBSTR`

*guid*<br/>
[v] Odkaz na `GUID` strukturu.

### <a name="remarks"></a>Poznámky

Copy konstruktor `m_str` nastaví na kopii bstr člen *src*. Konstruktor `REFGUID` převede identifikátor GUID na `StringFromGUID2` řetězec pomocí a uloží výsledek.

Ostatní konstruktory `m_str` nastavena na kopii zadaného řetězce. Pokud předáte hodnotu pro *nSize*, budou zkopírovány pouze znaky *nSize,* následované ukončujícím znakem null.

`CComBSTR`podporuje pohyb sémantiku. Konstruktor move (konstruktor, který přebírá odkaz na`&&`rvalu ( ) můžete použít k vytvoření nového objektu, který používá stejná podkladová data jako starý objekt, který předáte jako argument, bez režie kopírování objektu.

Destruktor uvolní řetězec, na `m_str`který je odkazováno .

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#37](../../atl/codesnippet/cpp/ccombstr-class_6.cpp)]

## <a name="ccombstrccombstr"></a><a name="dtor"></a>CComBSTR::~CComBSTR

Destruktor.

```
~CComBSTR();
```

### <a name="remarks"></a>Poznámky

Destruktor uvolní řetězec, na `m_str`který je odkazováno .

## <a name="ccombstrcopy"></a><a name="copy"></a>CComBSTR::Kopírovat

Přiděluje a `m_str`vrací kopii .

```
BSTR Copy() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Kopie člena [m_str.](#m_str) Pokud `m_str` je NULL, vrátí hodnotu NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#38](../../atl/codesnippet/cpp/ccombstr-class_7.cpp)]

## <a name="ccombstrcopyto"></a><a name="copyto"></a>CComBSTR::Copyto

Přidělí a vrátí kopii [m_str](#m_str) prostřednictvím parametru.

```
HRESULT CopyTo(BSTR* pbstr) throw();

HRESULT CopyTo(VARIANT* pvarDest) throw();
```

### <a name="parameters"></a>Parametry

*pbstr*<br/>
[out] Adresa BSTR, ve kterém chcete vrátit řetězec přidělený touto metodou.

*pvarDest*<br/>
[out] Adresa VARIANT, ve kterém chcete vrátit řetězec přidělený touto metodou.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT označující úspěch nebo neúspěch kopie.

### <a name="remarks"></a>Poznámky

Po volání této metody varianta poukázal *podle pvarDest* bude typu VT_BSTR.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#39](../../atl/codesnippet/cpp/ccombstr-class_8.cpp)]

## <a name="ccombstrdetach"></a><a name="detach"></a>CComBSTR::Detach

Odpojí [m_str](#m_str) od `CComBSTR` objektu `m_str` a nastaví na HODNOTU NULL.

```
BSTR Detach() throw();
```

### <a name="return-value"></a>Návratová hodnota

BSTR přidružené k `CComBSTR` objektu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#40](../../atl/codesnippet/cpp/ccombstr-class_9.cpp)]

## <a name="ccombstrempty"></a><a name="empty"></a>CComBSTR::Prázdné

Osvobodí [člena m_str.](#m_str)

```cpp
void Empty() throw();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#41](../../atl/codesnippet/cpp/ccombstr-class_10.cpp)]

## <a name="ccombstrlength"></a><a name="length"></a>CComBSTR::Délka

Vrátí počet znaků `m_str`v , s výjimkou ukončujícího znaku null.

```
unsigned int Length() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Délka [m_str](#m_str) člen.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#42](../../atl/codesnippet/cpp/ccombstr-class_11.cpp)]

## <a name="ccombstrloadstring"></a><a name="loadstring"></a>CComBSTR::Načítat

Načte řetězec prostředek určený *nID* a uloží jej do tohoto objektu.

```
bool LoadString(HINSTANCE hInst, UINT nID) throw();
bool LoadString(UINT nID) throw();
```

### <a name="parameters"></a>Parametry

Viz [LoadString](/windows/win32/api/winuser/nf-winuser-loadstringw) v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je řetězec úspěšně načten. v opačném případě vrátí hodnotu FALSE.

### <a name="remarks"></a>Poznámky

První funkce načte prostředek z vámi identifikovaného modulu pomocí parametru *hInst.* Druhá funkce načte prostředek z modulu prostředků přidruženého k objektu [odvozenému ccommodulem,](../../atl/reference/ccommodule-class.md)který se používá v tomto projektu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#43](../../atl/codesnippet/cpp/ccombstr-class_12.cpp)]

## <a name="ccombstrm_str"></a><a name="m_str"></a>CComBSTR::m_str

Obsahuje BSTR přidružené `CComBSTR` k objektu.

```
BSTR m_str;
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#49](../../atl/codesnippet/cpp/ccombstr-class_13.cpp)]

## <a name="ccombstroperator-bstr"></a><a name="operator_bstr"></a>CComBSTR::operátor BSTR

Převrhne `CComBSTR` objekt bstr.

```
operator BSTR() const throw();
```

### <a name="remarks"></a>Poznámky

Umožňuje předat `CComBSTR` objekty funkcím, které mají **parametry [in] BSTR.**

### <a name="example"></a>Příklad

Viz příklad pro [CComBSTR::m_str](#m_str).

## <a name="ccombstroperator-"></a><a name="operator_not"></a>CComBSTR::operátor !

Zkontroluje, zda je řetězec BSTR null.

```
bool operator!() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je člen [m_str](#m_str) null; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tento operátor kontroluje pouze hodnotu NULL, nikoli prázdný řetězec.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]

## <a name="ccombstroperator-"></a><a name="operator_neq"></a>CComBSTR::operátor !=

Vrátí logický opak [operátoru ==](#operator_eq_eq).

```
bool operator!= (const CComBSTR& bstrSrc) const throw();
bool operator!= (LPCOLESTR pszSrc) const;
bool operator!= (LPCSTR pszSrc) const;
bool operator!= (int nNull) const throw();
```

### <a name="parameters"></a>Parametry

*bstrSrc řekl:*<br/>
[v] Objekt. `CComBSTR`

*pszSrc*<br/>
[v] Řetězec s nulovým ukončením.

*nNull*<br/>
[v] Musí být null.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud se porovnávaná položka nerovná objektu. `CComBSTR` v opačném případě vrátí hodnotu FALSE.

### <a name="remarks"></a>Poznámky

`CComBSTR`s jsou porovnávány textově v kontextu výchozího národního prostředí uživatele. Konečný operátor porovnání pouze porovná obsažený řetězec proti NULL.

## <a name="ccombstroperator-amp"></a><a name="operator_amp"></a>CComBSTR::operátor&amp;

Vrátí adresu BSTR uložené v [m_str](#m_str) člen.

```
BSTR* operator&() throw();
```

### <a name="remarks"></a>Poznámky

`CComBstr operator &`má zvláštní kontrolní výraz s ním spojené pomoci identifikovat nevracení paměti. Program bude uplatňovat `m_str` při inicializování člena. Toto tvrzení bylo vytvořeno k identifikaci `& operator` situací, kdy `m_str` programátor používá k přiřazení `m_str`nové hodnoty členu bez uvolnění první přidělení . Pokud `m_str` se rovná NULL, program předpokládá, že m_str ještě nebyla přidělena. V takovém případě program nebude uplatňovat.

Toto tvrzení není ve výchozím nastavení povoleno. Definujte ATL_CCOMBSTR_ADDRESS_OF_ASSERT, chcete-li tento kontrolní výraz povolit.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#46](../../atl/codesnippet/cpp/ccombstr-class_14.cpp)]

[!code-cpp[NVC_ATL_Utilities#47](../../atl/codesnippet/cpp/ccombstr-class_15.cpp)]

## <a name="ccombstroperator-"></a><a name="operator_add_eq"></a>CComBSTR::operátor +=

Připojí řetězec k `CComBSTR` objektu.

```
CComBSTR& operator+= (const CComBSTR& bstrSrc);
CComBSTR& operator+= (const LPCOLESTR pszSrc);
```

### <a name="parameters"></a>Parametry

*bstrSrc řekl:*<br/>
[v] Objekt `CComBSTR` připojit.

*pszSrc*<br/>
[v] Řetězec s nulovým ukončením připojit.

### <a name="remarks"></a>Poznámky

`CComBSTR`s jsou porovnávány textově v kontextu výchozího národního prostředí uživatele. Porovnání LPCOLESTR se `memcmp` provádí pomocí na nezpracovaná data v každém řetězci. Porovnání LPCSTR se provádí stejným způsobem, jakmile byla vytvořena dočasná kopie *Unicode pszSrc.* Konečný operátor porovnání pouze porovná obsažený řetězec proti NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#48](../../atl/codesnippet/cpp/ccombstr-class_16.cpp)]

## <a name="ccombstroperator-lt"></a><a name="operator_lt"></a>CComBSTR::operátor&lt;

Porovná řetězec. `CComBSTR`

```
bool operator<(const CComBSTR& bstrSrc) const throw();
bool operator<(LPCOLESTR pszSrc) const throw();
bool operator<(LPCSTR pszSrc) const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je `CComBSTR` porovnávaná položka menší než objekt. v opačném případě vrátí hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Porovnání se provádí pomocí výchozího národního prostředí uživatele.

## <a name="ccombstroperator-"></a><a name="operator_eq"></a>CComBSTR::operátor =

Nastaví [člen m_str](#m_str) na kopii *pSrc* nebo na kopii člena BSTR *src*. Operátor přiřazení přesunutí `src` se přesune bez jeho zkopírování.

```
CComBSTR& operator= (const CComBSTR& src);
CComBSTR& operator= (LPCOLESTR pSrc);
CComBSTR& operator= (LPCSTR pSrc);
CComBSTR& operator= (CComBSTR&& src) throw(); // (Visual Studio 2017)
```

### <a name="remarks"></a>Poznámky

Parametr *pSrc* určuje buď LPCOLESTR pro verze Unicode, nebo LPCSTR pro verze ANSI.

### <a name="example"></a>Příklad

Viz příklad [ccombstr::Copy](#copy).

## <a name="ccombstroperator-"></a><a name="operator_eq_eq"></a>CComBSTR::operátor ==

Porovná řetězec. `CComBSTR` `CComBSTR`s jsou porovnávány textově v kontextu výchozího národního prostředí uživatele.

```
bool operator== (const CComBSTR& bstrSrc) const throw();
bool operator== (LPCOLESTR pszSrc) const;
bool operator== (LPCSTR pszSrc) const;
bool operator== (int nNull) const throw();
```

### <a name="parameters"></a>Parametry

*bstrSrc řekl:*<br/>
[v] Objekt. `CComBSTR`

*pszSrc*<br/>
[v] Řetězec s nulovým ukončením.

*nNull*<br/>
[v] Musí být null.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je `CComBSTR` porovnávaná položka rovna objektu; v opačném případě vrátí hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Konečný operátor porovnání pouze porovná obsažený řetězec proti NULL.

## <a name="ccombstroperator-gt"></a><a name="operator_gt"></a>CComBSTR::operátor&gt;

Porovná řetězec. `CComBSTR`

```
bool operator>(const CComBSTR& bstrSrc) const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je `CComBSTR` porovnávaná položka větší než objekt. v opačném případě vrátí hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Porovnání se provádí pomocí výchozího národního prostředí uživatele.

## <a name="ccombstrreadfromstream"></a><a name="readfromstream"></a>CComBSTR::ReadFromStream

Nastaví [člen m_str](#m_str) na BSTR obsažené v zadaném datovém proudu.

```
HRESULT ReadFromStream(IStream* pStream) throw();
```

### <a name="parameters"></a>Parametry

*pStream*<br/>
[v] Ukazatel na rozhraní [IStream](/windows/win32/api/objidl/nn-objidl-istream) na datovém proudu obsahující data.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

`ReadToStream`vyžaduje, aby obsah datového proudu na aktuální pozici byl kompatibilní s datovým formátem napsaným voláním [WriteToStream](#writetostream).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#44](../../atl/codesnippet/cpp/ccombstr-class_17.cpp)]

## <a name="ccombstrtolower"></a><a name="tolower"></a>CComBSTR::ToLower

Převede obsažený řetězec na malá písmena.

```
HRESULT ToLower() throw();
```

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Další `CharLowerBuff` informace o tom, jak se převod provádí, naleznete.

## <a name="ccombstrtoupper"></a><a name="toupper"></a>CComBSTR::Toupper

Převede obsažený řetězec na velká písmena.

```
HRESULT ToUpper() throw();
```

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Další `CharUpperBuff` informace o tom, jak se převod provádí, naleznete.

## <a name="ccombstrwritetostream"></a><a name="writetostream"></a>CComBSTR::WriteToStream

Uloží [m_str](#m_str) člen do datového proudu.

```
HRESULT WriteToStream(IStream* pStream) throw();
```

### <a name="parameters"></a>Parametry

*pStream*<br/>
[v] Ukazatel na rozhraní [IStream](/windows/win32/api/objidl/nn-objidl-istream) v datovém proudu.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Můžete znovu Vytvořit BSTR z obsahu datového proudu pomocí [ReadFromStream](#readfromstream) funkce.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#45](../../atl/codesnippet/cpp/ccombstr-class_18.cpp)]

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Makra převodu řetězců knihovny ATL a knihovny MFC](string-conversion-macros.md)
