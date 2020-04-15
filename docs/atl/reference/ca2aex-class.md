---
title: Třída CA2AEX
ms.date: 11/04/2016
f1_keywords:
- CA2AEX
- ATLCONV/ATL::CA2AEX
- ATLCONV/ATL::CA2AEX::CA2AEX
- ATLCONV/ATL::CA2AEX::m_psz
- ATLCONV/ATL::CA2AEX::m_szBuffer
helpviewer_keywords:
- CA2AEX class
ms.assetid: 57dc65df-d9cf-4a84-99d3-6e031dde3664
ms.openlocfilehash: 4f8b9f91e9bc499523fe3484bc76325e2efb8140
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319183"
---
# <a name="ca2aex-class"></a>Třída CA2AEX

Tato třída se používá makra převodu řetězce CA2TEX a CT2AEX a typedef CA2A.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <int t_nBufferLength = 128>
class CA2AEX
```

#### <a name="parameters"></a>Parametry

*t_nBufferLength*<br/>
Velikost vyrovnávací paměti použité v procesu překladu. Výchozí délka je 128 bajtů.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CA2AEX::CA2AEX](#ca2aex)|Konstruktor|
|[CA2AEX::~CA2AEX](#dtor)|Destruktor.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CA2AEX::operátor LPSTR](#operator_lpstr)|Operátor převodu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CA2AEX::m_psz](#m_psz)|Datový člen, který ukládá zdrojový řetězec.|
|[CA2AEX::m_szBuffer](#m_szbuffer)|Statická vyrovnávací paměť, která se používá k uložení převedeného řetězce.|

## <a name="remarks"></a>Poznámky

Pokud není vyžadována další funkce, použijte CA2TEX, CT2AEX nebo CA2A ve vlastním kódu.

Tato třída obsahuje statickou vyrovnávací paměť s pevnou velikostí, která se používá k uložení výsledku převodu. Pokud je výsledek příliš velký a nevejde se do statické vyrovnávací paměti, třída přidělí paměť pomocí **malloc**, uvolnění paměti při objektu přejde mimo rozsah. Tím je zajištěno, že na rozdíl od makra převodu textu, které jsou k dispozici v předchozích verzích seznamu ATL, je tato třída bezpečná pro použití ve smyčkách a že nebude přetečení zásobníku.

Pokud se třída pokusí přidělit paměť na haldě a selže, bude volat `AtlThrow` s argumentem E_OUTOFMEMORY.

Ve výchozím nastavení používají třídy převodu a makra atl aktuální vlákno pro převod.

Následující makra jsou založeny na této třídě:

- CA2TEX

- ČT2AEX

Následující typedef je založena na této třídě:

- CA2A

Diskuse o těchto marech převodu textu naleznete v tématu [ATL a Makra převodu řetězců knihovny MFC](string-conversion-macros.md).

## <a name="example"></a>Příklad

Příklad použití těchto makra převodu řetězců řetězce [knihovny ATL a knihovny MFC.](string-conversion-macros.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlconv.h

## <a name="ca2aexca2aex"></a><a name="ca2aex"></a>CA2AEX::CA2AEX

Konstruktor

```
CA2AEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2AEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Textový řetězec, který má být převeden.

*nCodePage*<br/>
Nepoužito v této třídě.

### <a name="remarks"></a>Poznámky

Vytvoří vyrovnávací paměť požadovanou pro překlad.

## <a name="ca2aexca2aex"></a><a name="dtor"></a>CA2AEX::~CA2AEX

Destruktor.

```
~CA2AEX() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní přidělenou vyrovnávací paměť.

## <a name="ca2aexm_psz"></a><a name="m_psz"></a>CA2AEX::m_psz

Datový člen, který ukládá zdrojový řetězec.

```
LPSTR m_psz;
```

## <a name="ca2aexm_szbuffer"></a><a name="m_szbuffer"></a>CA2AEX::m_szBuffer

Statická vyrovnávací paměť, která se používá k uložení převedeného řetězce.

```
char m_szBuffer[ t_nBufferLength];
```

## <a name="ca2aexoperator-lpstr"></a><a name="operator_lpstr"></a>CA2AEX::operátor LPSTR

Operátor převodu.

```
operator LPSTR() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí textový řetězec jako typ LPSTR.

## <a name="see-also"></a>Viz také

[Třída CA2CAEX](../../atl/reference/ca2caex-class.md)<br/>
[Třída CA2WEX](../../atl/reference/ca2wex-class.md)<br/>
[Třída CW2AEX](../../atl/reference/cw2aex-class.md)<br/>
[Třída CW2CWEX](../../atl/reference/cw2cwex-class.md)<br/>
[Třída CW2WEX](../../atl/reference/cw2wex-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
