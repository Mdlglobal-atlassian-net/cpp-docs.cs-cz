---
title: Třída CW2CWEX
ms.date: 11/04/2016
f1_keywords:
- CW2CWEX
- ATLCONV/ATL::CW2CWEX
- ATLCONV/ATL::CW2CWEX::CW2CWEX
- ATLCONV/ATL::CW2CWEX::m_psz
helpviewer_keywords:
- CW2CWEX class
ms.assetid: d654b22b-05a6-410f-a0ec-9a2cbbb4cca7
ms.openlocfilehash: 07dd0319586054403d8ed0c8efc813b4061e355a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330437"
---
# <a name="cw2cwex-class"></a>Třída CW2CWEX

Tato třída se používá makra převodu řetězce CW2CTEX a CT2CWEX a typedef CW2W.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<int t_nBufferLength = 128>
class CW2CWEX
```

#### <a name="parameters"></a>Parametry

*t_nBufferLength*<br/>
Velikost vyrovnávací paměti použité v procesu překladu. Výchozí délka je 128 bajtů.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CW2CWEX::CW2CWEX](#cw2cwex)|Konstruktor|
|[CW2CWEX::~CW2CWEX](#dtor)|Destruktor.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CW2CWEX::operátor LPCWSTR](#operator_lpcwstr)|Operátor převodu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CW2CWEX::m_psz](#m_psz)|Datový člen, který ukládá zdrojový řetězec.|

## <a name="remarks"></a>Poznámky

Pokud není vyžadována další funkce, použijte cw2ctex, CT2CWEX nebo CW2W ve vašem kódu.

Tato třída je bezpečné použití ve smyčkách a nebude přetečení zásobníku. Ve výchozím nastavení používají třídy převodu a makra atl aktuální vlákno pro převod.

Následující makra jsou založeny na této třídě:

- CW2CTEX

- CT2CWEX

Následující typedef je založena na této třídě:

- CW2W

Diskuse o těchto marech převodu textu naleznete v tématu [ATL a Makra převodu řetězců knihovny MFC](string-conversion-macros.md).

## <a name="example"></a>Příklad

Příklad použití těchto makra převodu řetězců řetězce [knihovny ATL a knihovny MFC.](string-conversion-macros.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlconv.h

## <a name="cw2cwexcw2cwex"></a><a name="cw2cwex"></a>CW2CWEX::CW2CWEX

Konstruktor

```
CW2CWEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2CWEX(LPCWSTR psz) throw(...);
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Textový řetězec, který má být převeden.

*nCodePage*<br/>
Znaková stránka. Nepoužívá se v této třídě.

### <a name="remarks"></a>Poznámky

Přidělí vyrovnávací paměť použitou v procesu překladu.

## <a name="cw2cwexcw2cwex"></a><a name="dtor"></a>CW2CWEX::~CW2CWEX

Destruktor.

```
~CW2CWEX() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní přidělenou vyrovnávací paměť.

## <a name="cw2cwexm_psz"></a><a name="m_psz"></a>CW2CWEX::m_psz

Datový člen, který ukládá zdrojový řetězec.

```
LPCWSTR m_psz;
```

## <a name="cw2cwexoperator-lpcwstr"></a><a name="operator_lpcwstr"></a>CW2CWEX::operátor LPCWSTR

Operátor převodu.

```
operator LPCWSTR() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí textový řetězec jako typ LPCWSTR.

## <a name="see-also"></a>Viz také

[Třída CA2AEX](../../atl/reference/ca2aex-class.md)<br/>
[Třída CA2CAEX](../../atl/reference/ca2caex-class.md)<br/>
[Třída CA2WEX](../../atl/reference/ca2wex-class.md)<br/>
[Třída CW2AEX](../../atl/reference/cw2aex-class.md)<br/>
[Třída CW2WEX](../../atl/reference/cw2wex-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
