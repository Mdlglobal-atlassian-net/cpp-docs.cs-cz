---
title: Třída CW2WEX
ms.date: 11/04/2016
f1_keywords:
- CW2WEX
- ATLCONV/ATL::CW2WEX
- ATLCONV/ATL::CW2WEX::CW2WEX
- ATLCONV/ATL::CW2WEX::m_psz
- ATLCONV/ATL::CW2WEX::m_szBuffer
helpviewer_keywords:
- CW2WEX class
ms.assetid: 46262e56-e0d2-41fe-855b-0b67ecc8fcd7
ms.openlocfilehash: b116775a595f9fb3612d46e19526cf1396f85002
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330350"
---
# <a name="cw2wex-class"></a>Třída CW2WEX

Tato třída se používá makra převodu řetězce CW2TEX a CT2WEX a typedef CW2W.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <int t_nBufferLength = 128>
class CW2WEX
```

#### <a name="parameters"></a>Parametry

*t_nBufferLength*<br/>
Velikost vyrovnávací paměti použité v procesu překladu. Výchozí délka je 128 bajtů.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CW2WEX::CW2WEX](#cw2wex)|Konstruktor|
|[CW2WEX::~CW2WEX](#dtor)|Destruktor.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CW2WEX::operátor LPWSTR](#operator_lpwstr)|Operátor převodu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CW2WEX::m_psz](#m_psz)|Datový člen, který ukládá zdrojový řetězec.|
|[CW2WEX::m_szBuffer](#m_szbuffer)|Statická vyrovnávací paměť, která se používá k uložení převedeného řetězce.|

## <a name="remarks"></a>Poznámky

Pokud není vyžadována další funkce, použijte CW2TEX, CT2WEX nebo CW2W ve vašem kódu.

Tato třída obsahuje statickou vyrovnávací paměť s pevnou velikostí, která se používá k uložení výsledku převodu. Pokud je výsledek příliš velký a nevejde se do statické vyrovnávací paměti, třída přidělí paměť pomocí **malloc**, uvolnění paměti při objektu přejde mimo rozsah. Tím je zajištěno, že na rozdíl od makra převodu textu, které jsou k dispozici v předchozích verzích seznamu ATL, je tato třída bezpečná pro použití ve smyčkách a že nebude přetečení zásobníku.

Pokud se třída pokusí přidělit paměť na haldě a selže, bude volat `AtlThrow` s argumentem E_OUTOFMEMORY.

Ve výchozím nastavení používají třídy převodu a makra atl aktuální vlákno pro převod.

Následující makra jsou založeny na této třídě:

- CW2TEX

- ČT2WEX

Následující typedef je založena na této třídě:

- CW2W

Diskuse o těchto marech převodu textu naleznete v tématu [ATL a Makra převodu řetězců knihovny MFC](string-conversion-macros.md).

## <a name="example"></a>Příklad

Příklad použití těchto makra převodu řetězců řetězce [knihovny ATL a knihovny MFC.](string-conversion-macros.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlconv.h

## <a name="cw2wexcw2wex"></a><a name="cw2wex"></a>CW2WEX::CW2WEX

Konstruktor

```
CW2WEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2WEX( LPCWSTR  psz) throw(...);
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Textový řetězec, který má být převeden.

*nCodePage*<br/>
Znaková stránka. Nepoužívá se v této třídě.

### <a name="remarks"></a>Poznámky

Vytvoří vyrovnávací paměť požadovanou pro překlad.

## <a name="cw2wexcw2wex"></a><a name="dtor"></a>CW2WEX::~CW2WEX

Destruktor.

```
~CW2WEX() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní přidělenou vyrovnávací paměť.

## <a name="cw2wexm_psz"></a><a name="m_psz"></a>CW2WEX::m_psz

Datový člen, který ukládá zdrojový řetězec.

```
LPWSTR m_psz;
```

## <a name="cw2wexm_szbuffer"></a><a name="m_szbuffer"></a>CW2WEX::m_szBuffer

Statická vyrovnávací paměť, která se používá k uložení převedeného řetězce.

```
wchar_t m_szBuffer[t_nBufferLength];
```

## <a name="cw2wexoperator-lpwstr"></a><a name="operator_lpwstr"></a>CW2WEX::operátor LPWSTR

Operátor obsazení.

```
operator LPWSTR() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí textový řetězec jako typ LPWSTR.

## <a name="see-also"></a>Viz také

[Třída CA2AEX](../../atl/reference/ca2aex-class.md)<br/>
[Třída CA2CAEX](../../atl/reference/ca2caex-class.md)<br/>
[Třída CA2WEX](../../atl/reference/ca2wex-class.md)<br/>
[Třída CW2AEX](../../atl/reference/cw2aex-class.md)<br/>
[Třída CW2CWEX](../../atl/reference/cw2cwex-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
