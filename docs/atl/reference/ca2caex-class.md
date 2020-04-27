---
title: CA2CAEX – třída
ms.date: 11/04/2016
f1_keywords:
- CA2CAEX
- ATLCONV/ATL::CA2CAEX
- ATLCONV/ATL::CA2CAEX::CA2CAEX
- ATLCONV/ATL::CA2CAEX::m_psz
helpviewer_keywords:
- CA2CAEX class
ms.assetid: 388e7c1d-a144-474c-a182-b15f69a74bd8
ms.openlocfilehash: 505c1e369bc5949fea291a2172c16d5e52c75567
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168511"
---
# <a name="ca2caex-class"></a>CA2CAEX – třída

Tato třída je používána makry převodu řetězce CA2CTEX a CT2CAEX a typedef CA2CA.

> [!IMPORTANT]
> Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
template<int t_nBufferLength = 128>
class CA2CAEX
```

### <a name="parameters"></a>Parametry

*t_nBufferLength*<br/>
Velikost vyrovnávací paměti použité v procesu překladu. Výchozí délka je 128 bajtů.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CA2CAEX::CA2CAEX](#ca2caex)|Konstruktor|
|[CA2CAEX:: ~ CA2CAEX](#dtor)|Destruktor.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CA2CAEX:: operator LPCSTR](#operator_lpcstr)|Operátor převodu|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CA2CAEX:: m_psz](#m_psz)|Datový člen, který ukládá zdrojový řetězec.|

## <a name="remarks"></a>Poznámky

Pokud nejsou vyžadovány žádné další funkce, použijte CA2CTEX, CT2CAEX nebo CA2CA ve vlastním kódu.

Tato třída je bezpečná pro použití ve smyčkách a nepřetéká do zásobníku. Ve výchozím nastavení budou třídy převodu ATL a makra pro převod používat znakovou stránku ANSI aktuálního vlákna.

Následující makra jsou založena na této třídě:

- CA2CTEX

- CT2CAEX

Následující definice typedef je založena na této třídě:

- CA2CA

Diskuzi o těchto makrech převodu textu viz [makra ATL a MFC String Conversion](string-conversion-macros.md).

## <a name="example"></a>Příklad

Příklad použití těchto maker převodů řetězců naleznete v tématech [ATL a makra převodu řetězců knihovny MFC](string-conversion-macros.md) .

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlconv. h

## <a name="ca2caexca2caex"></a><a name="ca2caex"></a>CA2CAEX::CA2CAEX

Konstruktor

```cpp
CA2CAEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2CAEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Textový řetězec, který má být převeden.

*nCodePage*<br/>
Nepoužitelné v této třídě.

### <a name="remarks"></a>Poznámky

Vytvoří vyrovnávací paměť požadovanou pro překlad.

## <a name="ca2caexca2caex"></a><a name="dtor"></a>CA2CAEX:: ~ CA2CAEX

Destruktor.

```cpp
~CA2CAEX() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní přidělenou vyrovnávací paměť.

## <a name="ca2caexm_psz"></a><a name="m_psz"></a>CA2CAEX:: m_psz

Datový člen, který ukládá zdrojový řetězec.

```cpp
LPCSTR m_psz;
```

## <a name="ca2caexoperator-lpcstr"></a><a name="operator_lpcstr"></a>CA2CAEX:: operator LPCSTR

Operátor převodu

```cpp
operator LPCSTR() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí textový řetězec jako typ LPCSTR.

## <a name="see-also"></a>Viz také

[CA2AEX – třída](../../atl/reference/ca2aex-class.md)<br/>
[CA2WEX – třída](../../atl/reference/ca2wex-class.md)<br/>
[CW2AEX – třída](../../atl/reference/cw2aex-class.md)<br/>
[CW2CWEX – třída](../../atl/reference/cw2cwex-class.md)<br/>
[CW2WEX – třída](../../atl/reference/cw2wex-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
