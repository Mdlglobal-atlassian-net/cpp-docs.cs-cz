---
title: Třída CA2WEX
ms.date: 11/04/2016
f1_keywords:
- CA2WEX
- ATLCONV/ATL::CA2WEX
- ATLCONV/ATL::CA2WEX::CA2WEX
- ATLCONV/ATL::CA2WEX::m_psz
- ATLCONV/ATL::CA2WEX::m_szBuffer
helpviewer_keywords:
- CA2WEX class
ms.assetid: 317d9ffb-e84f-47e8-beda-57e28fb19124
ms.openlocfilehash: c9123e163ca828fa71fe217e46537ceb18e6f549
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319132"
---
# <a name="ca2wex-class"></a>Třída CA2WEX

Tato třída je používána makry převodu řetězce CA2TEX, CA2CTEX, CT2WEX a CT2CWEX a typedef CA2W.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <int t_nBufferLength = 128>
class CA2WEX
```

#### <a name="parameters"></a>Parametry

*t_nBufferLength*<br/>
Velikost vyrovnávací paměti použité v procesu překladu. Výchozí délka je 128 bajtů.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CA2WEX::CA2WEX](#ca2wex)|Konstruktor|
|[CA2WEX::~CA2WEX](#dtor)|Destruktor.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CA2WEX::operátor LPWSTR](#operator_lpwstr)|Operátor převodu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CA2WEX::m_psz](#m_psz)|Datový člen, který ukládá zdrojový řetězec.|
|[CA2WEX::m_szBuffer](#m_szbuffer)|Statická vyrovnávací paměť, která se používá k uložení převedeného řetězce.|

## <a name="remarks"></a>Poznámky

Pokud není vyžadována další funkce, použijte ve svém kódu CA2TEX, CA2CTEX, CT2WEX, CT2CWEX nebo CA2W.

Tato třída obsahuje statickou vyrovnávací paměť s pevnou velikostí, která se používá k uložení výsledku převodu. Pokud je výsledek příliš velký a nevejde se do statické vyrovnávací paměti, třída přidělí paměť pomocí **malloc**, uvolnění paměti při objektu přejde mimo rozsah. Tím je zajištěno, že na rozdíl od makra převodu textu, které jsou k dispozici v předchozích verzích seznamu ATL, je tato třída bezpečná pro použití ve smyčkách a že nebude přetečení zásobníku.

Pokud se třída pokusí přidělit paměť na haldě a selže, bude volat `AtlThrow` s argumentem E_OUTOFMEMORY.

Ve výchozím nastavení používají třídy převodu a makra atl aktuální vlákno pro převod. Pokud chcete přepsat toto chování pro konkrétní převod, zadejte znakovou stránku jako druhý parametr konstruktoru pro třídu.

Následující makra jsou založeny na této třídě:

- CA2TEX

- CA2CTEX

- ČT2WEX

- CT2CWEX

Následující typedef je založena na této třídě:

- CA2W

Diskuse o těchto marech převodu textu naleznete v tématu [ATL a Makra převodu řetězců knihovny MFC](string-conversion-macros.md).

## <a name="example"></a>Příklad

Příklad použití těchto makra převodu řetězců řetězce [knihovny ATL a knihovny MFC.](string-conversion-macros.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlconv.h

## <a name="ca2wexca2wex"></a><a name="ca2wex"></a>CA2WEX::CA2WEX

Konstruktor

```
CA2WEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2WEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Textový řetězec, který má být převeden.

*nCodePage*<br/>
Znaková stránka použitá k provedení převodu. Další podrobnosti naleznete v diskusi o parametrech znakové stránky pro funkci [MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar) ve funkci sady Windows SDK.

### <a name="remarks"></a>Poznámky

Přidělí vyrovnávací paměť použitou v procesu překladu.

## <a name="ca2wexca2wex"></a><a name="dtor"></a>CA2WEX::~CA2WEX

Destruktor.

```
~CA2WEX() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní přidělenou vyrovnávací paměť.

## <a name="ca2wexm_psz"></a><a name="m_psz"></a>CA2WEX::m_psz

Datový člen, který ukládá zdrojový řetězec.

```
LPWSTR m_psz;
```

## <a name="ca2wexm_szbuffer"></a><a name="m_szbuffer"></a>CA2WEX::m_szBuffer

Statická vyrovnávací paměť, která se používá k uložení převedeného řetězce.

```
wchar_t m_szBuffer[t_nBufferLength];
```

## <a name="ca2wexoperator-lpwstr"></a><a name="operator_lpwstr"></a>CA2WEX::operátor LPWSTR

Operátor převodu.

```
operator LPWSTR() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí textový řetězec jako typ LPWSTR.

## <a name="see-also"></a>Viz také

[Třída CA2AEX](../../atl/reference/ca2aex-class.md)<br/>
[Třída CA2CAEX](../../atl/reference/ca2caex-class.md)<br/>
[Třída CW2AEX](../../atl/reference/cw2aex-class.md)<br/>
[Třída CW2CWEX](../../atl/reference/cw2cwex-class.md)<br/>
[Třída CW2WEX](../../atl/reference/cw2wex-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
