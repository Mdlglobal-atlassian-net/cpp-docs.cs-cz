---
title: Třída CA2CAEX
ms.date: 11/04/2016
f1_keywords:
- CA2CAEX
- ATLCONV/ATL::CA2CAEX
- ATLCONV/ATL::CA2CAEX::CA2CAEX
- ATLCONV/ATL::CA2CAEX::m_psz
helpviewer_keywords:
- CA2CAEX class
ms.assetid: 388e7c1d-a144-474c-a182-b15f69a74bd8
ms.openlocfilehash: e6c727993b2907aaa551421a5d2d23e372b68917
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319134"
---
# <a name="ca2caex-class"></a>Třída CA2CAEX

Tato třída se používá makra převodu řetězců CA2CTEX a CT2CAEX a typedef CA2CA.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<int t_nBufferLength = 128>
class CA2CAEX
```

#### <a name="parameters"></a>Parametry

*t_nBufferLength*<br/>
Velikost vyrovnávací paměti použité v procesu překladu. Výchozí délka je 128 bajtů.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CA2CAEX::CA2CAEX](#ca2caex)|Konstruktor|
|[CA2CAEX::~CA2CAEX](#dtor)|Destruktor.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CA2CAEX::operátor LPCSTR](#operator_lpcstr)|Operátor převodu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CA2CAEX::m_psz](#m_psz)|Datový člen, který ukládá zdrojový řetězec.|

## <a name="remarks"></a>Poznámky

Pokud není vyžadována další funkce, použijte CA2CTEX, CT2CAEX nebo CA2CA ve vlastním kódu.

Tato třída je bezpečné použití ve smyčkách a nebude přetečení zásobníku. Ve výchozím nastavení budou třídy převodu a makra atl používat pro převod kódovou stránku ANSI aktuálního vlákna.

Následující makra jsou založeny na této třídě:

- CA2CTEX

- CT2CAEX

Následující typedef je založena na této třídě:

- CA2CA (CA2CA)

Diskuse o těchto marech převodu textu naleznete v tématu [ATL a Makra převodu řetězců knihovny MFC](string-conversion-macros.md).

## <a name="example"></a>Příklad

Příklad použití těchto makra převodu řetězců řetězce [knihovny ATL a knihovny MFC.](string-conversion-macros.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlconv.h

## <a name="ca2caexca2caex"></a><a name="ca2caex"></a>CA2CAEX::CA2CAEX

Konstruktor

```
CA2CAEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2CAEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Textový řetězec, který má být převeden.

*nCodePage*<br/>
Nepoužito v této třídě.

### <a name="remarks"></a>Poznámky

Vytvoří vyrovnávací paměť požadovanou pro překlad.

## <a name="ca2caexca2caex"></a><a name="dtor"></a>CA2CAEX::~CA2CAEX

Destruktor.

```
~CA2CAEX() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní přidělenou vyrovnávací paměť.

## <a name="ca2caexm_psz"></a><a name="m_psz"></a>CA2CAEX::m_psz

Datový člen, který ukládá zdrojový řetězec.

```
LPCSTR m_psz;
```

## <a name="ca2caexoperator-lpcstr"></a><a name="operator_lpcstr"></a>CA2CAEX::operátor LPCSTR

Operátor převodu.

```
operator LPCSTR() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí textový řetězec jako typ LPCSTR.

## <a name="see-also"></a>Viz také

[Třída CA2AEX](../../atl/reference/ca2aex-class.md)<br/>
[Třída CA2WEX](../../atl/reference/ca2wex-class.md)<br/>
[Třída CW2AEX](../../atl/reference/cw2aex-class.md)<br/>
[Třída CW2CWEX](../../atl/reference/cw2cwex-class.md)<br/>
[Třída CW2WEX](../../atl/reference/cw2wex-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
